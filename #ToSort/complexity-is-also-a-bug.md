# Complexity Is Also a Bug

_Captured: 2017-01-19 at 11:10 from [dzone.com](https://dzone.com/articles/complexity-is-also-a-bug?edition=262904&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-01-18)_

The DevOps zone is brought to you in partnership with Sonatype Nexus. The [Nexus suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

Last month, I attended the DevOps Days Tel Aviv conference. I took some notes about the interesting stuff people said -- like many people do during a conference -- and then I put the notebook away -- like most people usually do after a conference.

However, yesterday I was going over my notebook (I guess I wanted to check what I still had to do from my endless to-do-lists), and I stumbled onto my notes from the conference. Among all the scribbles and drawings, there was a sentence that caught my eye, something I had written and then forgotten, but that when I saw it again, it managed to grab my attention.

> "Complexity is also a bug."

## Complexity Is Increasing and Will Continue to Increase

Below the sentence I wrote were the notes that the speaker had said in his presentation.

He was a founder/programmer/geek/CEO from the Valley, and he explained how from his point of view, complexity in software and applications was increasing and would continue to increase with time.

The point he was driving to was that as development companies, we have to make choices about who handles this complexity. He looked at this from a DevOps perspective and so he said that there were three choices for who could take on this complexity: development, IT, or the end users.

To put it simply, applications need to do more: talk to more applications in order to do stuff, do this stuff faster, and do it in more diverse environments. We are not really doing less of anything (unless you count less time spent sleeping and relaxing).

Being this the case, someone needs to "pay the penalty" for doing more, and this penalty could be handled by any of the three teams I mentioned above.

It could be handled as part of the development process by creating more complex algorithms and smarter code to handle all the complexity.

Parts of it could be passed on to the IT, who needs to deploy and configure the system so that it could handle some of this added complexity.

Finally, all the stuff not handled by any of previous two teams would end up being passed to the end user, who would need to work with more complicated installations and configurations and applications that were less friendly.

In the end, what he was explaining is that complexity is a [zero-sum game](https://en.wikipedia.org/wiki/Zero-sum_game), and as part of our development projects, we need to decide who will be handling it.

## **Looking at Complexity as a Bug in the Product**

Complexity is not a feature. It is also not an objective attribute like load level or application response time. Still, it is not less important than any of the other attributes of our products, such as a nice GUI or a good UX. Actually, complexity is usually handled via a combination of features and UX solutions.

Having said that, we need to handle excessive complexity as a bug in the products we are testing, but this may sometimes be trickier than you think.

### **Complexity Depends on the User**

Try to think about two different users: for example, your dad vs. yourself. My father is a great surgeon, but he is pretty bad with iPhone apps. This means that something that is trivial to me may be impossible for him to figure out.

On the other hand, if you compare me with some of the developers we have in PractiTest, then I become the guy who cannot get most of our configuration done straight. In this second case, something that to them may be trivial for me is utterly complex.

### **Complexity Is a Trade-Off**

I think we have all been in those projects where the Product Owner or Product Manager or even the end user comes and says, "Guys, we need to release this! It's time to make compromises…"

Compromises are just another term being used for bugs and missing features. These are the cases when the project is already delayed and we need to deliver something out, even if it is not perfect. In these cases, one of the first things to be "compromised" is complexity.

This is when we agree that we can release a document on how to configure the system manually instead of having the intelligent self-configuration or that the installation will ask many questions that could have been taken from the system directly.

These are not critical things, but depending on who the user is, this may be a blocker for him or her to install the system. In the best of cases, it will be only a nuance that they would have preferred do not deal with.

### **It's Hard to Handle Complexity After the Feature Is Developed**

Imagine you order a car to be custom made for you. You talked about the color, the shape, the interiors, wheels, mirrors, etc.

Then, when they are showing you the finished car you realize that you wanted this car to be driven in the UK where they ride on the right side of the road, that you wanted to save money by having it work with a diesel engine, and that you wanted an automatic car and the one they are showing you works with a stick.

Oops!

Just as making these changes once the car is done will be very costly and it will definitely delay the time you get to drive your car, so is the case with trying to reduce the complexity of the system once it has been done and it is close to being released.

It is true that by working Agile and with iterations, these issues should be reduced, but they will not be eliminated. Many times, the issues won't be discovered until the product actually reaches the end user, so solving the complexity issues or adding new functionality to handle them becomes even more costly and may end up having additional marketing repercussions and costs.

## **Complexity Is an Issue That Needs to Be Taken Seriously **

As you may understand by now, complexity is not only here to stay but it will become more of an issue as our products need to do more and communicate with additional products and solutions in order to fulfill their objectives.

Complexity is also something that, if we don't handle as part of the product design and development, will be passed to our end-users to handle -- or they may choose not work with our solutions because they don't want to or can't handle the complexity we are relegating to them.

Finally, complexity is easier, faster, and cheaper to handle early in the process than later on.

Most importantly, given that your users will see complexity as a flaw in your product, it is better that you start considering it as a bug that needs to be reported and eventually handled by your team.

The DevOps zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).
