# Workflow 1.4.4 Brings More Image Automation, HTML to Markdown Conversion

_Captured: 2016-03-08 at 00:47 from [www.macstories.net](https://www.macstories.net/ios/workflow-1-4-4-brings-more-image-automation-html-to-markdown-conversion/)_

![](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/2016-03-06-163356.jpeg)

As much as I like to use [Workflow](https://workflow.is/) for every task I don't want to perform manually, until last week there were still some things I couldn't automate with the app. Those tasks were utterly specific: converting HTML and rich text back to Markdown (with my beloved [html2text](http://www.aaronsw.com/2002/html2text/) in Python), or assembling iOS screenshots with pretty device frames (with [LongScreen](https://geo.itunes.apple.com/us/app/longscreen/id913571256?mt=8&uo=4&at=10l6nh&ct=ms_inline)). With the release of [Workflow 1.4.4 today](https://geo.itunes.apple.com/us/app/workflow-powerful-automation/id915249334?mt=8&uo=4&at=10l6nh&ct=ms_inline), I can finally integrate these two key tasks into Workflow's automation, and I'm in love with the results.

## Overlaying Images

Since Workflow added the ability to combine images from the Photos app with its action extension, I've stopped using scripts I had in Pythonista to create images for MacStories reviews. While Workflow was a great way to stitch multiple images together, however, it couldn't [overlay an image on top of another](https://www.macstories.net/linked/putting-ios-screenshots-in-device-frames-with-workflow/) - something that could be easily done in Python by pasting an image on top of a background. This is exactly what Workflow brings with today's update.

The new 'Overlay Image' action allows you to overlay an image (defined in the Image field of the action) on top of another image passed as input. The action offers various customizable parameters: you can tweak the size of the image you're overlaying, set rotation and opacity, and even adjust the position where the image will be overlaid choosing from five presets or by entering any coordinate you need through variables. If you don't want to set parameters beforehand, there's also an option to show an image editor and overlay the image manually. The combined image will be the output, so you can pass it to an action and save it to your library.

This is precisely what I needed to turn one of the few remaining tasks I couldn't automate into a flexible and powerful workflow. For a long time, I've wanted to automate the creation of composite images made of iOS screenshots and iOS device frames [provided by Apple](https://developer.apple.com/app-store/marketing/guidelines/). With Workflow's new overlay action and its Photos integration, I can now put screenshots for the iPhone 6s Plus (both portrait and landscape) and the iPad Pro (only landscape; I don't need portrait support) into device images without doing anything manually except picking them.

![These screenshots were overlaid and combined with my workflow.](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/2016-03-06-163840.jpeg)

> _These screenshots were overlaid and combined with my workflow._

To play around with this:

  * Download the workflow [here](https://workflow.is/workflows/221e34d7c6904bdbb0ae8bec379d0a78);
  * [Grab my edited templates and assets](https://bbf324e0f021017963b1-3b1073ac6adc6b2fffddbe35a528b598.ssl.cf1.rackcdn.com/Overlay%2520Assets.zip) for all three orientations.

Once you've downloaded the .zip file, save all images into Workflow's iCloud Drive folder and double check their filenames - they should match the ones used in the workflow.

Here's what the workflow does: given iPhone 6s Plus or iPad Pro screenshots in the supported orientations, the workflow creates framed screenshots and combines them in one final image. The best part: you can mix and match device types (such as two iPhone screenshots and one iPad Pro screenshot) and the result will be a composite image featuring all the correct device frames. At the end, the result is saved to your photo library.

The workflow is built to accept screenshots shared from the share sheet in the Photos app. Whether one or multiple screenshots are detected, the workflow then checks for each image's width and uses the Overlay Image action to put them into iPhone 6s Plus or iPad Pro frames. As I said above, I only needed to support landscape mode on the iPad Pro, but adding portrait support is easy enough - just create another If block to check for the width of an iPad Pro screenshot in portrait mode.

![](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/2016-03-06-164114.jpeg)

After picking screenshots, the image manipulation process is entirely automated. The only option you'll have to confirm at the end is whether you want to properly scale iPhone and iPad device frames. If you're dealing with different devices in the same image, choose Scale iPhone and iPad from the menu and Workflow will take care of resizing the 6s Plus template and aligning both devices toward the bottom edge. For images of the same device type (or if you don't care about scaling), choose the Finish option and the workflow will combine devices without scaling or aligning them.[1](https://www.macstories.net/ios/workflow-1-4-4-brings-more-image-automation-html-to-markdown-conversion/)

![Also automated with my workflow.](https://2672686a4cf38e8c2458-2712e00ea34e3076747650c92426bbb5.ssl.cf1.rackcdn.com/2016-03-06-164507.jpeg)

> _Also automated with my workflow._

Behind the scenes, this is possibly one of the most complex workflows I've built; in practice, though, I only have to choose some screenshots and see if I want to scale iPhone images if they're next to an iPad. Thanks to the Overlay Image action, this workflow is going to save me a lot of time I would have spent assembling hero images manually, and it's one more trick in my arsenal of screenshot workflows for image automation.

## Converting HTML to Markdown

The other task that I used to run in Pythonista with a script was converting rich text and HTML back to Markdown. I did this to ensure that webpages I linked to on MacStories (where I publish text as Markdown) would keep the formatting of the original source, which is lost if you copy text manually (or with most share extensions) from Safari webpages.

Workflow 1.4.4 includes a simple action called Make Markdown from Rich Text that is comparable to html2text. You can pass webpage selections to the action, and you'll end up with a Markdown version of the same text to use somewhere else. For anyone who uses Workflow to complement their iOS blogging setups, this is a must-have.

I put together a sample workflow to demonstrate how easy it is to generate Markdown from selections in Safari. Select some content on a webpage - you can select both images _and_ media - bring up the share sheet, and run the workflow. After a second, you'll have a Markdown version of the content you selected on your system clipboard, ready to be pasted in another app. Under the hood, Workflow uses the also-new 'Get Details of Safari Web Page' action[2](https://www.macstories.net/ios/workflow-1-4-4-brings-more-image-automation-html-to-markdown-conversion/) to extract the page selection parameter from the input variable, feeding it to Make Markdown from Rich Text.

You can download the workflow [here](https://workflow.is/workflows/e5b73c937bf64ce9a4f394f2ccc1c3e9).

## Workflow 1.4.4

There are [more actions worth noting](http://workflow.is/whatsnew) in this update. You can now unzip files in Workflow without having to use a separate file manager; you can use 'Get Device Details' to easily see whether a workflow is running on an iPhone or iPad (and take different routes if so); you can even add frames to GIFs and post GIFs to Tumblr.

On each release, [Workflow](https://workflow.is/) adds features that allow me to work faster and automate as much as I can so I can focus on more important and fun aspects of my job. Workflow 1.4.4 has some great improvements for image processing and Markdown, and it's [available now on the App Store](https://geo.itunes.apple.com/us/app/workflow-powerful-automation/id915249334?mt=8&uo=4&at=10l6nh&ct=ms_inline).

  1. For those curious: because Workflow doesn't have an option to combine images by placing the smallest one toward the bottom, I worked around this by creating taller white background images where the iPhone device is overlaid and resized, so it'll be properly scaled next to an iPad and aligned at the bottom (otherwise, it'd float toward the top of the iPad's display). [↩](https://www.macstories.net/ios/workflow-1-4-4-brings-more-image-automation-html-to-markdown-conversion/)
  2. Which, by the way, is a nice way to get URLs or titles from webpages more quickly than before. [↩](https://www.macstories.net/ios/workflow-1-4-4-brings-more-image-automation-html-to-markdown-conversion/)

### Want More from MacStories?

Club MacStories offers exclusive access to **extra MacStories content**, delivered every week.

Club MacStories will help you discover the best apps for your devices and get the most out of your iPhone, iPad, and Mac. Plus, it's made in Italy.

Starting at $5/month, with an annual option available. [Join the Club](https://club.macstories.net/?icn=club&ici=after-post-inline).

  * **MacStories Weekly** newsletter, delivered every week on Friday with app collections, tips, iOS workflows, and more;
  * **Monthly Log** newsletter, delivered once every month with behind-the-scenes stories, app notes, personal journals, and more;
  * **Access** to occasional giveaways, discounts, and free downloads.
