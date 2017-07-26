# Best Practices For Animated Progress Indicators

_Captured: 2016-12-09 at 23:53 from [www.smashingmagazine.com](https://www.smashingmagazine.com/2016/12/best-practices-for-animated-progress-indicators/)_

  * [Performance](https://www.smashingmagazine.com/tag/performance/)[User Experience](https://www.smashingmagazine.com/tag/user-experience/)[User Interaction](https://www.smashingmagazine.com/tag/user-interaction/)
  * [10 Comments](https://www.smashingmagazine.com/2016/12/best-practices-for-animated-progress-indicators/)

Visibility of system status is one of the most important principles in user interface design. Users want to feel in control of the system they're using, which means they want to know and understand their current context at any given time, and especially when a system is busy doing work. A wait-animation progress indicator is the most common form of providing a system status for users when something is happening or loading.

To get a better understanding of how your UI designs can benefit from animated progress indicators, it will help to sketch out your (app) ideas. A few months back, Adobe introduced a new design and wireframing app called Experience Design (or Adobe XD), designed for creating interactive wireframes and user interfaces. The app is still in public beta, with features added on a regular base, and you can [download and try it out for free](https://adobe.ly/2hej6U0). In this article, we'll explore the main types of animated progress indicators and provide recommendations on when and how to use each type.

While an instant response from an app is the best, there are times when your app won't be able to comply with the guidelines for speed. A slow response could be caused by a bad internet connection, or an operation itself can take a long time (e.g. install an update for OS). For such cases, in order to minimize user tension, you must reassure the users that the app is working on their request and that actual progress is being made. Thus, you should provide feedback to the user about what is happening with the app within a reasonable amount of time.

A user's wait time begins the moment they initiate an action, and the worst case is when they don't have any indicator the system has received it. When an app fails to notify users that it's taking time to complete an action, users often think the app didn't receive the request, and they try again. Plenty of extra clicks and taps have resulted due to a lack of feedback.

Any action, such as clicking a button or pulling to refresh, should have an immediate reaction. It's essential to give some visual feedback immediately after receiving the request from the user to indicate that the process has initiated.

![Pull-To-Refresh action. Image credit: Behance](https://www.smashingmagazine.com/wp-content/uploads/2016/11/Pull-To-Refresh-action.gif)[2](https://www.smashingmagazine.com/2016/12/best-practices-for-animated-progress-indicators/)

> _Pull-To-Refresh action Image credit:_

When the app takes more than 0.1 second but less than one second to respond to user input, it feels like the app is causing the result to appear. Although users notice a short delay, they stay focused on their current task. After one second, the user's attention begins to wander, and they notice that they're waiting for a slow app to respond.

In order to reduce a user's uncertainty, offer a reason to wait with a progress indicator for any action that takes longer than about _one second_ (Note: the use of animation isn't recommended for anything that takes less than one second to load, because users might feel anxious about what just flashed on the screen). Animated progress indicators mitigate the negative effects of waiting and prolong the user's attention on the site or in the app.

Progress indicators tell users that the app needs more time to process the last user action. The simplest form of process indicator is _indeterminate_ -- these types of indicators request users to wait while something finishes, but they don't indicate how long it will take.

![](https://www.smashingmagazine.com/wp-content/uploads/2016/11/Infinite-looped-animation.gif)[4](https://www.smashingmagazine.com/2016/12/best-practices-for-animated-progress-indicators/)

> _Infinite looped animation offers feedback that the system is working, but doesn't provides any information about how long the user will have to wait. Image credit:_

As a general rule, you should use this type of progress indicator for fast actions (2-10 seconds). Making the user stare at a spinning wheel or infinite linear animation longer can increase bounce rates for your website or cause people to close your app.

Another type of progress indicators tell _how long an operation will take_ (approximately or exactly). These types of indicators are called _determinate._ They are the most informative type of wait-animation feedback since they show the current progress, how much has already been accomplished, and how much is left. A visual indicator that progresses towards completion puts the user at ease and increases their willingness to wait.

There are two popular types of animated progress indicators -- _looped animation_ and _percent-done indicator_.

Since the majority of looped animation is indeterminate and serve a variety of types of delays, including long ones, this type of progress indicator tends to have negative connotations. For example, a default loading icon in Apple iOS (spinner of gray lines radiating from a central point area) serves a variety of operating system functions, indicating the status of everything from device boot to problems connecting to network or loading data. Because of that, users don't like to see only a loading spinner with no indication of progress or time.

![Watching a loading spinner is like watching the clock tick down — when you do, time seems to stop](https://www.smashingmagazine.com/wp-content/uploads/2016/11/loading-spinner.gif)[9](https://www.smashingmagazine.com/2016/12/best-practices-for-animated-progress-indicators/)

> _Watching a loading spinner is like watching the clock tick down -- when you do, time seems to stop. Image credit: appance_

A percent-done indicator is a determinate progress indicator that fills from 0% to 100% and never decreases in value. Both linear and circular progress indicators may be percent-done.

![Loading bar](https://www.smashingmagazine.com/wp-content/uploads/2016/11/Linear-percent-done-progress-indicator-opt.jpeg)[11](https://www.smashingmagazine.com/2016/12/best-practices-for-animated-progress-indicators/)

> _Linear percent-done progress indicator Image credit:_

![Circular percent-done progress indicators](https://www.smashingmagazine.com/wp-content/uploads/2016/11/percentdone-opt.jpg)[13](https://www.smashingmagazine.com/2016/12/best-practices-for-animated-progress-indicators/)

> _Circular percent-done progress indicators Image credit:_

As a general rule of thumb, you should use a percent-done animation for longer processes that take 10 or more seconds. Based on Jakob Nielsen's [research about response times](https://www.nngroup.com/articles/response-times-3-important-limits/), 10 seconds is a limit for users to keep their attention on a task, after this time users quickly grow impatient if they don't have enough information on how long they have to wait for the result.

You should always try to make the wait more pleasant if you can't shorten the line.

Many times, if users are informed, they may be more patient. It can be helpful to add additional clarity by including text that tells the user what is happening or explains why the user is waiting.

Don't try to be exact, a simple, "this might take five minutes" can be enough for the users and encourage them to wait it out.

![Software update estimation in Apple iOS](https://www.smashingmagazine.com/wp-content/uploads/2016/11/Software-update-estimation-in-Apple-iOS-opt.png)[18](https://www.smashingmagazine.com/2016/12/best-practices-for-animated-progress-indicators/)

> _Software update estimation in Apple iOS_

For time-consuming operations where it's unknown in advance how much work has to be done, it may be impossible to use a percent-done indicator, but you still can provide running progress feedback regarding the absolute amount of work done. In this case, consider showing the number of steps, because knowing the number of steps helps users at least form an approximate estimate.

A progress bar makes users develop an expectation for how fast the action is being processed. As a result, any unexpected freezes will be noticed and will impact user satisfaction. The worst possible case is when progress bar approaches 99% and suddenly stops. Most users will be frustrated by this behavior because it makes them think the app is frozen. Hopefully, there is a simple solution -- you can disguise small delays in your progress bar by moving it instantly and steadily.

![Image credit: Behance](https://www.smashingmagazine.com/wp-content/uploads/2016/11/progress-bar-opt.gif)[20](https://www.smashingmagazine.com/2016/12/best-practices-for-animated-progress-indicators/)

Keep in mind that perception can be just as important as raw speed. In order to [make a progress bar](http://johnnyholland.org/2008/11/the-effect-of-the-progress-bar/)_[ feel faster_](http://johnnyholland.org/2008/11/the-effect-of-the-progress-bar/) to users you can start the progressive animation slower and allow it to move faster as it approaches the end. This way, you give users a rapid sense of completion time.

![Image credit: Behance](https://www.smashingmagazine.com/wp-content/uploads/2016/11/make-progress-bar-feel-faster-opt.gif)[24](https://www.smashingmagazine.com/2016/12/best-practices-for-animated-progress-indicators/)

> _Image credit: Behance_

Creative progress indicators can reduce a user's perception of time. If an app gives users something interesting to look at while waiting, this makes users pay less attention to the wait itself. Thus, to ensure people don't get bored while waiting for something to happen, offer them a distraction. For example, this can be something fun…

![Image Credit: Behance](https://www.smashingmagazine.com/wp-content/uploads/2016/11/Visual-Distraction-opt.jpg)[26](https://www.smashingmagazine.com/2016/12/best-practices-for-animated-progress-indicators/)

Or something adorable…

![Image credit: Vimeo](https://www.smashingmagazine.com/wp-content/uploads/2016/12/adorable-kitten.gif)[28](https://www.smashingmagazine.com/2016/12/best-practices-for-animated-progress-indicators/)

> _Image credit: Vimeo_

Or something unexpected that catches users' attention long enough for your app to load.

![Fine animations can distract your visitors and make them ignore long loading times. Image credit: Behanc](https://www.smashingmagazine.com/wp-content/uploads/2016/11/Fine-animations.gif)[30](https://www.smashingmagazine.com/2016/12/best-practices-for-animated-progress-indicators/)

> _Fine animations can distract your visitors and make them ignore long loading times. Image credit: Behance_

As you've just learned, when things are going to take a while, we let people know that using progress indicators. However, while the intentions behind progress indicators are good, the end result can turn out to be bad. As Luke Wroblewski mentioned in his [article](http://www.lukew.com/ff/entry.asp?1797): "Progress indicators by definition call attention to the fact that someone needs to wait. It's like watching the clock tick down -- when you do, time seems to go slower." With the introduction of progress indicators to our UIs, designers often make people watch the clock. While it's better than nothing, when you design UIs you should always try to make the wait more pleasant.

Hopefully, there's a good alternative of progress indicators, the technique that lets people have a great experience while they are waiting. And this technique has a name, _skeleton screen_. Skeleton screens (a.k.a temporary information containers) are essentially a blank version of a page into which information is gradually loaded. Rather than show a loading indicator, skeleton screens focus on _actual progress_ and create anticipation of what is to come. This creates the sense that things are happening immediately as information is incrementally displayed on the screen and people think that the application is acting while they wait.

Medium uses this trick, showing a simple wireframe as a placeholder, while the actual content loads. The load screen also makes the user familiar with the overall structure of the content being loaded.

![Medium](https://www.smashingmagazine.com/wp-content/uploads/2016/12/medium-600px-preview-opt.png)[33](https://www.smashingmagazine.com/2016/12/best-practices-for-animated-progress-indicators/)

> _Medium focus on content being loaded, not the fact that it's loading. Image Source:_

No matter how fast we make our app and sites, there will often be something that takes time to process. Wait animations, such as loading spinners and percent-done indicators, reduce uncertainty by informing users of the current working state and increase the likelihood that the user will stay and wait for the information to load. A rule of thumb is to use a looped indicator or skeleton screens for reasonably fast operations taking between two and ten seconds, and a percent-done indicator for operations taking more than about ten seconds. When choosing between looped animation and skeleton screens, it's probably a good idea to favor latter because they contain one important advantage -- they can improve the feel of any action taking longer than a few milliseconds.

> This article is part of the UX design series sponsored by Adobe. The newly introduced [Experience Design app](https://adobe.ly/2hej6U0) is made for a fast and fluid UX design process, creating interactive navigation prototypes, as well as testing and sharing them -- all in one place. 
> 
> You can check out more inspiring projects created with Adobe XD on [Behance](http://adobe.ly/1U9LS0E), and also visit the Adobe XD blog to stay updated and informed. Adobe XD is being updated with new features frequently, and since it's in public Beta, you can [download and test it for free](https://adobe.ly/2hej6U0).

_(il, ms, vf, aa)_
