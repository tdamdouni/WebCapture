# Source of the famous “Now you have two problems” quote

_Captured: 2015-12-11 at 09:54 from [regex.info](http://regex.info/blog/2006-09-15/247)_

As I mentioned in my [previous post](http://regex.info/blog/2006-09-14/246), my _[Mastering Regular Expressions_](http://shop.oreilly.com/product/9780596528126.do) book was just [reviewed on Slashdot](http://books.slashdot.org/article.pl?sid=06/09/13/147213). One thing that struck me in reading all the resulting comments was the (several different copies of an) apparently famous quote that goes something like:

** Some people, when confronted with a problem, think   
"I know, I'll use regular expressions." Now they have two problems. **

It's apparently quite well known, so it floors me that this is the first I've seen it. Despite being a manifestation of the ignorance discussed in my [previous post](http://regex.info/blog/2006-09-14/246), I can certainly appreciate it for its wit.

This quote is generally attributed to [Jamie Zawinski](http://www.jwz.org/) (an early Netscape engineer) from a post on the **comp.lang.emacs** Usenet newsgroup. Unfortunately, there's never been a **comp.lang.emacs** newsgroup, which renders the whole attribution suspect. Oddly curious about it, I did some digging...

It turns out that the source of the mistaken comp.lang.emacs reference was a May 1998 **comp.lang.python** [post by Fredrik Lundh](http://groups.google.com/group/comp.lang.python/msg/85d15c93e56c5236?hl=en), who used it as a cute quote in his [sig](http://en.wikipedia.org/wiki/Signature_block). He's a prolific writer so the sig appeard wide and far, and many people picked up on it and started using it themselves, and the fame of the quote (along with an incorrect attribution) spread.

But it was indeed Jamie Zawinski who first said it, in a Usenet post on August 12, 1997. Unfortunately, it seems that Google Groups, which holds a repository of Usenet postings going back a thousand years, does not have this particular post in its database. If it would, the post would be at the end of this [broken link](http://groups.google.com/group/alt.religion.emacs/msg/b59f4a602fb68f0a?hl=en).

[**UPDATE Feb 2013:** it seems now that the link is no longer broken; Jamie's original post is there]

Actually, it seems that none of Jamie Zawinski's posts in the threads that spawned from this initial post are in Google's database. This is quite odd. I have been able to find parts of his posts quoted in the replies of others. It was a heated thread, so there's plenty to go on.

There was [a thread](http://groups.google.com/group/comp.emacs.xemacs/browse_frm/thread/b21dbf075be84ab/989698966fb25e7a?hl=en#989698966fb25e7a) in **comp.emacs.xemacs** and **alt.religion.emacs** in which the idea of embedding Perl into Emacs was proposed. (My first-thoughts comment on this idea is that it's fairly silly, since Emacs already has a powerful lisp interpreter in it. Lisp is odd, though, in that it's a vastly more regular language than Perl, yet arguably less readable. But I digress...).

The main goal of the guy making the original suggestion was to get better regular-expression handling into Emacs. Perl treats regular expressions as first-class language features, making them a breeze to work with. They're not that hard to work with in Emacs Lisp, but in any case, Emacs's regular expressions are much less powerful and have a syntax that's even less readable than that of Perl's, if that's possible. (If you look up "toothpicks, scattered" in the index of my book, it brings you to a page about Emacs regular-expression syntax. :-))

Two things must be understood about Jamie Zawinski when evaluating his comments about this idea: he despised Perl, and he spent a nontrivial chunk of his life tending to Emacs and its lisp system, to the point that he [considered it a religion](http://www.jwz.org/hacks/). I can understand and appreciate having that kind of passion about something. In any case, talk about embedding Perl into Emacs would be heresy of the highest order.

It seems that during the course of this thread, Jamie referenced a three-month-old [post by Kelly Murray](http://groups.google.com/group/comp.lang.functional/msg/84763c6d9185178b?dmode=source&hl=en) in which Kelly sarcastically suggests something even more outlandishly silly (treating all data simply as a stream of bytes). Apparently, Jamie didn't realize that it was meant to be humorous or sarcastic. Combining this with the idea of embedding Perl into Emacs just for its regular-expression handling, and it was enough to put him over the edge, and Jamie lashed out:

**Jamie Zawinski <jwz@netscape.com> wrote on Tue, 12 Aug 1997 13:16:22 -0700:**
    
    
    You are trying to shoehorn your existing preconceptions of how one
    should program onto a vastly different (and older, and more internally
    consistent) model.  I suggest your time would be better spent learning
    and understanding that other model, and learn to use it properly, and
    learn what it can and cannot do, rather than infecting it with this new
    cancer out of ignorance.
    
    The notion that everything is a stream of bytes is utterly braindead.
    The notion that regexps are the solution to all problems is equally
    braindead.
    
    Just like Perl.
    
    Some people, when confronted with a problem, think “I know,
    I'll use regular expressions.”  Now they have two problems.
    

Jamie really disliked Perl, and in the ensuing discussion had a few other comments about it. In this [snippet](http://groups.google.com/group/comp.emacs.xemacs/msg/3cd6d41ace570ac9?hl=en&) he responds to a "what's wrong with Perl?" question:
    
    
    > What's wrong with perl?
    
    It combines all the worst aspects of C and Lisp: a billion different
    sublanguages in one monolithic executable.  It combines the power of
    C with the readability of PostScript.
    

(I also appreciate that last sentence for its wit.)

A few days later it [became clear](http://groups.google.com/group/alt.religion.emacs/msg/991308e21103bb76?utoken=y6jr3TIAAAAHNAhXg1IfVuilpJeccStLGAmrE6vypPa-ZuYI0HTVtv3oCXeNlLzgllDXfF-UfC4p_tUz1V7g4RazWzRxYDBn) that it's not only Perl itself, that he's upset with, but how he perceives it's often used:
    
    
    Perl's nature encourages the use of regular expressions almost to the
    exclusion of all other techniques; they are far and away the most
    “obvious” (at least, to people who don't know any better) way to get
    from point A to point B.
    

Mind you, he's keeping a fair mind about himself, allowing that Perl has some merit:

I find that the next statement is quite telling:
    
    
    Maybe Java will save the day, once someone straps a Java front end onto
    the gcc back end.
    

Later, [he says](http://groups.google.com/group/comp.emacs.xemacs/msg/2d0462d725c19d16?hl=en):
    
    
    The heavy use of regexps in Perl is due to them being far and
    away the most obvious hammer in the box.
    
    The heavy use of regexps in Emacs is due almost entirely to
    performance issues: because of implementation details, Emacs
    code that uses regexps will almost always run faster than
    code that uses more traditional control structures.
    
    Based solely on how lame the syntax is, and how generally
    unmaintainable regexp-based code is, Perl would be very close
    to the bottom of my list of choices for most tasks.
    

I'd agree with that first paragraph if the "most obvious hammer" phrase were changed to "most appropriate hammer", because Perl is often used for advanced text processing, and that's exactly where regular expressions shine. That being said, I've written plenty of system tools in Perl that are mostly or completely devoid of regular expressions. I use them when they're the best tool, and don't when they're not.

Anyway, it was a colossal waste of time for me to track this all down (and for you to read this far :-)), but once I got on the trail it was hard to get off.

As cute as the "now you have two problems" quote is, it seems that Jamie wasn't the first to come up with the idea. The same quote (but with **AWK** rather than **regular expressions** as the punch line) shows up in the sig of [John Myers post from 1988](http://groups.google.com/group/comp.sys.ibm.pc.rt/msg/8c9ba376ae1c250c?hl=en), where he credits a "D. Tilbrook" for it:

** "Whenever faced with a problem, some people say `Lets use AWK.'   
Now, they have two problems." \-- D. Tilbrook **

I've also seen the AWK quote credited to a "Zalman Stern" (in this 1993 [post of quotations](http://groups.google.com/group/alt.quotations/msg/dcee3d3682dd0470?hl=en) on **alt.quotations**). As Mark Bessey notes in a [post on his blog](http://codemines.blogspot.com/2006/08/now-they-have-two-problems.html), it's an all-purpose joke.

I can imagine that it was first used in by servicemen during WW2, along the lines of "Some people think `Let's ask the officers'....".

**UPDATES:**

**January 10th, 2007**: this post made it high enough on [reddit](http://reddit.com/) that it made my pageview jump by a factor of 10, and in doing so, brought in comments with more details on the history of the phrase than I had been able to unearth myself. Excellent! See the comment section for details.

**January 15th, 2007**: Jamie Zawinski himself [commented](http://regex.info/blog/2006-09-15/247#comment-3085) on this post.
