# Blogging on an iPad with Workflow, Ulysses, and Drafts

_Captured: 2016-03-13 at 20:31 from [incompetentwriter.com](http://incompetentwriter.com/2016/01/17/blogging-on-an-ipad-with-workflow-ulysses-and-drafts/)_

![img_3351-1](https://danielwa11ace.files.wordpress.com/2016/01/img_3351-1.jpeg?w=1008&h=756)

Some readers seemed curious about my decision to do all of my writing and blogging on an iPad. So I thought I would describe a few of the more advanced things I do on my iPad Pro: in particular, how I use it for writing and publishing blog posts.

To give the short version: this mostly involves combining a writing app like [Ulysses](http://www.ulyssesapp.com/) or [Drafts](http://agiletortoise.com/drafts/) with the remarkable iOS app [Workflow](https://workflow.is). Workflow not only allows an iPhone or iPad user to automate many, many repetitive tasks, it can hook itself up to your WordPress blog, and send text, photos, and other media from your device to your WordPress site. You can simply add these items to your media library, or create entire posts, as I have done for this post.

Now, there are far more expert writers on this subject. I'm particularly indebted to Frederico Viticci's [guides to iOS 9](https://www.macstories.net/stories/ios-9-review/) and the [Workflow app](https://www.macstories.net/ios/publishing-articles-to-wordpress-with-workflow-on-ios/). If you like what I have written below, make sure to visit his site.

You may be wondering -- why bother creating your own program-combination for blogging? Why not write directly into the WordPress website, or use a pre-made blogging app? Well, on the one hand, writing in a browser usually feels too unreliable, with too high a risk of losing words. And on the other, I think it's fair to say that the state of blogging apps on iOS has long been disappointing. I've tried a lot of the different options, and I haven't been happy with any of them. Until recently, I did most of my blogging on a desktop computer, because it was simply too much work to blog on the iPad.

This was particularly sad because the iPad has a lot of great software for _writing_ -- there is the ingenious [Drafts](http://agiletortoise.com/drafts/), the aloof IA Writer, the super-geek-powered Editorial, the restrained Byword, and the master of long-form prose, [Ulysses](http://www.ulyssesapp.com/). There are iOS text editors for every writer's purpose.

(And, as I said before, I feel that iOS is actually a _superior_ writing environment to a desktop Mac or Windows: iOS naturally provides the simplicity and focus that good writing thrives on, and which desktop operating systems, with their layers of tiered, overlapping windows, tend to inhibit.)

But the two best options that I know of for blogging on the iPad -- the official WordPress app and the independent app Blogsy -- feel less than ideal. WordPress's own app occasionally formats things in odd ways, and feels unsuitable for long bouts of writing; Blogsy deals with images in an awkward, buggy manner.

And, until recently, there was an additional problem, one that arose from the design of iOS itself.

With any post that included a lot of links, I would have to find and insert a whole series of web addresses. I don't mean, here, the effort of turning web addresses into blog post links: I mean the simple effort of going looking for the addresses and collecting them. On a desktop, this was as easy as clicking in one window then another. But old-fashioned iOS only allowed one app on the screen at a time. So, to collect and insert a bunch of links meant moving from my writing app to the Safari browser, searching for the right address, copying it, and pasting it back into the text editor as HTML or Markdown code. The iOS clipboard only accepted one item at a time, so the app-switching process had to be repeated for each address: if a post needed more than a few links, this quickly became annoying and slow.

**Solution Number One: Collecting Links All In One Go**

The [Workflow](https://workflow.is) app can do a whole lot of things.

You either create your own workflows in the app, or download other people's workflows for your own use. Then, once a particular workflow is set up, you can activate that workflow while you're using other apps -- as an extension. That's how I actually I use workflows, most of the time, as an extension, activated from the "sharing" or "share sheet" boxes that almost all modern iOS apps now have.

Necessary brief digression number 1: once you've downloaded the Workflow app, the option to add its "action" to your system share sheet becomes available. You have to activate it in the share sheet in order to see it, and open the list of possible action extensions hiding in the dot-dot-dot button:

![IMG_0035](https://danielwa11ace.files.wordpress.com/2016/01/extension-2.jpeg?w=801&h=600)

![IMG_0036](https://danielwa11ace.files.wordpress.com/2016/01/swipe-to-turn-it-on-2.jpeg?w=801&h=600)

Necessary brief digression number 2: Designing a workflow _doesn't require any coding ability_: the vast majority of automation actions can be simply dragged and dropped, step by step, from the list of possible actions, into the workflow you're designing.

However, the one complication, which may make workflows seem more confusing to read than they really are, and which I suspect is completely obvious to people who know how to code, but which took me a while to figure out, is the role of "variables." Variables allow an individual workflow to keep track of more than one thing.

As you'll see from my screenshots, the workflow app works in a linear way. It carries out one action, then the next action, and then the next. If you want a workflow that keeps track of multiple "parts" of the thing you're working on, you will need to use the "Set Variable" action a lot.

Set Variable simply means "name this thing and remember it for the rest of the workflow."

Here, for instance, is a [very simple workflow](https://workflow.is/workflows/e27c602ce037485ba01ab588386c83fa) I created to speed up my "link gathering" process for a blog post. It's basically an "append to clipboard" action. When I want to collect the web addresses for a bunch of links for a post, this workflow allows me to copy them one by one to my clipboard, building up a list which I can then paste into the post.

Rather than searching, then pasting into the post, then searching again, I can do all the searching at once. The workflow takes the address I'm looking at in my browser, sets it as a variable, pulls up the current clipboard, sets that as a variable, combines them into a vertical list, and then copies that list back to the clipboard. When I've got all the links I need, I paste them into my post, and start coding them up.

![IMG_0028](https://danielwa11ace.files.wordpress.com/2016/01/clipboard-workflow.jpeg?w=801)

I activate this workflow, while I'm browsing the web, from the Safari action extension button.

![IMG_0030](https://danielwa11ace.files.wordpress.com/2016/01/extension-workflow-safari-2.jpeg?w=801)

This button pulls up my list of workflows, and I pick the one I want:

![IMG_0032](https://danielwa11ace.files.wordpress.com/2016/01/choose-your-workflow.jpeg?w=801)

**Solution Number Two: Posting a Simple Blog Post from Ulysses**

_Ulysses_ is probably the best app for long-form writing on the iPad. It's the equal of Scrivener, and a lot more streamlined.

However, it doesn't yet have the power to publish directly to WordPress. Workflow, however, does. And I can activate a workflow from Ulysses's export options.

When I write something in Ulysses, I can publish it to this or another WordPress blog by activating a workflow from the action extension / sharing sheet. Here's one very simple workflow: [Publish Complete Post](https://workflow.is/workflows/3fe3c16379c643faba02d88907e5ee76). It simply takes the text I've written, prompts me for a title, automatically corrects that title to have Title Case, gives me a preview so I can make sure the text has been sucked into the app correctly, and then posts it to my blog. Finally, it opens the WordPress app, so I can, if I want, check the post out before I publish it.

![](https://danielwa11ace.files.wordpress.com/2016/01/img_0037.png?w=1008)

If you still want a simple post, but with a single image at the top, like a header image, I offer this workflow: [Quick Post To WordPress With Photo](https://workflow.is/workflows/b3d1b2f1ee284e3da8bf63f00fde1d12). It takes the text you've written in Ulysses, asks you to pick a photo from your iOS photos, and puts that at the top of the post.

(There are also options for uploading a photo as the post's featured image, but because I don't like how my WordPress theme treats featured images, I don't use this option.)

**Solution Number Three: Creating a Complex Blog Post from Drafts**

Unfortunately, it's not yet possible to insert multiple photos from one's iOS photo collection into different parts of a post. So, if you want to create a post with lots of images, like this one, you'll need another solution. What I've done is create an image uploading workflow, which lets me select photos from my Camera Roll, upload them to WordPress, and then gives me the code for each image.

Now, this next bit is kind of magical -- and is probably too complex for me to explain in full here. It requires me to write the blog post in another program, the excellent writing app Drafts. Drafts is, no question, one of the highlights of iOS software, and well worth exploring. Drafts offers a clean, well-laid-out scratchpad for writing, and then a huge series of options for sharing, exporting, and saving the text you produce in it. Drafts, in many ways, is the best app for writing blog posts: while it lacks Ulysses's organisational abilities, it has lots of options for adding code to prose. For my novel, I only use Ulysses, but I find Drafts a lot better for working with Markdown and HTML.

Drafts also allows you to tell Workflow the "ID" of the current file you're writing. So I've created an action in Drafts that 1. Copies to clipboard the ID of the open file and then 2. Runs a workflow that selects, renames, resizes, and uploads a photo to WordPress, then gets the address of that image, then arranges the HTML code, and then automatically inserts that HTML code back into the file I was working on. I don't even need to hit "paste" -- the code simply appears on the page.

This is a pretty great solution. I can be happily typing away, realise I need an image for the post, and with the click of button, in a matter of seconds the code for that image has appeared in the post I'm writing. Plus the image is saved in my WordPress media library, if I ever want to use it again.

You can get the Workflow [here](https://workflow.is/workflows/dc29b1f124c44672bb26bb741d02892a), and the Drafts Action [here](https://drafts4-actions.agiletortoise.com/a/1eQ).

Now -- I am no expert at any of this stuff. If you have seen a mistake in any of these workflows, or a redundant step, please let me know.
