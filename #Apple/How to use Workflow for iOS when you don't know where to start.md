# How to use Workflow for iOS when you don't know where to start

_Captured: 2016-03-10 at 00:44 from [m.imore.com](http://m.imore.com/how-use-workflow-ios-when-you-dont-know-where-start)_

Workflow is the most powerful app on my iPhone and iPad. I wouldn't be able to work without it, and, almost two years after its release, I'm still discovering its infinite potential.

Whether it's sending a message to a group of people or organizing documents, you've likely come across a task on your iPhone or iPad that you'd like to speed up. Our iOS devices have evolved into powerful modern computers, but there are still some areas where we can be slowed down by app limitations, or, more simply, by the tedious process of performing the same task over and over.

![](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/2016-02-29-033411.jpeg)

Thankfully, we have a solution to this: automation. And when it comes to automating tasks on iOS, [Workflow](https://workflow.is/) is the undisputed king. Learning to master Workflow is the first step to living an efficient, productive life on iOS, and it's how I've been working on my iPad for years now.

## What Workflow does

Workflow is an automation app for iOS that lets you create **workflows**. It's quite a mouthful, but bear with me. You don't need to be familiar with [OS X automation apps](https://en.m.wikipedia.org/wiki/Automator_\(software\)) to understand Workflow: In the app, a workflow is made of a series of **actions**, executed in a single flow (thus the name) from top to bottom.

Tap the **Play** button at the top, and Actions will execute, one after the other; once it's done, the **output** of a workflow (its result) will be displayed at the bottom of the chain of actions or communicated visually to you.

![A workflow.](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/2016-02-29-033645.jpeg)

Think of actions inside a workflow as dominoes: After an action is completed, the workflow automatically jumps to the next one until it reaches the end. The power of this process lies in the ability to arrange actions any way you want -- building workflows that solve either basic or complex problems for you.

How Workflow enables you to start building workflows is the app's strongest aspect: It deeply integrates with iOS, bringing you actions based on system features native to the iPhone and iPad. For instance, there are "interface" actions to display native alerts and menus that look like standard iOS interface elements; text actions to manipulate plain text; actions that work with Photos to fetch the latest pictures from your library; and there are even actions to access data from the Health app and control playback in Music. In total, Workflow offers 13 categories and hundreds of actions by default that allow you to automate all sorts of daily tasks.

## How to make your first workflow

With Workflow, your imagination is, in many ways, the only limit. And that can also be a problem at first. Facing the potential of Workflow and the breadth of its actions can be a little daunting; fortunately, the app makes it easy to get started and experiment.

The first thing you'll want to understand is which kind of task you want to automate on your iOS device, and why. My suggestion, if you're new to automation: Find common tasks that would _truly_ benefit from requiring fewer seconds each day. They don't even have to be extremely complex; something simple will do. When automating, it's better to save a second on a trivial task that you repeat 10 times a day than to save 30 seconds on an impressive workflow you only need once a month.

Once you've found a task that should be automated, open Workflow, create a new (empty) workflow, and take a look at the sidebar on the left (or swipe right to open a tab on the left, if you're using Workflow on the iPhone).

![Creating a new workflow.](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/2016-02-29-033547.jpeg)

Here, Workflow neatly organizes actions by category and system integrations (documents, Health, Photos, etc); you can also view suggested actions or search. Don't be afraid to poke around, read action descriptions, and mark actions that catch your attention as favorites. Curiosity is the first step to good automation.

With an initial idea in mind, start dragging actions from the sidebar into the canvas on the right. Remember: Workflows are always executed from top to bottom, and each action passes its **output** (the result of what it did) to the next action as **input**.

When I was new to Workflow, visualizing the vertical flow of actions before building the stack was my biggest hurdle in getting started. I've since developed a habit that comes in handy every day: if I already know what a workflow should do at the beginning and at the end, I place the first action and the last one immediately on the canvas. Then, I only have to figure out how to go from Point A to Point B, dropping actions between those two as I play around with different ideas.

As you experiment with actions, you'll notice that they share some similarities. Some actions, like 'Text' and 'Show Alert', have text fields where you can type text that will be passed to an action or displayed on screen. Others _do stuff_ without requiring user interaction: 'Open URL' launches a URL in Safari, while 'Copy to Clipboard' copies whatever is passed to it to the system clipboard. There are actions with toggles for options ('Replace Text' can be case sensitive or not), actions with segmented controls ('Date' can pass the current date or a specific date to the next action), and actions that have buttons to pick additional settings from a list, such as choosing a team in the 'Post to Slack' action.

Once again: don't be afraid to try actions and see what happens. While you're creating a workflow, use the 'Show Alert' and 'Quick Look' actions to debug what is going on - they're good ways to preview that the correct text or image is being passed to the next action without having to wait until the end for the final output.

More importantly, keep in mind that there's no "right" or "wrong" way to create a workflow. The app gives you the building blocks and some basic guidelines, but, in most cases, the same result can be obtained in a dozen different ways. Workflow has been engineered to accept disparate combinations of actions (thanks to a powerful underlying engine called the Content Graph), and you should take advantage of its flexibility to test the craziest ideas you have.

## Why variables are your best friend

Variables are one of the key concepts behind Workflow. Understanding how they work will help you build more complex workflows and, in general, save a lot of time during the creation process.

Variables let you save values you want to re-use at a later point in a workflow. A variable can be anything: a bit of text, an image, a date, a location, or even a combination of multiple data types such as a string of text _and_ an image -- all inside the same variable. Think of variables as dynamic tokens: You can insert or pass them to actions with one tap, and they carry information that was generated at other points in the workflow.

For example, if you have a workflow that gets the current date at the beginning but only needs to use that date at the end, you can save the date to a variable at the top, and fetch it again later.

![Saving a date variable.](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/2016-02-29-033052.jpeg)

To work with variables, you'll use the 'Set Variable' and 'Get Variable' actions. Each variable has a name (assigned by you), and it can be used as many times as you want. The best aspect of variables is that, unlike actions, they can do more than simply being treated as an input and output - they can be embedded _into_ actions. Take the 'Choose from Menu' action, for example:

![Choose from menu](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/2016-02-29-033136.jpeg)

This action brings up a menu to pick from multiple options. There are several different fields you can modify in the action, including the title of the menu and the available options. But if you want the Prompt field to get data dynamically generated from previous actions, you can tap the 'Variable' button and pick one to be used inside the field.

![Showing a prompt with a date variable as title.](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/2016-02-29-033210.jpeg)

In Workflow, you should use variables whenever possible, as they will help save considerable time when creating new workflows. Keep in mind, though, that variables aren't global to the entire app (each variable exists within the workflow where it lives); if you need something more global, the system clipboard is always available as a "special" variable in the app with a dedicated Clipboard token in actions that allow it.

## How to use workflows outside of the app

There are several ways Workflows can be integrated with iOS at a deeper level.

If you have a workflow that you'd prefer to run from outside of the app, you can launch it as an action extension from the iOS share sheet. From a workflow's Settings, set the type as action extension, choose which kind of data the workflow will accept from other apps -- should it be available when you're sharing text? Or images? -- and you're set.

![Setting up a workflow as an action extension.](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/2016-02-29-033737.jpeg)

The next time you're in an app and would like to use data from that app in your workflow, run the Workflow extension, pick the workflow, and it'll execute right inside the host app. For example, there's a workflow that turns links into PDF versions of their webpages, which you can run in Tweetbot or Google Chrome, for instance. The action extension is, by far, my favorite aspect of Workflow and it has reinvented how I work on my iPad Pro.

There's also the ability to pin workflows as widgets and use them in the Today view of Notification Center. When running as widgets, your workflows will have some limited functionalities - you can't, for example, display PDFs or launch the keyboard in the widget - but everything else - interactive menus, images, web requests - will work perfectly with a slimmed down interface.

![A workflow as a widget.](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/2016-02-29-032932.jpeg)

The widget is a fantastic way to quickly access workflows that you run several times a day. I have one that shows me a quick list of contacts I want to message with pre-built canned responses (such as texting my girlfriend that I've arrived at home), and I couldn't live without them now.

Lastly, iCloud Drive. While Workflow isn't a file manager, it does have file management features to help you work with documents so that you can get details of files, open them, and share them with other apps and services. Workflow has long supported reading and writing to Dropbox, but in the last year the app has also [received support for iCloud Drive](https://www.macstories.net/ios/publishing-articles-to-wordpress-with-workflow-on-ios/) to save and open files to and from iCloud.

If used with the 'Get File' action and the 'Show Document Picker' toggle turned off, you'll be able to retrieve a specific file from the /Workflow/ folder in iCloud Drive by file name. This effectively enables you to store assets and documents in iCloud Drive, which you can then combine with other actions to automate files within Workflow.

## A place for experiments

[Workflow](https://workflow.is/) is the Minecraft of iOS productivity: By deeply integrating with native iOS features and apps, Workflow's hundreds of actions are the building blocks that will help you save time when performing any kind of repetitive task. For both novices and more advanced users, Workflow is a beacon for iOS automation, and there's nothing else like it on the App Store.

It's the most powerful app on my iPhone and iPad -- I wouldn't be able to work without it, and, almost two years after its release, I'm still discovering its infinite potential. And, with luck, this article can help you along your Workflow journey, too.
