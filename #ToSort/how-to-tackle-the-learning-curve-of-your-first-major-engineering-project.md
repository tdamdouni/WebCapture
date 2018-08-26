# How to Tackle the Learning Curve of your First Major Engineering Project

_Captured: 2018-05-23 at 20:14 from [dzone.com](https://dzone.com/articles/how-to-tackle-the-learning-curve-of-your-first-maj?edition=376359&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-05-23)_

**The Agile Zone is brought to you in partnership with [Techtown Training](https://dzone.com/go?i=275424&u=http%3A%2F%2Ftechtowntraining.com%2F%3Futm_source%3Ddzone%26utm_medium%3Dfooter). Learn how DevOps and SAFe® can be used either separately or in unison as a way to make your organization more efficient, more effective, and more successful in our [SAFe® vs DevOps eBook](https://dzone.com/go?i=275424&u=http%3A%2F%2Fpages.aspeinc.com%2FSAFe-vs-DevOps.html%3Futm_source%3Ddzone%26utm_medium%3Dfooter%26utm_campaign%3Dsafe_vs_devops%26utm_content%3Debook).**

![Image title](https://www.nylas.com/hubfs/blog_image_-Annie%27s-first-project-at-Nylas_v6_2.27.png?t=1519791926999)

Six weeks into my first full-time engineering job I was tasked with [a major project that put my programming abilities](https://www.nylas.com/blog/lessons-learned-syncing-800-million-contacts-to-our-database)[ to the test](https://www.nylas.com/blog/lessons-learned-syncing-800-million-contacts-to-our-database). I had to switch from the language and mindset I was most familiar with, Javascript, and dive head first into [Nylas's](https://www.nylas.com/) 4-year-old Python codebase in order to build a API to sync over 800 million contacts (and rising). What ensued was a 16 week-long project that deepened my understanding of engineering fullstack systems at scale and taught me about the challenges of tackling your first major project.

Many engineers question their abilities early on. Diving into a new company with an entirely new codebase as well as a unique set of infrastructure, monitoring systems, best practices, and workflows can feel overwhelming. My goal with this blog is to offer advice to other engineers who are early on in their careers. But first, let me provide some context about the product that Nylas offer and the project I was tasked with: updating our Contacts API.

If you're curious about the technical details of the project, [check out my previous post](https://www.nylas.com/blog/lessons-learned-syncing-800-million-contacts-to-our-database). What you need to know for now is that the Nylas APIs allow developers to build email, calendar, and contacts functionality (and two-way sync) into their apps. From early product feedback, we found that customers were asking for new features to our contacts API. We previously had a read-only functionality for very limited contact data, and customers were asking for more functionality. In short, this was by far my biggest and most complex fullstack project to date. I was excited, albeit nervous, to tackle this project, and I learned a lot along the way.

## Takeaways

### Writing Good Tests Is the Best Way to Ensure You Are Writing Good Code

The importance of writing good tests is one of those lessons that resurfaces with every project I work on. Your objective as a programmer is to write good code. The best way to evaluate your code, and continue to evaluate it as other factors in the code or environment change, is to write good tests. It's hypothetically a simple concept, but one that's surprisingly difficult to implement, even for people who aren't new to the industry.

On this project I learned to appreciate the power of unit tests for debugging. As the name suggests, unit tests isolate and test a specific unit of interest. Previously, when I would run into a bug that I was unsure about, I would immediately dive into trying to solve it. This was usually before I had a good understanding of what was going on and before I could replicate it. This meant that I spent more time debugging, had less confidence in my solutions, and had very little understanding of the causes.

Using unit tests to debug an issue is a different process. With unit tests in place, I start by isolating the problem and write a test that mocks out everything else before I dive into debugging. It's essential to do this because you want to make sure that the buggy behavior isn't influenced by other elements. Once you have the problem isolated, the test starts failing because of the bug. Now this failing test is a solid way to measure when the bug is fixed and if it will stay fixed. Once I have the test or tests in place, I can confidently dive into debugging knowing that the goal is to get the test to pass.

> Although writing tests takes time that isn't directly going towards the product, it will ultimately save time. 

### Use Your Mentor as a Resource

Joining a new company can be intimidating because there is so much to learn. To lessen the learning curve, Nylas pairs new hires with senior engineers. For the Contacts v2.0 project, I worked with [Karim](https://www.nylas.com/blog/author/karim-hamidou) as my coding partner, mentor, and overall resource.

In the beginning of the project, we worked exclusively through pair programming with me typing and him guiding and explaining along the way. As I gained confidence and understanding, I slowly began to take over and do larger pieces on my own. For a while, I still relied on him heavily to field questions as I worked. Over time, my volume of questions decreased. Eventually, I became the project lead and the go-to resource to answer questions coming from the project manager, our customers, and my fellow engineers.

This pairing was an essential part of my growth in the first few months at Nylas. If your company doesn't already do pair programming, I recommend suggesting it because it is incredibly beneficial, especially for new hires.

> Without Karim's mentoring throughout, my project would not have been as successful, and I would not feel as confident in my abilities going forward. 

### Ask Questions Even When You Don't Know What to Ask

In the beginning of Contacts v2.0, I often didn't speak up when I was confused because I felt that I didn't even know what to ask. Some concepts felt so far beyond my understanding that I wasn't able to piece together a question. I was embarrassed to ask what might be seen as basic questions, and even more worried that it might expose some fatal flaw in my ability. So instead, I would silently trudge along in my haze of confusion hoping that time would bring eventually clarity.

I quickly learned that this was not the best strategy. While it's possible that time might bring clarity, often it doesn't. And no matter what, clarity would have come more quickly had I just asked. Instead of my silence making me look like I understood exactly what was going on, it simply hid that I wasn't following along. These gaps in my understanding would almost certainly have backfired later in the project at a time when it was more critical. In addition, if came out at that point that I not only didn't understand the current concept, but had been in the dark all along, it would have reflected poorly on my entire performance.

However, simply knowing that you _should_ ask a question doesn't always help with knowing _what_ to ask. My strategy for how to ask the questions when you can't easily piece together the problem is to back up. If you are nested deep into some complex process, it can be helpful to continue to take steps back until you are at a level that you feel comfortable with. If you have some uncertainty regarding a function, follow the stack trace up until you get to a process you are familiar with. If all else fails, be very forthcoming about your confusion and ask your mentor to start with the basics.

> It's also important to keep in mind that you're probably not the only one to have these questions. Asking questions is not a sign of weakness, but a desire to learn. 

### Reflection Takes Time, but Is Time Well Spent

When I first joined Nylas, I felt like every day was full of new terms, processes, techniques, tips and projects. I would ask a lot of questions and receive great answers, but I felt like a lot of the information wasn't sticking.

To get more information to sink in and feel like I could answer questions about previous work, I started keeping a work log. It's very simple; just a Google doc where I write things that come up throughout each workday -- tips that I learn, how to use certain scripts, bugs that I run into, questions that arise, and the subsequent answers to those questions.

In a fast-paced startup environment it's easy to always be in forward motion, finishing one project and moving to the next. Keeping this log forces me to slow down and reflect on my work. Sometimes, the process of writing things down reveals gaps in my understanding.

> In a field where we are constantly needing to stay on top of new technologies, strategies that ease the learning process are important. Keeping a Nylas learning diary is one thing that helps me. 

My experience with this project -- from questioning my abilities as a programmer, to slowly becoming the lead engineer, to beta testing directly with customers, and updating the SDKs to ultimately launching -- has given me greater confidence. I am excited for all the learning to come in the next project. Every engineer's experience is different, but I hope that sharing what I learned in my first major engineering project will help others!

**Adopting a DevOps practice starts with understanding where you are in the implementation journey. Download the [DevOps Transformation Roadmap](https://dzone.com/go?i=266427&u=http%3A%2F%2Fpages.techtowntraining.com%2FDevOpsRoadmapDzone_DevOpsTransformationRoadmap.html%3Futm_source%3Ddzone%26utm_medium%3Dheader%26utm_campaign%3Ddevops-transformation), brought to you in partnership with [Techtown Training](https://dzone.com/go?i=266427&u=http%3A%2F%2Fwww.techtowntraining.com%2F). **
