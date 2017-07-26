# The Future of Markdown

_Captured: 2015-12-01 at 02:56 from [blog.codinghorror.com](http://blog.codinghorror.com/the-future-of-markdown/)_

Markdown is a [simple little humane markup language](http://www.codinghorror.com/blog/2008/05/is-html-a-humane-markup-language.html) based on time-tested plain text conventions from the last 40 years of computing.

Meaning, if you enter this…
…you get this!
    
    
      
    Lightweight Markup Languages  
    ============================
    According to **Wikipedia**:  
    > A [lightweight markup language](http://is.gd/gns)
    is a markup language with a simple syntax, designed  
    to be easy for a human to enter with a simple text  
    editor, and easy to read in its raw form.  
    Some examples are:  
    * Markdown
    * Textile
    * BBCode
    * Wikipedia
    Markup should also extend to _code_:  
    10 PRINT "I ROCK AT BASIC!"  
    20 GOTO 10  
    

## Lightweight Markup Languages

According to **Wikipedia**:

> A [lightweight markup language](http://en.wikipedia.org/wiki/List_of_lightweight_markup_languages) is a markup language with a simple syntax, designed to be easy for a human to enter with a simple text editor, and easy to read in its raw form. 

Some examples are: 

  * Markdown
  * Textile
  * BBCode
  * Wikipedia

Markup should also extend to _code_: 
    
    
      
    10 PRINT "I ROCK AT BASIC!"  
    20 GOTO 10  
    

You can think of Markdown as a radically simplified and far more human readable form of HTML. **I have grown to love Markdown over the last few years.** If you're a programmer of any shape, size, or color, you can't really _avoid_ using Markdown, as it's central to both GitHub and Stack Overflow. For that matter, my new project uses Markdown, too.

Markdown is a wonderful tool, but it does suffer a bit from [lack of project leadership](http://www.codinghorror.com/blog/2009/12/responsible-open-source-code-parenting.html). The so-called "spec" is anything but, and there are dozens of different flavors of Markdown out there, all with differences in the way they behave. While they are broadly compatible, Stack Overflow and GitHub have both tweaked Markdown in ways that can trip you up if you're familiar with one but not the other; compare [GitHub Flavor](http://github.github.com/github-flavored-markdown/) with [Stack Overflow Flavor](http://stackoverflow.com/editing-help).

That's why I was so excited to get this email from David Greenspan a few days ago:

> I'm the creator of [EtherPad](http://etherpad.com/) (a collaborative WYSIWYG editor), now working at [Meteor](http://meteor.com/). At Meteor, we're trying to "pave the web" for developers by writing better components. For example, we just released universal login buttons that talk over WebSockets and are wired into the users table of the app's database. Since Markdown is increasingly ubiquitous for writing content, it's going to be part of the Meteor toolchain. I wouldn't be surprised if we end up releasing a component [like Stack Overflow's editor](http://code.google.com/p/pagedown/), with the full "Meteor" standard of code quality, so that no one has to roll their own again. Today, we use Markdown in our API docs generation, and we're going to be writing more and more content in it -- which is a scary thought.
> 
> I think you and I share some concern (horror?) about [Markdown's lack of spec and tests](http://www.codinghorror.com/blog/2009/12/responsible-open-source-code-parenting.html). The code is ugly to boot. Extending or customizing Markdown is tricky (we already have some hacks and they are terrible), and I worry about "bit rot" of content if the format doesn't have a spec. I'm evaluating the possibility of starting over with a new implementation coupled with a real spec and test suite, and I've been thinking a lot about how to parse a language like Markdown in a principled way. I'm pretty fearless about parsers, by the way; I wrote a [full ECMAScript parser](http://jsparse.meteor.com/) in a week as a side project.
> 
> I want this new language - working name "Rockdown" - to be seen as Markdown with a spec, and therefore only deviate from Markdown's behavior in unobtrusive ways. It should basically be a replacement that paves over the problems and ambiguities in Markdown. I'm trying to draw a line between what behavior is important to preserve and what behavior isn't.

I was excited because, like David, I freaking _love_ Markdown. I love it so much that I want to see it succeed and flourish over the next 20 years. I believe the best way to achive that goal is for the most popular sites using Markdown to band together and take ownership of Markdown as a standard. **I propose that Stack Exchange, GitHub, Meteor, Reddit, and any other company with lots of traffic and a strategic investment in Markdown, all work together to come up with an official Markdown specification, and standard test suites to validate Markdown implementations.** We've all been working at cross purposes for too long, accidentally fragmenting Markdown while popularizing it.

Like any dutiful and well-meaning suitor, we first need to ask permission for this courtship from the parents. So **I'm asking you, [John Gruber](http://en.wikipedia.org/wiki/John_Gruber): as the original creator of Markdown, will you bless this endeavor?** Also, as a totally unreleated aside, have I mentioned what a _huge_ [Yankees](http://newyork.yankees.mlb.com) fan I am? [Derek Jeter](http://en.wikipedia.org/wiki/Derek_Jeter) is one of the all-time greats.

![Yankees_logo](http://blog.codinghorror.com/content/images/uploads/2012/10/6a0120a85dcdae970b017ee4727df7970d-800wi.png)

I realize that the devil is in the details, but for the most part what I want to see in a **Markdown Standard** is this:

  1. A standardization of the existing core Markdown conventions, [as documented by John Gruber](http://daringfireball.net/projects/markdown/), in a formal language specification. 
  2. Make the three most common real world usage "gotchas" in Markdown choices with saner defaults: intra-word emphasis (off), auto-hyperlinking (on), automatic return-based linebreaks (on). 
  3. A formal set of tests anyone can use to validate a Markdown implementation. 
  4. Some cleanup and tweaks for ambiguous edge cases that exist in Markdown due to the lack of a formal specification. 
  5. A registry of known flavor variants, with some possible future lobbying to potentially add _only_ the most widely and strongly supported variants (I am thinking of the GitHub style code blocks which are quite nice) to future versions of Markdown. 

And that's it, really. I don't want to extend Markdown by adding tons of crazy new functionality, or radically change the way it currently works, or anything like that. I'd be opposed to such changes. I just want to solidify and standardize the simple, useful version of Markdown that is working so well for everyone right now. I want there to be an unambiguous, basic standard that everyone using Markdown can expect to work in the same way across all web sites in the world when they begin typing.

![Markdown mark](http://blog.codinghorror.com/content/images/uploads/2012/10/6a0120a85dcdae970b017d3cfd6d03970c-800wi.png)

> _[Markdown mark](http://dcurt.is/the-markdown-mark)_

I'd really prefer not to fork the language; I'd much rather collectively help carry the banner of Markdown forward into the future, **with the blessing of John Gruber and in collaboration with other popular sites that use Markdown.**

So … who's with me?

[advertisement] [Stack Overflow Careers](http://careers.stackoverflow.com/) matches the best developers (you!) with the best employers. You can search our [job listings](http://careers.stackoverflow.com/jobs) or [create a profile](http://careers.stackoverflow.com/cv) and even let employers find you. 
