# Why Full Stack Matters

_Captured: 2017-03-08 at 01:03 from [dzone.com](https://dzone.com/articles/why-full-stack-matters?edition=276883&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-07)_

Check out this [8-step guide](https://dzone.com/go?i=161124&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F11431) to see how you can increase your productivity by skipping slow application redeploys and by implementing application profiling, as you code! Brought to you in partnership with [ZeroTurnaround](https://dzone.com/go?i=161124&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F11431).

Thanks for the great [feedback on my previous post](https://dzone.com/articles/full-stack-java), there were many insightful and interesting comments. I'd like to address a lot of these comments especially for those of us who don't go back to wade through the article comments in all the various channels.

To recap I discussed the silo effect within the Java ecosystem where we've fortified ourselves within a server or Android niche while JavaScript effectively took the place that Java used to occupy: a single language used everywhere. I argued that with native mobile apps, we can and should focus on a single stack that allows us great benefits.

## So What Am I Proposing?

Increase mobility and reduce the separation between the server and client teams both by using similar toolchains and by revisiting your culture.

The cultural step is probably the hardest in larger companies where teams are so separate they barely even talk or know each other. That's probably where working like this can be most beneficial.

This approach provides advantages across the board:

  * Lower costs due to shared code
  * Easier debugging/fixing of production code
  * Easier hiring/training of team members
  * Team member mobility -- as in between the client/server team in case one of the teams isn't making the schedule
  * Lower tool licensing costs if applicable

Some of these are more important to startups while others benefit larger projects but using the same language/tooling as much as reasonably possible in the stack is a huge benefit.

Here are some of the concerns people had after I published the previous article.

## Java Isn't Available for iOS, Windows Mobile, etc.

Because of this assumption, people assumed I meant a GWT-like solution, which I did not. I sometimes assume people know about [Codename One](https://www.codenameone.com/) or have looked at my bio at the top of the articles I write.

This really masks two separate doubts

  * Should I use a portability solution instead of native?
  * Why use Java and not JavaScript/Web or one of the other portability solutions?

I think that if you are a Java developer, then using Java all over the stack has a transformational effect. One of my best examples for this is Ram Nathaniel, who is probably one of the first developers using our platform.

## Ram Nathaniel

Ram picked up Codename One during the beta and built one of the [coolest apps](https://www.codenameone.com/featured-yhomework.html) ever back in 2012. It's a bit dated by now with its design, but it works well and had gained a loyal following because it's an amazing app.

Ram shipped his app on iOS and Android without a problem, but it stagnated for a couple of years. Ram, like a lot of us, didn't have the proper expertise in marketing and promotion to push the app to the prominent place it needs to be. A lot of apps die in this exact spot… Most of us think of a competitor as the worst thing that can happen to our app, and a strong competitor is exactly what happened to Ram!

A highly visible YC funded company entered the field and got a lot of visibility/PR. This sounds like a disaster right?

In Ram's case, this was a blessing!

Typically for that time, the newcomer was available only in iOS. Ram seized the opportunity, and as a result, people searching for similar solutions on Android installed his app, increasing his install base by leaps and bounds. These users shared the app socially, boosting his iOS installs as well.

While the specific app Ram built is unique, the lessons learned are not. Getting into the market fast and supporting secondary markets such as Windows Mobile is often a powerful play for smaller companies. You still need to invest in design, marketing, and the general alphabet soup as you don't want to rely on luck alone.

Ram's story also shows the value of product over form, he delivered an app that provided true value and delivered it fast. As a result, he was able to build a big gap from his competitor, and although his competitor had a couple of features Ram didn't have, in the overall count, Ram had far more features and a faster turnaround. This is doubly true for the enterprise developer who needs to deliver fast with a skeleton crew and no startup mentality within the organization.

## The Best Tool for the Job

This is a very common response to the previous article: "I'm for using the best tool for the job."

Some of this came out due to the assumption that I was talking about web and a GWT-like solution (I'm not). Our website is mostly static and uses JavaScript/HTML where necessary, but that's not core to our product. Our product connects to clients in IDEs (which are Java) and mobile clients written in [Codename One (Java).](https://www.codenameone.com/) As a side note, if you are looking for a great static site generator check out [jbake](http://jbake.org/).

When discussing general purpose languages, they are all the same more or less. You can get some benefits from using language X over language Y, but as long as we are talking about modern, safe, GC'd languages, you won't see a HUGE difference in any respect. Even if you think I am wrong with that statement, the JVM has many languages that might satisfy your taste. So when I say "Java", you can translate that to Kotlin/Scala/Jython or any other JVM language that works for you.

Using Java on the client, as opposed to Objective-C/Swift, wouldn't make a huge difference as long as I can call native code when necessary.

One of the comments discussed a 10x difference when using the wrong tool for the job. This is something I've never seen in modern GC'd languages. Normally, lines of code vary by small amounts for modern languages. Java has some boilerplate (e.g. imports), but that's not "real" code in the sense that we don't actually read it. Even with all of the imports and comments, the [Codename One Java implementation](https://www.codenameone.com/blog/property-cross-revisited.html) of [the Property Cross mobile app](http://propertycross.com/) is one of the smallest. It's got the same number of lines or less than JavaScript-based solutions.

> If you haven't heard of property cross, it's a project to evaluate cross platform solutions by pitting them in the creation of a standardized mobile app with a fixed specification 

You can see 10x improvement with domain specific languages for parsing, statistics, etc. but not in modern general purpose languages where differences are smaller. I would also argue that the lines of code metric is problematic, but judging code density is often pretty hard.

Last but not least is regulation. Back in 2003, I was consulting a bank building a major Swing app that connected to a backend WebSphere installation. One of the reasons they chose Swing over anything else was the fact that the financial algorithms on the server could be the exact same ones (same code) as the client. In the banking sector, there is a regulatory requirement to do that, so the calculations a user sees match what actually happens!

One of the happy side effects of this was how quickly we were able to beat the schedule and release something as opposed to other projects that used a web front-end.

On the negative side, years later, a couple of bank developers caught me at a conference and practically begged for my help in fixing RTL problems they were experiencing due to changes made by Sun to the way input worked in Swing/AWT. Despite working at Sun at the time, there wasn't much to be done, as I couldn't change AWT from my position. Even one of the top 100 banks in the world couldn't get Oracle or Sun to do something in their VM implementation.

To me, that was one of the biggest problems with Swing. When dealing with client UI, we must be agile as there are so many points of failure.

## These Are Separate Tiers/Teams

Another common statement is that server and client are completely separate by definition, and intentionally, so having a single language/environment would lead to bad engineering and tier mixing.

In many cases, the server and client teams/repositories are completely separate. They have separate management and separate processes. In those cases, the benefit of full stack is reduced slightly. However, the extreme separation usually doesn't make much sense.

It doesn't matter how many unit tests you have, there will still be a failure when a client tries to work with the server. The ability to debug, change, and commit quality code in the client or the server is very valuable.

Being able to run the client and the server in one IDE and have a complete debug environment is huge!

But the biggest value is shared code as I discussed above.

Business objects can be shared across tiers in a very effective way. That means validation code that must run on the server for security can be identical on the client for usability. It means a tremendous amount of code can be reused, reducing the overall app complexity.

## Any Programmer Should Be Able to Pick Another Language

This comment was thrown out in a rather disparaging way, as if anyone can pick up JavaScript, so anyone who can't just read any other language is stupid and slow.

When I started sending out my resume as a junior developer in the early 90s, I listed a lot of programming languages on top. I assumed my familiarity with every programming language would attract prospective employers (it didn't). As I became an employer later on in life, I learned that this is a sign of either really bad resume writing skills or an unfocused programmer.

Picking a language takes a few minutes, if it's not revolutionary. Understanding it well takes roughly six months of intense work with a recent version of that language. I used to be great with C++, but if I try to go back to it, I'm pretty sure it won't look pretty… I formed Java habits that don't fit in the world of C++ but the worst part is that I haven't kept up with the changes there.

I worked with C# when doing our first Windows Phone port. It was painful for me to get into VS, where I constantly fumbled. The language was similar enough to Java that I picked it up and ran very quickly. However, I'm confident my code looked similar to the code of a C# guy coming over to Java in the first few months.

Now, you can argue that this level of proficiency is enough for the use case of "I need to debug something on the server." That's sometimes true, but it creates a situation where we try to avoid making changes or interact. That deteriorates to throwing blame on the other team instead of taking a proactive approach of fixing things. It also makes late night debugging sessions bearable.

## What Next?

I've decided to divide this into three parts, with the first one being the "what" part, this article discussing the "why" -- trying to highlight the benefits of full stack and cross platform for Java developers. In the final segment, I'll focus on a deeper dive into "how."

Again, I'd appreciate all types of feedback and I highly appreciate the comments.

P.S. If you liked this article and found it interesting I'd appreciate a like and share. This brings more people into the conversation, which is always interesting!

The Java Zone is brought to you in partnership with [ZeroTurnaround](https://dzone.com/go?i=97821&u=http%3A%2F%2Fpages.zeroturnaround.com%2FRocket-Powered-White-Paper_Rocket-Powered-White-Paper.html%3Futm_source%3Ddzone%26utm_medium%3Djavazone_partner_resources%26utm_campaign%3Drocketpowered). Check out this [8-step guide](https://dzone.com/go?i=97821&u=http%3A%2F%2Fpages.zeroturnaround.com%2FRocket-Powered-White-Paper_Rocket-Powered-White-Paper.html%3Futm_source%3Ddzone%26utm_medium%3Djavazone_partner_resources%26utm_campaign%3Drocketpowered) to see how you can increase your productivity by skipping slow application redeploys and by implementing application profiling, as you code!

Opinions expressed by DZone contributors are their own.
