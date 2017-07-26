# The OpenSource Experience

_Captured: 2015-12-06 at 01:01 from [alisoftware.github.io](http://alisoftware.github.io/oss/2015/12/05/the-opensource-experience/)_

As you all know, [Swift just went OpenSource earlier this week](https://swift.org). That's huge news for the community, and there have been plenty of posts about that already explainging what a game changer that is.  
And now for something completely different™, today I'll take this opportunity to talk about my own experience with OpenSource and how contributing to OSS can be very enlighting for everybody.

## Introduction: The big deal with Swift OSS

So the big news of this week is obviously Swift now being OpenSource. Apple went way further that anyone expected there, releasing the **full GIT history** of [Swift source](https://github.com/Apple), but also the source of **other tools** like `lldb` and the REPL, revealing they are working on a [Swift Package Manager](https://swift.org/package-manager/), and making everything to [build a better community](https://swift.org/community/)!

That's a very welcomed move from Apple and even if they announced at the WWDC'15 that this were comming, I'm almost certain that nobody expected it to be that huge, and that well done and handled.

But what's all this fuzz about OpenSource, why is it so great? Instead of talking about what Swift being OpenSource can bring to all of us -- there is already plenty of blog posts on the net about that -- let me tell you my story with OpenSource and how it changed my way of thinking. Hopefully you'll get why I love it so much!

## Hello GitHub

So, my first experience with OpenSource was just writing some iOS libraries and publishing some code on GitHub, probably like a lot of you already. At first, I didn't really think "I'm doing OpenSource", but just "hey, I have written some nice code, let's push it on GitHub because that's nice and easy to share".

A lot of my first projects on GitHub were actually just tests, like little toy projects I wrote to experiment new concepts or new libraries. I'm super curious and love to experiment new frameworks or design patterns or ideas, so I was only playing around.

Then came my first real libraries that I put on GitHub to really share with others. I think my first pods were `OHAlertView` and `OHActionSheet`. But then came `OHHTTPStubs`.

## Share some love

So here is how it all started for me: after reading [a blog post about `NSURLProtocol`](http://www.infinite-loop.dk/blog/2011/09/using-nsurlprotocol-for-injecting-test-data/) I wanted once again to toy around and see how we could generalize the idea by making it customizable. By the time I wrote the first lines of that GitHub project, that was still a Proof of Concept. But then I improved it, transforming it into a stand-alone component… and people began to star the GitHub repository 🌟

I really didn't see the success of `OHHTTPStubs` coming, and **that brought me a nice feeling and some confidence**. Seeing that repository becoming more and more popular was heartwarming, realizing that this code helped people and that they actually use it in their projects made me very happy. That was not just a toy project anymore, I was helping the community.

> By doing OpenSource projects and releasing your libs to the community, you're receiving love in return ❤️. And that's what matters the most.

The thing to remember here is: don't do OpenSource projects just to be the popular kid. Do OpenSource projects because it's nice and rewarding to share with others. With `OHHTTPStubs` being OpenSource and becoming popular, **I gain the joy of knowing my work was used by others**, but also contributions from other people that helped a lot improving the library code and its feature. Teamwork is really great!

## Don't be afraid to contribute

After a while, I wanted to give back to the community. As I used [CocoaPods](https://cocoapods.org/about) a lot in my development projects, I wanted to help on that front.

I can't find back the first Pull Request I did on CocoaPods, but I remember quite well that at that time I was not really confident because:

  * CocoaPods seems like a huge project and I was kinda lost in it, and didn't know where to start
  * **I didn't know how to do Ruby _at all_**. I was thinking that my code would probably look ridiculous compared to the Grand Masters working on CocoaPods

So what I did is I started small, with Pull Requests about documentation typos, and helping improve the Guides using my experience as a CocoaPods user, to give feedback and avoid other people to have the same issues that I had when I first started using CocoaPods. It didn't seem much, but at least I was helping.

> Every little helps. And even sometimes helps a lot. Even Pull Requests on documentation and guides are important. 📚

As Chris Lattner says himself:

![Chris Lattner Tweet](http://alisoftware.github.io/assets/tweet-clattner-contribute.png)

> _[Chris Lattner Tweet](https://twitter.com/clattner_llvm/status/673162286127714304)_

## My first steps in a foreign code and language

Back after I first contributed to CocoaPods, it was time for me to try and fix some small bugs that affected me in the CocoaPods code base. Even not knowing how to code in Ruby, I started making small fixes in the CocoaPods source code. Ruby is very easy to understand and read (as easy as Swift) so changing bits in existing code was simple enough, even if I was scared of breaking everything.

Those first contributions were very welcomed by the team. **Seriously. The CocoaPods Team is really awesome** and made me feel welcome even if I wasn't totally confident at first about the modifications I did in their code.

But instead of telling me my code was not good, **they told me how to improve my Ruby skills and how I could improve my code in better ways**. They even helped my setting up my Ruby environment (as I had problems running the Unit Tests and understanding how this was organized at first)! It was very heartening and encouraging and made me want to do more.

> When working on an OpenSource project, the community is very important. A welcoming community -- that follows a nice code of conduct and helps newcomers -- changes everything. Understanding that not everybody has the same skills as you but wants to improve is way better.

As a matter of fact, I literally learned to do Ruby by contributing to CocoaPods, learning along by doing Pull Requests.

## All about people

One thing that can seem quite unsignificant but which is in fact quite important is also attribution. The simple fact that once I did my first Pull Requests on CocoaPods, I had my name added in the project's `CHANGELOG` was really nice.

It probably would have been nothing for any long time contributor on the project, but at that time as I was new as a CocoaPods contributor, having my name there was quite something, even if for a very little feature, it kinda made me proud.

> Don't be afraid to ask questions and ask some help to long-time contributors. Sure they'll take some time to help you and even if that takes time, this is not wasted time as it will make you improve, and contribute more. The more the merrier!

Time went by and I contributed more and more to CocoaPods, and at some point I was invited to join the Core Team, having even my name in CocoaPods's about page. That was quite another step for me!

Working on CocoaPods was also the occasion to meet awesome people and learning a lot from them, both in the virtual world via GitHub, Slack and all, but also IRL in conferences. That's one really great way to talk with other developers from all around the world.

## Being nice is nice

I think that being welcomed that way in the CocoaPods community helped me a lot doing much more OpenSource. The things I loved by working on CocoaPods is that they don't judge your skills and try to help instead of throwing you under the bus if you did something wrong, and they help you improve.

But participating in a community is sometimes hard. In GitHub everybody can create a new issue and make a Pull Request, but some people just open issues with harsh language like "this doesn't work, your project sucks" and this is not helping. I can understand that it can be frustrating when something doesn't work, but contributors have to keep in mind that:

  * The OpenSource project is brought to you free of charge
  * It's maintained by people taking on their own free time to write the code and improve it
  * Time is not infinite and people working on OSS can't test every configuration out there, even if we try to cover as much as possible
  * Being harsh doesn't help. Providing a way to reproduce the issue and explaining what you tried helps.

Orta would say, [Being Nice is Nice](https://realm.io/news/altconf-orta-therox-being-nice-in-open-source/). And that's also why Code of Conducts are important, to let people know how to be nice with people but more importantly that you are welcoming to everyone -- as long as they are nice to each other.

And you know what? That's also a way to participate in OpenSource and share some more ❤️.

> Opening descriptive issues on GitHub with ways to reproduce the problem is as important as writing Pull Requests in Open Source. Filing bugs or suggestions is also contributing, as long as it's constructive.

## Welcoming others

Once I was familiar with the CocoaPods project, I did also help newcomers to CocoaPods and tried to be as helpful as people were to me when I started.

But then I started having new projects of my own gaining popularity, like [SwiftGen](https://github.com/AliSoftware/SwiftGen) and [Dip](https://github.com/AliSoftware/Dip), and that now takes me quite some time (that's probably why I started spending less time on CocoaPods lately).

That's also when I saw the other good side of OpenSource. To my surprise, Newsletters and Tweets started to talk about those projects quite quickly, and those projects also gained popularity quite fast, generating a lot of demand and issues submitting ideas to improve those. I wasn't able to keep up alone.

That's when [Ilya](https://github.com/ilyapuchka) started to [contribute a lot to Dip](https://github.com/AliSoftware/Dip/graphs/contributors), adding a lot of Pull Requests that fixed bugs or add a lot of nice features, and I decided to give him Push Access to my repository.

That was the first time I gave someone I didn't know the push access to one of my public repositories. That might be frightening at first, because you never know if other people have the same idea as you about the project, if they won't mess it up, or if they have other coding habits and a way of writing code that don't match yours, and more importantly you don't want them to break everything.

But I don't regret that decision at all, and given my background in OpenSource I actually didn't even hesitate much to give them push access. It felt really great to trust someone, and in the end Ilya is doing an amazing job and brings way more features in `Dip` that I ever would've. And it's always interesting to have a fresh perspective on your code and what you're building!

> Trusting people on your project is also important and very heartwarming. You'll rarely be disappointed by trusting people in OSS as it's all about sharing and helping each other.

## Conclusion

  * Open Source is wonderful
  * Gives you opportunity to meet wonderful people
  * Sharing is very gratifying
  * Don't be ashamed by your skills or shy to participate on an OpenSource project
  * Every little PR or issue counts, Documentations PRs and well documented issues with ways to reproduce are as important as code contributions.
  * Nice things happen when being nice
  * You should all do [Open Source by Default](https://code.dblock.org/2015/02/09/becoming-open-source-by-default.html)

Well, now that I've talked about my experience in entering the OpenSource world, I hope I made you want to do more OpenSource and participate!

_Of course I'd welcome your contribution of one of my own OpenSource project, especially on [SwiftGen](https://github.com/AliSoftware/SwiftGen/) where there is tons of great ideas to implement to improve the tool_ 😉
