# Feel-good Interfaces

_Captured: 2015-12-31 at 22:17 from [medium.com](https://medium.com/moments/feel-good-interfaces-9c4b9590b80d#.xh5pifm32)_

In the day and age where digital interfaces are becoming rapidly pervasive in all aspects of our lives, I hate it when I see an interface where the attention given to small details is little and the result is agony, frustration and eventual abandonment.

> Every interface & design invokes a certain emotion from the user.

> We, humans are great at discerning things than articulating them. -- Jony Ive

Common expectations by the user are trust and stability in a product that has passed the "[toothbrush test](http://www.businessinsider.in/Heres-The-Toothbrush-Test-Googles-CEO-Uses-To-Make-Acquisition-Decisions/articleshow/40375194.cms)" as Larry Page likes to call it. Others are just one-trick ponies we use and forget. There are a lot of factors that contribute to invoking these feelings. But purely from the standpoint of **how** the app is built/designed, some patterns do emerge. If the product really is solving a problem for you in your life, it boils down to these details to ensure whether the app completely nails it or that it will always have that minor annoyance that you have to live with. You will use the app everyday but will always hate that small quirk and will jump ship as soon as a better alternative is available.

I can think of a few things that, if attended to properly, can help your design feel solid, masterfully engineered and user-focused to the core -- something that users love to evangelize to their friends and family because they love using it.

#### Pointers for designing a solid interface

Most of the points mentioned below are true for mobile as well as web apps. The list is by no means exhaustive.

  1. Don't change **content-container size** too often. Keep it the same even if the content changes. If you have to change the container size, graceful transition is the least you can do to helpfully guide the user.
  2. Don't force **unnecessary reloads** or new tab opens. Whenever possible, handle refreshing your data then and there. Reloads incur cognitive overload for the user as he has to get used to the structure of the new page from scratch.
  3. When possible, have a [visited](http://www.w3schools.com/css/css_link.asp) state for links across the site. This is overlooked many a times but it's a _good to have_ to inform users where they've already been. I myself use this state of the link (on all sites that have these) to track the page I recently visited on a site. Sites like Google and Wikipedia use this heavily to improve usability.
  4. Background processes should never block the UI. As much as possible, keep the **UI non-blocking**. Have meaningful indicators to denote ongoing processes.
  5. **Errors** should always point to a solution. Never leave the user hanging, trying to make sense out of a cryptic error message. When possible, **a good rule of thumb here is to have preventive indicators instead of reactive errors.**
  6. **Progress indicators** are a good opportunity to engage user with something. Don't keep them staring at blank boring spinners. Think about including small tips related to your product or explore a few easter eggs here and there.
  7. **Insanely subtle animations** play a solid role in **tightening up** of the UI. Make the animation slower & it feels laggy and overbearing. Animations in the UI should never slow down the user. One good rule of thumb is that the extent when you "notice" the animation, it's too long. Transitions, movements and animations are to be felt, not to be stared at.
  8. Make interfaces comply to **real-life dynamics** and laws of physics. People relate to physical objects and their motion, gravity and manually generated forces since these are a part of our daily lives. If your interface breaks the laws, e.g. if there are unnatural spins, turns or animations, movement against gravity that looks artificial, it gets taxing to comprehend the meaning & structure of the interface.
  9. Interplay between screens -- their stacking, folding, turning, flipping and other modifications that are a part of the interface have to be**true to life**. Depth, solidity, volume, layering and transitions in a 3D plane has to conform to the laws of physics and how objects behave in real life. For example, If there is a series of screens in your app, make screens move forward and backward so that it's easier to understand how the app structure is laid out. If there's a part of UI sliding in from the bottom, when the user is done with it, it has to slide out back to the bottom where it came from. That trains the user about where things are in the app. It helps the user create a mental model of the app quickly when motions and screen-stacking are well defined.
  10. Clever use of **sonic feedback** (Facebook uses this effectively on mobile & web) for user input and actions is a good idea to signal the user of various states.
  11. Design excellent **empty states** and guide the user through product initially. Empty states are an opportunity to communicate humanely with your user.
  12. Have as less screens as possible in the app ([Square Cash](https://cash.me/) is an excellent example). If you can do away with just a modal or a popup to display a piece of information, **cut that extra screen**. Something popping up on top of an already understood and learned screen is way better than figuring out a whole new view.
  13. Define **relaxed touch targets** all over the app. Make tapping experience forgiving and responsive.

> _Users remember how your design made them feel._

As you probably have noticed, all these above factors relate to what the user "feels" more than what he sees. You cannot put a metric to measure the feelings of the user using your app. What you can do is to ensure you did your best removing every bit of annoyance so that the user journey is as smooth as possible. Your product is a movie that has to be so well written, defined and choreographed that the user leaves happy every single time.

User-testing is your best friend to get these details right. Gather as much feedback as possible from incessant testing and fine-tune the little details. Your users **will** notice those details, **feel** the love and will thank you for it.

> Because we all love the apps that create the most memorable user experiences we cherish everyday.

![](https://cdn-images-2.medium.com/max/800/1*6PtMIJED7jW3EBYFGWbR1A.png)

_Do recommend it to others if you liked the article._
