# Taking Over a Project: Part I

_Captured: 2017-05-10 at 11:41 from [dzone.com](https://dzone.com/articles/taking-over-a-project-part-1-1?oid=twitter&utm_content=bufferb3adb&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

## Introduction

Have you recently received an existing project to maintain? How should you approach it? Is it worthy of a discussion? What does it mean to take over an existing project, is it just adding new features, fixing bugs, and taking it to the right place? Is there any systematic approach we can uncover for this common process? Well, the reality is that taking over and maintaining a project is an art, a skillset that you sharpen and refine over the years. As such, this process deserves focused attention. In this post, we are going to discuss some of the actions one is required to perform throughout such a process, write them down for the sake of laying down the infrastructure, and then separate out possible actions in our arsenal for targeting such a takeover mission.

## Two Approaches

There are two extreme approaches possible when taking over existing projects, namely, the unmindful and the mindful approach (the first being more commonly used). Of course, you could use either one of these approaches, or some kind of hybrid approach that falls at any point on the continuum in between them.

The unmindful approach is mostly a reactive one, while the mindful approach is mostly a proactive one; you are aware of the things you need to do in order to get this project well maintained and you follow a stringent process. While there is a tendency to take an intuitive approach, there are many similarities between the mindful approach and the unmindful one. However, it's not well structured and formalized, not to mention, it's not based on real lessons learned from past experience.

When equipped with the right information and a solid action plan based on past experiences, you have a better chance of success in taking over an existing project. Experience not only serves you well, it also sharpens your subconscious approach to project maintenance and provides better forecasting and tools for future projects. Moreover, a sharpened mindset provides you with the toolset to take the project to a point where its future maintainers are going to spend much less time in maintenance of the project.

## Two Systems

The two approaches described above have many similarities to Daniel Kahaneman's seminal work (where a Nobel prize was involved). In his work, Kahaneman describes human behavior in two systems, which are, in his own phrasing, System 1 and System 2.

### System 1

The intuitive one, System 1, is based on huge time spans of evolution. It has evolved in different conditions than we find ourselves today, definitely not in the surroundings of non-human computers and intelligent IDEs with crazy static code analysis tools. System 1 is prone to errors, as Kahaneman's experiments prove, and yet it is necessary. Without it, we would not be able to think quickly. This means that we must be cautious with our intuition, especially in processes new to our mind. Humans did not evolve alongside or with information technology. Evolution has not yet had a chance to make us better developers. Therefore, taking over projects and providing good project maintenance depends on the use of System 1 together with the use of System 2.

### System 2

The rational one, System 2, can be best explained by Daniel Kahanman's own thoughts, as a renowned newspaper editor. In this role, he looks over the intuitive unaware system behavior and examines it from above. As an editor, he tweaks the reporter's decisions, approves or disapproves an article, questions the reporters, and gives hints and pointers to the reporters for their future work. The reporters learn from him, even while they continue to use their own talent and intuitiveness.

In this blog series, we hope to duplicate this thought process. You want to examine the intuitive actions involved in taking over past projects and maintaining them in an unmindful and reactive way. You want to review what resulted well and what did not, all this, in order to come up with a checklist based on these existing takeovers.

## Meta-Goal: Easy-to-Maintain Project

With that, we come to the most important item in our checklist. This overall goal of the checklist is to define the steps required in transforming your newly acquired project into an easy-to-maintain project.

So, let's get started. You have just been given an existing project that you need to maintain. What is the best place to start? After a few days have passed, you have likely become more intimate with the project. Do you find the project easy to maintain without the need for a heavy consultation with the previous maintainers? Is it a snap to make changes and automatically test those changes? If so, then we can say that at first glance, you are lucky. In other words, the previous maintainers did a good job and some of the points here are not relevant to you. However, we are realistic. In most cases, this won't be the case and you should rely on a more strategic process to get your project under control.

In that realistic case, our first point is to remember your end goal as a clean coder. As clean coders or professional developers, you have a responsibility for not only working and successfully delivering a project but also for ensuring that any new maintainer, new members joining the team or proceeding us in the future have an easy entrance and a joyful time. Make their life easier. To help in these efforts, you must take immediate action.

In addition, let's take on the following thought: those who maintain a project may not always be other human coders; it may also be you, especially after a long period of time working on other projects and then returning to work on a project. It could also be (and this should not be taken lightly) non-human static code analyzers and complex IDEs. In any case, you want to enable simplicity.

Note: If the project you need to maintain is a super legacy code project, there is a great reference book for working with such types of projects: _Working Effectively With Legacy Code_ by Michael Feathers. This is an excellent book to add to your software development arsenal and would also be valuable for non-legacy code projects.

## Interrogate the Previous Project Maintainers

With the easy-to-maintain project meta-goal in mind, your next step in the checklist should include: "interrogate the previous project maintainers."

Your first step in interrogating should be to engage in an overview of the project, be it the previous maintainers or what they left as previous maintainers. Locate any documentation. Look specifically for architecture documents or slide presentations. Scan code. Play with it and reexamine the documents. Do you see any differences between the architecture documents and what you see in the actual code? Debug the code and statically analyze it using the methods you find valuable. Special consideration should be given to noting the differences. Check production server flows and logs and prepare new questions for upcoming meetings with the previous project maintainers. Refer new questions that you can't resolve to them, and continue this process until the project is under your control, at least conceptually.

An instrumental item that should be included in your checklist involves the discussion with the previous project creators about their motivation for the original project decisions during the initial design and coding phase. This is a key aspect.

Learn more about the alternatives they were considering. It is often impossible to understand the main course of action taken unless you understand the alternatives that were considered and why they got accepted or rejected. Let me stress this again, the alternatives and considerations at the early stages of a project are extremely important, as you are now maintaining an already-baked project. As you work toward the outcome, questions about the design will be raised not only by outsiders but also by your team and yourself.

When analyzing previous alternatives, you begin to understand that the basic design decisions that took place during the design phase of a project may no longer be valid if taken today. You may not need to re-architect your project, but it is helpful to understand it in terms of current maintenance needs. This helps you draw limits and restrictions imposed on a project.

It is important not to become emotional or judgmental over previous decisions, as they could have been the right ones given the time and context. Consider that every project is coded within its own constraints, which means it has its own peculiarities.

Note that a red flag should be raised in the following cases: if you notice a troublesome coding characteristic such as a field used with a totally different name than that of its actual usage, you detect improper function naming. While this topic will be discussed in the refactoring section, you should be scanning the code for similar characteristics and be sure that you understand the correct or incorrect naming conventions and terminology used. These issues can cause headaches and it's best to understand them as early as possible. Attempt to retrieve as much information as possible about why a certain naming convention was chosen or not.

## Summary

In Taking Over A Project: Part I, we acknowledge that we can approach existing projects in two different ways. We favor looking at our past actions to see if there are benefits in adopting previous techniques that we should utilize when taking over a project. Two main points for our checklist include: having a meta-target to produce a well crafted and maintainable project, and consulting with project creators or previous maintainers, that is if possible, and asking about the initial motivation for the key decisions and design based on its current state.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

### Like This Article? Read More From DZone
