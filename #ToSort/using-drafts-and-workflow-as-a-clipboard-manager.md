# Using Drafts and Workflow as a clipboard manager.

_Captured: 2017-01-06 at 20:18 from [sethclifford.me](http://sethclifford.me/2017/01/using-drafts-and-workflow-as-a-clipboard-manager/)_

As I continue to play this little game I've created for myself in which I try to use and install fewer apps while [discovering](http://sethclifford.me/2015/09/using-slack-as-a-personal-information-center/) [new ways](http://sethclifford.me/2016/07/an-update-on-how-im-using-my-private-slack-team/) to use [the ones I love](http://sethclifford.me/2016/12/using-drafts-reminders-and-slackbot-as-a-task-management-system/), my latest run is based on replacing a dedicated clipboard manager app. While I do really like [Copied](https://geo.itunes.apple.com/us/app/copied-copy-paste-everywhere/id1015767349?mt=8&uo=4&at=10lSkX&ct=gr) and other apps like it, the truth of the matter is that I don't need an app solely devoted to holding and managing snippets of information like this. I do _occasionally_ have this need, and so it's something I like the idea of having, but it's almost only for text/links, which I can do in a variety of ways.

The trick is storing the snippets, but also making them accessible and easily retrieved, and because of the way iOS works, we're limited in a few ways. Any app that does this can only run in the background for so long, and even if you're using a widget for this, there's only so much room in the UI to account for the things you can do without launching a full app UI. But since my specific needs are limited, I've experimented with pairing [Drafts](https://geo.itunes.apple.com/us/app/drafts-quickly-capture-notes/id905337691?mt=8&uo=4&at=10lSkX&ct=gr) and [Workflow](https://geo.itunes.apple.com/us/app/workflow-powerful-automation/id915249334?mt=8&uo=4&at=10lSkX&ct=gr) together: one as the snippet storage and one for the quick access to my most-used bits of text.

A quick note: I think it goes without saying that if you use an app like Copied for images and other rich media, this wouldn't really work for you. This is really centered on text, and the impetus for this was restoring my iPhone recently and for the millionth time not having my iCloud text expansions appear. Given that my needs are fairly limited anyway, I'm giving up on that broken-ass bullshit and building a replacement with the tools that I know will work. I still don't understand how this far along and with all it can do having iCloud remember a three-letter shortcut for my email address and making it available on new devices consistently is such a fucking Herculean task.

Anyway.

### Drafts as the library

I used to use [TextExpander](https://geo.itunes.apple.com/us/app/textexpander-+-keyboard/id1075927186?mt=8&uo=4&at=10lSkX&ct=gr). I also used to have a million snippets I couldn't remember. Then I decided to simplify and keep only the stuff I could. Once I realized this was a relatively small number of items, I decided to use the native iOS keyboard expansion for shortcuts. As you can see from my above comment, when it works, this is more than adequate for my needs. However, all too often I restore a device or set one up and I never get the shortcuts. Or they show up a month later.

But Drafts is always there. Building on my thinking for how I was [using filters to move tasks out of my inbox](http://sethclifford.me/2016/12/using-drafts-reminders-and-slackbot-as-a-task-management-system/), I created a filter to separate these text snippets out too. I liked the way Copied allows you to have a title for the snippet, so I created that same structure in Drafts. I just added a tilde to the end of the title line.

![](http://media.sethclifford.me/blog/drafts_snippet.png)

Along with that, I needed an action that would copy the body text but ignore the title line. Drafts has just such an action built in; just use the clipboard replace action, and instead of the `draft` tag, use the `body` tag. This takes everything but the first line and sets the clipboard.

From here you can go wherever and slap it in. You can even search right within the filter if you have a lot of these.

![](http://media.sethclifford.me/blog/drafts_snippet_search.png)

### Workflow for quick access

So that takes care of the storage and the occasional browse to find a thing you want. The other time I need this ability is when I'm doing something in another app, and the easiest way to do this is with a widget. I headed over to Workflow and built a very simple list of some frequent snippets that loads right in the widget body, replaces the clipboard, and can be dismissed immediately. I noticed that 15 lines is the max I can fit in one of these on my iPhone 7; any more beyond that and you won't see everything. Again, my needs are simple, so this is fine. What I've done is build a multi-step action that first asks which list you want to display, and then displays the snippets in that list.

![](http://media.sethclifford.me/blog/workflow_snippet_widgets.jpeg)

[The simplest way to get started](https://workflow.is/workflows/0eba95508858471a9955674c79326d1a) is to just do a basic text list, add the exact text you want, and have it replace the clipboard. But you could also use the text list to show a label, and then add "Replace Text" blocks for each one, and then send the replacement to the clipboard. This would work better if you had bigger blocks of stuff that you weren't going to see anyway, or if you just like things looking tidy. (This was [Tim's](https://twitter.com/nahumck) idea, I like it; I like tidy things.)

What I've described is two separate sets of actions that manage this content. Now you _can_ can get Workflow to talk directly to Drafts by using the "Get Contents of Draft" action. This requires you to copy the UUID of the draft you want and place it in the action. This would be true automation, and way more fun. Unfortunately, when you do this, Workflow can't grab the content directly from Drafts without first switching to the app, so you leave the widget and do a quick round-trip, which defeats the whole purpose of having a widget action in the first place. So I chose a few of my most-used snippets for access within the widget and spent the time up front to save it later.

Now, you might be thinking: boy, that seems like a LOT of dumb work to do just to get the same functionality that a single app can provide, and you'd be totally right! It is. I will not argue this, not even a little. But, there are two reasons I like this.

  1. I always have both of these apps installed, which means they're always on every device anyway, and it's one less app to install/manage in addition to that. 
  2. Every time I do this kind of thing, I figure out new things. In many cases, these dumb little experiments end up allowing me to refine something else I might have been doing already. This feels good. 

Finally, I figured I needed a quick way to make adding snippets easier, so I created [a basic Workflow](https://workflow.is/workflows/cecbbc0ade22475db15e46ab8a206826) that asks for input or grabs the clipboard (assuming I've copied what I want), asks for a title, and uses [Tim's nifty Auto-Archive action](https://drafts4-actions.agiletortoise.com/a/1vu) to dump the filtered draft in the right bucket.

Needless to say, since Tim and I go back and forth on this stuff all the time, I'll drop an idea on him, and he'll latch onto it and improve the flows.

![](http://media.sethclifford.me/blog/pair_programming_posts.jpeg)

So he figured out how to construct the text as an array, and have Workflow present the list and pull the right text that way. Which means you can build a single text file in whatever app you want containing the labels and links/snippets/etc. and then just drop it into the leading text block in the workflow. This makes things very easy and nice. [Here's the template for that.](https://workflow.is/workflows/b10ce195392744c5ba0eba6f0da06fd6)

And then sometime later I went to bed. But he didn't.

I woke up to a long message and a few links. One to a [new Drafts action](https://drafts4-actions.agiletortoise.com/a/1wD) and one to [a Workflow](https://workflow.is/workflows/93fe39fe2c7a4c47abb42be96a733930) that's called by that action. Basically, since Workflow can't get the info directly out of Drafts in the background, he thought to create a text file that Workflow _could_ access in the background, and stuck it in its iCloud folder. Within that text file is the array, containing the names of the text snippets, and the corresponding values for them. You can store these files in Drafts, and update them whenever you need to. Save the file again to that same folder in Workflow's iCloud storage, and it'll overwrite. The next time you run the workflow, it calls the new information from that file. It's still not quite directly linking the two apps the way you'd think you should be able to, but it's damned creative, and I told him so. And it's way easier to edit the array within Drafts than in a tiny box within Workflow.

As far as I'm concerned, that's the best way to do this: maintain a text file (or a series of text files for whatever you want) in Drafts, save out changes to Workflow's iCloud folder, and the updated versions are always available when you want them. If you want to keep this in the widget, you're still limited to the row number, but if you don't care, you can have a list as long as you want.

I realize it seems circuitous and somewhat silly, but the whole point of all of this is to **play and learn.** The game of reducing apps has a direct benefit in that every time I restore or set up a new device, it takes less time to get up and running. But these small excursions also allow me to think through problems and find new ways to solve them. Some people engage their leisure brain with crosswords or sudoku. These are the little puzzles I like to solve.
