# Why Developers Are Leaving VMs

_Captured: 2017-06-29 at 17:06 from [dzone.com](https://dzone.com/articles/why-developers-are-leaving-vms?edition=305177&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-28)_

What if you could learn how to use [MongoDB](https://dzone.com/go?i=219242&u=https%3A%2F%2Fwww.mongodb.com%2Fmongodb-accelerator-kit%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_DZone_AcKit_6.7%26utm_content%3Dpre-post-roll%26jmp%3Ddzone-ad) directly from the experts, on your schedule, for free? We've put together the ultimate guide for learning [MongoDB](https://dzone.com/go?i=219242&u=https%3A%2F%2Fwww.mongodb.com%2Fmongodb-accelerator-kit%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_DZone_AcKit_6.7%26utm_content%3Dpre-post-roll%26jmp%3Ddzone-ad). [Sign up](https://dzone.com/go?i=219242&u=https%3A%2F%2Fwww.mongodb.com%2Fmongodb-accelerator-kit%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_DZone_AcKit_6.7%26utm_content%3Dpre-post-roll%26jmp%3Ddzone-ad) and you'll receive instructions for how to get started!

I've spent most of my time over the last three years speaking with developers and helping them adopt containers as part of their software development cycle. Although convincing people to look at containers in 2014 was tough, I've been amazed at how quickly that resistance has dropped. Today it's becoming hard to find a developer who hasn't been playing with containers as part of their development cycle. This anecdotal impression was backed up by a recent [survey](http://blog.shippable.com/while-containers-move-to-the-mainstream-some-roadblocks-exist-on-path-to-adoption) showing 89% of developers indicated that they are likely to increase their use of containers this year.

But why are development teams rethinking their processes to embrace containers when they've often spent years of effort building and sharing VMs?

Although teams invested a great deal in VMs, for developers it's never really been a happy marriage. The developers' list of issues with VMs include:

  * **VMs are slow** to build, slow to run and painful to constantly update. This makes the repeated edit, build, debug cycle that's at the core of development clunky and slow -- a cardinal sin.
  * **VMs are stateful** -- I know this isn't inherently bad, but it does make them hard to sync with team members. It also makes them tricky to debug -- if the sequence of software updates I've made to my VM is different than the sequence you made to yours I can end up with behaviors you can't replicate.
  * **VMs are large**, making them painful to move from machine-to-machine or developer-to-developer.

These drawbacks have left teams continually looking for alternatives and containers with their promise of speed, statelessness and portability look like a great fit.

## **Containers Are Fast**

Containers start quickly allowing developers to iterate on their code much faster than with a VM. They're also typically faster to build than a VM as container recipes can be written to take advantage of layer caching.

## **Containers Are Stateless**

This is a mostly-positive. On the plus side, stateless containers will always execute identically for anyone on any machine. You never upgrade a container instead you just trash the old one and replace it with a clean new one. This ends the "well it worked on my machine…" complaint that every developer has heard (and hates).

However, stateful applications do need to be rethought before they're containerized. This is easy when you're building from scratch but requires planning when migrating legacy apps to containers. This is a one-time cost though, so only impacts a project once.

## **Containers Are Portable**

Containers are recipe-based which means that anyone using the same recipe will get an identical containerized runtime regardless of the OS they're on. This makes checking code in other branches or running tests on different configurations simpler and less error-prone.

Many organizations put their container recipe file in the source code repository so that it's version tracked and can be easily picked up by their CI system. This makes changes to it obvious and allows the CI system to build the code and container images simultaneously -- simplifying the task of checking the latest build.

## Containers Aren't Perfect…

This doesn't mean containers are right for every project though. From a technical perspective, containers are still very new and there's still a lot that is changing. This can make them exciting for developers, but for IT teams that have to support them, it can be nightmarish. Docker, for example, is released several times a month and those releases can include major structural changes without a lot of warning.

From a culture perspective, there can also be challenges. VMs have been around for decades which means that developers and operations staff know how to build them, debug them and deploy them. It takes some time for people to work through the process changes required to handle stateless container deployment, replacement (it's not really an upgrade), and rollback.

## …But Containers Will Win

Despite these challenges, even the largest and most risk-averse organizations are piloting container projects. Why? Their speed, consistency, and portability are qualities that developers demand and smart organizations will adopt as soon as possible because it brings faster releases and greater development efficiency. And that means more competitive differentiation.

What if you could learn how to use [MongoDB](https://dzone.com/go?i=219243&u=https%3A%2F%2Fwww.mongodb.com%2Fmongodb-accelerator-kit%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_DZone_AcKit_6.7%26utm_content%3Dpre-post-roll%26jmp%3Ddzone-ad) directly from the experts, on your schedule, for free? We've put together the ultimate guide for learning [MongoDB](https://dzone.com/go?i=219243&u=https%3A%2F%2Fwww.mongodb.com%2Fmongodb-accelerator-kit%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_DZone_AcKit_6.7%26utm_content%3Dpre-post-roll%26jmp%3Ddzone-ad). [Sign up](https://dzone.com/go?i=219243&u=https%3A%2F%2Fwww.mongodb.com%2Fmongodb-accelerator-kit%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_DZone_AcKit_6.7%26utm_content%3Dpre-post-roll%26jmp%3Ddzone-ad) and you'll receive instructions for how to get started!
