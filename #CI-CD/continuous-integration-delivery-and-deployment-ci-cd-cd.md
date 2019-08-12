# Continuous Integration, Delivery, and Deployment: CI/CD/CD

_Captured: 2018-12-31 at 19:15 from [dzone.com](https://dzone.com/articles/continuous-integration-delivery-and-deployment-cic)_

Everyone LOVES doing the same task day in and day out. Right? No? I guess that's one of the reasons we built computers, to automate repetitive workflows. Who knew? Since I touched on [microservices in my last post](https://blog.cloud-elements.com/what-are-microservices-and-why-youll-love-them), Continuous Integration/Delivery/Deployments seemed like the next logical post.

So…off we go to the Magic School Bus.

![Image title](https://dzone.com/storage/temp/10912495-tenor.gif)

As companies become more Agile they are also trying to show clients and investors why they are the best. What better way to do that than to continually deploy new features for people to play with? This is where Continuous Integration, Continuous Delivery, and Continuous Deployment come in. This means smaller changes/updates, more frequently, not one leviathanic push every quarter. Smaller changes to the environment means when something goes wrong it's easier to pinpoint, roll back, and fix. If you roll out 10K lines of code and something breaks, where is the break? It's the world's worst game of hide and seek and it's your job to figure it out. Deploy 1 commit at a time, and something goes wrong, guess what? I'll bet it's that commit. Go fix that one. You get to solve the problem, look like a hero, and move on to something new. Everyone wins.

## What Are Continuous Integration, Continuous Delivery, Continuous Deployment?

### Continuous Integration

In the dark ages, engineers merged code infrequently. When they did, it was a massive code dump. This could happen at anytime, but because engineers are usually juggling many things at once these commits happened around a release day. I despise dealing with merge conflicts. Maybe you love it but you're an oddity if you do. For the rest of us, these merge conflicts mean having to resolve things locally and then recommitting to some designated branch for the release. This can lead to releases being delayed and customers missing new features for their releases. No one is happy. With continuous integration, an engineer commits more frequently. If an error is found in that new code they can address it at that time. This quickens the release process since there should be no conflicts in the deploying branch. Customers are happy, Product Managers are happy, and no one is yelling at you. We all win!

Continuous integration means you will have to implement a few things. Yes, this will cost you things, and yes, it will slow you down for a bit. I promise you will enter nirvana after this learning curve. You will need to create a test suite and have it run automatically when new code is pushed. I know, "But I don't like writing test." Do you prefer breaking the build? Yeah, didn't think so. You build a robust test suite and when new code is pushed, it validates that you are actually that smart. Your code goes to Production and everyone wins. Way to go. You will also have to set up a separate server to run that cool new test suite. But once it's up and running you just have to maintain (like your code), and that's still less painful than having a ton of code pushed in the moments before a release is supposed to go out. Because the bugs are found before they go to customers your platform looks stronger, you look better, and QA (the unsung heroes of developing) are freed up to deal with more strategic issues like weird edge cases and such. Everyone gets to focus on what they really like and that, my dear internet audience, makes for a better atmosphere. One note here is to test your new code locally before pushing to master. Why? Because it's less expensive (both in terms time and CPU cycles), you can debug locally quicker, AND when you finally merge to master the final check confirms you're good to go.

### Continuous Delivery

So you've implemented continuous integration. Now what? Well you have to continuously deliver that code to the end user. Here's where one of those wonderful "CDs" comes into play. Continuous Delivery is just that. Our users get new features on some regular cadence. This sounds like the old "release once a quarter" and it kind of is. Except this is on a per commit, hourly, daily, or weekly basis, shortening the feedback loop and allowing you to improve on features in near real time. If something in your platform breaks right after new code has been delivered, well it's kind of obvious that the new code is to blame. Roll back to the old version, fix the issue, and redeploy. No one is the wiser.

This does mean, however, that you need to have a comprehensive test suite. Yeah, I know, testing is not sexy, nor fun, nor thrilling. But you either have tests that catch bugs before the code goes in front of clients, or you break your most important client, they churn, and the company looks like your goldfish in the 3rd grade that you forgot to feed. Your call, but I prefer having a job. The other cost to assess? Feature flags. No one wants a half-built feature. It doesn't serve a purpose. Hide that behind a flag and customers won't see it until it's nicely polished. You can commit code frequently (see Continuous Integration), but until that feature is 100% UAT accepted, it stays hidden. Somewhat important to mention is that someone (preferably an employee) has to manually kick off the deployment. This should be too involved since tests have been done, feature flags removed, and all is good. But that does mean taking someone off the thing they were working on to hit a button. So pick someone who likes pressing big red buttons (me, for example).

All these costs, but where's the benefit? Because you are now delivering code more often, clients get to try new features, have bugs fixed sooner, and move faster. That means they see a quicker return on their investment in you and are more likely to renew their contract. Because you are able to make more, smaller, changes, you can experiment more. Curious if this function would work better this way? Well, try it out. As William Blake said, "The true method of knowledge is experiment." So try it out. If it doesn't work, who cares, it didn't break anyone. Try again and succeed.

### Continuous Deployment

This idea takes Continuous Delivery one step further. Instead of having someone manually kick off the deployment a computer does it. So from "git push origin master" to your customer playing with the new feature no one has to touch the code. It's been tested, checked, verified, and deployed by a computer, freeing you and your team up to do better things on a Friday! Continuous Deployment can quicken the feedback loop even more. You can deploy new code every time you push to master. More new code in master means more customers trying it out and letting you know what can be improved. That quicker feedback means that everyone gets to find higher value in what you built.

Naturally, since this is a highly automated process, testing must be the keystone of your engineering team. The test suite must cover as much of the code base as possible, no diminishing returns here. 100% test coverage is ideal. If you miss something, it could wreak havoc all over the place. So, use TDD like your life depends on it, because it more than likely does. The other thing to consider is that your documentation needs to be in sync with the newly delivered code. Otherwise, no one, other than you, will know how to use the new feature. I'm no expert (ask my manager), but I don't think you scale easily. So make sure that documentation is a close second to testing. Otherwise, your support people will be inundated with questions that will frustrate them.

So that's it. CI/CD/CD means that you get to develop faster, customers get to use the newest features sooner, and everyone makes more money, and isn't that what Keynesian Economics is all about? The short version, if you didn't click the links is this:

  * Continuous Integration means that smaller chunks of code are committed more often. These smaller chunks are easier to triage when something goes wrong. 

  * Continuous Delivery means that customers get to try out new features sooner and give you meaningful feedback sooner. That allows you to build meaningful features that will ensure customers stick with you for years to come. 

  * Continuous Deployment is like Continuous Delivery on steroids. You develop code, get feedback, and iterate to success faster and have a more meaningful impact on your clients that everyone is happier. 

Isn't life great?

Have fun and see you next year, when I'm sure I'll be ranting about something else.
