# How to Select the Right IoT Hardware: From Prototype to Production

_Captured: 2018-07-31 at 22:38 from [dzone.com](https://dzone.com/articles/how-to-select-the-right-iot-hardware-from-prototyp?edition=385308&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202018-07-31)_

IoT development boards and modules are at the heart of every connected product. As IoT has developed, the variety and technical capabilities of these boards have only become more complex. When building an IoT product, you may start off with an off-the-shelf prototyping kit, but as you progress through the hardware development and design process, you'll need to invest in hardware boards that are designed for scaling and manufacturing.

But, what is the difference between prototyping and production hardware? This article aims to clean up some of the noise and make it easier for you to choose the right hardware solution for your IoT product.

## What Is the Difference Between Prototyping and Production Hardware?

In general, you can easily differentiate between prototype and production hardware based on these features:

Prototyping hardware is optimized for:

  * **Flexibility** -- Usually breadboardable and has an open SIM card slot
  * **Affordability** -- Low cost
  * **Modularity** -- Compatibility with other hardware ecosystems
  * **Ease of use** -- Can be set up in minutes and comes with tools
  * **Beginner audiences** -- Content and examples optimized for beginners

Mass production hardware is optimized for:

  * **Reliability** -- Has SMT(surface-mount-technology) components, can withstand extreme temperatures, and comes with hardware warranties
  * **Manufacturability** -- Pick and place machine-ready
  * **High volumes** -- Can be purchased in bulk via a reliable distribution partner
  * **Ease of integration** -- Should have complete product certifications
  * **Advanced audiences** -- Comprehensive datasheets and application notes

### Prototype and Production Hardware Examples

For instance, [Particle](https://www.particle.io/) produces three basic kinds of hardware -- Development Kits (DKs), Evaluation Kits (EVKs), and Mass Production Modules (MPMs). These are defined below:

![](https://cdn-images-1.medium.com/max/800/0*ZAtehe3M2aiVPVrL.jpg)

### Development Kits (DKs)

Development kits are breadboard friendly and optimized for expandability, modularity, and ease-of-use. As a result, they can be used for scaling, depending on the use case and application, but maybe best used as short-term PoCs in friendly environments.

  1. **Intended use **-- Useful for iterating/prototyping hardware and firmware systems quickly. It provides a quick start solution and gets an IoT project rolling.
  2. **Features** -- USB connectivity, an ecosystem of hardware accessories, breadboard-able headers, RGB status LED, onboard antenna, affordable costs
  3. **Audience **-- Hobbyist developers, engineers very new to hardware
![](https://cdn-images-1.medium.com/max/800/0*wBe0J5CSXeAIdmce.jpg)

### Mass Production Modules (MPMs)

Mass production modules are optimized for deployment in a mass production product, not for development. These are the real deal, intended for deployment for 5-10 years in hostile environments and small spaces. These products have little utility until they are soldered into your end product.

  1. **Intended use** -- Deployment in a mass production product
  2. **Features** -- Certifications, hardware warranty, and support, environmental robustness, optimized for size and manufacturability
  3. **Audience** -- Companies manufacturing products at scale
![](https://cdn-images-1.medium.com/max/800/0*rZEP150fIwkK39df.png)

### MPM Evaluation Kits (EVK's)

MPM Evaluation Kits are expansion boards for mass production modules and allow you to develop, iterate, and debug your IoT solution quickly and easily. In other words, they provide a friendlier development experience for mass production hardware solutions. They have an MPM soldered to them and, in many ways, can act as a good reference design.

  1. **Intended use** -- Companies designing a product for deployment at scale and companies iterating from DKs to MPMs. Useful for iterating and refining production firmware in the context of production hardware (MPMs).
  2. **Features** -- Largest number of GPIO and peripherals, large/comfortable debugging-optimized board layout, application notes and professional documentation
  3. **Audience **-- Professional engineers who are comfortable designing custom circuit boards, companies with intentions to deploy at scale

## Other Factors to Consider When Choosing IoT Hardware

When you're sourcing hardware for prototyping or production, you should also look at the platform, tools, and support that comes with it:

### 1\. A Consistent Platform, Infrastructure, Firmware, and Development Tools

You'll want to continue using the same cloud infrastructure and development tools as you scale. Switching between different hardware designs is enough of a task -- you don't want to carry this over to the software you are using. The same firmware application, when compiled on your DKs and MPMs, should perform exactly the same way. There should never be a need to tweak or modify the firmware application to get it running on an MPM.

### 2\. Domain Experts and Support

When selecting a hardware-solution, it's also important to consider the community surrounding it. Hardware solutions with limited adoption will have fewer resources available to aid you in development. For example, Particle's development kits have a large developer community surrounding it, which makes it easier to find information and support when needed.

### 3\. Ease of Deployment

You want to be able to get your product up and running as quickly as possible. When sourcing hardware, consider it's accessibility, availability, and the documentation that comes with it. Having these resources at the ready will make it easy for you to get your questions answered immediately.

## The Bottom Line

When sourcing prototyping and production hardware, you want to examine its accessibility, affordability, integrations, and manufacturing features. Whether you're prototyping or building a scalable IoT product, you want to choose hardware that offers a consistent platform environment and ease-of-deployment.
