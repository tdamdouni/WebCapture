# Multichannel Text Processing

_Captured: 2016-06-11 at 10:44 from [ia.net](https://ia.net/know-how/multichannel-text-processing)_

![](https://ia.net/content/4-know-how/20160610-multichannel-text-processing/full-multichannel-text-processing.png)

**In the classic era of word processing, text was born between MS Word, and a printer. Today, it is written and edited on multiple devices and apps, then mailed, printed, copied, pasted, annotated, published, RSSed, shared and re-shared, using all kinds of tools and platforms. Stubborn proprietary file formats fail in this frantic new environment. Plain text does better, but lacks Rich Text's formatting. Markdown could be our golden gun. If only it looked a little shinier!**

So what are the strengths and shortcomings of Rich Text, Plain Text and Markdown1 in this diverse writing landscape?

## 1\. Rich Text

Rich text like MS Word or .rtf is famous for its promise of WYSIWYG (What You See Is What You Get). We can use bold, italics, different fonts and formatting, and we see them right there on our screen! When introduced this was a revolution compared to clunky "Reveal codes"-based formatting, or no formatting at all. But there are downsides.

![](https://ia.net/content/4-know-how/20160610-multichannel-text-processing/plain-text-vs-rich-text-plain-text.png)

In Plain Text the text _is_ the source. With Rich Text we see a simulation. What we see may please us, but below the surface our word processor secretly builds a more complex text in code. You can see this hidden world by creating a Pages or Word document, typing "Hello World" and saving, then changing the extension to `.zip` and unzipping the file. Welcome to 1979![2](https://ia.net/know-how/multichannel-text-processing)

![](https://ia.net/content/4-know-how/20160610-multichannel-text-processing/hello-world.png)

If you are courageous enough to look inside the resulting folder, you may start wondering whether you typed "Hello World" or "Hello Hell":

![](https://ia.net/content/4-know-how/20160610-multichannel-text-processing/hello-hell.png)

Custom formats are heavier than plain text formats. The main issue of custom formats is that the relation between the source code and text--between what we see and what we don't see--is capricious. Here is what you really get when you work with these formats in 2016:

Bugs and UX Trouble

How do you get out of a list or remove indentation? How do you unlink a word? What about getting rid of that bold formatting, line height, or title size? And how the heck do you place two pictures next to each other? Sometimes it's not even clear if we are dealing with a bug or bad UX.

Copy Pastasciutta

The predominant challenge of custom formats in a multichannel publishing environment is that they break Copy-Paste. We copy a simple paragraph from a PDF, then on pasting it into our email the English text morphs into an Italian spaghetti Western, with lots of dramatic spaces and line breaks. And it's not just PDF. With formatted text we never know what we're going to get when we paste.

Compatibility

While `.rtf` is fairly established and most Word Processors read `.docx`, different apps interpret these formats differently. You can't reliably add RTF or Docx text into your CMS. And just forget about going back and forth between a CMS and a Word document.

Forking

Exporting may be "just a click", but forking your text into multiple versions complicates your workflow. Feedback or alternate edits can't be easily incorporated back into a master file. Managing these versions quickly becomes a nightmare.

Accessibility

Rich Text will not allow you to touch the source of your document. Maybe the text is in a folder that pretends to be a file, or hidden somewhere "safe from the user", buried deep in nested folders of spaghetti code, or encrypted in the Fort Knox of a secret database.

Of course, as a bizdev person you love the golden manacles of custom formats. As a regular person writing text in 2016, using different apps, devices, platforms and formats, you do not. And who knows how we'll feel about `.docx` in 10 years' time. Or 30.

> Although modern word processing programs can do some amazing things--adding charts, tables, and images, applying sophisticated formatting--there's one thing they can't do: Guarantee that the words I write today will be readable ten years from now. That's just one of the reasons I prefer to work in Plain Text: It's timeless. My grandchildren will be able to read a text file I create today, long after anybody can remember what the heck a .dotx file is. [3](https://ia.net/know-how/multichannel-text-processing)

In today's multichannel text environment a Rich Text file format creates even more barriers than in simpler times. The notion that you need to install a certain version of an app on a certain version of an operating system to open a file sounds like a joke. In order to be shareable between different apps and platforms, the text itself needs to be free of the shackles of app, platform or device.

## 2\. Plain Text

The only file format that works as expected anywhere is _no_ file format, in other words: Plain Text. And it's all we need to write our first drafts.

> Plain Text means words separated by spaces; sentences separated by periods; paragraphs usually separated by single blank lines. If you are in the writing business, even the publishing or screenwriting business, it's often all you need.[4](https://ia.net/know-how/multichannel-text-processing)

Plain Text is straight forward. It helps you focus on what you want to say.

Plain Text is free. TextPad, TextEdit, Vim, your cellphone, your uncle's 1997 AOL mail app… no jacket required.

Plain Text is light.

Plain Text flows like water. But unlike water, it does not quench every thirst. Be it print, a blog post, a PDF, an email, or even a fax, sooner or later that text will have to take on a medium-appropriate shape to be read. As our words take shape inside a medium, they require visual structure. Business materials need headers, footers, and cover pages. Some texts only come to life when illustrated and enriched with pictures, videos or tables. We want links when we write online. We need footnotes in a white paper.

The transition from Plain Text to formatted text has generally been abrupt and irreversible. You write in TextEdit or Notepad, but once you move to RTF, Docx or HTML there is no turning back. However, text naturally wants to slowly transform from just words to formatted prose. This is where Markdown enters the scene.

## 3\. Markdown

Markup languages, like Markdown, MediaWiki or LaTeX, allow you to structure your words without building an invisible Kingdom beneath the plain text. Unfortunately…

### 3.1 Markdown Sucks!

You might have tried writing Markdown or editing a Wikipedia entry and _hated_ it, because "Why would I want to learn some new 'syntax' for formatting text when I have a tool that does it at the push of a button, and shows me exactly what I'll get?"[5](https://ia.net/know-how/multichannel-text-processing) And right you are:

  * Writing in markup may get you around some copy-paste problems, but plain Markdown always looks messy
  * While Markdown is simpler than HTML, you still need to remember the syntax, and looking up how to add a link every time throws you out of the flow
  * Markup, Markdown, MultiWhatever… these formats have their own compatibility problems

Markdown is not the perfect solution for every type of writer, or every form and stage of writing. But if you do everything from note taking to publishing yourself, it is the most efficient solution to date. If you have a publisher that dictates your writing tools, Markdown is less of an option. But then again, the ability to be more easily shareable than traditional file formats may make that collaboration considerably smoother…

### 3.2 A Plea for Markdown

Aesthetic opinions aside, Markdown is unbeatable if all you do is **bold** and _italics_. Typing # or ## or ### for different headers might look clunky. But, once learned, typing hash signs is faster and easier than taking your hands off the keyboard, finding the mouse pointer, selecting some text, clicking on the Headline WYSIWYG pulldown, and choosing the right Headline level. And unlike those grumpy Style Formats, hash signs always behave like they should.

If you know these three things, *, ** and #, you know enough about Markdown to get started. And the better you get at Markdown, the less friction in your overall writing process. Let's look at some tougher challenges:

Links

Markdown links can completely ruin the look of your text. It is helpful to see the links right there in the text and not have to fiddle with right-clicks and pop-ups, but if you use too many links in the text it is awful. One workaround is using reference-style links. Another would be to collapse links in the editor, but this comes with those Rich Text Downsides.

Multimedia

Having more freedom with pictures in text is cool. If you want a program that deals with laying out pictures well, use InDesign, or do it in your CMS. Don't go for Word and, hell, don't expect your Markdown editor to do everything as well as it helps you get words out. Yes, you can use Markdown in Indesign.[6](https://ia.net/know-how/multichannel-text-processing)

Tables

Tables in plain text have a bad rep. If they are complex they look terrible indeed. But for a handful of rows and columns they can work well: Unlike in Word, you see exactly what is going on. (If you do advanced tables, Word is your enemy anyways--use Excel or Numbers.) They are annoying to create, too; but with some magic…

Automation

With MultiMarkdown[7](https://ia.net/know-how/multichannel-text-processing) (a souped-up version of Markdown) you can automate tables of content, and with metadata variables you can even build correspondence templates. Okay, that sounds hardcore. And it _is_ hardcore. But you should [try](http://vimeo.com/158324329) it. You don't need to be a ninja rockstar hacker to understand the basics. And once you do understand the basics, it gets easier to [generate a Table of Contents in MultiMarkdown](https://vimeo.com/158311378) than in MS Word.

Footnotes

MultiMarkdown also has footnotes. The syntax is a little obtuse like links, but they're squirrelly in Rich Text editors as well. But with [a Markdown editor that offers preview](https://vimeo.com/158933545) you can learn the syntax while doing clicking.

The better you master Markdown, the faster and easier you move between plain and formatted text. That is where Markdown kills: in _bridging_ Plain and Rich Text, it allows you to continuously form text--from the first random note up to multichannel publishing.

Live Rendering

There are ways to improve Markdown rendering, such as folding it, but if you just render Markdown in place, WYSIWYG, you reintroduce all the issues that make Rich Text editors obsolete, plus add a few new ones. If you try to do everything with Markdown that Word does without it, eventually you start building Word on a language that is not built for WYSIWYG. This is why iA Writer doesn't hide any Markdown characters.

## 4\. A Contemporary Workflow

We may fantasize the different steps in a writing process as being separate phases that can be controlled and put in a chronological order. In reality, we take notes ahead of writing, yet continue to collect material up until publication. Editing starts with the first draft, and--not only in digital media--it goes beyond publication.[8](https://ia.net/know-how/multichannel-text-processing)

Separating steps in a creative process is necessary, but flexible workflows are not waterfalls: they overlap, interact, cross-influence, and our writing and publishing tools should allow us to go back and forth as we wish.[9](https://ia.net/know-how/multichannel-text-processing) Writing is naughty by nature.

![](https://ia.net/content/4-know-how/20160610-multichannel-text-processing/workflow-note-draft-edit-publish.png)

Focused writing is not writing with blinders, it means your main attention is directed to one aspect of the whole process. It is even helpful to consciously move back and forth between two neighboring steps. Markdown allows you not to worry about the thresholds.

#### 4.1 Write And Preview

Moving back and forth between steps in a process is necessary and refreshing. If you love to work in a WYSIWYG editor, or print your text from time to time, or regularly preview it on your blog before publishing, you already know: Definite formatting helps us to take the reader's perspective on the text. Seeing our text printed out changes our perception of it. You get a similar effect when you swipe away from Markdown and look at your rendered text in HTML-preview.

![](https://ia.net/content/4-know-how/20160610-multichannel-text-processing/markdown-with-preview-plain-text.png)

The effect may not be as striking as the jump from screen to print, but it gives a glimpse of the shape of the text to come.  
With the feeling of how a reader will see your text, you can go back to your text with fresh eyes. This is quicker as it saves the boring, time-consuming exercise of retyping handwritten corrections.

The conscious switch between Plain Text and formatted text will let you imagine how the text reads from outside.

The deliberate switch between Plain Text and formatted text shows you how the text reads from outside.

#### 4.2 Edit and Publish

The same change of perspective happens when you switch between the front-end and back-end view of your text--once you move the content to your CMS.

If you already write your texts in Markdown, make sure your publishing tool allows you to edit the Plain Text without losing all the formatting. You don't need to go all in with a Markdown file-based CMS. If you use WordPress you can install a Markdown plugin for the editor. It helps if the writing apps you use support posting to different platforms from the get-go. This is why [iA Writer](https://ia.net/writer) allows you to publish directly to WordPress and Medium:

Publishing directly from your writing app is cool. The key though is that you can Copy-Paste your text back and forth without losing work. Copy-Paste is often faster than pushing lots of buttons. Unless you are a workflow genius, you won't get around adding some final touches in Indesign, WordPress or .Pages. What good is a publishing tool if it doesn't let you do things a word processor can't?

## Conclusion

We use different devices to take notes, different apps to draft and edit, we send text to other people, and we use different platforms to shape and publish our words. The production process, and the final shape of our text, has become less calculable. We need more than traditional text formats that lock us into a defined format/app/platform/device framework to cope with today's complex formatting and publishing reality.

Because of its universality and simplicity, Plain Text gets us further than any file format. Yet, Plain Text editors are not made to visually structure text, optimize complex layouts, fiddle with detailed typography, or interlink text bodies. They are great for finding the right words, but fall short the longer the text gets. A contemporary writing process needs to allow us to freely move back and forth between plain words and formatted text, via automated workflows or copy-paste.

So far, light markup languages like Markdown are the only things that allow this. Markdown may look a bit messy and, yes, all sorts of improvements are possible and necessary. In spite of its shortcomings, it solves complex methodical problems where the traditional separation of plain words and formatted text fails. It allows us to use our text and the file it is embedded in everywhere, independent of device, platform or app. The moment where you move between text and style, package and content, body text and layout shouldn't be a single point of no return, it must be a phase where you can freely move back and forth. Markdown makes this possible.

If you want more complex formatting options like links, pictures, footnotes and a TOC, use the UI or shortcuts. To improve your Markdown skills with more advanced syntax, get help from a text editor that offers live preview. This also gives you a glimpse of how the formatting will appear early on, allowing you to use more complex markup as you can quickly find any mistakes.

Automation between your cloud service, note app, text editor, and publishing environment is cool, but not essential. What _is_ fundamental is the ability to copy-paste your text back and forth without losing formatting or information. Only a plain text format guarantees this. Configure your publishing platforms to interpret Markdown, so you can move freely between Writing, Editing and Publishing. There are many different ways and apps to do this. And that's precisely the point. Plain text is light and free and should stay that way. Avoid apps that want to put it in shackles.
