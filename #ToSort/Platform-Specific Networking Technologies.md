# Platform-Specific Networking Technologies

_Captured: 2016-02-20 at 21:42 from [developer.apple.com](https://developer.apple.com/library/ios/documentation/NetworkingInternetWeb/Conceptual/NetworkingOverview/Platform-SpecificNetworkingTechnologies/Platform-SpecificNetworkingTechnologies.html)_

## iOS Requires You to Handle Backgrounding and Specify Cellular Usage Policies

This section describes networking technologies and techniques that are specific to iOS, including information about captive network support, backgrounding, and making Wi-Fi-only connections.

### Restrict Cellular Networking Correctly

There are two ways to prevent connections from being sent over a cellular network. Which method you use depends on your app's requirements and goals.

The `[kSCNetworkReachabilityFlagsIsWWAN](https://developer.apple.com/library/ios/documentation/SystemConfiguration/Reference/SCNetworkReachabilityRef/index.html)` flag in the `SCNetworkReachability` API tells you which interface will _probably_ be used if your app connects to the specified host. However, this flag can be misleading because:

  * The Wi-Fi signal could disappear after your app checks reachability, but before it connects.

  * Different hosts may be reachable over different interfaces. You cannot trust a reachability check for one host to be valid for a different host (and you cannot trust a reachability check for a fake IP address, such as `0.0.0.0`).

  * Different IP addresses for the _same_ host may be reachable over different interfaces. If a remote host has both IPv4 and IPv6 addresses, iOS typically attempts to connect to both addresses simultaneously, then uses whichever connection was established first and cancels the other connection attempt. If the user's cellular network provides IPv6 and the user's Wi-Fi network doesn't, the connection could be made either using cellular or Wi-Fi, depending entirely on which network connects more quickly.

**Note:** In iOS 6, the cellular network is never used as the primary interface for IPv4 or IPv6 if Wi-Fi is used as the primary interface for either IPv4 or IPv6, so this particular case is specific to iOS 5 and earlier.

If your app must strictly avoid sending data over a cellular connection, your app must declare that policy restriction explicitly when making the connection. If you are using reachability in an advisory fashion (for example, to warn the user before uploading a large movie over the cellular network), you should also consider making the connection with cellular connectivity disabled. Then, if the connection fails, ask the user for permission to send data over the cellular network and try again without those flags.

At the Foundation layer, you can use the `[setAllowsCellularAccess:](https://developer.apple.com/library/ios/documentation/Cocoa/Reference/Foundation/Classes/NSMutableURLRequest_Class/index.html)` method on `[NSMutableURLRequest](https://developer.apple.com/library/ios/documentation/Cocoa/Reference/Foundation/Classes/NSMutableURLRequest_Class/index.html)` to specify whether a request can be sent over a cellular connection. You can also use the `[allowsCellularAccess](https://developer.apple.com/library/ios/documentation/Cocoa/Reference/Foundation/Classes/NSURLRequest_Class/index.html)` to check the current value.

At the Core Foundation layer, you can achieve the same thing by setting the `[kCFStreamPropertyNoCellular](https://developer.apple.com/library/ios/documentation/CoreFoundation/Reference/CFSocketStreamRef/index.html)` property before opening a stream obtained from the CFSocketStream or CFHTTPStream APIs.

In older versions of iOS, you can continue to use the `[kSCNetworkReachabilityFlagsIsWWAN](https://developer.apple.com/library/ios/documentation/SystemConfiguration/Reference/SCNetworkReachabilityRef/index.html)` as a best-effort way of determining whether traffic will be sent over a cellular connection, but you should be aware of its limitations.

### Handle Backgrounding Correctly

Your app may be suspended when it goes into the background, which means that it can no longer handle network traffic. In some cases, existing connections may even close while your app is suspended. To learn techniques for coping with backgrounding, read _[Networking and Multitasking](https://developer.apple.com/library/ios/technotes/tn2277/_index.html)_.

### Register VoIP Sockets Correctly

The `NSInputStream`, `NSOutputStream`, `CFStream`, and `NSURLConnection` APIs have built-in support for Voice over Internet Protocol (VoIP) communication. This support allows you to register a TCP connection as being for VoIP purposes so that if your app gets suspended, data arriving on this socket causes your app to be resumed.

For more information, read Implementing a VoIP Application in _[App Programming Guide for iOS](https://developer.apple.com/library/ios/documentation/iPhone/Conceptual/iPhoneOSProgrammingGuide/Introduction/Introduction.html)_.

### Register for Captive Network Support

A captive network is a Wi-Fi network that doesn't provide Internet access until the user performs some action, such as logging in, specifying payment, or agreeing to terms and conditions. Captive networks are common in public areas, such as airports and hotels.

When a user joins a captive network, Captive Network Support typically provides a web sheet that allows the user to authenticate with the network. If your application registers the SSID of the captive network, however, the web sheet is suppressed, and the user can complete authentication in your application.

For more information, read _[CaptiveNetwork Reference](https://developer.apple.com/library/ios/documentation/SystemConfiguration/Reference/CaptiveNetworkRef/index.html)_.

## OS X Lets You Make Systemwide Changes

The following sections explain where to learn about working with network interfaces in OS X and developing network kernel extensions that extend the networking stack.

### Develop Network Setup Applications

If you want to modify the current network configuration in your user-level application, use the System Configuration framework.

To learn about the System Configuration architecture, read _System Configuration Programming Guidelines_. Then read _[System Configuration Framework Reference](https://developer.apple.com/library/ios/documentation/Networking/Reference/SysConfig/index.html)_ to learn about the available APIs.

If your application specifically deals with connecting to wireless networks with Wi-Fi, you can use the Core WLAN framework. For more information, read _CoreWLAN Framework Reference_.

### Develop Network Kernel Extensions

If you want to modify or extend the networking infrastructure of OS X--for purposes such as implementing a custom firewall, a custom VPN, or a bandwidth management system--you may need to write a kernel extension (kext) that plugs in to the kernel's networking subsystem. These extensions are called network kernel extensions, or NKEs.

To learn the fundamentals of writing a kext, read _Kernel Extension Programming Topics_. Then read _Network Kernel Extensions Programming Guide_ to learn how to implement a network kext.
