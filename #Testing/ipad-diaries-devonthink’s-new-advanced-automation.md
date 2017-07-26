# iPad Diaries: DEVONthink’s New Advanced Automation

_Captured: 2017-04-28 at 23:54 from [www.macstories.net](https://www.macstories.net/ios/ipad-diaries-devonthinks-new-advanced-automation/)_

![](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/2017-04-26-22-42-46.jpeg)

_iPad Diaries is a regular series about using the iPad as a primary computer. You can find more installments [here](https://www.macstories.net/tag/ipad-diaries/) and subscribe to the dedicated [RSS feed](https://www.macstories.net/tag/ipad-diaries/feed)._

When I covered [DEVONthink To Go](https://itunes.apple.com/us/app/devonthink-to-go/id395722470?mt=8&uo=4&at=10l6nh&ct=ipad_diaries) in the first [iPad Diaries column back in February](https://www.macstories.net/ios/ipad-diaries-advanced-file-management-and-research-with-devonthink/), I briefly mentioned the app's limited support for URL schemes and automation. I concluded the article noting that DEVONthink's advanced file management features were ideal candidates for my writing workflow - particularly given the app's ability to store different types of documents, reference them with unique links, and search them with Boolean operators. I also expanded upon the idea of using DEVONthink as my only iOS file manager in [the latest episode of Mac Power Users](https://www.relay.fm/mpu/374).

I've been moving more work documents and other research material (web archives and PDFs, mostly) to DEVONthink over the past two months. The turning point occurred a few weeks ago, when DEVONtechnologies began adding advanced [x-callback-url automation](http://x-callback-url.com/) to DEVONthink's beta channel and were kind enough to let me test and provide feedback for the functionality.

I was genuinely excited by the prospect of a scriptable DEVONthink: due to iOS' lack of a deeply integrated Finder, I've always wanted a file manager that could be extended and enhanced through automation and other apps. With an improved set of URL commands and various optimizations for usage in Workflow, DEVONthink To Go can now be that kind of file manager. I made my decision: this is the app I'm going to use to manage the research content for my iOS 11 review this summer.

The automation features introduced by DEVONtechnologies in the latest DEVONthink for iOS go deep into the app's structure, covering discrete functionalities such as file creation, search, and data retrieval. These changes will enable a greater number of users to integrate DEVONthink with their favorite iPad apps and workflows. And while the new commands are documented in the app, I thought it'd be useful to provide some concrete examples of how we can take DEVONthink to the next level through automation.

## DEVONthink's New Commands

Before digging into DEVONthink's improved automation commands and Workflow integration, it's important to explain what, exactly, DEVONtechnologies has changed.

The latest DEVONthink To Go is fully compliant with the x-callback-url spec and can be chained with other apps to perform actions and return data to the calling app. The primary reason for the adoption of x-callback-url is easy creation of actions in Workflow, but DEVONthink's URL scheme can be used by any other launchers on iOS - including [Launcher](https://itunes.apple.com/us/app/launcher-with-notification-center-widgets/id905099592?mt=8&uo=4&at=10l6nh&ct=ipad_diaries), [Launch Center Pro](https://itunes.apple.com/us/app/launch-center-pro-shortcut-launcher-workflows/id532016360?mt=8&uo=4&at=10l6nh&ct=ipad_diaries), [Drafts](https://itunes.apple.com/us/app/drafts-quickly-capture-notes-share-anywhere/id905337691?mt=8&uo=4&at=10l6nh&ct=ipad_diaries), and even Safari bookmarklets. In this article, I'm going to focus on pre-made automations for the Workflow app.

The new set of automation commands in DEVONthink is quite extensive. Using URL schemes, you can call DEVONthink to perform the following actions (in addition to the existing commands I mentioned in February):

  * Create new images;
  * Create new documents, using file data and [UTI details](https://en.m.wikipedia.org/wiki/Uniform_Type_Identifier) to specify which kind of document;
  * Add comments to files;
  * Retrieve file metadata;
  * Retrieve file contents;
  * Open a search in the app;
  * Perform a search and send back a list of results to another app.

All of these commands are based on two core features that DEVONtechnologies implemented: [base64 encoding](https://en.m.wikipedia.org/wiki/Base64) to create new files in DEVONthink and retrieve their contents from other apps; and [JSON objects](https://www.w3schools.com/js/js_json_objects.asp) to return file metadata or search results as [dictionaries](https://www.macstories.net/ios/workflow-update-brings-ability-to-interact-with-any-web-api/) that can be parsed by Workflow.

If you're an iPad power user who's been keeping an eye on DEVONthink, I bet your automation senses are tingling at this point. Thus, allow me to explain how I've been taking advantage of DEVONthink's deeper automation and what I have in mind for my future usage of the app.

### Create Images

I take _a lot_ of screenshots on a daily basis. The number goes up dramatically in the summer when I'm writing my annual iOS reviews as I take hundreds of screenshots for every beta seed. There's no great way to reference individual images in Apple's Photos app, but that's an area where DEVONthink excels thanks to its item links - bookmarks for individual files that can be opened from other apps. There's only one problem: importing a new image into DEVONthink is too slow and takes too many taps.

Enter the new `createImage` command in the DEVONthink URL scheme. Using this command, we can send an image to the app and create it in a specific group with a name and even a comment attached to it. Thus, rather than opening DEVONthink's file menu, picking an image, and then opening its metadata panel to type a comment, we can now do everything at once from Workflow, saving a lot of time.

![The workflow will ask for a title and comment with 'Ask for Input' actions before launching DEVONthink.](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/2017-04-26-22-52-09.jpeg)

> _The workflow will ask for a title and comment with 'Ask for Input' actions before launching DEVONthink._

With the workflow I've put together, you can send images to DEVONthink in two ways: you can either manually pick them from a photo picker, or you can select some images in the Photos app and share them with the workflow via the action extension. For each image you pick, Workflow will ask you to add a title (used as filename) and a comment; both are optional, but I recommend at least adding a title for context.

Each image will then kick off DEVONthink's automation by opening the app, saving the file, and going back to Workflow to repeat the process for the following image. This is the magic of x-callback-url and repeat loops at play, and it's best used with **Workflow in full-screen** - not in Split View. If you pick 10 images, Workflow and DEVONthink will switch between each other 10 times; it's not pretty to look at, but it works, and it speeds up image creation in the app considerably.

![](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/2017-04-26-16-04-34.jpeg)

> _Adding a comment for the image in Workflow._

The comment is also embedded with the image in DEVONthink.

At the end the workflow, you'll end up with a list of DEVONthink item links in your clipboard, which you can save in a note to reference each individual file you've just created in DEVONthink.

![The output of the DEVONimage workflow: title, item link, and comment.](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/2017-04-26-16-19-01.jpeg)

> _The output of the DEVONimage workflow: title, item link, and comment._

To better demonstrate this workflow, take a look at the video below and how easily I can archive a screenshot in DEVONthink:

There's an aspect of this automation I want to highlight, and it's how Workflow visually exposes the `x-success` parameter sent back by DEVONthink. After successfully creating an image, DEVONthink knows that it needs to launch Workflow again, and it'll do so by sending a JSON object with metadata for the newly created file. All it takes for Workflow to interpret this data is a 'Get Dictionary Value' action.

This idea is the centerpiece of DEVONthink's new automation, which explains why these URL schemes are best experienced in Workflow's visual playground rather than other, more limited launchers.

![](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/2017-04-26-16-10-50.jpeg)

> _The result of x-callback-url automation can be used as a Magic Variable in Workflow._

[ ![<p&gtWhat x-callback-url’s JSON looks like as a dictionary under the hood. In practice, you’ll never have to deal with this.</p&gt
](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/IMG_3850.jpeg) ](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/2017-04-26-16-11-51.jpeg)

> _

What x-callback-url's JSON looks like as a dictionary under the hood. In practice, you'll never have to deal with this.

_

This summer, I'm going to enhance this workflow to ensure that images are also saved in a specific group in DEVONthink. By default, new files are created in the app's global inbox; by adding a `destination` parameter with a UUID value to the URL command, we can tell DEVONthink to create a file inside an existing group.[1](https://www.macstories.net/ios/ipad-diaries-devonthinks-new-advanced-automation/)

This workflow alone has been a game changer for how I can take screenshots and save them somewhere I can reference them later. After years of trying to find old screenshots in Photos or, worse, having to manually import images one by one in [Scrivener](https://itunes.apple.com/us/app/scrivener/id972387337?mt=8&uo=4&at=10l6nh&ct=ipad_diaries), I now have a system to archive images, add comments to them, and automatically organize them. This workflow is going to become my most used one for longer stories and app reviews.

You can [get the workflow here](https://workflow.is/workflows/1d3e9887743b48568d5d1ee3a49e95cc).

The same technique that powers the `createImage` command - sending file attachments as base64-encoded strings - works for saving other documents in DEVONthink as well, such as PDFs. Using the Workflow extension with the 'Get Type' action, we can build a "smart extension menu" that sends a different command to DEVONthink depending on the file a user has shared with the extension.

This workflow is called DEVONmenu, and it intelligently creates the following document types in DEVONthink starting from the share sheet:

  * Web archives
  * Images
  * Markdown notes
  * PDFs

You don't have to choose a file type manually; Workflow can understand what type of file it's dealing with on its own. Before I get into the workflow's core ideas, though, let's take a look at how it works in practice:

The workflow's ability to discern multiple formats is made possible by the app's understanding of file types, but we also have to highlight the new commands and changes brought to DEVONthink in its latest release.

Most notably:

  * Images and PDFs can be created with the same new command (`createDocument`) by encoding files to base64 and attaching that string to the `source` parameter;
  * Images and PDFs created with the same command require a UTI string - examples of which [can be found on Apple's website](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/UTIRef/Articles/System-DeclaredUniformTypeIdentifiers.html);
  * Markdown notes and web archives have dedicated commands in the DEVONthink URL scheme;
  * Every file can be sent to DEVONthink with a title and a comment;
  * Once created, files can relaunch Workflow and pass their unique DEVONthink links to the app.

This versatility is the result of DEVONtechnologies' adoption of a rich set of x-callback-url commands; at this point, I'd say DEVONthink and Ulysses are the most flexible and powerful implementations of URL schemes optimized for Workflow on iOS.

The "optimized" qualifier is there for a reason: with the workflows I made, you **never** have to see or edit the URL schemes themselves. The actions I used are meant to abstract the complexity of URL schemes[2](https://www.macstories.net/ios/ipad-diaries-devonthinks-new-advanced-automation/) and provide an automation environment that "just works".

![](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/2017-04-26-16-34-40.jpeg)

> _Saving a PDF from iCloud Drive._

Whether you've selected some text or are sharing a PDF from the share sheet, you can invoke the DEVONmenu workflow, add a title and an optional comment, and save everything to DEVONthink. Unlike the default DEVONthink extension, this workflow will allow you to quickly save multiple documents at once, with comments, and with unique links for each document copied into the clipboard at the end.

The DEVONmenu workflow supercharges DEVONthink's Save dialog with automation and Workflow's integrations; I'm using it every day.

You can [get the workflow here](https://workflow.is/workflows/4dcf17e988d444dd9b80c5a1a7d5e77d).

What happens when you want to fetch a file you've already saved in DEVONthink, though? I'm glad you asked.

Just like DEVONthink supports saving files through the URL scheme via an encoded text string, the same idea works in reverse - you can read files from the URL scheme by _decoding_ a base64 string. If you use Workflow, decoding a base64 string takes only one action, which will return the original file as a Magic Variable. And obviously, the fastest way to retrieve a specific file already in DEVONthink involves the option I've added to all my workflows: unique item links.

I've always struggled to save screenshots for app reviews and articles while I was researching or writing them. Eventually, they'd get lost in Photos or I'd accidentally delete them. With DEVONthink and its item links, however, I've found a way to save images in an app that can expose them externally with links. So after solving the problem of quickly saving screenshots through automation, I turned my attention to the other end of my writing workflow - turning image references from my Markdown notes into actual image files.

I came up with this workflow by considering how I write and finding a solution that would require the least possible effort on my part. When I'm writing a story such as this one, I think of specific app features or interfaces that I want to capture right away. To do so, I can now take a screenshot, run the DEVONimage workflow, and receive a DEVONthink file link after the image has been saved. In Ulysses - my favorite text editor - I can hit Paste and the DEVONthink image link will become tappable in the document I'm working on.[3](https://www.macstories.net/ios/ipad-diaries-devonthinks-new-advanced-automation/)

![A DEVONthink item link can become tappable in Ulysses, but it takes some editing.](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/2017-04-26-22-54-47.jpeg)

> _A DEVONthink item link can become tappable in Ulysses, but it takes some editing._

Double-tapping the image link brings up Ulysses' link editing UI, which has a button to open the original source. Doing so with a DEVONthink link launches DEVONthink and shows the file. This allows me to check on embedded reference material in a couple of seconds and it works even if I'm offline because images are stored locally in DEVONthink.

Once I'm editing a draft, it's time to turn the DEVONthink link into a public URL to an image uploaded to our CDN. This is where the Get DEVONimage workflow comes in.

Thanks to its new automation commands, DEVONthink can now provide Workflow with two distinct kinds of details about a file: its metadata or its contents. Metadata include information such as the filename, creation date, and comments; the file contents are a base64-encoded string that can be decoded by Workflow into a native file. Using these two commands, I can first confirm that a file still exists in DEVONthink, and if it does, transform its base64 representation into an image available on the web.

The workflow I've put together accepts `x-devonthink://` file links either from the clipboard or shared with the Workflow extension.[4](https://www.macstories.net/ios/ipad-diaries-devonthinks-new-advanced-automation/) After reading the file link from the clipboard, the workflow isolates the file's UUID and launches DEVONthink with the `item` command. This action finds an item in DEVONthink's database by its ID and sends back metadata to Workflow using x-callback-url.

![File metadata passed from DEVONthink to Workflow.](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/2017-04-26-22-55-40.jpeg)

> _File metadata passed from DEVONthink to Workflow._

At this point, if the image exists, I want to upload it. First, I make Workflow check that the UTI of the file contains the word "image". If it doesn't, an alert comes up saying that I should try again with another file. This check prevents me from accidentally uploading, say, a PDF instead of a screenshot.

![An error comes up if the DEVONimage workflow doesn't receive an image file.](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/2017-04-26-22-56-21.jpeg)

> _An error comes up if the DEVONimage workflow doesn't receive an image file._

If the file is indeed an image, the workflow needs to launch DEVONthink again to fetch its contents via a base64 string.[5](https://www.macstories.net/ios/ipad-diaries-devonthinks-new-advanced-automation/) Once the file is passed back to workflow, it gets decoded, previewed with Quick Look, and, finally, uploaded to our CDN using a 'Run Workflow' action. You'll want to replace the upload action with whatever you use to upload images or save them somewhere else.

The Get DEVONimage workflow ends by generating a string of text I can paste in my Ulysses document. This text contains the image's new public URL and the file's comment, the latter directly fetched from DEVONthink. All I have to do is paste the text in Ulysses and format it as a Markdown image with a comment. In a couple of seconds, I've gone from a reference for a local file stored in DEVONthink to an image uploaded to our CDN that retains its original comment.

I've thought a lot about these image workflows because, as I said, I deal with hundreds of screenshots and they become a serious problem for my iOS reviews in the summer. I needed a better system to organize them, reference them, and turn them into uploads. With this setup, my Ulysses drafts look like this while I'm still writing them:

![DEVONthink image links and comments are highlighted in blue with my custom Ulysses theme.](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/2017-04-26-22-57-10.jpeg)

> _DEVONthink image links and comments are highlighted in blue with my custom Ulysses theme._

...and they turn into proper Markdown files with image links once I'm done editing:

![Markdown image links in Ulysses.](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/2017-04-26-22-58-09.jpeg)

> _Markdown image links in Ulysses._

There are a couple of ways this setup could be improved. First, I have to consider creating dedicated groups in DEVONthink for different articles I'm working on, as right now all images are saved in the global inbox.

Furthermore, Ulysses needs to support 'Paste as Markdown' - an option that has been available in the Mac version for years and that is still absent from the iOS app. With the ability to paste text as Markdown, I could create an `IMG` tag (instead of the blue highlighted text) as soon as I have a DEVONthink image link. Also, if I could choose one Scrivener feature to have in Ulysses, that would be an option to create arbitrary color highlights for text; that would allow me to easily distinguish portions of text within a document at a glance instead of using the app's 'Raw Source' button to highlight lines of text in blue.

I'm happy with the system I've established in DEVONthink, Workflow, and Ulysses. Keeping reference material in a separate app and connecting DEVONthink with Ulysses through Workflow enables me, among other things, to change image descriptions in DEVONthink, where it makes more sense to add comments to files. The screenshots in this story were all saved, embedded, and uploaded with this workflow, and I look forward to using it for bigger projects this year.

You can [get the workflow here](https://workflow.is/workflows/7695e08bc80e4007883e18a7e2eaf61c).

The final major addition to DEVONthink automation is the ability to start searches in the app and pass results back to Workflow with metadata for each result.

I covered DEVONthink's advanced search features in my previous coverage of the app - specifically, I focused on DEVONthink's `NEAR` operator to find words close to each other in PDF documents. My DEVONthink database isn't too big yet, but I've been running searches on a regular basis to find sections in past issues of MacStories Weekly and comments added to images or web archives. With automation, there's now a faster way to launch these advanced searches.

Effectively, the latest DEVONthink allows us to create saved searches in Workflow and open them in DEVONthink. There are two ways to search via automation: we can prepare a search query in Workflow and open the search screen with results in DEVONthink, or we can issue the search command from Workflow, temporarily launch DEVONthink to fetch results, and go back to Workflow to view results and process them.

I've been using both methods to find files in DEVONthink, but I find the latter to be more fascinating from a technical standpoint. Using x-callback-url, DEVONtechnologies has devised a system where Workflow can send a search query to DEVONthink, which will return a JSON object containing multiple results. Each result contains a set of metadata for the item, such as its ranking (as evaluated by DEVONthink's search algorithm), dates, comments, links, and more. This is basically an app search API, only exposed via a URL scheme.[6](https://www.macstories.net/ios/ipad-diaries-devonthinks-new-advanced-automation/)

To understand the limitations and possibilities enabled by automated DEVONthink search, I created a workflow that offers a total of four options. A search can either be a basic one (just type a search query), or it can be a `NEAR` search; if you don't want to use that operator, just swap it with another one. Then, the search can either stay in DEVONthink (so you can tap and preview results in the app), or it can kick you back to Workflow, which will parse results and display them in a list.

![](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/2017-04-26-23-00-46.jpeg)

> _Starting a DEVONthink search in Workflow._

I don't have a particular use case for feeding search results back to Workflow yet, but I added the option nonetheless as I wanted to understand the system and build a proof of concept for others to iterate upon.

The idea of a powerful app such as DEVONthink offering an x-callback-url search API that exposes rich results to other apps is an intriguing one. Performing additional filtering of results in Workflow by excluding file types or date ranges could be a possible use case; another could be to search for all files in a group and iterate over each item by opening its link, reading the file, and going back to Workflow. While both search methods would yield the same results, only one of them can be automated and integrated with other apps; I'm curious to see what other users will come up with.

I've mostly been using the DEVONsearch workflow to trigger `NEAR` searches from a widget. Unlike the other commands, I'm still experimenting with search, but I believe it has some serious potential.

You can [get the workflow here](https://workflow.is/workflows/0fe524bf65b54ad59fd3750e25e57f75).

The folks at DEVONtechnologies have been improving [DEVONthink To Go](https://itunes.apple.com/us/app/devonthink-to-go/id395722470?mt=8&uo=4&at=10l6nh&ct=ipad_diaries) at a remarkable pace over the past few months. As [I argued in February](https://www.macstories.net/ios/ipad-diaries-advanced-file-management-and-research-with-devonthink/), DEVONthink had already set a new standard for file managers on iOS thanks to its advanced search features and support for multiple document types. With its new automation, DEVONthink sets a standard for other pro apps on iOS, period.

DEVONthink's new automation features have provided a stronger foundation for managing my articles' assets and research material. I've always wanted a system to embed local file references to be processed at a later stage, and this is exactly what I had in mind. I'm also increasingly switching to PDFs and web bookmarks archived in DEVONthink now that the app can be integrated with Safari and email clients via Workflow. I'm still thinking about how to implement searches in Workflow, but I have some ideas.

[DEVONthink](https://itunes.apple.com/us/app/devonthink-to-go/id395722470?mt=8&uo=4&at=10l6nh&ct=ipad_diaries), [Ulysses](https://itunes.apple.com/us/app/ulysses/id950335311?mt=8&uo=4&at=10l6nh&ct=ipad_diaries), and [Workflow](https://itunes.apple.com/us/app/workflow-powerful-automation-made-simple/id915249334?mt=8&uo=4&at=10l6nh&ct=ipad_diaries) have become key elements of my writing and research workflow; I expect these automations to go even deeper in the next few months. This is going to be fun.
