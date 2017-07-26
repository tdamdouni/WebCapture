# Using Mock Objects to Stabilize Unit Tests

_Captured: 2015-12-06 at 01:17 from [www.infinite-loop.dk](http://www.infinite-loop.dk/blog/2011/04/using-mock-objects-to-stabilize-unit-tests/)_

In the [previous post](http://www.infinite-loop.dk/blog/2011/04/unittesting-asynchronous-network-access/) I presented one way of implementing unit tests for iOS code that access the internet asynchronously. In this post I'll go through how to use Mock Objects to further stabilize and optimize these tests. If you're unfamiliar with the concept of Mock Objects I'll suggest you first read [A Brief History of Mock Objects](http://www.mockobjects.com/2009/09/brief-history-of-mock-objects.html) or this [Wikipedia article](http://en.wikipedia.org/wiki/Mock_object).

As mentioned in the [previous post](http://www.infinite-loop.dk/blog/2011/04/unittesting-asynchronous-network-access/), it is possible that the unit tests may fail due to some outside factor even though our code is working perfectly. This could for instance be an internet service that is temporarily down or malfunctioning, or it could be your own ISP that have [some problems](http://technabob.com/blog/2011/04/07/little-old-lady-kills-internet/).

By replacing the code that access the internet by Mock Objects that mimic the same behavior the unit tests can be made completely independent of external factors. Additionally by mocking the internet access the unit tests will also execute substantially faster . A speed increment by a factor 1000 or more is not unusual.

In Test Driven Development the complete Unit Test suite should ideally be executed as part of your normal compile setup. This means that execution times in the order of seconds for just a single test is an absolutely no-go. As Noel Llopis states in [this blog post](http://gamesfromwithin.com/whats-your-pain-threshold), the total execution time for the full test suite of your entire project should be less than 2 seconds. Whether the limit is 1, 2 or maybe even 3 seconds is not important, but the point is that it should be so fast that it doesn't contribute to the perceived build time.

In the following I'll show how to mock the network access code for ILGeoNames using [OCMock](http://www.mulle-kybernetik.com/software/OCMock/) by [Mulle Kybernetik](http://www.mulle-kybernetik.com/en/index.html).

[AdSense - blog banner]

### Setting up the Xcode project

OCMock comes both as a framework and as a static library in the same download. The static library can be used both with logic tests and application testes whereas the framework only supports logic tests. I have chosen to use the static library in case I'll later need to add some application tests.

After downloading the latest version of OCMock it is placed next to the SampleApp folder. In order to be able to use the OCMock library, we also need to make the library and headers available in the Xcode project. This is done by adding a few parameters to the build settings of the UnitTest target:

![OCMock build settings](http://www.infinite-loop.dk/wp/wp-content/uploads/2011/04/OCMock-build-settings1-300x40.png)

> _Preparing the Test Data_

First we'll need to add a few extra variables to the ILGeoNamesLookupTest to hold the mock object as well as the data it will return:
    
    
    @interface ILGeoNamesLookupTest : SenTestCase  {
        ...
        id mockParser;
        [NSData](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSData_Class/) *cannedResult;
    }

The `cannedResult` variable is preloaded with the test data before executing each test by calling the method below. This will cause the named JSON file to be loaded from the UnitTest.bundle and stored so it can be returned later by the Mock Object:
    
    
    - (void)loadCannedResultWithName:([NSString](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSString_Class/)*)cannedName {
        cannedResult = [[[NSData](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSData_Class/) alloc] initWithContentsOfFile:
                           [[[NSBundle](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSBundle_Class/) bundleForClass:[self class]]
                               pathForResource:cannedName ofType:@"json"]];
        STAssertNotNil(cannedResult, @"Failed to load canned result '%@'", cannedName);
    }

We'll also need to grab some test data to return. To make sure no formatting, etc. is applied to the data, we'll just grab it by firing up `curl` in the Terminal:
    
    
    $ curl "http://api.geonames.org/findNearbyJSON?lat=37.33164146&lng=-122.03018903&style=FULL&username=unittest" -o AppleComputerHeadquaters.json

The "AppleComputerHeadquaters.json" file is then added to the UnitTest target so it can be loaded during execution of the tests.

### Deciding where to Mock the Interface

Before we start mocking the interfaces, let's first take a look at what's going on inside the code being tested.
    
    
    - (void)findNearbyPlaceNameForLatitude:(double)latitude longitude:(double)longitude {
        [NSString](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSString_Class/) *urlString;
     
        // Request formatted according to http://www.geonames.org/export/web-services.html#findNearby
        urlString = [[NSString](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSString_Class/) stringWithFormat:kILGeoNamesFindNearbyURL, latitude, longitude, userID];
        [self sendRequestWithURLString:urlString];
    }
     
    - (void)sendRequestWithURLString:([NSString](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSString_Class/)*)urlString {
        // Detach a thread to perform the request
        [[NSThread](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSThread_Class/) detachNewThreadSelector:@selector(threadedRequestWithURLString:)
                                 toTarget:self
                               withObject:urlString];
    }

Basically `findNearbyPlaceNameForLatitude:longitude:` method just constructs a `urlString` to be passed to the worker thread through the internal `sendRequestWithURLString:` method.  
You may wonder why the worker thread is not spawned directly from within the `﻿findNearbyPlaceNameForLatitude:longitude:` method, but as I will show shortly this makes it easier to mock the internet access.

Inside the `threadedRequestWithURLString:` method the actual network access is taking place:
    
    
    - (void)threadedRequestWithURLString:([NSString](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSString_Class/)*)urlString {
        [NSAutoreleasePool](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSAutoreleasePool_Class/) *downloadPool = [[[NSAutoreleasePool](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSAutoreleasePool_Class/) alloc] init];
        [NSURLRequest](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSURLRequest_Class/) *request;
     
        @synchronized(self) {
            done = NO;
            self.dataBuffer = [[NSMutableData](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSMutableData_Class/) data];
     
            // Create the request
            request = [[NSURLRequest](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSURLRequest_Class/) requestWithURL:[[NSURL](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSURL_Class/) URLWithString:urlString]
                                       cachePolicy:NSURLRequestReloadIgnoringLocalCacheData
                                   timeoutInterval:60.0];
     
            // Create the connection with the request and start loading the data
            dataConnection = [[[NSURLConnection](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSURLConnection_Class/) alloc] initWithRequest:request
                                                             delegate:self];
        }	
     
        // Just sit spinning in the run loop until all is done
        if(self.dataConnection) {
            [self performSelectorOnMainThread:@selector(downloadStarted)
                                   withObject:nil
                                waitUntilDone:NO];
            while (!done) {
                [[[NSRunLoop](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSRunLoop_Class/) currentRunLoop] runMode:NSDefaultRunLoopMode
                                         beforeDate:[[NSDate](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSDate_Class/) dateWithTimeIntervalSinceNow:5.0]];
            }
        }
     
        // Release resources used only in this thread
        @synchronized(self) {
            self.dataBuffer = nil;
            self.dataConnection = nil;
        }
     
        [downloadPool release];
    }

We could mock the individual interfaces used by the `threadedRequestWithURLString:` method (i.e. `NSURLRequest` and `NSURLConnection`) and thus provide Mock Objects that mimic the real interfaces as closely as possible. This would however require that we also deal with runloops, autorelease pools, etc.

We're not really interested in how `NSURLRequest` and `NSURLConnection` behaves. What we're really interested in is how our code reacts to the delegate callbacks from these classes.

The ideal place to mock the interface therefore seems to be the `sendRequestWithURLString:` method and the `NSURLConnectionDelegate` callbacks.

### Partially Mocking the Interface

In order to provide the test data upon calling `sendRequestWithURLString:` we'll create the following method which will first validate the URL constructed previously. Then it will return the canned result to the code being tested through the `NSURLConnectionDelegate` methods:
    
    
    - (void)returnCannedResultForRequest:([NSString](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSString_Class/)*)request {
        // Validate request
        STAssertNotNil(request, @"Invalid request");
        [NSURL](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSURL_Class/) *url = [[NSURL](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSURL_Class/) URLWithString:request];
        STAssertNotNil(url, @"Failed to make request '%@' into url", request);
        STAssertEqualObjects([url scheme], @"http", @"Invalid request scheme");
        STAssertEqualObjects([url host], @"api.geonames.org", @"Invalid request host");
        STAssertEqualObjects([url path], @"/findNearbyJSON", @"Invalid request path");
        [NSArray](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSArray_Class/) *params = [[url query] componentsSeparatedByString:@"&"];
        STAssertTrue([params containsObject:@"username=unittest"], @"Username not set correctly in request");
     
        // Return canned result or error
        if(cannedResult) {
            parser.dataBuffer = [[NSMutableData](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSMutableData_Class/) data];
            [parser connection:nil didReceiveData:cannedResult];
            [parser connectionDidFinishLoading:nil];
            parser.dataBuffer = nil;
        }
        else {
            [parser connection:nil didFailWithError:cannedError];
        }
    }

Next we'll create a partial Mock Object for the `ILGeoNamesLookup` code under test. This mock object will intercept the call to `sendRequestWithURLString:` and instead call the stub method which again will validate the request and finally return the canned result which have been loaded in the first line of the test case:
    
    
    -(void) testAppleComputerHeadquarters {
        // Mock the ILGeoNamesLookup so no actual network access is performed
        [self loadCannedResultWithName:@"AppleComputerHeadquaters"];
        mockParser = [OCMockObject partialMockForObject:parser];
        [[[mockParser stub] andCall:@selector(returnCannedResultForRequest:)
                           onObject:self]
            sendRequestWithURLString:[OCMArg any]];
     
        // Perform code under test
        [parser findNearbyPlaceNameForLatitude:37.33164146
                                     longitude:-122.0301890];
        // Validate result
        ...
    }

### Running the Test

When we now run the test we should hopefully see a result similar to the one below:
    
    
    Test Suite 'ILGeoNamesLookupTest' started at 2011-04-18 18:44:34 +0000
    Test Case '-[ILGeoNamesLookupTest testAppleComputerHeadquarters]' started.
    Test Case '-[ILGeoNamesLookupTest testAppleComputerHeadquarters]' passed (0.001 seconds).
    Test Suite 'ILGeoNamesLookupTest' finished at 2011-04-18 18:44:34 +0000.
    Executed 1 test, with 0 failures (0 unexpected) in 0.001 (0.002) seconds

Not only did our test pass without failures during this run, but it will continue to succeed every time we run it unless we break something in our own code. But what's equally important is that the test executed more than 3000 times faster than when we ran the same test using real internet access.

This means that by using Mock Objects we have ensured that our tests are completely reliable every time we run them and so fast that there aren't really any excuse for not running them every time we make some changes to the code.

But even though Mock Objects provide a way of improving your unit tests they are not able to fully replace functional and integration tests. They will make these tests easier by minimizing what is left to be tested by human (or monkey) testers.

In the above example we also removed the unit testing of the actual network access. This means that this code should instead be added to our list of things to check during integration and functional testing. Otherwise we might instead have created a loophole for bugs to creep through.

The Xcode project used in this post as well as the complete unit tests can be downloaded from [GitHub](http://github.com/InfiniteLoopDK/ILGeoNames).
