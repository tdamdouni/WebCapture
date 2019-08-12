# Jenkins Configuration as Code: Look Ma, No Hands

_Captured: 2018-09-07 at 16:08 from [dzone.com](https://dzone.com/articles/jenkins-configuration-as-code-look-ma-no-hands?edition=391208&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-09-07)_

Jenkins is highly flexible and is today the [de facto standard](https://jenkins.io/) for implementing continuous integration and continuous delivery (CI/CD). There is an active community that maintains [plugins](https://plugins.jenkins.io/) for almost any combination of tools and use cases. But flexibility has a cost: in addition to Jenkins core, many plugins require some system-level configuration to be set so they can do their job.

In some circumstances, a Jenkins administrator is a full-time position. One person is responsible for both maintaining the infrastructure, and also pampering a huge Jenkins master with hundreds of installed plugins and thousands of hosted jobs. Maintaining up-to-date plugins version is a challenge and failover is a nightmare.

This is like years ago when system administrators had to manage dedicated machines per service. In 2018, everything is managed as code using infrastructure automation tools and virtualization. Need a fresh new application server as a staging environment for your application? Just deploy a Docker container. Your infrastructure missing resources? Apply a Terraform recipe to allocate more on your favorite cloud.

What about the [Jenkins administrator role](https://go.cloudbees.com/docs/cloudbees-documentation/cjp-introduction/) in this context? Should they still spend hours in the web UI, clicking checkboxes on web forms? Maybe they already adopted some automation, relied on Groovy script voodoo or some home-made XML templating?

Early this year, we announced the first alpha release of Jenkins Configuration as Code (JCasC), a [fresh new approach](https://www.cloudbees.com/blog/use-configuration-code-plugin-declaratively-configure-your-jenkins-instance) to Jenkins configuration management, based on YAML configuration files and automatic model discovery. JCasC has been promoted as a [top-level Jenkins project](https://jenkins.io/projects/jcasc/), and the corresponding Jenkins Enhancement Proposal (JEP) has been accepted.

## What Can JCasC Do for Our Jenkins Administrator?

JCasC allows us to apply a set of YAML files on our Jenkins master at startup or on-demand via the web UI. Those configuration files are very concise and human-readable compared to verbose XML files the Jenkins uses to actually store configuration. The files also have user-friendly naming conventions making it easy for administrators to configure all Jenkins components.

Here's an example:

As you can see, you don't need a long explanation to understand how this YAML file will setup your Jenkins master.

## Benefits

The most immediate benefit of JCasC is reproducibility. An administrator can now bootstrap a new Jenkins master with the exact same configuration with only a trivial setup. This allows them to create a test instance and check the impact of plugin upgrades in a sandboxed environment. This also lets them be more confident in failover and disaster recovery scenarios.

Further benefits come when administrators start managing their Jenkins' YAML configuration files in source control like they do with Terraform configuration. Doing so gives them auditing and reversibility of their Jenkins master configuration. They can establish a sane configuration change workflow that runs a test Jenkins instance and ensure the configuration is healthy before actually applying any change to their production Jenkins master.

Last but not least, with an ability to quickly setup Jenkins masters and control them from a set of shared YAML configuration files, administrators can now offer per-team Jenkins instances, with more flexibility on installed plugins. A master becomes more or less a transient piece of infrastructure for your team, as long as they also manage build definition with Jenkinsfiles.

With configuration as code, we can stop having to treat our Jenkins master like a pet we need to pamper and start managing Jenkins masters as cattle you can replace without effort nor impact. Welcome to the "as code" world.

(They are still cute though, right?)

## OK, What's Next?

You can read more about the Jenkins Configuration as Code plugin on the project's [GitHub repository](https://github.com/jenkinsci/configuration-as-code-plugin). To chat with the community and contributors join our [gitter channel](https://gitter.im/jenkinsci/configuration-as-code-plugin) Or, come see us in person at [DevOps World | Jenkins World 2018](https://www.cloudbees.com/devops-world/san-francisco) to [discuss the JCasC project](https://devopsworldjenkinsworld2018.sched.com/event/F9Nh/look-ma-no-hands-manage-jenkins-configuration-as-code) and its future!

Also don't miss the next post from the Configuration as Code series, where we'll look at how JCasC works with sensitive data like passwords and other credentials.
