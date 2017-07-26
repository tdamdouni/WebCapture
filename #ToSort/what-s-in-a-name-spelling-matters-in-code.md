# What's in a Name? Spelling Matters in Code

_Captured: 2017-03-02 at 20:50 from [dzone.com](https://dzone.com/articles/whats-in-a-name-spelling-matters-in-code?edition=273882&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-02)_

[Bitbucket](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) is for the code that takes us to Mars, decodes the human genome, or drives your next car. What will your code do? [Get started with Bitbucket today, it's free.](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)

Think back to college (or high school, if applicable). Do you remember that kid that would sit near the front of the class and gleefully point out that the professor had accidentally omitted an apostrophe when writing notes on the white board? Didn't you just love that kid? Yeah, me neither.

Fate imbues a small percentage of the population with a neurotic need to correct any perceived mistakes made by anyone. XKCD immortalized this phenomenon with [one of its most famous cartoons, that declared, "someone is wrong on the Internet."](https://xkcd.com/386/) For the rest of the population, however, this tendency seems pedantic and, dare I say, unpleasant. Just let it go, man. It doesn't matter that much.

![](http://www.daedtech.com/wp-content/uploads/2014/11/ShakespeareWriting.jpg)

I mention all of this to add context to the remainder of the post. I work as a consultant and understand the need for diplomacy, tact, and choosing one's battles. So, I do not propose something like care with spelling lightly. But I will propose it, nonetheless.

Now I know what you're thinking. How can caring about spelling in code be anything _but_ pedantic? We're not talking about something being put together to impress a wide audience, like a newspaper. In fact, we're not even talking about _prose. _And code contains all sorts of abbreviations and encodings and whatnot.

Nevertheless, it matters. When English words occur in your code, spelling them right matters. I'll use the rest of this post to make my case.

## The Intellisense Conundrum

If you use Visual Studio, no doubt you make heavy use of [Intellisense](https://msdn.microsoft.com/en-us/library/hcw1s69b.aspx). To expand, any IDE or text editor with autocomplete functionality qualifies for consideration here. In either case, your tooling gives you a pretty substantial boost by suggesting methods/variables/classes/etc based on what you have typed. It's like type-ahead for code.

Now think of the effect a misspelling can have here, particularly near the beginning of a word. Imagine implementing a method that would release resources and accidentally typing Colse instead of Close. Now imagine consuming that method. If you're used to exploring APIs and available methods with auto-complete, you might type, "Clo", pause, and see no matching methods. You might then conclude, "hey, no call to Close needed!"

In all likelihood, such an error would result in a few minutes of head-scratching and then the right call. But even if that's the worst of it, that's still not great. And it will happen each and every time someone uses your code.

## Other Manual Typing Errors

The scope of this particular issue goes beyond auto-complete functionality. Perhaps you lack that functionality in your environment, or perhaps you simply don't use it much. In that case, you'll be hand typing your code.

Now, imagine hand typing the aforementioned call to a close method. Do you instinctively type "Colse" or do you instinctively type "Close?" So what do you think will happen?

You'll expect the call to be Close and you'll type that. Then, you'll stare in disbelief for a moment at the compiler message. You'll probably do a clean and rebuild. You'll stare again for a while and squint. Then, finally, you'll smack your forehead, realize the problem, and silently berate the person who misspelled the method name.

Again, the impact remains the same. Most likely this creates only friction and annoyance. Every now and then, it may trigger a thoroughly incorrect use of a library or API.

## Anchoring Effect

Moving away from the theme of confusion when using a declared member, consider the declaration itself. During the use of a variable/method/class/etc, you _must_ spell it right before the compiler allows you to proceed (assuming a strongly typed language). With the original declaration, however, you have the freedom to spell things wrong to your heart's content. When you do this, the original copy holds the error.

That first misspelling allows for easy correction. Same goes when you've used it only a time or two. But as usage grows and spreads throughout the codebase, the fix becomes more and more of a chore. Before long (and without easy refactoring tools), the chore becomes more than anyone feels like tackling, and the error calcifies in place.

Your unaddressed spelling mistake today makes fixes more difficult tomorrow.

## Comprehension Confusion

Let's switch gears again and consider the case of a maintenance programmer reading for comprehension. After all, programmers do a whole lot more reading of code than they do modifications of it. So, a casual read is a likely situation.

Spelling errors cloud comprehension. A simple transposition of characters or a common error, such as referring to a "dependency" do not present an insurmountable problem. But a truly mangled word can leave readers scratching their heads and wondering what the code actually means, almost as if you'd left some kind of brutal Hungarian notation in there.

Taking the time to get the spelling right ensures that anyone maintaining the code will not have this difficulty. Code is hard enough to understand, as-is, without adding unforced errors to the mix.

## The Embarrassment Factor

And, finally, there's the embarrassment factor. And I don't mean the embarrassment of your coworkers saying, "wow, that guy doesn't know how to spell!" I'm talking about the embarrassment factor for the team.

Think of new developers hiring on or transferring into the group. They're going to take a look at the code and draw conclusions, about your team. Software developers tend to have exacting, detail-oriented minds, and they tend to notice mistakes. Having a bunch of spelling mistakes in common words makes it appear either that the team doesn't know how to spell or that it has a sloppy approach. Neither of those is great.

But also keep in mind that what happens in the code doesn't always stay in the code. Bits of the code you write might appear on team dashboards, build reports, unit test run outputs, etc. People from outside of the team may be examining acceptance tests and the like. And, you may have end-user documentation generated automatically using your code (i.e. if you make developer tools or APIs). Do you really want the documentation you hand to your customers to contain embarrassing mistakes?

## It's Easy to Get Right

At this point, I'm finished with the supply of arguments for making the case. I've laid these out.

But, by way of closing words, I'd like to comment on what might be the biggest shame of the whole thing. Purging your code of spelling errors doesn't require you to be an expert speller. It doesn't require you to copy source code into MS Word or something and run a check. You have tools at your disposal that will do this for you, _right in your IDE_. All you need to do is turn them on.

I recommend that you do this immediately. It's easy, unobtrusive, and offers only upsides. And not only will you excise spelling mistakes from your code -- you'll also prevent that annoying kid in the front of the class from bothering you about stuff you don't have time for.

[Bitbucket is the Git solution](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) for professional teams who code with a purpose, not just as a hobby. [Get started today, it's free.](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)
