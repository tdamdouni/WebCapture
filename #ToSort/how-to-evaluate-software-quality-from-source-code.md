# How to Evaluate Software Quality from Source Code

_Captured: 2017-06-06 at 10:05 from [dzone.com](https://dzone.com/articles/how-to-evaluate-software-quality-from-source-code?utm_source=MVB&utm_medium=email&utm_campaign=Monday%202017-6-05)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

I'll understand if you read the title of this post and smirked. I probably would have done so, opening it up only to see what profound wisdom awaited me._ Review the code, Captain Obvious. _

So yes, rest assured, I understand the easy assumption that one can ascertain a codebase's quality by opening it up and starting to review it. But what does this really tell you? What comes out of this activity? Simply put, _your opinion_ of the codebase's quality comes out of this activity.

## Data-Driven Ways to Evaluate Software Quality

Initially, the idea for this practice arose out of some observations I'd made a while back. I watched consultants tasked with critical evaluations of codebases, and I found that they did exactly what I mentioned in the first paragraph. They reviewed it, operating from the premise, I'm an expert, so I'll record my anecdotal impressions and offer them as evidence. That put a metaphorical pebble in my shoe and bothered me. So I decided to chase a more empirical concept of code quality with my practice.

Don't get me wrong. The proprietary nature of source code and outcome data in the industry makes truly scientific experiments difficult. But I can still automate the inquiries and use actual, relative data to compare properties. So from that perspective, I'll offer you more data-driven ways to evaluate software quality from source code.

### **Average Cyclomatic Complexity per Method**

Perhaps you've heard of the term cyclomatic complexity. Succinctly put, it describes the number of paths through a piece of code. To picture this, consider the following trivial bits of code.

The code above has a cyclomatic complexity of one, since only one path through the code exists. But add a wrinkle, and you'll have a cyclomatic complexity of two.

You can use this to obtain a broad insight into software quality. Compute the codebases's cyclomatic complexity, normalized over the number of methods. This tells you the complexity of the average method, which carries critical significance. More paths through the code means more tests needed to verify the application's behavior. And this, in turn, increases the likelihood that developers and testers miss verification scenarios, letting untested situations into production. Does that sound like a recipe for defects? It should.

### **Cohesion and Coupling**

[Coupling and cohesion](http://courses.cs.washington.edu/courses/cse403/96sp/coupling-cohesion.html) represent fairly nuanced code metrics. I'll offer an easy mnemonic at the risk of oversimplifying just a bit. You can think of cohesion as the degree to which things that should change together occur together. And you can think of coupling as the degree to which two things _must_ change together.

Because software design forces endless trade-offs and few absolutes, we can't simply declare good and bad here. But some generalities do emerge. Specifically, you want to maximize cohesion while minimizing unnecessary coupling. You can never escape all coupling, or your code wouldn't do anything. And you can't have total cohesion, either. But you can work toward those goals.

Non-cohesive code creates the code smell affectionately known as [shotgun surgery](https://sourcemaking.com/refactoring/smells/shotgun-surgery). You may have experienced this in a codebase where doing something like adding a menu item to a GUI required you to modify 17 different files. Software quality suffers as this leads to necessary changes slipping through the cracks.

Similarly excessive coupling causes quality issues as well, albeit of a slightly different flavor. It causes the application to behave in weird, embarrassing ways. If changing the font on the login button causes some ETL process to fail, you have a problem caused by coupling.

### **Global State**

In the wild, global state frequently becomes the complete bane of software quality. With global state, you have information with a scope of the entire codebase. In a small application, this might not matter, but have you ever seen this scale well? If you have, please send me a link, because it would represent the first time I've ever encountered it.

With global state, you effectively give the software developers the ability to rip holes in the application's metaphorical space-time. They don't need to think through object graphs, interfaces, or anything else. They can simply reach into the ether and set a variable, and reach into it from somewhere else and read that variable. Neat trick, until people set it in 45 different places and read it in 332 others. Then, good luck reasoning about the variable's value at any point in time and in any situation.

Applications with significant global state tend to exhibit specific symptoms of low software quality. They tend to encourage "defect whack-a-mole" wherein fixing one bug just creates another one. This happens because developers can only address production issues through trial and error, reasoning having gone out the window.

### **Source Control Commit Hot Spots**

Go take a look through a codebase's commit history. While there, look for something specific. Do you see clustering around certain files or modules as hot spots? You can easily quantify this and even plot a distribution graph of how frequently developers touch which files.

In codebases with a relatively even and low distribution, you tend to see good software quality as measured by outcome. This happens because these codebases abide by something known as the [open/closed principle](https://en.wikipedia.org/wiki/Open/closed_principle). This principle offers the wisdom that you should design source code elements to be closed for modification, but open for extension.

If that sounds curious to you, think of it this way. Modifying existing code represents a relatively violent operation on a codebase compared to adding new code. Modifying existing code runs the risk of breaking dependent code. Adding code carries no such risk. So the open/closed principle steers you toward adding frequently, but touching existing stuff as infrequently as possible.

Contrast this with a codebase that has commit hot spots. This means people modify the code in question a lot. Do enough assessments, and you'll start to accurately perceive these hot spots as defect factories. Luckily, you can steer your way toward better situations by modifying the design to eliminate these hot spots.

### **Reasoning About Software Quality**

I've offered a series of ways to gain empirical insight into your expected software quality. With all of these, you can easily quantify across entire codebases. You can then compare that quantification with other codebases and observe differences in outcomes that matter to the business. I submit that this beats scanning through source files and saying things like, "this guy didn't even know how to implement a hash code on his object!"

But I think you should take more away than a handful of [application-wide metrics](https://stackify.com/application-metrics/). You should take away a preference for statistical and empirical consideration. Figure out how to quantify trends you observe and form hypotheses about how they impact code quality. Then do your best to measure them in terms of outcomes with the application. We lack a laboratory and we lack non-proprietary data, but that doesn't stop us from taking the lessons of the scientific method and applying them as best we can.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).
