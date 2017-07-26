# Ten Misconceptions About Software Testing - That Non-Testers Share

_Captured: 2017-05-30 at 13:45 from [dojo.ministryoftesting.com](https://dojo.ministryoftesting.com/lessons/ten-misconceptions-about-software-testing-that-non-testers-share)_

Software testing is a craft that's often misunderstood by those who are outside the field - and sometimes those who are inside it. Some of the most common misconceptions are also the most damaging to the field, leading to miscommunication, blame, and resentment.

## 1\. Testers Break Software

This is a very common misconception, that can quickly fall apart with some thought. Testers don't have a magical bug-insertion tool hidden between the developer's machine and the testing system, but somehow, code that worked just fine for the developer doesn't work for the tester.

The reason isn't that the tester broke it. The reason is that the tester did something the developer didn't expect. That might be "running the software on the test system without installing all the prerequisites first" because the developer didn't realize the test system didn't have the prerequisites on it in the first place. It might also be actively looking for weaknesses. This is also where "but it works on my machine" comes from. On the developer's machine everything that's needed has already been installed, all the configuration is done, and the developer knows what she's doing so her testing usually focuses on what the software should be doing.

Or it might be because the new feature the developer just finished interacts with an existing feature the developer didn't realize was linked to their new feature, and the unit test coverage wasn't as good as the developer thought.

The point is, there are any number of ways a complex application can break, and in my experience any team will encounter at least one of them at some stage in their careers.

### The Truth: Testers Didn't Write It So They Didn't Break It

Unlike a physical object that can be broken by dropping it or using it in an unexpected way, software can only be broken by those who created it. Testers just find places that are broken and report them. Sometimes, it isn't even actual breakage so much as something that doesn't work the way customers expect or want it to work.

In the worst case, testers can get blamed because something in the software isn't what the customer wanted or thought they wanted. I've been blamed for not finding a problem, or not finding a problem "in time", or even for finding a problem because it exposed a deeper problem that meant a lot of extra work for everyone. The whole "testers break software" attitude can easily lead to a no-win situation that ends with burned out, cynical testers and a seriously dysfunctional team. Nobody wants that.

## 2\. Testers Don't Have Tech Skills

This idea is one that sets my teeth on edge. I've known some very good testers who couldn't code and didn't have particularly deep technical skills. I've also known some very good testers who could out-code every developer in their organization. Technical skills are not just about being able to code, and arguably include being able to reproduce an error that's difficult to trace and difficult to reproduce, being able to read or understand an error code, being able to set up the application under test with different configurations, being able to clearly explain both to a developer and to someone with no development experience just what the software is doing and why that behavior is a problem.

Being able to communicate your findings about the product, or reproduce that odd event, or find the places where the developer's assumptions don't match the customer expectations before the customer sees the software, these are the kinds of skills that matter. They're a lot harder to define and much harder to quantify than "can code as well as a developer."

Probably the simplest way to describe this is that testers and developers have complementary skill sets with some overlap. Boosting the developer's ability to do tester-things takes time away from his primary activity. Boosting the tester's ability to do developer-things takes time away from her primary activity. Both are needed, and each supports the other.

### The Truth: Testing Is Not Development

Testing is a separate field with its own demands. Some of those demands overlap while others don't.

Developers use their skills to build solutions to problems expressed as user requirements. Before they write a line of code, they look at the use case or the feature request or the help desk ticket or whatever other documentation they have to work with, and they make a decision on the best way to help the person who made the request. Then while they're coding, they're making decisions about the best way to handle the many challenges they encounter while they're building a solution to someone's problem. It's a problem-solving skill set.

Testers use their skills to analyze the fitness for use of the solution presented to them. They will compare the software to the problem in the use case or feature request and look for gaps or areas that don't seem to fit the problem or the solution. They'll use every tool at their command to seek out potential risks and surprises. Where developers are primarily problem-solvers, testers are primarily problem-finders.

It doesn't matter if testers have less - or more - technical skills than developers do. What matters is that all their skills are a good fit for the tasks they need to perform or that they can quickly pick up whatever skills they don't have to do their job to the best of their ability.

## 3\. Testing Is Writing Test Cases Then Performing Them

You only have to scroll through job board listings to see this one in spades. Position after position will have descriptions referencing writing test cases and/or performing them. Senior testers write test cases, junior testers perform them. It's enough to make your eyes cross.

This, like many of these misconceptions, goes back to the factory model of code development and the associated "Any Warm Body" school of testing, with their assumptions that any software can be documented sufficiently and thoroughly enough that it's possible to write exhaustively detailed test cases before the software is completed. It's a very waterfall model assumption that doesn't survive most [agile practices](https://en.wikipedia.org/wiki/Agile_software_development). Or for that matter, an awful lot of waterfall projects either. It's because very few software projects have requirements that are well understood enough when they start for this to work effectively. There will always be rework and constant maintenance of these test cases no matter how much you try to make them "[evergreen](https://hub.uberflip.com/blog/evergreen-content)." It's always the [unknown unknowns](https://en.wikipedia.org/wiki/There_are_known_knowns) that bite you.

Since it's relatively easy to measure the number of test cases someone has written or performed, there's a tendency to want to keep this sort of wasteful practice.This tends to happen more often if there's reluctance to reduce the amount of documentation required. There are places where detailed test documentation is necessary. Software that could kill someone if it goes wrong, or software written for heavily regulated industries, often comes with a requirement that tests be thoroughly documented and include evidence that they were actually performed.

### The Truth: Test Cases Are Much Less Important to Testing Than Creativity, Communication, and Curiosity

Creativity, Communication, and Curiosity. These three traits are essential to testing. Test cases are not a trait of a good tester. As long as there is some documentation of what is tested and what is not, and why not, an agile team will have no problem producing high quality, well-tested code.

Even in highly regulated industries that need heavy documentation, a clever tester can set up automation with screenshots to deal with as much of the audit and regulatory requirements as possible, and use a capture tool to document exploratory sessions.

It's a lot harder to measure these skills than it is to measure test cases written and performed, which just might explain the persistence of test cases throughout the software testing community.

## 4\. It Doesn't Work In Production So Testers Failed

This is the irritating side of tester invisibility ([Reasons Why Testing Isn't Boring #10](https://dojo.ministryoftesting.com/lessons/ten-reasons-why-testing-isn-t-boring)). If something goes badly in production, then the testers failed. Since testers didn't write any of the code performing poorly, why blame them?

I don't like blaming testers or developers for problems in production. Developers might write the code, but every "bad" release I've seen was bad because of factors neither developers or testers could control. The problems were usually caused by things nobody could have foreseen, by things like communication mishaps, or dependencies on other parties, or scaling issues that couldn't be handled in-house.

Software is installed on servers we don't control, used by users we don't control, in circumstances we don't control. I've seen users blame testers for documented bugs in browsers as well as for their own typos. Yes, testers make mistakes, but so does everyone else. I've never met a tester who liked knowing that they missed something, even when they had no way to predict that problem might have occurred.

### The Truth: Nothing Can Be Tested Completely

It's silly to think testers should be able to catch everything that's wrong with a program. Take a basic calculator application, with or without scientific or other advanced functions. Now consider the addition function. To test only adding two integer numbers completely, you would have to test adding every number the calculator is capable of using to every number the calculator is capable of using and making sure that the result is correct and the display is correct.

Even with a very simple calculator that doesn't display exponential notation and can only add from -999999 to 999999, that's 1999998 possible integer numbers to add to 1999998 possible integer numbers - or (1999998)2. If it takes an average of only 5 seconds to perform the calculation and check the result, you're still looking at over 300000 years to test every possible addition of two numbers (and that's working 24/7/365). Nobody has that much time.

Even if you automate and can bring that average test time down to 0.1 seconds, you're still looking at thousands of years, or thousands of computers, before you've tested every possible combination. And remember, this hasn't even touched anything beyond adding two integers. What happens when you add decimals? Other operations? More than two numbers? It doesn't much for the number of possible outcomes to approach infinite.

This makes the notorious [Pentium math bug](https://en.wikipedia.org/wiki/Pentium_FDIV_bug) more understandable, doesn't it?

## 5\. Testing Can Find All The Bugs

To start with, see above. I'm sure that with an unlimited budget and an unlimited time frame (in the order of trillions of years) it would be possible to find every actual bug in a piece of software. Only problem is that by then, customers have moved on and the software that's being tested is trillions of years out of date, and the [heat death](https://en.wikipedia.org/wiki/Heat_death_of_the_universe) of the Universe may have just made all your worries obsolete.

Aside from the fun of combinatorial math increasing your test time exponentially each time a new operating system or hardware device or software feature is added, many things reported as bugs are not, technically speaking, faults in the software. In that case, the software works exactly as designed and built, but what it does and how it works doesn't match what the customer needs. This is normal.

### The Truth: Testers Can't Do Everything And Can't Read Minds

Not only is it physically impossible to test everything the software could do on every piece of hardware the software could run on, at least, if you want it tested and released in your lifetime. Testers are not telepathic. We try, but even at our best, we can't say for certain [what the customer actually wanted](http://www.projectcartoon.com/cartoon/3) or needed. This is why we try our best to test what matters - we do risk assessments and try to make sure the core functionality of a piece of software is working to the best of our knowledge and ability.

## 6\. Testing Can Be Automated

This is one of those misconceptions that gets a lot of its power from being almost true. In theory, any test case can be automated. The process of testing with its multiple contextual cues and extensive use of tester intuition can't be automated, not without true artificial intelligence, and possibly not even then. You might end up with the Douglas Adams' equivalent of [Marvin the Paranoid Robot](https://en.wikipedia.org/wiki/Marvin_\(character\)) Tester being told to do uninteresting things.

![](https://d2h1nbmw1jjnl.cloudfront.net/ckeditor/pictures/data/000/000/128/content/ten_misconceptions_about_software_testing_brain_planet.png)

> "Brain the size of a planet and what do I get?  
Follow this test script, automate that test script…"

Even if you can automate every test, that doesn't mean you should. Computers are very good at doing things exactly the same way many times over very quickly. Tests requiring a lot of things done fast many times over, and using exactly the same set of steps each time, should probably be automated.

Humans are very good at recognizing when something doesn't look right, using pattern-matching and spatial reasoning. These skills are extremely resource-intensive and error-prone for computers. It's much cheaper and easier for the humans to do this and for computers to do the multiple data-based calculation, or simple pattern type tests.

### The Truth: Some Tests Can Be Automated. Testing Can't

Currently, we can test if elements are visible or not visible, but we can't, not yet, test if they are exactly where they are supposed to be and how they look to the user. It is, theoretically, possible to automate testing that a printout contains the expected information, but the people who did that as a proof of concept needed 6 months work to create error-prone automation that failed whenever the printer or the camera failed. Whenever the printer needed ink, went offline, got a paper jam, the test failed. When the webcam trigger was joggled, or didn't have power, or was out of alignment, the test failed. It takes all of that to automate something could take less than a minute to test manually and more have more reliable, less error prone results.

No automation will ever replace the tester reaction of "hmm, that's odd," nor should it. Without that reaction, most bugs would remain undiscovered until after release.

## 7\. Testing Happens At The End

This is another misconception that gains power from being partially true. Working with the software is something that can't be done until the new feature/application/whatever has been coded.

The idea that there is this thing called testing which happens after coding is done and before release probably grew out of the waterfall development model, because that's what a simple [waterfall development model](https://en.wikipedia.org/wiki/Waterfall_model) looks like. It's also what a factory process looks like: widgets can't be checked for correctness until they exist.

Of course, as I've mentioned further on, software development isn't that much like a factory process. Developers aren't producing multitudes of more or less identical widgets, and testers can't discard code widgets that don't meet standards.

### The Truth: Testing Happens All The Time

Just because buttons and links aren't being clicked doesn't mean that testing isn't happening: testing is ultimately a process of comparing assumptions about a thing (the software being tested) to the actual performance of that thing. Before coding is completed, testers can work with team members and communicate the things they'll be looking for. They can go over requirements, ask awkward questions about use cases and user stories, and setup prerequisites. All of this is testing.

Even in a classic waterfall development model, testers aren't just testing at the end. When they're going through the requirements specifications, they're testing those documents and, more importantly, the assumptions behind them.

That's before you consider that developers should be creating unit tests, as well as testing their changes as they write them.

## 8\. Anyone Can Test Software

This is yet another misconception that gains power from being partially true. It also gains power from what I call the "Any Warm Body" school of testing - the idea that testing is a matter of following detailed instructions or test cases, and reporting anything that doesn't match the instructions. Of course anyone who can read and follow instructions could do that, and it's all based on the hope that the random people you've hired to test, instead of testers, can follow instructions.

It's testing in its most limited sense. The fact that this kind of testing doesn't often find major or relevant problems tends to be overlooked because it's easy to measure it. You can rank people by test cases completed, which makes bean-counting managers happy. Good managers don't like this kind of measure because they know it's not measuring their people's ability to surface important information about the software.

### The Truth: Anyone Can Follow Instructions. Testing Takes Skill And Training

If you make your instructions so simple that anyone can follow them, you'll find yourself with a task nobody with intelligence or creativity wants to do. Worse, you'll discourage the people you call testers from digging into the application and following oddities to find out more.

Even worse, you will release hard-to-find bugs that cause serious damage to customers and to the company's brand.

If you have skilled, trained testers with the freedom and knowledge to investigate past detailed instructions, you will find your testers doing things like searching the Internet to discover the obscure server setting that causes your software to break for some users. Or building load tests to find those nagging performance issues before you release. Or doing any number of other things to add value to your software that an untrained, unskilled person wouldn't know are even possible.

## 9\. Testers Are Quality Gatekeepers

This particular misconception implies that testers can control the quality of the code that developers write along with the release schedule of the software and everything in between. I'll admit there are times when I'm tempted to wish for a world like that, but I've never met a developer who wanted to produce bad code. Usually they're doing the best they can, and just like testers they can struggle with unclear requirements, convoluted legacy code, and any number of other problems that impact the quality of their work.

If that wasn't enough, there have been any number of times when business decisions forced a release to happen despite my objections. At least once, my objections were somewhere between "strident" and "desperate", and oddly enough, that particular release got a reputation among the customer base as a "dangerous" one that nobody should use for anything more than beta testing. If testers really were quality gatekeepers software wouldn't be released over our objections, and we wouldn't be pressured to give the okay to a release we knew had big problems.

Personally, I think that calling testers quality gatekeepers is a bit like the[ toll booth in Blazing Saddles](https://www.youtube.com/watch?v=SbWg-mozGsU) where the bad guys are riding through the prairie to attack the defenseless town and get stopped cold by a toll booth in the middle of nowhere. There's no fence or anything else blocking them, just a lonely toll booth in the middle of nowhere and the bad guys don't try to go around it. Testers as gatekeepers are staffing a toll booth in the middle of nowhere, while the rest of the business goes around them whenever they think it's reasonable to do so.

### The Truth: Testers Are Not Gatekeepers

Testers can't be everywhere, know everything, or do everything. We aren't a one-person software show where we're in control of everything from start to finish. Nor do we want to be.

There are any number of decisions that go into deciding whether to release or not, or even whether a bug should be fixed. Our role isn't to stand in front of the source control repository refusing to let anything through that doesn't meet our standards. It's to report on what we see and give an estimation of the risks involved in the possible courses of action.

In an ideal world we would be confident about our software releases, but life isn't always ideal. Our risk analysis could point to a potential problem that doesn't meet the organization's threshold of risk, which in turn is unique to each organization and each business domain. We're in an excellent position to observe and report on the quality of the software and the likely user response to it. We're not in a position to understand the wider perspective of the business's needs or contractual requirements.

## 10\. Testing Is Quality Assurance

This is partially true, in that testing is a part of quality assurance. That's about as far as it goes, though, because it's actually not possible to assure quality in software. Every application is different, every feature is different, no two coders work on the same function, and no two testers test the same changes.

Assuring quality requires controlling quality, and when there are that many variables in play, control comes down to everyone doing their best work to make the software as good as they can get it. The whole idea of software quality assurance was more or less imported wholesale from factory quality improvements, where changing processes to reduce the number of faulty widgets works. A factory produces large quantities of more or less identical widgets, so widget quality can be defined by a clear, measurable set of properties. The factory staff do near identical jobs, with the person on line 1 doing the same thing as the person on line 2 and so forth. Factory testers check widgets to make sure that the number of faulty parts doesn't exceed whatever the factory's standard is.

I'm sure by now, the idea of applying this kind of logic to software development has you cringing. It's simply not possible to force software development to work this way. Additionally, there are very few places where testers have the ability to change their employer's internal processes to improve code quality. That pretty much wipes out any chance of assuring quality a tester might have.

### The Truth: Quality Assurance Is More Than And Differs From Testing

Testers don't have a way to inject quality. We don't have a way to inspect code widgets and reject the faulty ones so only good widgets go out the door. At best we can tell people when the software doesn't do the things Marketing is saying it does, and even then it's even odds that the C-level managers aren't listening.

We evaluate quality as best we can from incomplete requirements because we're responsive and giving customers the best we can as soon as we can, then we're adjusting to them discovering that what they thought they wanted isn't actually what they [really needed](http://www.projectcartoon.com/cartoon/3). We advocate for quality and aim to reduce risk wherever we can, but it's not possible to mitigate all risks, and some things simply can't be predicted.

Testers are in the business of Quality Advocate more than Quality Assurance, and I for one have no problems with that.

## Dispelling The Misconceptions

If you find yourself working with someone who has been taught that any of these misconceptions are the right and proper way to develop software, you may have a challenge ahead of you. Nobody likes being told that they're doing it "wrong", but most people are willing to look at ways to make their work life easier.

I've found that all of these misconceptions tend to fall away, at least with developers and managers, just by being myself and doing the kind of testing work I know should be done. It can be a delicate balancing act until you've managed to set expectations to somewhere a little more tester-friendly, but once there, the benefits flow to everyone in the team.

# References

[What is Software Testing according to the "others"? - Mr Slavchev's blog](http://mrslavchev.com/2017/04/18/software-testing-according-others/)

[Blazing Saddles Toll Booth Scene - YouTube](https://www.youtube.com/watch?v=SbWg-mozGsU) (the language can get a bit ripe)

# About Kate Paulk

Kate refers to herself as a chaos magnet, because if software is going to go wrong, it will go wrong for her. She stumbles over edge cases without trying, accidentally summons demonic entities, and is a shameless geek girl of the science fiction and fantasy variety, with a strange sense of humor. In what she ironically refers to as her free time, she writes. Novels, short stories, and more recently, articles for the Dojo.
