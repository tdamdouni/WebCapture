# Azure vs. AWS: Which One Is Better?

_Captured: 2017-04-16 at 10:32 from [dzone.com](https://dzone.com/articles/azure-vs-aws-which-one-is-better?edition=290923&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-15)_

[MongoDB Atlas is a database as a service that makes it easy to deploy, manage, and scale MongoDB](https://dzone.com/go?i=193126&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Dcloud%26jmp%3Ddzone-ad). So you can focus on innovation, not operations. Brought to you in partnership with [MongoDB](https://dzone.com/go?i=193126&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Dcloud%26jmp%3Ddzone-ad).

We've used Azure for nearly five years at Stackify; in fact, we [built Retrace](https://stackify.com/retrace-apm-for-azure/) with Azure in mind. But is Azure the right cloud for you? The battle between Azure and AWS is heated, so we decided to see how they measure up in this head-to-head comparison. (For a side-by-side, feature-by-feature comparison chart including Google Compute, check out [this post](https://stackify.com/microsoft-azure-vs-amazon-web-services-vs-google-compute-a-comparison/).)

Customers love Amazon Web Services (AWS). There is no doubt about that. The segment [earned](http://www.zdnet.com/article/stacking-up-the-cloud-vendors-aws-vs-microsoft-azure-ibm-google-oracle/) a profit of more than $3 billion on revenues of more than $12 billion for the full year of 2016. That's an increase from only a little less than $8 billion in revenues the year before.

That gives AWS a run rate of $14 billion, which is similar to the run rate posted by Microsoft for its commercial cloud services. While it does not mean that Microsoft's Azure is on equal footing as AWS as far as customers go, it does show us that Azure is a worthy contender for the cloud service provider of choice. This perception is definitely boosted by Azure's offerings, which can easily match those of AWS.

If anything, Amazon has the starting lead as it has been in the cloud computing services space for more than 10 years. Azure has only been a market player starting 2010. That is not to say that AWS is better by default because Microsoft is a known powerhouse and it has the resources to really create an outstanding product or service if it decides to. And by all indications, Azure is one of those products that the software giant is relying on for its revenues. So how does Azure really compare with AWS?

## The Essentials

Amazon's AWS has a range of offerings that fall under IaaS and each of these are categorized into four classes:

  * Content delivery and storage
  * Compute
  * Networking
  * Database

No matter which IaaS offering you get, you will be using Amazon's identity and security services such as AWS CloudHSM's key storage service and Amazon's own Active Directory. Not only that, AWS offerings also have a range of management tools that users can use, including AWS Config, AWS Cloudtrail and Cloudwatch.

Azure, on the other hand, also has four classes of offerings:

  * Data management and databases
  * Compute
  * Networking
  * Performance

Security and management tools include Active Directory Federation Services, Azure Active Directory, Multi-Factor Auth, among others, as well as a range of integrations for [Azure monitoring](https://stackify.com/azure-monitoring/) and performance tweaks.

## Developer Love: Deploying Apps and PaaS

One of the biggest advantages of cloud computing is the simplicity of deploying an application. As a developer, I want to deploy my app to multiple servers without having to deal with the actual servers. Being able to take advantage of PaaS features like SQL databases, caching, queueing, NoSQL, and other technologies are also a big deal. Developers can use services like Redis & Elasticsearch without having to figure out how to install and manage them.

Azure has multiple app deployment options for developers. Including App Services, Cloud Services, Service Fabric, Container Service, Functions, Batch, WebJobs, and more. No matter what type of application you are developing, Microsoft has great tools in place to help deploy and scale it.

AWS offers similar solutions with Container Service, Elastic Beanstalk, Lambda, and Batch. AWS does not have as many options or features on the app hosting side. Microsoft has flexed their knowledge of developer tools to have a little bit of an advantage for hosting cloud apps.

Containers seem to be the preferred mechanism to deploy apps in the future, especially for open source applications. Look for more and more advancements around hosting containerized apps in the cloud.

## Hybrid Cloud and Legacy Apps

One of the hindrances of companies that are planning to migrate to cloud computing is their use of legacy apps. Not all companies would have the resources to create new apps for the cloud environment or even start everything up. For those that need to rely on legacy apps, a hybrid cloud that would combine the cloud environment with their own data centers would be a lot of help.

Hybrid clouds are also one of the most popular choices for some companies that do not really want to make a full conversion to the cloud and would want to keep some of their data and systems in-house.

**Hybrid clouds are easier with Azure**, partly because Microsoft has foreseen the need for hybrid clouds early on. Azure offers solid support for hybrid clouds, where you can use your onsite servers to run your applications on the Azure Stack. You can even set your compute resources to tap cloud-based resources when necessary. This makes moving to the cloud seamless. Aside from that, there are several Azure offerings that help you maintain and manage hybrid clouds such as Azure Stack, Hybrid SQL Server, and Azure StorSimple. Microsoft's long history of working on enterprise IT gives them an upper hand when it comes to the hybrid cloud.

While Amazon realizes that it needs to strengthen its offerings to support hybrid clouds, it is still catching up, with more investments earmarked for hybrid clouds, according to [Brian Olsavsky](http://fortune.com/2016/08/01/amazon-hybrid-cloud-2/), Amazon's chief financial officer. Still, the retail giant currently has a handful of solutions that is geared for companies who wants hybrid cloud deployments such as Storage Gateway, Direct Connect, and DynamoDB Local.

## Azure vs. AWS for Microsoft Shops

Microsoft has long been synonymous with larger enterprise customers. Microsoft Azure definitely makes it easy for those currently using Windows Server, SQL Server, Exchange, and other Microsoft technologies to move to the cloud.

For .NET developers, publishing your application to Azure is amazingly simple. Publishing an app to Azure App Services or Cloud Services takes away all of the headaches of deploying apps and managing servers.

**For Microsoft shops, Azure will hold a strong edge**. Although, AWS supports Windows, SQL Server, and other technologies that .NET developers use. Amazon AWS has a great SDK for .NET. **AWS might be more compelling for .NET developers if there is a specific AWS feature that is needed that does not have an Azure equivalent**.

## Azure vs. AWS for Open Source Developers

Amazon might have started off as merely an online seller, but Microsoft has constantly had its eye on business customers focusing on Windows and similar platforms. Azure continues this rapport with enterprise users by making sure that integration with Visual Studio is smooth, as well as the integration with Active Directory. You can even use your current Active Directory account to sign on the Azure platform and Office 365.

However, Amazon shines when it comes to open source developers. Microsoft has historically been very closed to open source applications, and it turned a lot of companies off. **AWS, on the other hand, welcomed Linux users and offered several integrations for open source apps**.

**In recent times, Microsoft has openly embraced open source technologies**. Microsoft recently open sourced the .NET Framework, and the new .NET Core runs on Windows, MacOS, and Linux. SQL Server now runs on Linux. Microsoft also claims that about 1/3 of Azure Virtual Machines are running Linux and some of the infrastructure that drives [Azure even uses Linux](https://www.wired.com/2015/09/microsoft-using-linux-run-cloud/).

## Government Cloud

When you think of the cloud you probably think of startups and big tech companies. IT leaders working in the government are also working on moving their apps to the cloud. Government websites and other cloud deployments need to adhere to certain regulations, which is why putting government assets on public clouds raises warning flags as far as compliance is concerned.

The good news is that both Azure and AWS have a special section for government users. These government clients make use of this isolated area so that their workloads do not share the computing, networking and other resources with ordinary business users. Azure and AWS promise compliance with various regulations, such as the HIPAA, DISA, FIPS, among many others.

Want to read more? Check out [Azure Government Cloud](https://azure.microsoft.com/en-us/overview/clouds/government/) and [AWS Government Cloud](https://aws.amazon.com/federal/).

## License, Fees, and License Mobility

**AWS has always made it a point to give customers headache-free licensing**. It is all a matter of paying for the licenses that you use no matter what AWS offering you avail yourself of. But if you have Microsoft licenses that you've already paid for, you might be eligible for license mobility. This means that you do not have pay double for using the same Microsoft server applications you're currently using.

Azure also has the same license and mobility standards.

Do not assume, however, that all your Microsoft licenses are eligible. For instance, Windows Server is not a part of the list of eligible applications, but Exchange Server, SQL Server, Skype, System Center Server and Project Server are.

Estimated costs on the use of either AWS or Azure might be a little difficult to come up with, but both services currently offer cost calculators that users can use to get an idea of how much they can expect to spend on each platform.

## Features

On a per feature basis, you will find that most of all features offered on Azure have a corresponding or similar feature on AWS. And while it will be quite difficult to come up with an exhaustive features list, you might find it interesting that there are some Azure services that have no AWS equivalent. These include the Azure Visual Studio Online, Azure Site Recovery, Azure Event Hubs, and Azure Scheduler. However, it seems that AWS is trying to close the gap. For instance, AWS now offers AWS Lambda on preview to counter Azure's Logic Apps.

In the end, choosing between Azure and AWS would depend on what you really need and what they offer. Which one is better? There is simply no blanket and definitive answer to that question. Both AWS and Azure have free offerings and trials, so give each one a test run to help you get a feel of what to pick!

## Cloud Services Comparisons

The battle between Microsoft Azure and Amazon Web Services has been heated for months, and experts everywhere are placing bets on who's going to win the race. For more insights on the ongoing battle between these two leading cloud vendors, check out the following resources:

MongoDB Atlas is [the best way to run MongoDB on AWS](https://dzone.com/go?i=193125&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Dcloud%26jmp%3Ddzone-ad) -- highly secure by default, highly available, and fully elastic. [Get started free](https://dzone.com/go?i=193125&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Dcloud%26jmp%3Ddzone-ad). Brought to you in partnership with [MongoDB.](https://dzone.com/go?i=193125&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Dcloud%26jmp%3Ddzone-ad)
