# Unit Testing Asynchronous Network Access

_Captured: 2015-12-06 at 01:23 from [www.infinite-loop.dk](http://www.infinite-loop.dk/blog/2011/04/unittesting-asynchronous-network-access/)_

In this post I'll go through one way of adding unit tests to code that fetch data from the internet through asynchronous threaded callbacks. As an example I'll use the ILGeoNames library described in the [previous post](http://www.infinite-loop.dk/blog/2011/02/reverse-geocoding-without-googles-restrictions/). More specifically I'll show how to write unit tests for `findNearbyPlaceNameForLatitude:longitude:` in the `ILGeoNamesLookup` class.

We're faced with three problems that prevent the normal straight-forward methods for writing unit tests:

  * **Asynchronous code** - the result is passed back by the use of a delegate method.
  * **Threaded execution** - the code under test is spawning off a new worker thread.
  * **Network access** - the result is fetched from a remote internet server.

The asynchronous code and threaded execution prevents the use of a normal linear flow in the unit test code and the network access adds a lot of uncertainty and latency to the tests. We want our unit tests to be fast and stable and not fail just because some remote server or internet provider have a problem from time to time.

Fortunately there are a few fairly straight forward solutions to these problems.

[AdSense - blog banner]

### Creating the UnitTest Target

First we'll need to create a new UnitTest target to the SampleApp Xcode project. This target will host all the unit tests, etc. so the production code is not touched or modified by the tests:

Select the top level SampleApp project in the Xcode project navigator and click the "Add Target" button. This pops up a small wizard for creating the new target:

In the first window select the "Cocoa Touch Unit Testing Bundle" target which is found in the iOS - Other section. 

Click "Next" to bring up the second window.

In the second window enter "UnitTest" as the product name. We'll just enter something in the Company Identifier. It's not that important since the test bundle is never going to be shipped with the product. 

Click "Finished" to create the new target.

Xcode have now created a new UnitTest target and added a couple of default files to the project under a new UnitTest group. The file structure should be something like this:

![UnitTest file structure](http://www.infinite-loop.dk/wp/wp-content/uploads/2011/04/DefaultUnitTestFileStructure.png)

> _We're now ready to run the default unit test provided by Xcode._

From the Scheme popup menu select the UnitTest target and make sure it is using the iPhone simulator. Next select "Product" -> "Test" from the menu. This compiles and runs the unit test. It should fail with the following message:

![Default unit test fails](http://www.infinite-loop.dk/wp/wp-content/uploads/2011/04/DefaultUnitTestFail.png)

> _This is as expected because we're still using the default unit test provided by Xcode. This file only contains a single test that is set to fail on purpose:_
    
    
    - (void)testExample
    {
        STFail(@"Unit tests are not implemented yet in UnitTest");
    }

### Preparing the Unit Test Class

In order to define some real unit tests we'll start by renaming the default UnitTest.m and .h files to ILGeoNamesLookupTest.m and .h respectively. It is not strictly necessary to name the unit test files after the code being tested, but it will make it a lot easier to later match the test code with the real code. The same goes for the class name for the unit test.

One of the tricky parts with testing `ILGeoNames` is that it returns the results through delegate methods. Additionally it spawns off a new thread when fetching the data from the internet.

In order to deal with this we first need to implement the various delegate methods in the test class. The following is added to the ILGeoNamesLookupTest.h file, replacing the default `UnitTest` class definition:

In the ILGeoNamesLookupTest.m file we start by adding the following, replacing the default `UnitTest` class implementation:
    
    
    @implementation GeoNamesLookupTest
     
    - (void)setUp {
        parser = [[GeoNamesLookup alloc] init];
        parser.delegate = self;
        searchError = nil;
        searchResult = nil;
        done = NO;
    }
     
    - (void)tearDown {
        [parser release];
        [searchError release];
        [searchResult release];
    }
     
    @end

The `setUp` method is automatically called before each test method is called. It is used to prepare the needed setup of our test variables, including creation of the actual `ILGeoNamesLookup` parser and setting up the test class as a delegate of it. Likewise the `tearDown` message is automatically called after the test method is finished. It is used for cleaning up the test environment.

Next we'll add the delegate methods that are called with the search result or, in case of error, the reason for the error:
    
    
    - (void)geoNamesLookup:(GeoNamesLookup *)handler didFailWithError:([NSError](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSError_Class/) *)error {
        searchError = [error retain];
        done = YES;
    }
     
    - (void)geoNamesLookup:(GeoNamesLookup *)handler didFindGeoNames:([NSArray](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSArray_Class/) *)geoNames totalFound:(NSUInteger)total {
        searchResult = [geoNames retain];
        done = YES;
    }

Finally we'll add the following method which will take care of the synchronization between the unit test code and the asynchronous code under test:
    
    
    - (BOOL)waitForCompletion:(NSTimeInterval)timeoutSecs {
        [NSDate](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSDate_Class/) *timeoutDate = [[NSDate](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSDate_Class/) dateWithTimeIntervalSinceNow:timeoutSecs];
     
        do {
            [[[NSRunLoop](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSRunLoop_Class/) currentRunLoop] runMode:NSDefaultRunLoopMode beforeDate:timeoutDate];
            if([timeoutDate timeIntervalSinceNow] < 0.0)
                break;
        } while (!done);
     
        return done;
    }

When called this method will await the callback from the delegate methods signaled through the `done` variable. In order to avoid blocking the main thread, it will just spin the run loop. If the delegate methods are never called it will return when the timeout occurs.

### Defining and Running the Unit Tests

We're now ready to add the actual unit tests. Let's use the location of a famous company as an example. The code under test is executed using this line of code:
    
    
    [parser findNearbyPlaceNameForLatitude:37.33164146 longitude:-122.0301890];

This will call the geonames.org web service and hopefully return the expected result at some time in a not-so-distant future. We'll wait for the call to complete - one way or the other - by calling the `waitForCompletion:` method with a timeout value of 90 seconds. This should be more than enough for even slow internet connections, otherwise it will cause test to fail to ensure it isn't stuck forever.

The complete unit test is shown below including validation of a few of the returned values:
    
    
    -(void) testAppleComputerHeadquarters {
        // Perform code under test
        [parser findNearbyPlaceNameForLatitude:37.33164146 longitude:-122.0301890];
     
        // Validate result
        STAssertTrue([self waitForCompletion:90.0], @"Failed to get any results in time");
        STAssertNotNil(searchResult, @"Didn't expect an error");
        [NSDictionary](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSDictionary_Class/) *firstResult = [searchResult objectAtIndex:0];
        STAssertNotNil(firstResult, @"Expected at least one result");
        STAssertEqualObjects([firstResult objectForKey:@"name"],
            @"Apple Computer Headquarters", @"Unexpected place name found");
        STAssertEqualObjects([firstResult objectForKey:@"adminName1"],
            @"California", @"Unexpected admin name found");
    }

Running the test now should hopefully be successful and provide some output similar to this:
    
    
    Test Suite 'ILGeoNamesLookupTest' started at 2011-04-07 18:34:55 +0000
    Test Case '-[ILGeoNamesLookupTest testAppleComputerHeadquarters]' started.
    Test Case '-[ILGeoNamesLookupTest testAppleComputerHeadquarters]' passed (3.681 seconds).
    Test Suite 'ILGeoNamesLookupTest' finished at 2011-04-07 18:34:59 +0000.
    Executed 1 test, with 0 failures (0 unexpected) in 3.681 (3.681) seconds

Depending on the speed of the internet connection and the current load of the geonames.org servers the test may take some time to complete. It is also possible it will fail due to some external error which have nothing to do with the code being tested.

In the [next post](http://www.infinite-loop.dk/blog/2011/04/using-mock-objects-to-stabilize-unit-tests/) I'll shown one way of using OCMock to prevent these kind of random errors which are unrelated to the code being tested.

The Xcode project used in this post as well as the complete unit tests can be downloaded from [GitHub](http://github.com/InfiniteLoopDK/ILGeoNames).
