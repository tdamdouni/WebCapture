# An Introduction to the Reduced Motion Media Query

_Captured: 2017-02-13 at 02:33 from [css-tricks.com](https://css-tricks.com/introduction-reduced-motion-media-query/)_

The open web's success is built on interoperable technologies. The ability to control animation now exists alongside important features such as zooming content, installing extensions, enabling high contrast display, loading custom stylesheets, or disabling JavaScript.

Sites all too often inundate their audiences with automatically playing, battery-draining, resource-hogging animations. The need for people being able to take back control of animations might be more prevalent than you may initially think.

When it was released in 2013, iOS 7 featured a dramatic reworking of the operating system's visuals. Changes included translucency and blurring, a more simplified "flat" user interface, and dramatic motion effects such as full-screen zooming and panning.

While the new look was generally accepted, many people using the updated operating system [reported experiencing motion sickness and vertigo](http://simplyaccessible.com/article/balance-awareness/). User interface movement didn't correspond with users' feeling of movement or spatial orientation, triggering the reported effects.

Although technology inflicting adverse effects existed before this, the popularity of iOS gave the issue prominence. Apple has great support for accessibility, so [an option in the operating system preferences](https://support.apple.com/en-us/HT202655) to disable motion effects for those with vestibular disorders was added in response.

Your vestibular system provides an internal sensor to communicate your body's physical position and orientation in the world, and is key to controlling balance and eye movement. [Vestibular disorders](http://a11yproject.com/posts/understanding-vestibular-disorders/) can cause your vestibular system to struggle to make sense of what is happening, resulting in loss of balance and vertigo, migraines, nausea, and hearing loss. Anyone who has spun around too quickly is familiar with a confused vestibular system.

Vestibular disorders can be caused by both genetic and environmental factors. It's part of the larger [spectrum of conditions](http://webaim.org/intro/) that make up accessibility concerns and it affects more than [70 million people](http://vestibular.org/understanding-vestibular-disorder).

Remember: [we're all just temporarily-abled](https://uxmag.com/articles/we-re-just-temporarily-abled). Feeling a little dizzy might not seem like that big a deal, but that moment of nausea might be a critical one: losing balance and falling down, a migraine during an interview, nausea-triggered vomiting while working a food service job, passing out while operating a car UI, etc.

So what can we do about it?

Safari 10.1 [introduces the Reduced Motion Media Query](https://developer.apple.com/library/prerelease/content/releasenotes/General/WhatsNewInSafari/Articles/Safari_10_1.html#//apple_ref/doc/uid/TP40014305-CH12-DontLinkElementID_60). It is a non-vendor-prefixed declaration that allows developers to "create styles that avoid large areas of motion for users that specify a preference for reduced motion in System Preferences."

The syntax is pretty straightforward:
    
    
    @media (prefers-reduced-motion) {
      .background {
        animation: none;
      }
    }

Safari will parse this code and apply it to your site, letting you provide an alternative experience for users who have the Reduced Motion option enabled. Think of this new Media Query [like `@supports`](https://www.lottejackson.com/learning/supports-will-change-your-life): describe the initial appearance, then modify the styles based on capability.

So, how do we check this bad boy out? Provided you're up to date with MacOS, you should be able to check it out in [Safari Technical Preview](https://developer.apple.com/safari/technology-preview/).

Go to System Preferences, select the Accessibility options, click the Display tab, and check the **Reduce Motion** option. You'll see that the example animation in the CodePen example below updates when the checkbox is toggled. The pulsing circle is changed to an inert square:

Here's a quick video if you don't have access to this:

Need a more practical example of how the media query could be applied?

[This feature from the New York Times](https://www.nytimes.com/interactive/2016/09/30/opinion/penn-station-reborn.html?_r=1) opens with full-screen autoplaying video that simulates falling from a great height.

![](https://cdn.css-tricks.com/wp-content/uploads/2017/02/falling.jpg)

> _It's sudden and unexpected, and a strong candidate to trigger vertigo._

The Reduced Motion Media Query, could provide an alternative that replaces the falling animation with a screenshot of the final frame of the animation. The content of the article is still communicated thematically. A beautiful rendering of the proposed Gateway project draws the reader in. The other less-dramatic animations in the feature remain unchanged, as they are both subtle with their transitions and activated by the reader deliberately browsing the page.

The impact of the story is preserved while not having the potential to inflict harm on the person trying to read it. It's a win-win!

Even if you ignore all the benefits of building accessible sites, it's probably a good idea to get [comfortable working with User Queries](https://decadecity.net/blog/2015/06/28/user-queries).

As capabilities traditionally controlled by the operating system are [integrated into the browser](https://whatwebcando.today/), crafting experiences that gracefully adapt to a person's preferences will become increasingly important. Reduced motion is likely to be supported by other browsers soon as part of a wave of new User Queries.

The browser's opinion needs to also be considered. Without a designed alternative, the browser's fallback settings for reduced motion or may not create a desirable experience. In fact, if animation alone communicates important information about your site, it may be lost.

Doing so would be a dramatic and not necessarily valid option. Animation, when used with discretion and restraint, can be a great way to communicate relationships between parts of your site or transitions between states, direct a person's attention, simplify the understanding of complicated concepts, or to simply add some fun. Used properly, animations can aid in accessibility by helping [address cognitive accessibility concerns](http://webaim.org/articles/cognitive/).

If you would like more information on what kinds of animation are more likely to trigger vestibular issues, Val Head has written [an excellent post on A List Apart](http://alistapart.com/article/designing-safer-web-animation-for-motion-sensitivity) on the subject.
