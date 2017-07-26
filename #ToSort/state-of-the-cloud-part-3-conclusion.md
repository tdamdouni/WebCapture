# State of the Cloud 2017 (Part 3, Conclusion)

_Captured: 2017-04-25 at 00:42 from [dzone.com](https://dzone.com/articles/state-of-the-cloud-2017-part-3-conclusion?utm_content=bufferd7de0&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[MongoDB Atlas is a database as a service that makes it easy to deploy, manage, and scale MongoDB](https://dzone.com/go?i=193126&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Dcloud%26jmp%3Ddzone-ad). So you can focus on innovation, not operations. Brought to you in partnership with [MongoDB](https://dzone.com/go?i=193126&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Dcloud%26jmp%3Ddzone-ad).

This blog outlines the emergence, convergence, and divergence of some more key areas in cloud computing. This blog is a continuation to State of the Cloud 2017 [Part 1](https://dzone.com/articles/state-of-the-cloud-2017-part-1) and [Part 2](https://dzone.com/articles/state-of-the-cloud-2017-part-2). Thanks for following this series, your continued feedback, and your support. This is the last part of the State of the Cloud 2017 series. As we all know, cloud computing is expanding in multiple areas, and this series of blogs is to provide a bird's eye view of various areas and its current state for the year 2017. The stakeholders of these multiple areas in cloud computing can be broadly classified as cloud service providers, cloud platform/tools providers (ISV), SIs/MSP, and cloud consumers. The consumption can be further classified as enterprises/SMBs/ISVs. The various key areas and stakeholders in cloud computing are depicted in the diagram below.

![](https://www.cloudenablers.com/wp-content/uploads/2017/04/stateofcloud-3.png)

![](https://www.cloudenablers.com/wp-content/uploads/2017/04/cloud3service.png)

## Enterprise File Sharing Platform

As per this Marketandmarkets [report](http://www.marketsandmarkets.com/Market-Reports/enterprise-file-sharing-and-synchronization-market-149308334.html), the Enterprise File Sharing and Synchronization market is expected to grow from USD 1.11 billion in 2015 to USD 3.51 billion by 2020, at a compound annual growth rate (CAGR) of 25.7%. Composed EFSS trends, the demand for cloud-based integration, and Bring-Your-Own-Device (BYOD) adoption have enabled wider adoption of EFSS solutions among many industries. Companies are increasingly adopting EFSS solutions to effectively share and manage the voluminous data being generated in their business processes on a daily basis and to improve the data security.

There are quite a number of players offering Enterprise File Sharing platform. Some of the leading players in this segment are [Sharefile](https://www.citrix.com/products/sharefile/), [Box](https://www.box.com/), [ownCloud](https://owncloud.org/), [Egnyte](http://www.egnyte.com/), [Sparkleshare](https://www.sparkleshare.org/), [Seafile](https://www.seafile.com/en/home/), [Pydio](https://pydio.com/), [Syncplicity](https://www.syncplicity.com/), and [WatchDox](https://us.blackberry.com/enterprise/blackberry-workspaces). ownCloud, Seafile, and Pydio are open-source platforms. Some of the acquisitions happened in this realm, including Syncplicity being acquired by Axway, WatchDox being acquired by Blackberry, and Sharefile being acquired by Citrix.

## Cloud Storage as a Service Providers

Storage needs are increasing for enterprises like never before due to the increased need for real-time applications, analytics, AI, machine learning, containers, etc. IDC expects [cloud IT infrastructure spending](http://www.forbes.com/sites/louiscolumbus/2016/03/13/roundup-of-cloud-computing-forecasts-and-market-estimates-2016/#2c7808e774b0), which includes [cloud data storage](http://info.zadarastorage.com/getting-great-performance-in-the-cloud-whitepaper-0), to increase at a compound annual growth rate (CAGR) of 15.1% between 2014 and 2019, reaching $53.1 billion by the latter year.

As per [TechTarget](http://searchstorage.techtarget.com/news/450411311/Enterprise-storage-market-poised-for-more-disruption-in-2017), the enterprise storage market is heading for more disruption in 2017. There are multiple sub-segments, like SDS, hyperconvergence, storage virtualization, storage controllers, etc. Our focus in this blog is limited to Cloud-Storage-as-a-Service providers whose storage can be consumed through the cloud such as AWS, Azure, and OpenStack.

Though the storage is available as part of the offering from cloud service providers, there are few enterprise-class, full-featured cloud storage service providers for specialized needs such as secure data in public or hybrid clouds, high performance, etc. There are not many players in this segment. The leading Cloud-Storage-as-a-Service providers for the enterprise are [Zadara Storage](https://www.zadarastorage.com/), [NetApp](http://www.netapp.com/us/solutions/cloud/hybrid-cloud/index.aspx), [Nimble Storage](https://www.nimblestorage.com/technology-products/nimble-cloud-volumes/), and [SoftNAS](https://www.softnas.com/wp/).

## Cloud Block Storage Platform

There is rapid growth anticipated in the adoption of virtual private clouds by enterprises for different tiers. As per [reports](https://globenewswire.com/news-release/2016/11/01/885249/0/en/Virtual-Private-Cloud-Market-is-Growing-at-26-35-CAGR-to-2022.html), this market is anticipated to grow at a CAGR of 26.35% during 2016-2022 globally. This includes block storage platforms, which are important parts of virtual private clouds. The leading open source block storage platforms are [OpenStack Cinder](https://wiki.openstack.org/wiki/Cinder) and [Ceph Block Storage](http://ceph.com/ceph-storage/block-storage/). OpenStack supports both Cinder and Ceph for block Storage. On the container side, [Flocker](https://clusterhq.com/flocker/introduction/) is a leading open-source container data volume orchestrator for Dockerized applications.

## Cloud Orchestration

In cloud computing, we see products and tools in cloud management, cloud governance, cloud brokerage, cloud marketplace, cloud service delivery, cloud application management, cloud orchestration, cloud automation, etc. Though all may sound the same, there is a difference in their fundamentals and features if we look at these products closely. What we increasingly see is that products are starting in one area on the list, but they're trying to satisfy the needs of other areas as well. Some of cloud management products started covering cloud governance, automation, and orchestration. [Cloudify](http://getcloudify.org/),[ Terraform](https://www.terraform.io/), and [Ansible ](https://www.ansible.com/)are some of the leading pure-play, open-source cloud orchestration platforms. Some platform or service providers have their own orchestration mechanisms, such as [AWS CloudFormation](https://aws.amazon.com/cloudformation/), [Azure ARM](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-overview), [OpenStack Heat](https://wiki.openstack.org/wiki/Heat), and [Google Cloud Deployment Manager](https://cloud.google.com/deployment-manager/docs/).

The cloud orchestration market is expected to grow from USD 4.95 billion in 2016 to USD 14.17 billion by 2021, at a CAGR of 23.4% from 2016 to 2021. The rapid growth in the cloud orchestration market is mainly owing to the increase in the need for resource optimization among small and medium enterprises.

Some of the notable acquisitions in this area included Ansible being acquired by Red Hat, Calm.io being acquired by Nutanix, Cliqr being acquired by Cisco, Appformix being acquired by Juniper, and Stackstorm being acquired by Brocade.

## Cloud Service Delivery Platform

Cloud service delivery platforms enable hosting service providers to offer unified cloud service delivery for their cloud business. There are many self-service portals in the market, which provide the capability to provision and manage a platform, but very few provide a packaged solution that takes care of not just managing, but also giving the power to run cloud services business for cloud service providers. [Cloud Portal Business Manager](https://accelerite.com/products/cloudportal-business-manager/) (CPBM) and [Atomia ](https://www.atomia.com/2014/10/30/atomia-canonical-managed-openstack/)are some of the leading products in this space. Citrix Cloud portal manager was acquired by Acclerite in 2016. Atomia partnered with Canonical. [NewScale](http://www.cisco.com/c/en/us/products/cloud-systems-management/data-center-automation/eot_nScale_ssPortal.html) had a similar capability, which was acquired by Cisco in 2011 and they announced the end of sale for their 4.3 version in 2016.

CPBM supports Citrix Cloud platform natively and later started supporting OpenStack. Atomia supports OpenStack Cloud.

CPBM and Atomia have a handful of customers, but the large cloud service providers prefer to build their own service delivery platforms, so there is no great traction for accelerated growth in this space.

## Cloud Consumers

I have had the opportunity to talk to a number of customers who have adopted the cloud or are in the process of adopting it. Here is the summary of the overall perception of the cloud consumers (that I have interacted with).

Cloud service providers and platforms have really matured in the last few years. The cloud ecosystem and value-added services are maturing to meet the demands of consumers. The on-demand nature suits the start-up, ISV, and SMB segments very well.

Security concerns in the cloud are slowly fading in the minds of the consumers, as they now understand that the cloud is in no way less secure than on-premise or hosted -- if both are exposed to the Internet. In fact, the security services in the cloud are on-demand, and there is no Capex involved, which provides them the ability to use the right kind of security tools for their needs.

The cloud is providing the agility businesses need, but cloud service providers are not providing the ability to move workloads across providers. Customers are forced to find their own way to manage vendor lock-in and workload movements across clouds.

While consumers agree that the cloud is the way to go, the roadmap on private cloud vs. public cloud vs. hybrid cloud is often taken based on the cost. Cost is one of the exercises required as part of the cloud roadmap of every organization. Hybrid clouds are often selected, since the private cloud provides cost advantages, though with some added overhead.

Large enterprises adopt more than one cloud to make the best use of a variety of cloud services along with a private cloud. SMBs prefer to go with one CSP, but they still prefer to maintain a private cloud. Start-ups prefer to operate with one public cloud. Though the cloud provides self-service capability, consumers require cloud solution providers or system integrators, who help them with consulting, migration, management, and the automation of their workloads across multiple cloud environments.

The "as-a-service" model is growing exponentially, and there are various categories that keep coming up. The motivation for coming up with this blog is to provide a comprehensive list of various areas in cloud computing that forms the foundation for the growing cloud ecosystem. Thanks for reading through the State of the Cloud 2017! Your feedback and suggestions are most welcome at sabapathy@cloudenablers.com.

MongoDB Atlas is [the best way to run MongoDB on AWS](https://dzone.com/go?i=193125&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Dcloud%26jmp%3Ddzone-ad) -- highly secure by default, highly available, and fully elastic. [Get started free](https://dzone.com/go?i=193125&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Dcloud%26jmp%3Ddzone-ad). Brought to you in partnership with [MongoDB.](https://dzone.com/go?i=193125&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Dcloud%26jmp%3Ddzone-ad)

### Like This Article? Read More From DZone
