# Progress Indicators in Mobile UX Design

_Captured: 2016-04-02 at 15:20 from [uxplanet.org](https://uxplanet.org/progress-indicators-in-mobile-ux-design-a141e22f3ea0)_

![](https://cdn-images-1.medium.com/freeze/max/30/1*CxeYNeoJ1vbg4Jgef6WJRw.png?q=20)![](https://cdn-images-1.medium.com/max/800/1*CxeYNeoJ1vbg4Jgef6WJRw.png)

_Visibility of system status_ is one of the most important [rules of UI design](https://uxplanet.org/golden-rules-of-user-interface-design-19282aeb06b). The goal behind this rule is pretty obvious-- _to minimize user tension_ you should provide feedback for the user about what is happening with the app _within a reasonable amount of time_. Don't keep the users guessing -- _tell _the user what's happening. And one of the most common forms of such feedback is a _progress indicator_.

In this article, we'll overview the main types of progress indicators and use cases for them.

### Good Interaction Design Provides Feedback

While instant app's response is the best, there are simply times when your app won't be able to comply with the guidelines for speed. Delays are usually caused by slow loading times and latency issues. For such cases, you **must **reassure the users that the _app is working_ on their request and that _actual _progress is being made.

Essentially, feedback answers questions across three categories:

  * Current Status: What's happening?
  * Outcomes: What just happened?
  * Future Status: What will happen next?

#### What is Good Progress Indicator?

Good progress indicators always give some type of immediate feedback. They _notify users that the app needs more time_ to process the user action, and tell (approximately) _how much time it will take_. They have two main advantages:

  * **Reduce user's uncertainty** (app reassures the user that it's working).
  * **Offer a reason to wait and reduce users' perception of time **(app gives the user something to look at while waiting. Thus, makes users pay less attention to the wait itself).

A user's wait time begins the moment when she taps the screen (initiates an action). Immediately, the system should give some _visual feedback_ to communicate that it has received the request.

**Use a progress indicator for any action that takes longer than about _one second_. **For anything that takes less than 1 second to load, it is distracting to use an animation.

#### Types of Indicators

Progress indicators could be _determinate _or _indeterminate:_

  * When indicators are_determinate _theyindicate_ how long an operation will take_ when the percentage complete is detectable.
![](https://cdn-images-1.medium.com/max/800/0*etFyd9H09WNqOynV.gif)

  * When indicators are _indeterminate _theyrequest that the user wait while something finishes when _it's not necessary to indicate how long it will take_.
![](https://cdn-images-1.medium.com/max/800/0*OnojxZLGGsDJNDCU.)

> _Indeterminate progress animation_

Also there could be combinations of these two types of indicators.

![](https://cdn-images-1.medium.com/max/800/0*AmVWS1MBIG3BPeAy.gif)

> _Image source: materialdoc_

### Looped Animation

Showing an animated graphic on loop offers feedback that the system is working, but usually doesn't give enough information about how long the user will have to wait.

As a general rule **you should use looped animation only for fast actions (2-10 seconds).** Making the user to stare at a spinning wheel longer can increase bounce rates.

![](https://cdn-images-1.medium.com/max/800/0*3_FKrfSi3qfIbRQk.gif)

It can also be helpful to add _additional clarity_ for the user by including text that explains _why _the user is waiting (e.g. "Loading comments…").

#### Users Expectations

Default loading icons (like the iOS spinner of gray lines radiating from a central point) _tend to have negative connotations_. They serve a variety of operating system functions, indicating the status of everything from device boot to problems connecting to network or loading a data. Because of that, people dont' like to see only a loading spinner with no indication of progress or time.

![](https://cdn-images-1.medium.com/max/800/0*OkpuB3JmeSlzsYx5.gif)

> _Image source: appnce_

#### Looped Animation Integration

You can integrate looped animation with existing controls, especially buttons. For Android application, a circular loader may be integrated with a floating action button.

![](https://cdn-images-1.medium.com/max/800/0*sM8xtgfVHFRfHNwj.gif)

> _Image source: Material Design._

The thought process here is to confirm that the submission was complete not necessarily the progress. That is shown through the completion of the circle.

#### System or Custom Looped Animation

Facebook app has very interesting experience with looped animation. Rusty Mitchell [highlighted this moment](http://mercury.io/blog/the-psychology-of-waiting-loading-animations-and-facebook) when he talked about a Facebook loading indicator: "When the users were presented with a custom loading animation in the Facebook iOS app (left) they blamed the app for the delay. But when users were shown the iOS system spinner (right), they were more likely to blame the system itself."

### Linear Animation

A _determinate _linear progress indicator should always fill from 0% to 100% and never decrease in value. For _multiple operations_ happening in sequence, you should use the indicator to represent the progress as a whole, and not each individual operation.

![](https://cdn-images-1.medium.com/max/800/0*HZ6Q66Dr1OsFHUS2.gif)

> _Linear Animation. Source: Dribbble_

#### Percent-Done Animation

Uncertain waits are longer than known, finite waits. Percent-done progress indicators are the most informative type of wait-animation feedback. They show the current progress, how much has already been accomplished, and how much is left. A percent-done indicator makes users understand how fast the action is being processed.

As a general rule **you should use percent-done animation for actions that take 10 seconds or more**.

![](https://cdn-images-1.medium.com/max/800/1*L--PZVptC42tnL4R0ZTM1g.jpeg)

> _Source: [Dribbble](https://dribbble.com/shots/870104-Progress-bar)_

#### Provide a General Time Estimate

Don't try to be exact, a simple, "This might take a minute" can be enough to inform the user and encourage them to wait it out.

#### Progressive Animation

Progress bars tell users how long an action is taking, but they're not always correct. You can disguise small delays in your progress bar by starting the progressive animation slower and allow it to move faster as it approaches the end. The progress bar _should never stop_, otherwise users will think the app froze.

![](https://cdn-images-1.medium.com/max/800/1*UdSMKDw4C9Le1qE79z5aFw.gif)

> _Image source: [tympanus](http://tympanus.net/codrops/2015/09/23/elastic-progress/)_

#### Showing Steps

Instead of showing a percentage number, consider showing the _number of steps_. Users might not know how long each step lasts, but knowing the number of steps at least helps them form an estimate.

You can follow a classic step-description way:

Or follow more creative approach:

![](https://cdn-images-1.medium.com/max/800/0*a9YVBfQQDI68Il7Z.gif)

> _Image source: Dribbble_

### Skeleton Screens

You should always try to make the wait more pleasant if you can't shorten the line. And wait-time is a right time for _skeleton screens_ (a.k.a temporary information containers). Skeleton screens are another way _to focus on progress instead of wait times._ A skeleton screen is essentially a blank version of a page into which information is gradually loaded. Such action creates the sense that things are happening immediately as information is incrementally displayed on the screen.

Medium uses this trick, showing a simple wireframe as a placeholder, while the actual content loads. With a such screen, the focus is on content being loaded not the fact that its loading.

### Don't Use Static Progress Indicators

This group of indicators is represented by not moving image or text like "Loading…" or "Please wait…" to indicate that the request has been received. While any feedback is better than none, static indicators don't offer enough information about what is happening and should be replaced with _more meaningful _type of indicator.

![](https://cdn-images-1.medium.com/max/800/0*-IoUUPvNx3NihgGi.gif)

> _Avoid using static progress indicators._

### One Last Thing

To ensure people _don't get bored_ while waiting for something to happen, offer them some distraction. This can be something fun, something unexpected or anything else that catches your users' attention long enough for your app to load. Fine animations can distract your visitors and make them ignore long loading times.

![](https://cdn-images-1.medium.com/max/800/0*jDiW43DO8662Sj52.gif)

> _Image source: dribble_

### Conclusion

Providing feedback is fundamental to a positive user experience. Feedback can _reduce uncertainty_ for users and _increase the time they are willing to wait_.

Thank you!
