# Operation DevOps

_Captured: 2017-08-12 at 19:44 from [www.skankworks.net](https://www.skankworks.net/agile/operation-devops/)_

## **The Agile Plan for Total Domination**

Not satisifed with muscling in on testing, and in an environment where the only things being continuously delivered are head-count and salary cuts, the Agile community has launched an offensive to take over operations. Software developers are, according to the plan, the only people who can reliably operate the systems they develop. Developers. Operations. Hence the unimaginative title "DevOps".

### **Testing **

Over the last three years we at the skankworks.net have seen, even participated in, DevTest. This involves Agile concepts such as test-driven development (TDD) whereby developers write their own test cases first, then code-towards-the-test. Only after the test has passed do agile developers write their design documents, which are little more than extended code-comments telling readers what the code does as opposed to what the code is supposed to be doing. But no matter, it's passed a test thought up by the same person that wrote the object under test. The difficult part in this discredited approach usually comes later when such development teams try to retro-fit customer requirements onto what they actually produced.

Embedding so-called "agile testers" into scrum teams is another idea we've yet to see work. In every case of our experience these testers are prevented from giving impartial objective assements and are used by developers for little more than a means of off-loading the unit testing they are supposed to be doing themselves. So that they can work on more story-points, apparantly. We've had development "skills group leaders" telling their teams that V&V's job is to "test stories". We have been given code to test that contains syntax errors and will not even compile - which tells us that the developers didn't even try to run their own code. A little over-confident in their abilities, perhaps.

All that gets tested in these environments are individual changes. Regression, system and functional testing no longer takes place. Verification and validation exist in name only, led by people who do not even know what the words mean. Inevitably this results in dysfunctional systems that take literally years longer to develop than originally planned.

### **Developers**

Now they are moving into operations. We don't think the developers are going to like that. Customers, many of whom may be losing money as a result of faulty code, tend to be a lot more subjective in their defect reports than testers. They can in fact become quite angry, and it frequently requires diplomacy to placate them. Diplomacy of this nature is a little hard to come by when it is your own short-comings that are being dissed by a paying-customer, and we feel that many developers are going to find themselves lacking in this area and likely to become quickly dissillusioned with the world of Ops.

Agile Evangalists, naturally, are already claiming that "this time next year 95% of the world will have adopted DevOps". They are coming up with new ways of assigning story points to customer complaints and service outages by creating them. The 95% coverage claim is, nevertheless, just another Agile pipe-dream. Unrealistic in claim, impossible in practice.

In regulated environments, such as finance or health-care, developers are not allowed access to operations, and vice versa. Many non-regulated organisations adopt the same rules, because they know that these rules have been created for a good reason. That being, it is unsafe and ill-advised to trust developers to run operations. For an extreme example, if somebody operating software for bank-accounts is also able to access the source code of that software, they could pay any money they like into their own account, cover-up the evidence, and quit their job tomorrow. For a more mundane example, code generally fails because of something that development didn't think of - hence the need for independent thinking in test and operations.

Thus, DevOps is largely forbidden by laws such as Sarbanes-Oxley. The Food and Drug Administration similarly has its own law, 21 CFR, which goes into great detail of the processes and practices required to produce quality systems. But the fact that such practices as DevOps have long been outlawed in sectors where software defects could do great harm to the health of people or the economy does not deter inexperienced Agile developers from thinking it's the best idea ever.

### **Operations**

In Operations we will allow senior developers limited read-only access to production, and occasionaly provide them with cuts of production data from which all client-identifying details have been removed. One of the main reasons why we have issues in operations is because of mistakes made by developers. We do not allow them to come and experiment on our production systems in order to find out what went wrong. If it's a software issue we tell them what they need to do to fix it. When hardware failures occur developers can't help us. Unless they want to drive out to the data-centre in the middle of the night to replace a system board that is.

After they get back from the data-centre, perhaps DevOps would like to be the one who has to try to get a hungover DBA out of bed at 3AM to reindex a table that developers forgot to provide a cron-script for? Or maybe they'd like to seek an emergency change-request approval from a board member, whose first question is likely to be 'who caused this mess?'. Does anyone really think that this is what developers want to be doing? Starting every call with the words, "I'm sorry I fouled-up and need you to…".

DevOps will take a different view. They will tell us we don't need failover because their software will never fail. They will have us assiging story points to system-board replacements and the whole time we are sitting around "doing it" by showing playing cards to each other in meeting rooms the system will remain down.

In Operations one is expected, nay required, to find quick solutions and act decisively. We do not "groom the backlog", we triage. We do not set pomodoro-timers to tell us how long we should work on a service-outage. We are not expected to provide continuous delivery, we are expected to provide immediate delivery. We write the work-arounds that will keep the business up-and-running in order that developers may have the time and space to come up with a permanent fix. If developers are spending their time scripting work-arounds to keep their code running in production, who is going to be available to code the fixes?

We _are_ the product owners and our responsibility is to the real world of customers and users, not the fantasy-world of story-point generation.

### **Conclusion - DevCust**

Tune in next year for DevCust, in which Agile developers only sell software to themselves. In DevCust tests are done before code is written. Design is done after code is written. Specifications and requirements are decided upon at runtime and dependent only upon the software's output.

What could possibly go wrong?

**Recommended Reading**  
[DevOps Is Bullshit: Why One Programmer Doesn't Do It Anymore](https://lionfacelemonface.wordpress.com/2015/03/08/devops-is-bullshit-why-one-programmer-doesnt-do-it-anymore/)
