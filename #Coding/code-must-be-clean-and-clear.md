# Code Must Be Clean. And Clear.

_Captured: 2018-09-18 at 07:36 from [dzone.com](https://dzone.com/articles/code-must-be-clean-and-clear?edition=397198&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-09-17)_

Sensu is an open source monitoring event pipeline. [Try it today](https://dzone.com/go?i=299442&u=https%3A%2F%2Fsensu.io%2F%3Futm_source%3DDZone).

There is a famous book by Robert Martin called _[Clean Code](http://amzn.to/2m7LmaA)_. The title is an obvious call to all of us: the code must be _clean_. Clean, like a kitchen, I suppose -- there are no dirty dishes, no garbage on the floor, no smelly towels. Dirt to be cleaned in a code base, according to Martin, includes large methods, non-descriptive variable names, tight coupling, lack of SOLID and SRP compliance, and many other things. Read the book, it's worth it. However, there is yet another aspect of source code. How _clear_ is it?

![](https://www.yegor256.com/images/2018/09/rum-diary.jpg)

> _The Rum Diary (2011) by Bruce Robinson_

The kitchen is clean when there is no dirt in the oven. But if it's electric panel speaks French, I can't use the kitchen. Even if it's perfectly clean, it's not clear how to use it -- that's why it's useless.

The metaphor applies to source code. Making it clean is the first and very important step, which will remove all those coding anti-patterns so many books speak about, including my favorites, _[Code Complete](http://amzn.to/2cs4cXW)_ by Steve McConnell, _[Working Effectively With Legacy Code](http://amzn.to/1SdcZ8M)_ by Michael Feathers, and _[Clean Code](http://amzn.to/2m7LmaA)_. A very important step, but not the most important one. A dirty kitchen that is useful is better than a clean one that I can't use, isn't it?

Making code clean but leaving it difficult to understand by others is the pitfall most of us fall for. By "others" I mean everybody, from our fellow in-project co-developers sitting next to us at the same desk, to imaginative junior contributors who will join the project in five years after we're all hired by Google. All of them, across this very large timeframe, must be able to use the kitchen source code without any additional help. The oven has to speak their language. Not the language of its designer.

How do you do that? How do you make sure the code is clear, not just clean?

Well, test it. Ask someone who is outside of the project to take a look at your code and tell you how clear it is. Not how beautiful your classes and code constructs are -- that's what makes it clean. Instead, ask someone to fix a bug in just 30 minutes and see how they react. You will realize how clear the code is and whether it speaks the language a stranger can understand.

This is the definition of maintainability. If a stranger can modify your code and fix a bug in less than an hour, it is maintainable. Obviously, cleanliness will help. But it's not enough. There has to be something else, which I don't really know how to describe. The only way to achieve it is to let strangers regularly see your code, attempt to make a contribution, and report bugs when something is not clear.

Making your code open and encouraging programmers to report bugs when something is not only broken but unclear -- are the best two ways to achieve high maintainability.

Sensu: workflow automation for monitoring. [Learn more--download the whitepaper.](https://dzone.com/go?i=302541&u=https%3A%2F%2Fmonitoringlove.sensu.io%2Fmonitoringeventpipeline%3Futm_source%3DDZone)

Topics:

clear code ,clean code ,maintainability ,code ,open source ,communication
