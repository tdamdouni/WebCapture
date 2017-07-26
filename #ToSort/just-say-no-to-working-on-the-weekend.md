# Just Say No to Working on the Weekend

_Captured: 2017-01-25 at 15:51 from [dzone.com](https://dzone.com/articles/just-say-no?edition=154263&utm_source=Weekly%20Digest&utm_source=Weekly%20Digest&utm_medium=email&utm_medium=email&utm_campaign=wd%202017-01-25&utm_campaign=wd%202017-01-25)_

### A company that is not listening to the workforce, dissing experienced software engineers' advice, and sinking projects as a consequence does not deserve your free time.

Learn more about [how DevOps teams must adopt a more agile development process](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702), working in parallel instead of waiting on other teams to finish their components or for resources to become available, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702).

This is something some of us may have experienced. We get a call during the weekend from our Project Manager asking us to modify and deploy an application ASAP. Many times, the modification might be as inconsequential as a text change on some web page.

My advice? Since the answer is in the title, I'll cut to the chase: it is risky, irresponsible, and it's an insult to our profession.

## We Are Developers, Not Firefighters

Let's start with the obvious: developers are not firefighters. I know we all did it as juniors, and possibly, we even felt good about it -- until we noticed how risky it was. We put in production code that was not tested, we were not certain of the impact of our changes, and we inadvertently deployed bits of code that were not finished.

A firefighter is a brave soul with an emergency at hand. A firefighter is trained to react. A firefighter knows what he or she can do to stop a fire and take everyone to safety. A firefighter does not think it through, or at least not too much; by the time he or she's done thinking of a strategy, the house has burned to the ground and everybody is dead. Instead, a firefighter is trained to recognize situations and act fast.

A developer does not react; he or she adapts. Every single project is different and every situation is different. So, the developer sits, thinks, and comes up with a solution. Thinking takes time and focus. It requires examining the options, selecting the best one based on the context, implementing the solution using a computer language. The developer measures the consequences of his code; the developer acts "slow."

So, a developer and a firefighter: definitely not the same job.

## What Could Go Wrong?

However, just for a moment, let's say that a developer is willing to do a quick fix and deploy it ASAP. What could go wrong?

(You. Yes, you, the Senior Developer. I can see you're smiling. Memories are coming back to tease you, hey?)

A few years ago, I did a small fix on the front end of our project. It was just a typo in the landing page, so I did not test it and immediately pushed it into production. Then I went home.  
The next day the service desk was exploding with calls from angry users.

What happened? Well, the front end code included changes that would access the new REST API from the back end, which is a separate app. However, the new REST was not in production; it was still being tested in acceptance. Now, because there was another bug we still hadn't taken care of, there was no visible error message on the screen. We had a console's error logs, but it had been removed for production by that gulp plug-in we use to clean the code before we package it. So, when the web app crashed, the users did not get feedback. What they saw was an empty page because their data was not loading. In the user's terms: "My data is gone!"

My team was not happy about it. They obviously were right.

So, I learned that, when in a hurry, many things can go wrong -- mostly the things you didn't think of.

## You Will Be Replaced!

What if we refuse to work outside office hours? Many times the answer I get is: "Watch out -- we will be replaced by outsourced teams of Indians."

The "overseas outsourcing" cataclysm argument was already doing the rounds when I started programming about 12 years ago.

I'm still waiting for it to happen.

A company asks to develop a project internally or by a team of local consultants. The estimated budget is 200. Too expensive, so the company outsources it overseas.

The outsourced team replies with a budget of 100. The deal is done. Three months later, the project comes back. It's a cluttered mess.

So, the company calls back those consultants to fix things. This involves many rewrites after the project is done. The budget has reached 500 and the project is way past deadline.

Why? It's a complex issue, way more complicated than "Indians can't code," which is an oversimplification. I'd probably blame communication issues...

Then again, maybe the reason why overseas outsourcing is cheap is simply because programmers are pressurized to code for 14 hours straight while being paid a misery?

Anyway, the consequence is that the demand for in-house developers has kept increasing since I started as a developer. Even in a [country whose labor costs are exorbitant](http://www.amcham.be/policy/labor-market/labor-costs).

## You Have the Right to Remain Calm

Finally, let me look at this from another angle: your self-esteem and well-being.

Many of us are probably working during the weekend. We learn new technologies, we work on our pet project, we do code katas, we watch technical webcasts on YouTube -- we do all of these things because we love our profession. We do it for ourselves because it brings us satisfaction. We want to do it.

On the other end, we have a Project Manager who has never read the _[Mythical Man-Month_](https://www.amazon.com/dp/0201835959/163-9319240-7984556/ref=cm_sw_r_cp_ep_dp_aN5Eyb4KPWDE6), _[The Clean Coder_](https://www.amazon.com/dp/0137081073/159-2802298-2724357/ref=cm_sw_r_cp_ep_dp_7N5EybYY66YHY), or _[Death March_](https://www.amazon.com/dp/013143635X/159-8822155-6607304/ref=cm_sw_r_cp_ep_dp_KO5Eyb7RDHK1S). He or she is convinced that developing code merely consists of typing a few simple keywords, easy peasy. He or she believes Kanban is his or her right to ban developers from the company if they don't code fast enough, and introducing the Project Manager to Agile is a discussion that always ends up with him drooling on the floor while mentioning some very beautiful celebrity lady.

(Yes, I witnessed that. No, I still can't believe that guy was for real.)

So, that Project Manager ruins the project with "I-know-better-than-you" decisions. Other developers hide under the desk when he or she's out looking for people to join the team to make it go faster (_Mythical Man-Month_, for sure). Now, after demoralizing everyone on board, he's asking you to stop recharging your batteries and give up your well-earned relaxation time to do a quick fix?

## Conclusion

Just. Say. No.

A company that is not listening to the workforce, dissing experienced software engineers' advice, and sinking projects as a consequence does not deserve your "free time" investment as a compensation for its mistakes.

We should be professionals, not tired clumsy code hackers.

The topic is not new and is nowadays extensively documented by experts, for example, in the aforementioned books.

If companies keep ignoring the lessons learned from the others' mistakes, they will end up with teams of disillusioned programmers whose only _raison d'etre_ is to earn as much money as possible before moving to the next employer.

Cheers!

[Discover the warning signs of DevOps Dysfunction](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702) and learn how to get back on the right track, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702).
