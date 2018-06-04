# Bitbucket Vs. GitHub

_Captured: 2018-02-26 at 20:28 from [dzone.com](https://dzone.com/articles/bitbucket-vs-github?edition=364100&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-02-26)_

How to Set Up Continuous Integration Pipelines with Drone on Ubuntu 16.04. Get the DigitalOcean [detailed tutorial](https://dzone.com/go?i=274449&u=https%3A%2F%2Fwww.digitalocean.com%2Fcommunity%2Ftutorials%2Fhow-to-set-up-continuous-integration-pipelines-with-gitlab-ci-on-ubuntu-16-04%3Futm_medium%3Dbumper%26utm_source%3Ddzone%26utm_campaign%3Dbrand%2Bsimplicity%2Bat%2Bscale%26utm_content%3Dconinuous%2Bubuntu%2Bdzonedevops).

In keeping with our journey around DevOps, today I wish to focus on DevOps tools. At MagenTys, it is not uncommon that someone has come to us with the same problem: they want to move their version control solutions from a source code version that was "imposed" some time ago, to something more modern, broadly accepted and that can easily integrate with their CI/CD pipelines.

I've come across a variety of teams with a range of control server versions, and despite what many may think, not everything out there is just Git and GitHub. There were teams using TFVC moving to Git, others deep into Perforce moving to SVN, even some with Visual SourceSafe (still!) migrating to Assembla Git! The most common of all are teams moving from the above to Git or from Git to GitHub or Bitbucket.

Within this article, I will be comparing two of the top rated and most-known version control systems on the market: Bitbucket and GitHub. I won't just be looking at their On-Premises versions, but their alternatives on the cloud as a service as well.

From a developer's point of view, both tools allow you to carry out common actions which are required by most Dev teams nowadays, these include:

  * Pull request
  * Code review
  * Inline editing
  * Issue tracking
  * Markdown support
  * Two-factor authentication
  * Advanced permission management
  * Hosted static web pages
  * Feature-rich API
  * Fork/clone Repositories
  * Snippets
  * 3rd party integrations

## Bitbucket

From the [Atlassian suite](https://magentys.io/atlassian-services/), Bitbucket comes as a distributed version control system based on Git. Very well-known for its full integration with other products in the Atlassian family such as Jira, Fisheye and Bamboo.The advantage Bitbucket holds over its competitors is that Bitbucket offers unlimited number of private repos.

To elaborate further on the features Bitbucket has to offer:

  * Supports Mercurial and Git
  * Has direct integration with Bamboo, Jira, Crucible and Jenkins
  * Supports external authentication with Github, Facebook, Twitter and Google
  * Can import repos easily from Git, Codeplex, Google Code, HG, SourceForge and SVN
  * Has branch comparison and commit history
  * Has a Mac and Windows client called **[SourceTree ](https://www.sourcetreeapp.com/)**and an Android app called **[BitBeaker](https://play.google.com/store/apps/details?id=fi.iki.kuitsi.bitbeaker&hl=en_GB)**
  * Release with Jira Software and Bitbucket, which are seamlessly integrated from branch to deployment. Create Bitbucket branches from within Jira Software or transition issues without ever leaving Bitbucket.
  * Pipelines are built within Bitbucket Cloud giving you end-to-end visibility from coding to deployment.

One downside, however, is that it does not include support for SVN but this can be easily amended migrating the SVN repos to Git with tools such as [SVN Mirror for Bitbucket.](https://marketplace.atlassian.com/plugins/org.tmatesoft.subgit.stash-svn-importer/server/overview?_ga=2.158539961.206740462.1518977646-1113002839.1518977646)

There are currently two versions of Bitbucket to choose from:

### Bitbucket Cloud (Hosted by Atlassian)

If you don't want to host your own Bitbucket server, this is the best option for you. It also offers a flexible pay as you go option to scale up and down your teams on a click. The plans offered are as follow:

> ## Free Plan: $0 per month
> 
> Free upto 5 users  
Jira software integration  
Unlimited private repos  
Projects  
Pipelines
> 
> *Includes: 50 min/month of builds and 1 Gb/month of LFS storage

> ## Standard Plan: $2 per user/month
> 
> Starts at $10/month  
Jira software integration  
Unlimited private repos  
Projects  
Pipelines  
Unlimited users
> 
> *Includes: 500 min/month of builds and 5 Gb/month of LFS storage

> ## Premium Plan: $5 per user/month
> 
> Starts at $10/month  
Jira software integration  
Unlimited private repos  
Projects  
Pipelines  
Unlimited users
> 
> *Includes: 1000 min/month of builds and 10 Gb/month of LFS storage

If you want to scale up in terms of using the building and storage capabilities of BitBucket, it offers 1000 more minutes for $10/month and 100 GB for also $10/month.

Payments are made on a monthly subscription basis and currently, there is no option for annual subscriptions on Bitbucket Cloud. If you don't want to pay by card and prefer Purchase Orders, please contact

### Bitbucket Server (Typically Azure or AWS)

If you wish to move from a single server deployment to a highly available, active-active cluster with Bitbucket Data Center. If you decide to instal your own Bitbucket server, you have a choice of two variants:

**Server**

  * Git based code hosting and collaboration for teams

  * A single server deployment

  * Perpetual license + free year of maintenance

**Datacenter**

  * Git-based code hosting and collaboration for teams

  * Active-active clustering for high availability

  * Smart mirroring for performance across geographies

  * Annual term license + maintenance

Moving on to the second tool within my comparison: GitHub.

## GitHub

Among the general features of GitHub, there are a few features which really stand out:

  * GitHub Pages and GitHub Gists
  * It supports SVN clients
  * Supports GIT
  * Direct integration with: Zendesk, Cloudbees, Travis, AWS, Codeclimate, Azure, Google Cloud and Heroku
  * Can easily import repos from Git, SVN, TFS, and HG

The disadvantage of using GitHub is that you have to pay for having a private repository, something that comes for free with every Bitbucket plan.

## Github.com (Hosted by Github)

[GitHub ](http://github.com/)is a very well-known development platform with more than a million teams forming its community. From [open source](https://github.com/open-source) to [business](https://github.com/business), you can host and review code, manage projects, and build software alongside millions of other developers.

As you probably know it's free, **BUT**, despite this free plan allowing you to create unlimited number of public repositories, it doesn't allow you to have private repositories. For that, you need to upgrade your free plan to one of the following subscription plans:

> ## Free Plan: $0 per month
> 
> Free plan, unlimited public repositories

> ## Developer Plan: $7 per month
> 
> Personal account
> 
> Unlimited public repositories
> 
> Unlimited private repositories
> 
> Unlimited collaborators

> ## Team Plan: $9 per month
> 
> Organization account
> 
> Unlimited public repositories
> 
> Unlimited private repositories
> 
> Team and user permissions
> 
> Starting at $25 / month which includes your first 5 users.
> 
> $9per user/month or $108 per user/year

> ## Business Plan:
> 
> Includes everything in the Team plan plus:
> 
> $21 per user/month or $250 per user/year or $2500 per 10 users /year (same as GitHub Enterprise)  
Organization account  
SAML single sign-on  
Access provisioning  
24/5 support with 8-hour response time  
99.95% uptime SLA

For more information, you can go to <https://github.com/pricing>.

## GitHub Enterprise (Typically Azure or AWS)

**GitHub Enterprise** is the on-premises version of [GitHub.com](https://github.com/home).

All repository data is stored on machines that you control, and access is integrated with your organization's authentication system (LDAP, SAML, or CAS).

GitHub Enterprise is delivered as a virtual appliance, this includes all software required to get up and running. The only additional software required is a compatible virtual machine environment.

The following minimal hardware requirements are suggested for production deployments:

  * Processor: Two 3.0 GHz CPU cores (or virtual equivalent)

  * Memory: 14-16 GB (minimum dependent on selected platform)

  * Disk: 80 GB VM root partition

  * 100 GB data partition (our recommendation, actual size depends on your data)

  * Storage: High-performance SAN or locally attached storage

As Virtual Environments supported, the following are available:

**Platform**
**Image Format**

[VMware](https://www.vmware.com/)
[OVF](https://en.wikipedia.org/wiki/Open_Virtualization_Format)

[OpenStack KVM](https://www.openstack.org/)
[QCOW2](https://en.wikipedia.org/wiki/Qcow#qcow2)

[XenServer](http://www.xenserver.org/)
[VHD](https://en.wikipedia.org/wiki/VHD_%28file_format%29#Software_support)

[Hyper-V](https://www.microsoft.com/en-us/server-cloud/solutions/virtualization.aspx)
[VHD](https://en.wikipedia.org/wiki/VHD_%28file_format%29#Software_support)

[Microsoft Azure](https://azure.microsoft.com/en-us/)
[VHD](https://en.wikipedia.org/wiki/VHD_%28file_format%29#Software_support)

[Amazon Web Services (AWS)](https://aws.amazon.com/)
[AMI](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html)

[Google Cloud Platform (GCP)](https://cloud.google.com/)
[Google Compute Engine (GCE) image](https://cloud.google.com/compute/docs/images)

One of the advantages of using GitHub enterprise is the integration with LDAP directory or IAM systems.

For hosting projects, as GitHub Enterprise is a private instance, it is designed for internal collaboration only, so **public projects are not allowed in it.**

GitHub Enterprise is not following the traditional pay per user per month model as [GitHub.com](http://github.com/), it is licensed under an annual subscription model where seats are purchased for a one-year period, this includes full support and access to all updates and upgrades.

Licenses must be purchased in 10-seat packs, with the price of $21 per user/month.

This includes, as we commented before:

  * Multiple organizations
  * SAML, LDAP, and CAS
  * Access provisioning
  * 24/7 support for urgent issues
  * Advanced auditing
  * Host on your servers, AWS, Azure, or GCP

But again, seats are sold in packs of 10 users and billed annually.

More information here: <https://enterprise.github.com/features#pricing>.

## Integration With Jira

Despite Bitbucket being an Atlassian product, both tools have full integration with Jira. When developers create a branch, create a pull request, commit code, etc, everything is reflected in your Jira tickets.

![JiraIntegration](https://eoblogdotnet.files.wordpress.com/2018/02/jiraintegration.jpg?w=640)

But not only that, using the [DVCS plugin in Jira](https://confluence.atlassian.com/adminjiraserver071/enabling-dvcs-smart-commits-802592225.html), you will be able to change some properties in your tickets just by adding the right comment in your repository operation, further capabilities include:

  * Comment on issues
  * Record time tracking information against issues
  * Transition issues to any status (for example 'Resolved') defined in the JIRA Software project workflow.
  * Add labels

In terms of quantity of integrations, The Atlassian Marketplace blows GitHub out of the water. Unifying your extensions under Atlassian means easier implementation and more coherent workflows, so you won't have to juggle between multiple app providers. The built-in compatibility will allow developers to leverage more tools more easily and code a better product.

## Integration With Jenkins

One thing to take very seriously is how your Version Control System integrates with other tools that form part of your CI/CD pipeline. Among the most popular CI/CD Automation Servers we have Jenkins, which is used extensively for many dev teams to build, test and deploy solutions in an automated way.

People may view Jenkins is being an Open Source tool as it has hundreds of plugins and customizations and it's very easy to integrate with any VCS. However, the same can't be said about integrating it with Github or Bitbucket than with TFVC or Perforce. Integration can be quite straightforward or be a real nightmare.

Both of them Github and Bitbucket have the classic integration with Jenkins, such as trigger on commit or pull request.

Jenkins, itself located on GitHub, has a number of plugins for integrating into GitHub. The primary avenues for integrating your Jenkins instance with GitHub are:

  * "Build integration" - using GitHub to trigger builds
  * "Authentication integration" - using GitHub as the source of authentication information to secure a Jenkins instance.

More info [here.](https://jenkins.io/solutions/github/)

For Bitbucket, it's a bit more clunky but it can be also done. There is a [nice article ](https://bjurr.com/continuous-integration-with-bitbucket-server-and-jenkins/)from Tomas Bjerre about how to do it.

Atlassian also has a paid [plugin for Jenkins here](https://marketplace.atlassian.com/plugins/com.nerdwin15.stash-stash-webhook-jenkins/server/overview) which is not really expensive and can get it done more efficiently.

For migrating from GIT to GitHub or Bitbucket, both of them follow similar procedures and are straightforward, no workarounds needed.

## Costs

Finally, I want to scope the cost for an average of **50 users** (dev, test, ops, etc) that want to work with private repositories **over the course of a year**:

[GitHub.com](http://github.com/): Team Plan: $5160

  * The Team Plan is $9 per month per user on the top of a payment of $25 per month (which includes 5 users at $5 cheaper rate).

  * Estimation 50 users on Team plan **per year**: $25×12(5 users) + $9×12*45 = $300 + $4860 = $5160

  * It can be paid monthly or per year

GitHub Enterprise: Business Plan: $12,600

  * $21 per user / month = $252 per year

  * Estimation 50 users on Enterprise Plan : $21x12x50 = $12,600

  * It has to be paid **per year**

Bitbucket Cloud: Standard Plan: $1,200

  * Costs are: $10 / month for first 5 users + $2 / user / month for additional users

  * Given this, 50 users under a Standard license would be: $10 (5 users) + $2*45 users =$100 per month = $1,200 per year

Bitbucket Enterprise: $3,600

  * Perpetual license on a payment based on the number of users (upgradable)

  * Total cost: 50 users for a year is $3,600

  * Prices are reduced when acquiring more users (for example 100 users is $6,600) (this estimation applies to the server installation, datacenter is slightly cheaper.Bitbucket Server has a perpetual license while Data Center has an annual term license that includes updates and support as long as your term license is active. Data Center licenses expire and are not perpetual like our server licenses)

There is an awesome calculator for Bitbucket to calculate how much it will cost you for cloud and on-premises [here](https://www.atlassian.com/purchase/product/bitbucket).

## Summary

At [MagenTys, ](http://magentys.io/)we have implemented both options many times, and I have to say that is a very good option if you know how to optimize your Cloud resources properly, as it's not only about installing in in a VM with the right access and network properties, but things like the cloud storage accounts can be monitored and optimized properly to save space or transactions and similar with the VMs usage, as you should be tweaking again and again these machines until they have their optimal resources usage according to your team habits.

Overall, the hosted options look very attractive for both Github and Bitbucket, integrating with Jira and Jenkins indistinctly. It is also much more affordable, also taking in consideration that if we want to host on our own servers we don't have to pay for the licenses or for hosting the server in our own infrastructure or cloud. However, thinking about the size of the VM to support the server installation, the server and data redundancy, the 24/7 support and the scalability, makes me seriously doubt whether it would be the best choice… unless you have some constraints about where your IP needs to be hosted in.

In terms of quantity of integrations, The Atlassian Marketplace blows GitHub out of the water. Unifying your extensions under Atlassian means easier implementation and more coherent workflows, so you won't have to juggle between multiple app providers. The built-in compatibility will allow developers to leverage more tools more easily and code a better product.

In terms of cost, moving Bitbucket for most teams would be the smart choice. Also migrating the Git repos to Bitbucket is not a heavy task and can be achieved without losing any history.

But as usual, my main recommendation would be to try both and then decide, as in the end it's better to see it with your own eyes. Opening a free bitbucket cloud account: just log in with your Atlassian account here: **<https://bitbucket.org/>. **Opening a free **[github.com](http://github.com/)** account: (you have one, you can create an organization inside for free with public repos): **<https://github.com/>.**

I hope this information is useful for you to decide which version control repository is more suitable for you and if you would like further advice and interested in moving your version control solutions to Bitbucket or Github, speak to us today at

And remember, DevOps is not a tool, it's not a guide, it's not a methodology, it's a journey.

We did the [research and have the tutorials](https://dzone.com/go?i=274450&u=https%3A%2F%2Fwww.digitalocean.com%2Fcommunity%2Ftutorials%2Fci-cd-tools-comparison-jenkins-gitlab-ci-buildbot-drone-and-concourse%3Futm_medium%3Dbumper%26utm_source%3Ddzone%26utm_campaign%3Dbrand%2Bsimplicity%2Bat%2Bscale%26utm_content%3Dci_cd%2Bcomparison%2Bdzonedevops) on how to install the top CI/CD tools. See how Jenkins, Gitlab CI, Buildbot, Drone and Concourse compare.
