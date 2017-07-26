# Improve Peer Code Review by Eliminating These Bad Habits

_Captured: 2017-02-21 at 01:30 from [dzone.com](https://dzone.com/articles/improve-peer-code-review-by-eliminating-these-bad?oid=twitter&utm_content=buffer7e85c&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Learn more about [how DevOps teams must adopt a more agile development process](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702), working in parallel instead of waiting on other teams to finish their components or for resources to become available, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702).

In my New Year's [webinar](https://alm.parasoft.com/exercise-your-code-every-day) and subsequent blog post, I explained some of the [habits of highly successful programmers](https://blog.parasoft.com/7-habits-of-highly-successful-programmers) that you can adopt to improve your software quality. Here, I'm going to dive into the first habit: peer code review.

It has been well-established that peer review provides more value than one might expect. As stated in Steve McConnell's excellent book, [Code Complete](http://cc2e.com/):

> _"…the average defect detection rate is only 25 percent for unit testing, 35 percent for function testing, and 45 percent for integration testing. In contrast, the average effectiveness of design and code inspections are 55 and 60 percent."_

An impressive statistic indeed; however, it only pans out if what you're doing in peer review is effective and efficient. Over the years, I've witnessed the many pitfalls that lead to ineffective peer reviews. Avoiding these bad habits may be just as effective as adopting new good ones! Eliminate the bad habits below to avoid ineffective peer reviews.

## **1\. Underutilizing Tools**

To start, you shouldn't be reviewing or looking for anything that can be done by static analysis. This could include branding issues, style issues like curly placement {

don't get me started;

},

or using a specific encryption algorithm. If a tool can find it for you, let it. Free yourself to look deeper into the algorithm, security, and performance characteristics of the code. Doing clever work rather than tedious work also has the side benefit of making the review more interesting to participate in, which in turn makes it more engaging and effective.

## **2\. Reviewing When the Code/Author Isn't Ready Yet**

This is a classic problem that especially pervades calendar-centric organizations. Chances are if you release based on a date, you also review based on a date. The logic goes like this: "I'm not done yet, but we've already scheduled a review so let's at least look at what we have." You know it as well as I do - it isn't a great way to do an effective review, so stop doing it. Make sure the code author is finished, and if they're not ready yet, postpone until they are.

## **3\. Spending Too Much Time on Review**

This is an easy trap to fall into. If a review is taking too much time, you need to rethink something. "Too much" could be either review sessions that are over an hour or sessions that consume too much of the overall development schedule. If reviews take more than an hour, you're probably trying to review too much at once (or the author wasn't ready for the review). After an hour of review, potential effectiveness declines fast, especially for the code authors. Even if the commentary wasn't initially personal, after an unnecessarily long review, the critique can compound and feel more painful.

## **4\. Getting Personal**

Peer review is about the code, not the people. Make sure you are talking about the code and not the developer. Statements like, "This code won't scale as well as we need" is less likely to offend than, "You wrote this badly." Conversely, when you're on the receiving end of the critique, be a good sport. Recognize that everyone's code can be improved, and you can learn from the data you're getting. No matter which end of the review you're on, you can probably be more graceful to facilitate a smooth, pleasant, and speedy review. Think of reviewing as a great way to get a free mentor - everyone wants to get a mentor, but we rarely think about the review process as a mentoring process. Valuing the mentorship may help you resist taking it personally.

## **5\. Doing it at the End**

It's not just a [new year's resolution metaphor](https://alm.parasoft.com/exercise-your-code-every-day) - I really am a big believer that most software quality practices should be treated like exercise. If you try to binge them at the last moment, they won't be effective. You can't run a treadmill the night before a marathon, and you can't do your peer review the night before your release.

## **6\. Inconsistent Follow-up**

How a review is followed-up can greatly affect the value of the review. If you find items during a review and don't check that they're fixed, you're probably wasting your time. The best benefit is found with a consistent process that includes accountability. Make sure everyone knows what is expected of them, and follow up to make sure fixes are being made. If nothing is found in the review, be critical. While this can happen from time-to-time, it should certainly make you suspicious. It may be a sign of quid-pro-quo reviews occurring between developers, or a sign that your development team doesn't understand the value of code review or how to do it properly.

## **7\. Inconsistent Criteria**

If each reviewer isn't looking for the same things, you will have no idea if your reviews are effective. The scope of peer view must be based on an unambiguous policy that is clearly written down and can be referenced. Having a checklist may feel constricting at first, but it will help keep the review on track, and serve double duty if you're in a compliance industry like automotive or medical, and you need to prove that you've done an effective review. Eliminating ambiguity takes more discipline than just writing down the policy, although that's a great first step. Ideally, you'd flesh out a couple of scenarios based on your policy and ask different people how they'd do it. It's not uncommon to find companies accepting a status quo where different groups do things differently, and both think the other group is doing it wrong, but both are being allowed under the ambiguous policy. You can do better. Get everyone on the same page - it will improve your quality, provide the consistency necessary for assessment and improvement, and protect you if something goes wrong. If you're in a compliance environment like ISO 26262 or FDA, having consistent criteria will streamline your audits.

I've witnessed peer reviews at a wide variety of organizations and seen where it can be unbelievably worthwhile, as well as a complete waste of time. Building the right tools into the right processes will help ensure that you are gaining value from the process. Support your bad-habit-free peer review system with a static analysis tool that you can depend on for enforcing standards and best practices, and focus on the interesting defects that will make you a better engineer.

[Discover the warning signs of DevOps Dysfunction](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702) and learn how to get back on the right track, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702).

### Like This Article? Read More From DZone
