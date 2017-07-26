# 5 myths busted: Using open source in higher education

_Captured: 2017-06-02 at 00:50 from [opensource.com](https://opensource.com/article/17/5/how-linux-higher-education?utm_campaign=Sharing%20Security%20Stories&utm_content=55113465&utm_medium=social&utm_source=twitter)_

![5 myths busted: Using open source in higher education](https://opensource.com/sites/default/files/styles/image-full-size/public/images/education/EDU_misconceptions_520_9658437_0712LL.png?itok=8T7lvlZJ)

> _Image by : opensource.com_

Have you ever heard someone say, "It's impossible to do X with Linux"? Me too. This is the story of how I busted the myths about open source in my own head and used Linux to finish my PhD in fine arts.

Many people think non-technical students can't use Linux, and they make a lot of assumptions about people who use it in their advanced degree programs. They scoff and reply with something along the lines of, "Well, of course; those people do 'computer stuff,' but in my [lofty, important, unique area] it's just not possible." Well, it is possible, and I'm proof.

Here are some of the many (misguided) reasons I've heard people use to argue why Linux can't work in higher ed:

  1. **Real world:** Linux/open source is not what I'll/they'll need or use in the _real world_.
  2. **Tool over task:** I _have_ to use [special program] in [specific field].
  3. **Special knowledge:** Sure, it works for you because _you_understand computers.
  4. **Change is hard:** Open source is just different/another thing to learn. I _know_ how to use [Windows/Mac/Chrome].
  5. **Lack of integration:** It just won't run/do [specific application / task].

While all of these things hold a grain of truth, usually the objections come because they're underexplored or misplaced.

## How I discovered Linux

I grew up using Windows, learning Microsoft Office, and believing that I should use them because well, honestly, I didn't think about tools because that was just what everyone else used. Eventually, I bought a PowerPC Mac Mini, only to discover mere months later that Apple was switching to Intel processors and my desktop would eventually be unsupported. (A shoutout to Debian for keeping the Mac Mini running and useful well into 2017.)

Being newly married and entering graduate school 1,000 miles away from family made me extremely price sensitive. I also had a growing interest in free/libre software, having been swayed by the ethical arguments and the strong communities, plus I like having alternatives that aren't necessarily driven by a profit motive (and if they are--and if things go wrong--they can be forked).

Learning that [GIMP](https://www.gimp.org/) was this thing called "free and open source software" opened a new world to me. Suddenly I saw open source software everywhere, even in things I was already using, and I reached out for other options like OpenOffice, Firefox, and Audacity. That brought me to something entirely new to me: free and open source operating systems.

I read with interest and suspicion. Eventually, Ubuntu's [Wubi](https://wiki.ubuntu.com/WubiGuide) install (a familiar-feeling .exe file) won me over because it allowed me to choose whether to boot into Ubuntu or Windows. I found myself using Windows Vista less and less, until one day my Wubi install wasn't an option anymore. It had disappeared.

The community came through for me, and I learned how to use Windows' cmd.exe to restore my folder, boot back into Ubuntu, and rescue my files. That day I wiped my drive and installed Ubuntu as my sole OS.

To this day, I've never met another Linux user in the flesh.

## The tools shouldn't matter

Language works against you when you're an open source student in a closed-source world. Instructors will tell you to turn in your paper as a _Word document_ (with specific formatting guidelines and instructions for the version of Word that's on their computer) or insist that you give a _PowerPoint presentation_.

They're likely well-meaning people who are unaware of the alternatives. You'll have to educate them. At the end of the day, they're not teaching you software, they're teaching you concepts and ideas. In my fine arts PhD program, I was ultimately being judged on how effectively I employed the concepts of narrative structure or negative space, so it shouldn't (and didn't) really matter if I put the words into LibreOffice or the pixels into GIMP; what I said with those words and how I arranged the pixels are what was most important.

## How I found the right solutions

Still, finding the right open source tools was somewhat of a trial-and-error process.

While you can use [LibreOffice Impress](https://www.libreoffice.org/discover/impress/) for presentations, I saw so many PowerPoint-style presentation mishaps that I started to use PDFs when presenting. Every computer and every OS will display them, and they always work―no glitches. At the beginning, I designed in LibreOffice Impress and printed to PDF, but eventually, I started hand-designing my own slides in [Inkscape](https://inkscape.org/en/) for pixel-perfect presentations.

Now there are tons of cool, open source presentation software available. For example, [Sozi](http://sozi.baierouge.fr/) is an amazing tool that creates what most people know as Prezi-style presentations. I greatly prefer it, as you can dance around your .svg files from Inkscape and infinitely zoom without loss. [Here's a quick, incomplete example](https://kylerconway.com/fedora-design/become-designer.sozi.html#frame6961) of something I did for the Fedora Project about the process of becoming a contributor.

Perhaps the most essential tool in my area of study is playwriting software. There are important reasons for standard formatting in plays, such as allowing a quick way to assess a play's length (i.e., how long will this play be?) by page number that is common across all scripts. Professional playwrights tend to use the closed source Final Draft for formatting, and the old, rebellious writers use Microsoft Word with painful, manual manipulations.

Since neither of those met my demands, I googled a bit and found [Celtx](https://www.celtx.com/index.html). This cross-platform desktop application worked beautifully. It turned out that no one could tell I didn't use Final Draft, and I was even able to help other writers use Celtx on their own computers.

You'd probably be surprised how many of my fellow students had Windows but not Microsoft Word. I introduced them to [OpenOffice](https://www.openoffice.org/) (and later [LibreOffice](https://www.libreoffice.org/)) and even created some custom formats and keyboard shortcuts to make quick work of formatting play scripts in those apps in real time.

When I was writing scripts as part of my dissertation project, I moved to [Emacs](https://www.gnu.org/software/emacs/) for writing and [LaTeX](https://www.latex-project.org/) for processing PDFs because _why not?_ The words are what matter most, the format matters next, the software matters not at all.

Since then there have been even more interesting developments. Screenwriter [John August](https://twitter.com/johnaugust) found the joy of open-format text files and developed a markdown-like plain-text conversion system called [Fountain](https://fountain.io/). Apps [(many open source)](https://fountain.io/apps) can be created to leverage this format.

## Busting the myths

I think educators, students, and others often get lost on the tools at the expense of the thing they're actually doing--teaching and learning new ideas--and that's a mistake. If education is overly focused on teaching you a specific tool, then you could just as easily RTFM and save the expense of a degree.

People have legitimate reasons to think they can't use Linux for education, but if you dig just a layer below their initial, knee-jerk assumptions, you'll often find they're built on unsound ground.

Remember all those reasons I relayed at the beginning for why people say open source won't work in education? Here are my responses to them.

### Real world

The real world changes so fast that this really isn't a solid argument. I wrote my dissertation on Emacs and [Gedit](https://wiki.gnome.org/Apps/Gedit) and formatted it in LibreOffice. I work at an organization that runs on Google Apps for Business. In the real world, you're better off being adaptable, and most organizations expect to give you on-the-job training anyway. Start learning to adapt today. Consider it part of your education.

This is related to No. 1 but has a different focus. The tool (Photoshop, Word, Final Draft) is not what you're actually trying to accomplish (e.g., create a poster for your event, send a memo, write a screenplay). Don't confuse the tool with the task. I was fortunate to team-teach an art course with [Dirk Fowler](http://www.depts.ttu.edu/ART/SOA/nav/faculty/faculty/Fowler,%20Dirk/fowler.php) at Texas Tech University. Dirk is a visual artist who has made [posters for bands](http://f2-design.com/store/#store) you probably like. He's also a visual artist who doesn't use Photoshop―he doesn't even use computers, rather he uses an antique letterpress. Task > Tool.

### Special knowledge

I "understand" computers (better than most, I guess) because I tried to do things with them that teachers couldn't or wouldn't teach me. Again, start adapting. Don't let your fear of getting it wrong prevent you from learning something new. There's no cost to start (i.e. free as in beer) and nothing prevents you from learning (i.e. free as in freedom). Wanna know how it works? Read the source, mod the config file, or talk with the dev on IRC. Heck, get a group of users together and code it yourselves or fund its development. You'll gain knowledge by doing, and that knowledge is both specific (to the improvements you identify and the changes you make) as well as general (because whether you know it or not you can affect the tools you use directly if they're free/libre and open source).

Yes, it is. That's the wrong point to make though. The question isn't whether or not it's hard―it's whether or not it's worth it. When most "normal" users have complaints about their tools they tend to make an incorrect assumption―not that they don't know how to do it (which might be true), or that the tool doesn't do it (which also might be true), but that it simply can't be done. And I can't overstate this point enough: using and being a part of the community that uses open source tools means that the answer the to question "Can X be done?" is always―always―yes. It might not be how you thought of doing it, but there's always a way (and, helpfully, often multiple ways). So if "change is hard" is the mantra you hear, focus on the benefits: Is it worth it? (Note: the answer is always "yes.")

### Lack of integration

Do you _need_ to use [application]? If so, then, by all means, use it. If not, what are you waiting for? And even if you do need to use a certain application for some reason, ask yourself what you're missing by not integrating other tools into your workflow. As an example, Emacs's Org-Mode is amazing. I challenge any writer hooked on Scrivener to watch science writer [Jay Dixit's walk through](https://www.youtube.com/watch?v=FtieBc3KptU&feature=youtu.be) of his customized Org-Mode writing setup and not drool a few times. Then, read [an article by Howard Abrams](http://www.howardism.org/Technical/Emacs/orgmode-wordprocessor.html) about styling Org-Mode as a word processor so that it looks better for writing. The point is this: There are features out there that you don't even know you're missing. You'd want them if you knew about them. There are people just like you who have already thought these features up, coded them together, and shared them freely. I promise they'll help.

Lastly, the biggest lack of integration is that a piece of software is not open source and free/libre. That one omisson means you have anti-integrations (e.g. no export at all for vendor lock-in), and no real ability to get new features added ("it's too hard to maintain, "not enough of our users want it," "we don't integrate with X because they're a competitor"). Every time I even think of using a closed piece of software I run through a list of negatives related to this "lack of integration" that is thrown around―falsely―as a negative of free/libre software. The opposite is true. Can this free/libre software integrate with X? Yes.

If like me, you're using open source against the grain in your industry, you've probably heard similar excuses from your colleagues about why it won't work. How do you respond?
