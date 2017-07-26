# 4 Tips To Code While Overcoming Our Own Psychological flaws

_Captured: 2017-05-23 at 18:54 from [readwrite.com](http://readwrite.com/2017/05/22/4-tips-for-writing-code-while-overcoming-our-own-psychology/)_

![](http://readwrite.com/wp-content/uploads/medium-publication-a1.png)

Given the choice between one piece of cake right not or a whole cake one month from now, we would probably choose the first. This [psychological bias](https://en.wikipedia.org/wiki/Time_preference) is known as "**Time Preference**" or "**Delay Discount".**

We've all seen this fine example of kids trying to hold on by not eating a marshmallow, in hope of a greater reward:

When writing code we often face the same problem, having to choose between the short-term advantages of bad practice and the long-term costs it generates.

To help rise above binging on inefficient marshmallows, here are 4 examples of **when** and **how** we can conquer our bias to gain in the long run.

### 1\. Write unit test, for your own benefit

We've all read, learned and heard about it. Tests are a fine example of something I know I should be doing for the long-run benefit, but is in my way when trying to get the job done right now.

Here are a few thoughts that can help balance this equation:

  * **Tests make sure nothing breaks when you change stuff**. That means you can make changes to your code and know on the spot if everything works. This allows you to work more freely, even right now.
  * **Tests help decide when something is "good enough".** Tests define what it means for a piece of code to "work". This can actually allow you to spend **less** time optimizing things you don't really need to optimize.
  * **Tests help write reusable code**. You can compose [larger things out of smaller modular pieces](https://addyosmani.com/first/). Slowly, you're building an impressive arsenal of reusable building blocks ready to be used at your command.

Also, take pride in the tests you write. See all the green indicators hanging over your code. Know that your practice and ethic is excellent. There is no shame in that.

### 2\. Make code reusable as you work

Writing reusable code has many long-term advantages as well as some immediate ones. Whenever possible, **[design your code to be reused**](https://addyosmani.com/first/)**.**

**Then, publish/export it to the open source**.

You don't have to spend hours publishing packages. Instead, you can [export these small components to Bit.](https://github.com/teambit/bit) Here is a [blog post](https://blog.bitsrc.io/introducing-bit-writing-code-in-the-age-of-code-components-fd8512a9aa90) by [Ran Mizrahi](https://medium.com/u/9e1ec60fcb5c) explaining why and how you can export small components in seconds.

Very quickly you can create an arsenal of reusable React or Angular components or a [nice Scope of utility functions](https://bitsrc.io/bit/utils#object). You can also share

The effort is low and Bit's community Hub web view grants a [quick view of your component's docs, tests, downloads and more](https://bitsrc.io/bit/utils/array/first), giving immediate satisfaction with your work now available to the world. You can also share it with your team or the community.

### 3\. Don't copy-paste. Just don't.

![Don't duplicate code!](http://15809-presscdn-0-93.pagely.netdna-cdn.com/wp-content/uploads/05-15-duplication-02.jpg)

A classical example. Copy pasting makes gets the job done much faster right now, but duplications make our codebase [harder to maintain](http://stackoverflow.com/questions/4226284/how-to-convince-a-colleague-that-code-duplication-is-bad) tomorrow creating an ever growing technological debt.

Every little change will have to be made in multiple places and problems will often be found only when rolling to production.

What can we do? well, don't copy-paste code! Just don't. Instead, find / create / share reusable components. [Sindre Sorhus](https://medium.com/u/37166cebf99b) released [over 1,000 tiny packages](https://www.npmjs.com/~sindresorhus). Packages are hard, and 1,000 is a lot.

We can use Bit to make this process easy (exporting components in seconds) and set an achievable goal such as making 100 components reusable. You'll find 100 or so might be enough to dramatically reduce the number of duplications, and very soon you'll see reusing is much faster than duplicating.

### 4\. Document your code, tell a story

Good documentation means that if I would get eaten by wild coyotes tomorrow, someone else will be able to replace me. Important no doubt, but not my prime concern right now. I'd rather get the job done than worry about "future me" or those who will follow me. I'll worry about them later, If I get to it in time. This kind of (very human) prioritizing leads to gaps and sloppiness in documentation.

However, there is another point of view I can embrace to help make sure I don't neglect my documentation.

Both the code itself and its documentation are representations of the logical story I'm telling. By writing down what each and every part of my code does, adding the arguments it receives, its returns, adding some examples and so on, I also get a good view of the storyline of the code I'm writing. I understand how it works as part of the bigger picture.

Good docs show that you fully understand what you're doing and how you're doing it. If the story doesn't make sense, it's better to find out through the docs than through the code itself.

At the end of the day, our willpower is a limited resource. Forcing ourselves to fight our own psychology every hour of every day is a tough battle to win. However, embracing good practice is a routine and giving ourselves immediate rewards for doing it can help us gain much more at the end of the day.

After all, one marshmallow at a time really isn't enough.
