# Swift Holy War: Comments are not an Anti-pattern

_Captured: 2016-11-03 at 19:32 from [ericasadun.com](http://ericasadun.com/2016/11/03/swift-holy-war-comments-are-not-an-anti-pattern/)_

Got into a debate yesterday about [this write-up](http://www.strongopinionsweaklytyped.com/blog/2014/08/27/beware-the-siren-song-of-comments/) by developer Andrew Warner. His "_Beware the Siren Song of Comments_" suggests that developers delude themselves because comments detract from code quality:

> Comments decay. They aren't compiled, and they'll never get executed at runtime. If they become out of date or incorrect, [no test is going to fail](http://genius.com/4069108/Andrew-warner-beware-the-siren-song-of-comments/No-test-is-going-to-fail) and no user is going to complain. Programmers work around them out of fear that "somebody might need this comment or it might provide some value in the future", pushing them along far after they're useful (if you can even argue that they were useful in the first place).

His recommendation?

> [Y]ou don't have any excuse to write comments. Give these methods a try, and I promise you'll have a cleaner codebase that's easier to maintain.

I don't claim that comments should counterbalance bad design decisions like poor naming or flawed algorithms. I do believe they play an important role in good coding practices -- whether or not your code is meant strictly for internal use or to be consumed as APIs.

As I discussed [on this blog](http://ericasadun.com/2016/09/12/reconciling-past-you-with-future-you/) a few weeks ago, there's a big difference between the you writing code and "future you", your team, and anyone else reading code. Here's what I have to say about commenting in _Swift Style_:

> Comment, comment, comment and while you're at it, write tests. Tests can save you the whole "What I was doing here?" because you can just look at what is broken and what you expected to work." It's better to write less code and make up that time by explaining the code you did write better.
> 
> Sure, it helps to leave in a "TODO:" where it counts ("the performance is really bad here") but while you're at it, try to leave a few ideas about what exactly is going wrong, and what hypotheses you have rolling around your soon-to-be-extinct neurons. Past you understood things. Future you is clueless.
> 
> It always costs less to fix things in the past because you've invested in uploading the full design into your brain. Re-upping that design and getting back up to speed involves huge penalties.

Comments can explain the non-obvious, the tricky, or the counter-intuitive to a reader: _This is intentional. This thing affects that thing. This data is not validated at this stage. Responsibility for this process now passes to this delegate. _Comments enable you to establish what your assumptions are at which points in code and they allow you to comment on design qualities.

Comments create a record of intent. They may mention approaches that were tried and why they were abandoned. They may discuss how design decisions came to be -- what paths were explored and why some of those paths weren't chosen in the end.

Comments allow you to colocate thoughts with the code they refer to. Commit messages are helpful but I don't think a commit message is the proper place to document workarounds or unexpected behavior. Plus version control history may not travel with source code, if the code is reused in another project.

Comments provide a bread crumb trail of design decisions that aren't kept in working memory and cannot be intuited just from reading code or scanning tests. Unexpected complexity is one of the things you'll want to comment about. In fact, commenting on the unexpected is important because the alternative is essentially a bug.

Structured comments add [another layer of utility](https://itunes.apple.com/us/book/swift-documentation-markup/id1049010423?mt=11), supporting API consumption. Markup allows these special comments to automatically convert into highly formatted local documentation providing another set of readers beyond code review, debugging, maintenance, and enhancement.

Comments don't just paper over bad design and coding. They document a process of making code right, supporting future reading and modification. Good comments reduce the mental effort needed by readers each time they review your source, enabling them to focus more on specific tasks like "how to I add this feature" rather than "what the hell was going on here". While good code _can_ at times be "self documenting", that doesn't mean it always _is_ (or even _usually_ is) self documenting.

As stepping stones to "past you", good comments document what you were thinking and why you did things the way you did. Your past design decisions should never be a mystery or a burden placed before future readers of your code no matter how brilliant or insightful you expect them to be.

[ Tweet this Post ](https://twitter.com/share?text=Swift%20Holy%20War%3A%20Comments%20are%20not%20an%20Anti-pattern&url=http://ericasadun.com/2016/11/03/swift-holy-war-comments-are-not-an-anti-pattern/&counturl=http://ericasadun.com/2016/11/03/swift-holy-war-comments-are-not-an-anti-pattern/)
