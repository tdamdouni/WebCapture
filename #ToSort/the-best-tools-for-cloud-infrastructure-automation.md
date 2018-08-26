# The Best Tools for Cloud Infrastructure Automation

_Captured: 2018-05-01 at 16:12 from [dzone.com](https://dzone.com/articles/the-best-tools-for-cloud-infrastructure-automation?edition=376228&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202018-05-01)_

[Site24x7](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

Cloud migrations don't happen by themselves--there's [no shortage of tasks](https://docs.newrelic.com/docs/guide-planning-your-cloud-adoption-strategy) to complete before declaring the project a success. One of the biggest benefits of a cloud move is the opportunity to reduce toil and operating costs, and one of the most important elements is the automation and configuration of your new cloud infrastructure. By automating the provisioning, configuration, and management of your cloud-based infrastructure, your organization can free up time and resources for mission-critical innovation instead of routine maintenance.

Fortunately, there are many cloud infrastructure automation tools available to help speed the process. In addition, a number of related tools may also be helpful. While no single tool is right for every situation, this guide can help you consider the various benefits offered and choose the ones that best serve your cloud infrastructure needs, whether your migration targets public, private, or hybrid cloud architectures.

## AWS CloudFormation

Helping to secure its leadership in all things "cloud," Amazon's AWS CloudFormation allows you to model resources in YAML or JSON, automate them, and then deploy them in your AWS cloud-based infrastructure.

If you use or plan to use AWS-based cloud offerings, CloudFormation can help ensure configurations are as easy as possible for all your teams.

CloudFormation lets you run a huge list of other AWS tools right out of the box, including [Amazon CloudWatch](https://aws.amazon.com/cloudwatch/) and [AWS Elastic Beanstalk](https://aws.amazon.com/elasticbeanstalk/?hp=tile&so-exp=below). CloudFormation also handles automated management of cross-region accounts, making it easier to expand into new locales as your business scales. [CloudFormation Change Sets](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-updating-stacks-changesets.html) are a great way to preview impending changes to your infrastructure before they happen.

If you plan on using the AWS cloud, let CloudFormation do as much heavy lifting as you need it to.

## Puppet

A longtime leader in the configuration automation market, Puppet helps some of today's largest software teams model, configure, and systematically enforce desired configurations of their infrastructures. With [Puppet Enterprise](https://puppet.com/products/puppet-enterprise)--the company's commercial offering--you can manage all aspects of your cloud-based infrastructure, from compute to storage to networking resources, at an impressive scale (think upwards of 20,000 nodes for a basic deployment). And it works on public, private, and hybrid clouds. You write modules in Puppet's domain-specific language (DSL) that provide code for the configurations that are enforced by an agent you install on each node.

With Puppet Enterprise, you get out-of-the-box orchestration and task-based command execution and multi-device management. It's GUI console makes it easy to classify and manage all the cloud machines you've deployed. And while the Puppet DSL is known for taking a while to learn, the payoff can be huge.

Puppet maintains integrations and partnerships with major players like Microsoft, VMware, Google, and Amazon. AWS Opswork for Puppet Enterprise, for example, provides a fully integrated suite of automation tools for managing your cloud-based infrastructure.

If on-the-mark enforced configuration and drift remediation is what you need, Puppet is the automation tool for you.

![](https://blog.newrelic.com/wp-content/uploads/cloud-gears-min.jpg)

## Ansible

Recently brought under the [RedHat](https://www.redhat.com/en) umbrella, Ansible is quickly becoming an industry standard based on its easy-to-use, task-based infrastructure automation. Ansible boasts that you don't need an advanced degree in computer science to write automation, configuration, or orchestration tasks in its simple language, which you package in "playbooks." Additionally, you can easily manage all aspects of your cloud infrastructure without installing a single agent anywhere in your cloud infrastructure.

Key capabilities of [Ansible Tower](https://www.ansible.com/products/tower) (Ansible's commercial offering) include job scheduling, GUI-based inventory management, multi-playbook workflows, and a flexible REST API that lets you embed Ansible Tower in almost any task-based configuration management process.

Major integrations include AWS, Microsoft Azure Cloud Computing, VMware, Rackspace, Digital Ocean, and Google Cloud Computing.

Automating configurations with Ansible's tasks execution may make your job feel a bit too easy.

## Chef

Chef is another veteran player in the infrastructure configuration game. Like Puppet, Chef provides its own DSL to help you enforce everything from configuration policies to continuous delivery of production code. For [Chef Automate](https://www.chef.io/automate/) users (Chef's commercial platform), you can automate the management of your self-hosted AWS-based infrastructure on an hourly basis or use [AWS Opswork](https://aws.amazon.com/opsworks/) for Chef Automate.

With Chef Automate you can expect critical features like detailed compliance management, high availability, and GUI-based workflow pipeline creation.

Major integrations include AWS, Microsoft Azure Cloud Computing, VMware, and Google Cloud Computing.

Chef is a solid choice if compliance management is what you need.

## Kubernetes

Originally developed by Google, Kubernetes is a container orchestration platform for automating the deployment, scaling, and management of containerized applications. In fact, it's [established itself as the defacto standard for container orchestration](https://blog.newrelic.com/2017/11/09/docker-kubernetes-future/) and is the flagship project of the [Cloud Native Computing Foundation](https://www.cncf.io/), backed by key players like Google, AWS, Microsoft, IBM, Intel, Cisco, and RedHat.

While it's by no means an actual infrastructure configuration management tool, Kubernetes makes it easy to deploy and operate applications based on a microservice architecture for almost any cloud. It does so by creating an abstraction layer on top of a group of hostsso that development teams can deploy their applications and let Kubernetes manage things like controlling resource consumption by application or team, evenly spread application loads across their host infrastructure, and automatically load balance requests across the different instances of an application.

Thinking about adopting containers and a microservices architecture? Many suspect that Kubernetes may one day make traditional configuration management tools completely obsolete.

## Terraform

Another aspect of infrastructure management is the idea of "infrastructure as code." The Big 3 all claim this as a central philosophy, and Terraform is no different. Put simply, Terraform is an open source tool that you use to write declarative configuration files to create and modify infrastructure, but it's not exactly a "configuration automation tool."

If you used the company's commercial product [Terraform Enterprise](https://www.hashicorp.com/products/terraform) in a cloud-based workflow (in AWS, for example), you'd write modules that are version-controlled configurations declaring the creation or modification of high-level resources, such as Amazon EC2 instances or Amazon Relational Database Service (RDS) resources. Terraform can help you automatically configure these resources with the aid of extensive resource graphing and execution plans. But you'll still likely need a configuration management tool like Puppet or Chef to help you automate the setup and execution of the software on those resources.

Major integrations for Terraform include AWS, Google Cloud Platform, Microsoft Azure Cloud Computing, and Oracle Cloud.

Terraform takes "infrastructure as code" pretty seriously. You're gonna get exactly what you expect here-strong, stable declarative configurations.

## Google Cloud Deployment Manager

If you plan to build your cloud infrastructure with [Google Cloud Computing](https://cloud.google.com/), check out Cloud Deployment Manager. Here you can automate the configuration and deployment of your Google cloud with parallel, repeatable deployments and template-driven configurations. Cloud Deployment Manager provides a rich set of tools from CLIs and APIs to GUIs for managing all phases of your infrastructure's configuration and management, from resource creation to deletion.

## Microsoft Azure Automation

Azure Automation delivers a cloud-based automation and configuration service that provides consistent management across Azure and non-Azure environments. It consists of process automation, update management, and configuration features designed to help you reduce errors and cut the time spent on your infrastructure deployments. Azure Automation also provides automated control over maintenance and compliance runs.

Best of all, it's not just for Windows! With Azure Automation, you get heterogenous deployments for Windows or Linux hosts using automation that you trigger with PowerShell or Python runbooks.

Microsoft is clearly showing its dedication to the modern DevOps practitioner. If you need to a run a diverse set of operating systems, Azure could be a great way to roll.

## Cisco Intelligent Automation for Cloud

Cisco provides a number of cloud offerings, from private to public to hybrid solutions. Alongside these offerings, Cisco Intelligent Automation for Cloud gives everything from infrastructure-as-a-service (IaaS) to hands-on provisioning and management of instances running in the Cisco cloud or in other cloud environments, including AWS, [OpenStack](https://www.openstack.org/), and [VMware](https://www.vmware.com/).

Top features include a self-service portal for users of your cloud, multi-tenancy, and network service automation. Though clearly created with Cisco's own cloud infrastructure offerings in mind, Cisco Intelligent Automation for Cloud benefits from being able to extend the automation tooling into other ecosystems.

Some pretty great features include a self-service portal for users of your cloud, multi-tenancy, and network service automation.

Cisco is a proven, stable giant and it looks like its automation services are perfect for those needing a one-stop full-service provider.

## SaltStack

Originally an open source project like Puppet and Chef, Saltstack has also joined the enterprise sphere, with a big focus on automating security compliance. Like Ansible, SaltStack can be run agentless (but you can also run an agent if your workflows require it).

If you're interested in moving to the cloud, SaltStack provides an interface for interacting with cloud providers called [Salt Cloud](https://docs.saltstack.com/en/latest/topics/cloud/), so you can use Salt to configure and manage all aspects of your cloud-based infrastructure.

Key capabilities of SaltStack include agentless node management and exceptional security compliance tooling. It also has major cloud integrations with AWS, Microsoft Azure cloud computing, VMware, Rackspace, Digital Ocean, OpenStack, and Google Cloud Computing.

Security compliance is seemingly a huge deal these days, so if this is a concern, maybe SaltStack is the way you want to go.

## VMware vCenter Configuration Manager (VCM)

This small slice of the VMware world helps you configure and maintain your VMware cloud environments (running on vendors like AWS and RackSpace) so they meet your operational, security, and compliance requirements.

VCM gives you a central location to control configuration of your VMware-based infrastructure, whether it's running on Windows, Linux, or Unix operating systems. You'll also have a selection of VMware integrations at your fingertips--useful to help keep track of configuration data, change data, networking configurations, and compliance policies using a number of VMware tools, including vCenter, vCloud Director, and VMware vCloud Networking and Security.

## CFEngine

CFEngine is a classic configuration management tool that's long been used to automate IT infrastructures in all sizes of enterprises. Unlike tools such as Puppet that require a central management server, CFEngine relies on "autonomous agents" that run every five minutes to enforce their hosts' configurations. Impressively, CFEngine lets you manage up to 5,000 hosts per management server.

CFEngine integrates with your Amazon EC2 infrastructure.

If you're looking for stability and scale, check out CFEngine.

## Foreman

If you need a lightweight tool to manage the full lifecycle of your servers, from bare metal to provisioning to orchestration, the open source Foreman project can help. However, note that Foreman relies on a fairly deep integration with open source Puppet for configuration management of your nodes, but it also boasts plugin support with Chef, Ansible, and Salt for other management aspects.

Its dedicated open source community maintains an extensive plugin library. You can provision cloud instances with Foreman on major providers such as Amazon EC2, Google Cloud Computing, OpenStack, and VMware.

Foreman is definitely one of the best options for teams building open source software.

## Conclusion

Every infrastructure automation tool has its strengths, weaknesses, and learning curves. In choosing a tool, you'll want to find the one that best matches the needs of your project and the needs of your teams. Cloud-vendor built tools may provide the easiest way to get the ball rolling as you start your cloud migration, especially if a "one-stop shop" is what you're looking for.

That said, tools like Puppet, Chef, and Ansible have built tremendous reputations with DevOps practitioners managing infrastructures in all kinds of cloud environments, and their integrations prove it. But be sure to do your homework because some of the related tools may have exactly what you need. In fact, in many cases, you may find that the best of approach is to combine two or more of these tools.

[Site24x7](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)
