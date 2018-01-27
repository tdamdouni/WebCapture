# How to Reduce Tech Debt: A Practical Guide

_Captured: 2017-10-17 at 15:19 from [dzone.com](https://dzone.com/articles/how-to-reduce-tech-debt-a-practical-experience-gui-1?edition=332507&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=agile%202017-10-17)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

So here we are going to talk about **what technical debt** really **is** and how we can reduce it. Everything you wanted to know is here - actual practical steps.

Let's say, you want to outwork your competition and add features before competitors, the release date is pressing on you, and your client wants the new stuff right here and right now. What do you do then?

Well, you might start working quickly and dirty - some examples:

  * You "forget" to upgrade to the new release of the compiler.
  * You don't follow UI guidelines.
  * You promised to add many features to the client in a short period of time and now you are short on time.

As a result, you add something new and everything looks fine… until it is not. After the product release, you start getting feedbacks from unsatisfied users: they found bugs and the client does not understand what is going on.

## Congratulations, You Have Technical Debt!

Technical debt is a metaphor which explains the situation when you have two choices of adding functionality: a long-term good solution which needs lots of time **or** a quick but messy and unpredictable solution. When you choose an easy solution, you have tech debt which results in code problems, bugs, and difficulties with the delivery of the future features.

### Why Does It Happen?

In a [study by the Software Engineering Institute](https://insights.sei.cmu.edu/sei_blog/2015/07/a-field-study-of-technical-debt.html), 1318 qualified IT-developers defined the reasons for **technical debt in Scrum**. You can see the results in the diagram below or go to the[ original link](https://insights.sei.cmu.edu/sei_blog/2015/07/a-field-study-of-technical-debt.html).

![Image title](https://dzone.com/storage/temp/6879266-1.png)

As a company with solid experience in reducing technical debt, we created a list of the possible problem causes based on the research above and our own experience.

  * Poorly qualified developers who choose short-term solutions over a long-term one because they don't know the alternatives.
  * Competition and market pressure: the team wants to outrun the competition, surprise users, and bring new technologies to the market.
  * Budget and time pressure, because the client wants everything right now.
  * Ignoring the possible consequences of TD (happens especially with inexperienced developers). If you are not completely sure whether your developers have enough qualifications and knowledge on **how to calculate technical debt**, don't take a risk.

### Is Tech Debt Such a Bad Thing?

Not all the time. There are different** types of technical debt** \- in some cases, it might actually be a good thing.

Firstly, when you are a newcomer to the market, you have to impress users with your features and ideas. Sometimes, you have to do it fast - before your competitor does. So spending time on a long-term solution is not the best idea.

Secondly, sometimes technical debt is a part of your company growth: you release new features and products which help your clients and make your company well-known. If developers spend too much time on fixing insignificant bugs, it can be a straight road to stagnation.

## How to Manage Technical Debt Using Agile

We have already gone through the main theoretical aspects of TD. So now it feels like time to discuss real practical actions: what you are going to do if you have technical debt?

Here we have some tips which have been proven to work.

### You Have to See Your Technical Debt Very Clear

Keep a regularly updated Technical Debt List. In order to solve problems, you have to know exactly which problems you are going to solve. My team uses the practice of creating a Debt Backlog: it is a comfortable technique which helps estimate the consequences, calculate the debt, and track debt by its name.

### Debt Backlog - My Natural Healer iPhone App

![Image title](https://dzone.com/storage/temp/6879279-2.jpg)

**How to avoid technical debt** \- our Debt Backlog

[SEI Research about Technical Debt](https://insights.sei.cmu.edu/sei_blog/technical-debt/) showed that most executives, developers, and project managers are unaware of their TD (42%), 26% had no opinion, and only 10% were managing TD. Many companies are chasing new trends while forgetting the possible magnitude of its consequences (i.e. creating a security risk).

Again, keep your enemies closer- know your technical debt and control it.

### Make a Schedule

When we talk about financial debt, it is obvious that you have to plan everything: what and when you are going to pay to get rid of the debt. You save money each week or each month and pay it. The same thing works with TD. It is important to have practical experience on **how to reduce technical debt**: for example, we organize the "clean-up" periods when all the developers work on reducing TD.

### Do Not Let Technical Debt Buildup

On my team, we practice the "Boy Scout" rule, which is: always leave the code cleaner than it was before. It is impossible to reduce technical debt all at once - do it with one piece of code at a time (and don't forget to update your Technical Debt List in the process).

### Recheck Your Definition of "Done" and "Ready"

You might need some changes. For us, it was helpful to add a "Review" column to our working boards. Also, we practice creating checklists - so developers double- and triple-check everything they work on.

### Test Your Solution

Each developer knows that testing is important yet not everyone is doing it responsibly enough. We made it a rule - to test each new solution because this is the most objective way to see each problem clearly.

### Use Tools to Manage TD

The research by SEI showed that only a few developers and managers are using tools to measure and track their technical debt. There is a list of tools and **metrics of technical debt** they listed - check it out yourself.

![Image title](https://dzone.com/storage/temp/6879288-3.png)

> _Tools used for managing technical debt according to SEI Research_

### Talk to Your Client About TD and Its Cost

You can show some case studies that we talked about or show your risks calculation. When your client knows about possible TD, he or she is more likely to give you more time on the project.

### Ensure Stakeholders That Architecture Growth Is Akin to Any Application Growth

For any new features that we add to an application, we should have an equal extension in architecture in the initial phases of a Sprint. This practice has been well described in the SAFe framework as having an architectural runway that is parallel to the application runway. This can be planned based on the requirements of the application. This way, we'll reduce technical debt by following proper engineering processes.

### Plan and Predict Your Technical Debt in Your Developing Process

Write it down, save the information, and schedule the reducing date. If you are aware of possible consequences, it is much easier to reduce them (planning will save you plenty of time during your clean-up periods).

### Let's Go Through the Main Points One More Time

  * Before working on a project, calculate the possibility of having technical debt, analyze your architectural choices, add checklists, and "Review" columns to your working boards.
  * Technical debt is not necessarily a bad thing if you have calculated the risks and planned how you are going to reduce it in the process.
  * Communicate with your team and client. If everyone knows about the **technical debt in the infrastructure**, your work will be much more effective.
  * Don't be afraid to consult professionals. Everything that we described here looks easy at first glance, but practically everything will be much more complicated. As a company which helps with reducing technical debts, we have seen cases where the project managers wanted to reduce very complicated TD on their own - and in fact, they only made the situation worse.
  * Don't let the problems build up - leave the code cleaner than it was before, control bugs, and update your Technical Debt list.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

Opinions expressed by DZone contributors are their own.
