# Effective Refactoring, Part 1: Asking the Right Questions

_Captured: 2018-03-29 at 14:17 from [dzone.com](https://dzone.com/articles/effective-refactoring-part-1-asking-the-right-ques?edition=370197&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=web%20dev%202018-03-29)_

[Learn how](https://dzone.com/go?i=282429&u=https%3A%2F%2Fcraftersoftware.com%2Fresources%2Fwhite-papers%2Ffive-reasons-you-need-a-git-based-cms%3Fdzone) Crafter's Git-based content management system is reinventing modern digital experiences.

> _Refactoring is the process of changing a software system in such a way that it does not alter the external behavior of the code yet improves its internal structure. It is a disciplined way to clean up code that minimizes the chances of introducing bugs. In essence, when you refactor, you are improving the design of the code after it has been written._

Martin Fowler provided this definition in one of the quintessential books on the subject: _[Refactoring: Improving the Design of Existing Code](https://www.safaribooksonline.com/library/view/refactoring-improving-the/0201485672/)_. If you haven't read this book and you're interested in learning more about refactoring, I highly recommend it.

Over the years, I've completed refactoring projects of varying sizes. I've always enjoyed the sense of satisfaction I get from rewriting code to be cleaner (or at least cleaner by my standards).

I've done my due diligence on the subject. I've read several books on refactoring and did plenty of research on the web. Most of these resources describe **techniques** and **general considerations**. They specify conditions under which you should extract, move, rename, or encapsulate, but something is always missing. For lack of a better term, let's call this the _refactoring guidance _problem. It's hard to find good answers to common questions:

  * Where do I start?

  * How do I manage changes and not break the production application?

  * How do I implement new features during the refactor?

  * **How do I avoid catastrophe?**

![It could happen.](https://dzone.com/storage/temp/8391345-catastrophe.png)

> _It could happen._

I recently took on a substantial refactoring project for a sales budget management and analytics application that was built using React and Redux. The app was about 13,000 lines of code spread across 300 files. There were a few tests written to ensure the React components were rendering correctly, but [statement coverage](http://istqbexamcertification.com/what-is-statement-coverage-advantages-and-disadvantages/) was only at 1.82%. I had been working regularly with the codebase, so I knew what had to be updated to adhere to our current coding standards. Here's the list of goals I ended up with:

  * Update folder structure to centralize Redux files (actions, reducers, selectors).

  * Remove unnecessary abstractions and dead code.

  * Install and configure the [Jest](https://facebook.github.io/jest/) testing framework and write unit tests.

I was able to accomplish these goals, but not without learning a few things the hard way. With the experience I've gained over the course of several projects, I feel that I can provide some valuable guidance that goes beyond techniques and general considerations.

In Part 1 of this series, I will review some of the questions you should ask yourself before you decide to take on a major refactoring project. As an aside, this article is geared towards **projects with the specific goal of refactoring**. Throughout the course of normal development, I recommend that you adhere to [Uncle Bob's Boy Scout Rule](http://programmer.97things.oreilly.com/wiki/index.php/The_Boy_Scout_Rule) when you're adding features or fixing bugs.

## Before You Start

![Questions questions questions](https://dzone.com/storage/temp/8391355-questions.png)

> _Questions questions questions_

### **First, Ask Yourself, Should I Refactor This?**

I cannot stress the importance of this question. Most programmers I know love to write clean, elegant code. Unfortunately, the real world isn't elegant and it sure as hell isn't clean: deadlines and shifting requirements are just the start of your problems.

You may look at a large codebase and feel the overwhelming urge to do a rewrite. You **_should_** consider refactoring if you're able to answer "yes" to any of these questions:

  * Is there significant technical debt that's on the cusp of becoming a huge problem?

  * Is it difficult to add new features?

  * Does making a minor change in one section of the codebase break unrelated functionality in another part of the application?

  * Are you using outdated dependencies that have security or performance issues?

  * In the case of JavaScript, is it ES5 syntax that can be enhanced with some of the new language features like arrow functions and destructuring?

Rather than just diving right in, I recommend discussing it with some of your peers. Getting the opinion of a senior engineer who has been around the block a few times could make the decision to refactor much easier. They may be able to elaborate on why the code was written a certain way or provide some valuable insights that affect your opinion. An experienced engineer might caution you against attempting to refactor due to a failed attempt in the past. In some cases, it might not be worth the effort.

### **Next, Ask Yourself, Can I Refactor This?**

Now you're faced with the next roadblock: determining if the refactor is even feasible. When asking yourself, _can I refactor this?_ the **"can"** represents any number of limiting factors.

  * Can I refactor this given my **current skill set**?

  * Can I refactor this given my **availability**?

  * Can I refactor this while also **adding new features**?

  * Can I refactor this given the **available budget**?

If you **can't** answer yes to all those questions, you're asking for trouble. In my case, there was an opportunity to do some cleanup and I took advantage of it. I had support from engineering and approval from the product owner. Especially in a consulting environment, product management approval is imperative because they work directly with the client and manage the budget. If you try doing this under the radar or take on more than you're comfortable with, you will end up backed into a corner.

### **Finally, Ask Yourself, Do I Want to Refactor This?**

This question may seem preposterous considering you've gotten this far into the article, but it is something you want to ask yourself nonetheless. If you've been assigned this project at work and you wish to remain employed, you'll have to skip this question. However, if you're taking the initiative, it's important to be realistic.

Understand that a rewrite can be a massive undertaking that can be incredibly stressful and demanding, especially if there's a strict budget or schedule. There may be some stigma associated with the project, so you may find yourself having to answer the same questions:

  * _Why wasn't the code written the right way in the first place?_

  * _If the application works fine, why mess with it?_

  * _It can't be that bad, haven't you been able to add new features?_

  * _Does this add value to the business?_

Dealing with this negativity and confusion can be disheartening, which can make refactoring feel like a thankless task. It becomes even more problematic if some existing functionality breaks as a result of a rewrite (we'll go over that in a later post). Despite the downsides, a refactor can be a valuable investment of time. Cleaning up the codebase while adding good unit tests will ensure that features are easier to add and regression bugs are less likely to occur.

## **Wrap Up**

Due diligence is required for seeing a refactoring project through to successful completion. If you don't think it **can** or **should** be done, it'll be doomed from the start.

Now that you've decided (and are able to) move forward with your refactor, the next thing you'll need is a plan. In part 2 of this series, I'll cover the planning phase and how to get started.

Crafter CMS is a modern Git-based platform for building innovative websites and content-rich digital experiences. [Download this white paper now](https://dzone.com/go?i=282430&u=https%3A%2F%2Fcraftersoftware.com%2Fresources%2Fwhite-papers%2Ffive-reasons-you-need-a-git-based-cms%3Fdzone).
