# Building DevOps Workflows for an IoT App

_Captured: 2018-08-28 at 17:30 from [dzone.com](https://dzone.com/articles/building-devops-workflows-for-an-iot-app?edition=385426&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202018-08-28)_

Many IoT software developers are constrained by imperfect IoT tools and platforms in terms of delivering their apps to end users. But, can building DevOps workflows help solve this issue?

IoT is establishing an ever-growing presence in our lives. Smartwatches, apps for [Alexa smart speakers](https://itsvit.com/blog/alexa-apps-dive-move-along-wait-now/) in our homes, [edge computing IoT nodes](https://itsvit.com/blog/cutting-edge-trends-2018-cloud-big-data-ai-ml-iot/) for Industry 4.0 factories, and the energy industry, including self-driving cars from [Tesla](https://www.tesla.com/autopilot) and autonomous driving trucks from [Mercedes](https://www.mercedes-benz.com/en/mercedes-benz/innovation/the-long-haul-truck-of-the-future/), and even [Amazon's self-service grocery store](https://www.theguardian.com/business/2018/jan/21/amazons-first-automated-store-opens-to-public-on-monday) without cashiers -- all of these are the reality of our advanced world.

The IoT ecosystem grows daily, but it is still hampered by obstacles and challenges. The most obvious and unavoidable of them are the dependency on the hardware limitations and the immaturity of the development space as a whole. This means every IoT developer has to deal with the limitations of the chosen SDK and produce apps with somewhat limited capabilities. The hardest point is the software delivery to end users and the process of on-site updates, as these can go only according to one or two scenarios (updating the devices that are currently online or delayed updates for offline devices).

The DevOps approach to software delivery is centered on automating multiple infrastructure management operations to speed up the software development lifecycle. The [DevOps culture](https://itsvit.com/blog/devops-culture-huge-step-mankind/) of collaboration between Devs and Ops is aimed at maximizing the value delivered to the customers and continuous integration of their feedback to facilitate the best usage of the product or service.

Despite being mostly centered on web development and infrastructure support of existing enterprise workloads, DevOps workflows can be utilized to automate literally any software-related process, including the process of IoT app development, deployment, and management.

![DevOps-for-IOT_info.jpg](https://dzone.com/storage/temp/9995913-devops-for-iot-info.jpg)

## Benefits of Using DevOps Practices in IoT Processes

The process of IoT app development is actually quite similar to any other software development process, with several understandable alterations. IoT developers need the same infrastructure setup as everyone else:

  * development environments and code repositories with version control;

  * build and automated unit testing environments for QA;

  * reliable means of delivering the ready product to end users and roll back if necessary;

  * the tools for getting user machine feedback on the app (telemetry, etc.)

That being said, there are various IoT development products and services from [AWS or Azure](https://itsvit.com/blog/aws-vs-ms-azure-cloud-provider-choose/), and GCP or IBM. Depending on the target audience (and the devices deployed by the end users), the IoT development might utilize a vast array of platforms, SDK's, and services. However, despite the varying starting points, the ways to the release are essentially the same, so standard [DevOps tools](https://itsvit.com/blog/must-have-devops-tools-make-things-right-get-go/), like Kubernetes, Terraform, Jenkins, Ansible, etc., can be used on the cloud side of the process. On the customer's side, there will be the devices like Raspberry Pi 2 or 3, which should interact with the cloud over the Wi-Fi connectivity using certain APIs.

## Challenges of Using DevOps Approach to Delivering IoT Software

The main issue here is the fact that the end-user configurations will vary immensely, and the technology stack used for the app delivery is actually quite limited. This means that only the most standardized configurations will be 100 percent covered, while some edge variants might be not accounted for during the testing, which will cause bugs and malfunctions. For example, the end user edge computing node uses the hardware that was not included in the possible configuration during the product testing stage, which will result in service downtime.

The next major issue is connectivity, which means that updates might crash if the connectivity disappears. Because of that, the Continuous Integration/Continuous Delivery (CI/CD) pipelines for IoT app delivery must include the health check scripts, roll back to stable versions, and restart the updates.

However, these challenges were here since the beginning of the IoT era and are mostly addressed by now or will be addressed soon. Major cloud service providers increase their ecosystems to enable the IoT developers to use more and more various SDKs and APIs and drive even more value for their customers.

## Final Thoughts on DevOps and IoT

As the main emphasis of DevOps workflows is around increasing the efficiency of cloud infrastructure operations, it aligns quite well with the needs of IoT software development. A decent infrastructure support team can handle building the IoT CI/CD pipelines using the same tools as for web-based apps. The main challenge is writing the tests for the biggest possible numbers of hardware configurations and ensuring fluent feedback acquisition from target devices. Once the data goes from the IoT node to the cloud -- it is safely handled according to DevOps practices. Thus, using DevOps workflows is quite feasible for the IoT apps lifecycle.

Did we miss any crucial points? Please share your thoughts in the comments below!

Topics:

ci/cd ,workflow automation ,devops ,iot ,automation ,end user ,connectivity
