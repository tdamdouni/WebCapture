# Hyperlinking Beyond the Web

_Captured: 2018-07-18 at 19:23 from [dzone.com](https://dzone.com/articles/hyperlinking-beyond-the-web-css-tricks?edition=385251&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-07-18)_

[Learn how error monitoring with Sentry](https://dzone.com/go?i=299453&u=https%3A%2F%2Fsentry.io%2F_%2Flp%2Ftelephone-game-ebook%2F%3Futm_source%3Dadvertisement%26utm_medium%3Dtext%26utm_content%3Ddzonewebdevzone%26utm_campaign%3Dsponsorship) closes the gap between the product team and your customers. With Sentry, you can focus on what you do best: building and scaling software that makes your users' lives better.

[Atishay Jain, on CSS Tricks, writes](https://css-tricks.com/hyperlinking-beyond-the-web/) about an area close to my heart, linking:

> Hyperlinks are the oldest and the most popular feature of the web. The word hypertext (which is the ht in http/s) means text having hyperlinks. The ability to link to other people's hypertext made the web, a web -- a set of connected pages. This fundamental feature has made the web a very powerful platform and it is obvious that the world of apps needs this feature. All modern platforms support a way for apps to register a URI (custom protocol) and also have universal links (handling web links in an app).

This was a great article that covers all the different types of hyperlinking available to apps and sites. I've been doing a lot of research into this space ever since Web Intents and the state of advanced linking on the web leaves a lot to be desired, in my opinion.

One of the reasons why I love the web is that behind a link is direct access to the resource, I don't know any other platform that can combine the link and the actual resource in the same way, but it could be soooo much more. The standard link provides essentially a VIEW intent that contains state (the URL) and context (text between the anchors), and you can hack about with it custom protocols but we need to go a lot further.

  * We need to expand the vocabulary to `registerProtocolHandler` to all more access to more native schemes.
  * Anything registered with the protocol handler needs to be system-wide.
  * We need to be able to have websites to be able to handle opening a range of content types and have pages available to be registered as a system file handler.
  * We need to have higher order actions available to developers, VIEW is great, we need an agreed upon set of core actions such as PICK, SAVE, EDIT so that we can more effectively understand a site's or app's capabilities, and the ability to extend them with higher-order semantics. Android has this, Siri is getting it, both using 'Intents,' the Web should have it too.

This is one of the reasons why I'm so excited about messaging abstractions such as [Comlink](https://github.com/GoogleChromeLabs/comlink) that remove the burden of the postMessage madness and let you think about exposing a function to other apps, and then once you expose function you need to more easily enable the discovery of that function… and that's what links enable.

[What's the best way to boost the efficiency of your product team](https://dzone.com/go?i=299454&u=https%3A%2F%2Fsentry.io%2F_%2Flp%2Ftelephone-game-ebook%2F%3Futm_source%3Dadvertisement%26utm_medium%3Dtext%26utm_content%3Ddzonewebdevzone%26utm_campaign%3Dsponsorship) and ship with confidence? Check out this [ebook](https://dzone.com/go?i=299454&u=https%3A%2F%2Fsentry.io%2F_%2Flp%2Ftelephone-game-ebook%2F%3Futm_source%3Dadvertisement%26utm_medium%3Dtext%26utm_content%3Ddzonewebdevzone%26utm_campaign%3Dsponsorship) to learn how Sentry's real-time error monitoring helps developers stay in their workflow to fix bugs before the user even knows there's a problem.
