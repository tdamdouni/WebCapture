# 12 Key Skills & Best Practices from Automation Guild 2017

_Captured: 2017-06-06 at 10:08 from [www.joecolantonio.com](https://www.joecolantonio.com/2017/03/30/automation-guild-recapp/)_

![ block 1 1020x560](https://joemainzone-ilyznmosqlw0zs.netdna-ssl.com/wp-content/uploads/2017/03/block_1-1020x560.png)

> _Automation Guild Recap_

I just realized that I never did a recap of what I learned from the 2017 [Automation Guild](https://automationguild.com/). Here are some skills and best practices gleaned from this year's conference.

![Automation Guild Conference Room](https://joemainzone-ilyznmosqlw0zs.netdna-ssl.com/wp-content/uploads/2016/11/AutomationGuildConference.jpg)

## **What is the Automation Guild?**

[Automation Guild](https://automationguild.com/) is the first ever online conference 100% dedicated to automation testing.

The conference was something of a hybrid. I asked the speakers to record their sessions ahead of time so I'd be able to get the best audio and video quality possible. I then uploaded them to a membership site where attendees were allowed to begin viewing the sessions two weeks before the conference officially began.

During the actual week of the conference, I livestreamed myself and the speakers' Q&A sessions, during which attendees were able to ask questions of the speakers. I tried to make it an attendee-led conference, in that they could set the agenda with their questions.

![ wAAACwAAAAAAQABAEACAkQBADs ](https://joemainzone-ilyznmosqlw0zs.netdna-ssl.com/wp-content/uploads/2017/02/300x445_DevOps_04.png)

_Here are the top 12 takeaways you need to know:_

## **1.Expand Test Coverage with Visual Validation Testing**

We are all moving towards rapidly developing software. We have to release software more and more quickly. As we try to ship it faster, we need ways to obtain better coverage. One of those ways is Visual Validation testing.

Tools like QTP and Selenium are functional rather than visual validation test tools. They don't tell you how your site looks from the point of view of a real user. Visual Validation testing allows you to actually look at a website and tell whether or not there are any visual differences. Visual Validation testing allows you to create better test coverage for many tests that you might currently have as manual tests-responsive design tests, for instance.

### **Response Design Testing**

Think of all the different kinds of operating systems and devices your application needs to run on. Your application needs to look good on a smart watch, iPhones, Android devices, Mac 27″ screen or a small laptop, which means your application needs to scale on all those different screens. Functional testing doesn't give you the information you need to make ensure your app is doing that.

At this year's Automation Guild, Adam Carmi from Applitools gave a really popular session on Advanced Test Automation Techniques for Responsive Apps that went into detail on how to get better responsive testing coverage.

### **Localization Testing**

Another session on visual validation testing was led by Peter Kim. Peter focused on how you to automate Localization tests. As I mentioned above, using a functional testing tool will only confirm a DOM that's being rendered, or HTML. It's not really rendering or telling you what it really looks like. Peter Kim does a lot of enterprise-type testing, and he gave a demonstration of how he uses it for localization testing.

Peter and the attendees brought up a good point. Visual validation testing is able to catch things that normally wouldn't be caught without it. Peter also mentioned that he doesn't know how it would be possible to get the type of coverage he's able to get _without_ visual validation testing.

## **2\. Use the Right Tool**

Some folks seem to be confused about which test tools they need in order to automate their tests. For example, during Adam's session the folks in the chat started asking how Applitools differs from Galen, which Adam explained as follows:

1) It doesn't test everything.

2) It doesn't test what it is showing to the user, so it doesn't treat it. Rather, it just looks at the DOM, or the HTML. It doesn't actually look at the images to ensure they're exactly the same.

3) It's hard to use for large, complex sites.

This is not a knock on Galen. Adam himself admitted that it's a great tool. The main point is that it's a tool designed for a different purpose, and one shouldn't try and force a tool to do something it wasn't designed for. Also, depending on your situation a tool that is right for your team is not necessarily the right tool for another team.

I also interviewed the creator of Galen and asked him the same question. He said that Applitools is awesome if you're doing visual validation testing. Galen is not a visual validation tool. It's much better suited for UX engineers and developers.

This once again highlights the point that not every tool is right for everyone.

![Visual Validation Tools](https://joemainzone-ilyznmosqlw0zs.netdna-ssl.com/wp-content/uploads/2017/02/visualvalidationtools-300x181.jpg)

## **3\. Open-Source Visual Validation Testing Tools**

I received a ton of question from attendees asking whether there are any free, open-source solutions aside from Applitools, so I created a resource highlighting the top [21 FREE Visual Validation tools ](https://www.joecolantonio.com/2017/02/02/top-21-free-visual-validation-tools-testers/)you can use to get visual validation incorporated into your frameworks.

## **4\. Flaky Tests**

The next takeaway -- and this was a pretty popular session -- was with [Dave Haeffner](http://davehaeffner.com/) about how to grade your Selenium tests. What Dave did is really step through the core tenets of what he believes constitutes a "good" test. What makes a good page object design?

He showed a grading system to objectively tell you how to assign your tests a grade. For example, Dave came up with some rubrics. Your tests start off with a grade of 100, but with each infraction points are deducted, ultimately ending up with a grad that ranges from an "A" to an "F."

It's a great way to measure how maintainable and reliable your test are. It can also help you plan your tech debt, since you're going to want to refactor poorly graded tests at some point.

## **5\. Screen Play Pattern**

One of the most controversial topics discussed during the conference was around the screen play pattern. [John Smart](https://johnfergusonsmart.com/), the creator of [Serenity](https://www.joecolantonio.com/2015/03/05/serenity-bdd-getting-started-using-serenity-with-selenium-and-jbehave/), gave a hands-on session on how he uses the screen play pattern. He demonstrated how he thinks it represents the next generation of page objects. Page objects are good place to start when doing automation, but they can get ugly.

Even though they're trying to encapsulate and get some re-use, a lot of teams aren't creating page objects that follow development practices like the [SOLID principle](https://en.wikipedia.org/wiki/SOLID_\(object-oriented_design\)).

Page objects are good place to start to help make your test maintainable, but if you're not careful, they can grow out of control over time.

The [screenplay pattern](http://serenity-bdd.info/docs/articles/screenplay-tutorial.html) takes page objects and chops them down into really tiny pieces. John talked about how the fact that this has made his tests much more maintainable and reliable. Another major benefit is that it makes test scripts more readable.

After viewing John's session I'm convinced that the screenplay pattern is the next wave of page objects.

## **6\. BDD: Not the Same for Everyone?**

When we talk about BDD, we usually discuss the benefits of determining what you are going to develop before you write even one line of code. What you typically don't want to do is talk about implementation details like mouse clicks, because _how_ you implement is not of concern to the user.

Or so I thought

I was a bit shocked when [Matt Wynne](http://blog.mattwynne.net/), in his session Q&A on Keeping your Cucumbers Sweet, said "There is no definite way to create BDD. It's a team decision. If you find the consensus is that people want information like clicks and drop-downs, then that's what you should do, because that's what the team cares about."

## **7\. Vendors Embrace Open Source**

I've spoken about this a few times in the past, and once again it really came through during this year's conference.

HP revealed their product roadmap, and some of the stuff they mentioned actually turned up in their latest [UFT 14](https://www.joecolantonio.com/2017/02/23/uft-14-quick-overview-need-know/) release. Things like being able to run on Linux and Mac and the support for TFS. Things that even three years ago you would never have dreamt of, since HP was so anti-open source. Not anymore. In their session you could tell that they have completely embraced it, and have even developed a new, lightweight functional test tool- UFT PRO (LEANFT) -- that allows you to use the same tools, IDEs and languages as your developers to create automation scripts.

## **8\. Test Data Management**

Another thing that came up test data strategies. Often when tests are flaky, there are many reasons why tasks might be flaky -- one of them being that you're not using the right synchronization networks. Instead you're just loading up your application and trying to bang on it instead of saying "Okay. Wait. Is this field available? Is the DOM fully loaded?"

Another reason is one that I don't think occurs to many people, which is that test data can cause their tests to be flaky.

We had a really great session by [Paul Merrill](http://beaufortfairmont.com/author/dpm3354/) on test data strategies. He gave four different ways in which you can utilize [test data strategies ](https://joecolantonio.com/testtalks/105-data-strategies-testing-paul-merrill/)to help make your tasks more reliable and more repeatable.

This is really important when you're trying to run against different environments in your CI/CD systems. Paul showed some different ways that you can try to minimize automation test data issues to help make your tests more atomic. You can run against any environment and obtain the data you need because you're following these different principles.

## **9\. Selenium is Just for Browser Automation**

I'm still surprised when I'm asked how to automate Windows applications using Selenium. Selenium is for browser based-automation only. So what if you also need to automate thick client window applications? That's why I was excited to talk to [Maciek Konkolowicz](https://www.linkedin.com/in/mkonkolowicz/) about how his team uses the open source tool [White Framework](https://github.com/TestStack/White) to test his Windows, WPF and Silverlight applications.

Another tool that was discussed was [WinAppDriver](https://github.com/Microsoft/WinAppDriver) (still in beta) that uses Appium to drive Windows-based applications. I think we're going to be seeing more open-source automation solutions for more than just browser applications.

## **10\. Performance Testing is Shifting Left**

More and more folks are also discussing how to move performance testing up to an earlier position in the development life cycle. [Michael Sage](https://www.linkedin.com/in/michael-sage-6682285/) talked about how this can be done using an open-source performance tool called [Tauras](https://github.com/Blazemeter/taurus), which was developed by Blaze Meter. Michael gave an excellent session on using Tauras, an easy-to-use, open-source tool that allows developers to write their tasks in YAML.

You can describe a full-blown script in about ten lines of code using Tauras. It's a big leap forward from the old days of starting up Loadrunner and creating large, vendor-specific recording, scripting tests.

With Taurus all you need to do is create a YAML file test using natural language to create their tasks.

This is important because as you start having sprint teams involved in performance testing, not everyone may be a performance-testing expert. But if you can use something like Taurus using YAML files it can help you be faster when it comes to creating performance testing and incorporating it into your continuous integration environment.

## **11\. Docker**

When discussing test data management, what we sometimes need to do is create instances of the database in a [Docker](https://www.docker.com/) or [Vagrant](https://www.vagrantup.com/) container. This can help you to start each test in with a known state. And it fast because it's not the full environment. It's not a full VM. It comes up really quick, so it makes running your tests easier to run and spin up all kinds of different environments in seconds.

[Dima Kovalenko](https://www.joecolantonio.com/2015/08/19/selenium-interview-with-dima-kovalenko/) discussed some ways in which it helped his team to do better automation. He also shared some tools he uses that others might find helpful:

  * DotCi brings ease of build configuration of cloud ci systems like Travisci and ease of runtime environment configuration of Docker to Jenkins.
  * Docker Compose. Docker Compose is a great tool that allows you to tie together multiple instances of Dockerfile in a very easy to use, coherent way.

If you look up Google trends, you'll see Docker is really taking off. A key takeaway from the conference was that it's important to start learning about technologies like Docker and Vagrant.

If you're an automation engineer, you really should increase your knowledge of these types of things. It's time to move towards a more holistic, high level CI, CD, big picture. Ensure that you have quality at all gates within your checking code, from development, all the way through to deployment. Using things like Docker can help you get there.

## **12\. API Testing**

I've been doing automation for 17 years. No matter what tool you use, GUI test automation is going to be hard to maintain and a bit unreliable, simply due to the inherent nature of GUI tests. That's why I try to avoid GUI tests whenever possible. One way to do that is to use API testing. Bas Dijkstra gave an excellent session on an API testing user tool called Rest Assured, a Java DSL that allows you to write tasks using Java. During this session as in some of the others, attendees recommended other tools to help with API testing, including [RestSharp ](http://restsharp.org/)for .Net and [Postman](https://www.getpostman.com/), a Chrome add-in, and [Karate](https://www.joecolantonio.com/2017/03/23/rest-test-tool-karate-api-testing/), which allows you to create codeless API test using BDD.

## **Recap**

Those are the 12 main takeaways I took away from the conference, and there were a lot more. It was an awesome conference, and it's still [available](https://automationguild.com/)! I've received so many requests that I decided to keep [registration open](https://automationguild.com/), since all the sessions are recorded and are still accessible. You can still view all the sessions, see all the chat and get access to the private slack channel.

Furthermore, I'm happy to announce that A[utomation Guild ](https://automationguild.com/)will be a yearly event. So if you missed the chance to be a live participant at this year's conference, be sure to check it out in 2018!
