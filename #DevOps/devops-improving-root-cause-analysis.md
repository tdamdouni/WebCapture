# DevOps: Improving Root Cause Analysis

_Captured: 2018-08-24 at 16:47 from [dzone.com](https://dzone.com/articles/devops-improving-root-cause-analysis?edition=385414&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-08-24)_

Easily enforce open source policies in real time and reduce MTTRs from six weeks to six seconds with the Sonatype Nexus Platform. See for yourself - [Free Vulnerability Scanner.](https://dzone.com/go?i=290455&u=https%3A%2F%2Fwww.sonatype.com%2Fsoftware-bill-of-materials%3Futm_campaign%3Ddzone%252520-%252520AHC%26utm_source%3DDZone%252520-%252520AHC%2525202018%26utm_medium%3DDZone%252520-%252520AHC%2525202018)

We have all been there in a postmortem when someone says, "Let's get to the root of the problem." And, we all know what that means: who or what is to blame?

We also all know that no one wants to play the blame game, yet we all do. But it isn't our fault (no blame, see what I did there?). It has been the default system for solving problems in business for decades. It is called root cause analysis (RCA).

We can change -- for the better.

## There Is No Root Cause: Emergent Behavior in Complex Systems

I recently watched a presentation from Matthew Boeckman ([@matthewboeckman](https://twitter.com/matthewboeckman?lang=en)) entitled, _There Is No Root Cause: Emergent Behavior in Complex System_. Matthew is a Developer Advocate with VictorOps and a Technology Strategist with Dryan.io. He grew up a systems guy and jokes that he has been in DevOps for 18 years, even though DevOps wasn't around because he has always been nice to developers.

Digging in (pun intended), RCA focuses on what went wrong, and how we can prevent it from happening again.

![](https://lh5.googleusercontent.com/kTMjYbGVl4l6CncGaHLqFotjoMs2CNYzfc2XKDn01ckDBhMYUBAhSP4zbmyS3G4vii1O5evlx1FSq7CPtXABxV9MTgYnDm81Cs8V1aAxbAtJxFevAw2jKc7vE1cSiANfOvtoD-UM)

The core problems with RCA for development is that it doesn't provide for enough complexity and its natural focus is blame, which can undermine a positive DevOps culture.

RCA was more applicable when Waterfall was the development methodology because states stayed consistent for months or even years at a time. In the age of Agile, DevOps, CI/CD, microservices, etc., states of work are in a constant flux. RCA can't provide solutions quickly enough. As Matthew notes, in RCA, things are either good or bad, working or broken, uptime or failure. The reality is that our world is more nuanced.

What Matthew recommends is to look at it through the principle of emergence because it, "separates judgment from the good and the bad binary approach to our system health, and instead focuses on behaviors and interactions, patterns and complexities of our system. With practice and effort, we can manage them to more desirable states."

But what does this look like in practice?

Getting back to the analogy of the tree and its roots, the answer is more of a forest than a tree. Trees are one living organism, forests are ecosystems.

Matthew takes this philosophy and mental picture and gives us a better system -- Cynefin. It is a Welsh word that means habitat, and was created by Dave Snowden ([@snowded](https://twitter.com/snowded?lang=en)), originally for managing IBM's intellectual capital. It draws on research in systems, complexity, network, and learning theories.

![](https://lh4.googleusercontent.com/IPaHcMQBWFbUKiAh1gqkCcD-5JmTcTUeQc6b_r-mGsihmy5lp3ieJIaB-SGT__6jR-8LpvKhMU21JbX4euqZExh2-iga9KKZxQEij4oddSx08yuGDpB6Bgv5SQQA4tHFVC40-_ZT)

Starting in the bottom right quadrant, working counter-clockwise, it goes from simple to more complex.

### **Simple**

These are patterns or behaviors that don't require a great deal of understanding. DevOs is increasingly setting up automated systems to respond to simple issues.

### **Complicated**

These are known unknowns. You can imagine a set of realities where they can occur, and they are probable, but not certain. For instance, a busy harbor might get a storm that causes damage to boats, docks, etc. It is hard for the harbor manager to manage and they need to think about it. This requires people to do some thinking, and it is difficult, if not impossible, to automate.

## **Complex**

This is where we start to see emergent behaviors occur. We don't have the metrics need to understand or manage these problems or you haven't looked at that metric before. We start with probing, going into the system, and exploring. Think of any collection of humans at any scale. Things are still in the scope of probable, but things change quickly. There are many moving parts that aren't predictable and that we didn't fully encounter in our test methodology.

### **Chaotic**

This is, well, chaos. Matthews' real-world example was an entire region for AWS went down, causing other regions to be overloaded as system admins were moving services. In chaos, you _act_, then get a _sense_ of where things are, and then _respond_.

## **Disorder**

In DevOps, this is where you have a lack of communication and collaboration. Here teams need to: _reduce_: figure out what you agree on; _analyze_: build consensus; and, _iterate_: move to a quadrant and continue.

Matthew notes that knowledge and practice move patterns towards more favorable quadrants. But, complacency erodes the process. Complex systems left poorly managed will create increasingly complex processes to manage.

![](https://lh3.googleusercontent.com/Q2QeroWiqeRZSgHClho9T62VpUWytMyOm2oPyNiGkBhd6FdZZmkxxgTC6EK5A00aAjCAwFX0Wbf6i-SewXOX6PuKMsLzWLACH8fD7oMqWlFo9KuFsvHBwu160y0j4q0icIqirXSL)

## **How to Adopt Cynefin**

  * In the moment, ask, what quadrant does this map to?
  * In the post-incident report: How did we manage the pattern? Was it complicated, complex, simple? What can we do to change it?
  * In your sprint planning: Devote time to manage your patterns clockwise. What can we move with a little bit of work?
![](https://lh4.googleusercontent.com/45APSDL11YUpX6yjGp6_jxxJKVcXPYaYRuA4PPUfC5vq8XPQRqNm3KCUmV7FfBoAZKyaWaPmk6Sul1Bu2uxi3PsT9QReFmd2V0ki8KTQMO-pY2_RJjSv-vJxTSNpqJIPxQpDee2n)

> _The reality is that RCA is really only present after the fact. Cynefin calls us to action._

Convinced that Cynefin might be just what your organization needs or want to dig a little deeper? Share and watch Matthew's full talk above or check it out [here](https://youtu.be/EbcLmgrpLN4). You can watch any of the 2017 AllDayDevOps sessions free-of-charge [here](https://www.alldaydevops.com/all-day-devops-2017-recordings).

## All Day DevOps 2018

[All Day DevOps 2018](https://www.alldaydevops.com/) is just around the corner! Registration is available [here](https://www.alldaydevops.com/register?utm_campaign=2018%20All%20Day%20DevOps&utm_source=SPONSOR%20-%20Registration%20\(DZone\)&utm_medium=DZone).

The **free**, online conference goes live on October 17th, offering 100 different practitioner-led sessions, each one 30-minutes long. With 5 separate tracks: [CI/CD](https://www.alldaydevops.com/addo-speakers/tag/ci-cd), [Cloud-Native Infrastructure](https://www.alldaydevops.com/addo-speakers/tag/cloud-native-infrastructure), [DevSecOps](https://www.alldaydevops.com/addo-speakers/tag/devsecops), [Cultural Transformations](https://www.alldaydevops.com/addo-speakers/tag/cultural-transformation), & [Site Reliability Engineering](https://www.alldaydevops.com/addo-speakers/tag/site-reliability-engineering), and [100 speakers](https://www.alldaydevops.com/addo-speakers), there's sure to be something for everyone.

And speaking of _everyone,_ if you're part of an organization with 20+ people that want to attend the conference (again, it's free!) then you should consider joining the[ Club 20 program](https://www.alldaydevops.com/blog/introducing-club20) so that you might get your company logo added to the ADDO site. Check out some of the Club 20 participants [here](https://www.alldaydevops.com/club-20-all-day-devops) and consider joining them.

Hope to see you online at the show!

Automate open source governance at scale across the entire software supply chain with the Nexus Platform. [Learn more.](https://dzone.com/go?i=290456&u=https%3A%2F%2Fwww.sonatype.com%2Fwp-enforce-open-source-policies-with-confidence)
