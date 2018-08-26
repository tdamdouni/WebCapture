# Choosing a Framework for IoT Infrastructure

_Captured: 2018-07-17 at 19:12 from [dzone.com](https://dzone.com/articles/choosing-a-framework-for-iot-infrastructure?edition=385243&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202018-07-17)_

One of the most rewarding aspects of developing innovative IoT systems at scale is the opportunity to define the process and make sense of a rapidly changing marketplace where no single methodology, platform, or approach dominates yet.

But the volatility of the IoT landscape also means extra work in defining the road ahead for client projects. As new protocols and resources gain prominence, the client might incline towards the solutions that are the most mature, most familiar, or perhaps most advertised - even where these have been superseded by superior open source or third-party products; or else might commit the client to one major provider's services at potential cost to the long-term integrity of their project.

Some of the early tough decisions are comfortingly familiar: The cheaper solution won't scale well, and the capacities of the more expensive and flexible solution may never be needed. Therefore, the client needs to distinguish from the outset whether they're set on fulfilling a specific production remit or looking to develop true scalability. The last thing anyone wants is a ground-up rebuild eighteen months down the line because demand is straining the system's outer margins of operability.

**The IoT system-development market currently forks into three obvious routes:** off-the-shelf platforms (such as [AWS IoT Core](https://aws.amazon.com/iot-core/features/), [Azure IoT Suite](https://azure.microsoft.com/en-us/suites/iot-suite/) and [Google Cloud IoT Core](https://cloud.google.com/iot-core/)), which trade off vendor lock-in and higher-end volume pricing against cost-effective scalability and shorter lead times; reasonably well-established MQTT configurations over the Linux stack (such as [Eclipse Mosquitto](https://mosquitto.org/)); and the more exotic emerging protocols and products (such as Nabto's [P2P protocol](https://www.nabto.com/)) that are developing enough uptake, interest, and community investment to stake a claim for strong market presence in the future.

If the project is looking for massive scalability and portability via platform-agnostic code, initial development investment and lead times will be considerable, but the client gets to keep the later value of that innovative effort. Since the product will only need relatively generic cloud provisioning, it's also futureproofed when it comes to the top IoT cloud players.

Even that level of investment can't purchase certainty in an environment where IoT messaging protocols such as MQTT, HTTP, CoAP, and AMQP are currently [contending](http://ieeexplore.ieee.org/document/8088251/) for dominance. Therefore, your own project experience and industry practices will likely be deciding factors here.

**Security is another logistical consideration when considering mainstream IoT cloud sourcing. **The advantages of going with the major providers can be off-set by the extra (and ongoing) effort of securing your system against the attackers that routinely probe their channels for vulnerabilities. Proprietary code may be harder to develop and maintain, but it doesn't usually carry this particular burden.

Since the IoT ecostructure is still far from consolidation, even the well-resourced client will need clear and current advice at the ideation stage in order to define their ambitions realistically. So for the framework developer, 'vanguard' remains the default position, requiring an uncommon mix of experience, research and market instinct.
