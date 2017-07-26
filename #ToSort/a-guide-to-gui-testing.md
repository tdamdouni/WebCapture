# A Guide to GUI Testing

_Captured: 2017-01-16 at 19:21 from [dzone.com](https://dzone.com/articles/a-guide-to-gui-testing?edition=263883&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-16)_

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

This is a topic that keeps coming up regarding user interfaces. How do we do UI testing? Many people don't but definitely should be doing some GUI testing. I decided to write an article that could serve of a sort of guide where you will get a deeper understanding of GUI and UI testing.

## What Is UI?

In computer science, we often talk about the user interface. As its name says, it refers to the interface that a program "shows" to the user, the means by which the user will interact with a computer system. This can include the screen, the keyboard, the mouse, and the appearance of the desktop itself.

## Graphical User Interface vs. Command Line Interface

It's important to know that there are two types of interfaces: the Command Line Interface (CLI) and the Graphical User Interface (GUI). A CLI is when you type in a text command into the terminal and the computer responds to that command, while a GUI is when you interact with the computer by using a mouse or a keyboard. It's an interaction where you manipulate visual elements instead of using text.

![UI tesing - GUI](https://apiumtech.com/wp-content/uploads/2016/12/graphical-user-interface-tesing-GUI.png)

_GUI._

![UI tesing - CLI](https://apiumtech.com/wp-content/uploads/2016/12/graphical-user-interface-tesing-CLI.png)

_CLI._

The fact is that today, almost all of us need to (or choose to) interact with computers, may it be for personal or professional use. This implies that almost all of us interact with a graphical user interface. However, looking back at the 70s, that was a completely different story!

The typical user will start by checking out the design of the app, how it feels and looks, and how easy it will be to navigate through. If the interface is not appealing and that the user feels like he or she won't really be comfortable, this won't encourage him or her to continue using the software, platform, or app. GUI is extremely important and UI testing is even more important because having worked on the graphical user interface but not testing it can mean the loss of time.

UI testing should therefore definitely be implemented at the beginning of the development to reduce risks at the end of the cycle.

## What Is UI Testing? 

GUI testing is mainly about ensuring that the UI functions correctly, that an app follows its written specifications, and that defects are identified. Other than that, we check that the design elements are good. This involves checking the screens with controls like menu bars, toolbars, colors, fonts, sizes, icons, content, buttons, etc. How do they respond to user input?

To do UI testing, we usually use various test cases, sets of conditions that will help the tester determine if a system is working as it's supposed to. There are two ways of conducting it: manually (with a human software tester) or automatically (with the use of a software program).

### Manual Testing

One of the approaches to UI testing is manual testing, which implies having a human tester that will perform a set of operations and basically check manually that the app is behaving in the right way and the graphical screens are in conformance with the requirements. Although this approach has a few advantages, it has some problems such as the fact that it can be time-consuming, it requires a lot of efforts, and the quality really depends on the capabilities of the tester.

### Capture and Replay Testing

We can also do GUI testing by using some automation tools that were developed specifically for it. The idea is to run the app and capture and record the interaction that has to happen between the user and the app itself (mouse movements, etc.). We then repeat that for all the actions that users should have with the app and during the replay. The user actions that were saved will be reproduced and compared with what is expected.

### Model-Based Testing

An approach that we found to be much more efficient is model-based testing. This is mainly about building a model (a graphical description of the behavior of the system) in order to get a deeper understanding and to generate more efficient test cases. After determining the inputs and calculating the expected outputs, you run the tests. You end up comparing the results with what was expected. This approach is great because it helps a lot when determining states of the GUI that are not wanted. The level of automation is much higher.

## Some Test Cases to Consider in UI Testing

When you are testing the GUI, there are many test cases to take into consideration. These are not the only ones of course but it's a good checklist!

  * **Font type and size. **Make sure that the font is the same on all screens (or at least is in the same family). Keep it professional. Same for the font sizes (headers, body text, etc.)

  * **Colors. **Don't be inconsistent. Stay with the same colors and follow a style guide. You can't be using four different variations of orange (unless it's really part of the design). Look at hyperlinks, background, buttons, body text, etc. 

  * **Icon styles. **You shouldn't go for five different styles of icons. If you choose "flat" icons, stay with flat icons.

  * **Visual inconsistencies. **Consistency is key, always. The look and feel should be the same throughout the app, and other than the look and feel, abbreviations also have to be consistent.

  * **Dialog box consistency: **Again with consistency. If your user "exits" in some dialog boxes, you shouldn't use "leave" on others.

  * **Required fields. **It is always better to specify that a field is required by adding an asterisk and by providing the user with a sort of warning if the data is not given.

  * **Data type errors.** Always ensure that the right type of data is given (dates, ages, weight, etc.).

  * **Same document, multiple opens.** When a document is opened or downloaded more than once, instead of overwriting another one, you can rename it by adding a number to the file name.

  * **Field widths. **Obviously, if there is a certain amount of characters permitted and that the data entered shouldn't exceed a specific number, you should make this clear.

  * **Onscreen instructions.** Screens that are not clear should contain some sort of onscreen instructions that will help and guide the user. Keep it brief and straight to the point!

  * **Progress bars. **When waiting for results, progress bars are great so that users understand that they have to wait for something and that the process is still on.

  * **Confirm savings. **If you can do changes to the app without needing to save, it's still always nice to make sure that the user doesn't want to save before moving to another screen.

  * **Confirm delete.** As we confirm savings, it's always good to confirm that the user wants to delete an item. I am sure that many of you (as I) have deleted something on a page without really wanting to do so!

  * **Drop-down list type ahead.** When you have hundreds of options to choose from, it's much nicer to have the option to type ahead than to have to go through the whole list.

  * **Invalid options.** Sometimes, for some specific options, you need to validate other characteristics before being able to use that option. This option should only be shown available when all characteristics are fulfilled. An example would be not showing that you can go to the next screen before fulfilling all the required information.

  * **Menu items.** Only show menu items that are available at the moment instead of showing all the items even though they are not available.

  * **Error messages.** Error messages should be informative.

  * **Working shortcuts.** If you've got shortcuts on your application, make sure they all work, no matter which browsers are being used.

Earlier, I mentioned the three main ways of doing UI testing, but we didn't really talk about the automation tools that will make this possible and that will definitely make your life easier. Here are a few we recommend.

## 1\. Watir

[Watir](http://www.watir.com/) is an open-source Ruby library that interacts with a browser the same way people do (clicking links, filling out forms, and validating text). It has a simple class for non-tech users. It has multi-browser support and a rich API.

## 2\. Sahi

[Sahi](http://sahipro.com/) has a good capture-and-replay utility and is quite easy to learn. In fact, it has an all-in-one solution (capture, replay, debug, troubleshoot, log management, etc.). It uses JavaScript as the scripting language. Another nice thing about Sahi is that is has a very good development community with an active forum and they have frequent releases.

## 3\. Sikilu

[Sikilu](http://www.sikuli.org/) automates anything you see on the screen. It uses image recognition to identify and control GUI components and it is useful when there is no easy access to a GUI's internal or source code. It uses Python as a scripting language and is used mainly on Windows, Mac OSX, and Linux.

## 4\. AutoIT

[AutoIT](https://www.autoitscript.com/site/autoit/) is a freeware automation language for Microsoft Windows. It automates tasks in a way that is not possible with other languages. Unlike other tools, AutoIT provides real-time mouse movements to select an element. It's very small and self-contained and will run on all versions of Windows.

## 5\. TestComplete 

With [TestComplete](https://smartbear.com/product/testcomplete/overview/), you get the chance to choose between JavaScript, Python, VBScript, JScript, DelphiScript, C++Script, and C#Script to create tests. It is quite easy to understand and makes it easy to automate tests on windows desktop, web apps, and mobile devices.

## Conclusion

In conclusion, here are a couple of reasons why you should automate your UI testing.

  * You will be able to find regression errors.
  * Test automation will guarantee you consistency.
  * You will reduce the margin of errors.
  * Automation increases efficiency. Manual GUI testing can be very long and inefficient. Resources and testers should be working on other things instead of running tests that a robot can do. 
  * You will use fewer resources and you do it faster. You will save time, resources, and money. 
  * Upgrading will occur often. Keep in mind that with every new test and every new bug discovered, the tool upgrades the information and you will always keep up-to-date.
  * You will get better QA ticket quality.

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).
