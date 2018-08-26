# Deploy to Production: 5 Tips to Make It Smoother

_Captured: 2018-03-23 at 13:25 from [dzone.com](https://dzone.com/articles/deploy-to-production-5-tips-to-make-it-smoother?edition=368224&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-03-23)_

[Download the blueprint](https://dzone.com/go?i=228233&u=https%3A%2F%2Foffers.automic.com%2Fblueprint-to-continuous-delivery-with-automic-release-automation%3Futm_campaign%3DAMER%252520Online%252520Syndication%252520DZone%252520Platinum%252520Sponsorship%252520Ads%252520JULY-2017%26utm_source%3DDzone%252520Ads%26utm_medium%3DBlueprint%252520to%252520CD) that can take a company of any maturity level all the way up to enterprise-scale continuous delivery using a combination of Automic Release Automation, Automic's 20+ years of business automation experience, and the proven tools and practices the company is already leveraging.

Who hasn't had issues when deploying a software change to production? No one.

I once accidentally deleted a bin folder from a .NET application in one of four servers when deploying a change. The site was working intermittently as a consequence, so I had to check all the servers again to find the one that was having problems. Luckily for me, there were _only_ four servers.

Everything that _can_ go wrong in a deployment change to production _will_ go wrong. It's [Murphy's law](https://en.wikipedia.org/wiki/Murphy%27s_law). For that reason, we have a sort of respect that borders on fear when we think about doing deployments. There's too much at risk, so sometimes we avoid the struggle. But in reality, **deployments should be the most boring task of the workflow**. The trick is knowing how to do it.

With that in mind, let's talk about some ways to smoothly deploy to production without risking quality.

## 1\. Automate As Much As Possible

Let computers do the repeatable work for you-they're better at that than we are. I prefer to invest some hours working on a script to do deployments, like a recipe of commands. Then I test the script locally and in the development environment. That way, next time I want to deploy a change, I won't have to worry about missing any steps like creating a folder or giving permissions to some files. I'll just need to run the script again.

But I'm not talking about just a bash script that can be hard to read and understand. In the last few years, new things have emerged. You have at your disposal tools like [Terraform](https://www.terraform.io/), [Ansible](https://www.ansible.com/), and [Jenkins](https://jenkins.io/), which allow you to use code principles. You can have all your scripts in version control, and that will be the only source of truth. That means everyone will know what changed, as well as when and why it changed, not just in code but also in infrastructure and deployment pipelines.

All of this means that **deployments can be as easy as clicking a button**. Even reverting the deployment is a button-click away. You can get to the point where anyone, even non-technical people, can do deployments.

Automation makes deployments smoother by letting you move forward _and_ backward with ease. The process becomes repeatable and reliable.

## 2\. Build and Pack Your Application Only Once

The build process usually takes a while, so it will make things run so much more smoothly at deployment time if you only build once. You can keep coding and push changes all the time without worrying about promoting code that's not ready.

After you build your app, the next step is to pack it and to make sure the package remains untouchable. That way, you're constantly taking snapshots of your app. There will be times when the app is packed with errors or incomplete code. But that's no problem because you get to choose which package will be deployed.

**You'll move the same package across all your environments.** This means that when you generate it for development, you'll use the exact same version of the app to update the production environment. You can easily achieve this by doing adequate configuration management. Just replace placeholders with the respective values of the environment-like database endpoints, for example.

You'll want to practice **continuous integration **to make packing easier, and one of its fundamental principles is that you build only once. Practices like this allow you to integrate constantly in a shared repository, verify the process with automated tests, and fix things quickly if needed.

Do all of these things, and you'll smooth the deployment to production because what you tested in development is the same thing you tested in other environments, including production.

## 3\. Deploy the Same Way All the Time

There's no value in applying the previous tips if you don't deliver the same way in all circumstances. You packed once to deploy the same code everywhere, and you need to deliver the same way. By doing this, you'll avoid any surprises in production.

For this, **you need to have production-like environments**. This doesn't necessarily mean that you'll have the same data everywhere-that can be expensive and a possible security risk. It just means that if you have a load balancer in production because you need to be able to scale out/in, you also have to have one in development. If you're hosting production in the cloud, you need to do the same for development.

Of course, you can think about how to have cheaper environments. You just need to change configurations when you update an environment.

This deployment tip will help you to be bold when changing production. You'll be fearless because you've already practiced it several times before actually doing it.

## 4\. Deploy Using Feature Flags In Your Application

If you only take away one tip from this list, make it this one. Using feature flags will increase your confidence to deploy. And the benefit is even bigger when you combine them with strategies like [blue/green](https://docs.cloudfoundry.org/devguide/deploy-apps/blue-green.html) and [canary](https://octopus.com/docs/deployment-patterns/canary-deployments) deployments. These strategies will help you to deploy without customers noticing there was a change.

It doesn't matter which strategy you choose-all changes should be backward compatible. I recommend you choose a strategy that works for you. Blue/green deployments tend to be costly, depending on your infrastructure and how small your app is. But they're the safest way to deploy because you're duplicating the environment and testing it before pushing it live. In the case of canary deployments, you're pushing changes little by little. You can do it server by server or by recreating containers one at a time.

But you can do it better using feature flags.

In fact, you can do it so much better that you can deploy all changes with the feature flag turned off. Then you can turn on the feature flag for a small fraction of users, monitor their behavior for a while, and keep enabling the feature for more users until you're sure that the change is good to keep. And you can do this all without worrying about adding more complexity to your code or deployment strategy.

One good tool that makes feature flags easier to implement is [Rollout](https://rollout.io/product/feature-flag-management/). You set up your [audience](https://support.rollout.io/docs/audience) and roll out your changes little by little.

## 5\. Deploy in Small Batches, and Do It Often

When you put all the previous tips in practice, deploying in small batches and doing it frequently becomes natural. It will take some time to get there, especially because deployments should be predictable and reliable. But it'll be worth it.

Now, automated testing is a prerequisite. It doesn't matter how much effort you put into automating your deployments-if at the end of the day you spend a lot of time manually testing your application, you won't see the benefit. So try to spend time automating your test cases. Otherwise, there's no point in doing automated deployments.

But back to the subject at hand. How small should your batches be, and how frequently should you deploy them?

Well, if you've ever played the hot potato game, you'll have a good idea of what "small" and "frequent" mean. As soon as you have something ready to be deployed, do it. It doesn't have to be complete, so long as you use feature flags. Treat deployments like coding. It's pretty weird when someone spends many hours coding without testing. Without checking your code as you write it, you won't know exactly what's causing an error. And if there aren't many lines of code, there are fewer things you need to check.

Amplify feedback by increasing the number of times you deploy. It might sound risky, but it's not. The fewer changes you make, the easier it will be to know what's wrong. Don't wait until you have a lot of changes to deploy. Do it frequently.

## Make Deployments a Mundane Task

When you practice one or all of the above tips, your deployments will become boring. And in this case, boring is a big win. You'll find more exciting things to do rather than face the same problems over and over again.

The tools, services, and practices that exist today - especially those I've mentioned here - are wonderful. They help you avoid surprises, transforming all those scary nights or long weekends into peaceful, routine workdays. You can do things like automate many of your tasks, especially testing, to make going forward easier and more efficient. Also, you can pack your application; it will help you make deployments consistent. Note, too, that production environments don't deserve to be treated differently. And make sure you use feature flags. They'll help you be less stressed when deploying because you know you can always turn off features and everything will continue working. Lastly, work in small batches. It's easier to spot bugs, and it's less risky because you're not changing too many things at the same time.

[Download](https://dzone.com/go?i=228234&u=https%3A%2F%2Foffers.automic.com%2Fblueprint-to-continuous-delivery-with-automic-release-automation%3Futm_campaign%3DAMER%252520Online%252520Syndication%252520DZone%252520Platinum%252520Sponsorship%252520Ads%252520JULY-2017%26utm_source%3DDzone%252520Ads%26utm_medium%3DBlueprint%252520to%252520CD) the 'Practical Blueprint to Continuous Delivery' to learn how Automic Release Automation can help you begin or continue your company's digital transformation.
