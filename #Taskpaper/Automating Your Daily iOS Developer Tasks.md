# Automating Your Daily iOS Developer Tasks

_Captured: 2015-12-11 at 02:05 from [realm.io](https://realm.io/news/felix-krause-fastlane-automating-ios-tasks/)_

![](https://embed-ssl.wistia.com/deliveries/c2b8f11999f9dad71c22cbfe9e3f1868bdb1055f.jpg?image_crop_resized=640x360)

![](https://embed-ssl.wistia.com/deliveries/1fa8ee5837bfd2ccc7facf97183b6f95676d79f3.jpg?image_crop_resized=640x360)

### Introduction [(0:00)](javascript:presentz.changeChapter\(0,0,true\);)

fastlane is a set of open source command line tools that help you automate every aspect of your testing, building and release process. It consists of nine individual tools that help you do things like generate screenshots, deal with code signing and, in general, maintain your provisioning profiles. fastlane itself is a tool that connect all these tools, plus some third party ones, into a single workflow. This allows for automation of every step of the process. In this post, I will focus on three common issues you've probably experienced in the past and how you can solve them.

I will demonstrate how to capture beautiful, localized screenshots, how to handle code signing, provisioning profiles, certificates, all these kind of things, and finally, how you can automate your whole process using fastlane.

### Screenshots [(1:31)](javascript:presentz.changeChapter\(0,4,true\);)

Every time you deploy your application to the App Store, you have to generate new screenshots and upload them to iTunes Connect. You also have to generate screenshots every time you change the design of your application, every time Apple announces a new device, and every time you add a new language. It's really hard to do screenshots right. if you support 10 languages with six different device types, including the iPad Pro, and each has five screenshots, you end up with 300 screenshots you have to generate and upload to iTunes Connect.

Fortunately, fastlane offers a tool called "snapshot." snapshot uses UI testing, which was introduced at this year's WWDC. UI testing is an amazing technology to interact with your application in a very natural way. It was designed to run UI tests, but you can also use it to generate screenshots with the help of snapshot.

This works by the provision of a UI test automation file, written in Objective-C or Swift, which tells snapshot how to navigate in your app and where to take the screenshots.

If you've already set up snapshot for your project, all you have to do is run snapshot in your command line. snapshot will automatically detect your project settings so you don't have to think about it. The great thing is that snapshot runs in the background, so you can do something else while the computer generates the screenshots for you. You'll be able to see the simulator doing all its magic: rotating, tapping, etc.

Once everything is done, snapshot will generate an HTML report containing all the screenshots it generated. This is an incredible way to get a quick overview of how your app looks on different devices and different languages. You can then upload all the screenshots to iTiunes Connect using "deliver," another fastlane tool.

### Provisioning Profiles [(3:58)](javascript:presentz.changeChapter\(0,8,true\);)

We want to focus on how you can properly code sign and build your application using the command line. This is important because we want to be able to build and sign our application using SSH with a remote desktop connection, or in a CI service like Jenkins or Travis.

In order to properly code sign, you first need a certificate, and we can use a tool called "cert" for that. cert will make sure we have a valid code signing identity installed on our local machine.

"sigh" is for provisioning profiles. sigh will use the information from cert to generate download a valid provisioning profile from the Apple Developer portal so you can sign your application.

Next, we need to build the application, for which there a tool called "gym.". It builds the application, packages it up to an IPA file, and properly code signs your application. You end up with an IPA file which you can upload to iTunes Connect or any third party testing service.

In the terminal, we basically enter three commands, one for each tool. Each command has a lot of options, but the defaults are generally pretty good. If you take a look, these three commands still seem like a lot of work. How can we automate this?

### Automation and Beta Deployment [(5:28)](javascript:presentz.changeChapter\(0,12,true\);)

We can start automating our beta deployment using fastlane. Consider the following situation: your boss or project manager asks you to install the latest version of a beta on a phone in order to show it to clients. Normally, you would have to: increment the version number or the build number, commit that, push it back to Git, make sure you have a valid provisioning profile to properly build and sign your application, export it using Xcode to generate an IPA file, upload to some kind of beta testing service or iTunes Connect, add some release notes, and finally send the version to your boss.

Really, this is a waste of time. We want to spend our time building cool things, so what if you could automate all these and reduce this chain of tasks into a push of a button?

fastlane uses a so called "Fastfile" which contains all information to build and deploy your application. You define which steps to run and in what order, and fastlane will make sure to execute them. If one of the steps fail, fastlane will stop executing the whole lane and it will fail.

### Automation Example [(6:43)](javascript:presentz.changeChapter\(0,15,true\);)

In order to automate our previous example (getting a beta to your boss), we first have to define a lane. You can define as many lanes as you want, but I will focus on the beta lane, which contains three actions: we first increment the version number for Xcode project, we commit the version bump, and finally push it back to our git remote like GitHub. Easy enough!

We're on cert to have a valid code signing identity, sigh to get a provisioning profile, and gym to build and sign our application. Finally, we want to distribute our binary, so we will upload it to a beta testing service like Crashlytics, and finally post the message on Slack, so that all team members know the new build is ready.

A great thing about fastlane is that it comes with so many built-in integrations, including Slack, email, and interactions with Git. If an integration is not available yet, you can easily extends fastlane to fit your needs, or use the existing tools.

fastlane also takes care of passing on information from one build step to the next, so we end up with a very clean and minimalistic configuration file. For example, the Crashlytics action knows where the IPA file is located, and gym knows what provisioning file to use.

After you've finished writing the configuration file, you can run it by running fastlane beta.

### Deployment [(8:28)](javascript:presentz.changeChapter\(0,19,true\);)

For a real world example, could deploy an app to the App Store using fastlane. There is another lane called "fastlane iOS release" that will first build and sign our application using gym. It will execute, then print out a nice table summary of the available parameters. It will also use a tool called Pilot to upload the build to iTunes Connect. Under the hood, this uses the iTunes Transporter, provided by Apple and built in into Xcode.

In general, every time fastlane runs a command, it will print out the command so you can see what's going on and easily debug issues if you have any problems. Additionally, it will show you a summary of the parameter it used. This is extremely useful if you use a CI system like Jenkins: roll back a few weeks, and you can see what the values of certain parameters were.

### Tool Overview [(9:34)](javascript:presentz.changeChapter\(0,22,true\);)

I just want to provide a quick overview of what tools are available within fastlane.

First, we briefly talked about **deliver**. It basically allows you to upload app metadata, screenshots and binaries to iTunes Connect. It even allows you to submit apps for review.

**snapshot** generates localized screenshots, and **frameit** works nicely together with snapshot. It allows you to add device frames around your screenshots, so you end up with nice captures with text on top.

**pem** allows you to automate the creation of push notification certificates.

**sigh** does provisioning profiles, **cert** does code signing identities, and **produce** is for creating new app IDs on iTunes Connect and to the Apple Developer portal using the command line.

**gym** builds the application, and **scan** is a new tool that allows you to easily run tests on your app.

#### Spaceship [(10:27)](javascript:presentz.changeChapter\(0,23,true\);)

Spaceship is a tool that is usually not consumer facing. Instead, it is used under the hood to communicate with Apple's web services. Most of the other tools communicate with Apple in some way. This is all abstracted out into its own tool and into its own Ruby gem, so people can reuse it for their own tools.

Spaceship itself is a plain HTTP client using the APIs directly. There are three different API points: iTunes Connect, Apple Developer portal and the Xcode API. Spaceship consolidates all of them into one unified API.

#### Boarding [(11:04)](javascript:presentz.changeChapter\(0,24,true\);)

There's another one tool called Boarding, and it allows you to easily set up a landing page for your potential TestFlight users. You basically host this on Heroku, and people who want to beta test the application can just enter their email address.

#### WatchBuild [(11:19)](javascript:presentz.changeChapter\(0,26,true\);)

Recently, the processing time of iTunes Connect has changed from being something closer to 10 minutes to now being possibly 10 hours. Instead of waiting for it yourself, there is now a tool called WatchBuild which will do the waiting for you and notify you once the build is ready.

### Live Demo [(11:35)](javascript:presentz.changeChapter\(0,27,true\);)

While giving this talk at SLUG, I was able to do a live demo of fastlane. I prepared an empty Apple account with no certificates and no provisioning profiles, I prepared an empty Xcode project with no fastlane setup. I showed how easy it was to set up fastlane to sign and build my example application and upload it to Crashlytics.

Check out that demo [above](javascript:presentz.changeChapter\(0,27,true\);).

### What's Next? [23:00](javascript:presentz.changeChapter\(0,28,true\);)

This was all a short introduction of what you can do with fastlane, and how it can help save you time during development and deployment. fastlane supports all kinds of setups no matter what tools you're already using or how complex your setup is. Please check out [fastlane.tools](http://fastlane.tools) to access links to all the repos and guides on how to get started.

### Q&A [(23:32)](javascript:presentz.changeChapter\(0,29,true\);)

_**Q: For screenshots, it would be really cool if I could drop a PSD template somewhere and then have it use the screenshots generated with snapshot to pre-populate those PSD templates, and then export JPEGs. Is that possible?**_

Felix: It doesn't support real live screenshots. However, frameit does already provide this nice design.

_**Q: Where do you tell fastlane which password to use when it tried to connect to iTunes?**_

Felix: This was not part of the demo, but on the first run of fastlane, it will ask you for the password and it will be stored in the local keychain. It never leaves your computer, and it's not stored in any configuration file.

_**Q: Along those lines, there's a lot of valuable information scrolling by when you were using those commands. Are they saved somewhere convenient so they're easy to get to?**_

Felix: Some of them are. In general, there is a command where you can easily log it out and also print it. For example, gym actually stores all the things in logs by default. We have the raw files there in addition to the prettified output. As you see during building, this is a prettified using xcpretty, but you also have access to the raw output.

_**Q: Do you have support for sharing certificates with other developers? The private key is stored in the keychain when you generate it, so how would you share it?**_

Felix: Well, according to Apple, every developer should have their own account, right? I'm not of that opinion, though, and I'm working on something really cool!
