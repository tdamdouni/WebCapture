# Should a Progressive Web App Use a Framework?

_Captured: 2017-02-23 at 09:48 from [dzone.com](https://dzone.com/articles/should-a-progressive-web-app-use-a-framework?oid=twitter&utm_content=buffer71631&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

As I mentioned in a previous [post](https://www.danylkoweb.com/Blog/building-progressive-web-applications-pwa-with-visual-studio-IR), Progressive Web Applications (PWA) are a new way to build responsive mobile websites allowing users to use their browser instead of native apps.

When you go this route, you get limited functionality as opposed to the full native experience.

However, browsers are adding more native features through JavaScript APIs. They're slowly catching up. Slowly.

Until then, we continue to work with the current list of features in JavaScript to enhance the user's experience. But couldn't we just use a library or framework to structure our PWA instead of writing plain JavaScript?

## Javascript Libraries and Frameworks

Do we need a JavaScript framework or library to build a Progressive Web Application?

Taken from [Google's Progressive Web App page](https://developers.google.com/web/updates/2015/12/getting-started-pwa), here are some of the characteristics of a Progressive Web App:

  * **Progressive.** Works for every user regardless of their browser.
  * **Responsive. **The app works on any form factor whether it's desktop, mobile, or tablet.
  * **Connectivity-independent. **Allows the user to use the web app even if it's offline.
  * **Native look and feel.** Acts and feels like a native application, but is strictly web-based.
  * **Fresh. **Always up-to-date with a service worker update process.
  * **Safe.** Always served up to the client through HTTPS.
  * **Discoverable.** Even though it's an "application," it can be indexed into a search engine.
  * **Re-engageable.** Allows re-engagement through features like push notifications.
  * **Zero-deploy hassle. **Allows users to add the web app to their home screen without having issues with app stores.
  * **Link-friendly.** Allows you to reshare using a URL.

After looking over this list two or three times, I didn't see speed anywhere on this list to be considered a factor.

I guess it could be covered under the responsive characteristic, but from every Progressive Web App I've seen, a framework or library wasn't used when building a PWA.

Does this seem unusual?

No Angular, Backbone, Meteor, or React. Heck, not even jQuery.

Why not? I've got a theory.

One word: Size.

Most JavaScript libraries are too large to load and it keeps the user waiting while everything initializes.

If you look at the Weather PWA from Google (which is also a [project I converted into a Project Template](https://www.danylkoweb.com/Blog/building-progressive-web-applications-pwa-with-visual-studio-IR)), you'll notice there isn't any framework attached to it.

It's just JavaScript.

Minimal. Hand-written. JavaScript.

## One Shell to Rule Them All

Another challenge with a PWA is writing the smallest amount of JavaScript possible.

Again, if you notice the weather PWA, it only has one screen. Most full-featured native applications have at least two or more screens to be considered helpful and worthy of a download and a place on your smartphone's "desktop."

One of the recommendations from Google is to use a shell-based approach where the shell controls what components are loaded when, where, and how.

This is where service workers come into play. Your JavaScript triggers certain events to load data and proceed to hide and show certain areas of the application.

The service workers provide more control and flexibility when managing your API calls from JavaScript.

The hard part is moving from screen to screen.

One question always asked is how do you maintain state in your PWA?

This is why the shell-based approach is best when writing a PWA and managing state from screen to screen.

## Why and Why Not?

Based on these arguments, here are some valid points as to why you should and should not use a library or framework.

### **Advantages of Using a Framework**

  * **Existing shell.** Some frameworks already provide you with an application shell giving you a more structured application right out of the box.
  * **Modular.** A majority of frameworks provide modular loading when needed.
  * **Small JavaScript routines.** While frameworks provide more structured development, small, compact JavaScript routines win in the end making it faster to load the application and cutting down on the user's wait time.
  * **State.** The shell mentality gives users a way to maintain state across the pages.

### **Disadvantages of Using a Framework**

  * **Load time.** When adding a JavaScript library, this increases the amount of time it takes before the screen appears for the user.

Since Google considers the [load time as one of its critical factors](http://searchengineland.com/google-says-page-speed-ranking-factor-use-mobile-page-speed-mobile-sites-upcoming-months-250874) for ranking websites, I'm having a hard time justifying using a framework or library to build a PWA, but it would make things tremendously easier.

As I scrolled through the Getting Started with Progressive Web Apps on Google's site, I did notice a number of developers already created [Progressive Web Applications with and without frameworks](https://developers.google.com/web/updates/2015/12/getting-started-pwa#progressive_web_apps_with_and_without_frameworks). Does this mean I'll use a framework? Maybe.

Of course, I'll run some tests to confirm if my app is small and fast enough to load for users. If I do use a framework, I will probably use [Aurelia with Visual Studio](https://www.danylkoweb.com/Blog/using-aurelia-with-visual-studio-IK) and see if I can perform bundling and shrinking using the Task Runner.

## Conclusion

Today, I gave some valid points whether developers should use a framework or library to build Progressive Web Applications.

This post was primarily meant to be more of a discussion than general statements since I only see one disadvantage to using a JavaScript framework with a PWA, but boy, I wouldn't want to take that chance of ignoring that one disadvantage.

It could mean the difference between position 2 and position 23 on Google's search results. (Hint: You want to be on page 1 instead of page 3.)

If you do decide to use a framework or library, post a comment below to let the community know that you're building a PWA using a framework. We all want to hear about it.

On my end, I will keep everybody up-to-date as to what I experience with writing a PWA with Aurelia.
