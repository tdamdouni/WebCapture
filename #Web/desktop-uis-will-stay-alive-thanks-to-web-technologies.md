# Desktop UIs Will Stay Alive Thanks to Web Technologies

_Captured: 2018-01-28 at 22:19 from [dzone.com](https://dzone.com/articles/desktop-uis-will-stay-alive-thanks-to-web-technolo?edition=358100&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-28)_

[Build vs Buy a Data Quality Solution: Which is Best for You?](https://dzone.com/go?i=251321&u=http%3A%2F%2Fwww.melissa.com%2Fresources%2Fwhitepapers%2Fbuild-vs-buy-challenge.html) Gain insights on a hybrid approach. Download white paper now!

To understand what's wrong with Java desktop apps, let's take a look at the new features of JavaFX, a leading UI framework for desktop applications. It becomes obvious that it is trending towards the web approaches, borrowing more and more features from the web world. JavaFX supports a subset of CSS features, accompanying it with their own properties.

However, this all is far away from what the web offers for UI. Another essential aspect is tooling. Have you seen anything in any way similar to developer tools coming along with all the popular web browsers for desktop UI design? Finally, as [JNLP goes deprecated in Java 9](http://www.oracle.com/technetwork/java/javase/9-deprecated-features-3745636.html), it certainly doesn't add points to desktops.

But then, why does desktop stay afloat? There are a few very important things that are poorly covered by a web approach:

  * Offline mode
  * Advanced integration with peripheral devices
  * Local data/file processing

Partially, these problems are being solved using new web standards, such as Service Worker, but it would be great if we could implement a technology that brings web UI development technologies and tooling to our desktop Java applications. What if I told you there was an app on the market that did just that?

## What Is Electron?

And that's where Electron comes in. It was formerly known as Atom Shell, a technology behind GitHub's Atom editor. Atom was the first widely known desktop application built with HTML, JavaScript, CSS, and Node.js integration.

Electron is an open-source framework that allows using web technologies for the development of desktop GUI applications. You can use front- and back-end components originally developed for web applications: JS for the backend and HTML/CSS/JS for the frontend.

In a nutshell, Electron consists of two main components: the Node.js backend plus a Chromium web browser in a single executable, as well as additional desktop integrations: native menus, notifications, tray icons, installers, etc.

## Why Do We Need This Approach?

First of all, we can solve a lot of problems of the current Java desktop UI world:

  * Java desktop technologies do not evolve
  * There is a way smaller set of available UI libraries for Java than for the web
  * It is hard to implement responsive, rich UIs with JavaFX

In addition to this, the Electron ecosystem has a lot of useful tools:

  * Installers for all major operating systems
  * Smooth automatic update subsystem
  * Crash reporting

Finally, it is an open source technology, and it is the bleeding edge of the modern UI.

There is only one small problem… Electron is all about JS.

There are two ways to make it suitable for Java applications:

  * Build your application using GWT client-side and compile it to JS
  * Write code in a server-side Java framework and bundle a servlet container inside of an application

If we want to provide advanced hardware integration and local file system access from Java code, then approach #1 is not the way to go.

The second approach can be implemented using an embedded servlet container, such as Jetty, and an automatic procedure of start/stop for the Java process. Thus, we will have a full-featured Java process on the client PC and will be able to use both Java and Electron features. Well, as it turns out, it can be done easily!

I will show you the full step-by-step process of crafting your own UI toolkit for desktop applications in the tutorial available [via GitHub](https://github.com/cuba-labs/java-electron-tutorial/blob/master/README.md). Check it out to see how to leverage the power of web technologies in your desktop apps:

# ![](https://vaadin.com/documents/472491/0/image1.png/5f17cbbb-9b06-42a0-8454-6b5c48c9147d?t=1514986952000)

## Benefits of the Hybrid Approach

What good is the hybrid approach of wrapping a web app inside a native app?

  1. We have full access to the desktop machine: hardware, file system, installation, notifications, and integration with the operating system.
  2. We can use JS/CSS to develop UI widgets while at the same time employing Java for business logic.
  3. We can reuse existing JS/CSS libraries and approaches.
  4. We can even bundle our existing Vaadin application for desktop usage!

## How Do We Use It for Real-Life Applications?

CUBA Studio is a powerful enterprise application development tool for applications based on [CUBA Platform](https://www.cuba-platform.com/). With Studio, applications are up and running within minutes.

We have used Vaadin for CUBA Studio for 4 years, and through all of that time, it has been a web application that runs locally, but shows the UI inside of a web browser.

This year, we introduced the new version of CUBA Studio that uses Electron to bring better UX for our users. It enables developers to use CUBA Studio as an independent desktop application without a web browser. We can use all the advantages of an operating system, such as the taskbar, fast switching between applications with shortcuts, and shutdown of the application on window close.

And what makes me so happy is that we bundled our existing Java code without any changes! Well, almost without changes. Of course, we improved a couple of things.

![](https://vaadin.com/documents/472491/0/image-2.png/b0a97d0d-1183-41ed-b0d5-4bab724e9060?t=1514987289000)

> _With this approach we have:_

  * Desktop integration: taskbar, window switching, shutdown on close
  * All the features of Chromium for UI, including CSS animations, Canvas, and even WebGL
  * A controlled version of the browser, thus the application will not be broken in the event of a Chrome update. And more importantly, the same version of the UI engine we tested before release.

In the next version, we are planning to introduce new features:

  * Multi-window support
  * Desktop notifications on build/deploy events
  * Smooth automatic update

These features are available since we are no longer limited by the web browser.

## Conclusion

To sum up, Electron became a very strong player in the market of modern desktop application frameworks. It is an interesting approach that could help Java applications to look and perform better on desktop, employing the latest features of web technologies for UI.

You can find a more complex application with all the tricks described in this post on GitHub: <https://github.com/jreznot/electron-java-app>

If you want to try the application based on this approach, I recommend that you take a look at [CUBA Studio SE](https://www.cuba-platform.com/discuss/t/platform-cuba-studio-se-a-desktop-application-based-on-electron/2914/).

[Build vs Buy a Data Quality Solution: Which is Best for You?](https://dzone.com/go?i=251322&u=http%3A%2F%2Fwww.melissa.com%2Fresources%2Fwhitepapers%2Fbuild-vs-buy-challenge.html) Maintaining high quality data is essential for operational efficiency, meaningful analytics and good long-term customer relationships. But, when dealing with multiple sources of data, data quality becomes complex, so you need to know when you should build a custom data quality tools effort over canned solutions. [Download our whitepaper](https://dzone.com/go?i=251322&u=http%3A%2F%2Fwww.melissa.com%2Fresources%2Fwhitepapers%2Fbuild-vs-buy-challenge.html) for more insights into a hybrid approach.
