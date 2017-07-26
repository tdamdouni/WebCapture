# How to do Software Deployments with Confidence

_Captured: 2017-03-12 at 20:25 from [dzone.com](https://dzone.com/articles/how-to-do-software-deployments-with-confidence?edition=281882&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-12)_

Learn more about [how DevOps teams must adopt a more agile development process](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702), working in parallel instead of waiting on other teams to finish their components or for resources to become available, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148026&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fexploring-the-tools-that-make-agile-parallel-development-possible.register.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001285-000000492%26aid%3D00702).

Everyone wants to ship their code faster. Agile development and all the variants of it have helped companies release software more often and spend less time in large, waterfall planning and project management. Agile development still has one big problem - confidence in software deployments.

**Developers have no idea if they are really ready to ship their new version.**

## Does This Happen in Your Office?

You just finished a sprint and we are ready to push it to production. You ask everyone on the team, including the development manager, how they feel about pushing to production. And you get Lumbergh…

The problem is that the tasks are all done, and "testing" is finished, but nobody has any real idea if the code is going to blow up spectacularly in production, or work just fine. How often do you delay releases because you are nervous about potential problems? What issues are lurking right beneath the surface?

### The #1 Problem With Agile Development Is Confidence in Your Releases

There are a lot of risks anytime you do a deployment. How do you confidently measure that risk?Using your spidey senses is not good enough. And since nobody knows, eventually someone says, 'Just ship it!' Then the next day looks about like this…

