# Hey, The iPad Just Got PC-Style Drag And Drop–But Not From Apple

_Captured: 2017-05-25 at 21:25 from [www.fastcompany.com](https://www.fastcompany.com/40423958/the-ipad-just-got-drag-and-drop-thanks-to-readdle-not-apple)_

Someday-maybe as soon as its WWDC keynote on June 3-Apple will surely bring the familiar PC interface concept known as drag-and-drop to the iPad. But Ukraine-based productivity app developer Readdle isn't waiting.

Instead, Readdle is using its own suite of apps to make Apple's tablet feel more PC-like. Starting today, Readdle will let users drag and drop files between four of its productivity apps, including the Spark email client, the Documents file browser, PDF Expert, and Scanner Pro. Because Apple doesn't officially support drag-and-drop between iOS apps, Readdle spent months building its own workaround.

Even so, Readdle is rooting for its new feature to become redundant soon. Denys Zhadanov, Readdle's vice president of marketing, says the company would rather see Apple build its own version of drag-and-drop that works with any iOS app, not just those made by Readdle.

"We believe that this is the way inter-app communication should've been done on iOS since the very beginning of iPad," Zhadanov says.

That idea of official drag-and-drop support on iPad doesn't seem too farfetched, given that Apple is trying harder than ever to [market its tablet as a laptop replacement](https://news.fastcompany.com/apple-has-decided-that-the-ipad-pro-isnt-a-computer-after-all-4030875). But as with every PC-like concept Apple folds into iOS, drag-and-drop would require a tricky balance between simplicity and complexity.

## Hidden Trickery

Readdle experimented with a couple of approaches to build drag-and-drop, but ultimately settled on a technical workaround that uses local networking protocols. With two Readdle apps running side by side, each one creates its own local HTTP server. When the user starts dragging a file, the two servers share data about the file type, its thumbnail image, and its position on the screen, coordinating the appearance as the file moves between the apps. When the user lifts her finger, the file transfers between the two servers.

Zhadanov says this system took much longer to build than Readdle expected, but the company pushed ahead because of its own dissatisfaction with using the iPad for work. The kinds of things that drag-and-drop handles well, like signing and returning an emailed PDF, or attaching files to an email from different sources, can be a chore on iOS today.

"In my opinion, one of the reasons why the iPad didn't become my default working machine is that the multitasking is problematic, and of course moving files from one app to another is quite hard," Zhadanov says.

Still, Readdle's drag-and-drop system has limits. It only handles distinct file attachments, not snippets of text or inline images. Apps must be running in Split View for drag-and-drop to work, precluding users from moving a file between two full-screen apps. Most importantly, the feature only works with Readdle's own offerings, and while Zhadanov says Readdle would like to offer its version of drag-and-drop to other developers, he's uncertain about the timeline.

"Hopefully we can build an ecosystem off apps that support this," he says. "That would be amazing."

## Waiting For Apple

At the same time, Zhadanov is hoping Apple gets inspired to build its own version of drag-and-drop, which would naturally be free of the restrictions that Readdle has run into. And he's not alone.

Last week, _MacStories_ writer Federico Viticci-a longtime advocate for iPad productivity-published [a list of features he'd like to see in iOS 11](https://www.macstories.net/stories/ios-11-ipad-wishes-and-concept-video/), and worked with product designer Sam Beckett to visualize those ideas in a concept video. System-wide drag-and-drop was at the top of Viticci's list.

"Drag-and-drop is an essential improvement to iPad multitasking," Viticci says. "Ever since the release of iOS 9, which brought Split View and other iPad enhancements, it has seemed obvious to me that iPad users should be able to select something in one app and drop it in another. The iPad is uniquely suited for this kind of direct, tactile manipulation of content."

> _Federico Vittici's drag-and-drop concept_

But making drag-and-drop work across all iOS apps could be a bigger undertaking than what Readdle set out to do. In Viticci's mind, users should be able to drag an item with one finger while using their free hand to navigate around iOS. That way, users could drag content from one full-screen app into another.

"I understand why limiting drag-and-drop to Split View could be easier to implement and explain, but I hope Apple has bigger plans," he says.

There's also the question of whether Split View should support two instances of a single app, for example allowing drag-and-drop between two Word documents-something that iOS doesn't currently do, although Safari's ability to display two pages at once comes close. Viticci's concept doesn't address whether that functionality should be baked in at the operating-system level.

"It's a tough question, because Safari's implementation of tabs is inherently well suited for the in-app split-screen approach," he says, while acknowledging that it still could make sense for other apps.

Supporting drag-and-drop across all iOS apps could even lead to some compatibility challenges. What should happen, for instance, if the user tries to drag a snippet of text into an image editor, or a picture into a bare-bones text editor that doesn't support images? Translating content into a compatible format would require a deep understanding of how different apps work together. Viticci notes that Apple's [recent acquisition of the automation app Workflow could help solve that problem, as its underlying Content Graph engine was built to make those connections.](https://sixcolors.com/link/2017/03/apple-acquires-workflow/)

"I don't know if Apple plans to use the Content Graph engine for drag-and-drop, but I can see how a similar technology could be useful for that," Viticci says.

## Drawing A Line

Those kinds of challenges underscore the tough position Apple is in as it tries to market the iPad as the future of personal computing. Last year, Apple senior worldwide marketing head Phil Schiller referred to the 9.7-inch iPad Pro as "[the ultimate PC replacement](http://www.pcworld.com/article/3046422/ipad/apple-trolls-windows-users-launching-smaller-ipad-pro-as-ultimate-pc-replacement.html)," and the company recently launched an ad campaign calling out [traditional PC pain points](https://www.theverge.com/2016/8/1/12346576/apple-ipad-pro-ad-tablet-full-computer-keyboard-stylus) that don't exist on the iPad. But that angle puts greater pressure on the company to adopt some elements of the traditional PC experience, even as it tries to avoid duplicating what it already has in MacOS.

"One of the keys with iOS is that it's not meant to feel like a Mac or PC, it's meant to feel like its own thing," says Jan Dawson, the chief analyst of Jackdaw Research. "It's drastically simpler, and that has some limitations, but you have be true to the operating system and what it is to people."

Dawson is generally wary of having too many elements on the screen at once, and felt that some of Viticci's concepts, like a "Shelf" that can temporarily store items atop the screen during drag-and-drop, would veer too far into PC territory.

"What you really are used to with iOS is focus, working on one thing, maybe two things side-by-side," Dawson says. "But when you start to get three or even four things on the screen and interacting with each other at the same time, it just feels like, 'Hey, this is not what people come to iOS for.'"

Yet Readdle's Zhadanov says Apple hasn't gone far enough. A feature like drag-and-drop, at least, would help Apple crystalize its argument that the iPad can be a PC replacement.

"I think their first try to position this as a PC killer didn't work out and pissed people off, because the iPad did not replace the PC in many cases," he says. "My personal opinion is that it's an amazing piece of hardware, and the problem was in software."
