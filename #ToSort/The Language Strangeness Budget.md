# The Language Strangeness Budget

_Captured: 2015-06-27 at 15:06 from [words.steveklabnik.com](http://words.steveklabnik.com/the-language-strangeness-budget)_

I've always loved programming languages. I've spent plenty of times with many of them, and am fortunate enough that [language design is now part of my job](http://blog.rust-lang.org/2014/12/12/Core-Team.html). In discussions about building Rust, I've noticed myself making a particular kind of argument often in design discussions. I like to call it 'the language strangeness budget'.

When building anything, it's important to understand why you are building it, and who you are building it for. When it comes to programming languages, making a language [building one is easy](https://github.com/steveklabnik/mojikun), but getting people to use it is much, much harder. If your aim is to build a practical programming language with a large community, you need to be aware of how many new, interesting, exciting things that your language is doing, and carefully consider the number of such features you include.

Learning a language takes time and effort. [The Rust Programming Language](http://doc.rust-lang.org/stable/book/), rendered as a PDF, is about 250 pages at the moment. And at the moment, it really covers the basics, but doesn't get into many intermediate/advanced topics. A potential user of Rust needs to literally read a book to learn how to use it. As such, it's important to be considerate of how many things in your language will be strange for your target audience, because if you put too many strange things in, they won't give it a try.

You can see us avoiding blowing the budget in Rust with many of our syntactic choices. We chose to stick with curly braces, for example, because one of our major target audiences, systems programmers, is currently using a curly brace language. Instead, we spend this strangeness budget on our major, core feature: ownership and borrowing.

On the other hand, if you're trying to accomplish something different with your language, purposefully blowing this budget can be useful too. I really enjoy Haskell, and for a long time, thier slogan has been '[avoid success at all costs](http://www.computerworld.com.au/article/261007/a-z_programming_languages_haskell/)':

> As for the second, I don't know if you know this, but Haskell has a sort of unofficial slogan: avoid success at all costs. I think I mentioned this at a talk I gave about Haskell a few years back and it's become sort of a little saying. When you become too well known, or too widely used and too successful (and certainly being adopted by Microsoft means such a thing), suddenly you can't change anything anymore. You get caught and spend ages talking about things that have nothing to do with the research side of things.
> 
> I'm primarily a programming language researcher, so the fact that Haskell has up to now been used for just university types has been ideal

This is Simon Peyton-Jones knowing exactly what kind of language he wants to build, and in what way. Haskell's embrace of strangeness in this sense is what makes Haskell Haskell, and actually furthers its goals.

If you include no new features, then there's no incentive to use your language. If you include too many, not enough people may be willing to invest the time to give it a try. Language designers should give careful thought to how strange their langauge is, and choose the right amount to accomplish what they're trying to accomplish.
