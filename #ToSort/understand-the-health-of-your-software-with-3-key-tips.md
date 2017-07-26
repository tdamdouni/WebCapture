# Understand the Health of Your Software With 3 Key Tips

_Captured: 2017-05-23 at 03:44 from [dzone.com](https://dzone.com/articles/understand-the-health-of-your-software-with-these?edition=299094&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-22)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

Shipping code both on time and within budget can be difficult when software errors rear their ugly heads.

Software veterans will tell you there's no silver bullet approach to keeping your end users protected from errors. It's pretty much impossible to write flawless code and catch every bug before releases end up in the hands of customers. It's more about understanding the overall health of your software so you can address software errors quickly and effectively.

So how can we get a realistic picture of the health of our software so we can face issues proactively? As leaders in the software intelligence space, we recognize three main ways you can build an accurate picture of your application health:

  1. Use the right KPIs to benchmark your efforts.
  2. Foster a healthy company attitude toward software errors.
  3. Automate the process of finding and resolving errors so you can fix them quickly.

## **1\. Use the Right KPIs to Benchmark Your Efforts**

Which KPIs should you be tracking to monitor the health of your software? We _know_ that what gets measured gets managed, but which metrics give you the most accurate picture of what is _actually_ happening in your application after deployment?

A recent survey by Software Advice found that 60% of project managers want reporting features as part of their error monitoring tools.

![bug-tracking-top-requested-features.png](https://blog.assembla.com/hs-fs/hubfs/bug-tracking-top-requested-features.png?t=1495143447901&width=1953&name=bug-tracking-top-requested-features.png)

> _The team at Raygun are accountable to four KPIs that we know will:_

  * Improve user experience with fewer crashes and faster software.
  * Reduce technical debt.

### **Users Affected by Software Bugs**

This is a much better metric than total error count. It's easy to forget there are people behind the numbers. Reducing your error count still means end users are experiencing a slow buggy app, therefore it's better to measure by user.

If you have 20,000 errors affecting one customer, it's not as critical as 100 errors affecting 500 customers. Be smart where you allocate your developer resources.

### **Median Application Response Time**

The median response time is what 50% of your customers are experiencing (or faster). Get your team to collaborate around making this time faster. Afterall, poor app performance costs money!

### P99 Application Response Time

We also need to appreciate our upper 99th percentile of users. This will usually be pretty slow - but we are aiming for 5 seconds or less, not 30 seconds slow!

### **Resolved Bugs vs. New Bugs**

Instead of managing crash counts (instances of bugs encountered), we find it best to measure bug count. That way, your team is fixing errors as quickly as they are being created.

We use our own software, Raygun, to track these metrics in real time. The key is to make them visible across your whole staff.

Raygun has the ability to create custom dashboards, so whichever operational metrics you use they can be held in the front of mind across your team (and it also makes it easier to show your key stakeholders your progress).

## **2\. Foster a Healthy Company Attitude Toward Software Errors**

Using the benchmarks above, you can start to accept that software bugs will happen, and zero bug software doesn't exist. If Microsoft can be a 300 billion dollar company, spend billions on software quality, and _still have bugs_, then it's best to accept them as part of the development process.

![Collab.png](https://blog.assembla.com/hs-fs/hubfs/Collab.png?t=1495143447901&width=2001&height=1002&name=Collab.png)

The best solution is to build a process to quickly iterate and resolve bugs as they're found. Your development team are in your code base all day long and probably have a great nose for when 'something isn't quite right.'

Encourage your team members to take an investigative approach to errors and performance issues. A crash reporting tool can make this process enjoyable for your team, as they can dig right into the diagnostic details of an error rather than the frustrating process of digging around in log files trying to replicate issues.

This small switch in attitude can work wonders for a team. A collaborative approach emerges and software errors are no longer an afterthought. Code quality becomes a priority and your end users become much happier for it!

## **3\. Automate the Error Resolution Process**

Because zero-bug software is an unattainable goal, the best solution is to build a process to quickly iterate and resolve bugs as they're found. Automating the error resolution process allows you to move faster and reduces the risk of large errors disturbing sprint goals.

For example, at Raygun, we make fixing issues our priority over releasing features. We recognize customers would rather have a great experience than be on the receiving end of buggy features.

![reporting errors.png](https://blog.assembla.com/hs-fs/hubfs/reporting%20errors.png?t=1495143447901&width=1911&height=855&name=reporting%20errors.png)

So, why not prioritize your most important asset - your customers? Tools like Raygun and Assembla are designed to do just that. They help you automate your bug reporting so you can build an accurate picture of the health of your software.

![How.png](https://blog.assembla.com/hs-fs/hubfs/How.png?t=1495143447901&width=2001&height=1002&name=How.png)

Taking a proactive approach to solving errors in your applications will help put your end users first, boosting user engagement and satisfaction.

### **What This Process Looks Like**

At a high level, Raygun automatically reports bugs then promotes them to the issue tracker so fixes can be assigned a time frame and fixed accordingly. At Raygun we assign 20 story points to fixing errors and managing any technical debt.

Here's how the error resolution looks with Raygun and Assembla (you can see how this workflow looks in Raygun and Assembla in more detail [here](https://blog.assembla.com/raygun-integration)).

An error arrives in Raygun and is presented in your dashboard:

![Error group.png](https://blog.assembla.com/hs-fs/hubfs/Error%20group.png?t=1495143447901&width=1911&height=1116&name=Error%20group.png)

> _You can even search for the specific user who reported an issue:_

![Raygun 2 .png](https://blog.assembla.com/hs-fs/hubfs/Raygun%202%20.png?t=1495143447901&width=2001&height=1440&name=Raygun%202%20.png)

When you click on an error group, you can view the diagnostic details, including stack trace, for that particular occurrence:

![stack trace example 1a.png](https://blog.assembla.com/hs-fs/hubfs/stack%20trace%20example%201a.png?t=1495143447901&width=2001&height=777&name=stack%20trace%20example%201a.png)

> _Now for the resolution._

Using Assembla, assign team members, loop in support staff and put this into your workflow within your team's Assembla account. You can then prioritize fixes easily in your Assembla account:

![raygun ticket.png](https://blog.assembla.com/hs-fs/hubfs/raygun%20ticket.png?t=1495143447901&width=1911&height=747&name=raygun%20ticket.png)

You can also easily click to return to Raygun at any stage and view the error diagnostic information again:

![Raygun 4 .png](https://blog.assembla.com/hs-fs/hubfs/Raygun%204%20.png?t=1495143447901&width=2001&height=1269&name=Raygun%204%20.png)

Once a fix has been deployed, Raygun will scan for any problematic deployments including the version, so you can detect whether or not your fix was effective:

Taking a proactive approach to solving software errors will help you to automate the entire process.

![Deployment tracking -1.png](https://blog.assembla.com/hs-fs/hubfs/Deployment%20tracking%20-1.png?t=1495143447901&width=2001&height=1455&name=Deployment%20tracking%20-1.png)

Shipping more features that your customers love is what's important, not chasing software errors.

Tools like Assembla and Raygun are designed to work together to automate your error resolution process. They make it easier and faster to fix errors affecting real people.

If you rely on healthy software to bring in revenue, it makes sense to understand your software health inside and out.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).
