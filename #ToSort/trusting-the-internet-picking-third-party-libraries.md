# Trusting the Internet: Picking Third-Party Libraries

_Captured: 2017-01-30 at 22:57 from [dzone.com](https://dzone.com/articles/trusting-the-internet-picking-third-party-librarie?edition=266885&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-30)_

What every Java engineer should know about microservices: [Reactive Microservices Architecture](https://dzone.com/go?i=153025&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ). Brought to you in partnership with [Lightbend](https://dzone.com/go?i=153025&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ).

Many applications today are like the human body*: a relatively small proportion of "in-house" code, leveraged by dozens if not hundreds of third-party libraries -- everything from object-relational mappers to a single function that left-pads a string. And that leads to a conundrum: how do you pick the libraries that you include in your project? Or in other words, is it OK to download something from the Internet and make it a fundamental part of your business?

> *The reference is to the amount of bacteria and other organisms that don't share your DNA but live on or in your body. You'll often find a 10:1 (bacteria:human) ratio quoted, but see [this article](http://news.nationalgeographic.com/2016/01/160111-microbiome-estimate-count-ratio-human-health-science/) for commentary on the history and validity of that ratio (tl;dr, it's more like 60:40). 

Sometimes, of course, you don't have a choice. If you use the JUnit testing framework, for example, you are going to get the Hamcrest library along with it (and maybe you'll feel some concern that the hamcrest.org domain is no longer registered). But what criteria did you use to pick JUnit?

I was recently faced with that very question, in looking for a library to parse and validate JSON Web Tokens in Java. There are [several](https://jwt.io/#libraries-io) libraries to choose from; these are the criteria that I used to pick one, from most important to least.

  1. **Following the crowd  
**If 100,000 projects use a particular library without issue, chances are good that you can too. But how do you know how many projects use a library? For JavaScript projects, [npm](https://www.npmjs.com/) gives you numbers of downloads; ditto for Ruby projects and the [gems](https://rubygems.org/) they use. Java projects don't have it so easy: while Maven Central does keep statistics on downloads (they're available to package maintainers), that information isn't available to consumers (other than a [listing of the top 10 downloads](http://search.maven.org/#stats)). One interesting technique for following the crowd is looking in your local repository, to see if the package is already there as a dependency of another library. If you can create a dependency tree for your project, look at where the candidate lives in the tree: is it close to the root or deep in the weeds? Is it included by multiple other libraries or just one? These are all signals of how the rest of the world views the library.
  2. **Documentation  
**I believe that care in documentation is a good proxy for care in implementation. Things I want to see are complete JavaDoc and examples. For projects hosted on GitHub, I should be able to understand the library based solely on the README (and there's no reason that a non-GitHub project should omit a README, although I admit to being guilty in that regard).
  3. **Author credibility  
**This can be difficult, especially where the "author" is a corporation (although large corporations tend to do their own vetting before letting projects out under the corporate name). In the case of a sole maintainer, I Google the person's name and see what comes up. I'd like to see web pages that demonstrate deep knowledge of the subject (especially for security-related libraries). Even better are slides from a conference, because that implies tha the author has at least some recognition in the community.
  4. **Issue handling  
**Every library has issues. Does the maintainer respond to them in a reasonable timeframe? A large number of outstanding issues should raise a red flag, as should a maintainer that responds in a non-professional manner. You wouldn't accept that from a coworker (I hope), and by using a package you make the maintainer your coworker.

Once I have decided on a candidate library (or small number of candidates) I try it out for my use case. If it looks good, it becomes part of my application. One thing that I do _not_ do is dig into the library source code.

The promise of open-source software is that you can download the sources and inspect them. The reality is that nobody every does that -- and nobody could, because it would be more than a full-time job. So we choose as best we can, and hope that there isn't a dependency-of-a-dependency-of-a-dependency that's going to hurt us.

Microservices for Java, explained. Revitalize your legacy systems (and your career) with [Reactive Microservices Architecture](https://dzone.com/go?i=153026&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ), a free O'Reilly book. Brought to you in partnership with [Lightbend](https://dzone.com/go?i=153026&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ).
