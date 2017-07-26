# Workflow Tips to Ship Faster Without Sacrificing Security or Quality

_Captured: 2017-06-13 at 17:16 from [dzone.com](https://dzone.com/articles/workflow-tips-to-ship-faster-without-sacrificing-s?edition=304170&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-12)_

Address your unique [security needs at every stage](https://dzone.com/go?i=216224&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity.html%3Fcmp%3DDZone-SIG-pre) of the software development life cycle. Brought to you in partnership with [Synopsys](https://dzone.com/go?i=216224&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity.html%3Fcmp%3DDZone-SIG-pre).

[Release early and often](https://about.gitlab.com/2016/07/21/release-early-release-often/), respond quickly to customer feedback, iterate. Rinse, repeat. The value of getting new features and products in front of customers faster has made its mark on the business world. As a result, development teams are under pressure to shorten release cycles and meet tighter deadlines all while maintaining high quality and security standards. How do experienced teams do it?

Accelerating the development lifecycle without cutting corners is no easy feat but it can be done. While there's no "silver bullet" solution, adopting a security-first mindset and a few workflow best practices can help.

Watch our webcast with HackerOne below to get all the details on how you can build in quality and security checks throughout your development lifecycle from GitLab's Product Manager, [Victor Wu](https://about.gitlab.com/team/#victorwu416), and GitLab Security Lead, [Brian Neel](https://about.gitlab.com/team/#b0bby_tables).

You can watch the recording, check out the slides, and read a few of the highlights below.

## Security as a First-Class Citizen

Ensuring every line of code is secure is a shared responsibility, meaning security should be at the front of your mind from the very beginning of the development process. Don't wait until the very end to start the conversation around security and check for vulnerabilities.

> "We want to take security and make it a first-class citizen. You want security controls baked into each stage of your development process. When we develop software and we develop in small chunks, we always say we want cross-functional collaboration. We want people at the table earlier on." \- Victor Wu, Product Manager, GitLab. 

Whether you have dedicated security experts, or perhaps a lead engineer who's wearing multiple hats, talk about security from the get go so that security issues can be identified earlier, and vulnerabilities can be avoided altogether.

## Workflow Best Practices

In the webcast, Victor details how DevOps teams can bake quality and security controls into their workflows so that these checks don't become cumbersome bottlenecks at the very end of the process.

Here are a couple of his highlights:

### Make Smaller Changes and Commit Often

Perhaps the most critical adjustments to make to your workflow is how you actually write and collaborate on code. When we talk about development speed, a big part of this is transitioning away from developing huge portions of code over long periods of time to making smaller changes more often and making that work visible sooner.

> "We want to ship smaller pieces, often. Whether it's in an Agile context, Scrum, or moving away from the more traditional waterfall requirements, we want to ship in small pieces so we can react more quickly and minimize risk." \- Victor Wu 

By adopting this practice, it's quicker to perform code reviews and security checks because reviewers are only dealing with a couple of changes. Then, if there is an issue, it becomes much easier to identify the cause because there are fewer new variables to consider.

### Involve Experts and Reviewers Early in the Development Process

Involving collaborators and reviewers earlier in the development process does two things. First, it can speed up the development process by giving stakeholders an opportunity to anticipate problems _before_ developers begin to write code, and nip them in the bud. It's common to involve your UX team, product managers, and software architects during the planning phase and throughout the code review process, but often security is left out.

Get your security experts involved in the earlier phases of your development process so it doesn't become a bottleneck right before you're trying to release.

> "Let's get our UX folks early on, let's get our business managers involved early on. Let's not wait until very late in the game before we bring our product managers, senior engineers, our architect, and security experts." \- Victor Wu 

Secondly, by keeping all stakeholders involved in the conversation throughout the development process, you can ensure that by the time the code is ready to move to production, most errors have been spotted and corrected.

### Get Code Into Staging or Test Environments Earlier

This goes back to the high-level concept that we want to work on small pieces of code and get them integrated into the mainline branch right away to minimize the risk of something not working, or not accounting for certain things.

"The point of pushing code into production-like environments is to get your feature into a place that looks and functions more like the real world," says Victor. Getting your code into staging or test environments sooner can also help to minimize security risks.

> "You might have certain tools to scan dynamically and inject attacks into your systems, whether that might be directly into your data or your code base. In the same way that you have human testers doing manual testing, in addition to the automated testing, you might have human users doing the security testing as well." \- Victor Wu 

Again, if you're developing in small chunks, and involving stakeholders earlier on in those environments, that they can jump into those environments and start testing the feature.

### Leverage Your Community to Spot and Prioritize Security Issues and Bugs Faster

Even with all the right quality and security checks threaded throughout the development process, problems can slip through. In the webcast, Security Lead, Brian Neel, details the evolution of the security development process (starts at 28:20) and why GitLab's security team uses a bug bounty program to round out our security practices.

Find out how [Synopsys](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity.html%3Fcmp%3Ddzone-sig-post) can help you build security and quality into your SDLC and supply chain. We offer [application testing and remediation expertise](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity%2Fsecurity-testing.html%3Fcmp%3Ddzone-sig-post), guidance for [structuring a software security initiative](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity%2Fsoftware-security-strategy.html%3Fcmp%3Ddzone-sig-post), training, and [professional services](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity%2Fsoftware-security-services.html%3Fcmp%3Ddzone-sig-post) for a proactive approach to application security.
