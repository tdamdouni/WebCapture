# 5 Pillars of Learning Programming

_Captured: 2018-06-18 at 07:09 from [dzone.com](https://dzone.com/articles/5-pillars-of-learning-programming?edition=382200&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-06-17)_

**Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=291448&u=http%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fagile-test-data-management-the-new-must-have.html%3Fcid%3DNA-DSP-CD-AGJ-000195-00001461-000001106%26utm_source%3Donline_ads%26utm_medium%3Ddzone%26utm_campaign%3Dtdm_acquire%26utm_content%3Dagile_tdm_report-pre_roll). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=291448&u=http%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fagile-test-data-management-the-new-must-have.html%3Fcid%3DNA-DSP-CD-AGJ-000195-00001461-000001106%26utm_source%3Donline_ads%26utm_medium%3Ddzone%26utm_campaign%3Dtdm_acquire%26utm_content%3Dagile_tdm_report-pre_roll). **

![Image title](https://dzone.com/storage/temp/9445448-5-pillars.png)

Learning how to program is hard. I often find that university courses and boot camps miss important aspects of programming and take poor approaches to teaching rookies.

I want to share the 5 basic pillars I believe a successful programming course should build upon. As always, I am addressing the context of mainstream web applications.

A rookie's goal is to master the fundamentals of programming and to understand the importance of libraries and frameworks.

Advanced topics such as the cloud, operations in general, or build tools should not be part of the curriculum. I am also skeptical when it comes to Design Patterns. They presume experience that beginners never have.

## Test-Driven Development (TDD)

![Image title](https://dzone.com/storage/temp/9445410-tdd.png)

TDD brings a lot of [benefits](https://www.rainerhahnekamp.com/en/why-we-test-do-things-faster-with-test-driven-development/). Unfortunately, it is an advanced topic that beginners are not entirely ready for.

Beginners shouldn't write tests. This would be too much for their basic skill levels. Instead, they should learn how to use and work with tests.

Each programming course should center around exercises. I extend my exercises with unit tests and provide the students with an environment which is already setup for running those tests.

All the students have to do is write their code and then watch the lights of the test runner turning from red to green. The resulting gamification is a nice side effect.

For example, if the selected technology is Spring, I provide the exercises and tests within a Spring project. The students don't need to know anything about Spring. All they need to know is the location of the exercises and the button to trigger the tests.

Additionally, students must know how to use a debugger and have a REPL at hand. The ability to analyze code during runtime and to have a playground for small experiments is essential in TDD.

The main point is to ensure students don't have to learn basic TDD behaviors after they acquired core programming skills. Changing habits later in the students' career would be much harder than learning those habits now. That's why they should live and breath unit tests from the beginning.

Later in their professional life, they should have an antipathy for projects without unit tests. They should intuitively see the absence of unit tests as an anti-pattern.

## Fundamentals First

![Image title](https://dzone.com/storage/temp/9445414-fundamentals.png)

I hear very often that rookies should immediately start with a framework. This is like teaching people how to drive by placing them in a rally car and asking them to avoid oversteering. This simply ignores the fact that they still mistake the brake for the throttle.

The same applies when we start students with a framework like Angular. Beginners need to understand the fundamentals of programming first. They need to be familiar with the basic elements and what it means to write code before they can use somebody else's.

The concept of a function, a variable, a condition and a loop are completely alien to novices. These 4 elements build the foundations of programming. Everything a program is made of relies on them.

Students are hearing these concepts for the very first time, but it is of the utmost importance that the students become proficient with them. If students do not master the fundamentals, everything that follows looks like magic and leads to confusion and frustration.

Teachers should spend more time on these fundamentals but, sadly, move on far too quickly. The problem is teachers struggle to put themselves into the role of a student. They have been programming for ages and have forgotten what types of problems a beginner has to deal with. It is quite similar to a professional rally driver. He can't imagine that somebody needs to think before braking. He just does it automatically.

I design my exercises in a way that they are challenging but solvable in a reasonable amount of time through a combination of the four main elements.

A good example is a converter for Roman and Arabic numbers. This challenge requires patience from the students. Once they successfully apply the 4 elements to solve the challenge, they also get a big boost in motivation.

Fundamentals are important. Don't move on until they are settled.

## Libraries and Frameworks

![Image title](https://dzone.com/storage/temp/9445415-libraries.png)

After students spend a lot of time coding, they must learn that most code already exists in a form of a library or a framework. This is more of a mindset than a pattern.

As I have written [before](https://www.rainerhahnekamp.com/en/modern-software-development/): modern developers know and pick the right library. They don't spend hours writing a buggy version on their own.

To make that mindset transition a success, the examples from the "fundamentals phase" should be solvable by using well-known libraries like Moment.js, Jackson, Lodash or Apache Commons.

This way, students will immediately understand the value of libraries. They crunched their head around those complicated problems. Now the students discover that a library solves the exercise in no time.

Similar to TDD, students should become suspicious when colleagues brag about their self-made state management library that makes Redux unnecessary.

When it comes to frameworks, students will have no problem understanding the importance once they understand the usefulness of libraries.

Depending on the course's timeframe, it may be hard to devote time to frameworks. But as I already pointed out, the most important aspect is shifting the mindset of the student away from programming everything from scratch to exploring and using libraries.

I did not add tools to this pillar since they are only of use to experienced developers. At this early stage, students do not need to learn how to integrate and configure tools.

## Master & Apprentice

![Image title](https://dzone.com/storage/temp/9445435-master.png)

In my early 20s, I wanted to learn to play the piano. I did not want a teacher and thought I could learn it by myself. 5 years later, I consulted a professional tutor. Well, what can I say? I've learned more in 1 month than during the 5 years before.

My piano teacher pointed out errors in my playing I couldn't hear and made me aware of interpretational things I would never have imagined. After all, she instilled in me the mindset for music and art, both of which were out of reach for me as a technical person.

It is the same in programming. If somebody has no experience in programming, then self-study is a bad idea. Although there are many success stories, I question the efficiency of doing it alone.

Instead, there should be a "master & apprentice" relationship. In the beginning, the master gives rules the apprentice must follow -- blindly! The master may explain the rules, but usually, the reasoning is beyond the apprentice's understanding.

These internalized rules form a kind of safety net. If one gets lost, one always has some safe ground to return to.

Teaching should not be a monologue. The master has to deal with each student individually. He should check how the students work, give advice and adapt the speed of the course to their progress.

Once the apprentices reach a certain level of mastery, they should be encouraged to explore new territory. The master evolves into a mentor who shares "wisdom" and is open for discussions.

## Challenge and Motivation

![Image title](https://dzone.com/storage/temp/9445437-challenge.png)

"Let's create a Facebook clone!" This doesn't come from a CEO backed by a horde of senior software developers and a multi-million euro budget. It is an exercise of an introductory course for programmers. Such an undertaking is impossible. Even worse, students are put into wonderland and deluded into believing they have skills that are truly beyond their reach.

No doubt, the teacher is aware of that, but creates such exercises for motivational reasons.

The main goal of an exercise is not to entertain. It should be created around a particular technique and should help the students to understand that technique.

Motivation is good, but not at the sacrifice of content. Programming is not easy. If the students don't have an intrinsic motivation, coding might not be the way to go.

Newbies should experience what it means to be a professional developer. They should know what awaits them before they invest lots of hours.

For example, many business applications center around complex forms and grids. Creating these is an important skill that exercises can impart. An application similar to Facebook & Co. might not be the best lesson for students to learn.

Similarly, a non-programmer might be surprised at how few code lines a developer writes per day. There are even times where we remove code or achieve nothing.

Why? Because things go wrong all the time. We spend endless hours fixing some extremely strange bugs that turn out to be a simple typo. Some tool might not be working just because a library got a minor version upgrade. Or the system crashes because somebody forgot to add a file to git. The list can go on and on.

Students should enjoy these experiences. An exercise targeting an unknown library under time pressure might be exactly the right thing.

The sun isn't always shining in real life. Beginners should be well-prepared for the reality of programming.

## Final Advice

Last but not least: one cannot become a professional programmer in 2 weeks, 2 months or even a year. It takes time and patience.

Trainers should not rush or make false promises. They should focus on whether students understand the concepts and not move on too fast.

**[See how three solutions work together](https://dzone.com/go?i=291449&u=https%3A%2F%2Fwww.ca.com%2Fus%2Ftrials%2Fca-agile-requirements-designer.register.html%3Fcid%3DNA-DSP-CD-AGJ-000195-00001462-000001108%2520%26utm_source%3Donline_ads%26utm_medium%3Ddzone%26utm_campaign%3Dard_acquire%26utm_content%3Dard_trial) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=291449&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=291449&u=https%3A%2F%2Fwww.ca.com%2Fus%2Ftrials%2Fca-agile-requirements-designer.register.html%3Fcid%3DNA-DSP-CD-AGJ-000195-00001462-000001108%2520%26utm_source%3Donline_ads%26utm_medium%3Ddzone%26utm_campaign%3Dard_acquire%26utm_content%3Dard_trial). **
