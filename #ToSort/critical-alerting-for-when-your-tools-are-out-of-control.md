# Critical Alerting for When Your Tools Are Out of Control

_Captured: 2017-03-08 at 09:26 from [dzone.com](https://dzone.com/articles/critical-alerting-for-when-your-tools-are-out-of-c?oid=twitter&utm_content=buffer5a58f&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

We have all heard stories of DevOps woe. Some tales are sad. Some tales describe true misfortune. Some tales just leave you thinking, _what the heck were developers thinking?_ This story is a tale of the later. This story will tell the tale of how some developers at a start-up in New England created code that was supposed to live and work on AWS EC2 servers. However, the developers never thought to test what they were spinning up or to put critical alerting in place for when things went wrong. And that is where our tale of woe begins.

## Tale Number 1: Automation Destroyed the World

What the tool was supposed to do has long since been forgotten but the horror and nightmares it caused will not go away so soon. At the start-up I am referring to here, every protocol was seemingly ignored when this new tool was written and deployed. There was little documentation, little testing, way too much privilege, and no way to muzzle the tools. The code had to run at highest privilege which means it could do anything. This is bad because code that can do anything will do everything. Somehow, the engineers just thought the tools would work without these necessary considerations.

This tool was built to reach out to AWS and scale up infrastructure based on requests, but the tool did not work consistently. For example, the base instance of the code worked but when a new instance of the code was required and new servers were spun up, the tool didn't reach out to the GitHub repository to get a new copy of the code. Instead, the code had to be pushed manually.

Additionally, when the servers were no longer needed, the code would scale down by killing oldest instances first. And indeed, this is how scaling down should work. However, the tool didn't check if the code was working on the newest servers before destroying the old ones. And, as the tool didn't efficiently push code to the new instances the company was left with these new servers that had no code running on them.

### The Resolution: How Automation Was Muzzled

Eventually, the issues of the original tool were recognized. The reality is that the tool was actually not a terrible tool. The problem was that it was that it was not fully thought out. What the tool needed was another tool and critical alerting to monitor the original tool. This second tool which was eventually built could check if the data and the environment were in good order. The second tool checked if the input was healthy. If not, the original tool would do nothing. The second tool checked if the environment was not healthy. If it was not, it would do nothing.

In addition to validation requests, code also needs critical alerts to notify developers and Ops for when it doesn't work as planned. You wouldn't let a developer deploy code without testing. Similarly, you cannot build a tool and assume it works the way it does on laptop. Critical alerting tools such as OnPage are clearly needed in DevOps to ensure requests and environmental checks are working.

## Tale Number 2: Automation Quickly Balloons Your Amazon Bill

In this second tale of DevOps horror and woe, another New England start-up had a group of its developers create a tool for spinning up infrastructure. When this tool decided it needed something, it would go out and build it. That is to say, the tool had no dependencies. What does that exactly mean? That means that if the tool wanted to build a SQS queue, it could. If the tool wanted to create an SNS operator, it could. If the tool wanted to build up another server, it could. Again, the tool was designed to have no dependencies and indeed it did not. Every instance could create anything and everything.

Sounds great, right? Not exactly. The problem with having no dependencies is that you can build everything and there is a cost to building infrastructure. No dependencies can start costing your team a lot of money very quickly. That is indeed what happened in this case. The lack of control on this tool enabled it to create lots of unnecessary infrastructure.

The lack of supervision also allowed for the creation of thousands of CloudWatch metrics. These thousands of metrics, however, were initially unbeknownst to the DevOps team. As the team was using Datadog to check CloudWatch metrics, Datadog would make API calls every 10 minutes to check the metrics. However, as there were 80,000 CloudWatch metrics as a result of all of the infrastructure and the metrics were checked every 10 minutes, that soon became a lot of API calls. AWS charged the company anytime it made more than two million API calls per month. However, with 80,000 metrics being called every 10 minutes, the company very quickly exceed two million calls.

The only recognition of how far things had gone out of control was only the bill came at the end of the month and the team realized their error.

### Fix It!

From a pure DevOps perspective, there should have been - from the very beginning - a clear understanding of what the code was designed to do and how the Ops team would monitor the tool. Should it ever be the case that infrastructure is built and Ops doesn't know about it? Probably not.

What proved the saving grace in this situation was critical alerting. Any time costs exceed $_x_, the managers would receive an alert. Any time new infrastructure was spun up, the managers would receive an alert. With a tool like OnPage this company, could have easily created low priority and high priority alerts based on the how big the bill was or how much new infrastructure was created.

Furthermore, developers were now given their own account that is separate from Testing and Production that does not create new infrastructure that impacts Ops. Now Ops can create and ideate all they want without costing the company thousands of dollars.

Finally, the company instigated weekly Dev and Ops meetings to ensure that each side is aware of the others' pain points. Ops knows what the goals of the Devs are and vice-a-versa. We actually [wrote a blog](http://onpage.com/bringing-dev-and-ops-together/) on this very point a few months back highlighting the need for this constant back and forth communication between Devs and Ops. Only through this constant communication can companies hope to achieve true collaboration and growth.

## A Cautionary Tale for Developers Everywhere: Use Critical Alerting

While much fault in both tales can be found with the developers, the scenarios are not unique. Most DevOps engineers can probably think of instances where imperfect code was pushed into production. The cautionary tale here lies in that there was no mechanism or alerting platform to recognize the problems. Prayer is not a strategy for effective DevOps. Instead, you need:

  * You need to have mechanisms in place to alert you when things go wrong. 
  * Test! Don't assume that because things are supposed to work, they will. Use effective monitoring tools to keep track of how your system is responding to growth and the data it is given.
  * Create documentation that explains how the tool is supposed to work and how to test inputs.
  * Make sure your Dev and Ops teams are talking to each other and each knows what the code is supposed to do. Never deploy new code and go off on vacation.

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

### Like This Article? Read More From DZone
