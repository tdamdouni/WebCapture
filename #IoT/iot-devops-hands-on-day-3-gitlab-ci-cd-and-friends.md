# IoT DevOps Hands-On (Day 3): GitLab CI/CD and Friends

_Captured: 2018-06-19 at 19:50 from [dzone.com](https://dzone.com/articles/hands-on-iot-devops-day-3-gitlab-cicd?edition=383217&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202018-06-19)_

In this article, we continue our journey into the world of DevOps and IoT with [GitLab CI/CD](https://about.gitlab.com/features/gitlab-ci-cd/). That's right, GitLab has its own CI/CD solution and, actually, it's been used by many developers. Until recently, Gitlab CI/CD was only an end-to-end solution within the GitLab platform, but it seems that now they added support for external repositories as well. So, let's see how Gitlab CI/CD can be used in DevOps for IoT development.

![Image title](https://dzone.com/storage/temp/9333699-stacked-wm-no-bg-1.png)

No, wait! I think it's also a good time to share with you some interesting findings of the remaining CI/CD tools, because I realized that they do not seem much different, in terms of features and design. Actually, they look very similar. For that reason, in this article, we will also say a few words about the rest of the CI/CD tools that are available.

![Image title](https://dzone.com/storage/temp/9333658-screen-shot-2018-06-04-at-111209.png)

## Background

GitLab has integrated CI/CD pipelines to build, test, deploy, and monitor your code. You can run builds on multiple platforms like Windows, Linux, and Mac. Support for many languages is provided, like Java, Ruby, PHP, and C (yes, great for all the web developers out there but still nothing for the embedded world).

![GitLab CI/CD pipeline](https://docs.gitlab.com/ee/ci/img/cicd_pipeline_infograph.png)

> _GitLab CI/CD pipeline_

Like in the other CI/CD solutions, a special file called _.gitlab-ci.yml_, should be added in the root directory of our repository to configure GitLab and trigger the execution of the defined jobs. In GitLab, you can have a pipeline with multiple stages, e.g. build, test and deploy. Each stage can have a number of jobs that will run in parallel. The jobs of the next defined stage will run after the jobs from the previous stage have finished. I think this approach with the dedicated groups of jobs seems much better than Travis CI that we tested in the [previous article](https://dzone.com/articles/iot-devops-hands-on-day-2).

But, let's see how GitLab CI/CD can help us in an IoT device development workflow. For example, how can we use it for functional testing in an IoT device?

## GitLab CI/CD Setup

Since GitHub integration has been added recently in GitLab CI/CD, we don't need to move our project to a GitLab repository. That said, please note that this will be provided as a paid service from GitLab. Currently, they offer this integration for about 1 year for free.

Fortunately, the [quick start guide](https://docs.gitlab.com/ee/ci/quick_start/) is very helpful and I was really pleased to see that someone is actually caring about their documentation, great job guys!

To connect with GitHub, we need to go to <https://github.com/settings/tokens/new> and generate a new access token with _repo_ and _admin:repo_hook_ enabled. Then we create a new _CI/CD for external repo_ project and we select _GitHub._

![GitHub Integration](https://docs.gitlab.com/ee/ci/ci_cd_for_external_repos/img/github_omniauth.png)

> _GitHub Integration_

Next, we can paste the previously generated access token and we will be able to get a list of all our GitHub repositories with the option to "connect" them with GitLab.

![GitHub integration](https://dzone.com/storage/temp/9172652-screen-shot-2018-05-18-at-095856.png)

> _GitHub integration_

Now, everything is synchronized and every change of our GitHub repository will be reflected in the GitLab project. What is missing is to add the _.gitlab-ci.yml_ file and start playing with it.

## GitLab Playground 

In .gitlab-ci.yml, you can define one or more stages. Βy default, there are three stages: build, test, and deploy. We are free to define our job names, etc. An example to see the format of stages and jobs is shown below:

In the above example, the execution order is job1 and job2 (parallel), job3, job4.

Now, based on the [quick start guide](https://docs.gitlab.com/ee/ci/quick_start/README.html), let's try to convert the _.travis.yml_ file that we created in our [previous article](https://dzone.com/articles/iot-devops-hands-on-day-2) to a _.gitlab-ci.yml_ file.

As you can see, they look almost identical! Also, note that one job can be ignored by simply setting a dash in front of the job name -- e.g ".ota_update:" above will be ignored. One more interesting thing is that each job can have dependencies from other jobs, which is very helpful if one wants to have a meaningful workflow. Last, we can define the artifacts from the build stage and after running the jobs they will be available for download from the web interface. Cool!

Since we created the required _gitlab-ci.yml_ file, we are ready to go as soon as we push this file in our repository. Then, we can check the status of our pipelines and jobs from the GitLab CI/CD web interface.

![Image title](https://dzone.com/storage/temp/9278334-screen-shot-2018-05-29-at-134800.png)

![GitLab CI web interface](https://dzone.com/storage/temp/9278317-screen-shot-2018-05-29-at-134736.png)

> _GitLab CI web interface_

On the bad side, if you're using a shared runner (virtual runtime environment), you may encounter big delays (up to 10 minutes) until you get an available runner. Dedicated runners are available, but they require extra configuration. For example, one option is to install runners on a Kubernetes cluster.

In general, I believe GitLab has done a better job in terms of flexibility compared with Travis CI for example.

## GitLab CI/CD for IoT? No Thanks!

When it comes to IoT device development, we end up having the exact same problems with Travis CI that we covered in our [previous article](https://dzone.com/articles/iot-devops-hands-on-day-2). There is no automation in terms of setting up the build environment for an IoT hardware platform, and there is no "what's next" after getting a binary from the build system. What this means is that we are out of luck when we try to write some unit tests for an IoT device. And it becomes more challenging when we start talking about functional testing. How can I check if my smart bulb actually lights up or goes from red to green? I guess you agree that we cannot rely on the result of an HTTP request, right?

![Testing](https://dzone.com/storage/temp/9333712-testing-icon.png)

## GitLab Friends?

Except for Travis CI and GitLab CI/CD, there are plenty of popular CI/CD tools and services out there like TeamCity, CircleCI, Bamboo, Codefresh, Codeship, and the list is endless. Although, for an embedded developer that is trying to create and/or maintain his precious IoT hardware, all these tools seem very similar in terms of the end result. They all provide a way to build a binary for the hardware by manually adding all the required commands to the build job of each CI/CD tool. They all provide a way to run some tests, usually limited to the communication API of the device with the rest of the world.

Is this what we need? Of course not. What we need is to somehow add the actual hardware in the tests. That is what will make the biggest difference. Fully automated functional tests increase productivity, lead to robust products, reduce time to market, and save money. That's good news for Execs, but, even if you are the IoT device developer, automated tests make you sleep better as well -- no more horror themes with flying devices in your dreams!

![Functional Testing](https://blog.testfort.com/wp-content/uploads/2015/09/api.png)

> _Functional Testing_

## What Goes Around Comes Around

Nobody expects that a generic CI/CD tool or service will cover everything but it's obvious that they try hard for this to become more and more generic and to have new features and areas of support. But this race to perfection and completeness make them bad players for the specifics and, in our case, for the IoT device specifics. When we add the hardware to the equation, then everything is going south for the majority of the available CI/CD tools. It's where you'll be alone, trying to find ingenious solutions for testing, but that you know that in the end, you have to put your hands on the hardware and test it. You know that you have to create your unit and functional tests and test them one by one, manually.

![What Goes Around](https://coffeewiththelord.files.wordpress.com/2017/01/what-goes-around-comes-around-cartoon.jpg)

> _What Goes Around_

## What's Next?

So far, we talked about some of the most popular CI/CD tools and whether they fit well in IoT device development. The results were not very encouraging. In our final series of articles, we are going to cover [Spanner CI](http://www.spannerci.com), a very promising solution for Continuous Integration, specifically for IoT device development. Stay tuned!
