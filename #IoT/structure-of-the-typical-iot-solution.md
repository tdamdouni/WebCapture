# Structure of the Typical IoT Solution

_Captured: 2017-03-30 at 20:17 from [dzone.com](https://dzone.com/articles/structure-of-the-typical-iot-solution?edition=287891&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-30)_

As you strategize about how to use the Internet of Things (IoT) to gain a competitive advantage, the first item on your task list must be understanding all of the pieces in the IoT puzzle. Successfully connected solutions must integrate an entire ecosystem in a way that results in a simple, seamless, and cohesive experience for users in order to fully capitalize on the opportunity IoT presents.

This task is easier said than done, since planning and building an IoT architecture differs from solution to solution. However, there are some commonalities between IoT solutions that allow us to make certain assumptions in terms of what a generic, methodological approach could look like. Having this information from the outset will help you make informed decisions about what pieces of the puzzle you can or want to own, and how you want all of the pieces to fit together to facilitate the seamless collection and use of your device data to meet your unique business needs.

![Image title](https://dzone.com/storage/temp/4774883-blog-1-1.jpg)

In order to build any IoT solution; first, you would need to connect your **hardware** device to the platform over the Internet. The best way to do that is to choose hardware agnostic platform, which allows you to connect any device that suits your solution without requiring any special adaptations, whether you have various sensors, gateways, wearables, smartphones, or industrial PCs, machines, Raspberry Pis, Arduinos, etc.

It is also necessary to establish and maintain a secure and fault-tolerant **connection** between the platform and the edge devices to collect and aggregate data and manage the device. Whether you're connecting an existing product, designing an IoT-enabled product from scratch or adapting a previously IoT-enabled product, it's preferable to choose vendor which provides API abstraction and functions to help you connect your hardware device.

Then, you would need to develop an **application**, the software which visualizes data, manages devices, and adds value to the data. In this case, consider Platform vendor which provides you open APIs and libraries to develop apps that can securely control and manage your devices. You are then able to focus on your apps and let them carry the systems, security, and communications, so you can save valuable development time and forget about IT infrastructure cost, problems and scalability issues.

And finally, to make it all work, you would also need a **platform** that has the capabilities to support all of your users and devices as you scale. We all know that high security and scalability are a must. Furthermore, some of the platforms exist independently between the hardware and the application layers of the IoT technology stack. I like to call it an IoT application enablement platform since it is an integral part and the major software nexus that brings everything together in the overall IoT infrastructure.

Under this structure, I am not talking just about a gateway, or a Wi-Fi connection, or just a platform, and not even about applications. It all has to seamlessly work together as a complete entity, and it has to be configurable to suit the needs of any particular business.

Opinions expressed by DZone contributors are their own.
