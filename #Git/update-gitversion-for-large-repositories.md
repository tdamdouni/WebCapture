# Update GitVersion for Large Repositories

_Captured: 2017-04-26 at 20:21 from [dzone.com](https://dzone.com/articles/update-gitversion-for-large-repositories?edition=292930&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-26)_

[Discover how Microservices are a type of software architecture](https://dzone.com/go?i=201129&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-how-to-build-scale-with-microservices%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%252520zone%26utm_content%3Debook-how-to-build-scale-with-microservices%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital) where large applications are made up of small, self-contained units working together through [APIs that are not dependent on a specific language.](https://dzone.com/go?i=201129&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-how-to-build-scale-with-microservices%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%252520zone%26utm_content%3Debook-how-to-build-scale-with-microservices%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital) Brought to you in partnership with [AppDynamics](https://dzone.com/go?i=201129&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Febook-how-to-build-scale-with-microservices%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%252520zone%26utm_content%3Debook-how-to-build-scale-with-microservices%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital).

As you know, I'm a fanatic user of [GitVersion](http://www.codewrecks.com/blog/index.php/2015/10/17/integrating-gitversion-and-gitflow-in-your-vnext-build/) in builds, and I've [written a simple task](http://www.codewrecks.com/blog/index.php/2016/03/17/writing-a-custom-task-for-build-vnext/) to use it in a TFS Build automatically. This is the typical task that you write and forget because it just works and you usually not have the need to upgrade it, but there is a build where I start to see really high execution timing for the task; as an example, GitVersion needs two minutes to run.

![image](http://www.codewrecks.com/blog/wp-content/uploads/2017/04/image_thumb-7.png)

> _Figure 1: GitVersion task run time it is too high, 2 minutes._

This behavior is perfectly reproducible on my local machine. That repository is quite big, it has lots of tags and feature branches, and it seems that GitFlow needs a lot of time to determine semantic versioning.

Looking at the GitHub page of the project, I read some issues regarding performance problem; the good part is that all performance problems seem to disappear with the newer version, so it is time to upgrade the task.

Thanks to the new build system, updating a task in VSTS / TFS is really simple- I just deleted the old GitVersion executable and libraries from the folder where the task was defined, I copied over the new Gitversion.exe and libraries, and with a tfx build tasks upload command, I could immediately push the new version on my account.

Since I changed GitVersion from version 2 to version 3, it is a good practice to update the [Major number of the task](http://www.codewrecks.com/blog/index.php/2017/02/04/task-versioning-for-tfs-vsts-build/), to avoid all build to automatically use the new GitVersion executables, because it could break something. What I want is all build to show me that we have a new version of the task to use, so you can try and stick using the old version if Gitversion 3.6 gives you problems.

Whenever you do Major change on a TFS / VSTS Build task it is a good practice to upgrade major number to avoid all builds to automatically use the new version of the task.

Thanks to versioning, you can decide if you want to try out the new version of the task for each distinct build.

![image](http://www.codewrecks.com/blog/wp-content/uploads/2017/04/image_thumb-8.png)

_Figure 2: Thanks to versioning, the owner of the build can choose if the build should be upgraded to use the new version of GitVersion task._

After upgrading the build, just queue a new build and verify if the task runs fine, and especially if the execution time is reduced.

![image](http://www.codewrecks.com/blog/wp-content/uploads/2017/04/image_thumb-9.png)

> _Figure 3: New GitVersion executable has a real boost in performance._

With few minutes of work, I upgraded my task and I'm able to use the new version of GitVersion.exe in all the builds, reducing the execution time significantly. Compare this with the old XAML build engine and you understand why you should migrate all of your XAML build to the new build system as soon as possible.

[Discover the six challenges and best practices in managing microservice performance](https://dzone.com/go?i=201130&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Ftop-6-performance-challenges-in-managing-microservices%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%252520zone%26utm_content%3Dtop-6-performance-challenges-in-managing-microservices%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital), brought to you in partnership with [AppDynamics](https://dzone.com/go?i=201130&u=https%3A%2F%2Fwww.appdynamics.com%2Flp%2Ftop-6-performance-challenges-in-managing-microservices%2F%3Futm_source%3Dsponsorship%26utm_medium%3Ddzone%26utm_campaign%3Djava%252520zone%26utm_content%3Dtop-6-performance-challenges-in-managing-microservices%26utm_term%3Ddzone-content-syn%26utm_budget%3Ddigital).

Topics:

execution ,simple ,tfs ,git ,version ,integration
