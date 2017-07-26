# Colors

_Captured: 2016-03-05 at 00:36 from [dimsumthinking.com](http://dimsumthinking.com/Blog/2016/03/03-Colors.html)_

I understand why developers want an IDE with syntax coloring when they code. I have no idea why we would want to see syntax colored code in books or presentations.

When you're coding away, it helps to see keywords highlighted in one color, strings in another, methods and properties in yet another. For one thing, I can spot typos in my code sometimes because the syntax coloring hasn't recognized something as a class name or method name. For another, it helps me classify what I need when I work with code.

Syntax coloring is there to help us while we code. It helps us focus. It helps us ignore what isn't of interest to us. It helps us get our work done.

None of this is true while we read a book or watch a conference presentation.

You've seen this may times.

You are watching a session at a conference and the presenter puts up a slide that is over-flowing with code in a font that is slightly too small. The code looks pretty because it is syntax colored.

Some colors jump out at you more than others but that doesn't mean that those things that jump out the most are the most important or are related to what the speaker is talking about.

Maybe the color used for strings is the most striking and so you are looking at a screen filled with code and the strings are popping out at you.

The syntax coloring is communicating information that isn't helpful to you.

As the speaker talks through the code, the coloring is actually fighting what they are saying.

Instead, imagine code that is mostly presented in a single color. The speaker uses an accent color to highlight the code they are talking about. As they talk their way through the code example, the highlight moves with them to direct your eye to the relevant pieces of code.

Now the colors are working with the speaker and not against them.

Unfortunately, it's easier for speakers and authors to use a syntax coloring tool or cut code from Xcode and paste with syntax coloring preserved.

Ironically, and yes I believe I'm using that word correctly, it's easier to produce code listings with more colors than it is to produce code listings with just the relevant parts highlighted.

Many book and slide production systems are moving to a Markdown based system. You can't easily color code in such a system (other than with a syntax coloring plugin) because marks that we would use to distinguish highlighted code from non-highlighted code are taken to be literals within a code block.

I wanted to create my ePub version of [A Swift Kickstart](https://gum.co/swift-kickstart) in Markdown but couldn't figure out how to color my code how I wanted to without writing my own Markdown parser. I wanted one color for existing code, another for new code, and a third color for comments. I also want another color for console and playground response.

I want to make it easier for you to glance at my code samples and have your eye be drawn to the most important parts.

I don't want syntax coloring.
