# The CI/CD Infrastructure: My Recommended Tools

_Captured: 2018-08-09 at 06:10 from [dzone.com](https://dzone.com/articles/the-cicd-infrastructure-my-recommended-tools?edition=385348&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-08-08)_

Read why times series is the [fastest growing database](https://dzone.com/go?i=283423&u=https%3A%2F%2Fwww.influxdata.com%2Ftime-series-database%2F) category.

In my last article, I detailed [CI/CD best practices for improving your code quality.](https://www.blazemeter.com/blog/5-ci-cd-best-practices-for-better-code-quality?utm_source=blog&utm_medium=BM_blog&utm_campaign=the-ci-cd-infrastructure-my-recommended-tools) Now, I want to explain how to set up a [CI/CD](https://www.blazemeter.com/continuous-integration?utm_source=blog&utm_medium=BM_blog&utm_campaign=the-ci-cd-infrastructure-my-recommended-tools) pipeline: choosing tools, installation, and execution. In this blog post, I will recommend tools for the pipeline. Next time, I will explain about installation and execution. Let's get started.

## CI/CD Infrastructure Tools

When setting up a CI/CD pipeline, the first thing we need to do is to create our infrastructure. This blog post will explain which types of tools you need to install and the tools I recommend for each type. Let's get started.

For a CI/CD pipeline, we need to install:

  * A source code repository;
  * Continuous integration software;
  * Code quality tools;
  * A repository manager to store binary artefacts (optional);
  * A communication tool (optional).

There are lots of mature open source tools to choose from.

## Source Code Repository

The Source Code Repository is used in the pipeline as a place from which to take the source code for processing: building, testing, deploying and so on. You can choose between a SaaS service like [GitHub](https://github.com/), [GitLab](https://gitlab.com/gitlab-com), or [Bitbucket](https://bitbucket.org/), which have free plans, or a self-hosted service (when you take GitLab and install on your server), which is more secure.

The best tool, in my opinion, is GitLab. It has an integrated issue tracker, a CI/CD tool, so you can build code similar to Jenkins right on GitLab, code coverage, auto deploy, Jira integration, a container registry a secure and private registry for Docker images), a wiki and many more features.

Here is a screenshot of the GitLab projects screen:

![](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/cicd1.png)

## Continuous Integration Software

Continuous Integration Software is used for the implementation of the CI/CD pipeline. The best open source tool for CI/CD in my opinion, which is also the most popular one, is [Jenkins](https://jenkins.io/) CI. Jenkins has a huge amount of plugins for almost everything and also has great integration with IDEs like [Eclipse](https://www.eclipse.org/) and [IntelliJ Idea](https://www.jetbrains.com/idea/).

Here is a [Jenkins](https://www.blazemeter.com/jenkins?utm_source=blog&utm_medium=BM_blog&utm_campaign=the-ci-cd-infrastructure-my-recommended-tools) Job screen:

## ![](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/cicd2.png)

## Code Quality Tools

A CI/CD pipeline is an implementation of the development process. The pipeline can be used to automate the development process, to make it faster, cheaper and less error-prone (humans make more mistakes and more often than robots). So, if code quality is important for your development process, you need to integrate your CI/CD pipeline with some Code Quality Tool.

Code quality tools are useful for displaying the estimation of code quality - easy and understandable visualizations of different code quality aspects: code coverage, tests failures, static code analysis and so on.

The most popular tools for checking code quality are static code analyzers like [PMD](https://pmd.github.io/), [checkstyle](http://checkstyle.sourceforge.net/), [FindBug](http://findbugs.sourceforge.net/), and [Checkmarx](https://www.checkmarx.com/). Jenkins CI has plugins or interactions with these tools.

I would recommend [SonarQube](https://sonarqube.org/) because it has a great integration with IDEs like Eclipse and IntelliJ Idea and you can see all code violations in real time in real time.

![](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/cicd3.png)

This is what the [sonarlint](https://www.sonarlint.org/) and IntelliJ Idea integration looks like:

## ![](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/cicd4.png)

## Binary Repository Manager

The binary repository manager is used to store binary artefacts. A CI/CD pipeline usually works like this: take the source code from the Source Code Repository, build it, test it, create versioned binary artefacts and put them in the Binary Repository Manager. After that, if required, the CI/CD pipeline can take the binaries that were already created from the Binary Repository Manager, and deploy them to an environment (like test, dev, staging or prod environment).

In other words, the Binary Repository Manager is required if you want to deploy the same binary to many environments, instead of building it again and again. After all, it is faster to deploy binaries that were already created than build new ones each time. The repository can also be used to deploy scripts. So, you can store Docker images in the repository and deploy them to a Kubernetes cluster, for example.

There are plenty of open source Binary Repository Managers. You can consider [Sonatype Nexus Repository](https://github.com/sonatype/nexus-public) or [Archiva](http://archiva.apache.org). [Here is comparison table of them.](http://binary-repositories-comparison.github.io/)

Here is a screenshot of Archiva:

![](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/cicd5.png)

## Communication Tool

A communication tool is useful in a CI/CD pipeline because it enables an immediate reaction on your side. For example, if the CI/CD pipeline sends a notification to a Communication Tool (like chat or email) when something went wrong, or when a new version of the software was deployed and it is ready for testing. In the second case, for example, the tester can start testing immediately to decrease the development cycle, which is the time between when the feature appeared in TODO until it was deployed to production. You can also use BlazeMeter to add automated performance testing to your CI/CD pipeline and cut out manual interference altogether.

I recommend open source RocketChat because it is mature, open-source, and has great integrations with other tools. I know many people prefer [Slack](http://info.blazemeter.com/slack-jmeter-lp?utm_source=blog&utm_medium=BM_blog&utm_campaign=the-ci-cd-infrastructure-my-recommended-tools); [here is a comparison between them.](https://stackshare.io/stackups/rocketchat-vs-mattermost-vs-slack)

Here is what RocketChat looks like:

![](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/cicd6.png)

> _That's it for now! Next time we will explain how to install my chosen tools: GitLab, Jenkins CI, SonarQube and Rocket.chat, and how to execute them in one pipeline._

## Running BlazeMeter in Your CI/CD Pipeline

Your performance tests should be part of your Continuous Integration Pipeline, to ensure that any code change doesn't degrade performance. You can add BlazeMeter to Jenkins with the BlazeMeter Jenkins Plugin, or to other CI tools through plugins or through our API. Then, run your tests and analyze with BlazeMeter's insightful reports.

This is the Jenkins integration:

![](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/cicd7.png)

Learn how to get 20x more performance than Elastic by [moving to a Time Series database](https://dzone.com/go?i=283422&u=https%3A%2F%2Fwww.influxdata.com%2Fresources%2Fbenchmarking-influxdb-vs-elasticsearch-for-time-series%2F%3Futm_campaign%3Ddbzone%26utm_medium%3Dpartner%26utm_source%3Ddzone%26utm_content%3D%26utm_term%3D).
