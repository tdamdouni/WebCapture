# Making the wrong arguement about Markdown

_Captured: 2015-11-07 at 12:58 from [mygeekdaddy.net](http://mygeekdaddy.net/2014/10/08/making-the-wrong-arguement-about-markdown/)_

It's funny how people keep trying to redefine what Markdown is, when the original definition is so simple:

> Thus, "Markdown" is two things: (1) a plain text formatting syntax; and (2) a software tool, written in Perl, that converts the plain text formatting to HTML. 

This is the definition given by John Gruber, one of the creators of Markdown. This is the definition that has stood since Markdown was introduced on 17 Dec 2004. In the very next sentence after defining what Markdown is, Gruber gives [a syntax page](http://daringfireball.net/projects/markdown/syntax) "for details pertaining to Markdown's formatting syntax." But over the past couple of months there's been quite a dust up on what people think Markdown is and what some [people think it should be](http://commonmark.org). The latest is an article in Ars Technica, written by Scott Gilbertson - [Markdown throwdown: what happens when FOSS software gets corporate backing?](http://arstechnica.com/information-technology/2014/10/markdown-throwdown-what-happens-when-foss-software-gets-corporate-backing/2/).

Scott goes into the history of Markdown and why a lot of us think it's an important development on how we work and write. In this part I wholeheartedly agree. Gruber has created a tool that allows me to create and save my work in simple text files and convert them into a [multitude of other formats](https://itunes.apple.com/us/app/marked-2/id890031187?mt=12&uo=4). But then Scott argues that "[t]here are bugs, but worse there are ambiguities and edge cases where it's unclear what should happen." He goes on to argue with the variety of editors and parsers that Markdown, a user won't get what they expect from one editor/engine to another. One of the points Scott raised was how the following text would get parsed by various Markdown engines:
    
    
    Here's a list of stuff:
    * item one
    * item two
    * item three
    

> In fact, depending on which fork of Markdown you use, there are 15 possible ways this snippet of Markdown might be rendered.

Here's the problem with Scott's arguement, Markdown is a tool to format plain _syntax_ into HTML. Syntax implies there are rules on how the plain text needs to be written. So let's see what happens if we follow the rules. Correcting the text to meet the syntax specifications laid out by Gruber means there should be a line break when starting a list. The updated raw text should look like this:
    
    
    Here's a list of stuff:
    
    * item one
    * item two
    * item three
    

Using the correct text, I get the following HTML output from some of my favorite Markdown editors/engines:

**Byword:**
    
    
    <p>Here&#8217;s a list of stuff:</p>
    
    <ul>
    <li>item one</li>
    <li>item two</li>
    <li>item three</li>
    </ul>
    

**Marked 2:**
    
    
    <p>Here's a list of stuff:</p>
    
    <ul>
    <li>item one</li>
    <li>item two</li>
    <li>item three</li>
    </ul>
    

**MultiMarkdown Composer:**
    
    
    <p>Here&#8217;s a list of stuff:</p>
    
    <ul>
    <li>item one</li>
    <li>item two</li>
    <li>item three</li>
    </ul>
    

**PHP Markdown 1.0.2:**
    
    
    <p>Here's a list of stuff:</p>
    
    <ul>
    <li>item one</li>
    <li>item two</li>
    <li>item three</li>
    </ul>
    

**Editorial for iOS:**
    
    
    <p>Here&#39;s some stuff:</p>
    
    <ul>
    <li>item one</li>
    <li>item two</li>
    <li>item three</li>
    </ul>
    

Huh? So besides the encoding for an apostrophe (which renders the same anyway), if I follow the rules, I get the same results.

Guess Markdown isn't broken after all.
