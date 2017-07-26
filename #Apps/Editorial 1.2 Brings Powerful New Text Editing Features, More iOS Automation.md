# Editorial 1.2 Brings Powerful New Text Editing Features, More iOS Automation

_Captured: 2015-06-15 at 19:05 from [www.macstories.net](http://www.macstories.net/reviews/editorial-1-2-brings-powerful-new-text-editing-features-more-ios-automation/)_

![](http://48ce6c28e7bf5f42a1b7-2712e00ea34e3076747650c92426bbb5.r89.cf1.rackcdn.com/2015-06-15-130049.jpeg)

If I had to pick one iOS app I couldn't live without, that would be [Editorial](https://itunes.apple.com/us/app/editorial/id673907758?mt=8&uo=4&at=10l6nh&ct=ms_inline).

Developed by Berlin-based Ole Zorn, [Editorial](http://omz-software.com/editorial/) was the app that [reinvented text automation in 2013](http://www.macstories.net/stories/editorial-for-ipad-review/) and that pushed me to start working exclusively from my iPad. Editorial is a powerful Markdown text editor that combines visual Automator-like actions with a web browser, text snippets, Python scripts, and URL schemes to supercharge text editing on iOS with the power of automation. I spend most of my days writing and researching in Editorial, and my workflow depends on this app.

Editorial also has a slow release cycle. Zorn likes to take his time with updates that contain hundreds of changes: Editorial 1.1, [released in May 2014](http://www.macstories.net/reviews/editorial-1-1/), brought an iPhone version and custom interfaces, making Editorial feel like an entirely new app. The same is happening today with Editorial 1.2, which adds support for the latest iPhones, iOS 8 integration, custom templates, browser tabs, folding, and _much more_.

Editorial 1.2 with iOS 8 support is launching right after [Apple's announcement of iOS 9](http://www.macstories.net/stories/ios-9-our-complete-overview/), but the wait has been worth it. The new version builds upon the excellent foundation of Editorial 1.1, and the enhancements it brings vastly improve the app for users who rely on its automation features and Python interpreter.

Rather than covering every single change, I'll focus on the 10 new features that have most impacted the way I get work done with Editorial on a daily basis.

## iPhone 6

The most apparent change in Editorial 1.2 is support for the latest iPhones and iOS 8. Editorial 1.1 worked okay on the iPhone 6 and iOS 8, but there were a few bugs and lack of support for the bigger screens that made the app barely usable for many. Thankfully, all this has been rectified with version 1.2.

![](http://48ce6c28e7bf5f42a1b7-2712e00ea34e3076747650c92426bbb5.r89.cf1.rackcdn.com/2015-06-15-130213.jpeg)

On iPhone 6, Editorial 1.2 shows a revamped title bar with a new quick settings button. The latter opens a new panel where you can tweak some of Editorial's most used settings such as dark theme, syntax mode (with HTML, CSS, Fountain, and JavaScript now fully supported), and editor. There's a new option to control text size dubbed 'text zoom', which lets you increase/decrease text size with simple taps and in real time. You can also activate an option to rearrange paragraphs with touch, which I'll cover in a bit.

![](http://48ce6c28e7bf5f42a1b7-2712e00ea34e3076747650c92426bbb5.r89.cf1.rackcdn.com/2015-06-15-050454.jpeg)

A lot has been refined from a visual standpoint in this release, including some controls for workflow actions and the position of buttons in the built-in browser. I especially like the new Editorial on the 6 Plus, as the device's special landscape keyboard combined with the app's extra keyboard row gives me a lot of options for editing text.

## Templates and Previews

With this release, Ole Zorn strived to refine Editorial's feature set as a text editor, adding features and new customizations to make Editorial the best option for Markdown writers on iOS. A common requirement among people who write in plain text and automate Markdown on a daily basis is custom templates, and Editorial 1.2 delivers on this front. You can create multiple custom templates for new documents and custom previews for finished files. Both changes have significantly improved the way I write in Editorial, in small and big ways.

Editorial ships with three basic templates for its supported document formats - Markdown, plain text, and TaskPaper. The new template system in Editorial 1.2 is based on workflows: effectively, document templates are workflows that let you customize the way a file is created at the end with a Create Document action. The entire flow of actions and blocks before file creation is completely under your control.

![](http://48ce6c28e7bf5f42a1b7-2712e00ea34e3076747650c92426bbb5.r89.cf1.rackcdn.com/2015-06-15-125326.jpeg)

You can come up with your own way to prepare a template for a new file. You can use all the variables, scripts, presets, and actions that you normally use in Editorial workflows - just remember that everything will have to lead to a Create Document action at the end. This makes Editorial the most flexible solution for personalized document templates on iOS: no other text editor brings this level of versatility to templates, and, in this case, imagination is your only limit. You can come up with [MultiMarkdown](http://fletcherpenney.net/multimarkdown/) templates that set up document tags and variables beforehand; you can display dialogs and conditional blocks before creating a file; you can query web services and use the app's browser.

Personally, I just replaced the app's default template with one that creates a new file with a timestamp in the filename instead of 'Untitled'. While custom document generation was possible with regular workflows before, the new system brings a welcome integration with the app's document creation flow: once you've assigned a default template (Settings > File Settings > Select Default Template), tapping the '+' button to create a new file will automatically create a new file off your chosen template, which is better than having to run a workflow to create a new file.[1](http://www.macstories.net/reviews/editorial-1-2-brings-powerful-new-text-editing-features-more-ios-automation/)

Custom previews are based on a similar idea, but for files you're working on instead of new ones. If you don't want to preview documents with the default HTML preview of Editorial, you can tap on the Preview title in the preview section, select Edit Preview Themes, and you'll be shown a list of HTML files that define the app's preview screen with different styles and placeholders. Editorial 1.2 has a variety of preview themes, which should suffice if you're looking for alternative ways to view your finished files.

![MacStories preview theme in Editorial 1.2.](http://48ce6c28e7bf5f42a1b7-2712e00ea34e3076747650c92426bbb5.r89.cf1.rackcdn.com/2015-06-15-125505.jpeg)

> _MacStories preview theme in Editorial 1.2._

However, this being Editorial, you can create your own previews. Tap one of the preview files, and you'll see that Editorial now has full support for HTML and CSS syntax highlighting. You can take a look at the way previews work in the app to start making your own: perhaps you want to style the preview after your website's look or maybe you need to inject other variables and placeholders in the final preview.

Thanks to some help from [Brett Terpstra](http://brettterpstra.com/), I created a custom Editorial preview based on how articles will look on MacStories when published, which greatly helps in understanding the visual flow of an article before it goes live.

## Browser Tabs

This is another change that has considerably sped up the way I work in Editorial: the app's browser can now have multiple tabs open at the same time.

The entire engine of the accessory panel view has been rewritten to support tabs for the web, documentation, and Python console. You can choose to keep multiple websites open as I normally do, or you can, say, keep two documentation tabs and the console open if you're building a complex workflow and need to look up help quickly.

![](http://48ce6c28e7bf5f42a1b7-2712e00ea34e3076747650c92426bbb5.r89.cf1.rackcdn.com/2015-06-15-125603.jpeg)

I've always wished for Editorial to be able to handle multiple tabs in the built-in browser: having tabs for different websites is essential to research, and I'm happy that the app is capable of keeping a decent amount of tabs stored in memory before having to reload them. You can rearrange tabs on the iPad with drag & drop, and you get a nice grid view with visual previews on the iPhone.

The Open URL workflow action has also been updated to take advantage of tabs. When you open a URL programmatically, you can now decide to open it in the last tab used, in a new tab, or in a tab with a specific ID.[2](http://www.macstories.net/reviews/editorial-1-2-brings-powerful-new-text-editing-features-more-ios-automation/)

My only quibble is that there's no way to pin tabs to save horizontal space on iPad and that website icons aren't shown next to the tab title, which can make differentiating between multiple tabs at a glance a bit tricky. Overall, though, I'm satisfied with the addition of tabs and they've turned out to be good timesavers whenever I have to look up sources for an article or link to two different blog posts.

## Improved Editor Search and Highlight All

Editorial 1.2 has an improved in-editor search feature with new options for replacing and highlighting matches, plus a new Highlight All menu item that I've been using to edit my articles more efficiently.

The improved document search has options to replace occurrences (no more custom workflows for that) and it can look for matches that contain a keyword, start with it, or that are the full word. When editing long documents that have recurring mistakes or other typos, this is quite convenient.

![](http://48ce6c28e7bf5f42a1b7-2712e00ea34e3076747650c92426bbb5.r89.cf1.rackcdn.com/2015-06-15-125929.jpeg)

You can also highlight any word or sentence in the editor and tap Highlight All in the copy & paste menu to highlight all instances of that string in the document. You can then Command-G your way through highlights with an external keyboard (like on a Mac) and select a match again to show Clear Highlights and dismiss the search. Thanks to the high contrast between the app's light background and yellow highlights, this makes it an ideal option to highlight words I use too often, see repetitions at a glance, and fix them.[3](http://www.macstories.net/reviews/editorial-1-2-brings-powerful-new-text-editing-features-more-ios-automation/)

## Folding and Arranging Paragraphs

If you use Editorial to write longform documents, you'll be happy about the addition of folding and rearranging paragaphs. The latter is inspired by the app's existing TaskPaper mode and reminiscent of other apps like [Phraseology](http://www.macstories.net/reviews/efficient-writing-on-ios-with-phraseology-2-0/): once activated, each paragraph will get a light gray handle on its right side, and you can grab that to rearrange the paragraph vertically and move it above or below other paragraphs.

I've been using manual paragraph rearrangement in combination with my new Instapaper-Editorial workflow to annotate articles in Instapaper and turn my notes into blog posts. With the addition of Notes and Markdown export in Instapaper, I've been able to start using Instapaper as a blogging tool, as it lets me read articles in a comfortable environment with annotations that persist across platforms even after I archive articles. As [I wrote two weeks ago](http://www.macstories.net/ios/instapaper-launches-notes-bringing-annotations-to-articles/):

> Thanks to Notes, I've started using Instapaper as a blogging tool. When I'm reading and I find something I want to comment on, I highlight noteworthy passages and add my notes to start composing a linked post for MacStories. This enables me to stay inside Instapaper, avoid external distractions, and retain the context of the article I'm reading. When I've reached the end of the article, I can then tap the new Share All Notes button, pick Markdown (plain text and HTML are also available), and export all my highlights and notes from an article to an iOS extension as text. Using [Workflow](https://itunes.apple.com/us/app/workflow-powerful-automation/id915249334?mt=8&uo=4&at=10l6nh&ct=ms_inline) and [Editorial](https://itunes.apple.com/us/app/editorial/id673907758?mt=8&uo=4&at=10l6nh&ct=ms_inline), I can go from Instapaper to a linked post ready to be published on MacStories in two taps. I find this incredibly empowering and practical. Most of [the linked posts](http://www.macstories.net/category/linked/) I've published for the past month generated from Instapaper Notes. 

When I add a note in Instapaper, I usually need to move the first line of my note on top of a quote from the original article - notes in Instapaper always follow quotes and sometimes that order isn't okay for MacStories. Once I've ended up with Markdown text from Instapaper into Editorial, I can simply grab the handle on the right side of a paragraph and move it up with no copy & paste required.

I don't know if these could be useful as they're designed for the linked post format on MacStories, but you can find the Workflow and Editorial workflows I use for this task [here](https://workflow.is/workflows/2dc099451f064056bf9e492b5a518d8b) and [here](http://www.editorial-workflows.com/workflow/4962768541188096/V59ideK9eVY).

![Folded sections in Editorial 1.2.](http://48ce6c28e7bf5f42a1b7-2712e00ea34e3076747650c92426bbb5.r89.cf1.rackcdn.com/2015-06-15-125701.jpeg)

> _Folded sections in Editorial 1.2._

Folding is a solid addition for those who write long essays and documents that span dozens of sections. Like some of the most popular [Sublime Text](http://www.sublimetext.com/) plugins, you can now fold an entire section (contained inside a Markdown header) via a downfard-facing triangle on its left side. Tap it, the section will be folded, and you'll see a word count for the text inside that section next to it. Folded sections can be rearranged like paragraphs, and while I haven't found myself using this regularly because I like to always see all my text in front of me, I believe it is a great enhancement for writers who are used to this type of control on the desktop.

## iOS 8 Share Sheet as Workflow Action

Need to share some text or a URL with other apps? Editorial 1.2 enables you to use the system share sheet as a workflow action so you can bring up your action and share extensions at any time.

Due to the way extensions are activated on iOS 8, you can choose to share text or a URL with the new Share action - the extensions that are displayed in the share sheet will change depending on the input type.

What's nice about this is that you're free to display the iOS share sheet in workflows without tapping a share icon first. In older versions of the app, whenever I wanted to tweet a price drop grabbed with one of my workflows with [@MacStoriesDeals](https://mobile.twitter.com/macstoriesdeals), I was forced to open a URL scheme for Twitter or Tweetbot and then manually return to Editorial. Now, I can just use the Share action to tweet it with @MacStoriesDeals without leaving the app.

## More Share Sheets

Editorial 1.2 also has share sheets for the document preview and the browser.

When you're browsing webpages in the app, you can hit the share button to share the URL with any installed action or share extension. This enables some useful workflows such as the ability to save links to Drafts or use Workflow inside Editorial.

![Share Sheets in Editorial 1.2.](http://48ce6c28e7bf5f42a1b7-2712e00ea34e3076747650c92426bbb5.r89.cf1.rackcdn.com/2015-06-15-130515.jpeg)

> _Share Sheets in Editorial 1.2._

Sharing HTML from the preview page has also been rewritten to take advantage of extensions. In Editorial 1.2, if you want to grab a document's HTML code after you're done editing, you can open the preview and hit share. You'll be shown extensions capable of accepting HTML text input and a Copy button so you can paste the code elsewhere. If you send the output to apps that support rich text like Mail, HTML will be turned into rich text from the extension.

## 1Password Button

With proper browser tabs come new responsibilities, and Editorial can now help you fill logins in its browser with the 1Password extension. A new 1Password icon in the browser toolbar lets you log into websites without leaving Editorial, which makes the app's browser an even more compelling option for those who like to always research and look up information without using Safari.

Speaking of the browser, Zorn has added controls to erase cache and cookies from the app without having to reinstall it. I had run into this type of issue a bunch of times in the past, and I'm glad I have an easier option now.

## New Twitter module

Among Editorial's new Python modules, `twitter` has been the most interesting one for me. With a bit of Python knowledge, Editorial can expose Twitter accounts configured in the iOS Settings and allow you to get tweets, search, and perform requests on the [Twitter API](https://dev.twitter.com/rest/public). The implementation is straightforward and I was able to have a basic script running within minutes.

I embed tweets on MacStories articles regularly, and I thought it'd be useful to automate the process and speed it up by not having to grab the embed code manually on the web. As it turns out, the Twitter API supports returning embed codes and Editorial's simplified Twitter integration makes it easy to authenticate with an account to perform a request.

I put together an Embed workflow that returns embed codes for YouTube, Vimeo, Instagram, and IFTTT links. Twitter queries the API through the `twitter` module, while other services return codes thanks to [oEmbed](http://oembed.com/). Whenever I need to generate an embed code for MacStories, I copy the original link (like a tweet or a video), run the workflow, and I have the code ready to be embedded in an article in two seconds. This is a nice demo of Editorial's new Twitter integration, and I use the new module almost daily.[4](http://www.macstories.net/reviews/editorial-1-2-brings-powerful-new-text-editing-features-more-ios-automation/)

You can download the workflow [here](http://www.editorial-workflows.com/workflow/5270448723984384/vjmhPRrJ0lE).

## editorial-http URL Scheme and Bookmarklet

Editorial 1.2 brings an easier way to open links from other apps into its built-in web browser. Using the new `editorial-http` and `editorial-https` URL schemes, you can now create JavaScript bookmarklets that open any given URL directly into the Editorial browser without having to run a workflow.

In my case, I always send webpages from Safari to Editorial, so I simplified my existing bookmarklet to open a URL directly without passing it to a workflow. Here's the updated bookmarklet:

`javascript:window.location='editorial-'+document.location.href;`

As you can see, you just need to prepend `editorial-` to a standard link to send it to the app's browser. This is a more convenient solution than older versions of the app, and I'm glad I can get rid of a workflow I just used to open links sent from Safari.

## A Text Editor

With the new features in version 1.2, [Editorial](http://omz-software.com/editorial/) is a better text editor.

As far as general automation on iOS goes, Zorn finds himself in a tough spot now: more advanced users will always seek out the power of [Pythonista](https://itunes.apple.com/us/app/pythonista/id528579881?mt=8&uo=4&at=10l6nh&ct=ms_inline) (also in need of an update), while those looking for an easier way to build workflows, integrate them with extensions, and share them with others have probably switched to the excellent [Workflow](https://itunes.apple.com/us/app/workflow-powerful-automation/id915249334?mt=8&uo=4&at=10l6nh&ct=ms_inline). The 2015 iOS automation landscape is a lot more different than 2013: Editorial isn't the only player in town, and Workflow is showing [how to automate anything on iOS](http://www.macstories.net/reviews/workflow-1-1-deeper-ios-automation/) - not just text - with easy to use actions and fantastic integrations with the system.

In many ways, Workflow has "won" the automation game on iOS, and I bet that Zorn knows this. It'd be difficult for Editorial to compete with the scope and flexibility of Workflow at this point. With this mind, today's release of Editorial 1.2 makes a lot of sense. Zorn is doubling down on what makes Editorial unique and better than anything else on iOS: Markdown text editing with automation features.

This is why I'm not surprised about the lack of an action extension to run Editorial workflows outside of the app. Editorial 1.2 is focused on enhancing what makes working with text inside Editorial a great experience, and, in this regard, every change in this release is instrumental to locking users like me into the app.

Today's update takes Editorial's writing environment one step further. There are dozens of other features that I haven't covered here (TaskPaper improvements, [CriticMarkup](http://criticmarkup.com/) and [Fountain](http://fountain.io/) support, new `dialogs` and `reminders` modules in Python, a Generate PDF action, etc.), and Zorn has been extremely thoughtful in considering other use cases for Markdown and automation on iOS (such as screenwriting and document edits).

Features like browser tabs, folding, custom templates, preview themes, and better search make Editorial the undisputed king of Markdown text editing on iOS - an area where no other app can compete at this point. I would like to see a faster release cycle from Zorn - hopefully adopting iOS 9 multitasking and search won't take long - but that doesn't change the fact that Editorial continues to be the most powerful app for writing and automating Markdown on iOS - for [all the reasons I covered in the past](http://www.macstories.net/stories/editorial-for-ipad-review/).

Editorial reinvented how I work on iOS, and I wouldn't be able to use anything else at this point.

Editorial 1.2 is [available on the App Store](https://itunes.apple.com/us/app/editorial/id673907758?mt=8&uo=4&at=10l6nh&ct=ms_inline).

  1. I haven't used tab IDs much in my tests, but they allow you to open links in specific tabs that are always open in Editorial, and I assume they could be useful to users who want certain types of links to open in certain tabs. 
  2. Another nice addition: the Search in Editor workflow action has been renamed to Highlight Occurrences and it can now highlight matches (including those from a regular expression) without showing the document search bar. 
