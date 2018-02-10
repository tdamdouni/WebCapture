# Who's Responsible for Security in AWS?

_Captured: 2018-02-06 at 17:13 from [dzone.com](https://dzone.com/articles/whos-responsible-for-security-in-aws?edition=359129&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202018-02-06)_

Get the Metrics Collection and Monitoring Essentials [tutorial collection](https://dzone.com/go?i=274448&u=https%3A%2F%2Fwww.digitalocean.com%2Fcommunity%2Ftutorial_series%2Fmetrics-collection-and-monitoring-essentials%3Futm_medium%3Dbumper%26utm_source%3Ddzone%26utm_campaign%3Dbrand%2Bsimplicity%2Bat%2Bscale%26utm_content%3Ddistributed%2Bmicroservices%2Bdeployments). A 4-part tutorial series from [DigitalOcean](https://dzone.com/go?i=274448&u=https%3A%2F%2Fwww.digitalocean.com%2F%3Futm_medium%3Dbumper%26utm_source%3Ddzone%26utm_campaign%3Dbrand%2Bsimplicity%2Bat%2Bscale%26utm_content%3Dmetrics%2Bcollection%2Bmonitoring).

If you haven't read over the [AWS shared responsibility model](https://aws.amazon.com/compliance/shared-responsibility-model/) for security yet, I strongly suggest you do so now. While some people still like to debate about whether or not the responsibility of security should fall with the tenant or the infrastructure (because outsourcing infrastructure means outsourcing security responsibility as well), lines were already drawn in the sand years ago, and then updated and re-drawn. The point is, there's no point in debating something that is ultimately the provider's decision.

Here's the ultimate do and don't: DON'T expect your cloud provider to keep you secure, but DO periodically check in to see whether or not your cloud provider has made updates to their regulations.

Amazon Web Services, easily the largest cloud provider, has made their shared responsibility model crystal clear: As a SaaS provider they place control (and thus security) squarely within the customer's realm. It's part of the reason why CloudPassage Halo has recently been [added to the AWS Marketplace](https://blog.cloudpassage.com/2018/01/24/halo-is-live-on-aws-marketplace/), and why it is a recommended addition to your Amazon workloads.

The image below demonstrates exactly what AWS provides themselves, and what rests on an organization's (your) shoulders:

![](https://x9a3mnc941tz8gz3x1e0sda1-wpengine.netdna-ssl.com/wp-content/uploads/sites/2/2018/01/Amazon-shared-responsibility-model-.png)

> _As you can see, Amazon protects their own cloud, not your network security, data encryption, access control, or inventory._

At the end of the day "responsibility" is typically defined within the provider's Service Level Agreement (SLA). With any provider, (not just Amazon), look for clauses such as "this SLA does not apply to actions or inactions of third parties," which is effectively a get out of jail free card for the provider if your data is compromised by a non-employee. So while responsibility for applying security may rest under the provider's control, your recourse for security failures may be severely limited.

So what's the take away? While you should always leverage security controls as much as possible, it's up to you to find a security solution that can be tailored to the needs of your workloads.

If we could offer any advice it would be to find something automated, that scales at the speed of your DevOps team, and that's provider-agnostic. Therefore if your organization ever decides to test out various public cloud models, or expand into [containerization practices](https://www.cloudpassage.com/products/container-secure/), you aren't exposing any workloads to needless threats.

Interested in CloudPassage Halo? Check out our listing on [AWS Marketplace](https://aws.amazon.com/marketplace/pp/B008KTGRKK/?ref_ptnr_blg)!

Get a [free in-depth tutorial:](https://dzone.com/go?i=274447&u=https%3A%2F%2Fwww.digitalocean.com%2Fcommunity%2Ftutorials%2Fhow-to-automate-backups-digitalocean-spaces%3Futm_medium%3Dbumper%26utm_source%3Ddzone%26utm_campaign%3Dbrand%2Bsimplicity%2Bat%2Bscale%26utm_content%3Dbackups%2Bdigitalocean%2Bspaces%2Bdzonecloud) How to Automate Backups with [DigitalOcean Spaces](https://dzone.com/go?i=274447&u=https%3A%2F%2Fwww.digitalocean.com%2Fproducts%2Fspaces%2F%3Futm_medium%3Dbumper%26utm_source%3Ddzone%26utm_campaign%3Dbrand%2Bsimplicity%2Bat%2Bscale%26utm_content%3Dbackups%2Bdigitalocean%2Bspaces%2Bdzonecloud).
