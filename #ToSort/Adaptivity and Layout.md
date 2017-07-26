# Adaptivity and Layout

_Captured: 2015-12-15 at 10:13 from [developer.apple.com](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/MobileHIG/LayoutandAppearance.html#//apple_ref/doc/uid/TP40006556-CH54-SW1)_

### Build In Adaptivity

People generally want to use their favorite apps on all their devices and in multiple contexts, such as different device orientations and in Split View on iPad. Size classes and Auto Layout help you meet this expectation by defining how the layout of screens, view controllers, and views should adapt when the display environment changes. (The concept of _display environment_ can refer to the entire device screen or only a portion of it, such as the area in a popover or the area in one side of Split View on iPad.)

iOS includes the concept of display environment in the definition of a _trait collection_, which includes size class, display scale, and user interface idiom. You can use a trait collection to make your views and view controllers responsive to changes in the display environment. (To learn more about trait collections, see _[UITraitCollection Class Reference](https://developer.apple.com/library/ios/documentation/UIKit/Reference/UITraitCollection_ClassReference/index.html)_.)

iOS defines two size classes: regular and compact. The _regular_ size class is associated with expansive space and the _compact_ size class is associated with constrained space. To characterize a display environment, you specify a horizontal size class and a vertical size class. As you might guess, an iOS device can use one set of size classes for portrait orientation and a different set of size classes for landscape.

iOS automatically makes various layout changes when the size classes of a display environment change. For example, when the vertical size class changes from compact to regular, navigation bars and toolbars automatically become taller.

When you rely on size classes to drive changes in the layout, your app can look great in any display environment. To learn how to work with size classes in Interface Builder, see _[Size Classes Design Help](https://developer.apple.com/library/ios/recipes/xcode_help-IB_adaptive_sizes/_index.html)_.

Within a size class, continue to use Auto Layout to make small layout adjustments, such as stretching or condensing content. To learn more about using Auto Layout, see _[Auto Layout Guide](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/AutolayoutPG/index.html)_. 

The following concrete examples can help you visualize how size classes characterize the display environments of various devices. For example, iPad (including iPad Pro) uses the regular size class in both dimensions and in both orientations. In other words, the iPad display environment is always horizontally and vertically regular.

![image: ../Art/ipad_size_class_v_2x.png](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/MobileHIG/Art/ipad_size_class_v_2x.png)

![image: ../Art/ipad_size_class_h_2x.png](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/MobileHIG/Art/ipad_size_class_h_2x.png)

With multitasking support on eligible iPad models, your app may have to share the screen with another app. Be sure to use Auto Layout so that you can respond when the user decides to use multitasking features, such as Split View and Slide Over. 

In addition to using Auto Layout, it's important to rely on the `UIView` `[readableContentGuide](https://developer.apple.com/library/ios/documentation/UIKit/Reference/UIView_Class/index.html)` property when you lay out readable content on iPad Pro so that the margins are comfortable for readers. 

The display environment of iPhone can vary depending on the device and its orientation.

![image: ../Art/iphone02_size_class_v_2x.png](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/MobileHIG/Art/iphone02_size_class_v_2x.png)

In portrait, iPhone 6 Plus uses the compact horizontal and regular vertical size classes.

![image: ../Art/iphone02_size_class_h_2x.png](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/MobileHIG/Art/iphone02_size_class_h_2x.png)

All other iPhone models, including iPhone 6, use the same sets of size classes.

![image: ../Art/iphone01_size_class_v_2x.png](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/MobileHIG/Art/iphone01_size_class_v_2x.png)

In portrait, iPhone 6, iPhone 5, and iPhone 4s use the compact horizontal and regular vertical size classes.

![image: ../Art/iphone01_size_class_h_2x.png](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/MobileHIG/Art/iphone01_size_class_h_2x.png)

### Provide a Great Experience in Each Environment

When you take advantage of adaptivity, you can ensure that your UI responds appropriately to changes in the display environment. Follow these guidelines to give people a great experience on all devices and environments.

**Maintain focus on the primary content in all environments.** This is your highest priority. People use your app to view and interact with the content they care about. Changing the focus when the environment changes can disorient people and make them feel they've lost control over the app.

**Avoid gratuitous changes in layout.** A comparable experience in all environments lets people maintain their usage patterns when they rotate a device or run your app on a different device. For example, if you use a grid to display images in a horizontally regular environment, you don't have to display the same information in a list in a horizontally compact environment, although you might adjust the dimensions of the grid.

**Be straightforward if your app runs in only one orientation.** People expect to use your app in different orientations, and it's best when you can fulfill that expectation. But if it's essential that your app run in only one orientation, you should:

  * **Avoid displaying a UI element that tells people to rotate the device.** Running in the supported orientation clearly tells people to rotate the device, if required, without adding unnecessary clutter to the UI. 

  * **Support both variants of an orientation.** For example, if an app runs only in landscape, people should be able to use it whether they're holding the device with the Home button on the right or on the left. And if people rotate the device 180 degrees while using the app, it's best if the app responds by rotating its content 180 degrees. 

**If your app interprets changes in device orientation as user input, handle rotation in app-specific ways.** For example, a game that lets people move game pieces by rotating the device can't respond to device rotation by rotating the screen. In a case like this, you should launch in both variants of the required orientation and allow people to switch between the variants until they start the main task of the app. As soon as people begin the main task, begin responding to device movement in app-specific ways.

### Use Layout to Communicate

Layout encompasses more than just how UI elements look on an app screen. With your layout, you show users what's most important, what their choices are, and how things are related.

**Make it easy to focus on the main task by elevating important content or functionality.** Some good ways to do this are to place principal items in the upper half of the screen and--in left-to-right cultures--near the left side of the screen:

![image: ../Art/focus_on_main_task_2x.png](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/MobileHIG/Art/focus_on_main_task_2x.png)

**Use visual weight and balance to show users the relative importance of onscreen elements.** Large items catch the eye and tend to appear more important than smaller ones. Larger items are also easier for users to tap, which makes them especially useful in apps--such as Phone and Clock--that users often use in distracting surroundings.

![image: ../Art/phone_hangup_button_2x.png](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/MobileHIG/Art/phone_hangup_button_2x.png)

**Use alignment to ease scanning and communicate groupings or hierarchy.** Alignment tends to make an app look neat and organized and it gives users places to focus while they scroll through screenfuls of information. Indentation and alignment of different information groups indicate how the groups are related and make it easier for users to find specific items.

**Make sure that users can understand primary content at its default size.** For example, users shouldn't have to scroll horizontally to read important text, or zoom to see primary images.

**Be prepared for changes in text size.** Users expect most apps to respond appropriately when they choose a different text size in Settings. To accommodate some text-size changes, you might need to adjust the layout; for more information about displaying text in your app, see [Text Should Always Be Legible](ColorImagesText.html#//apple_ref/doc/uid/TP40006556-CH58-SW3).

**As much as possible, avoid inconsistent appearances in your UI.** In general, elements that have similar functions should also look similar. People often assume that there must be a reason for the inconsistencies they notice, and they're apt to spend time trying to figure it out.

**Make it easy for people to interact with content and controls by giving each interactive element ample spacing.** Give tappable controls a hit target of about 44 x 44 points.

![image: ../Art/interact_with_content_r_2x.png](https://developer.apple.com/library/ios/documentation/UserExperience/Conceptual/MobileHIG/Art/interact_with_content_r_2x.png)
