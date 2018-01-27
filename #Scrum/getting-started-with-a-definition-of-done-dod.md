# Getting Started with a Definition of Done (DoD).

_Captured: 2018-01-13 at 10:18 from [dzone.com](https://dzone.com/articles/getting-started-with-a-definition-of-done-dod?edition=352110&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-12)_

[Download this white paper](https://dzone.com/go?i=150025&u=https%3A%2F%2Fwww.scrum.org%2FAbout%2FAll-Articles%2FarticleType%2FArticleView%2FarticleId%2F1029%2FCharacteristics-of-a-Great-Scrum-Team%3Futm_source%3DDZone%26utm_medium%3DArticle%26utm_campaign%3DGreatScrumTeam) to learn about the ways to make a Scrum Team great, brought to you in partnership with [Scrum.org](https://dzone.com/go?i=150025&u=https%3A%2F%2Fwww.scrum.org%2FAbout%2FAll-Articles%2FarticleType%2FArticleView%2FarticleId%2F1029%2FCharacteristics-of-a-Great-Scrum-Team%3Futm_source%3DDZone%26utm_medium%3DArticle%26utm_campaign%3DGreatScrumTeam).

In my last post about professional software teams creating working software, David Corban made a good point. How do you determine what "free from fault or defect" means? Since that is different for each product and may change over time, you need to focus on quality and reflecting that quality in a Definition of Done (DoD).

Your Development Team needs to decide what Done means. They need to sit down and create a list of things that must be true for every increment of software that they deliver. Working software is not specific to a PBI; it's applied regardless of PBI to the entire delivery, not just for each PBI.

> "The increment must be in useable condition regardless of whether the Product Owner decides to release it."  
-- <http://scrumguides.org>

If you can't ship working software at least every 30 days then by its very definition, you are not yet doing Scrum. Since [Professional Scrum Teams build software that works](https://nkdagility.com/professional-scrum-teams-build-software-works/), stop, create a working increment of software that meets your definition of Done, and then start Sprinting. Review what you mean by "working" continuously, and at least on a regular cadence.

## What is a Definition of Done (DoD)

You need to start somewhere, and most often we don't have a greenfield product. Either we are handed an existing product, or we are the team that built it and are switching to Scrum. Wherever your product originated, the code, and thus the product, will not currently be working software. How can it be when you don't have a definition of what working means? So what do you do?

Before you cut a single line of code, you need to decide what "Done" means for your product and your company. It will be defined very differently if you are building firmware for pacemakers or if you are creating an e-commerce portal. Here are some characteristics of a Definition of Done:

  * **A short, measurable checklist: **Try and have things on your DoD that can be measured, that you can test the outcome, preferably in an automated fashion.
  * **Mirrors shippable:** While you might not have shipped your product, [although we recommended it](https://nkdagility.com/continuous-deliver-sprint/), you should have that choice. Your Product Owner should be able to say, at the Sprint Review: "That's awesome. Let's ship it."
  * **No further work:** There should be no further work required from the Development Team to ship your product. Any additional work means that you were not Done, and it takes away from the Product Owner's capacity for the next iteration. Ideally, you have a fully automated process for delivering software, and [never use staggered iterations for delivery](https://nkdagility.com/a-better-way-than-staggered-iterations-for-delivery/).

Your short, measurable checklist that mirrors shippable and results in no further work required to ship your product needs to be defined. I find the best way to do this is to get the Scrum Team (the Product Owner plus the Development Team) into a facilitated DoD Workshop. Without a Definition of Done we don't understand what working software means, and [without working software we can't have predictable delivery](https://nkdagility.com/release-planning-and-predictable-delivery/). Your [Product Owner can't reject a Backlog Item](https://nkdagility.com/the-fallacy-of-the-rejected-backlog-item/), only decide whether the Increment is working or not.

## My First Definition of Done (DoD)

Your Definition of Done does not just magically appear, and your software does not magically comply. Making your software comply with your definition of Done is hard work, and while your definition of Done should organically grow, you need to create the seed that you can build on.

I recommend that you run a workshop with the entire Scrum Team, and likely some other domain experts. If there are Stage Gates that your software has to pass after the Development Team is Done, then you need representatives from those Gates to participate in the workshop. Regardless of your product you likely need representatives with the following expertise; Code, Test, Security, UX, UI, Architecture, etc. You may have this expertise on your team, or you may need to bring in an expert from your organisation, or even external to your organisation.

Some examples of things to put on your definition of Done:

  * **Increment Passes SonarCube checks with no critical errors:** You will be increasing over time, so maybe you need to say "_Code Passes SonarCube checks with no more than 50 Critical errors_" then work on it over time.
  * **Increment's Code Coverage stays the same or gets higher:** Looking at a specific measure, like 90%, of code coverage is a read hearing and tells you nothing of code quality. However, it might be advantageous to monitor and measure for adverse change in code coverage, and we [always advocate for TDD practices](https://nkdagility.com/you-are-doing-it-wrong-if-you-are-not-using-test-first/).
  * **Increment meets agreed engineering standards: **You should decide rules for naming of methods, tests, variables and everything in-between. Start small and add over time. Link to your agreed standards on a Wiki and continuously improve and expand your rules. Automate if possible.
  * **Acceptance Criteria for Increment pass:** Making sure you at least meet the prescribed criteria is a laudable goal and [automating them with ATDD practices](https://nkdagility.com/you-are-doing-it-wrong-if-you-are-not-using-test-first/) is even better.
  * **Acceptance Tests for Increment are Automated** \- Make sure that you automate all of your tests. If you think something will break, then you should have a test for it.
  * **Security Checks Pass on Increment: **Use an automated tool as part of your build and check for known security vulnerabilities. You will not find all of your security issues, but at least don't do things we know to be reflective of poor Security.
  * **Increment meets agreed UX standards** \- Again, have a Wiki page and make sure that you check it twice. If you are not using an automated DoD entry, then you need to agree as a Team that you have met the criteria.
  * **Increment meets agreed Architectural Guidelines: **Wiki's are fantastic for this, but automate what you can.

Whatever Definition of Done you come up with it is unlikely that your entire Product currently meets the criteria. You are not yet doing Scrum. Before you start Sprinting, you need to focus on making sure that your current Increment meets your new Definition of Done. Focus on quality, which is what the Development Team is accountable for, and make sure that your Increment meets that new quality bar before you start. The next Increment can only reach the quality bar of all those that came before do.

Create a Working Increment of software that meets your definition of Done and then start sprinting. Keeping your software in a working state [will require a modern source control system that provides you with the facility to implement good DevOps](https://nkdagility.com/getting-started-with-modern-source-control-system-and-devops/) practices.

## Growing your Definition of Done (DoD)

It's super important that quality is always increasing, and that means that you will need to at least reflect on your Definition of Done on a regular cadence. In Scrum, this cadence is defined by your Sprint length, and you have a Kaizen moment at the Sprint Retrospective. That does not mean that you don't reflect on your DOD all the time, you do. You reflect continuously on wither your increment currently meets your DoD, and what you need to do to get it there. You should always be reflecting on whether your DoD fits your needs. If your Development Team finds that something is missing from the DoD halfway through the Sprint, then they should go ahead and add it, making sure that they are not endangering the Sprint Goal.

You may discover that you have a performance problem with your product as David Corban pointed out in my previous post. How do we make sure that we fix that issue? As I see it there are two pieces to this once you are in flight. You can Scrumble (stop Sprinting because of poor quality), and fix it, or you can integrate this new knowledge into your product cycle.

If it is a significant issue that results in you not having working software, then you need to stop and fix. In Scrum, this is called a Scrumble, as a reflection that the Development Team stumbled because something is missing. You should stop adding new features and create working software before you continue Sprinting and adding new features. Once you have repaired the issue, you can increase your Definition of Done to make sure that all future Increments meet the new requirements.

If it is less significant, you might want to keep working and add what you need to your Product Backlog. You can then deliver improvements over the next few Sprints that mitigate and then resolve the identified issue. Once you have resolved it, you can then pin the outcome by adding something to your DoD.

**Always look for ways that you can increase your quality. What does your definition of Done look like today?**

[Learn more](https://dzone.com/go?i=259322&u=https%3A%2F%2Fwww.scrum.org%2Fresources%2Fconvergence-scrum-and-devops%3Futm_source%3Ddzone%26utm_medium%3Ddevops) about the myths about Scrum and DevOps. [Download the whitepaper](https://dzone.com/go?i=259322&u=https%3A%2F%2Fwww.scrum.org%2Fresources%2Fconvergence-scrum-and-devops%3Futm_source%3Ddzone%26utm_medium%3Ddevops) now brought to you in partnership with Scrum.org.
