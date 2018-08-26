# DevOps: Who Does What (Part 2)

_Captured: 2018-07-15 at 03:06 from [dzone.com](https://dzone.com/articles/devops-who-does-what-part-2?edition=386202&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-07-14)_

Discover how quick and easy it is to secure secrets, so you can get back to doing what you love. [Try Conjur](https://dzone.com/go?i=289439&u=https%3A%2F%2Fwww.conjur.org%2Flp%2Fget-open-source%2F%3Futm_source%3Ddzone%26utm_medium%3Dpaid_display%26utm_content%3Dpre_roll%26utm_campaign%3Dconjur_os_en), a free open source security service for developers.

This is Part 2 -- make sure you [read Part 1](https://dzone.com/articles/devops-who-does-what) before you continue.

## Next, Let's Talk About Ops

I have talked to countless organizations where operations is in the infrastructure group, and they're part of the run, plan, build, etc. They run everything. They run the platform, they run the infrastructure, they run the middleware, they run the applications.

What we could be talking about here is really DevOps. Let's put operations, let's make operations part of the product teams. Again, it doesn't have to be the same exact individual. It has to be the team though. Instead of having one operations group, let's put operations capabilities into each of the product teams so that the people who are experts in operating the platform product can operate the platform product, and we empower the teams and the application team. We give them the right abstractions so that they can do their own operations.

That doesn't mean that they have to learn the entire stack down to the infrastructure. For goodness sake, no!

We don't all become experts at everything, but we give them the tools and the empowerment to do their own operations. We take a function that was one function, and we split it out over the different product teams.

### The Next One Is Capacity Planning

![](https://itrevolution.com/wp-content/uploads/2018/06/Screen-Shot-2018-06-10-at-11.47.41-AM.png)

I was working with a very large automotive manufacturer in the United States, and I was talking with somebody from their ops team. I was poking at these roles, trying to understand exactly what theirs looked like, and I said, "Who's responsible for capacity planning?" And, I kid you not, the individual from this organization pulled up the IT manual and said, "See, it says right here, we're responsible for capacity planning." It was that rigid. There was one group that was responsible for capacity planning across this entire spectrum.

That's pretty normal. So what happens?

Well, the capacity planning process goes something like this. Really early on, well before production, we have to come up with some estimate of how much capacity you're going to need, and you know what? We're lousy at that. It's impossible to come up with a really good prediction of what the capacity is that we're going to need.

Since, we know that we're lousy at it, the worst thing that would happen is if we underestimate. So we overestimate. We end up over provisioning, and we have resources that are under-utilized.

The answer here is to put capacity planning in both of the places. Now, it's not as easy as that. It comes back to the contract that's sitting between the platform team and the application team. You cannot, for example, have the App team doing their capacity planning and doing the scaling. Capacity planning is not just an estimation function now. Capacity is really capacity management. If I need more, I get more.

But how do I keep the application teams from exhausting the resources that are in the platform? Well, we do that with contracts. Simple things like quotas.

Even if you're using GCP, or Azure, or EC2, or any of the AWS capabilities, you have quotas. Yes, it's very simple to get more, but you have that contract with AWS that says here's the amount of capacity that I need. AWS or whoever your platform team, is going to use those quotas to estimate the actual capacity that they need to provide from the platform. So it's important to come up with that contract and then each of the teams comes up with the processes that they're going to use to both provide enough capacity to their consumers and to estimate their capacity needs going down.

The next ones, you'll notice I pulled from the data team. Now I will confess to you right now that, again, I've been working on Cloud Foundry for the last just about five years, that we as an industry have made a lot of progress on breaking things up and figuring out how to reorganize groups when it comes to application capacity, when it comes to compute, but we haven't done as well on the data side.

For example, in most cases, we're seeing, organizations creating microservices based architectures that if you peek behind the covers just a little bit, you notice they're all tied to the same very large monolithic database. From an organizational perspective, we've seen very little movement on the way that the data team is reorganized and they're the ones that are responsible for providing any kind of database capacity into the organization.

I sometimes like to say this is the group that you go to and they say, "Hi, Oracle is the answer. What's the question?" We want to break that apart as well. Whether these terms are the exact right terms or not, you can notice that I moved the DBA, and I'm considering the DBA, the individual who's responsible for providing the database servers, the database clusters, for providing that capacity. They belong as a part of the platform team.

![](https://itrevolution.com/wp-content/uploads/2018/06/Screen-Shot-2018-06-10-at-11.47.48-AM.png)

Now the platform team, can, in fact, be subdivided into smaller two-pizza teams, so you might still have a team that specializes in providing relational database capacity, another team that specializes in providing compute capacity, another one that specializes in providing graph database capacity and so on. But we have that team that's responsible for providing those services as a part of the platform substrate.

Then what we want to do is give them control of their databases and their Schemas. Let them evolve their Schemas, let them version those Schemas, let them figure out how they can have multiple Schemas running in parallel, all of those types of patterns. We want to break up data into the right groups as well.

### Next, I Want to Talk a Little Bit About Product Teams Needing Product Managers

I'm going to bring another organization into the picture here, and that's the business. What we've had in the past, you'll notice there, under enterprise architecture, are business analysts. Business analysts have generally been in the business of taking the requirements from the business and translating them into something that they can start to launch the rest of the IT process.

What I want to do here is I want to take your business analyst and not make them THE product manager. I want to pair them with somebody from the business, because if you don't pair them with somebody from the business, then you're still throwing things over the wall. Remember the picture at the very beginning, I'm still starting with the business who's throwing things over the wall, and so you're still going to have that conflict, that tension, that finger pointing that happens when we do scope creep, etc. Make them part of the product management team, though, they're now responsible for the scope themselves. There are no longer change orders.

Now, of course, it's not just the application, the consumer-facing application team that needs product managers. The platform team needs product managers as well, and what we found that is really, helpful is that the folks from your enterprise architecture group are really good candidates for becoming the product managers, or maybe pairing with somebody from the infrastructure teams to be the product managers for the platform team.

![](https://itrevolution.com/wp-content/uploads/2018/06/Screen-Shot-2018-06-10-at-11.48.02-AM.png)

> _You'll also notice that I've put enterprise architecture as a part of the platform team, but I've left them over there in their bubble as well._

Now, I've got two things left.

I've got some enterprise architecture roles, and I've got enterprise application roles.

![](https://itrevolution.com/wp-content/uploads/2018/06/Screen-Shot-2018-06-10-at-11.48.08-AM.png)

> _The third house that I'm going to add is your enterprise applications house._

So DCTM, you're probably wondering what that is.

Documentum Enterprise Application was built 30 years ago. It's one of those monolithic applications. Built on top of kind of a three-tier architecture. It's got that big old Oracle database, or a sequel server database at the bottom. Very resilient, resilient storage systems. It's got a big, thick tier in the middle, and it started out with the desktop client application, and this was pre-web, of course.

You all have these types of enterprise applications in your organization, and we have to continually deal with them. The first thing that I'll tell you is that I want you to start thinking about your Documentum team, or your enterprise application team, as the product teams.

Now, they are not going to be able to move as agile as some of those other organizations. However, there are like Rosalind Radcliffe who is applying DevOps principles to the mainframe. The lessons that you may learn from her are the lessons that you should be applying here. You can do product management, you can do DevOps in these settings as well.

These systems, however, will tend to move, particularly while you're still making the DevOps transformation at a pace that is not quite the same cadence as the daily or multi-daily releases that are happening by the App teams.

![](https://itrevolution.com/wp-content/uploads/2018/06/Screen-Shot-2018-06-10-at-11.55.56-AM.png)

What we want to do now is create multiple product teams, multiple application teams across the top that are leveraging both the new platform as well as connecting into the enterprise systems. I call that the legacy service team here.

![](https://itrevolution.com/wp-content/uploads/2018/06/Screen-Shot-2018-06-10-at-11.56.05-AM.png)

This is the team that is generating the interface that's going to mediate between the application teams on the left-hand side, and the enterprise system on the right. Notice that it's a product team just like any of the other product teams with a product manager, capacity planning, all of those types of things.

### Coming Down to the Final Couple of Roles Here…

Let's talk a little bit more about enterprise architecture. I was at a conference a couple of years ago, and I was having breakfast with a number of individuals that I didn't know. There was somebody from QVC. There were two individuals from that organization there. One of the individuals was telling a story where he said, "Last year when I was at the conference, I was part of one of these teams over here. This year I'm in enterprise architecture. Last year I was policed, this year I am the police." I thought, "Remind me not to go work there."

What we want to move away from is this notion of enterprise architecture being the ivory tower. This has been one of the most successful things that I've seen with the organizations that I've been working with. By and large, the enterprise architects love this transformation.

Here's what we're doing, I'm going to introduce a new house. This last house I'm adding is what I'm calling the "Enablement house." It says: take some of those functions that are in enterprise architecture and instead of making them an ivory tower, follow the practices, have them in the role of enabling teams. One of the best ways that you can have them in a role of enabling teams is actually to make them part of the team.

![](https://itrevolution.com/wp-content/uploads/2018/06/Screen-Shot-2018-06-10-at-11.56.15-AM.png)

You'll notice here that I didn't remove them from the enablement organization. These are individuals that can stay as a part of a matrixed organization like enterprise architecture, but they actually spend part of their time pairing in the teams. They become parts of the team members. They're measured on that team success. It's important, though, that they still have this broad view across the different projects because that's where you start to see about the reuse.

One final thing that I want to add into this picture is that enterprise architecture is not the only organization that I'm suggesting that stays together as an organization and is then paired into the product teams. Other organizations like that would be things like information security.

That is the final sorting that I want to do, now, let the wizarding begin.

**Attend the DevOps Enterprise Summit in [Las Vegas: October 22-24, 2018](https://events.itrevolution.com/us/)**

Conjur is a free open source security service built by DevOps engineers. With integrations with all your favorite tools and an easy way to secure secrets, it's a no brainer. [Come check it out!](https://dzone.com/go?i=289440&u=https%3A%2F%2Fwww.conjur.org%2Flp%2Fget-open-source%2F%3Futm_source%3Ddzone%26utm_medium%3Dpaid_display%26utm_content%3Dpost_roll%26utm_campaign%3Dconjur_os_en)
