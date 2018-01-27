# 5 Reasons Bad Techies Will Give for Not Using an Application Framework

_Captured: 2018-01-13 at 19:11 from [dzone.com](https://dzone.com/articles/5-reasons-bad-techies-will-give-for-not-using-an-a?edition=352117&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-13)_

[Learn how to build modern digital experience apps](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) with Crafter CMS. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).

I know what you are thinking, in this day and age who would not want to use a framework? But if you have enough confirmation bias, the internet will provide you with [evidence](http://www.catonmat.net/blog/frameworks-dont-make-sense/). I have met at least a couple of tech leads who denied their teams the comfort of using a robust framework. One of them worked at a company which had raised more than $9M in funding rounds. Don't make the mistake of thinking that companies that allow their leads to perpetuate such stupidity will quickly get lost into oblivion. Well, they eventually do but not without burning a lot of their investor's money. Without further ado, if you are being sold this idea of not using a framework, here are the top 5 reasons that you will hear and the subtle undertones of incompetence that they carry.

### 5\. Frameworks Are Complicated

This is one of my favorites. You would hear phrases like, "there is too much magic happening in there" or "setting it up will take a lot of time" or "it works while it works, but when it stops..." etc. This person is evading the responsibility of understanding the framework thoroughly. The person advocating to not use a framework because it's complicated probably never understood the difference between _Complex_ and _Complicated_. Of course, frameworks are complex, because they are created to tackle complex problems and reduce the complications which would otherwise result from bad design. They don't even realize that there is a good chance they will indeed end up with a bad design because [only 1 in 50 developers are able to define good abstractions](https://sourcemaking.com/antipatterns/the-grand-old-duke-of-york). In short, you are being told, "I can't wrap my head around this complexity yet, and I don't think I will ever be able to make this work. So I'd rather let the junior developers toil away barebones. When they are stuck, it'll be their fault."

Try stating these aphorisms to convince your boss.

  1. A system should be as simple as possible, but no more.
  2. Simple is better than complex. Complex is better than complicated.

### 4\. Frameworks Inhibit Learning

Another gem. A bad tech lead will try to convince you that you need to learn what happens under the hood. They never knew that there is such thing as a good [Abstraction](https://en.wikipedia.org/wiki/Abstraction_\(software_engineering\)). Their priorities are misaligned because they think that in order to use something, you need to be aware of each and every implementation detail, regardless of how ingenious or mundane it may be. They also fail to understand that by [reinventing the wheel](https://en.wikipedia.org/wiki/Reinventing_the_wheel) they are making a huge dent on their company's finances because reinventing the wheel requires lots of resources which cost money and you end up with a buggy, low-quality product which costs even more money. They may be suffering from [Not Invented Here](https://en.wikipedia.org/wiki/Not_invented_here) syndrome.

### 3\. No Framework Can Cater to Our Special Needs

Citing this problem requires a some level of grandiosity and myopia as well. Good frameworks are designed to be as generic as possible. Not only do they cater to a wide audience, the makers have probably already figured out your future needs that you yourself might not be aware of. Because hey, roughly 90% of software projects have the same horizontal concerns. A good framework could possibly have a decade of experience coming from a wide variety of contributors belonging to different domains distilled into code. It's unlikely that you bumped into a special case which is not already addressed. Even if that happens, most good frameworks will allow you to extend their functionality to custom fit your special requirement.

### 2\. Using This Framework Will Require Me to Use X

Good frameworks allow you to use as much of it as you want and doesn't get in the way when you don't want to use its features. Take, for example, [Spring](https://spring.io/) for Java and [Symfony](https://symfony.com/) for PHP. You can use any of the features provided by these frameworks independently, for example, Routing, or ORM, or Dependency Injection or Security and use something entirely different for other stuff. People holding this opinion do not peruse the documents, they just skim through it and assume that whatever they read under the same domain name is the lowest common denominator and cannot be broken down further.

### 1\. Performance

And the top spot goes to... "Using frameworks results in bad performance." If only I got a dollar every time someone blamed the framework for their incompetence. Frameworks, ideas, dependency injection, annotations get rejected because of non-existent performance issues. People often cite this reason when all other of their reasons fail. This one is a very good conversation finisher. Since you've never used a framework, you couldn't possibly know what effects it will have on performance. Even if someone says this from personal experience, I am unlikely to believe them. Chances are, no one tried to figure out the bottleneck and since frameworks can't advocate for themselves, they became a convenient scapegoat. Performance overhead caused by good quality frameworks is only ever an issue when memory is at a premium, for example, in embedded systems. Modern day computers (including cell phones and servers) provide copious amounts of RAM at a very cheap price. Whenever someone tells you that using frameworks on web/mobile/desktop applications cause performance issues, ask them for benchmarks. If the person has really taken time to locate the bottleneck, they would love to fire up a quick benchmark and claim bragging rights for taking down that famous framework. Otherwise, they are living in a bubble. Or do them one better by presenting them with the benchmarks. With good frameworks, performance overhead will be negligible. On the other hand, the opposite might be true. Custom code might be less performant since a good framework is used by many people with varying needs, thus it is audited more frequently and thoroughly.

## Conclusion

The idea of not using a framework stems from a superficial analysis or sloth. Do not fall into this trap unless you count yourself in the ranks of [Linus Torvalds](http://harmful.cat-v.org/software/c++/linus), in which case, be like Linus. Lastly, let me end with this quote.

> Let "performance reasons" be the last resort of all sleeping [wo]men. 

Crafter is a [modern CMS platform for building modern websites](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) and content-rich digital experiences. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).
