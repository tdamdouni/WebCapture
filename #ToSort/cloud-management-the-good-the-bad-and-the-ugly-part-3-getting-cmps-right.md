# Cloud Management: The Good, The Bad, and The Ugly (Part 3): Getting CMPs Right!

_Captured: 2018-08-22 at 09:42 from [dzone.com](https://dzone.com/articles/cloud-management-the-good-the-bad-and-the-ugly-par-2?edition=385399&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202018-08-21)_

[Site24x7](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

_See [Part 1 ](https://platform9.com/blog/cloud-management-the-good-the-bad-and-the-ugly-part-1/)and [Part 2](https://platform9.com/blog/cloud-management-the-good-the-bad-and-the-ugly-part-2-5-key-capabilities-for-cmps/) of this series._

![](https://platform9.com/wp-content/uploads/2018/07/the-good-bad-ugly-of-cloud-management-CMP.jpg)

Cloud Management is one of the key areas that CTOs and CIOs need to make investments in in the coming years. In the previous 2 posts in this series, we discussed the [challenges with existing cloud management platforms](https://platform9.com/blog/cloud-management-the-good-the-bad-and-the-ugly-part-1/) and the [5 key capabilities of CMPs](https://platform9.com/blog/cloud-management-the-good-the-bad-and-the-ugly-part-2-5-key-capabilities-for-cmps/). In this last part, I'd like to discuss the four key principles around which Platform9 has designed our industry-leading offering in this space, and why we provide an alternative to traditional CMPs that have, unfortunately, given hybrid clouds a bad name.

## Design Principle #1: Cloud Management Should Be Simple and Elegant

A clear first principle we take to heart is simplification and accelerating time-to-value for complex hybrid cloud management and operations tasks. This can be broken down into four different areas:

  1. We understand that Cloud should not turn into another "ERP" project for the enterprise. This approach is what makes digital transformation initiatives [fail so often](https://platform9.com/blog/what-we-can-learn-from-ge-and-why-digital-transformations-fail/). At Platform9, we aim to make cloud management - even in the most complex, hybrid environments - simple. As the [Ovum Decision Matrix for Multicloud and Hybrid Cloud Report](https://ovum.informa.com/resources/product-content/int003-000062) points out, the cloud is a journey and most enterprises starting out have a lot of virtualization in place, they are slowly migrating to the public cloud while implementing open source virtualization KVM on OpenStack. Whatever your infrastructure choices are, the CMP should be easy to set up (in a day) and to help your developers and IT Ops deploy applications into the underlying cloud with a push of a button, all within just a few hours from initial installation.
  2. We shy away from unnecessary complexity - it adds no value to our users, only lengthens the implementation and learning curve, slows adoption and increases your investment before you see results. Many CMPs bundle in automation, billing, etc. There are already a variety of proven automation tools and cost optimizations tools available that customers have invested in. By simplifying the core essential components of cloud management, we move enterprises from a model of paying millions of dollars to standing up and maintaining a cloud with support for Day 2 operations. This means customers see immediate and long-term business value faster, and do not need to rip and replace additional services that are on the periphery of the core competency they needed to support.
  3. IT teams are being nudged in a direction to make DevOps practices possible in the organization in order to enable digital transformation. To that end, CMP platforms should support both legacy applications and processes while enabling organizations to easily experiment and adopt new technologies, and to take advantage of modern architectures and delivery patterns (in Gartner's terms, supporting [Bimodal IT](https://www.gartner.com/it-glossary/bimodal/).) This is critical so that (legacy) CMPs don't end up getting organizations stuck in "middle-ages" IT, but allow them a path to DevOps-ify and modernizing their applications and their infrastructure. These platforms need to not just support the existing applications and stacks, but also enable organizations to start decomposing monolithic applications to microservices, and taking advantage of containers, serverless applications, and more.
  4. No organization is perfectly cloud-optimized across all internal IT, and not all applications are cloud-aware or cloud-enabled. While Greenfield applications will use Kubernetes, serverless, and containers, a portion of your business will still run on VMs or even bare metal for a while. Legacy apps may require refactoring but not re-platforming. The CMP should support a unified experience across all of these types of applications: VMs, containers, serverless, and whatever new pattern or technology comes next.

## Design Principle #2: Cloud Management Should Be Delivered as SaaS

The most difficult thing about running a CMP is the setup, installation, configuration, and Day 2 operations. We have seen enterprises take months (sometimes years!) of around-the-clock professional services and consulting in order to get a CMP running across even a relatively small fleet of data centers and cloud providers.

Public clouds have already set the bar for ease of use:

  * Developers are used to using the public cloud, where it takes 5-10 mins to get started. Anything different is unacceptable and obsolete.
  * Cloud management should "just work"- with customers taking 5 - 30 mins to get up and running, not months and years.
  * The CMP should be fully integrated (batteries included), and interoperable with any environment or technology stack, as well as easily extensible to additional services, integrations, point-tools and APIs.
  * The CMP and the infrastructure should be installed, managed, and monitored using a SaaS-based delivery model. No more manual work, heavy lifting on the Operations side, or taxing management overhead.

Finally, from a business model standpoint, vendors should not have conflicts of interest such as selling large-scale professional services to enable their platform. If you need advanced expertise and a year-long process to implement something, then it's not SaaS, and it's sure as hell not simple.

## Design Principle #3: Build on Open Source Frameworks

Today, Open Source Software (OSS) frameworks provide the core capabilities that matter for any modern development, IT operations or DevOps processes. A wide range of developer communities contribute to various OSS projects, constantly enhancing the tools we use with additional functionality as well as with new governance capabilities, creating a constant stream of innovation allowing us - as an industry - to take our software delivery to the next level.

Building on OSS as a fundamental principle ensures your solution can:

  1. **Incorporate the latest and greatest innovation** in the space, as it continues to evolve, and benefit from the vibrant open source community;
  2. **Be future-proof** for whatever new technology comes next;
  3. **Allow you to avoid lock-in**, and be portable and interoperable across any environment or provider;
  4. **Be easily extensible** and is flexible to support new integrations, services, and specific use cases;
  5. **Benefit from the open source economics** and savings versys high licensing fees of proprietary solutions.

In accordance with our two guiding design principles above, Platform9 is built on the open source cloud standards - [Kubernetes](https://platform9.com/managed-kubernetes/) and [OpenStack](https://platform9.com/managed-openstack/) - delivered as a SaaS-managed service. This critical coupling lets you avoid lock-in and benefit from OSS cost savings, without the burden and management overhead to keep these running on your diverse infrastructure.

In addition, to make sure we keep things simple for IT Ops, we included out-of-the-box plugins to easily integrate with all the public cloud vendors and on-prem technologies - such as AWS, Google Cloud, Azure, KVM, VMware, and more. This lets you hit the ground running with no lengthy custom developments or professional services to plug into your various datacenters or multi-cloud environments.

Lastly, we developed "just enough" governance and compliance capabilities where these were lacking in the core OSS technologies, to allow organizations to have better auditability and control over enterprise workloads.

## Design Principle #4: Unified Experience

Whatever the underlying cloud or infrastructure provider are, CMPs should provide a unified experience across four areas:

  1. **A single view of all types of infrastructure:** servers, VMs, containers, storage, and network - across all VM providers and private/public clouds, all the cloud regions and the tenants across these regions.
  2. A single way for Site Reliability Engineers (SREs) to administer hybrid infrastructure across critical areas such as **security & identity management.**
  3. **Unified and open API** for both developers and operations to perform lifecycle management and easy integrations with point tools or management processes.
  4. **Continuous monitoring** across all of the different cloud regions and environments.
![](https://platform9.com/wp-content/uploads/2018/07/Screen-Shot-2018-07-31-at-1.03.38-PM-e1533067602580.png)

## Getting Cloud Management Right

![](https://platform9.com/wp-content/uploads/2018/07/nirvana-in-cloud-management-at-scale-across-VMs-kubernetes-serverless-on-any-infrastructure.jpg)

As the industry's [first and only](https://solutionsreview.com/cloud-platforms/crn-emerging-vendors-hybrid-cloud/) SaaS-managed cloud management platform, we at Platform9 recognize the challenges that IT Ops face managing today's hybrid/multi-cloud environments, and offer a unique way out of the failures and lost investments with traditional CMPs.

One of the foundational beliefs we have is that Cloud Management has become unnecessarily complicated as a result of legacy VM management technologies being extended or retrofitted with support for public clouds and containers. This is another instance of unfortunate architectural choices and technological debt in the tech industry, that ends up being a hurdle for developers and IT Ops/SREs alike, causing many cloud transformation or digital transformation initiative to fail. A badly conceived CMP can significantly drain enterprise resources, and with so many failed CMPs implementations, no wonder traditional cloud management solutions have such a bad rep.

[Site24x7](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)
