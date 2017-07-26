# Basic Patterns For Mobile Navigation: Pros And Cons

_Captured: 2017-05-10 at 14:20 from [www.smashingmagazine.com](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)_

Today, too many websites are still inaccessible. In our new book _Inclusive Design Patterns_, we explore how to craft **flexible front-end design patterns** and make **future-proof and accessible interfaces without extra effort**. Hardcover, 312 pages. [Get the book now!](https://shop.smashingmagazine.com/products/inclusive-design-patterns?utm_source=magazine&utm_campaign=inclusive-design-patterns&utm_medium=html-ad-content-1)

Once someone starts using your app, they need to know where to go and how to get there at any point. Good navigation is a vehicle that takes users where they want to go. But establishing good navigation is a challenge on mobile due to the limitations of the small screen and the need to prioritize content over chrome.

Different navigation patterns have been devised to solve this challenge in different ways, but they all suffer from a variety of usability problems. In this article, we'll examine five basic navigation patterns for mobile apps and describe the **strengths and weaknesses of each** of them. If you'd like to add some patterns and spice up your designs, you can download and test [Adobe XD](https://adobe.ly/2q0pi6P) for free and get started right away.

Screen space is a precious commodity on mobile, and the hamburger menu (or side drawer) is one of the most popular mobile navigation patterns for helping you save it. The drawer panel allows you to hide the navigation beyond the left edge of the screen and reveal it only upon a user's action.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/hamburger-menu-780w-opt.png)[6](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)

> _In its default state, the hamburger menu and all of its contents remain hidden. (_

The main downside of the hamburger menu is its [low discoverability](https://thenextweb.com/dd/2014/04/08/ux-designers-side-drawer-navigation-costing-half-user-engagement/), and it's not recommended as the main navigation menu. However, this pattern might be an appropriate solution for secondary navigation options. Secondary navigation options are destinations or features that are important for users only in certain circumstances. Being secondary, they can be relegated to less prominent visual placement, as long as users can quickly find a utility when they need it. By hiding these options behind the hamburger icon, designers avoid overwhelming users with too many options.

Uber uses a hamburger icon for this purpose. Because everything about the main screen of the Uber app is focused on requesting a car, there's no need to display secondary options such as "Payment," "History" or "Settings." The normal user flow doesn't include these actions, and so they can be hidden behind the hamburger icon.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/uber-preview-opt.png)[9](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)

  * **Large number of navigation options**  
The main advantage of the navigation menu is that it can accommodate a fairly large number of navigation options in a tiny space.
  * **Clean design**  
The hamburger menu allows the designer to free up screen real estate by shifting options off screen into a side menu. This pattern can be particularly useful if you want the user to focus on the main content.
  * **Less discoverable**  
What's out of sight is out of mind. When navigation is hidden, users are less likely to use it. While this type of navigation is becoming standard and many mobile users are familiar with it, many people still simply don't think to open it.
  * **Clashes with platform navigation rules**  
The hamburger menu has become almost a standard on Android (the pattern has the name "[navigation drawer](https://material.io/guidelines/patterns/navigation-drawer.html)" in material design), but in iOS it simply cannot be implemented without clashing with basic navigation elements, and this could overload the navigation bar. ![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/navigation-preview-opt.png)[11](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)  


> _(Image: lmjabreu)_

  * The hamburger icon hides context. The hamburger menu doesn't communicate the current location at a glance: [Surfacing information](https://www.nngroup.com/articles/hamburger-menus/) about the current location is harder because it's only visible when the person clicks on the hamburger icon.  
![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/The-hamburger-icon-hides-context.gif)[14](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)  


> _Out of sight, out of mind. The hamburger menu hides the user's current location in the app._

  * Extra action is required to move to the target destination. Reaching a particular page usually takes at least two taps (one tap on the menu icon and another on the target option).
  * Prioritize the navigation options. If the navigation is complex, hiding it won't make it user-friendly. A lot of practical examples clearly show that exposing menu options in a more visible way [increases engagement and user satisfaction](http://www.lukew.com/ff/entry.asp?1945). Ask yourself, What's important enough to be visible on mobile? Answering that question will require an understanding of what matters to your users.  
![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/navigation-options-preview-opt.png)[16](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)  


> _Redbooth's move from a hamburger menu to a bottom tab bar resulted in [increased user sessions.](https://redbooth.com/blog/hamburger-menu-iphone-app?utm_campaign=iOS_Dev_Weekly_Issue_181&utm_medium=email&utm_source=iOS%2BDev%2BWeekly)[17](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/) (Image: [LukeW](https://twitter.com/lukew/status/562297190735806464)[18](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/))  
_

  * Consider using tabs or a tab bar if you have a limited number of high-priority navigation options.  
![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/youtube-780w-opt.png)[19](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)  


> _YouTube makes the main pieces of core functionality available with one tap, allowing rapid switching between features. (Source: Luke Wroblewski) ([View large version](https://www.smashingmagazine.com/wp-content/uploads/2017/05/youtube-large-opt.png)[20](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/))  
_

  * Review your information architecture. Good apps are highly focused. So, if you have one complex app, you could split its functionality into two (or more) simple apps. Facebook released its Messenger app in order to [solve the problem of complexity](http://www.businessinsider.com/why-is-facebook-messenger-a-separate-app-2014-11). The reduced functionality results in a reduced set of menu options, and less need for a hamburger menu.
![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/facebook-780w-opt.png)[22](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)

> _View large version_

The tab bar pattern is inherited from desktop design. It usually contains relatively few destinations, and those destinations are of similar importance and require direct access from anywhere in the app.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/tab-bar-preview-opt.png)[24](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)

> _The tab bar doesn't hide navigation, but allows direct access and presents feedback on the icon it's related to._

Tabbed navigation is a great solution for apps with relatively few top-level navigation options (up to five). The tab bar makes the main pieces of core functionality available with one tap, allowing rapid switching between features.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/Tab-bar-in-Twitter-preview-opt.png)[25](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)

> _The tab bar in Twitter lets the user navigate directly to the screen associated with the item._

* The tab bar fairly easily communicates the current location. Properly used visual cues (icons, labels and colors) enable the user to understand their current location at a glance.  
![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/tab-bar-pros.gif)[26](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)  


> _(Image: [Ramotion](http://ramotion.com/)[27](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/))  
_

* Tab bars are persistent. The navigation remains in sight no matter what page the user is viewing. The user has clear visibility of all the main app views and has single-click access to them.
* With a thumb zone, the bottom navigation is easier to reach with the thumb when the device is held in one hand.  
![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/thumb-zone-780w-opt.jpg)[28](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)  


> _Ideal placement of navigation for the thumb zone, according to_

* The navigation options are limited. If your app has more than five options, then fitting them in a tab or navigation bar and still keeping an optimum touch-target size would be hard.  
![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/tab-bar-cons-preview-opt.jpg)[31](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)  


> _Don't use more than five options in a tab bar._

* The location and logic of the tab bar options on iOS and Android are different. Platforms have different rules and guidelines for UI and usability, and you have to take them into consideration when designing a tab bar for a particular platform. Tabs appear at the top of the screen on Android and at the bottom of the screen on iOS. This happens presumably because Android's control bar at the bottom is hardware. Please note that this rule doesn't apply to mobile websites, because the experience with them should be consistent regardless of the device used to browse them (Android or iOS).  
![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/tab-bar-cons-1-preview-opt.png)[32](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)  


> _Proper location and logic will help to maintain a consistent experience with other apps on the platform and prevent confusion between actions and view-switching. (Image:_

  * Make touch targets big enough to be easily tapped or clicked. To calculate the width of each bottom navigation action, divide the width of the view by the number of actions. Alternatively, make all bottom navigation actions the width of the largest action.  
![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/touch-targets-preview-opt.jpg)[34](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)  


> _Most users can comfortably and reliably hit a 10 × 10-millimeter touch target. (Image:_

  * Order the navigation options. Users expect to see a certain order in the tab bar. The first tab item has to be the home screen of the app, and the order of tabs should reflect their priority or the logical order in the user flow. One of the tabs should always be active and [visually highlighted](https://www.nngroup.com/articles/tabs-used-right/).
  * Test your icons for usability. As you can see in the example below, app designers sometimes hide functionality behind icons that are pretty hard to recognize. To prevent this from happening, [test your icons with the five-second rule](https://www.nngroup.com/articles/icon-usability/): If it takes you more than five seconds to think of an appropriate icon for something, then it is unlikely that an icon can effectively communicate that meaning.  
![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/Bloom.fm-app-preview-opt.png)[38](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)  


> _Bloom.fm app has a tab bar full of abstract icons._

  * If an icon fails the five-second rule (i.e. [isn't self-evident](https://www.smashingmagazine.com/2016/10/icons-as-part-of-a-great-user-experience/)), it needs a text label. It's pretty rare in the offline world that we rely on iconography alone to represent ideas -- and for good reason. Due to the [absence of a standard usage](https://www.nngroup.com/articles/icon-usability/) for most icons, text labels are necessary to communicate meaning and reduce ambiguity. Users should understand what exactly will happen before they tap on an element.  
![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/bottom-navigation-icons-780w-opt.png)[41](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)  


> _Use text labels to provide short, meaningful definitions to bottom navigation icons. (_

The "[Priority+](http://justmarkup.com/log/2012/06/19/responsive-multi-level-navigation/)" pattern was coined by Michael Scharnagl to describe navigation that exposes what's deemed to be the most important navigation elements and hides away less important items behind a "more" button.

This pattern might be good solution for content-heavy apps and websites with a lot of different sections and pages (such as a news website or a large retailer's store). [The Guardian](http://www.theguardian.com/) makes use of the priority+ pattern for its section navigation. Less important items are revealed when the user hits the "All" button.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/bradfrost.gif)[45](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)

> _The Guardian employs the Priority+ pattern for its section navigation. Image credit:_

  * This pattern prioritizes navigation options. It surfaces the most frequently accessed navigation options.
  * It makes use of available screen space. As space increases, the number of exposed navigation options increases as well, which can result in better visibility and more engagement.
  * This menu is very adaptive. You can scale it quite nicely across screen sizes without having to transform the pattern.
  * It might hide some important navigation options. The priority+ pattern requires designers to assume the relative importance of navigation items. Be aware that the items you prioritize to be visible might not be the same ones users are looking for most.

Shaped like a circled icon floating above the UI, the floating action button changes color upon focus and lifts upon selection. It's well known by all Android users and is a distinct element of material design. Floating above the interface of an app, it promotes user action, [says Google](https://material.io/guidelines/components/buttons-floating-action-button.html#).

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/action-button-preview-opt.png)[48](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)

> _Floating action button_

The design of the floating action button hinges on the premise that users will perform a certain action most of the time. You can make this "hero" action even more heroic by reinforcing the sense that it is a core use case of your app. For example, a music app might have a floating action button that represents "play."

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/FAB-preview-opt.png)[49](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)

> _Use the floating action button for actions that are strongly characteristic of your app. Playback tells users that this is a music app._

The button is a natural cue to users for what to do next. In user research, [Google found](https://youtu.be/dZqzz5lZFvo?t=23m9s) that users understand it as a wayfinding tool. When faced with an unfamiliar screen, as many users are regularly (like when running an app for the first time), they will use the floating action button to navigate. Thus, it is a way to prioritize the most important action you want users to take.

  * It's a signpost of what's important. It's a good way to prioritize the most important action you want users to take.
  * It takes up little screen space. Compared to the tab bar, it doesn't take up an entire row.
  * A visually pleasing UI element such as this might not improve usability. However, emotion is a factor in user experience. If a user is pleased to use an app because they find it visually attractive, then that would create positive UX effects.
  * It also improves effectiveness. A study by [Steve Jones demonstrates](http://stevejones.io/img/projects/honors-thesis/SteveJones-Honors-Thesis.pdf) that a floating action button slightly impairs usability when users first interact with the button. However, once users have successfully completed a task using the element, they are able to use it more efficiently than a traditional action button.
  * A floating action button can distract users from content. It is designed to stand out -- it is colorful, raised and grid-breaking. Its design is meant to draw the user's attention. But sometimes its presence can distract the user from the main content.  
![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/Red-FAB-780w-opt.jpg)[52](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)  


> _A red button stands out from the background and focuses user attention. (Image: [Paul van Oijen](https://dribbble.com/PaulVanO)[53](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)) ([View large version](https://www.smashingmagazine.com/wp-content/uploads/2017/05/Red-FAB-large-opt.jpg)[54](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/))  
_

  * It can block content. Take Google's Gmail app for instance. In the example below, you can see that it blocks the "favorite" star, as well as the time stamp for the last row. Additional scrolling is needed whenever the user wants to see this information.  
![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/Gmail-app-preview-opt.png)[55](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)

  * It is also icon-only navigation. By design, the floating action button is a circle containing an icon. It's an icon-only button, with no room for text labels. The problem is that [icons are incredibly hard to understand](http://uxmyths.com/post/715009009/myth-icons-enhance-usability) because they're so open to interpretation. Even a simple action icon like the pencil in the example below can mean different things in different apps.  
![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/Icon-only-navigation-780w-opt.jpg)[57](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)  


> _Same icon, different meanings: "Compose" in the Gmail and Inbox apps, but "Edit" in the Snapseed app. Here, context helps to explain the action. ([View large version](https://www.smashingmagazine.com/wp-content/uploads/2017/05/Icon-only-navigation-large-opt.jpg)[58](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/))  
_

  * Because it is so prominent and intrusive, use only one per screen.  
![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/multiple-FABs-780w-opt.png)[59](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)  


> _Multiple floating action buttons should never appear on screen at one time because that would confuse the visual hierarchy. (_

  * Not every screen should have one, simply because not every screen has an action of such importance.
  * The floating action button is strongly [associated with positive actions](https://material.io/guidelines/components/buttons-floating-action-button.html#buttons-floating-action-button-floating-action-button). Because it is full of character, it's generally taken to be a positive action, like create, favorite, navigate, search and so on. Don't use it for destructive actions, like delete.  
![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/FAB-1-780w-opt.png)[62](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)  


> _View large version_

  * The floating action button could be replaced with a sequence of more specific actions. This would help to surface a set that doesn't really belong at the top but is still important. Apps such as Evernote simplify the controls by using a floating action button for the most important user actions.  
![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/FAB.gif)[64](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)  


  * It can improve transitions between screens, too. The floating action button is not just a round button; it has some transformative properties that you can use to ease users from screen to screen. It can expand, morph and react.  
![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/FAB-1.gif)[65](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)  


> _(Image: [Anish Chandran](https://dribbble.com/anish_chandran)[66](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/))  
_

While with other patterns mentioned in this article, you'd be struggling to minimize the space that the navigation systems take up, the full-screen pattern takes the exact opposite approach. This navigation approach usually devotes the home page exclusively to navigation. Users incrementally tap or swipe to reveal additional menu options as they scroll up and down.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/Full-Screen-Navigation-780w-opt.png)[67](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)

> _(Image: Smashing Magazine) (View large version)_

This pattern works well in task-based and direction-based websites and apps, especially when users tend to limit themselves to only one branch of the navigation hierarchy during a single session. Funnelling users from broad overview pages to detail pages helps them to home in on what they're looking for and to focus on content within an individual section.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/Yelp-preview-opt.png)[70](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)

> _Full-screen navigation options in Yelp_

  * The full-screen navigation pattern is best for achieving simplicity and coherence. You can organize large chunks of information in a coherent manner and reveal information without overwhelming the user; once the user makes their decision about where to go, then you can dedicate the entire screen space to content.
  * Prime real estate will be wasted on chrome. You won't be able to display any content except the navigation options.
  * Use a hamburger menu to hide secondary functionality and keep the focus on the main experience.  
![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/cookly-preview-opt.png)[71](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)  


> _(Image: Cookly via [Dribbble)](https://dribbble.com/shots/1353546-Mobile-Self-Service-Support-Communities/attachments/192600)[72](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)  
_

29 June 2007 was a game changer. From the moment Apple launched the first fully touchscreen smartphone on the market, mobile devices have been dominated by touchscreen interaction.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/touch-gestures.gif)[73](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)

> _(Image: [Aaron Wade](https://dribbble.com/areus)[74](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/))  
_

Gestures immediately became popular among designers, and many apps were designed around experimenting with gesture controls.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/Gesture-driven-to-do-app-Clear-preview-opt.jpg)[75](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)

> _Gesture driven to-do app Clear_

In today's world, the success of a mobile app can largely depend on how well gestures are implemented in the user experience.

This pattern is good when users want to explore the details of particular content easily and intuitively. Users will spend more time with content than they will with navigation menus. So, one of the reasons to use in-context gestures instead of a standard menu is that it's more engaging. For example, as users view page content, they can tap on a card to learn more.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/GitHub.gif)[76](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)

> _This type of navigation takes users on a journey of what they're interested in. Menus simply don't have this engaging effect. (Image: Ramotion)_

  * It removes UI clutter. Building gestures into the heart of your design allows you to make your interfaces more minimal and to save screen space for valuable content.
  * The UI is more natural. Luke Wroblewski talks about a [study](http://www.lukew.com/ff/entry.asp?1197) in which 40 people in 9 different countries were asked to create gestures for 28 different tasks, such as deleting, scrolling and zooming. He found that the gestures tend to be similar across culture and experience. For example, when prompted to "delete," most people -- regardless of nationality -- tried dragging the object off screen.
  * Gestures can be a distinctive feature of a product. Tinder has massively popularized the concept of gesture-based navigation and basically made those swipes a product-defining gesture.
![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/tinder-780w-opt.png)[79](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)

> _View large version_

* The navigation is invisible. One important rule in designing a UI is visibility: Through the menus, all possible actions should be made visible and, therefore, easily discoverable. An invisible UI can be seductively beautiful, but because it's invisible, it will likely have [many usability issues](http://www.jnd.org/dn.mss/gestural_interfaces_a_step_backwards_in_usability_6.html).
* User effort increases. Most gestures are neither natural nor easy to learn or remember. When designing gesture-based navigation, be aware that every time you remove UI clutter, the application's learning curve goes up; and without proper visual hints and cues, users could get confused about how to interact with the app.

  * Make sure you don't have to teach people a whole new way to interact with an interface. Design a familiar experience. In order to design good gesture-based navigation, start by looking at the current state of gestures in the mobile world. For example, if you're designing an email app, you could use a swipe instead of an email gesture, because there's a strong possibility that the gesture would be familiar to many users:  
![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/gmail-inbox-preview-opt.png)[82](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)

  * Educate in context to teach people how to interact with your interface. Avoid long static up-front tutorials. Instead, show only the information that is relevant to the user's current activity.  
![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/Pudding-Monsters-.gif)[83](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)  


> _Pudding Monsters uses an animated hand to present a new scenario to users._

3D Touch is a subtle touch mechanism that was first introduced in Apple's iPhone 6s and 6s Plus. It allows for some new interactions, which Apple defines in two main categories:

  * **Quick actions**  
The iOS home screen isn't just a grid of apps anymore, because 3D Touch allows users to perform actions specific to an app outside of the app, right from the home screen. Pressing firmly on an app icon presents a short list of quick actions: Jump right into taking a selfie from the Camera icon, or immediately navigate to your favorite contacts from the Messages app. ![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/3D-touch-780w-opt.jpg)[84](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)  


> _3D Touch quick-action shortcuts for the camera, messages and maps apps (_

  * **Peek and pop**  
3D Touch allows users to preview content and perform related actions within an app before deciding whether to view the full content. When users press firmly on a piece of content -- such as a mail message in a list -- 3D Touch opens a preview of what that content contains. ![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/3D-touch.gif)[86](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)  


> _3D Touch immediately previews an email, which disappears when the user removes their finger. (Image:_

Using 3D Touch, you can make the most frequent actions the most accessible. Think of 3D Touch like keyboard shortcuts on a desktop computer: They enable people to do repeated tasks more quickly. You can use 3D Touch to help users skip a few steps or to avoid unnecessary steps altogether.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/3D-touch_1.gif)[88](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)

> _From the home screen, the camera lets users access common features: taking a selfie, recording video or taking a normal photo. (Image:_

However, just like keyboard shortcuts, essential features shouldn't be exclusive to 3D Touch. Users must be able to operate your app normally without it.

  * With its shortcut actions, 3D Touch has the potential to save users a lot of time by skipping several taps within an app.
  * By simplifying an interface, 3D Touch enables quick, lightweight interaction. It gives designers and developers new opportunities to simplify their interfaces, while surfacing enhanced functionality for users.
  * Users have to remember which apps have quick actions. 3D Touch still isn't ubiquitous on iOS. Some apps have it, others don't. Users sometimes expect 3D Touch shortcuts for apps that don't have them.

People are shifting to larger-screen phones. Large smartphones don't surprise anyone anymore. But the bigger the display is, the [less easily accessible](http://scotthurff.com/posts/how-to-design-for-thumbs-in-the-era-of-huge-screens) most of the screen is, and the more necessary it is to adapt the design (and navigation, in particular) to improve the user experience.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/Innovative-Navigation-Patterns.png)[91](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)

> _(Image: LukeW)  
_

To solve this problem, designers are forced to look for new solutions to navigation. A couple of interesting innovative solutions can be found in the recently published article "[Bottom Navigation Interface](https://blog.prototypr.io/bottom-navigation-interface-fa4bff52065f)." One solution can be found in a health app named [Ada](https://ada.com). This app's interface layout is a mirror image of a basic interface with a hamburger menu: Everything that's usually at the top is conveniently at the bottom, in the easy-to-access zone.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/ada.png)[94](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)

> _The start screen in Ada for iOS_

The second solution is a concept for a calling app that applies one-handed navigation principles. The method feels good for calling and messaging apps because users tend to use one hand for dialing and texting.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/05/cuberto.gif)[95](https://www.smashingmagazine.com/2017/05/basic-patterns-mobile-navigation/)

> _(Image: cuberto)_

Helping users navigate should be a high priority for every app designer. Both new and returning users should be able to figure out how to move through your app with ease. The easier your product is for them to use, the more likely they'll use it.

> This article is part of the UX design series sponsored by Adobe. The newly introduced Adobe Experience Design CC (Beta) tool is made for a [fast and fluid UX design process](https://adobe.ly/2q0pi6P), as it lets you go from idea to prototype faster. Design, prototype and share -- all in one app.  
You can check out more inspiring projects created with Adobe XD on [Behance](https://www.behance.net/galleries/adobe/5/Experience-Design), and also visit the [Adobe XD blog](https://blogs.adobe.com/creativecloud/design/) to stay updated and informed. Adobe XD is being updated with new features frequently, and since it's in public Beta, you can [download and test it for free](https://adobe.ly/2q0pi6P).

_(ms, vf, al, yk, il)_
