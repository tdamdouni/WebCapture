# Accessible UI Components For The Web

_Captured: 2017-02-06 at 22:00 from [medium.com](https://medium.com/@addyosmani/accessible-ui-components-for-the-web-39e727101a67#.4aa931wg2)_

# Accessible UI Components For The Web

> _Web Accessibility Tooling covered in the new Totally Tooling Tips s03e08_

To be **accessible**, UI components need to work across multiple devices with varying screen-sizes and different kinds of input. Moreover, components should be usable by the broadest group of users, including those with disabilities.

**When designing for accessibility, there are four key areas of disability to consider: visual, hearing, mobility and cognition.**

**Visual issues** can range from an inability to distinguish colors to no vision at all.

  * Ensure a minimum [contrast ratio threshold](http://www.w3.org/TR/WCAG20/#visual-audio-contrast-contrast) is met for text content.
  * Avoid communicating information [using solely color](http://www.w3.org/TR/2008/REC-WCAG20-20081211/#visual-audio-contrast-without-color) and ensure that all text is [resizable](http://www.w3.org/TR/2008/REC-WCAG20-20081211/#visual-audio-contrast-scale).
  * Ensure all user interface components can be used with assistive technologies such as screen readers, magnifiers and braille displays. This entails ensuring that UI components are marked up such that accessibility APIs can programmatically determine the _role_, _state_, _value_ and _title_ of any element.

**Hearing issues** mean a user may have issues hearing sound emitted from a page.

  * Make the content understandable using [text alternatives](http://www.w3.org/TR/WCAG20/#media-equiv-av-only-alt) for all content that is not strictly text.
  * Ensure you test that your UI components are still functional [without sound](http://www.w3.org/TR/2008/REC-WCAG20-20081211/#content-structure-separation-understanding).

**Mobility issues** can include the inability to operate a mouse, a keyboard or touch-screen.

  * Make the content of your UI components [functionally accessible from a keyboard](http://www.w3.org/TR/wai-aria-practices/#keyboard) for any actions one would otherwise use a mouse for.
  * Ensure UI components are correctly marked up for assistive technologies; these users may use technologies such as voice control software and physical switch controls, which tend to use the same APIs as other assistive technologies like screen readers.

**Cognitive issues** mean a user may require assistive technologies to help them with reading text, so it's important to ensure text alternatives exist.

  * Avoid a visual presentation that is [repetitive](http://www.w3.org/TR/WCAG20/#time-limits) or flashing as this can cause some users [issues](http://www.w3.org/TR/WCAG20/#seizure).
  * Avoid interactions that are timing-based.

This may seem like a lot of bases to cover, but we'll walk through the process for assessing and then improving the accessibility of your UI component.

### Is your UI component accessible?

#### Summary (tl;dr)

When auditing your application for accessibility, ask yourself:

  * **Can you use your UI component with the keyboard only?** Does it manage to focus and avoid focus traps? Can it respond to the appropriate keyboard events?
  * **Can you use your UI component with a screen reader?** Have you provided text alternatives for any information which is presented visually? Have you added semantic information using ARIA?
  * **Can your UI component work without sound?** Turn off your speakers and go through your use cases.
  * **Can it work without color?** Ensure your UI component can be used by someone who cannot see colors. A helpful tool for simulating color blindness is a Chrome extension called [SEE](https://chrome.google.com/webstore/detail/see/dkihcccbkkakkbpikjmpnbamkgbjfdcn), (try all four forms of color blindness simulation available). You may also be interested in the [Daltonize](https://chrome.google.com/webstore/detail/chrome-daltonize/efeladnkafmoofnbagdbfaieabmejfcf) extension which is similarly useful.
  * **Can your UI component work with high-contrast mode enabled? **All modern operating systems support a high contrast mode. _[High Contrast_](https://chrome.google.com/webstore/detail/high-contrast/djcfdncoelnlbldjfhinnjlhdjlikmph?hl=en) is a Chrome extension available that can help here.

Native controls (such as <button> and <select>) have accessibility built-in by the browser. They are focusable using the tab key, respond to keyboard events (like Enter, space and arrow keys), and have semantic roles, states and properties used by accessibility tools. The default styling should also meet the accessibility requirements listed above.

Custom UI components (with the exception of components that extend native elements like <button>) do not have any built-in functionality, including accessibility, so this needs to be provided by you. A good place to start when implementing accessibility is to compare your components to an analogous native element (or a combination of several native elements, depending on how complex your component is).

The following is a list of questions you can ask yourself when attempting to make your UI components more accessible.

### Can your UI component be used with the keyboard alone?

Ideally, ensure that all functionality in your UI component can be reached by a keyboard. During your UX design, think about how you would use your element with the keyboard alone, and figure out a consistent set of keyboard interactions.

Firstly, ensure that you have a sensible focus target for each component. For example, a complex component like a menu may be one focus target within a page, but should then manage focus within itself so that the active menu item always takes focus.

![](https://cdn-images-1.medium.com/max/800/0*fBdUEDMEoXoL4IiQ.png)

> _Managing focus within a complex element_

#### Using tabindex

The tabindex attribute allows elements / UI components to be focused using the keyboard. Keyboard-only and assistive technology users both need to be able to place keyboard focus on elements in order to interact with them. Native interactive elements are implicitly focusable, so they don't need a tabindex attribute unless we wish to change their position in the tab order.

**There are three types of tabindex values:**

  * **tabindex="0" **is the most common, and will place the element in the "natural" tab order (defined by the DOM order).
  * **a tabindex value greater than 0** will place the element in a _manual_ tab order -- all elements in the page with a positive tabindex value will be visited in numerical order before elements in the natural tab order.
  * **a tabindex value equal to -1** will cause the element to be _programmatically_ focusable, but not in the tab order.

For custom UI components, always use tabindex values of 0 or -1, as you won't be able to determine the order of elements on a given page ahead of time -- and even if we did, they may be subject to change. A tabindex value of -1 is particularly useful for managing focus within complex components as described above.

Also ensure that focus is always visible, whether by allowing the default focus ring style, or applying a discernible focus style. Remember not to trap the keyboard user -- focus should be able to be moved away from an element using only the keyboard.

_You may also be interested in the roving tabindex or aria-activedescendant approaches, covered over on __[MDN_](https://developer.mozilla.org/en-US/docs/Web/Accessibility/Keyboard-navigable_JavaScript_widgets#Technique_1_Roving_tabindex)_._

#### Using autofocus

The HTML autofocus attribute allows an author to specify that a particular element should automatically take focus when the page is loaded. It is already supported on [all web form controls](https://html.spec.whatwg.org/multipage/forms.html#association-of-controls-and-forms), including <input>. To autofocus elements in your own custom UI components, call the [focus()](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement.focus) method supported on all HTML elements that can be focused (e.g document.getElementById('myButton').focus()).

#### Adding keyboard interaction

Once your UI component is focusable, try to provide a good keyboard interaction story when a component is focused, by handling appropriate keyboard events -- for example, allow the user to use arrow keys to select menu options, and space or enter to activate buttons. The ARIA [design patterns guide](http://www.w3.org/TR/wai-aria-practices/#aria_ex) provides some guidance here.

Finally, ensure that your keyboard shortcuts are discoverable. For example, a common practice is to have a keyboard shortcut legend (on-screen text) to inform the user that shortcuts exist. For example, "Press ? for keyboard shortcuts". Alternatively a hint such a tooltip could be used to inform the user about the shortcut existing.

The importance of managing focus cannot be understated. One example is a navigation drawer. If adding a UI component to the page you need to direct focus to an element inside of it otherwise users may have to tab through the entire page to get there. This can be a frustrating experience, so be sure to test focus for _all_ keyboard navigable components in your page.

### Can you use your UI component with a screen reader?

Around 1-2% of users will be using a screen reader. At the end of this article, we list some screen readers which are free to use: try using your component with at least one of these screen readers. Can you determine all important information and interact with the component using the screen reader and keyboard alone?

The following questions should help guide you in addressing screen reader accessibility:

#### Do all components and images have meaningful text alternatives?

Wherever information about the _name_ or _purpose_ of an interactive component is conveyed visually, an accessible text alternative needs to be provided.

For example, if your <fancy-menu> UI component only displays an icon such as..

![](https://cdn-images-1.medium.com/max/800/0*uSnlWw_Mn3yVyT88.png)

> _Settings menu icon_

to indicate that it is a settings menu, it needs an accessible text alternative such as "settings", which conveys the same information. Depending on context, this may use an alt attribute, an aria-label attribute, an aria-labelledby attribute, or plain text in the Shadow DOM. You can find general technical tips in [WebAIM Quick Reference](http://webaim.org/resources/quickref/).

Any UI component which displays an image should provide a mechanism for providing alternative text for that image, analogous to the alt attribute.

#### Do your components provide semantic information?

Assistive technology conveys semantic information which is otherwise expressed to sighted users via visual cues such as formatting, cursor style, or position. Native elements have this semantic information built-in by the browser, but for custom components you need to use [ARIA](http://www.w3.org/WAI/PF/aria/) to add this information in.

As a rule of thumb, any component which listens to a mouse click or hover event should not only have some kind of keyboard event listener, but also an ARIA role and potentially ARIA states and attributes.

For example, a custom <fancy-slider> UI component might take an ARIA role of slider, which has some related ARIA attributes: aria-valuenow, aria-valuemin and aria-valuemax. By binding these attributes to the relevant properties on your custom component, you can allow users of assistive technology to interact with the element and change its value, and even cause the visual presentation of the element to change accordingly.

![](https://cdn-images-1.medium.com/max/800/0*Xqo2LP8DT5v7hV-h.png)

> _A range slider component_
    
    
    <fancy-slider role="slider" aria-valuemin="1" aria-valuemax="5" aria-valuenow="2.5"></fancy-slider>

#### Can users understand everything without relying on color?

Color shouldn't be used as the only means of conveying information, such as indicating a status, prompting for a response or distinguishing a visual custom component. For example, if you created an <fancy-map> component using color to distinguish between heavy, moderate and light traffic, an alternative means of distinguishing traffic levels should also be made available: one solution might be to hover over an element to display information in a tooltip.

#### Is there sufficient contrast between the text/images and the background?

Any text content displayed in your component should meet the [minimum (AA) contrast bar](http://www.w3.org/TR/2008/REC-WCAG20-20081211/#visual-audio-contrast-contrast). Consider providing a high-contrast theme which meets the [higher (AAA) bar](http://www.w3.org/TR/2008/REC-WCAG20-20081211/#visual-audio-contrast7), and also ensure that user agent style sheets can be applied if users require extreme contrast or different colors. You can use this [Color Contrast Checker](http://webaim.org/resources/contrastchecker/) as an aid when doing design.

#### Is the moving or flashing content in your components stoppable and safe?

Content that moves, scrolls or blinks that lasts for anything more than 5 seconds should be able to be paused, stopped or hidden. In general, try to flash no more than three times per second.

### Accessibility Tooling

A number of tools are available that can assist with debugging the accessibility of your visual components. These include:

  * [aXe](http://www.deque.com/products/axe/) -- automated accessibility testing for your framework or browser of choice
  * The [Accessibility DevTools extension](https://chrome.google.com/webstore/detail/accessibility-developer-t/fpkknkljclfencbdbgkenhalefipecmb?utm_source=chrome-ntp-icon) for Chrome provides a helpful audit for discovering accessibility issues, including issues within Shadow DOM. It's powered by the [Accessibility DevTools module](http://bit.ly/a11y-devtools-module) and a [CLI](http://bit.ly/a11y-ci) is available that also uses this work for continuous integration audits.
![](https://cdn-images-1.medium.com/max/800/1*k7-YgmcM8rNy_aKZHs2CXg.png)

> _In addition to audits, the Accessibility DevTools extension also provides insights into color issues-- above it points to AA and AAA contrast ratio scores and suggestions. Clicking each box toggles a color-change suggestion against the currently selected DOM node._

In case you're wondering, work is underway to bring first-class accessibility inspection natively to the Chrome DevTools without the need of an extension too:

![](https://cdn-images-1.medium.com/max/800/1*si5Xm0401h-x9OiJjRn8Qg.png)

> _Native Accessibility Inspection is coming to DevTools too! Try it out: http://bit.ly/a11y-experiment_

  * [Tenon.io](https://tenon.io/) -- useful for testing common accessibility problems. Tenon has strong integration support across build tools, browsers (via extensions) and even text editors.
  * You can examine the way that assistive technologies see web content by using [Accessibility Inspector](https://developer.apple.com/library/mac/documentation/Accessibility/Conceptual/AccessibilityMacOSX/OSXAXTesting/OSXAXTestingApps.html#//apple_ref/doc/uid/TP40001078-CH210-TPXREF101) (Mac), or [Windows Automation API Testing Tools](http://msdn.microsoft.com/en-us/library/windows/desktop/dd373661%28v=vs.85%29.aspx) and [AccProbe](http://accessibility.linuxfoundation.org/a11yweb/util/accprobe/) (Windows). Additionally you can see the full accessibility tree that Chrome creates by navigating to _chrome://accessibility_.
  * The best way to test for screen reader support on a Mac is using the VoiceOver utility. You can use ⌘F5 to enable/disable, Ctrl+Option <--> to move through the page and Ctrl+Shift+Option + ↑↓ to move up/down tree. For more detailed instructions, see the [full list of VoiceOver commands](http://www.apple.com/voiceover/info/guide/_1131.html) and the [list of VoiceOver Web commands](http://www.apple.com/voiceover/info/guide/_1131.html#vo27972).
  * [tota11y](http://khan.github.io/tota11y/) is a useful visualiser for assistive technology issues built by Khan Academy. It's a script that adds a button to your document that triggers several plugins for annotating things like insufficient contrast ratio and other a11y violations
  * [ally.js](http://allyjs.io/) (by Rodney Rehm) is a library that tries to simplify adding a few accessibility features to your app. It helps query the DOM for all focusable or tabbable elements, traps focus to specific DOM sub-trees, helps determine how focus has changed and comes with several other helpers.
  * On Windows, [NVDA](http://www.nvaccess.org/) is a free, open source screen reader which is fully featured and rapidly gaining in popularity. However, note that it has a much steeper learning curve for sighted users than VoiceOver.
  * ChromeLens helps develop for the visually impaired. It's also got great support for visualising keyboard navigation paths <http://chromelens.xyz/>
![](https://cdn-images-1.medium.com/max/800/1*0_1rEB0yjRHT2AILjo8xLQ.jpeg)

> _ChromeLens DevTools extension, with multiple options for emulating different forms of blindness, tab tracing and accessibility auditing._

  * [ChromeVox](http://www.chromevox.com/) is a screen reader which is available as a Chrome extension, and built in on ChromeOS devices. However, it currently doesn't read content in Shadow DOM.

_Note: An older version of this article was previously published __[here_](https://docs-05-dot-polymer-project.appspot.com/0.5/articles/accessible-web-components.html)_. Big thanks goes to __[Alice Boxhall_](https://twitter.com/sundress)_ and __[Rob Dodson_](https://twitter.com/rob_dodson)_ for helping out with the original article and reviews of this episode of Totally Tooling Tips._

PS: If you're interested in learning more, you can learn about Accessibility fundamentals in this free Udacity course <https://bit.ly/web-a11y>