![worked fine in dev](https://stackify.com/wp-content/uploads/2017/01/worked-fine-in-dev-300x225.png)

## Is Agile Working Well for You?

Velocity is not the goal of Agile development. Shipping new value to your customers as soon as possible is the goal. However, no part of that means to ship crappy code as quickly as possible. Going fast in the wrong direction is not the right kind of velocity you are after.

### **In Your Last Sprint, What Percent of the Work Items Were Bug Fixes?**

If you spend a lot of time on bug fixes and not on new features or improvements, then your current velocity is not working. You need to put more focus on quality and less time on velocity.

One of the great things about Agile is shipping things quickly and being able to take feedback about it to quickly make changes. This feedback from your users is critical to guide what development work should be done.

But, your users aren't the only ones providing you feedback!

### **Listen to Your Users and Your Code for Feedback.**

What developers need is feedback loops at every step of the development cycle. While writing their code, testing it, building it, deploying it, in QA, and in production. Utilizing this constant feedback can help you quickly identify problems before they get to production.

### How to Integrate Feedback Into Your Development Process

Before starting the next step in the development process, you need to review feedback from the previous step. It all starts with the start of the process, planning your next sprint!

### Before You Finish Planning the Next Sprint, How Are Things Going in Production?

**Performance review** - First thing you need to do is review how things are working in production. Here are some things you should do before every sprint planning meeting:

  * Review application errors that are occurring.
  * Ensure the most important web requests are performing well.
  * Look for poorly performing SQL queries.
  * Decide if any web requests need any performance tuning.
  * Verify if all changes from the previous release are performing well.

Reviewing your APM solution to see how things are going in production is a critical feedback loop. You want to find potential performance problems before your customers do. It is also important to understand performance before your next release, so you have some sort of baseline for comparison.

### The Best Time to Find Bugs Is While Writing Them!

The best time to find and prevent bugs is while creating them. As you start working on new work items, here are some suggestions on how to improve code quality.

_"When informed about a problem whilst in the moment I'm in a much better position to make corrections or come up with alternative solutions. Without a quick feedback loop, the passing of time makes it difficult to get into the initial mindset which caused the problem to begin with."_ - [Vince Panuccio](https://www.google.com/url?q=http://stackify.com/asp-net-profiler/&sa=D&ust=1484586995998000&usg=AFQjCNFS129XRmRqE0iZf5mYGgN7gZrhGg)

**IDE plugins** - After using tools like Resharper, it is hard to live without them. They are awesome at helping point out possible places in your code where common exceptions or problems could occur.

**Code level transaction tracing** - Depending on which programming language you are using, there are amazing tools now that can show you most of the key things about what your code is doing and how long it takes. These tools are awesome to help you understand what SQL queries, web services, and other things your code is calling. Check out our list of these tools included in our list of APM tools.

**Code reviews** - Having a second set of eyes look at your changes is never a bad thing, especially if it is a critical part of the code or complicated. Don't nitpick over silly things like how people named variables. Focus on the things that matter and ask questions.

### Automate Your Builds and Deployments to Remove Human Error

**Build server **- Having an automated build and deployment process is critical. If your current process involves asking Bob (what else would you name the builder?) to do a build and push code manually, your process is full of human error and too dependent on Bob. You should be using tools like Octopus Deploy, Jenkins, Continuum, TFS, or others to automate your build and deploy process to make sure it is done the same way every single time and Bob doesn't skip step #3.

**Unit tests** - I personally don't believe that you need unit tests for everything. They shouldn't be a replacement for a compiler. But I do think they are highly valuable for testing complex scenarios, business rules, etc. Have your build server run your [units test](https://stackify.com/unit-test-frameworks-csharp/) to help validate the build before it deploys.

**Review code commits **- One of my favorite things about a good build and deployment tool is its ability to show you exactly what code commits were included in the new build. This is a good way to verify if anything has sneaked its way in that you weren't aware of.

Your build server is a good first line of defense to make sure nobody checked in bad code. The last thing you want to do is go to push your code to production and find out you can't even compile.

### Collaborate With QA and Do Performance Reviews

Everyone hates QA. I get it. I really do. My favorite card in Developers Against Humanity is about putting the entire QA team on the bottom of the ocean. But QA can actually be very helpful if you work with them and give them good guidance on what to help test. You can do it… work with them!

**Actually tell QA what to test **- OK this seems obvious, but nobody does it. If you want your QA team to be very helpful and find problems, it is critical that you tell them as many details as possible about what they should be testing for. I think there should be a separate and required field in your ALM tool for this!

**Performance review** - Earlier I mentioned important things you should be reviewing in production to assist in planning your next sprint. You should be doing the same sort of things in QA to see how performance changes between builds and looking for new errors.

**Synthetic tests** - Use [selenium](http://www.seleniumhq.org/) or some other tool to set up and run automated synthetic tests for basic and key parts of your application. Make sure a user can login, navigate to key pages, etc.

### After Your Software Deployment, Quickly Check These Things!

During your deployment can be a nervous time. The last thing you want to do is push code, do a quick test to make sure your app loads, and call it done. If you want to sleep at night, you need to do a few more things!

Watching production after your software deployment is a critical part of the feedback you need to ensure that your release was a success. If things don't look right you can quickly fix the problem or decide if you have to roll back the deployment. Utilize your various monitoring and APM tools to verify these items.

**Look for new errors** - After almost every single release you are likely to see some new errors being thrown by your code. Be sure to check your error tracking tool to see if anything new is happening.

**Check your error rates** - A certain amount of errors is normal in most apps. A certain amount of noise, goofy errors, transient errors, etc. Ensure that the overall level of errors is consistent with normal and hasn't rapidly increased.

**Watch requests per minute** - Make sure that the overall traffic rate on your site looks normal. If traffic drastically goes up or down, either way, something could be wrong.

**Review top requests** - Double check that your key web requests that get accessed a lot still look normal.

**Database performance** - It is also a good idea to make sure your database and potentially other dependencies still look normal. If you pushed any SQL schema changes, there is definitely a chance things could be better or worse.

### Utilize Feedback to Build Release Confidence

Every step of the development process can provide a lot of feedback about the quality of your code and software. Utilizing these quick feedback loops can help you deploy more often and with more confidence.

Also, check out my article about [Essential developer tools to find bugs… before they get to production](https://stackify.com/developer-tools-to-find-bugs-before-production/). I discuss some great free and low-cost tools that every development team should have.

[Discover the warning signs of DevOps Dysfunction](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702) and learn how to get back on the right track, brought to you in partnership with [CA Technologies](https://dzone.com/go?i=148027&u=http%3A%2F%2Ftransform.ca.com%2Fpragmatic-guide-to-devops.html%3Fmrm%3D540542%26cid%3DNA-DSP-ABUS-ACM-000195-00001286-000000493%26aid%3D00702).
