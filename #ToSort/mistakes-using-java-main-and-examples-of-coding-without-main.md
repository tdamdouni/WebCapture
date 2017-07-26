# Mistakes Using Java Main and Examples of Coding Without Main

_Captured: 2017-07-10 at 09:09 from [dzone.com](https://dzone.com/articles/mistakes-using-java-main-and-examples-of-coding-wi?edition=306242&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-09)_

[Evolve your approach to Application Performance Monitoring](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html) by adopting five best practices that are outlined and explored in this [e-book](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html), brought to you in partnership with [BMC](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html).

_Update - for some reason this was sitting in draft for over two years ( the last date was 3/March/2015). I seem to have used some of the material in the post in other posts (possibly I thought this post was too large), but there are some examples in here I haven't mentioned before so I hereby click publish and release it to the world._

I think I've written a 'main' method only 4 or 5 times in my Java career. I rarely have to package up my code in a form that can run from the command line. I have only recently (in January 2015) written a Java GUI, which starts from a main method. All of the rest of my code, and I've written a lot of Java code, I have executed as a JUnit or TestNG (Test method, in the early days).

I only need a main method when writing an application. I normally write code to automate applications. Most of the code I write takes the form of automated checks of an application to confirm assumptions represented as assertions in the code. Most people learning Java for the first time do not learn to do write code in the form of @Test methods, they learn the main method first. And then always use a main method.

Here are some of the mistakes I've seen people writing automation code make with the main method.

Some people will read this post and think - uh oh, he's talking about me. And I probably am for one of the examples. But I haven't seen just one person making these mistakes, I've seen many people make the following mistakes. And I have included some examples of how I have managed to go through my Java career and avoid packaging my code into an app.

### Mistake - Write All the Code in a Main Method

Since people learn 'main' first, they often write all their code in, or from, a main method.

Leading to:

  * Hardly any classes.
  * Hardly any abstractions.
  * Harder to unit test because no one really trains you to write tests around a main method.
  * Very often, very few conduct unit tests in their code base because they started with a main method, rather than @Test methods.
  * Lots of copy-pasted code across lots of projects.

Unfortunately, I've also encountered situations where people are taught to write automation code like this. With no mention of a TestRunner (e.g. JUnit or TestNG). So, effectively they are having to learn Java at the same time as writing an @Test Execution engine, something that you get for free with JUnit or TestNG.

No wonder people give up with Java and jump to a scripting language instead.

I find it better to start with @Test annotated methods, and build up the code base, and work towards a main method (if I need it), but not to start with a main method.

### Mistake - Multiple Main Methods

I can see advantages in having [multiple entry points](http://stackoverflow.com/questions/4754058/multiple-main-methods-in-java) into your packaged code. It might be a good idea in certain situations, and we know we can define which specific main method to run when we start the jar file.

But sometimes main methods are added because people don't know why they needed them in the first place.

I've seen code where main methods don't do anything, because doesn't every class need a main method?

Why?

Because every example they have seen starts with a main method, and most of the example code people see in books is not related, therefore each chapter has a separate application, i.e. a separate main method.

I avoid this problem by driving everything with @Test methods - even my main methods will have an @Test around them. And I can run the disparate parts of my code base using the filters provided by JUnit Suites or maven configuration, or running individual @Test methods or classes from the IDE.

### Advice and Examples

I advise you learn to package your code and use main methods at the point when you are writing an application for other people to use. But not before.

Because you may not need to.

When you are writing @Test methods you can use the standard configuration of Maven to run all your JUnit tests automatically without you having to create your own test runner or main method.

You can also write @Test methods that you can run from the IDE to gain many of the benefits of scripting languages.

#### Example - Selenium Simplified Book Generation

When I wrote Selenium Simplified, I couldn't find a text file based book generator that I liked, given the use cases I needed. So I wrote my own. It was a fairly large Java project, with a lot of classes. And no main method. The IDE was my execution GUI.

  * If I wanted to process a different book, I changed the file path.
  * If I wanted different options, I amended the outputDetails.
  * I had multiple @Test methods for different configurations with relevant names I built my book by right clicking on the method and selecting "Run" as a JUnit Test.

This code project still doesn't have a main method.

#### Example - Code for Java for Testers

After some copy-paste and proofing errors during the creation of Selenium Simplified, I wasn't prepared to write another book with code in it until I could pull code from the main source into the book.

I couldn't find a tool that worked the way I wanted, so I wrote code to automate the process for me.

Looking through my history I can see that on** revision 14**, I added the following code:

I created a new class called ApplicationRunner, with a main method. But I was, at this point, still running the code from the IDE, under control of an @Test, which only ran from the IDE because it was @Ignore annotated, so it would not run from CI.

It was not until **revision 16**, that I added the manifest details into pom.xml to allow me to package the code as an application.

When I did this in revision 16, I had the ability to run the code outside the IDE, but I retained the ability from revision 14, to run it from the IDE by wrapping it in an @Test annotated method.

I used the @Test execution approach first.

#### Example - Backup Mindmeister

I wrote some automation code to help me backup my MindMeister Mind Maps
    
    
     Map < String, String > folderPaths = mm.getFolderPaths();

I run this automation code by right clicking on the 'backupAllMaps' @Test method in the IDE.

I had multiple automation use cases. All executed by right clicking on an appropriately named @Test method and running it as a JUnit test.

This is the kind of use case people put forward as a reason for using scripting languages.

## Summary

I actually write a lot of my ad-hoc support code this way. By running it from the IDE as an @Test method. I have many other examples of this approach on my disk but I think the above are representative enough. This approach gives me many of the benefits that people claim that scripting languages bring to their work-flow. Only when I need to run the code during a work-flow outside the IDE or allow other people to run the code, do I use a main method.

And at that point, I generally make sure I have an @Test method which can all the main method to allow me to create ad-hoc debug test runs. It is important to learn how to use main, but not as one of the first things you do. Particularly when you are writing automation code as opposed to application code.

The point at which your automation code becomes application code is the point at which you learn how to package your code and use the main method.

Learn tips and best practices for optimizing your capacity management strategy with the [Market Guide for Capacity Management](https://dzone.com/go?i=161136&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-BCO-GartnerMarketGuide-CapMgmtTools-AR.html), brought to you in partnership with [BMC](https://dzone.com/go?i=161136&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-BCO-GartnerMarketGuide-CapMgmtTools-AR.html).
