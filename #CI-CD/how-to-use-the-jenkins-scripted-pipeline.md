# How to Use the Jenkins Scripted Pipeline

_Captured: 2018-03-29 at 20:47 from [dzone.com](https://dzone.com/articles/how-to-use-the-jenkins-scripted-pipeline?edition=371191&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-29)_

[Jenkins](https://jenkins.io/) is an open source [continuous integration](https://www.blazemeter.com/blog/continuous-integration-101-how-run-jmeter-jenkins?utm_source=blog&utm_medium=BM_blog&utm_campaign=how-to-use-the-jenkins-scripted-pipeline) server that provides the ability to continuously perform automated builds and tests. Several tasks can be controlled and monitored by Jenkins, including pulling code from a repository, performing static code analysis, building your project, executing unit tests, automated tests and/or [performance tests](https://www.blazemeter.com/load-testing?utm_source=blog&utm_medium=BM_blog&utm_campaign=how-to-use-the-jenkins-scripted-pipeline), and finally, deploying your application. These tasks typically conform a continuous delivery pipeline.

[Pipelines](https://jenkins.io/doc/book/pipeline/) are a suite of [Jenkins](https://www.blazemeter.com/jenkins?utm_source=blog&utm_medium=BM_blog&utm_campaign=how-to-use-the-jenkins-scripted-pipeline) plugins. Pipelines can be seen as a sequence of stages to perform the tasks just detailed, among others, thus providing continuous releases of your application. The concept "continuous" is relative to your application and/or environment: In some cases, releases can be performed on a daily basis while for others could be weekly, depending on your business needs. In some situations - a critical fix, for example - it would be desirable to have your environment ready to release your application as soon as possible. Pipelines provide a way to do this through an automated process.

In Jenkins, Pipelines are specified by using a specific DSL following almost the same structure as [Groovy](https://www.blazemeter.com/blog/groovy-new-black?utm_source=blog&utm_medium=BM_blog&utm_campaign=how-to-use-the-jenkins-scripted-pipeline) to specify its statements and expressions. This makes pipelines easy to use for Groovy savants.

Starting with [Jenkins 2.0](https://www.blazemeter.com/blog/jenkins-20-new-devops-engineer-your-team?utm_source=blog&utm_medium=BM_blog&utm_campaign=how-to-use-the-jenkins-scripted-pipeline), the pipeline functionality comes right out of the box, meaning that no configuration needs to be made to be able to create them. Another improvement is that pipelines can be specified as code, enabling you to develop a pipeline script and add it to your code repository so you can version it.

By using script, releases of code can be pushed to the repository along with pipeline scripts in order to test specific functionalities just developed. This is done to ensure no bugs were introduced and that the application can perform with at least the same response times as the previous code. So, you can develop your pipeline script to execute automated tests only for specific flows and run performance tests by invoking [Apache JMeter™](http://jmeter.apache.org) only for the desired test cases.

In this post, we will discuss the [Scripted Pipeline](https://jenkins.io/doc/book/pipeline/syntax/#scripted-pipeline) (Pipeline as Code) in detail, while explaining its structure and providing examples of how to use it. More information on using Jenkins Pipelines with JMeter can be found in the blog post [Continuous Integration 101: How to Run JMeter With Jenkins](https://www.blazemeter.com/blog/continuous-integration-101-how-run-jmeter-jenkins?utm_source=blog&utm_medium=BM_blog&utm_campaign=how-to-use-the-jenkins-scripted-pipeline). Also, the post [How to Run a JMeter Test with Jenkins 2.0 Pipelines and GitHub](https://www.blazemeter.com/blog/how-run-jmeter-test-jenkins-20-pipelines-and-github?utm_source=blog&utm_medium=BM_blog&utm_campaign=how-to-use-the-jenkins-scripted-pipeline) provides an example of how to run [JMeter](http://www.blazemeter.com/jmeter-load-testing?utm_source=blog&utm_medium=BM_blog&utm_campaign=how-to-use-the-jenkins-scripted-pipeline) tests by using a Pipeline script.

With the introduction of the Pipeline, Jenkins added an embedded Groovy engine, making Groovy the scripting language in the Pipeline's DSL.

Here are the steps you need to take to set up a Jenkins Pipeline.

1\. First, log on to your Jenkins server and select "New Item" from the left panel:

![](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/pipe1.png)

2\. Next, enter a name for your pipeline and select "Pipeline" from the options. Click "Ok" to proceed to the next step:

![](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/pipe2.png)

> _3. You can now start working your Pipeline script:_

![](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/pipe3.png)

The red box in the middle is where you can start writing your script, which will be explained now.

Pipelines have specific sentences or elements to define script sections, which follow the Groovy syntax.

## Node Blocks

The first block to be defined is the "node:"

A "node" is part of the Jenkins distributed mode architecture, where the workload can be delegated to multiple "agent" nodes. A "master" node handles all the tasks in your environment. Jenkins agent nodes offloads builds from the master node, thus performing all the pipeline work specified in the node block. Detailed information on this can be found at [Jenkins Distributed builds](https://wiki.jenkins.io/display/JENKINS/Distributed+builds).

This block is not mandatory but it is desired and can be considered as a good practice, since with the code included in this block, Jenkins will schedule and run all the steps once any node is available and creates a specific workspace directory.

## Stage Blocks

The next required section is the "stage:"

Your pipeline will consist of several steps that can be grouped in stages. Among these stages you might have:

  * Pull code from the repository
  * Build your project
  * Deploy your application
  * Perform functional tests
  * Perform performance tests

Each of the these can include more than one action. For example, a stage to deploy your application can consist of copying the files to a specific environment for functional tests and to a dedicated server for performance tests; and once files are copied successfully, proceed to deploy it.

Each stage block specifies the tasks to be performed. For example, a full scripted pipeline might be:

This script has the following stages:

  * Build stage:
  * Selenium tests stage: 
    * dir(automation_path): Changes the current directory to the value set on the automation_path variable.
    * bat "mvn clean test ... ": Invokes maven to perform tests specified in the suite "SMOKE_TEST" and using the values defined on "QA". Also, the "clean" flag will clean the build.

Stage blocks are also optional, but they are recommended because they provide an organized way of specifying tasks to be executed in the script.

[Jenkins](https://www.blazemeter.com/blog/are-you-using-jenkins-right-way?utm_source=blog&utm_medium=BM_blog&utm_campaign=how-to-use-the-jenkins-scripted-pipeline) provides an interface that generates pipeline sentences for predefined actions that can be added to any of the script stages. On your pipeline script page, click on "Pipeline Syntax" to access the following page:

![](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/pipe4.png)

For example, to create a script command to execute a windows batch file, select the following:

![](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/pipe5.png)

Clicking on "Generate Pipeline Script" will create the desired sentence that can be added to your script right away.

Pipeline as code is based on the idea of being able to add the pipeline script to a code repository for source control and versioning. The text file containing the code of your pipeline is also known as a Jenkinsfile.

Writing your pipeline into a Jenkins file and make it part of your application repository for source control has several advantages: it can be reviewed/edited by other team members and the file can be versioned and included with your application builds.

Your Jenkinsfile can be edited through the Jenkins web interface or with a text editor, and you can also edit it with your prefered IDE, thus making it part of your project. Then, you can configure Jenkins to automatically poll your repo, while triggering new builds when updates to it are detected. This can be done through the following screen on your Project configuration under "Build triggers" section:

![](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/pipe6.png)

Enabling "Poll SCM", allows you to enter a cron-like expression in the Schedule text box. Configuring Jenkins to poll your repo is not a clean and efficient way to retrieve updates. Instead, Git Hooks is a neat way of doing it. The document at [Customizing Git - Git Hooks](https://git-scm.com/book/be/v2/Customizing-Git-Git-Hooks) provides information on how to configure it.

Jenkins limits the execution of any Groovy script by providing a sandbox. The option "Use Groovy Sandbox", shown below, is available in the Pipeline tab, and it allows the scripts to be run by any user without requiring administrator privileges. In this case, the script is run only by using the internal accessible APIs (that allow you to develop your script by using Groovy).

![](https://cdn2.hubspot.net/hubfs/208250/Blog_Images/pipe7.png)

When unchecked, if the script has operations that require approval, an administrator will have to provide them. This method is known as "Script approval". By default, all Jenkins pipelines run in a Groovy sandbox. If the option is checked and unauthorized operations are used, the script will fail when run. Both the whitelist and the blacklist of functions can be checked at [Script Security's built-in list](https://github.com/jenkinsci/script-security-plugin/tree/master/src/main/resources/org/jenkinsci/plugins/scriptsecurity/sandbox/whitelists). Please refer to [In-process Script Approval](https://jenkins.io/doc/book/managing/script-approval/) for more information on this topic.

One of the latest Pipeline improvements is the [Jenkins Declarative Pipeline](https://jenkins.io/doc/book/pipeline/syntax/#declarative-pipeline), which is a bit different than the Scripted Pipeline that we have been discussing. Both are implementations of the pipeline as code, but the Declarative way is designed to make it easier to develop and maintain your code by providing a more meaningful syntax. These two enhancements are achieved by adding syntax elements allowing you to define a different pipeline skeleton.

Basically, a scripted pipeline has the following skeleton:

On the other hand, a declarative pipeline can be written by using more elements, as shown next:

The script has the elements "pipeline", "agent" and "steps" which are specific to Declarative Pipeline syntax; "stage" is common to both Declarative and Scripted; and finally, node" is specific for the Scripted one.

  * "Pipeline" defines the block that will contain all the script content.
  * "Agent" defines where the pipeline will be run, similar to the "node" for the scripted one.
  * "Stages" contains all of the stages.

In this blog, we have reviewed Jenkins pipeline as code. We also provided guidelines on how to develop your pipeline scripts along with its advantages. For full documentation please refer to [Jenkins pipeline](https://jenkins.io/doc/book/pipeline/).

Learn how to use Jenkins for all of your testing needs for free from our [Continuous Testing Academy.](https://www.blazemeter.com/jmeter-tutorial#continuous-testing?utm_source=blog&utm_medium=BM_blog&utm_campaign=how-to-use-the-jenkins-scripted-pipeline)

You can also integrate [BlazeMeter](http://info.blazemeter.com/testing-landing-page2?utm_source=blog&utm_medium=BM_blog&utm_campaign=how-to-use-the-jenkins-scripted-pipeline) into your Jenkins Pipeline. Try out running your performance tests in BlazeMeter by [requesting a demo](http://info.blazemeter.com/live-request-a-demo?utm_source=blog&utm_medium=BM_blog&utm_campaign=how-to-use-the-jenkins-scripted-pipeline) or putting your URL in the box below, and your test will start in minutes.
