# Using Electron for Cross-Platform Desktop Application Development

_Captured: 2018-01-05 at 18:15 from [dzone.com](https://dzone.com/articles/developing-progressive-web-apps-in-ionic-framework?edition=347165&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-04)_

When computers first became popular and started functioning with ease at workplaces and homes, it was desktop applications that caught the eye. However, with the advent of the internet and the online commerce boom, things changed drastically and web applications came into prominence. A bleak future for software applications was predicted, and while the popularity of desktop applications was pushed aside, they never completely died out. There were some fundamental differences between the two that made it evident that you cannot just throw desktop software application development into the bin.

#### Desktop-Based Applications

A desktop based application is software that's installed on a single computer that will perform specific functions and tasks for which it was designed. However, the same device can accommodate multiple users with the help of networking. Examples would be media players, word processors, etc.

#### Web-Based Applications

As the name suggests, web-based applications are those apps that function with the help of the internet. They can run on multiple devices irrespective of the local network, especially if the coding is done so. These are called cross-platform web apps. These apps are usually built on the client server, and use a web browser as the client interface. The concept of coding once and having it run on multiple devices helps developers work out new applications quickly for clients.

This is where the difference between the two lies. You cannot develop a desktop application that works for multiple OSs with a small budget.

Modern languages like JavaScript and Python proved to be useful because they let you create apps for all three major operating systems. However, that was also not easy because the major challenge web developers had to face was to learn the languages and their APIs separately for developing the apps.

This was about when developers started thinking about developing a desktop application that functions equally well on multiple OSs, and cross-platform web development started gaining importance. But to do that, they need something that would help them build apps that function on multiple desktops.

It's at this juncture that [Electron](https://electron.atom.io/) came into existence, and then prominence. Electron allows developers to make the best use of their skill set and build highly functional desktop apps. Electron is the framework that is used to create the open-source source code editor Visual Studio Code and the cloud-based team collaboration tool and services app Slack.

## Why Desktop Applications?

It is not possible to replace desktop applications because they are really needed when you want your apps to fulfill certain criteria. Let's look at some of them:

**1\. Data Security:** Unlike web apps, all the data is stored within the user's computer system, so there is no worry about it being hacked. The user has total control over standalone applications and therefore it allows protection from various vulnerabilities. Web applications are open to a huge community of users connected through the internet, and this widens the threat.

**2\. Available Controls:** When compared to browser-based projects, desktop applications come with a number of interactive controls. These interactive controls include Visual Studio for Windows as well as 3rd party controls for desktop application developers. The controls also let you access the underlying hardware and OS components. Additionally, there are also keyboard controls that come with an additional layer of interactive capabilities, including the use of arrow keys in the keyboard.

**3\. Flexibility:** To write desktop apps, developers can use the user's computer hardware like serial ports, camera, network ports, scanners, and Wi-Fi.

**4\. Performance:** Desktop apps are considerably faster and more responsive when compared to web apps. This is because web apps inherently carry overhead that you see with a general purpose web server. On the other hand, a desktop app, if designed correctly will load only what's needed. So they take up less memory and fewer resources, thereby improving the performance and increasing the app's efficiency.

Developing a cross-platform app makes sense because it saves time. All developers need to do is code once, and the app will run on all the major platforms. This is also what makes Electron unique. It allows people to develop applications a little differently when compared to traditional programming languages. This is also the reason why applications using Electron make use of the three main components/languages usually used for scripting web pages, which are HTML, JS, and CSS. This allows for increased productivity, lesser TTM (time to market) and a high-quality app that functions remarkably well on iOS, Android, Linux, and Windows devices.

Cross-platform frameworks have received major hype over the years because they hold some really notable advantages over native frameworks. Some of them are:

**Reusable code** \- Maintaining and deploying codes makes cross-platform [ application development](https://www.cabotsolutions.com/services/mobile-application-development/) an easy task because it totally avoids repetitive tasks. There is no need to write a fresh piece of code for each action while developing apps for all the major platforms.

**Faster time to market** \- Leveraging the unified codebase makes it easier for businesses to create apps faster, and ship it on time. Deadlines are met with precision.

**Easy deployment** \- Cross-platform frameworks come with a host of modules and extensions that make it easier to deploy and maintain codes to make the apps run on all major platforms. Each time you make an update to the app, it would be easily refreshed in all the apps working on various devices and platforms.

**Uniform user experience** \- Developers take great precautions to render impeccable User Experience (UX). This is done through a single code base, and even the overall look, feel and consistency of the app on multiple platforms.

**Cost-effectiveness** \- By leveraging a single codebase, developers can build cross-platform desktop applications, thereby making it easier for companies to handle projects within a budget.

Out of the many cross-platform frameworks, Electron is one of the best because it can build a desktop app with web technologies like CSS, HTML, and JavaScript.

## What Exactly Is Electron and How Does It Work?

Electron was known as Atom when Cheng Zhao created it on 15th July 2013. It is now developed by GitHub and meant to be an open source framework written in C++, JavaScript, Objective C, and Python. The framework was initially intended for use by Atom, a full-featured cross-platform text editor; that's how the name "Electron" came into being. It can make cross-platform development very easy.

The framework uses front-end and back-end components developed for web applications to develop the desktop GUI applications. For front-end requirements, Chromium is used, while Node.js is used for the backend. Electron does this by combining both Node.js and Chromium into a single runtime, and packages multi-platform apps.

### The Structure of an Electron App

The simplest of Electron apps comes with three main files. They are:

  * _package.json_ (metadata, npm file): This the most important file in an Electron app. It is embedded with information about the package like name, version, etc.

  * _main.js_: This is the code.

  * _index.html_ (GUI): It is all about graphical user interface.

#### How an Electron App Works

![Image title](https://www.cabotsolutions.com/public/Electron-Process.png)

The main file defined in the package.json file will be executed. The main.js file creates an application window or a browser window instance to run web pages. This will be powerful enough to interact with the native Graphical User Interface of the OS.

To run the Electron app, you will need to have npm installed. As npm is distributed along with Code.js, you automatically get npm installed on your computer when you download Node.js.

Electron is the main framework behind the two main open-source source code editors: Microsoft's Visual Studio Code and GitHub's Atom. The Electron executable file (electron.exe in Windows, electron.app on OS X, and electron on Linux) provides the framework. The Electron executable file can easily be edited according to developer requirements (examples would be: adding branding, custom icons, etc.).

The web page runs its own processes known as the Renderer process. The browser window instances run the web pages through its own renderer process. So when the browser window instance is destroyed, the renderer process attached to it will also be destroyed.

In order to understand the Electron process, let's take a look at a sample application.

There are two main types of Electron processes. They are:

  * **The Main Process** \- This is the entry point of the application. This is the file that will be executed once you run the app.

  * **The Renderer Process** \- This is the controller for a given window in the application. Each window has its own Renderer process.

To make sure the code is clear, each Renderer process needs a separate file. In order to define the Main Process for the app, open _src/app.js_ and include the _app_ module to start the app, and the _browser-window_ module to create the various windows of the app (both part of the Electron core):
    
    
    var app = require('app'),
    
    
    Once the app starts, it fires a ready event, that you can bind to. Instantiate the main window of the app like this:
    
    
        mainWindow.loadUrl('file://' + __dirname + '/windows/main/main.html');

At a glance:

  * Create a new window with a new instance of the `BrowserWindow` object.

  * You can define the various settings of the object and change its default settings by taking each object as a single argument.

  * You can load the contents of either a local or a remote HTML file through the `loadUrl()` method.

  * Debugging is possible through the `openDevTools()` method, where you can open an instance of Chrome Dev Tools.

For the next step, you must organize the code. An ideal way to do this would be by creating a _windows/_ folder in our _src/_ folder and creating a subfolder afterward.

The server-side logic of the application is at _main.controller.js_, while the client-side logic of the application would be at _main.view.js_.

The _main.html_ file is an HTML5 webpage, and will look like this:

The app will be ready to run now. Type this at the root of the src folder:

`$ electron`

This process can be automated by defining the start script of the package.son file.

Credits: [Toptal](https://www.toptal.com/javascript/electron-cross-platform-desktop-apps-easy)

## Why Should You Use It?

Open source developers, startups, and established companies have all started using Electron to build desktop applications. They've used the Electron framework to create the following:

  * Slack Desktop App
  * WordPress Desktop App
  * Visual Studio Code

Electron has become a popular framework for building cross-platform desktop apps because it comes with many benefits such as:

**Freedom to use cutting-edge features supported by Node.js and Chromium**: One of the biggest benefits of Electron is that it always comes with the [latest versions of Node.js](https://www.cabotsolutions.com/node-js-app-development-company/) and Chromium, giving developers the freedom to use cutting-edge platform features supported by both. Electron comes with the stable version of Chromium that is always 2 weeks behind the next release.

**Leveraging your existing skill sets**: And the other advantage is that the same skill set you have for developing web applications will be sufficient for developing desktop applications. This is a huge factor in saving money and time. If your knowledge of HTML, JavaScript, and CSS is solid, that's all you need. There is no need to invest time in learning a new programming language.

**Electron has access to operating system APIs**: Electron comes with a number of APIs that let you access several operating system features like the ones mentioned below:

  * Developers can add menus to the application window.
  * They can add context menus to the application.
  * Make use of the OS notifications system to send notifications to users.
  * Custom dock menu and user tasks.
  * Include a progress bar in the taskbar.
  * Update the recent items list.

**Direct access to Node.js APIs and npm modules**: The framework delivers direct access to the Node.js API and npm modules from web pages within the application. And the difference with web apps here is that the entire Node.js runtime is available inside the desktop application itself. Developers can easily use custom modules and the compiled Node.js native modules written in C or C++.

## Who Has Used Electron for Their App Development?

Some of the major companies in the world use Electron. Have a look at a few of the amazing apps built with the framework:

### GitHub Atom Editor:

![Image title](https://www.cabotsolutions.com/public/GitHub-Atom-Editor.png)

Written in JavaScript, and built on the Electron framework, [Atom](https://atom.io/) is a 21st-century, free, open source, and cross-platform code editor. It is heavily customizable at the application level and possesses extensible functionality through themes, packages, etc. These extensions improve Atom's core functionality.

Developers create code snippets so they no longer have to waste time on repeated chunks of code. Additionally, the editor comes with several out of the box features like cross-platform editing, a built-in package manager, smart autocompletion, file system browser, multiple panes, and find and replace for all kinds of projects. You can create an app environment just the way you want it.

### Microsoft Visual Studio Code:

![Image title](https://www.cabotsolutions.com/public/Microsoft-Visual-Studio-Code.png)

MS Code is a cross-platform source code editor developed by Microsoft. It supports debugging, embedded Git control, syntax highlighting, intelligent code completion, snippets, and code refactoring. The source code gives the flexibility to the users to customize the theme, preferences and keyboard shortcuts. [Visual Studio Code](https://code.visualstudio.com/) combines with JavaScript and Node.js to create apps that have the speed and flexibility of native apps.

### Slack:

![Image title](https://www.cabotsolutions.com/public/Slack.png)

[Slack](https://slack.com/) doesn't need much introduction. It has some of the most popular team collaboration tools and services based on the cloud. It comes with a plethora of features that are almost similar to IRC (Internet Relay Chat). Other benefits include chat rooms organized by topic (channels), private groups, and direct messaging. Slack can integrate third-party services and community built integrations into the fold.

In addition to these apps, there is a host of other applications developed with Electron framework. The full list is available at the [Awesome Electron community at GitHub](https://github.com/sindresorhus/awesome-electron/blob/master/readme.md).

## Conclusion

Special care must be taken while writing code for desktop applications because this code will have to be executed in the way it was meant to be on the client computer. And users could be using a wide range of browsers, starting from the age-old Internet Explorer to the most modern versions of Safari.

So, in short, Electron is an awesome framework that lets developers build complex desktop apps easily by removing the harder parts of coding. Developers can now focus on building a successful app rather than worrying about the time consuming aspects of coding and programming.
