# How to Save on Planning Cloud Deployments

_Captured: 2017-05-31 at 19:17 from [dzone.com](https://dzone.com/articles/how-to-save-on-planning-cloud-deployments?oid=twitter&utm_content=buffere47f3&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Learn how our [document data model](https://dzone.com/go?i=214229&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Ddb%26jmp%3Ddzone-ad) can map directly to how you program your app, and native database features like secondary indexes, geospatial and text search give you full access to your data. Brought to you in partnership with [MongoDB](https://dzone.com/go?i=214229&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Ddb%26jmp%3Ddzone-ad).

Since the creation and launch of the [Red Hat Cloud Suite](https://access.redhat.com/products/red-hat-cloud-suite/) last year, additional tooling was provided to help make good use of all the technologies included in this stack.

![Image title](https://2.bp.blogspot.com/-ABZd3HJP0v4/WR2G9hVODPI/AAAAAAAAp98/WWvIvGE2jwg-zf2RSEwV69yywqg6SOLhgCLcB/s1600/cdp-1.png)

> _Figure 1: Cloud Deployment Planner virtual stack designer._

It's the [cloud stack you can't ignore](http://www.schabell.org/2016/02/appdev-cloud-stack-cant-ignore-stack-anymore.html) when looking to facilitate both your infrastructure needs and your application development needs.

One key aspect is [planning and designing a cloud stack](http://rhelblog.redhat.com/2016/05/18/cloud-solutions-made-simple/) before diving in to set up a digital architecture using open technologies. With that in mind, Red Hat [published a free and useful tool](http://www.schabell.org/2016/08/redhat-cloud-suite-cloud-deployment-planner-video.html) to help with planning, designing and deploying your cloud infrastructure with Red Hat Cloud Suite.

This week, a new version of this planning tool was released, called [Cloud Deployment Planner](https://access.redhat.com/cloud-deployment-planner/#/), still freely available online. It includes a new feature to help visualize the planning of your components in your cloud stack, called Virtual Stack Designer.

Let's look at how this tool saves time and effort up front when planning a cloud deployment.

## Planning Cloud Deployments

When [accessing the Cloud Deployment Planner](https://access.redhat.com/cloud-deployment-planner/#/), the first thing presented is the Virtual Stack Designer. It is an architectural view of the available cloud infrastructure components. Clicking on the components that are desired in a cloud deployment causes them to turn a blue color, as shown in Figure 2.

![Image title](https://3.bp.blogspot.com/-Q0TrwusBeN0/WR2oNXEa0qI/AAAAAAAAp-M/gPFtjYgqzTsDBE-8AesCyc3XJuS01lIZwCLcB/s1600/cdp-2.png)

> _Figure 2: Selecting open technology components for a cloud deployment._

Submitting the choices made by clicking on the _Build_ button at the bottom automatically generates a view of the components selected with an array of version numbers.

These versions allow alignment with current deployments and future thinking selections when exploring upgrade scenarios.

Figure 3 shows how version numbers are selected, become blue, and generate a list of _Feature & Service Compatibility_ tables. Each one provides an overview of what works (green with a check mark), what does not (red with an _x_) and what has issues (red with informational _i_).

![Image title](https://3.bp.blogspot.com/-vgG3mo3RAdw/WR2tuHHOZaI/AAAAAAAAp-c/mS8Kg6wOiGshMn2oYuCTmBqoHyU3iXCMwCLcB/s1600/cdp-3.png)

> _Figure 3: Choose version numbers for selected components._

By clicking on the informational _i,_ a pop-up displays any issue details for further exploration.

The compatibility information table is shown in Figure 4 based on previous choices and is the results of an automated process integrated into how these technologies are productized.

![Image title](https://1.bp.blogspot.com/-gTb6enZFRJ0/WR2uzwWw5kI/AAAAAAAAp-k/ptA5-3-DU6Uvooyy5_jvTznfpsTxgPNtwCLcB/s1600/cdp-4.png)

> _Figure 4: Component compatibility based on scenarios for chosen items._

This part of the tool can save hours if not days of pouring through product documentation, pursuing online experiences, and trialing software in various proof of concept scenarios to verify compatibility.

Finally, as icing on the cake, there is a second tab available reporting on _Lifecycle Compatibility_. Figure 5 shares the availability and lifespan of the components selected. This provides an overview of how long a component and product is supported including overlaps to ensure deployments are supported throughout the projected usage plans.

![Image title](https://2.bp.blogspot.com/-LHYZFFAiDgM/WR8DxfyeyMI/AAAAAAAAp-4/XiSVdoJIMtYcIEhCtszGFAmvqM4h4p8BQCLcB/s1600/cdp-6.png)

_Figure 5: Lifecycle Compatibility ensures deployments are done with supported components._

This is a really nice feature to save time with planning and rolling out new cloud infrastructure or determining upgrade planning for existing cloud architectures. Time will be saved, which is cost savings in any organization, so that efforts can be spent on delivering on Cloud deployments instead of stumbling on any of the issues covered previously.

If you are looking to experience some of the possibilities around deploying containerized applications on cloud deployments, [visit the Red Hat Demo Central](https://github.com/redhatdemocentral).

Time to start planning your cloud deployments using the free online tooling to ensure both time and efforts are saved up front. No more stumbling through your cloud deployments!

Discover when your data grows or your application performance demands increase, MongoDB Atlas allows you to scale out your deployment with an [automated sharding process](https://dzone.com/go?i=214230&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Ddb%26jmp%3Ddzone-ad) that ensures zero application downtime. Brought to you in partnership with [MongoDB](https://dzone.com/go?i=214230&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-2%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3Ddb%26jmp%3Ddzone-ad).
