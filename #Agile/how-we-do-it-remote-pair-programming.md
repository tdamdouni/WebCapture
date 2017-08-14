# How We Do It: Remote Pair Programming

_Captured: 2017-07-29 at 08:52 from [www.sonatype.org](http://www.sonatype.org/nexus/2015/03/23/how-we-do-it-remote-pair-programming/?utm_content=buffer31884&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

![Dilbert and Agile](http://www.sonatype.org/nexus/content/uploads/2015/03/Dilbert.jpg)

> _Update: In support of this article, we continue our discussion of_

_[How We Do It_](http://www.sonatype.org/nexus/category/article-series/engineering-2/)_, Inside the Sonatype Engineering Machine: Experiences from our Distributed Agile Team, with a **[live online broadcast**](http://go.sonatype.com/2015NexusWebinarSeries). This week's topic is _**_[The Process (and a little tooling__)_**](http://go.sonatype.com/2015NexusWebinarSeries)_. Please join us at 11:00am EDT, Wednesday, April 25._

In [our last post on TheNEXUS](http://www.sonatype.org/nexus/2015/02/20/how-we-do-it-defining-work-from-a-distance/) we talked about how we as a team get together to define "what" we want to work on. Having identified the "what" and to some extent the "how", where do we go from there? Where does the rubber meet the pavement, and how do we as a team work together? The Nexus team has been experimenting with old tricks in new ways to ultimately help solve a few interesting problems we encounter as [a fully distributed Agile team](http://www.sonatype.org/nexus/2014/11/20/overseeing-remote-developers-dont-even-try/).

There are quite a few problems that our team faces. For instance, we have quite a few knowledge silos contained within our team. Certainly this problem is not distinct to our team but it can become amplified by other problems we encounter. One such problem we have is that working remotely there is a tendency to proceed as lone wolves rather than as a pack. Communication is a subtle art at the best of times, and even a slight increase in the cost of sharing knowledge creates a pressure toward solo work. Left unchecked, this perception of lower cost solo work can cost the team and business a lot in the long run.

Nexus as a team is spread across a good portion of the Northern Hemisphere. Lunch for some of our members is when the rooster cries for others. As you can see in the picture below, we have roughly three distinct time zone overlaps within the team.

****![Locations of Sonatype Team](http://www.sonatype.org/nexus/content/uploads/2015/03/LocationsOfSonatypeTeam.png)****

> _* courtesy of the nifty Chrome Extension: Figure It Out_

As a team with this setup, a member can be inclined at times to take work and run with it, and eventually this member becomes the reigning expert with specific functionality in Nexus. On the surface this appears great, we have an expert in a functional area! However the high cost comes when that member goes on vacation, or is stuck working on other areas and we end up having to wait to either fix an issue or to create additional functionality.

Imagine for a second that the team member is working on a new format for Nexus such as Docker, but they are the only team member positioned to work on support for NuGet. If a high priority NuGet issue comes in, we either have to pause working on Docker support, or we have to continue Docker and put the NuGet issue on hold. This can add a lot of incremental time to delivery of either issue as we [context switch](http://agile.dzone.com/articles/waste-6-task-switching) and incur [other costs](http://agile.dzone.com/articles/waste-5-delays). We obviously don't like this as it can delay important items to our users.

Another challenge we encounter with our team being fully distributed is that while we are generally working very hard, we are very rarely together. There are no classic water cooler moments for us, no running into your coworker in the hallway, and no [dilbert cartoons](http://dilbert.com/strip/2005-11-16) coming to life! Even though our entire team works remotely, we still desire to work together. When we don't work together we end up becoming a bunch of lone wolves rather than a wolf pack. This runs in contrast to our desire to [create tight knit teams that communicate efficiently](http://www.sonatype.org/nexus/2014/10/23/n-n-1-2-as-small-as-possible-and-no-smaller/) at Sonatype.

One way a team of lone wolves can be negative is in the following example. Imagine for a second that you have seven engineers moving in different directions. Even with the strictest of coding standards each will have their own style and move the overall product's codebase in seven directions. Imagine as well that each member's first feedback on their work may come once they've submitted a pull request for their work. Now imagine that other team members find flaws in the submitted work, or notice overlaps with work they've done. This original engineer now heads back to the drawing board and may have to do a significant amount of rework. Worse yet, another member who did something very similar could have likely spent their time on something else. As we inspect our process, we try and adapt and see what we can do to be more efficient in cases like this.

Starting with some work for Nexus 3 and implementing NuGet as a repository format we took two great guinea pigs and tried out remote pair programming. Building on the example from the previous blog post, we had a Subject Matter Expert on NuGet by the name of Michael Prescott. Chris Wilper functioned as our Co-Pilot, a party that had been involved in the core architecture of the new repository format work but not necessarily in the know with NuGet as much as Michael. We also took a look at members within matching time zones so that the members could get as much time with each other as possible. For example, pairing a member on the West Coast of America with a member in Romania wouldn't give us much to work with.

Our goals for pairing on NuGet were ultimately to bring more team members into the knowledge base on the format itself. Beyond that there are many other advantages that the software development community has attested to such as improved team communication, rapport, continual code review. Thinking these items were important, we started the experiment, and we started it with a set of User Stories, one of which we've made public: [NuGet Proxy Repository](https://issues.sonatype.org/browse/NEXUS-7632).

Some past teams had used the tool [Screenhero](https://screenhero.com/) to do remote pair programming or screensharing. In addition to starting with Screenhero, we used our standard Sonatype VOIP for communication and HipChat as needed.

I find it best to let the team do the talking so below Michael and Chris will explain what they found during this experiment. Did this solve the problems we think we have? What problems did it add? What other problems did it solve? Was it worth doing? Did the tools work properly?

## **Chris:**

Overall, I found pairing to be a positive experience, and there were several clear benefits. Most notably, it helped to break down the knowledge silos: Michael and I were both engaged in working on NuGet functionality from the start, so an immediate benefit was that we both gained the necessary knowledge that we lacked going in. Another advantage was that it lowered the barrier to communication. When you're remote, it's easy to avoid sending an IM or picking up the phone for fear that you're interrupting someone's flow. When you're working together, that question is erased and questions and observations can flow more freely.

On a couple occasions, I also noticed that we kept each other on course in solving the most important parts of the problem at hand. Another benefit that I thought was significant, but is hard to quantify, was the social aspect. Pairing gave us a chance to develop some of the camaraderie that we'd naturally get by being in the same physical location. It also made the work feel a lot more like collaboration, which made it more fun.

The two main challenges I noticed with our pairing experience wouldn't dissuade me from trying it again, but they're worth mentioning.

First, on pairing days, I was more mentally exhausted by the end of the day. I attribute this to the need to focus on the development task while maintaining communication with the other person. Second, I think development was ultimately a bit slower than it would have been if we'd been acting alone. This makes intuitive sense, and it's the price we chose to pay for breaking down the knowledge silos that could have easily formed otherwise. Since Michael and I both had knowledge gaps to fill, the NuGet work represented a perfect opportunity for pairing, and I think we came out ahead.

## **Michael:**

![Author,  Michael Prescott](http://www.sonatype.org/nexus/content/uploads/2015/03/Michael-Prescott.jpg)

I'll echo all of Chris' thoughts, both specifically and the overall sense that it was a positive experience.

Part of the price of admission is that someone's going to watch you blunder around in your weak spots. Chris and I both simultaneously realized we were shy about revealing we could never quite remember that mock expectation API. But a corresponding benefit is that the partner can point out tool-use tips that wouldn't ever be communicated other ways (e.g. IDE navigation or refactoring shortcuts, favorite karaf commands and so on).

As far as dealing with exhaustion goes, I think the continuity of working together a few days at a stretch is important, but perhaps the stints ought not to be quite so long. Perhaps 3-4 days at most, with a few off in between. (This is something I expect individual pairs would work out between themselves.)

In terms of how to use this, I think it's great for dissolving silos and spreading knowledge around. So, I'd recommend it for tackling areas that have a fair bit of design uncertainty, have inherently complex requirements, emergent logistical ugliness, or interfacing with complicated third-party APIs.

In short, remote pair programming has shown strong promise to help with the problems we have historically encountered. However we still have plenty of experimentation left to do! This experiment has been largely limited to a small portion of the team, and we need to see how others take to it. As well, we need to continue capturing data or making observations to see if our assumptions around both the quantitative and qualitative hold true. Stay tuned for more experiments and sneak peeks into our growing process.
