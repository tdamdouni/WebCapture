# How to Detect Whether an Application Is Running Inside a UI Test Environment

_Captured: 2015-12-03 at 09:59 from [macoscope.com](http://macoscope.com/blog/how-to-detect-whether-an-application-is-running-inside-a-ui-test-environment/)_

![blog_img](http://cdn.macoscope.com/blog/wp-content/uploads/2015/11/blog_img.jpeg)

UI tests are here to stay, so we are all moving towards using them in our applications. Although, in general, an application shouldn't know if it's running inside a UI test, there are reports in the wild of `UIRefreshControl` causing an error during UITesting. Namely:
    
    
    t = 14.84s   Synthesize event
    t = 15.25s   Wait for app to idle
    t = 45.45s   Assertion Failure: UI Testing Failure - App failed to quiesce within 30.0s
    

This happens in various scenarios, especially if we call `[UIRefreshControl beginRefreshing]` when `UIRefreshControl` is directly added to `UITableView` (instead of `UITableViewController`) and if it doesn't have space to expand.

We couldn't use `UITableViewController`, so we decided to make our application aware of whether it is being run inside a UI test environment and use it at least until Apple fixes the problem with `UIRefreshControl`.

First, we tried to use one widely known technique to check whether an app is being unit-tested:
    
    
    BOOL IsRunningTests()
    {
        NSDictionary *environmentDictionary = [[NSProcessInfo processInfo] environment];
        NSString *injectBundle = environmentDictionary[@"XCInjectBundle"];
    
        return [[injectBundle pathExtension] isEqualToString:@"xctest"];
    }
    

But it turned out that `XCInjectBundle` doesn't get injected into the environment inside UI tests (at least when directly running the test). Our next approach was to modify the environment in Test Scheme Settings, but those aren't forwarded to the application either.

Finally, we decided to take a look at `XCUIApplication`. This is part of the UI Testing framework and is described as a "_proxy for an application._" `XCUIApplication` contains the property `launchEnvironment` which can be used to inject environment variables into the tested application.

In order to notify the application that it is being run inside a test, you can modify the app's launchEnvironment to contain some known key:
    
    
    - (void)setUp { 
       [super setUp];
    
       XCUIApplication *app = [[XCUIApplication alloc] init];
       NSMutableDictionary *launchEnv = [app.launchEnvironment mutableCopy];
       launchEnv[@"MCSUITestEnvironment"] = @"YES";
       app.launchEnvironment = launchEnv;
       [app launch];
    }

And then check for the existence of this key using standard practices:
    
    
    BOOL IsRunningUITests() {
       NSDictionary *environmentDictionary = [[NSProcessInfo processInfo] environment];
       return (environmentDictionary[@"MCSUITestEnvironment"] != nil);
    }
    

This is a hackish solution, but sometimes we are forced to use these sorts of approaches by system bugs and other external constraints.
