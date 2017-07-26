# App Extensions Are Not a Replacement for User Automation

_Captured: 2017-01-11 at 18:03 from [www.macstories.net](https://www.macstories.net/stories/app-extensions-are-not-a-replacement-for-user-automation/)_

Here's a thought experiment. Let's imagine that Apple decided to combine their engineering resources to form app teams that delivered both iOS and macOS versions of applications.

In such a scenario it may seem logical to retain application features common to both platforms and to remove those that were perceived to require extra resources. Certainly Automation would be something examined in that regard, and the idea might be posited that: "**App Extensions** are equivalent to, or could be a replacement for, **User Automation** in macOS." And by User Automation, I'm referring to Apple Event scripting, Automator, Services, the UNIX command line utilities, etc.

Let's examine the validity of that conjecture, beginning with overviews of App Extensions and User Automation.

## What are App Extensions?

**App Extensions** (often called simply "extensions") are essentially application (or framework) plugins that provide the functionality to perform specific tasks, such as manipulate an image, post media items to social services, share items and documents, or filter an audio stream. There are many types of extensions, and you control their use in the Extensions preference pane of the [System Preferences](x-apple.systempreferences:) application.

But the most important ability of App Extensions is that they can be used by apps other than the one in which they are contained. For example, an application that creates QR codes may also contain an app extension that enables other applications to use the containing application's functions to create and place QR codes within their own documents.

Extensions physically exist as bundles (with the file extension "appex") placed within their containing application's bundle. However, macOS will make them available while you are using other applications by placing them at "extension points," such as in the Share Menu, or in the Photos application when it is in edit mode.

![](https://31468fb5fb2bdd537aee-cb22f1c32609fa6d332a03da76e227e5.ssl.cf1.rackcdn.com/photos-extension-point-opt1483984673219.jpg)

In the example shown above, extensions included in the Pixelmator application are available as filter and editing options in the Photos application. When an extension is chosen, the Photos interface changes to display the image and extension controls.

![](https://31468fb5fb2bdd537aee-cb22f1c32609fa6d332a03da76e227e5.ssl.cf1.rackcdn.com/extension-mode1483984738148.jpg)

You can make edits to the image using the tools provided by the extension, click the "Save Changes" button, and you will be returned to the standard Photos interface.

Extension Points are exposed in multiple locations in macOS, from additional data sharing options added to the Share Menu, to inline content such as the Markup extension in Mail. The chart below lists some of the macOS extension points (types):

![](https://31468fb5fb2bdd537aee-cb22f1c32609fa6d332a03da76e227e5.ssl.cf1.rackcdn.com/extension-points1483984768127.jpg)

### How do App Extensions work?

By design, most App Extensions follow specific rules governing how they function. In general:

  * Some app extensions, like content blockers, can run without user interaction. But other extensions, like those that manipulate images, are triggered only by direct user action, such as selecting a menu item, or pressing a button.
  * Once triggered by the user, the extension is provided a copy of the current object or data selected in the hosting application. The extension may display a user interface (if needed), then processes the data, and returns the edited data to the hosting app.

  * By design, App Extensions have restricted access to resources outside of their bundle, and have restrictions placed upon them in regard to their access to the macOS frameworks, networks, and the user environment.

### Who creates App Extensions?

App Extensions are created by Apple developers in [Xcode](https://developer.apple.com/xcode/) using either the [Swift](http://www.apple.com/swift/) or [Objective-C](https://developer.apple.com/reference/objectivec) programming languages. Non-programmers are not the target audience for developing app extensions.

### App Extensions Summary

App Extensions are developer-created application plugins, exposing powerful functionality within multiple applications at pre-determined "Extension Points," such as in the Share Menu, or in the Today view of the Notification Center. App Extensions are executed within a defined set of parameters and restrictions, and their scope is often limited to processing the selection in the host application.

## What is User Automation?

The term **User Automation** represents multiple technologies and architectures whose purpose is to enable the user to create simple or extended workflows for editing documents, processing data, and performing repetitive tasks.

The technologies of User Automation operate with the user's level of authority and are not restricted in the scope of their abilities: **whatever the user can do, they can do**. They have unrivaled access to the frameworks of the operating system, and to the extensive library of UNIX tools that ship with macOS. And most importantly, AppleScript, JavaScript (JXA), and Automator can directly query and control scriptable applications using Apple Events, the inter-application communication technology that has existed on the Mac since System 7.

macOS applications that support Apple Events are said to be "scriptable," in that they allow the built-in Cocoa scripting frameworks of macOS to communicate with and control the application and its elements. Every "scriptable" application includes a "dictionary" providing detailed information about every scriptable object in the application and the commands used to interact with them. As an example, the dictionary excerpt shown below is from the Keynote application's dictionary, and describes the slide object of a Keynote presentation document.

slide _n _: [_inh_. iWork container; see also Compatibility Suite] : A slide in a presentation document.

elements

contains audio clips, charts, iWork items, lines, movies, shapes, tables, text items; contained by document.

properties

base slide ( master slide ) : The master slide this slide is based upon.

body showing ( boolean ) : Is the default body text item visible on the slide?

default body item ( text item r/o ) : The default text item container for the body text of the slide. Its visibility is determined by the value of the body showing property.

default title item ( text item r/o ) : The default text item container for the title text of the slide. Its visibility is determined by the value of the title showing property.

presenter notes ( rich text ) : The presenter notes for the slide.

skipped ( boolean ) : Is the slide skipped?

slide number ( integer r/o ) : The index of the slide from the beginning of the document. Note: skipped slides have a slide number value of -1. Un-skipped slides have a positive slide number value.

title showing ( boolean ) : Is the default title text item visible on the slide?

transition properties ( transition settings ) : A list of key/value pairs for the properties of the slide's transition.

responds to

get, set, delete, exists, make, move, duplicate

Using this dictionary, scripts written using the macOS scripting languages can create, move, duplicate, and delete slides, as well as change their master slide, read, set, and edit their displayed text, add images and video elements, and even adjust whether they are skipped or shown. **No other architecture or framework in macOS offers the ability to query and control the internal workings of applications like Apple Events.** And most of the important productivity applications, such as Microsoft Office, Adobe InDesign, and the excellent suite of apps from the Omni Group, include robust and extensive scripting support, and are the "go-to apps" for implementing powerful user automation workflows.

Apple Events are used to communicate with _applications_. For communication with the OS and its tools, the User Automation technologies of AppleScript and JavaScript (JXA) have integrated code "bridges" that provide them access to all of the Cocoa frameworks, some of which are listed in this graphic.

![](https://31468fb5fb2bdd537aee-cb22f1c32609fa6d332a03da76e227e5.ssl.cf1.rackcdn.com/user-automation-apis1483984847216.jpg)

Using these frameworks as well as the default UNIX tools of macOS, the scope of what scripts can do expands to an impressive range of abilities.

And since User Automation can freely work between applications and frameworks, creating workflows that involve multiple apps and the transformation of data are common practice. For example, the workflow shown in the animation below begins with converting a table in a Numbers document into a chart in Keynote, then adding text, generating a QR code, and finally sending the completed Keynote document in an email message. All of these actions are possible with user automation.

Below is the AppleScript script code used to transfer and transform Numbers table data into a new chart in Keynote. As you can see, [scripting support](https://iworkautomation.com/) (Apple Events) provides direct access to the internal workings of the iWork applications. An Apple Events-based script can deep query the selected table object in Numbers to retrieve a range of data, and then use the retrieved data to create a new slide and chart in Keynote.
    
    
        tell the front document
            set aTable to the first table of active sheet whose class of selection range is range
            set aRange to cell range of aTable
                copy {column count, row count} to {columnCount, rowCount}
                copy {header column count, header row count, footer row count} to {headerColumnCount, headerRowCount, FooterRowCount}
                set dataRowCount to rowCount - headerRowCount - FooterRowCount
                if headerRowCount is 0 then
                        set the end of the columnNames to ""
                    set columnNames to the formatted value of cells (headerColumnCount + 1) thru -1 of row headerRowCount
                        set the end of the rowNames to ""
                    set rowNames to the formatted value of cells (headerRowCount + 1) thru (FooterRowCount - 1) of column headerColumnCount
                set topLeftRangeCellID to the name of cell (headerColumnCount + 1) of row (headerRowCount + 1)
                set bottomRightRangeCellID to the name of last cell of row ((FooterRowCount + 1) * -1)
                set tableDataRange to range (topLeftRangeCellID & ":" & bottomRightRangeCellID)
                set cellValuesArray to value of every cell of tableDataRange
                repeat ((count of cellValuesArray) div dataColumnCount) times
                    set the end of chartData to items x thru (x + (dataColumnCount - 1)) of cellValuesArray
                    set x to x + dataColumnCount
            set aSlide to make new slide with properties {base slide:master slide "Blank"}
                add chart row names rowNames column names columnNames data chartData type vertical_bar_2d group by chart column
    

And if you prefer using a scripting language other than AppleScript, the same Apple Event functionality could be delivered via a [JavaScript](https://developer.apple.com/library/content/releasenotes/InterapplicationCommunication/RN-JavaScriptForAutomation/Articles/OSX10-11.html#//apple_ref/doc/uid/TP40014508-CH110-SW1) (JXA) script…
    
    
    Keynote.addChart(newSlide,{rowNames:rwNames, columnNames:colNames, data:chartData, type:"vertical_bar_2d", groupBy:"chart row"})
    

> Excerpt shown here, [open in script editor](applescript://com.apple.scripteditor?action=new&name=New%20Chart&script=transferNumbersTableToKeynoteChart%28%29%0D%0Dfunction%20transferNumbersTableToKeynoteChart%28%29%7B%0D%09var%20Numbers%20%3D%20Application%28%27com.apple.iWork.Numbers%27%29%0D%09var%20frontDocument%20%3D%20Numbers.documents%5B0%5D%0D%09for%20%28i%20%3D%200%3B%20i%20%3C%20frontDocument.activeSheet.tables.length%3B%20i%2B%2B%29%20%7B%0D%09%09if%20%28frontDocument.activeSheet.tables%5Bi%5D.selectionRange%28%29%20!%3D%20null%29%20%7B%0D%09%09%09var%20aTable%20%3D%20frontDocument.activeSheet.tables%5Bi%5D%0D%09%09%09var%20aRange%20%3D%20aTable.cellRange%0D%09%09%09var%20columnsLength%20%3D%20aTable.columnCount%28%29%0D%09%09%09var%20rowsLength%20%3D%20aTable.rowCount%28%29%0D%09%09%09var%20headerColumnsLength%20%3D%20aTable.headerColumnCount%28%29%0D%09%09%09var%20headerRowsLength%20%3D%20aTable.headerRowCount%28%29%0D%09%09%09var%20footerRowsLength%20%3D%20aTable.footerRowCount%28%29%0D%09%09%09var%20dataColumnCount%20%3D%20columnsLength%20-%20headerColumnsLength%0D%09%09%09var%20dataRowCount%20%3D%20rowsLength%20-%20headerRowsLength%20-%20footerRowsLength%0D%09%09%09var%20colNames%20%3D%20%5B%5D%0D%09%09%09var%20rwNames%20%3D%20%5B%5D%0D%09%09%09if%20%28headerRowsLength%20%3D%3D%200%20%29%7B%0D%09%09%09%09for%20%28i%20%3D%200%3B%20i%20%3C%20dataColumnCount%3B%20i%2B%2B%29%20%7B%0D%09%09%09%09%09colNames.push%28%22%22%29%0D%09%09%09%09%7D%0D%09%09%09%7D%20else%20%7B%0D%09%09%09%09var%20aRow%20%3D%20aTable.rows%5BheaderRowsLength-1%5D%0D%09%09%09%09var%20cellCount%20%3D%20aRow.cells.length%0D%09%09%09%09for%20%28i%20%3D%20headerColumnsLength%3B%20i%20%3C%20cellCount%3B%20i%2B%2B%29%20%7B%0D%09%09%09%09%09colNames.push%28aRow.cells%5Bi%5D.formattedValue%28%29%29%0D%09%09%09%09%7D%0D%09%09%09%7D%0D%09%09%09if%20%28headerColumnsLength%20%3D%3D%200%20%29%7B%0D%09%09%09%09for%20%28i%20%3D%200%3B%20i%20%3C%20dataRowCount%3B%20i%2B%2B%29%20%7B%0D%09%09%09%09%09rwNames.push%28%22%22%29%0D%09%09%09%09%7D%0D%09%09%09%7D%20else%20%7B%0D%09%09%09%09var%20aColumn%20%3D%20aTable.columns%5BheaderColumnsLength-1%5D%0D%09%09%09%09var%20cellCount%20%3D%20aColumn.cells.length%0D%09%09%09%09for%20%28i%20%3D%20headerRowsLength%3B%20i%20%3C%20cellCount%3B%20i%2B%2B%29%20%7B%0D%09%09%09%09%09rwNames.push%28aColumn.cells%5Bi%5D.formattedValue%28%29%29%0D%09%09%09%09%7D%0D%09%09%09%7D%0D%09%09%09var%20rowData%20%3D%20%5B%5D%0D%09%09%09var%20chartData%20%3D%20%5B%5D%0D%09%09%09for%20%28i%20%3D%20headerRowsLength%3B%20i%20%3C%20rowsLength-footerRowsLength%3B%20i%2B%2B%29%20%7B%0D%09%09%09%09rowData%20%3D%20aTable.rows%5Bi%5D.cells.value%28%29%0D%09%09%09%09rowData%20%3D%20rowData.slice%28headerColumnsLength%2C%20columnsLength%29%0D%09%09%09%09chartData.push%28rowData%29%0D%09%09%09%7D%0D%09%09%09var%20Keynote%20%3D%20Application%28%27com.apple.iWork.Keynote%27%29%0D%09%09%09Keynote.activate%28%29%0D%09%09%09var%20frontDocument%20%3D%20Keynote.documents%5B0%5D%0D%09%09%09var%20aMasterSlide%20%3D%20frontDocument.masterSlides%5B%22Blank%22%5D%3B%0D%09%09%09var%20newSlide%20%3D%20Keynote.Slide%28%7BbaseSlide%3AaMasterSlide%7D%29%3B%0D%09%09%09frontDocument.slides.push%28newSlide%29%3B%0D%09%09%09Keynote.addChart%28newSlide%2C%7BrowNames%3ArwNames%2CcolumnNames%3A%20colNames%2Cdata%3AchartData%2Ctype%3A%22vertical_bar_2d%22%2CgroupBy%3A%22chart%20row%22%7D%29%0D%09%09%09return%20true%0D%09%09%7D%0D%09%7D%0D%7D) to see the full script. 

…or by using [Automator actions for Keynote](https://iworkautomation.com/keynote/automator/chart-actions-01.html).

## Automator

And then there's Automator. The unrivaled tool for creating your own "automation recipes" using a simple drag-and-drop process of stringing together nuggets of predefined functionality (Automator actions) into "workflows." Saved workflows can be executed at integrated extension points throughout macOS, including: as contextual System Services, as Image Capture and Print to PDF plugins, as Folder Actions, as Script Menu items, as Calendar alarms, and even as stand-alone applets or droplets.

There's a common misconception that Automator is "visual-AppleScript," but Automator is actually language-agnostic. Its "actions" can be written in nearly every macOS-supported automation language: AppleScript, AppleScriptObj-C, JavaScript, Shell, perl, python, ruby, and Objective-C. Automator can drive Apple Events, the UNIX utilities, and the Cocoa frameworks, within a single workflow. Automator also has an [extensive variable architecture](https://userautomation.com/automator-variables.html) for capturing, generating, and reusing data during the execution of its workflows.

Automator is unprecedented in its scope and abilities in macOS. No application or system service comes close to matching what it can do.

But the most amazing thing about Automator is that powerful automation tools can be created by users _without writing a single line of code_--like this contextual system service that combines the PDF files selected in the Finder:

![](https://31468fb5fb2bdd537aee-cb22f1c32609fa6d332a03da76e227e5.ssl.cf1.rackcdn.com/automator-service1483984926203.jpg)

### Who creates User Automation tools?

Which brings up the question: _who creates User Automation tools_?

In my 23-years of working with customers and businesses around the globe, it is my observation that the majority of automation solutions are created in-house by customers and employees, motivated to address the challenges, complexities, and redundancies they face in their day-to-day work.

Of course this is not to say that I have not witnessed numerous solutions created by professionals for businesses, some of which involved very elaborate and powerful codebases, but much of the time an automation solution is as simple as a script or collection of scripts created by someone who is not a programmer or developer.

Automation tools aren't limited to scripts and some may display interfaces (such as Automator actions) for interacting dynamically with the user. These tools are usually written in Xcode, using the provided AppleScript application and Automator actions templates. Xcode automation projects can incorporate all of the standard UI elements, outlets, actions, and bindings used in the creation of traditional macOS and iOS applications.

For writing AppleScript or JavaScript (JXA) scripts, you can use the Script Editor application that ships with every copy of macOS, or for composing and editing AppleScript and AppleScriptObj-C scripts you can use feature-rich 3rd-party editors like [Script Debugger](http://latenightsw.com/) that include code-completion and step-by-step debugging.

User Automation involves a variety of languages and technologies. The native Apple Events architecture of macOS provides the means for communicating with applications via scripts or code. The Objective-C bridges for JavaScript (JXA) and AppleScript (AppleScriptObj-C) provide access to the Cocoa frameworks that are the foundation of macOS. And specialized scripting additions (OSAX) deliver access to the UNIX command line and the numerous utilities that come with being a UNIX-based OS. And then there's Automator, which has access to practically everything.

But putting the technicalities aside, the whole purpose of _User_ Automation is to serve the _user_ of the computer, to enable a motivated customer to use and create automation tools, like scripts, workflows, and applets, without restrictions or the requirement of being a developer proficient in Xcode and Objective-C or Swift. _User Automation is for the rest of us_. Ah, remember that old chestnut?

## Conclusion

**Tubes and Wires**. I came across this quote the other day:

> AppleScript has survived and remained relevant during a turbulent decade-long transition, despite its unbeloved language syntax and technical hurdles, for the simple reason that it solves real-world problems in a way that no other OS X technology does. In theory, AppleScript could be much better; in practice, though, it's the best thing we have that works. It exemplifies the Mac's advantages over iOS for tinkerers and advanced users.  
--John Gruber, Macworld, Dec 12, 2012, The unlikely persistence of AppleScript 

App Extensions and the User Automation technologies have _some_ similarities but _many_ differences. App Extensions are written by developers. User Automation is often written by customers. App Extensions provide restricted manipulation of selected data, while User Automation enables open query and control of applications and frameworks. App Extensions represent a habitat of "approved" developer-created _tubes_, while User Automation is about connecting _wires_ to application and framework APIs to create a flow. App Extensions exist as app plugins. User Automation technologies are manifested as scripts, workflows, applets, droplets, applications, services, and plugins, available globally and at extension points throughout macOS.

Based upon the information presented in this overview, it is clear that App Extensions do not provide the same abilities and functionality as the User Automation technologies of macOS, and objectively should not be considered a comparable replacement for them. Of course, this conclusion assumes that customers should retain the same level of control over their devices as provided by the current User Automation in macOS. Such is the foundation of the credo that _the power of the computer should reside in the hands of the one using it_.

But let's take a step back, and think about this topic differently. **Why not have both?**

Perhaps it is time for Apple and all of us to think of User Automation and App Extensions in terms of "AND" instead of "OR." To embrace the development of a new cross-platform automation architecture, maybe called "AutomationKit," that would incorporate the "everyman openness" of User Automation with the focused abilities of developer-created plugins. App Extensions could become the new macOS System Services, and Automator could save workflows as Extensions with access to the Share Menu and new "non-selection" extension points. And AutomationKit could even include an Apple Event bridge so that it would work with the existing macOS automation tools.

App Extensions could become another type of User Automation. What a concept.

![](https://31468fb5fb2bdd537aee-cb22f1c32609fa6d332a03da76e227e5.ssl.cf1.rackcdn.com/circles1483984987315.png)

  * [Xcode template for writing Automator actions for the Apple Configurator iOS device management application.](https://configautomation.com/developer.html)

Club MacStories offers exclusive access to **extra MacStories content**, delivered every week; it's also a way to support us directly.

Club MacStories will help you discover the best apps for your devices and get the most out of your iPhone, iPad, and Mac. Plus, it's made in Italy.

Starting at $5/month, with an annual option available. [Join the Club](https://club.macstories.net/?utm_source=ms&utm_medium=web-inline).

  * **MacStories Weekly** newsletter, delivered every week on Friday with app collections, tips, iOS workflows, and more;
  * **Monthly Log** newsletter, delivered once every month with behind-the-scenes stories, app notes, personal journals, and more;
  * **Access** to occasional giveaways, discounts, and free downloads.
