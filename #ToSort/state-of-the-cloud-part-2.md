# State of the Cloud 2017 (Part 2)

_Captured: 2017-04-25 at 00:44 from [dzone.com](https://dzone.com/articles/state-of-the-cloud-2017-part-2)_

[MongoDB Atlas is a database as a service that makes it easy to deploy, manage, and scale MongoDB](https://dzone.com/go?i=193126&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Dcloud%26jmp%3Ddzone-ad). So you can focus on innovation, not operations. Brought to you in partnership with [MongoDB](https://dzone.com/go?i=193126&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Dcloud%26jmp%3Ddzone-ad).

This blog is a continuation to [State of the Cloud 2017 (Part 1)](https://dzone.com/articles/state-of-the-cloud-2017-part-1). I got a good response for the various topics covered, and this blog outlines the state of few more key areas in cloud computing.

## Cloud Security

Our survey on cloud security indicates that organizations are convinced that the cloud is in no way less secure than hosted or on-premise data centers. As cloud adoption increases, concerns about security in Cloud are fading, but the measures and efforts for securing heterogeneous infrastructure are growing. Though we have seen an unprecedented number of data breaches, hacking, and other in threats in the past year, these security threats are not necessarily limited to cloud infrastructure. Organizations are taking security very seriously and seeing that as a separate vertical, whether the focus is on cloud or non-cloud infrastructure. Security is becoming an in-built consideration in any new product release, not an afterthought.

The following are the trends for security measures:

  1. Transforming from DevOps to DevSecOps.

  2. Managing security through a Security Operations Center (SOC).

  3. Adopting SaaS-based security services. The list of SaaS-based security services are covered in my other blog.

  4. A cloud strategy includes careful planning regarding workloads, data, applications, and the environment in private and public clouds.

Cloud service providers such as AWS, Azure, and Google Compute Engine are coming up with their own on-demand security services. This may be a threat for SaaS-based security service providers, but their ability to provide security services across these multiple clouds augurs well for them.

## Cloud Migration

Cloud migration may sound like a solved problem but it is not yet. Every customer defines their own approach for migration and not all migration is 100% automated and seamless yet. Typically, the large migrations are done by cloud SIs in partnership with any of the migration tool vendors. The migration is mostly a combination of tool-based and manual processes, as there are a lot of considerations based on modularity, scalability, and performance involved during the planning phase. There are multiple forms of migrations happening such as physical-to-cloud, virtual-to-cloud, and cloud-to-cloud. Migration happens either through a virtual image or the operating system. Appzero and Racemi are based on operating system migrations. Meanwhile, Zerto and Doubletake are based on virtual images.

AWS has introduced a set of migration tools that covers migration of applications, data, databases, and servers into AWS, but the reverse is not supported.

Microsoft introduced the Azure App Service Migration Assistant for migrating apps from Windows or Linux to the Azure App Service.

Cloud migration is not yet as seamless as it has to be. The hope is on containers to provide the ease of migration that organizations look for.

## Cloud PaaS Platforms

The PaaS platform was predicted to be the future of the cloud, but it did not live up to its expectations due to some of the changes during evolution. When we analyzed the PaaS market in 2012, we found there were 66 PaaS platforms under construction. Not all of them survive now. Out of the list, CloudFoundry and OpenShift emerged as the leaders in PaaS platforms. There are multiple siblings that came out of Cloudfoundry, such as Stackato, Appfog, Ironfoundry, etc.

PaaS platforms did not provide the transformational approach for customers to migrate their applications and did not provide the control and flexibility required to manage complex environments.

The evolution of cloud orchestration and containers sidelined the focus and growth of PaaS platforms, as they provided most of the features offered by PaaS platforms, but with fewer constraints.

OpenShift and Cloudfoundry started supporting Docker to take advantage of container images' mobility.

There have been multiple acquisitions of PaaS platforms, including Appfog by Centurylink, Stackato by HP, Cumulogic by CA technologies, and Makara by Red Hat.

We see that PaaS platforms have seen more use for new app development, rather than migration of existing applications.

## Cloud PaaS Service Providers

After all the emergence, convergence, and divergence in PaaS area, the leading PaaS service providers are Salesforce, Google App Engine, Red Hat OpenShift, IBM Bluemix, Engine Yard, and Heroku (acquired by Salesforce).

Not all PaaS platform providers provide PaaS services. While Azure and Google started with PaaS and moved to IaaS, AWS started with IaaS and added PaaS as part of their ecosystem of services.

PaaS sometimes finds itself as one of the services in an organization's cloud strategy instead of being the only strategy.

## Cloud Object Storage Platforms

Object storage is becoming an important building block for customers in their cloud adoption. OpenStack Swift is an open source object storage platform that is widely used and gaining popularity. Some of the world's largest storage clouds such as SwiftStack, Rackspace, and Internap, are built using OpenStack Swift. Hybrid object storage adoption is also on the rise. Most object storage platforms provide APIs, which are compatible with leading object storage service providers such as S3 or Azure Blob to support hybrid storage. Other object storage platforms include Red Hat Ceph, Cloudian, Scality, and EMC ECS.

## Cloud Object Storage Service Providers

Every cloud adoption by an organization is associated with the adoption of cloud object storage as well. Object storage is used for managing configuration files, backups, logs, etc. Like many other aspects of cloud computing, AWS S3 is considered a market leader in cloud object storage. The other leading object storage service providers are Azure Blob Storage, Swiftstack, Rackspace, Internap, Google Cloud Storage, Tiscali, and Scality. Object storage adoption is on the rise. The current trend in object storage is to have a hybrid object storage that helps in bursting to the cloud from enterprise object storage based on certain policies. The AWS Storage Gateway service is to accelerate hybrid storage. AWS also has a cheaper version of object storage called AWS Glacier, which is used for managing archives and backup.

## Cloud File Hosting Service Providers

Cloud file hosting has matured, and there are multiple players with market share. Dropbox, Google Drive, Microsoft OneDrive, AWS Cloud Drive, Apple iCloud, Sugarsync, and Mediafire are the leading cloud file storage service providers. File storage is largely driven by mobile and IoT devices. We see that enterprise file servers are getting migrated to cloud file hosting service providers. Enterprise cloud file hosting requires lot of accelerators on performance, migration, security, and availability, which is driving innovation and acquisition of innovation

We will come up with the State of the Cloud 2017 (Part 3) in a short while.

MongoDB Atlas is [the best way to run MongoDB on AWS](https://dzone.com/go?i=193125&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Dcloud%26jmp%3Ddzone-ad) -- highly secure by default, highly available, and fully elastic. [Get started free](https://dzone.com/go?i=193125&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Dcloud%26jmp%3Ddzone-ad). Brought to you in partnership with [MongoDB.](https://dzone.com/go?i=193125&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Dcloud%26jmp%3Ddzone-ad)

### Like This Article? Read More From DZone
