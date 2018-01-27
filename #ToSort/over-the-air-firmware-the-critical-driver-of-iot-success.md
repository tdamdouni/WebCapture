# Over-The-Air Firmware: The Critical Driver of IoT Success

_Captured: 2017-12-17 at 12:47 from [hackernoon.com](https://hackernoon.com/over-the-air-firmware-the-critical-driver-of-iot-success-f4604bd0b881)_

## Learn the basics of OTA firmware updates and how they are transforming the future of IoT products.

![](https://cdn-images-1.medium.com/freeze/max/60/0*zYED3kHUEr3JZY1r.jpg?q=20)![](https://cdn-images-1.medium.com/max/1600/0*zYED3kHUEr3JZY1r.jpg)

In the early days of IoT, updating remote devices often caused intermittent disruption and performance degradation. As IoT platforms have matured, they have embraced a novel way to remotely and reliably update connected devices with little to no disruption: **over-the-air (OTA) firmware updates.**

Over-the-air firmware updates refers to the practice of remotely updating the code on an embedded device. The embedded hardware must be built with OTA functionality for this mechanism to work.

Here is a visualization of how OTA firmware is delivered to remote devices using a[ device management system](https://console.particle.io/login):

![](https://cdn-images-1.medium.com/freeze/max/60/0*eW0oxsx4YqZ86nD4.?q=20)![](https://cdn-images-1.medium.com/max/1600/0*eW0oxsx4YqZ86nD4.)

### Why OTA Firmware?

Prior to OTA updates, you had to go out and retrieve the device, take it apart, connect it to your computer, reprogram it, put the device back together, and then take the device back.

However, this process is overly burdensome and unscalable for companies who have devices out on the field. Although, it hasn't stopped some from trying . . .

  * In 2015, Chrysler was criticized for patching a software vulnerability via mailed USB drives. Chrysler's method put many consumers at risk because the USB drives could be intercepted, modified, and resent.

On the other hand,

  * In 2016, Tesla drivers woke up to find substantial new features to their car after the company sent out an OTA firmware update. Consumers could now self-park their cars without having to manually update their vehicles.

You tell me which is the better headline.

### OTA Firmware Benefits

  1. **Bugs and product behavior** can be continuously improved even after the device is in the hands of your consumers.
  2. **Companies can test new features** by sending updates to one or multiple devices.
  3. **Companies can save costs** by managing the firmware across their fleet of devices from a seamless, unified interface.
  4. **Developers can deploy frequently and reliably, **knowing that products will stay functional as updates are released.
  5. **OTA firmware augments scalability** by adding new features and infrastructure to products after they are released.

### OTA Firmware & Device Management

To send out OTA firmware updates, you need a device management system that can interface with microprocessors and local software on IoT devices. This is complicated to build because few companies have an IoT software and hardware ecosystem that can process OTA firmware updates and manage remote devices.

> "The updating of software/firmware over-the-air (SOTA/FOTA) is being seen as a critical methodology to manage software updates with the latest revisions for the entire lifecycle of a system." -- Stephane Strahm, Smart 2.0

### Implementing OTA firmware updates

There are two options companies can take: you can build your own OTA firmware system or buy a managed OTA firmware system. For the build route, it is imperative that you research, plan, and consult domain experts to help you add OTA functionality to your hardware and software. Implementing the proper industry encryptions, finding the compatible hardware/software, and finding domain experts who can actually help you will be some of your biggest concerns.

However, due to the complexities of transmitting of the data and security concerns, you could harness a managed platform solution. For example, one such platform is by Particle.

### Getting Started with Particle and OTA firmware

[Particle ](https://www.particle.io/)is a full stack IoT platform that offers the hardware and software tools to connect everyday electronics to the internet. Part of this platform, Particle cloud and console, also allows consumers to control fleets of devices and products with wireless firmware updates. Here are some of the benefits of using Particle for OTA firmware updates:

  1. **Future-proof your products **knowing that Particle is taking care of the infrastructure, hardware, and software.
  2. **OTA firmware updates are sent in chunks** so your device won't brick. If your device loses connection during the update process, it'll just resume when the connection comes back online.
  3. **Firmware updates are delivered immediately **because the update is just sent to the application layer and not the system layer. System firmware is maintained by the Particle team so you can focus on the use case.
  4. **Easily scale from sending OTA** firmware updates from 1 to 1,000 devices without hardware scalability or software issues.
  5. **Test application updates **by sending firmware updates to one or a controlled group of devices.
  6. **Deliver updates securely** knowing all communication channels between the device and Particle cloud are fully encrypted and authorized.
  7. **Document each release** throughly via Particle console to provide your team a comprehensive picture of what has changed in each version.
  8. **Devices can be set into safe mode** so it doesn't execute any application code, which can be useful if new application code contains bugs that stop the device from connecting to the cloud.

### All and all

OTA firmware is the critical driver for IoT success because it is powering the reliability and scalability of connected devices. Companies must decide whether building their own OTA firmware system is worth the time and potential costs, or if purchasing a platform that has OTA firmware functionality is a more efficient and effective way to update remote wireless devices.
