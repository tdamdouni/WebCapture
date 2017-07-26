# Agile vs. Corporate Culture

_Captured: 2016-07-10 at 23:10 from [joebarkai.com](http://joebarkai.com/agile-software-development/?utm_content=buffer0afe0&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_
  
![Donald Knuth](http://joebarkai.com/wp-content/uploads/2016/07/donald-knuth.jpeg)

## Agile Software Development

Those of you who practice [Agile software development](https://en.wikipedia.org/wiki/Agile_software_development) will surely recognize the viewpoints expressed in the following quotations:

**_“Particularly alarming is the seemingly unavoidable fallibility of large software, since a malfunction in an advanced hardware-software system can be a matter of life and death.”_**

**_“In design you have to start at the level of organization of programs and machines, with the design of hardware and software together.”_**

**_“Begin with skeletal coding: Rather than aiming at finished code, the 46 first coding steps should be aimed at exploring interfaces, sizes of critical modules, complexity, and adequacy of the modules … Some critical items should be checked out, preferably on the hardware if it is available.”_**

You may be surprised to learn that these are not brought to you from a recent Agile conference or even from the _[Agile Manifesto_](http://agilemanifesto.org/) circa 2001. These comments are from a [NATO software engineering conference](http://homepages.cs.ncl.ac.uk/brian.randell/NATO/nato1968.PDF) that was held in Germany in 1968!

The professional community has recognized the challenges in developing large, complex hardware-software systems long before the Internet of Things (IoT), [connected car hacking](http://joebarkai.com/connected-car-security/), and refrigerators that reveal their [owner’s Gmail login](http://fortune.com/2015/08/24/samsungs-smart-fridge-hacked/) information placed the topic squarely in the limelight.

Why do software problems recognized nearly 50 years ago are still lingering in much of the software development industry today?

## Engineering or Art?

Donald Knuth’s classic book _[The Art of Computer Programming_](https://www.amazon.com/Computer-Programming-Volumes-1-4A-Boxed/dp/0321751043) was first published in 1968, the same year the NATO conference took place, and was later named one of the “[100 or so books that shaped a century of science](http://www.americanscientist.org/bookshelf/pub/100-or-so-books-that-shaped-a-century-of-science)” by the Scientific Research Society (right next to Einstein’s _The Meaning of Relativity_). Despite its dated beginning, the book is still highly regarded as the best comprehensive book on the subject of software development. And the title of the book represents the prevailing sentiment of software engineers then and today: programming is more an art than a disciplined engineering practice.

Much effort has been put into structuring the software development process and curtailing the negative side effects of treating it as “art.”

Many product development methodologies have evolved and put into practice in software development organizations.  Today, Agile methodologies, [OSLC](https://en.wikipedia.org/wiki/Open_Services_for_Lifecycle_Collaboration), [PLE](http://www.productlineengineering.com/) and other frameworks continue to contribute significantly to the state of the profession. In particular, Agile methodologies and application management (ALM) software tools address many issues related to requirement management, testing, and rapid incremental software development. Indeed, organizations that have implemented Agile, report overall productivity gain in the 20-30% range, improved IT-business alignment, and greater process agility.

But despite their undisputed success, especially in developing large-scale software-only applications, these tools alone do not seem to deliver similar results when used to develop complex embedded control software systems, such as those in cars, medical equipment, and similarly complex systems.

Project teams that have reorganized and redefined product development processes to follow Agile principles discover that these methods cannot be transferred willy-nilly to just any area in product development, nor do they work equally well in all industry sectors.

For instance, the typical Agile mantra “satisfying customers by satisfying their constant changing requirements” doesn’t translate well in industries in which each product iteration is complex, expensive, and time consuming, and often involves intricate supply chains and work in progress inventories.

Product organizations that must comply with strict safety and reporting regulations may have difficulties with Agile’s popular culture of “don’t waste time on documentation” and “we’ll patch it later.”

These differences do not bode well with a corporate culture dominated by mechanical and electrical engineers and cause friction and process inefficiencies. Plainly stated, modern approaches that focus on rapid product development and “continuous integration” are likely to work much more smoothly at Google than at General Motors.

Although we seem to focus our attention on software, the problem many organizations face is not in writing the embedded code itself.  As I mentioned in _[Why Do Software Bugs Continue to Plague Products?_](http://joebarkai.com/software-development/), developers use [knowledge-based engineering](https://en.wikipedia.org/wiki/Knowledge-based_engineering) and modeling tools that can generate software code automatically from simulation models, which reduce the amount of new code that needs to be tested and validated. Over time,  a corpus of pre-validated, reusable code will contribute significantly to higher software quality and easier integration.

The more complex and harder to tackle problem is how to integrate and test complex hardware-software systems with a growing number of options and variants. How to verify and validate complex, multi-domain control systems with hardware and human in the loop.

In a follow-up article, I will discuss the benefits of creating tight integration and process alignment between the product lifecycle management (PLM) and the application lifecycle management (ALM) software environment.  This unification of complex multidisciplinary data structures, while allowing the different engineering practices (event those that consider themselves art), forms the foundation for a more effective product development environment.

