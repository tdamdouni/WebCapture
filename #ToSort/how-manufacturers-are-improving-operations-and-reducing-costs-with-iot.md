# How Manufacturers are Improving Operations and Reducing Costs With IoT

_Captured: 2018-07-03 at 23:15 from [dzone.com](https://dzone.com/articles/service-thread)_

On the manufacturing floor, even the smallest moving parts can cause intermittent disruption and performance degradation if they break. These unplanned events can not only cause catastrophic financial loss for manufacturers, but the parties they serve. What's worse, the cause of these disruptions are hard to locate without allocating a significant amount of resources on machine inspections.

However, the Internet of Things (IoT) is giving manufacturers the power to monitor even the smallest moving aspects of their production. Small, inexpensive computing hardware (like IoT prototyping kits and development boards) can monitor and transmit data instantly on the state of any machine wirelessly. For companies looking to improve efficiencies, reduce costs, or fully-optimize their production, IoT is a surefire way to go.

![spindle-thread](https://blog.particle.io/uploads/spindle-thread.png)

How manufacturers can implement embedded hardware into their operations isn't always clear though. For this article, we're going to clear that up by explaining how [Service Thread](http://www.servicethread.com/), an American manufacturer of commercial thread and yarn, used IoT hardware to monitor and maintain 3,000 spindles across 115,000ft of floor space.

![manufacturer-inspection](https://blog.particle.io/uploads/manufacturer-inspection.png)

## Service Thread Aims to Saves Costs With IoT-Driven Data

Service Thread's main goal was to gain better insights on the effectiveness of their spindle machines. In the past, they relied on in-person inspections. However, there are a couple of issues they had with this system:

  * **Inspectors spent 10 hours per week,** or 500 hours per year, performing these analyses.
  * **The possibility for human error is significant;** any inaccuracies could impact overall shop performance.
  * **The scope of their data was limited**, and their final estimates were not necessarily accurate.

While Service Thread's machines already had some capabilities to monitor and track spindle performance with onboard computers, they could not record the status of each individual spindle in a centralized location. They wanted an IoT device that could track all this data easily.

## IoT Device Requirements

For this IoT device, they had some goals they set out to accomplish:

  * **Build a simple device** that can provide and report data through the network to a central location.
  * **Find affordable hardware components** so they could create multiple devices that could go in different machines.
  * **Create an end-to-end device** that could connect to the cloud and communicate with other devices and systems.
  * **Be accessible and easy to use** for those who need to access the device or read the data that it reports.
![Image title](https://dzone.com/storage/temp/9499347-photon-image.png)

> _A photon-powered retrofit_

## The Solution

Dan Thyer, the CEO of Logical Advantage, and his team used a [Photon](https://www.particle.io/products/hardware/photon-wifi/) (a Wi-Fi connected microcontroller) so the device could connect to the internet and communicate with other human-centered interfaces. With the Photon, their spindle-monitoring device can communicate the state of the spindles (like if they're moving or not) to the cloud. The Photon is also capable of sending and receiving [OTA firmware updates](https://blog.particle.io/2017/12/18/over-the-air-firmware-the-critical-driver-of-iot-success-859927/), which gives them the ability to send code updates to the device even after it's deployed. This is critical, because they can easily update and maintain their devices, all while remaining cost effective.

## The Result

Ever since Service Thread implemented IoT hardware and cloud services into their daily manufacturing services, they have been reaping the benefits:

  * **Enhanced Data management** \- Service Thread is now collecting data that provides them more accurate information on the performance of their machines. This also helps them make smarter decisions with their labor, sales, and supply-chain management.
  * **Improved Fleet Visibility** -- Service Thread can now see if spindles are having trouble or need maintenance immediately with real time information feeds.
  * **Reduced Operating Costs** -- Service Thread currently estimates that their IoT solution will reduce their per-spindle operating costs by at least 50 percent.
  * **Increased Savings** -- The company anticipates savings around $117,000 from reduced maintenance overtime and overhead costs.

With IoT, Service Thread was able to improve their operations and gain insights on the smallest moving parts of their machines. Current manufacturers must decide if their current systems give them enough insight into their daily operations, or if investing in IoT solutions is a more efficient and effective way of monitoring their daily operations.
