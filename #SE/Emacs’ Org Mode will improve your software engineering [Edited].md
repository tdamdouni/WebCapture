# Emacs’ Org Mode will improve your software engineering [Edited]

_Captured: 2016-03-23 at 15:40 from [medium.com](https://medium.com/@rtotheohan/emac-s-org-mode-will-improve-your-software-engineering-d7bc2f30a0)_

#### Your brain is chaos

When working deep within a problem, often a bundle of ideas can pop into your brain at the same time. Each of these ideas has potential, but as soon as you explore one of these ideas, the context and momentum of the remaining thoughts start evaporating. Exploring an idea incurs a cost to the brain in that zaps in a whole new set of related ideas (damn you, [associative machine](http://www.amazon.com/Thinking-Fast-Slow-Daniel-Kahneman/dp/0374533555)). As time goes on, you realize that those initial ideas had some worth, but you no longer remember the ideas nor the thought that led to those ideas. Backtracking only works in a linear chain of transitions, perhaps with a branch here or there. Our deductive skills can only take us so far.

Though we have a huge capacity to store information and memory, it takes time and practice to save things there. Our working memory is small and will regularly drop things in order to keep up with wherever our focus and attention is moving. Instead of dropping things, we should save things and move on, like a [Turing Machine.](https://en.wikipedia.org/wiki/Turing_machine)

#### Deterministic Finite Automata vs Turing Machines

DFAs and Turing Machines are identical except for [one small difference](http://cs.stackexchange.com/questions/16315/difference-between-a-turing-machine-and-a-finite-state-machine) -- a Turing Machine has a tape of memory that it could read and write from. This has enormous implications for how powerful of a program it can implement, what sort of languages it can understand, the types of problems it can solve. The key is the ability to _write things down_.

By writing a few words about your ideas as soon as you have them, you've done a few things:

  1. You saved it to revisit later, allowing you to move forward
  2. You memorized it a bit. The process of writing the thought allows the brain a re-run of it -- a bit of rote memorization. This allows for better contextualization when you're ready to explore it.
  3. You've edited and refined it. Externalizing it in a relaxed setting with the ability to see what you're saying and reflect back immediately leads to clearer ideas that can be shared with other people.

The interesting thing to note is exploring an idea is simply following these steps again -- _it's a recursive process_. Hierarchical structures are intuitive and sort of mirror how the brain thinks, which is why outlining makes so much sense (and not a timeline of thoughts or something else). This quick and iterative note-taking and outlining ultimately introduces some order to the chaos stemming from your mind.

#### Tasks flow naturally from your notes

The purpose of this post is not to advocate note-taking or outlining, but rather use it to help map the space of large software and research projects and plan. For example, let's say you were given an enhancement request from a client on an Sales and Inventory application that you work on:

> I need to see the min and max number of sales that happened for product X in the past week

In my nascent stages of software engineering, I may have just gone to see what code I needed to change to implement it, make the changes, have it reviewed, and release it. As I've matured and learned from senior software engineers, this is the wrong approach. Solving this one problem will most likely not solve the larger problem, and will not help determine what the larger problem is. It could potentially lead to other problems.

Here are some questions that come to mind:

  * Would clients want other statistics such as the mean, median, standard deviation in addition to min and max?
  * Would showing a sorted arrangement solve the problem?
  * How simple would it be to sort the current arrangement of sales in the UI?
  * What problem does showing the min and max help the client solve?

As soon as these come to mind, it's worth jotting them down _before_ you investigate each question. This is the most important part. From this, it's apparent that the understanding the code changes for sorting the sales per week requires a concrete look through the code and building an estimate. This is a task and the beauty of Org-mode is seamlessly allowing the interweaving of tasks and notes.

Just type **TODO** before any line item to make it a task.

Completing a task is just as simple too.

As bullet points grow, we'll naturally begin to group things together, classify them, and build hierarchies. Org-mode allows for this through promotion and demotion of subtrees.

#### Never write HTML again

While you may be intimate with the inner workings of your Org file within Emacs, it's not exactly the friendliest UI to product and project managers. One of the many perks of Org-mode is the ability to export Org files to a variety of formats, including HTML.

I enjoy this because with a little CSS these exports can look professional with negligible amounts of effort. Once I've published to HTML I serve it up in my home page directory and share it with relevant folk.

#### To context switch or not

Since I code in Emacs, being able to write a function, run it, evaluate it, and reflect can all happen within the same window. When new ideas come up, I can start documenting my thoughts within the same application by just switching to an **org** file. If you program regularly in Emacs, this is 100 % up your alley. If not, then it may take some persuading, but hopefully my post took you some of the way there.

Switching applications is a context switch and an opportunity to get distracted. Every time I open Google Chrome I'm a lot more likely to offer myself a snack of The Times, The Atlantic, Medium, and Hacker News. I can lose the context that got me here and lose valuable energy in order to recover it, if I'm even able to recover it.

This means that using Org Mode while making Emacs you're go-to code editor of choice has a multiplier effect. Being able to code, explore, outline, and plan in one application has profound consequences for productivity and completeness.

#### Weakness

The caveat here is that it's mostly a one man show. It will never be a replacement for Atlassian's or Asana's project management software. A Story or Epic on JIRA could be one of the final outputs of your note-taking and planning using Emacs Org-mode. I often publish my problem investigations to an HTML page and link that throughout JIRA stories for transparency.

Org mode serves as a bridge between conception of an idea or problem to the final set of assumptions, tasks, and estimates that go into a project. It's not meant to replace any project management system.

#### Conclusion

I hope this post opens you up to the idea of using Org-mode if you're an Emacs user and at the very least makes you more inclined to find a note-taking methodology that suits you and your work :)
