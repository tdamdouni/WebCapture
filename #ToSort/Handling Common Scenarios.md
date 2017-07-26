# Handling Common Scenarios

_Captured: 2015-11-16 at 09:22 from [developer.apple.com](https://developer.apple.com/library/prerelease/ios/documentation/General/Conceptual/ExtensibilityPG/ExtensionScenarios.html)_

As you write custom code that performs your app extensionâs task, you may need to handle some scenarios that are common to many types of extensions. Use the code and recommendations in this chapter to help you implement your solutions. 

### Using an Embedded Framework to Share Code

You can create an embedded framework to share code between your app extension and its containing app. For example, if you develop an image filter for use in your Photo Editing extension as well as in its containing app, put the filterâs code in a framework and embed the framework in both targets. 

Make sure your embedded framework does not contain APIs unavailable to app extensions, as described in [Some APIs Are Unavailable to App Extensions](ExtensionOverview.html#//apple_ref/doc/uid/TP40014214-CH2-SW6). If you have a custom framework that does contain such APIs, you can safely link to it from your containing app but cannot share that code with the appâs contained extensions. The App Store rejects any app extension that links to such frameworks or that otherwise uses unavailable APIs. 

To configure an app extension target to use an embedded framework, set the targetâs âRequire Only App-Extension-Safe APIâ build setting to Yes. If you donât, Xcode reminds you to do so by displaying the warning _âlinking against dylib not safe for use in application extensionsâ_. 

Important 

A containing app that links to an embedded framework must include the arm64 (iOS) or x86_64 (OSÂ X) architecture build setting or it will be rejected by the App Store. (As described in [Creating an App Extension](ExtensionCreation.html#//apple_ref/doc/uid/TP40014214-CH5-SW1), all app extensions must include the appropriate 64-bit architecture build setting.) 

When configuring your Xcode project, you must choose âFrameworksâ as the destination for your embedded framework in the Copy Files build phase. 

Important 

Always choose âFrameworksâ as your Copy Files build phase destination. If you instead choose the âSharedFrameworkâ destination, the App Store will reject your submission. 

You can make a containing app available to users running iOS 7 or earlier, but then must take precautions to safely link embedded frameworks when running in iOS 8 or later. Read Deploying a Containing App to Older Versions of iOS for details. 

For more on creating and using embedded frameworks, watch the WWDC 2014 video âBuilding Modern Frameworks,â available at [https://developer.apple.com/videos/wwdc/2014](https://developer.apple.com/videos/wwdc/2014/#416). 

### Sharing Data with Your Containing App

Even though an app extension bundle is nested within its containing appâs bundle, the running app extension and containing app have no direct access to each otherâs containers. 

Background 

To learn about containers, read [About the iOS File System](../../../FileManagement/Conceptual/FileSystemProgrammingGuide/FileSystemOverview/FileSystemOverview.html#//apple_ref/doc/uid/TP40010672-CH2-SW12) in _[File System Programming Guide](../../../FileManagement/Conceptual/FileSystemProgrammingGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40010672)_. 

You can, however, enable data sharing. For example, you might want to allow your app extension and its containing app to share a single large set of data, such as prerendered assets. 

To enable data sharing, use Xcode or the Developer portal to enable app groups for the containing app and its contained app extensions. Next, register the app group in the portal and specify the app group to use in the containing app. To learn about working with app groups, see [Adding an App to an App Group](../../../Miscellaneous/Reference/EntitlementKeyReference/Chapters/EnablingAppSandbox.html#//apple_ref/doc/uid/TP40011195-CH4-SW19). 

After you enable app groups, an app extension and its containing app can both use the `[NSUserDefaults](../../../Cocoa/Reference/Foundation/Classes/NSUserDefaults_Class/index.html#//apple_ref/occ/cl/NSUserDefaults)` API to share access to user preferences. To enable this sharing, use the `[initWithSuiteName:](../../../Cocoa/Reference/Foundation/Classes/NSUserDefaults_Class/index.html#//apple_ref/occ/instm/NSUserDefaults/initWithSuiteName:)` method to instantiate a new `NSUserDefaults` object, passing in the identifier of the shared group. For example, a Share extension might update the userâs most recently used sharing account, using code like this: 

  1. `// Create and share access to an NSUserDefaults object`
  2. `NSUserDefaults *mySharedDefaults = [[NSUserDefaults alloc] initWithSuiteName: @"com.example.domain.MyShareExtension"];`
  3. ` `
  4. `// Use the shared user defaults object to update the user's account`
  5. `[mySharedDefaults setObject:theAccountName forKey:@"lastAccountName"];`

Figure 4-1shows how an extension and its containing app can use a shared container to share data. 

**Figure 4-1**An app extensionâs container is distinct from its containing appâs container ![image: ../Art/app_extensions_container_restrictions_2x.png](Art/app_extensions_container_restrictions_2x.png)

Important 

You must set up a shared container if your app extension uses the `[NSURLSession](../../../Foundation/Reference/NSURLSession_class/index.html#//apple_ref/occ/cl/NSURLSession)` class to perform a background upload or download, so that both the extension and its containing app can access the transferred data. To learn how to perform an upload or download in the background, see Performing Uploads and Downloads. 

When you set up a shared container, the containing appâand each contained app extension that you allow to participate in data sharingâhave read and write access to the shared container. To avoid data corruption, you must synchronize data accesses. 

Use Core Data, SQLite, or Posix locks to help coordinate data access in a shared container. 

Version Note 

Starting in iOS 8.2, but not in earlier versions of iOS, you can also safely employ the `[UIDocument](../../../UIKit/Reference/UIDocument_Class/index.html#//apple_ref/occ/cl/UIDocument)` class to coordinate shared data access. Do not use file coordination APIs directly in any version of iOS. 

### Accessing a Webpage

In Share extensions (on both platforms) and Action extensions (iOS only), you can give users access to web content by asking Safari to run a JavaScript file and return the results to the extension. You can also use the JavaScript file to access a webpage before your extension runs (on both platforms), or to access or modify the webpage after your extension completes its task (iOS only). For example, a Share extension can help users share content from a webpage, or an Action extension in iOS might display a translation of the userâs current webpage. 

To add webpage access and manipulation to your app extension, perform the following steps: 

  * Create a JavaScript file that includes a global object named `ExtensionPreprocessingJS`. Assign a new instance of your custom JavaScript class to this object. 
  * In the `NSExtensionActivationRule` dictionary in your app extensionâs `Info.plist` file, give the `NSExtensionActivationSupportsWebPageWithMaxCount` key a nonzero value. (To learn more about the activation rule dictionary, see Declaring Supported Data Types for a Share or Action Extension.) 
  * When your app extension starts, use the `[NSItemProvider](../../../Foundation/Reference/NSItemProvider_Class/index.html#//apple_ref/occ/cl/NSItemProvider)` class to get the results returned by the execution of the JavaScript file. 
  * In an iOS app extension, pass values to the JavaScript file if you want Safari to modify the webpage when your extension completes its task. (You use the `NSItemProvider` class in this step, too.) 

To tell Safari that your app extension includes a JavaScript file, add the `NSExtensionJavaScriptPreprocessingFile` key to the `NSExtensionAttributes` dictionary. The value of the key should be the file that you want Safari to load before your extension starts. For example: 

  1. `<key>NSExtensionAttributes</key>`
  2. ` <dict>`
  3. ` <key>NSExtensionJavaScriptPreprocessingFile</key>`
  4. ` <string>MyJavaScriptFile</string> <!-- Do not include the ".js" filename extension -->`
  5. ` </dict>`

On both platforms, your custom JavaScript class can define a `run()` function that Safari invokes as soon as it loads the JavaScript file. In the `run()` function, Safari provides an argument named `completionFunction`, with which you can pass results to your app extension in the form of a key-value object. 

In iOS, you can also define a `finalize()` function that Safari invokes when your app extension calls `completeRequestReturningItems:completion:` at the end of its task. A `finalize()` function can use items your extension passes in `completeRequestReturningItems:completion:` to change the webpage as desired. 

For example, if your iOS app extension needs the base URI of a webpage when it starts and it changes the background color of the webpage when it stops, you might write JavaScript code like that shown in Listing 4-1. 

**Listing 4-1**Example `run()` and `finalize()` functions

  1. `var MyExtensionJavaScriptClass = function() {};`
  2. ` `
  3. `MyExtensionJavaScriptClass.prototype = {`
  4. ` run: function(arguments) {`
  5. ` // Pass the baseURI of the webpage to the extension.`
  6. ` arguments.completionFunction({"baseURI": document.baseURI});`
  7. ` },`
  8. ` `
  9. `// Note that the finalize function is only available in iOS.`
  10. ` finalize: function(arguments) {`
  11. ` // arguments contains the value the extension provides in [NSExtensionContext completeRequestReturningItems:completion:].`
  12. ` // In this example, the extension provides a color as a returning item.`
  13. ` document.body.style.backgroundColor = arguments["bgColor"];`
  14. ` }`
  15. `};`
  16. ` `
  17. `// The JavaScript file must contain a global object named "ExtensionPreprocessingJS".`
  18. `var ExtensionPreprocessingJS = new MyExtensionJavaScriptClass;`

On both platforms, you need to write code to handle the values that get passed back from your `run()` function. To get the dictionary of results, specify the `kUTTypePropertyList` type identifier in the `NSItemProvider` method `[loadItemForTypeIdentifier:options:completionHandler:](../../../Foundation/Reference/NSItemProvider_Class/index.html#//apple_ref/occ/instm/NSItemProvider/loadItemForTypeIdentifier:options:completionHandler:)`. In the dictionary, use the `NSExtensionJavaScriptPreprocessingResultsKey` key to get the result item. For example, to get the base URI passed in the `run()` function in Listing 4-1, you might use code like this: 

  1. `[imageProvider loadItemForTypeIdentifier:kUTTypePropertyList options:nil completionHandler:^(NSDictionary *item, NSError *error) {`
  2. ` NSDictionary *results = (NSDictionary *)item;`
  3. ` NSString *baseURI = [[results objectForKey:NSExtensionJavaScriptPreprocessingResultsKey] objectForKey:@"baseURI"];`
  4. ` }];`

To pass a value to the `finalize()` function when your iOS app extension finishes its task, use the `NSItemProvider` `initWithItem:typeIdentifier:` method to pack the value in the dictionary for the `[NSExtensionJavaScriptFinalizeArgumentKey](../../../Foundation/Reference/NSItemProvider_Class/index.html#//apple_ref/c/data/NSExtensionJavaScriptFinalizeArgumentKey)` key. For example, to specify red for the background color used in the `finalize()` function in Listing 4-1, your extension might use code like this: 

  1. ` NSExtensionItem *extensionItem = [[NSExtensionItem alloc] init];`
  2. ` extensionItem.attachments = @[[[NSItemProvider alloc] initWithItem: @{NSExtensionJavaScriptFinalizeArgumentKey: @{@"bgColor":@"red"}} typeIdentifier:(NSString *)kUTTypePropertyList]];`
  3. ` [[self extensionContext] completeRequestReturningItems:@[extensionItem] completion:nil];`

### Performing Uploads and Downloads

Users tend to return to the host app immediately after they finish their task in your app extension. If the task involves a potentially lengthy upload or download, you need to ensure that it can finish after your extension gets terminated. To perform an upload or download, use the `[NSURLSession](../../../Foundation/Reference/NSURLSession_class/index.html#//apple_ref/occ/cl/NSURLSession)` class to create a URL session and initiate a background upload or download task. 

Note 

Recall that other types of background tasks, such as supporting VoIP or playing background audio, are not available to app extensions. For more information, see [Respond to the Host Appâs Request](ExtensionCreation.html#//apple_ref/doc/uid/TP40014214-CH5-SW3). 

After your app extension initiates the upload or download task, the extension can complete the host appâs request and be terminated without affecting the outcome of the task. To learn more about how an extension handles the request from a host app, see [Respond to the Host Appâs Request](ExtensionCreation.html#//apple_ref/doc/uid/TP40014214-CH5-SW3). In iOS, if your extension isnât running when a background task completes, the system launches your containing app in the background and calls the `[application:handleEventsForBackgroundURLSession:completionHandler:](../../../UIKit/Reference/UIApplicationDelegate_Protocol/index.html#//apple_ref/occ/intfm/UIApplicationDelegate/application:handleEventsForBackgroundURLSession:completionHandler:)` app delegate method. 

Important 

If your app extension initiates a background `[NSURLSession](../../../Foundation/Reference/NSURLSession_class/index.html#//apple_ref/occ/cl/NSURLSession)` task, you must also set up a shared container that both the extension and its containing app can access. Use the `[sharedContainerIdentifier](../../../Foundation/Reference/NSURLSessionConfiguration_class/index.html#//apple_ref/occ/instp/NSURLSessionConfiguration/sharedContainerIdentifier)` property of the `NSURLSessionConfiguration` class to specify an identifier for the shared container so that you can access it later. 

Refer to Sharing Data with Your Containing App for guidance on setting up a shared container. 

Listing 4-2 shows one way to configure a URL session and use it to initiate a download. 

**Listing 4-2**An example of configuring an `NSURLSession` object and starting a download

  1. ` NSURLSession *mySession = [self configureMySession];`
  2. ` NSURL *url = [NSURL URLWithString:@"http://www.example.com/LargeFile.zip"];`
  3. ` NSURLSessionTask *myTask = [mySession downloadTaskWithURL:url];`
  4. ` [myTask resume];`
  5. ` `
  6. `\- (NSURLSession *) configureMySession {`
  7. ` if (!mySession) {`
  8. ` NSURLSessionConfiguration* config = [NSURLSessionConfiguration backgroundSessionConfigurationWithIdentifier:@âcom.mycompany.myapp.backgroundsessionâ];`
  9. `// To access the shared container you set up, use the sharedContainerIdentifier property on your configuration object.`
  10. `config.sharedContainerIdentifier = @âcom.mycompany.myappgroupidentifierâ;`
  11. ` mySession = [NSURLSession sessionWithConfiguration:config delegate:self delegateQueue:nil];`
  12. ` }`
  13. ` return mySession;`
  14. `}`

Because only one process can use a background session at a time, you need to create a different background session for the containing app and each of its app extensions. (Each background session should have a unique identifier.) Itâs recommended that your containing app only use a background session that was created by one of its extensions when the app is launched in the background to handle events for that extension. If you need to perform other network-related tasks in your containing app, create different URL sessions for them. 

If you need to complete the host appâs request before you initiate a background URL session, make sure that the code that creates and uses the session is efficient. After your app extension calls `[completeRequestReturningItems:completionHandler:](../../../Foundation/Reference/NSExtensionContext_Class/index.html#//apple_ref/occ/instm/NSExtensionContext/completeRequestReturningItems:completionHandler:)` to tell the host app that its request is complete, the system can terminate your extension at any time. 

### Declaring Supported Data Types for a Share or Action Extension

In your Share or Action extension, itâs likely that you can work with some types of data but not others. To ensure that a host app offers your extension only when the user has selected data of a type that you support, add the `NSExtensionActivationRule` key to your extensionâs `Info.plist` property list file. You can also use this key to specify a maximum number of items of each type that your extension can handle. 

When your extension runs, the system compares the `NSExtensionActivationRule` keyâs values with the information in an extension itemâs `[attachments](../../../Foundation/Reference/NSExtensionItem_Class/index.html#//apple_ref/occ/instp/NSExtensionItem/attachments)` property. For a complete list of keys you can use with this key, see [Action Extension Keys](../../Reference/InfoPlistKeyReference/Articles/SystemExtensionKeys.html#//apple_ref/doc/uid/TP40014212-SW2). 

For example, to declare that your Share extension can support up to ten images, one movie, and one webpage URL, you might use the following dictionary for the value of the `NSExtensionAttributes` key: 

  1. `<key>NSExtensionAttributes</key>`
  2. ` <dict>`
  3. ` <key>NSExtensionActivationRule</key>`
  4. ` <dict>`
  5. ` <key>NSExtensionActivationSupportsImageWithMaxCount</key>`
  6. ` <integer>10</integer>`
  7. ` <key>NSExtensionActivationSupportsMovieWithMaxCount</key>`
  8. ` <integer>1</integer>`
  9. ` <key>NSExtensionActivationSupportsWebURLWithMaxCount</key>`
  10. ` <integer>1</integer>`
  11. ` </dict>`
  12. ` </dict>`

If you donât support a particular data type, use `0` for the value of the corresponding key or remove the key from your `NSExtensionActivationRule` dictionary. 

Note 

If your Share or iOS Action extension needs to access a webpage, you must include the `NSExtensionActivationSupportsWebPageWithMaxCount` key with a nonzero value. (To learn how to use JavaScript to access a webpage from your extension, see Accessing a Webpage.) 

The keys in the `NSExtensionActivationRule` dictionary are sufficient to meet the filtering needs of typical app extensions. If you need to do more complex or more specific filtering, such as distinguishing between `public.url` and `public.image`, you can create a predicate statement. Then, use the bare string that represents the predicate as the value of the `NSExtensionActivationRule` key. (At runtime, the system compiles this string into an `[NSPredicate](../../../Cocoa/Reference/Foundation/Classes/NSPredicate_Class/index.html#//apple_ref/occ/cl/NSPredicate)` object.) 

For example, an app extension item's `attachments` property can specify a PDF file like this: 

  1. `{extensionItems = ({`
  2. ` attachments = ({`
  3. ` registeredTypeIdentifiers = (`
  4. ` "com.adobe.pdf",`
  5. ` "public.file-url"`
  6. ` );`
  7. ` });`
  8. `})}`

To specify that your app extension can handle exactly one PDF file, you might create a predicate string like this: 

  1. `SUBQUERY (`
  2. ` extensionItems,`
  3. ` $extensionItem,`
  4. ` SUBQUERY (`
  5. ` $extensionItem.attachments,`
  6. ` $attachment,`
  7. ` ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.adobe.pdf"`
  8. ` ).@count == $extensionItem.attachments.@count`
  9. `).@count == 1`

Here is an example of a more complex predicate statement: 

  1. `SUBQUERY (`
  2. ` extensionItems,`
  3. ` $extensionItem,`
  4. ` SUBQUERY (`
  5. ` $extensionItem.attachments,`
  6. ` $attachment,`
  7. ` ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "org.appextension.action-one" ||`
  8. ` ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "org.appextension.action-two"`
  9. ` ).@count == $extensionItem.attachments.@count`
  10. `).@count == 1`

This statement iterates over an array of `[NSExtensionItem](../../../Foundation/Reference/NSExtensionItem_Class/index.html#//apple_ref/occ/cl/NSExtensionItem)` objects, and secondarily over the `[attachments](../../../Foundation/Reference/NSExtensionItem_Class/index.html#//apple_ref/occ/instp/NSExtensionItem/attachments)` array in each extension item. For each attachment, the predicate evaluates the uniform type identifier (UTI) for each representation in the attachment. When an attachment representation UTI conforms to any of of two different specified UTIs (which you see on the right-hand side of each `UTI-CONFORMS-TO` operator), collect that UTI for the final comparison test. The final line returns `TRUE` if the app extension was given exactly one extension item attachment with a supported UTI. 

During development only, you can use the `TRUEPREDICATE` constant (which always evaluates to `true`) as a stub predicate statement, to test your code path before you implement your predicate statement. 

Important 

Before you submit your containing app to the App Store, be sure to replace all uses of `TRUEPREDICATE` stub predicates with functional predicate statements or with `NSExtensionActivationRule` keys. If any app extensions in your containing app include the string `TRUEPREDICATE`, the app will be rejected. 

To learn more about the syntax of predicate statements, see [Predicate Format String Syntax](../../../Cocoa/Conceptual/Predicates/Articles/pSyntax.html#//apple_ref/doc/uid/TP40001795) in _[Predicate Programming Guide](../../../Cocoa/Conceptual/Predicates/AdditionalChapters/Introduction.html#//apple_ref/doc/uid/TP40001789)_. 

### Deploying a Containing App to Older Versions of iOS

If you link to an embedded framework from your containing app, you can still deploy it to versions of iOS older than 8.0, even though embedded frameworks are not available in those versions. 

The mechanism that lets you do this is the [dlopen](x-man-page://dlopen) command, which you use to conditionally link and load a framework bundle. You employ this command as an alternative to the build-time linking you can specify in the Xcode General or Build Phases target editor. The main idea is to link embedded frameworks into your containing app only when running in iOS 8.0 or newer. 

You must use Objective-C, not Swift, in your code statements that conditionally load a framework bundle. The rest of your app can be written in either language, and the embedded framework itself can likewise be written in either language. 

After calling `dlopen`, access the embedded framework classes using the following type of statement: 

  1. `MyLoadedClass *loadedClass = [[NSClassFromString (@"MyClass") alloc] init];`

Important 

If your containing app target links to an embedded framework, it must include the arm64 architecture or it will be rejected by the App Store. 

**To set up an app extension Xcode project to take advantage of conditional linking**

  1. For each of your contained app extensions, set the deployment target to be iOS 8.0 or later, as usual. 

Do this in the âDeployment infoâ section of the General tab in the Xcode target editor. 

  2. For your containing app, set the deployment target to be the oldest version of iOS that you want to support. 
  3. In your containing app, conditionalize calls to the `dlopen` command within a runtime check for the iOS version by using the `[systemVersion](../../../UIKit/Reference/UIDevice_Class/index.html#//apple_ref/occ/instp/UIDevice/systemVersion)` method. 

Call the `dlopen` command only if your containing app is running in iOS 8.0 or later. Be sure to use Objective-C, not Swift, when making this call. 

Certain iOS APIs use embedded frameworks via the `dlopen` command. You must conditionalize your use of these APIs just as you do when calling `dlopen` directly. These APIs are from the `[CFBundleRef](../../../CoreFoundation/Reference/CFBundleRef/index.html#//apple_ref/c/tdef/CFBundleRef)` opaque type: 

  * `[CFBundleGetFunctionPointerForName](../../../CoreFoundation/Reference/CFBundleRef/index.html#//apple_ref/c/func/CFBundleGetFunctionPointerForName)`
  * `[CFBundleGetFunctionPointersforNames](../../../CoreFoundation/Reference/CFBundleRef/index.html#//apple_ref/c/func/CFBundleGetFunctionPointersForNames)`

And from the `[NSBundle](../../../Cocoa/Reference/Foundation/Classes/NSBundle_Class/index.html#//apple_ref/occ/cl/NSBundle)` class: 

  * `[load](../../../Cocoa/Reference/Foundation/Classes/NSBundle_Class/index.html#//apple_ref/occ/instm/NSBundle/load)`
  * `[loadAndReturnError:](../../../Cocoa/Reference/Foundation/Classes/NSBundle_Class/index.html#//apple_ref/occ/instm/NSBundle/loadAndReturnError:)`
  * `[classNamed:](../../../Cocoa/Reference/Foundation/Classes/NSBundle_Class/index.html#//apple_ref/occ/instm/NSBundle/classNamed:)`

In a containing app you are deploying to versions of iOS older than 8.0, call these APIs only within a runtime check that ensures you are running in iOS 8.0 or newer, and call these APIs using Objective-C. 
