# Holy Crap, I’m Programming on My iPad: A Web Developer’s look at Diet Coda

_Captured: 2015-12-03 at 10:21 from [josephschmitt.me](http://josephschmitt.me/post/23738549352/diet-coda)_

No seriously, I was[1](http://josephschmitt.me/post/23738549352/diet-coda). Honest to God, I did real programming and fixed a couple of real bugs for an imminent new feature/product on [Vimeo](http://vimeo.com/musicstore) using [Panic's Diet Coda](http://www.panic.com/dietcoda/). I even did it all using just the touch-screen keyboard (because I appantly hate myself). It was all surprisingly smooth and straightforward[2](http://josephschmitt.me/post/23738549352/diet-coda) and completely blew me away. Within _minutes_ I had done a fresh [git](http://git-scm.com/) pull, diagnosed the bug (in Mobile Safari, for reasons I'll get to), implemented a fix, confirmed the fix, and pushed up to our repository. Major, MAJOR kudos here to the folks at Panic. _slow clap_. A beer on me when you're [in town](http://developer.apple.com/wwdc).

After the initial shock wore off that I was doing all of this _on a freaking iPad_, I did start to notice a bunch if things about the app: some good, some bad. That's what I'll spend the rest of my time talking about, starting with[3](http://josephschmitt.me/post/23738549352/diet-coda)…

### The Good

There's a lot to love here, and in typical Panic fashion, the UI is equal parts splendidly well thought-out and gorgeous. I could talk all day about the innovative way they handle file tabs, or the super loupe, or the scrollable bread crumbs. But you've undoubtedly [heard about](http://www.macstories.net/stories/diet-coda-from-an-ipad-bloggers-perspective/) all these headlining features already, so instead I want to talk about the tiny, detail stuff that made me smile/gave me a big-ass grin:

**Multi-touch: what is it good for**  
Text selection, it seems. That's right, you can start a text selection with one finger in one hand, and when you put another finger down on the screen (likely from your other hand unless you're related to [Plastic Man](https://en.wikipedia.org/wiki/Plastic_Man)) you'll select all the text in between. It feels so natural in use that it's silly it took this long for someone to implement it. If you're less dexterous, tapping and dragging on the line numbers in the left-hand gutter will do the trick too.

**A save button**  
Yes, this might be the "Post-PC Revolution" where things auto-save and yadda, yadda, but when we're editing remote server contents, you want more control over when a file should be updated (and uploaded), so saving is _key_. Luckily Diet Coda delivers with a handy (amd gigantic) green check-mark. I'm equally grateful they forewent a floppy disk icon for the button itself.

**Context-sensitive keyboard**  
I certainly wouldn't recommend building a whole site using the touch-screen keyboard, but when in a pinch it works well enough. And the part that _really_ made me smile is the bar of shortcut buttons above the keyboard changing based on the language of the file you're working with. Angle brackets for HTML, dollar sign for PHP, semicolons and parenthesis for JavaScript. Nice.

**Go to line number**  
Not much else to say here other than I'm glad it wasn't overlooked. Also, [it's beautiful](http://cl.ly/GtBj).

However, as good this initial release of Diet Coda is, I found myself getting quite frustrated at several points while coding. Almost none of it had to do with limitations of a tablet or touch-screen platform, leading us to…

### The Missing

Unfortunately, this list is going to be a long one. I don't do this to nitpick (yes I do). I do this because this app got so much right and came so close to making me feel comfortable in it, that these sore spots really hurt.

**No route mapping**  
This one hit me right off the bat and was pretty much the only thing keeping me having a 100% working setup immediately. The file preview button might work great for static HTML files, but if your site has even a modest level of complexity, your preview url probably won't fall into the `/remote-path/path-to-file/file` scheme. Some way to declare a different url when previewing a file's changes (or just being able to spawn a browser window as a new tab) would help. Until then (and until the preview browser can show Console logs), I'll be previewing changes in Mobile Safari.

**No quick-find for files**  
Our project structure is massive. Thankfully, apps like TextMate ™ and SublimeText 2 (ST2) have a "Find in Project" command that behaves like Quicksiver or Alfred for files in the project you're in. I didn't realize how much I depended on this and how much I forgot about where our files lived until I had to go looking for files on my own.

**No quick-find for symbols**  
In conjuction with a quick-find for a file in a project, another stunningly useful feature in TM and ST2 is the "Go To Symbol" command. This behaves very similarly to "Find in Project", except it's just for the symbols in your open file (symbols being things like functions in JavaScript, tags with ID's in HTML, or CSS declarations). Sure, the find window works, but it's much slower since it'll match both the invoked version of what you're looking for as well as the definition itself. Textastic offers a [list of symbols you can jump to](http://cl.ly/GtdC), which would be a good start too.

**Hitting "return" in the find window doesn't jump to the next result**  
Instead, it just adds a return character to the find input field. I guess I understand why they need to support multi-line finds, but there needs to be an easier way to go to the next result. The next button is much too small, especially if you want to keep your eyes on the search result itself as you tab through on to the next result. I'm just as likely to hit "Replace" as "Next" when tapping blind (which can be quite destructive, actually).

**Comment shortcut button doesn't comment out the whole line**  
It's hard enough to perfectly position your cursor in iOS, so it's especially annoying that in order to comment out a line of code with the handy Comment Out Button, I have to position it perfectly at the beginning of a line. Just have it work the way most text editors do: if I hit the button, no matter where in the line my cursor is, comment out from the beginning of the line all the way to the left.

**Wrap a selection when using paired punctuation (ie. quote, parenthesis, bracket)**  
This one's a biggie for me and relates to the previous one. Again, cursor positioning is really hard on iOS; it takes a lot of effort to get the thing at exactly the right spot next to a word. What's a lot easier, though, is double-tapping to highlight a word. Therefore, I was dissapointed to find that typing any of the pair-punctuation characters don't wrap around a selection. What do I mean? If I highlight a word and hit single quote, I want that word to be surrounded by a single quote on either side of the selection, not replaced with it. This is a huge time saver on a desktop text editor, but would be amazingly convenient on iOS.

**Tabbing from anywhere in a line doesn't indent that line**  
Similar to the comment-out button, but for indentation. I don't want to have to position my cursor when indenting a line. Let the indentation apply to the whole line no matter what position in that line I'm in.

**No way to turn off line-wrapping**  
I hate soft-wrap, especially for code. It's nice for certain types of code, but more often than not it just makes me confused as to the structure of a document. This is especially annoying when writing things where line-endings and indentation tell you the structure, like HTML and JSON.

**Terminal session quits way too often**  
It seemed to me like if I spent more than a couple of minutes outside the SSH client, by the time I switched back I would be logged out again. Mildly annoying to say the least. Would be nice if I could at least change the timeout time.

**No code snippets for terminal**  
Speaking of that SSH prompt, 90% of the time I switched to it was to type 'git status', 'git pull origin master', or 'git push origin master'. It would be nice if I could save these snippets in a similar UI as the ones in the code editor.

**No redo???**  
I saw the undo button, but for the life of me couldn't find a "redo". That has to be a mistake, right? (**Update**: looks like there is a way, thankfully: <http://josephschmitt.me/post/23738549352/diet-coda#comment-538608035>)

These are all things I feel are _essential_ in a code editor for me to go more than 30 seconds without getting frustrated. There are, however, a few nice-to-haves that I'd like to see in Diet Coda…

### The Pie in the Sky

This wouldn't be a ridiculous, unsolicited product review without a few outlandish feature requests, right? Right. Let's get right to it:

**Multiple Carets and Selections**  
Alright, this one's probably asking for a bit much, but once you have multiple carets and selections, [there's no going back](https://www.youtube.com/watch?v=g9TvM46ZW9E).

**Syntax-highlighting needs some work on mixed files**  
For example, a PHP file with inline CSS and JavaScript.

**Better code completion**  
"A"-for-effort for even _trying_ to implement this, but in practice I found that the auto-suggest window didn't suggest very many useful things. Something to work on.

The fact that the pie-in-the-sky list of web developer that uses text editors every day for a living is so short really speaks volumes about this app, which leads me to some…

### Conclusions

[Diet Coda](http://panic.com/dietcoda) is great. Seriously. This app might not be your first choice to do serious work on (yet). However, if the only reason you're taking your huge, heavy laptop with you on that otherwise relaxing vacation is just in case you get the 5-alarm-fire call from your boss because of a major bug that needs to get fixed RIGHT NOW (don't they all?), Diet Coda and an iPad with an LTE/3G connection could be all you need.

  1. A few notes on my setup. I was able to do this because of the way our dev environment is set up. We basically work off of NFS mounts of our dev server where each dev has their own folder with their own full git checkout of the site. So working Diet Coda was a simple process of using SFTP to get at the files I needed, and then using the built-in ssh terminal to do all the other stuff (like git pulls and pushes). [↩](http://josephschmitt.me/post/23738549352/diet-coda)

  2. Diet Coda sure beat the previous iOS setup I had: ssh-ing in and using vim. Do _not_ use vim through iOS on a regular basis, you'll live longer. [↩](http://josephschmitt.me/post/23738549352/diet-coda)

  3. Forgive my [Rands](http://randsinrepose.com)-style lead-ins here, but they're fun. [↩](http://josephschmitt.me/post/23738549352/diet-coda)
