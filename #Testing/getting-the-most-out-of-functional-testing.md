# Getting the Most out of Functional Testing

_Captured: 2017-12-26 at 22:18 from [dzone.com](https://dzone.com/articles/getting-the-most-out-of-functional-testing?edition=347109&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=agile%202017-12-26)_

The Agile Zone is brought to you in partnership with [Techtown Training](https://dzone.com/go?i=151022&u=http%3A%2F%2Fwww.techtowntraining.com%2F). Understand how your role fits into your organization's DevOps transformation with our [DevOps eBook](https://dzone.com/go?i=151022&u=http%3A%2F%2Fpages.aspeinc.com%2Fdevops-enterprise-ebook.html%3Futm_source%3Ddzone%26utm_medium%3Dfooter%26utm_campaign%3Ddevebook).

For as long as people have written software, they've also tested it. This applies both to the history of the industry and to the history of any individual programmer. Obviously, people coding against early mainframes verified the behaviors of the code they wrote for business purposes. But you, as an individual developer, started doing this right from the beginning as well. You'd write a "hello world" program, then run it to see if it did, in fact, print out "hello world" on your console.

So you might say that software development and software testing are inseparable (though the [so-called waterfall approach](https://en.wikipedia.org/wiki/Waterfall_model) did its best to separate them). And that makes sense. After all, creating software and testing it both count as [knowledge work](https://simplicable.com/new/knowledge-work-definition) pursuits. They're also both absolutely necessary to ship good software. Oh, and they're both complicated.

You can observe this in the software world with the proliferation of different patterns, architectures, and algorithms. In the testing world, you see it with the challenges in organizing and categorizing testing methodologies. You cannot possibly test everything a piece of software might ever do in any scenario. So you find yourself faced with the daunting task of trying to represent the most likely and most important scenarios without boiling the ocean.

## Broad Categories of Testing

To simplify for the purposes of this post, let's speak to some broad categories of software testing. Note that, because I'm staying at the 10,000-foot view, there might be some gray areas between these categories. But this should cover the vast majority of the space.

First, you have [white box](http://softwaretestingfundamentals.com/white-box-testing/) style tests. This name and variations of it arise from a vivid description. Imagine having something like a motor or appliance and, instead of the normal casing, it came in a see-through box (a "white box"). You could then see the interior mechanical workings. So we use this imagery to describe a style of software testing wherein we see and understand the source code. White box testing then largely describes the [so-called test pyramid](https://martinfowler.com/bliki/TestPyramid.html) \-- automated tests that software developers write and execute.

The white box label naturally invites comparisons to its counterpart, the black box. Imagine that same appliance, but wearing its normal casing. In that situation, you have no idea (or interest in) how the internal mechanics work. You just want to verify that it works the way its users expect. This is also called functional testing, and it's what the rest of the post will focus on. Generally, non-developers do this and, usually, it's specifically QA pros that handle it.

The third form that I'll mention sometimes earns the moniker "non-functional testing" because that's how people distinguish it from the aforementioned functional testing. I'd rather not define it by negation, however, so let's call it "fit for purpose" testing. This style of testing covers things that are important, but not directly related to the intended functionality of the software. Does it perform well with lots of people using it? Is it secure? Does it comply with regulatory concerns? Fit for purpose testing [answers these questions and more](http://istqbexamcertification.com/what-is-non-functional-testing-testing-of-software-product-characteristics/).

## Functional Testing in More Detail

Having oriented ourselves on the broader testing map, let's dive more into functional testing. What, exactly, does this involve, and how does it work?

Functional testing, at its core, examines whether or not the software delivers on its promises. Does the login screen let you log in when you enter the correct credentials? If you withdraw money from your bank account, can you observe a reduced balance? Does the "add a customer" screen successfully add a customer to your records? You get the idea.

Because it aims to address the core purposes of your software, it relates heavily to the software's requirements. This means that, like requirements, your testing scenarios, or "test cases," require a great deal of organization. For any given scenario, like "log in," you have to understand the inputs and their expected outputs, as well as understanding how to navigate to the relevant part of the application. With that information in hand, you also need to keep careful track of what you did while interacting with the software and then of whether the test succeeded or failed. Oh, and then you have to do that for hundreds, thousands, or tens of thousands of test cases.

As you can see, most of the complexity around functional testing resides in organizing and managing the comprehensive testing effort. Sure, actually executing these methodically requires some skill and knowledge of the domain. But management and coordination tend to dominate the effort.

## The Importance of Automation

In years gone by, before tooling was quite as good as it is now, management of functional testing required a ton of elbow grease. QA groups would turn the requirements into binders full of test cases, which included exhaustive detail on how to execute the tests. They might then turn the effort over to data entry personnel, supervised by an experienced tester, who would expend a great deal of effort recording and organizing results.

Hopefully, your organization isn't _still_ doing this. Two important areas of automation have emerged, simplifying matters greatly. First, test case management systems now exist. You can do away with lower-tech ways of gathering this data in favor of ones that organize it all based on requirements, trace it back to those requirements and to code check-ins, and track results for you over time. Test case organization has come a long way. And, secondly, you can automate the execution of test cases, meaning you don't have to pay data entry people to do it. You can achieve this with scripted testing tools like [Selenium](http://www.seleniumhq.org/) or with playback and record types of tools.

Do not confuse this type of automation with the white box automation that I mentioned earlier. You're not automating based on the internal details of the code. Instead, you're automating the procedural execution of steps that used to come from humans following a binder full of instructions. This allows your skilled QA personnel to spend their time in more productive ways than supervising temps hired to perform drudgery.

## Get the Most Out of Functional Testing

So what does functional testing look like in a modern world, on a healthy team with a sophisticated approach? What do the QA folks do?

To understand that, consider an Agile construct known as [the "three amigos" collaboration](http://www.velocitypartners.net/blog/2014/02/11/the-3-amigos-in-agile-teams/). This involves a developer, tester, and business analyst contemplating a requirement together and agreeing on what it will mean to call that requirement completed. For his part in this, the tester examines the requirement and conceives of a test that, when passing, means the requirement is done.

That captures, in a nutshell, the role of QA in functional testing. They understand the software, the domain, and their craft quite well. And they leverage that understanding to conceive of tests that establish the completeness of a given feature. "Sure, the login screen should log you in," they might say, "but we can't consider the login feature complete until it provides feedback on failed logins and limits you to three attempts." The functional testers contribute to defining done for features and then act as stewards of that "done-ness." And they leverage a lot of automation to help them.

In some ways, functional testing is the most basic and essential form of testing. Make something that prints "hello world," run it, and see if it does, in fact, print "hello world." It's basic and essential, though, because it's foundational. Without it, no concept of done exists. So make sure you do adequate functional testing and make sure you pay attention to the results. But leverage intelligent automation so that you can make sure you focus on the big picture instead of getting lost in the details.

Adopting a DevOps practice starts with understanding where you are in the implementation journey. Download the [DevOps Transformation Roadmap](https://dzone.com/go?i=151021&u=http%3A%2F%2Fpages.techtowntraining.com%2FDevOpsRoadmapDzone_DevOpsTransformationRoadmap.html%3Futm_source%3Ddzone%26utm_medium%3Dheader%26utm_campaign%3Ddevops-transformation), brought to you in partnership with [Techtown Training](https://dzone.com/go?i=151021&u=http%3A%2F%2Fwww.techtowntraining.com%2F).
