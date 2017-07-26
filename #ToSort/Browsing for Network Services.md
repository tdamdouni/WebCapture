# Browsing for Network Services

_Captured: 2016-03-19 at 11:19 from [developer.apple.com](https://developer.apple.com/library/mac/documentation/Networking/Conceptual/NSNetServiceProgGuide/Articles/BrowsingForServices.html)_

[Next](https://developer.apple.com/library/mac/documentation/Networking/Conceptual/NSNetServiceProgGuide/Articles/ResolvingServices.html)[Previous](https://developer.apple.com/library/mac/documentation/Networking/Conceptual/NSNetServiceProgGuide/Articles/PublishingServices.html)

An important part of Bonjour is the ability to browse for services on the network. This chapter describes how to use the `NSNetServiceBrowser` class to discover Bonjour network services.

## The Browsing Process

The `NSNetServiceBrowser` class provides methods for browsing for available Bonjour network services.

Because of the possible delays associated with network traffic, `NSNetServiceBrowser` objects perform browsing asynchronously by registering with the default run loop. Browsing results are returned to your app through delegate methods. To handle results from an `NSNetServiceBrowser` object, you must assign it a delegate.

To Browse for Bonjour network services, your app must perform three steps:

  1. Initialize an `NSNetServiceBrowser` instance and assign a delegate to the object.

  2. Begin a search for services of a specific type in a given domain.

  3. Handle search results and other messages sent to the delegate object.

## Initializing the Browser and Starting a Search

To initialize an `NSNetServiceBrowser` object, use the `init` method. This sets up the browser and adds it to the current run loop. If you want to use a run loop other than the current one, use the `removeFromRunLoop:forMode:` and `scheduleInRunLoop:forMode:` methods.

To begin the browsing process, use the `searchForServicesOfType:inDomain:` method. The service type expresses both the application-layer protocol (FTP, HTTP, and so on.) and the transport protocol (TCP or UDP). The format is as described in [Domain Naming Conventions](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/NetServices/Articles/domainnames.html)--for example, `_printer._tcp` for an LPR printer over TCP.

The domain parameter specifies the DNS domain in which the browser performs its search. There are four common ways to use this parameter:

  * To limit searches to the local network (for a chat program, for example), pass `@"local"` to search only the local LAN.

  * For limited wide-area support, pass `@""` to search the system's default search domains. To avoid confusion, be sure to display each service's domain in your user interface.

  * For full wide-area support, use the `[searchForBrowsableDomains](https://developer.apple.com/library/mac/documentation/Cocoa/Reference/Foundation/Classes/NSNetServiceBrowser_Class/index.html)` method to obtain a list of browsable domains, as described in [Browsing for Domains](https://developer.apple.com/library/mac/documentation/Networking/Conceptual/NSNetServiceProgGuide/Articles/BrowsingForDomains.html). Then present a user interface that allows the user to choose the domain to browse. When the user chooses a domain, browse only in that domain.

  * To provide maximum flexibility for power users, provide a text field in which the user can specify an arbitrary domain name to browse.

To stop a search, use the `stop` method. Then perform any necessary cleanup in the `netServiceBrowserDidStopSearch:` delegate callback.

Listing 3-1 demonstrates how to browse for Bonjour network services with `NSNetServiceBrowser`. The code initializes the object, assigns a delegate, and begins a search for a hypothetical music service type, `_music._tcp`, on the local network. For a good example of service browsing, see the _[PictureSharingBrowser](https://developer.apple.com/library/mac/samplecode/PictureSharingBrowser/Introduction/Intro.html)_ sample code project in the Mac Developer Library.

**Listing 3-1** Browsing for Bonjour network services
    
    
    id delegateObject; // Assume this exists.
    
    
    NSNetServiceBrowser *serviceBrowser;
    
    
    serviceBrowser = [[NSNetServiceBrowser alloc] init];
    
    
    [serviceBrowser setDelegate:delegateObject];
    
    
    [serviceBrowser searchForServicesOfType:@"_music._tcp" inDomain:@""];

## Implementing Delegate Methods for Browsing

`NSNetServiceBrowser` returns all browsing results to its delegate. If you are using the class to browse for services, your delegate object should implement the following methods:

  * `netServiceBrowserWillSearch:`

  * `netServiceBrowserDidStopSearch:`

  * `netServiceBrowser:didNotSearch:`

  * `netServiceBrowser:didFindService:moreComing:`

  * `netServiceBrowser:didRemoveService:moreComing:`

The `netServiceBrowserWillSearch:` method notifies the delegate that a search is commencing. You can use this method to update your user interface to reflect that a search is in progress. When browsing stops, the delegate receives a `netServiceBrowserDidStopSearch:` message. In that delegate method, you can perform any necessary cleanup.

If the delegate receives a `netServiceBrowser:didNotSearch:` message, the search failed for some reason. The delegate method should extract the error information from the dictionary with the `NSNetServicesErrorCode` key and handle the error accordingly. For a list of possible errors, see [NSNetService](https://developer.apple.com/library/mac/documentation/Cocoa/Reference/Foundation/Classes/NSNetService_Class/index.html).

You track services with the `netServiceBrowser:didFindService:moreComing:` and `netServiceBrowser:didRemoveService:moreComing:` methods, which indicate that a service has become available or has shut down. The `moreComing` parameter indicates whether more results are on the way. If this parameter is `[YES](https://developer.apple.com/library/mac/documentation/Cocoa/Reference/ObjCRuntimeRef/index.html)`, delay updating any user interface elements until the method is called with a `moreComing` parameter of `[NO](https://developer.apple.com/library/mac/documentation/Cocoa/Reference/ObjCRuntimeRef/index.html)`.

**Important:** A `moreComing` value of `[NO](https://developer.apple.com/library/mac/documentation/Cocoa/Reference/ObjCRuntimeRef/index.html)` does _not_ indicate that browsing has finished. It indicates that your app has been provided with the complete state of the world as Bonjour understands it up to that point in time. There is still a chance that more services will become available as new services appear on the network or as unusually slow devices respond to requests.

Be sure to retain the `didFindService` parameter before trying to resolve it. Otherwise, you risk the object becoming deallocated. If you want a list of available services, you must maintain your own array based on the information provided by delegate methods.

**Note:** If you specify the `@""` search domain, you may receive search results with the same name in multiple domains. For example, you might get `"Foo._music._tcp.local."` and `"Foo._music._tcp.arbitraryusername.me.com."`. To avoid causing confusion, consider designing your user interface so that it restricts the results to the local domain, groups the results by domain, or shows the domain information in a separate column.

Listing 3-2 shows the interface for a class that responds to the `NSNetServiceBrowser` delegate methods required for service browsing, and Listing 3-3 shows its implementation. You may want to use this code as a starting point for your service browsing code.

**Listing 3-2** Interface for an NSNetServiceBrowser delegate object used when browsing for services
    
    
    #import <Foundation/Foundation.h>
    
    
    @interface NetServiceBrowserDelegate : NSObject <NSNetServiceBrowserDelegate>
    
    
    {
    
    
    }
    
    
    @property BOOL searching;
    
    
    @property (strong,atomic) NSMutableArray *services;
    
    
    // Other methods
    
    
    - (void)handleError:(NSNumber *)error;
    
    
    - (void)updateUI;
    
    
    @end

**Listing 3-3** Implementation for an NSNetServiceBrowser delegate object used when browsing for services
    
    
    #import "NetServiceBrowserDelegate.h"
    
    
    @implementation NetServiceBrowserDelegate
    
    
    - (id)init
    
    
    {
    
    
        self = [super init];
    
    
        if (self) {
    
    
            self.services = [NSMutableArray arrayWithCapacity: 0];
    
    
            self.searching = NO;
    
    
        }
    
    
        return self;
    
    
    }
    
    
    // Sent when browsing begins
    
    
    - (void)netServiceBrowserWillSearch:(NSNetServiceBrowser *)browser
    
    
    {
    
    
        self.searching = YES;
    
    
        [self updateUI];
    
    
    }
    
    
    // Sent when browsing stops
    
    
    - (void)netServiceBrowserDidStopSearch:(NSNetServiceBrowser *)browser
    
    
    {
    
    
        self.searching = NO;
    
    
        [self updateUI];
    
    
    }
    
    
    // Sent if browsing fails
    
    
    - (void)netServiceBrowser:(NSNetServiceBrowser *)browser
    
    
            didNotSearch:(NSDictionary *)errorDict
    
    
    {
    
    
        self.searching = NO;
    
    
        [self handleError:[errorDict objectForKey:NSNetServicesErrorCode]];
    
    
    }
    
    
    // Sent when a service appears
    
    
    - (void)netServiceBrowser:(NSNetServiceBrowser *)browser
    
    
            didFindService:(NSNetService *)aNetService
    
    
            moreComing:(BOOL)moreComing
    
    
    {
    
    
        [self.services addObject:aNetService];
    
    
        NSLog(@"Got service %p with hostname %@\n", aNetService,
    
    
            [aNetService hostName]);
    
    
        if(!moreComing)
    
    
        {
    
    
            [self updateUI];
    
    
        }
    
    
    }
    
    
    // Sent when a service disappears
    
    
    - (void)netServiceBrowser:(NSNetServiceBrowser *)browser
    
    
            didRemoveService:(NSNetService *)aNetService
    
    
            moreComing:(BOOL)moreComing
    
    
    {
    
    
        [self.services removeObject:aNetService];
    
    
        if(!moreComing)
    
    
        {
    
    
            [self updateUI];
    
    
        }
    
    
    }
    
    
    // Error handling code
    
    
    - (void)handleError:(NSNumber *)error
    
    
    {
    
    
        NSLog(@"An error occurred. Error code = %d", [error intValue]);
    
    
        // Handle error here
    
    
    }
    
    
    // UI update code
    
    
    - (void)updateUI
    
    
    {
    
    
        if(self.searching)
    
    
        {
    
    
            // Update the user interface to indicate searching
    
    
            // Also update any UI that lists available services
    
    
        }
    
    
        else
    
    
        {
    
    
            // Update the user interface to indicate not searching
    
    
        }
    
    
    }
    
    
    @end

[Next](https://developer.apple.com/library/mac/documentation/Networking/Conceptual/NSNetServiceProgGuide/Articles/ResolvingServices.html)[Previous](https://developer.apple.com/library/mac/documentation/Networking/Conceptual/NSNetServiceProgGuide/Articles/PublishingServices.html)
