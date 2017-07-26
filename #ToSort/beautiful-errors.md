# Beautiful Errors

_Captured: 2017-05-21 at 20:16 from [dzone.com](https://dzone.com/articles/beautiful-errors?oid=twitter&utm_content=buffer4d0f9&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Evolve your approach to Application Performance Monitoring](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html) by adopting five best practices that are outlined and explored in this [e-book](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html), brought to you in partnership with [BMC](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html).

The following code in a recent PR caused it to be rejected. Can you figure out why?

![image](https://ayende.com/blog/Images/Open-Live-Writer/Beautiful-errors_11ADF/image_thumb.png)

The error clearly states what the error is, but it fails to provide crucial details -- namely, _which_ files have been corrupted. If I'm seeing an error like this in my logs, I need to be able to figure out what happened, and not just hope and guess.

I'm picking up on this particular change because I found myself tallying in my head the number of comments I make on PRs from our team, and quite a large portion of that involve these kinds of changes. What I'm looking for with error handling is not just to do it properly and handle all edge cases, but to also properly report it so the person who will end up reading this error message (very likely years from now) will have some clue about what they are supposed to do now.

Sometimes, we go to great lengths to ensure that this is the case. We have an entirely different server mode dedicated to handling catastrophic errors, so when you try to get into RavenDB, you'll get a meaningful error page that will at least try to give you an idea about how to fix this issue, for example. The sad part is that it is very easy to have a single error sour up a really good experience because it doesn't provide you with the right information to fix it.

We spend a _lot _of time just crafting errors properly. They go to the log, they are sometimes blocking the UI (if the server cannot start), and we have a dedicated alert system that handles error and alert distribution across the cluster so that an admin can get into any node and see all the stuff that they need to know about across the entire cluster.

Learn tips and best practices for optimizing your capacity management strategy with the [Market Guide for Capacity Management](https://dzone.com/go?i=161136&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-BCO-GartnerMarketGuide-CapMgmtTools-AR.html), brought to you in partnership with [BMC](https://dzone.com/go?i=161136&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-BCO-GartnerMarketGuide-CapMgmtTools-AR.html).
