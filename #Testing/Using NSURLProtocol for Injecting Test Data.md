# Using NSURLProtocol for Injecting Test Data

_Captured: 2015-12-06 at 01:13 from [www.infinite-loop.dk](http://www.infinite-loop.dk/blog/2011/09/using-nsurlprotocol-for-injecting-test-data/)_

In earlier posts I described methods for [unit testing asynchronous network access](http://www.infinite-loop.dk/blog/2011/04/unittesting-asynchronous-network-access/) and how to [use mock objects](http://www.infinite-loop.dk/blog/2011/04/using-mock-objects-to-stabilize-unit-tests/) for further control of the scope of these unit tests. In this tutorial I'll present an alternative way of providing reliable test data by customizing the `NSURLProtocol` class in order to deliver static test data.

A few months ago [Gowalla](http://gowalla.com/) made the networking code used in their iPhone client available as open source on [GitHub](https://github.com/gowalla/AFNetworking). The AFNetworking library as it is called is a "_A delightful iOS networking library with NSOperations and block-based callbacks_". One of the things that first caught my eye was the built-in support for accessing JSON based services with just a few lines of code.

The simplicity of the AFNetworking interface inspired me to give it a test spin and write [ILBitly](https://github.com/InfiniteLoopDK/ILBitly) which provides an Objective C based wrapper for the [Bitly](http://bitly.com/) url shortening service. It's very easy to use AFNetworking and especially the JSON support that is accessed using a single class methods. Unfortunately this simplicity also makes it quite difficult to write self-contained unit and mock tests using OCMock. This is mainly because OCMock doesn't support mocking of class methods. My attempts with other techniques such as method swizzling wasn't successful either.

It wasn't until a few days ago when I noticed a [discussion on GitHub](https://github.com/gowalla/AFNetworking/issues/19) about how to properly mock the interface to AFNetworking. In the discussion [Adam Ernst](https://github.com/adamjernst) [suggested ](https://github.com/gowalla/AFNetworking/issues/19#issuecomment-1959592)to use a customized `NSURLProtocol` for doing the task. That finally gave me the missing clue on how to solve the testing problem.

[AdSense - blog banner]

### Subclassing NSURLProtocol

As mentioned above I didn't find any easy way to mock the interface to `AFJSONRequestOperation` in order to intercept the network access. So an alternative solution is to intercept the standard http protocol built into iOS. This is done by registering our own custom `NSURLProtocol` subclass capable of handling http requests: `ILCannedURLProtocol`. Since each registered protocol handler is asked in reverse order of registration our class will always be consulted before the standard classes.

The primary goal of `ILCannedURLProtocol` is to respond with a pre-loaded set of test data every time a http request is made. This way we'll be able to remove any outside influences when running the tests. We'll also be able to have the http request fail when we want it to fail. The interface for `ILCannedURLProtocol` is shown below:
    
    
    @interface ILCannedURLProtocol : [NSURLProtocol](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSURLProtocol_Class/)
    + (void)setCannedResponseData:([NSData](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSData_Class/)*)data;
    + (void)setCannedHeaders:([NSDictionary](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSDictionary_Class/)*)headers;
    + (void)setCannedStatusCode:(NSInteger)statusCode;
    + (void)setCannedError:([NSError](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSError_Class/)*)error;
    @end

It is not able to fully replace any http requests in its current form. For instance it is only designed to intercept GET requests. Neither does it support any type of authentication challenge/response. But it provides enough functionality to deliver the test data needed for testing `ILBitly` and probably other similar classes.

Basically each of the `setCannedXxx` methods just retains the object passed to it so the object can be returned again when needed by a http request. This also means that it is only able to serve one set of test data at a time.

There are a few additional methods that need to be implemented when subclassing `NSURLProtocol`. One of these is `canInitWithRequest:` This method is called every time a `NSURLRequest` is started in order to determine if that request is supported by the class. We'll use that to intercept the http GET requests:
    
    
    + (BOOL)canInitWithRequest:([NSURLRequest](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSURLRequest_Class/) *)request {
      // For now only supporting http GET
      return [[[request URL] scheme] isEqualToString:@"http"]
             && [[request HTTPMethod] isEqualToString:@"GET"];
    }

We also need to implement the `startLoading` method. This method is called once the appropriate protocol handler has been instantiated in order to service the request with data. Our method is able to either respond with a successful response or with an error depending on which of the canned data that has been set:
    
    
    - (void)startLoading {
      [NSURLRequest](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSURLRequest_Class/) *request = [self request];
      id client = [self client];
     
      if(gILCannedResponseData) {
        // Send the canned data
        [NSHTTPURLResponse](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSHTTPURLResponse_Class/) *response = 
          [[[NSHTTPURLResponse](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSHTTPURLResponse_Class/) alloc] initWithURL:[request URL]
                                      statusCode:gILCannedStatusCode
                                    headerFields:gILCannedHeaders 
                                     requestTime:0.0];
     
        [client URLProtocol:self didReceiveResponse:response
                cacheStoragePolicy:NSURLCacheStorageNotAllowed];
        [client URLProtocol:self didLoadData:gILCannedResponseData];
        [client URLProtocolDidFinishLoading:self];
     
        [response release];
      }
      else if(gILCannedError) {
        // Send the canned error
        [client URLProtocol:self didFailWithError:gILCannedError];
      }
    }

If you decide to use the above code for testing in your own project you must make sure not to accidentally include it in the production code for any apps targeted for the App Store. If you haven't already spotted the reason for this I'll lead your attention to the initializer for `NSHTTPURLResponse`. This is a private api obtained by running [class-dump](http://www.codethecode.com/projects/class-dump/) on the iOS 4.3 SDK. If you include this call in your production code you therefore risk it being rejected by Apple. There is also a slight chance Apple might decide to modify it in future updates of iOS. But as long as it's just used when running the unit tests everything should be fine.

Except for a few other methods which are basically empty that's all there is to it. Now we'll just need to register our custom class and load some canned data into it.

### Preparing the Unit Tests

The unit test class for `ILBitly` just includes a few instance variables:
    
    
    @interface ILBitlyTest : SenTestCase {
      ILBitly *bitly;
      id bitlyMock;
      BOOL done;
    }
    @end

The `bitly` variable contains an instance of the `ILBitly` code under test, `bitlyMock` holds the partial mock object for the `ILBitly` test, and `done` is used for signaling when the asynchronous calls have finished. These are explained more in details later.

Before every test case is executed the `setUp` method is automatically called allowing us to prepare things:
    
    
    - (void)setUp
    {
      [super setUp];
     
      // Init bitly proxy using test id and key - not valid for real use
      bitly = [[ILBitly alloc] initWithLogin:@"LOGIN" apiKey:@"KEY"];
      done = NO;
     
      [[NSURLProtocol](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSURLProtocol_Class/) registerClass:[ILCannedURLProtocol class]];
      [ILCannedURLProtocol setCannedStatusCode:200];
    }

We'll use this method to prepare a default test instance as well as registering the `ILCannedURLProtocol`. The parameters used for initializing the `ILBitly` instance are just placeholders which are passed on to the service requests. Since we'll be using static test data they have no real meaning except that we'll verify later on that they are actually passed on as expected.

In order to balance things out properly, we'll unregister our custom protocol as well as dispose of the test data after each test:
    
    
    - (void)tearDown
    {
      [[NSURLProtocol](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSURLProtocol_Class/) unregisterClass:[ILCannedURLProtocol class]];
      [ILCannedURLProtocol setCannedHeaders:nil];
      [ILCannedURLProtocol setCannedResponseData:nil];
      [ILCannedURLProtocol setCannedError:nil];
     
      [bitly release];
      bitlyMock = nil;
     
      [super tearDown];
    }

We'll also need to prepare some test data. This can easily be done by using `curl` to save the raw response from [bitly](http://code.google.com/p/bitly-api/wiki/ApiDocumentation) to a JSON file and loading that again for each test case as described in [this previous post](http://www.infinite-loop.dk/blog/2011/04/using-mock-objects-to-stabilize-unit-tests/).

### Putting it all Together

Finally we'll need to write some tests that verifies the `ILBitly` code. As an example one of the tests for the shortening service is shown below:
    
    
    - (void)testShorten {
      // Prepare the canned test result
      [ILCannedURLProtocol setCannedResponseData:[self cannedDataWithName:@"shorten"]];
      [ILCannedURLProtocol setCannedHeaders:
        [[NSDictionary](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSDictionary_Class/) dictionaryWithObject:@"application/json; charset=utf-8" 
                                    forKey:@"Content-Type"]];
     
      // Prepare the mock
      bitlyMock = [OCMockObject partialMockForObject:bitly];
      [NSURL](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSURL_Class/) *trigger = [[NSURL](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSURL_Class/) URLWithString:@"http://"];
      [[[bitlyMock expect] andReturn:[[NSURLRequest](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSURLRequest_Class/) requestWithURL:trigger]]
        requestForURLString:[OCMArg checkWithBlock:^(id url) {
          return [url isEqualToString:EXPECTED_REQUEST]; 
      }]];
     
      // Execute the code under test
      [bitly shorten:@"http://www.infinite-loop.dk/blog/" result:^([NSString](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSString_Class/) *result) {
        STAssertEqualObjects(result, @"http://j.mp/qA7S4Q", @"Unexpected short url");
        done = YES;
      } error:^([NSError](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSError_Class/) *err) {
        STFail(@"Shorten failed with error: %@", [err localizedDescription]);
        done = YES;
      }];
     
      // Verify the result
      STAssertTrue([self waitForCompletion:5.0], @"Timeout");
      [bitlyMock verify];
    }

In the first part the static test data is loaded into the test protocol.

Next a partial mock object is created for the `bitly` object. Its primary role is to intercept the internal call to `requestForURLString:` and setup an expectation that it's actually being called. Once that call is made it will verify that the expected url is requested and finally return an instance of `NSURLRequest`. That instance just contains enough of the basic url scheme in order to trigger the load of our custom protocol.

The code under test can now be executed as shown in the third part. Since the blocks may be called at any time after invoking the `shorten:result:error:` method `done` is set so we know when it has been called.

The final part of the code then waits for up to 5 seconds for `done` to be set as detailed in [a previous post](http://www.infinite-loop.dk/blog/2011/04/unittesting-asynchronous-network-access/). Finally `verify` is called on the mock object to ensure that the expected messages were received.

If we instead want to test for proper handling of errors we'll just have to replace the first part of the test method so it sets up error data and change the tests accordingly:
    
    
      [ILCannedURLProtocol setCannedError:
        [[NSError](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSError_Class/) errorWithDomain:NSURLErrorDomain
                            code:kCFURLErrorTimedOut
                        userInfo:nil]];

### Conclusion

As I've shown above it's possible to use `NSURLProtocol` for injecting predictable test data into unit and mock tests that would otherwise have been subject to external factors. It's also possible to extend these tests even further. For instance you could use this method for implementing various simulations of bad network conditions such as high latencies and low bandwidth. The possibilities are endless and I just hope that this post at least have provided some inspiration.

The `ILBitly` wrapper as well as the accompanying test classes used in this post are available on [GitHub](https://github.com/InfiniteLoopDK/ILBitly) along with a sample iPhone app that demonstrates some of the functionality.

**Update:** The `ILCannedURLProtocol` class is now included in the [ILTesting repository on Github](https://github.com/InfiniteLoopDK/ILTesting).

Comments and suggestions are welcome as always.
