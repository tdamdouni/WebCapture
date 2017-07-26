# TUTORIAL: Creating an iOS App Extension to perform custom actions with Safari content

_Captured: 2016-05-08 at 10:53 from [swiftiostutorials.com](http://swiftiostutorials.com/tutorial-creating-ios-app-extension-ios-8-perform-custom-actions-safari-content/)_

### iOS App Extension

From all the new features introduced in iOS 8, app extensions are definitely the most exciting ones, especially Action Extensions as they "help users view or transform content within the context of another app" according to docs. This formulation actually provides quite much freedom for iOS developers.

This tutorial will cover the creation of an ios app extension.

### The demo app

We are going to build a simple length unit conversion extension, which will allow to convert between meters and feet on the webpage. The extension will search for all occurrences of a unit and convert them to another unit.

There will also be a "dummy container app", because iOS 8 extension are not standalone and should be bundled within an app. The demo app will have just one label that says to open Safari. In a real application it should do something more reasonable:

![main_app_view](http://swiftiostutorials.com/wp-content/uploads/2014/08/main_app_view-e1409241599812.png)

The extension itself will have three buttons - two of them to select what to convert and a cancel button:

![extension_view](http://swiftiostutorials.com/wp-content/uploads/2014/08/extension_view-e1409241677785.png)

For testing purposes, an HTML page has also been created:

![safari_test_page](http://swiftiostutorials.com/wp-content/uploads/2014/08/safari_test_page-e1409241767603.png)

The HTML is available here: <http://swiftiostutorials.com/test_text.html>

### Complete code

You can find the complete code here (tested with Xcode 6 beta 6):

### Getting started

Open Xcode and Create a new project by choosing the Single View Application template. If you're using XCode 6, choose whether Swift or Objective-C on the screen. This tutorial covers both Swift and Objective-C.

![create_project](http://swiftiostutorials.com/wp-content/uploads/2014/08/create_project1-e1409242188763.png)

Now let's design the main user interface. Open Main.storyboard and drag a label to the view.

![app_interface](http://swiftiostutorials.com/wp-content/uploads/2014/08/app_interface-e1409242297383.png)

> _That's all for the main app. Now let's create an extension by adding a new target._

Choose File -> New -> Target.

![add_new_target](http://swiftiostutorials.com/wp-content/uploads/2014/08/add_new_target-e1409242418294.png)

> _And select the desired extension's type. For this tutorial select "Action extensions"._

![select_extension_target](http://swiftiostutorials.com/wp-content/uploads/2014/08/select_extension_target-e1409244632125.png)

Enter the desired name for the extension and select the programming language of your choice.

![name_extension](http://swiftiostutorials.com/wp-content/uploads/2014/08/name_extension-e1409244781209.png)

> _Xcode will also ask to activate the extension's scheme. Press "Activate"._

![activate_extension_scheme](http://swiftiostutorials.com/wp-content/uploads/2014/08/activate_extension_scheme.png)

By default Xcode will create a dummy extension with an ImageView and actions to handle the image. It's a good starting point for creating your own extension.

![default_extension_code](http://swiftiostutorials.com/wp-content/uploads/2014/08/default_extension_code-e1409245019403.png)

### User interface

The user interface for the extension will have 3 buttons: one to convert from meters to feet, another for vice versa conversion and a cancel button.

![extension_interface](http://swiftiostutorials.com/wp-content/uploads/2014/08/extension_interface-e1409245225560.png)

> _Add the corresponding IBActions to the ActionViewController:_

**Objective-C:**

-(IBAction) convertMetersToFt:(id)sender;-(IBAction) convertFtToMeters:(id)sender;-(IBAction) cancel:(id)sender;

**Swift:**

### Info.plist configuration

In order to access a webpage in Safari, two properties must be declared in the Info.plist file:

  * In the NSExtensionActivationRule dictionary (which is created by Xcode automatically), set NSExtensionActivationSupportsWebURLWithMaxCount to a nonzero value.
  * Web content access and changes are managed by a separate javascript file. Add a new empty javascript file to your extension's target and put its name to a NSExtensionJavaScriptPreprocessingFile key. **Don't add the .js extension to the name - it won't find the file with .js.**

Full declaration:

### Accessing and changing webpage content

Open the javascript file that you created in the previous section. If you haven't created or declared it yet, do it as described in the previous part.

Setup the javascript file as following:

  * The javascript file should have a globally defined object named **ExtensionPreprocessingJS.**
  * Create a custom class and assign a new instance of it to the **ExtensionPreprocessingJS **object.
  * A custom class can implement two functions: run() and finalize(). Run() is invoked as soon as Safari loads the javascript file. It is a good place to pass some content from javascript to the extension (ActionViewController in our case). Finalize() function is called, when the extension has processed the content and returned it back. The javascript class can then perform some operation with changed or processed content. If no more action is needed after the extension has finished, finalize() function is also not needed (e.g in case of content sharing in Share extensions).

The complete code of the javascript file for this demo app:

The javascript class does only two things: in run() function it passes body content to the extension. The extension changes the HTML content and passes it back to javascript. Page contents are finally updated in the finalize() function.

### Writing the extension

Now, when our extension is finally set up (all required keys are declared in Info.plist, the javascript file is added and the user interface is designed), we're ready to write some code for the extension.

In order to do something useful with the content, it needs to be passed to the ActionViewController's class. The sending part is handled by javascript. The receiving part should be done in the ActionViewController's class. The receiving will be implemented in the viewDidLoad method.

To handle sending and receiving actions, UIViewController has an extensionContext property. The property can be also used to check, if the controller is participating in an extension request. The extension context has an array of input items that are associated with the context. The array can be empty.

In order to get the content, we need to pass the input items array:

Each input item is an instance of NSExtensionItem. NSExtensionItem should have attachments that represent some content that was passed to the extension. According to the documentation, attachments are always of type NSItemProvider. In order to check, if NSItemProvider has associated content of a desired type, a hasItemConformingToTypeIdentifier method can be used. For this tutorial, we should check for kUTTypePropertyList type as it represents dictionaries that are used in javascript communication:

If the check is successful, we can finally query the content by using NSItemProvider's method loadItemForTypeIdentifier. As a result, we get a dictionary that has another dictionary inside. The second dictionary, is actually what we were looking for - it's the object that was sent by javascript. To access it, the NSExtensionJavaScriptPreprocessingResultsKey key should be used.

And finally, the full source code for the content receiving part:

**Objective-C:**

**Swift:**

### Performing the action

The conversion action itself is an easy string search and replace with a regex. Let's declare a method that takes a regex pattern to find, a replacement string and a multiplier number which represents the ratio between units.

The method does backward string replacements, because otherwise the found ranges would be incorrect after the first replacement.

**Objective-C:**

**Swift:**

To convert meters to feet following parameters are used:

**Objective-C:**

**Swift:**

And for vice versa:

**Objective-C:**

**Swift:**

The finalizeReplace method returns the modified content back to javascript. It does it by creating an NSExtensionItem object and passing content as its attachment:

**Objective-C:**

**Swift:**

### Cancelling the action

When cancel button is pressed, the finalizeReplace method is called. It basically just passes unchanged content back to javascript.

### Testing the extension

In order to test the extension, run first the container app. Then open Safari and go to <http://swiftiostutorials.com/test_text.html>.

Press the Share button and select more action:

![press_more_to_add_extension](http://swiftiostutorials.com/wp-content/uploads/2014/08/press_more_to_add_extension-e1409256573891.png)

> _In order to start using the extension, you need to enable it:_

![enable_extension](http://swiftiostutorials.com/wp-content/uploads/2014/08/enable_extension-e1409256618221.png)

Now it is available in share actions:

![choose_extension](http://swiftiostutorials.com/wp-content/uploads/2014/08/choose_extension-e1409256664967.png)

Select the "ConvertMe Extension" and press "m to ft" and you can see that all meters are converted to ft:

![m_to_ft_test](http://swiftiostutorials.com/wp-content/uploads/2014/08/m_to_ft_test-e1409256774649.png)

> _Select "ft to m" and all units will be converted to meters:_

![ft_to_m_test](http://swiftiostutorials.com/wp-content/uploads/2014/08/ft_to_m_test-e1409256810492.png)

If you have any trouble, you can run the extension separately and attach it to Safari (Xcode will let you choose). You can then see extension's logs and debug it.

### Complete code

You can find the complete code here (tested with Xcode 6 beta 6):

[Swift](http://swiftiostutorials.com/wp-content/uploads/2014/08/ConvertMe.zip)

[Objective-C]()
