# Keep Calm and Hide Your Code: Code Encapsulation

_Captured: 2017-01-31 at 23:55 from [dzone.com](https://dzone.com/articles/keep-calm-amp-hide-your-code-code-encapsulation?edition=266901&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-31)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114902%26PluID%3D0%26ord%3D%5Btimestamp%5D).

In this article, I'd like to open your eyes on code encapsulation and, hopefully, you will enjoy the five tricks I will give you when it comes to hiding your code.

A few years ago, when I was still a college student during my senior year, I had one of the most thrilling and eye-opening experiences at my first ever real job as an intern in the software department in a research and development company in the chemical sector.

The company, with a battery of patents in the back pocket, would design and manufacture complex equipment for chemical analysis. Equipment with a price tag of a Ferrari, yet only a two-digit number of them shipped every year -- because of the exhaustive testing and flexibility needed to meet final customer specifications and the need to manually build for most of the parts.

I was held in a meeting because of a breakdown of one of the devices, with pictures of the internal parts sent by the customer, documentation, and reports on that particular unit, and the readings of the last weeks from all the sensors the machine had. It was a protocol meeting before sending the repair team. It wasn't my first meeting, yet this was different, as the founder of the company was presiding over it -- one of the brightest people I've ever met.

After a long discussion, after all sorts of suppositions were made, after every pixel of every photograph was checked, it was the boss' turn to speak. He'd barely spoken during the whole meeting. The room went quiet, and all eyes pointed to him. Completely silent, with his arms crossed, he slowly leaned back in his chair. After a pause, he said:

"This is not what our customer wants. The customer wants to open the side cover, check a few lights, find the broken part, remove it, order a new one, install it back, and make it work again. It needs to be more modular."

That simple sentence gave me a lot to think about. That is the behavior we expect of more and more things that surround us. Think of your computer, for instance, and how easy it is to upgrade it. Probably soon enough, the same thing will happen with smartphones. And this happens not only with your hardware, but also with your code. With good code encapsulation, with classes of high cohesion between data and behavior, it's easier to read and extend.

Most of you have probably seen some old spaghetti code such as an endless PHP file that prints HTML and JavaScript, or some more modern one using an MVC framework, like Laravel, for example, with controllers of thousands of lines and endless functions. Maintaining such code can be a [real nightmare](https://www.apiumtech.com/blog/of-gods-and-procrastination-agile-management/). But do you avoid falling into these situations? My advice is to always try to hide your code as much as you can. Hide code details and internal complexity. Make it modular. Convert it to separate black boxes, each one with a clear purpose. It will make it easier to substitute one module with another and build new functionality re-using existing components. But how exactly?

## **5 Tricks for Code Encapsulation**

### Hide Class Attributes, Make Them Private

Use a well-defined public interface instead. If others are aware of the implementation details of your class, and need to access your attributes, then there is logic that should've been encapsulated in your class spread across only-god-knows where. Any change in that class requires you to review all its uses.

Therefore, instead of:

How about:

### Hide Code Details Inside a New Function

Have a piece of code that repeats in multiple places? Hide code details inside a new function. Use the function instead. With code encapsulation, you keep your code DRY. It will be easy to reuse later, and the refactor and maintenance will be easier.

### Hide the State

Don't use global variables, as it will break encapsulation and make the sections that use them dependent, as they would rely on the state of those variables.

### Break Them Into Smaller Sections

Have large methods with nested sections and comments? Break them into smaller ones, extract code, and hide your code in private methods. Normally a comment in your code would be a good name for a private function. Reviewing a function of 500 lines can make a developer cry. Reviewing a function that calls five small functions with self-describing contracts is more pleasant.

### Give Your Methods Only One Job

If a method has a single responsibility, it will keep it short and focused on a single task, and the hidden code it contains will be behind the interface of the class. If you can't give only one responsibility to a function, then the class has low cohesion, and it should be separated into two different ones.

These simple tricks will help you have a more flexible code. In other words, always keep the cohesion high, and the coupling low. The first one will assure that the data and behavior are well-placed in a class, and the methods perform all the logic using only and most of the data inside the class. The second will ensure that the interdependence of the modules won't be a problem when modifying or reusing code.

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=http%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20114901%26PluID%3D0%26ord%3D%5Btimestamp%5D).
