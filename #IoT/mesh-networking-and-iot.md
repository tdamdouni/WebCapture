# Mesh Networking and IoT

_Captured: 2018-05-22 at 21:17 from [dzone.com](https://dzone.com/articles/how-mesh-networking-will-make-iot-real?edition=376341&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202018-05-22)_

In the past, building beyond a single-point of connection required high-cost hardware solutions and software implementations to connect the in-between spaces needed for device-to-device communication. As IoT platforms have matured, they have started to embrace a low-power, low-cost alternative that can bridge the gaps between these devices: wireless mesh networks.

## **What Is a Wireless Mesh Network?**

A wireless mesh network is an infrastructure of nodes (a mesh topology) that are wirelessly connected to each other. These nodes piggyback off each other to extend a radio signal (like a Wi-Fi or cellular connection) to route, relay, and proxy traffic to/from clients. Each node spreads the radio signal a little further than the last, minimizing the possibility of dead zones.

![](https://cdn-images-1.medium.com/max/800/0*xq4uagQuRb3vF63a.)

## **What Are the Components of a Mesh Network?**

  1. **Gateway** -- Border routers are the devices that have additional connectivities beyond mesh that allow them to pass messages between networks. You can think of these devices as providing a "backhaul" to the internet for the local mesh network.
  2. **Repeater** -- Routers are devices that forward messages between end devices (endpoints) in a mesh network. They are not typically designed to sleep because they are a part of the mesh networks' infrastructure.
  3. **Endpoint** -- End devices are mesh-only devices that do not route messages for other devices in the mesh network. Because they have no networking responsibilities, they can enter sleep mode and are good candidates for battery-powered nodes and sensors.

## **How Does Mesh Networking and IoT Work Together?**

It should be noted that each mesh networking solution works differently. So for this article, will focus on how [Particle Mesh](https://www.particle.io/mesh/) technology works. Particle Mesh is a wireless mesh network designed to connect the spaces in between existing Wi-Fi and cellular deployments with local networks that are low-cost, secure, and reliable.

![](https://cdn-images-1.medium.com/max/800/0*siiwq7RKboE3nEc_.)

> _Particle Mesh Hardware -- Argon, Boron, and Xenon_

Traditional IoT devices that use Wi-Fi and cellular connectivity depend on the cloud to relay messages between devices. This works great when you're making a standalone product -- but sometimes you need more than that. Particle Mesh development kits aren't just connected to the Internet, they're gateways to the Internet and create a local wireless mesh that other devices can join. These devices work together to ensure that messages get where they're going, and power products that aren't possible or economically feasible with Wi-Fi and cellular connectivity. Particle Mesh gives every IoT device a local network to understand and connect with the world around it, ensuring products have the information they need.

## **Why Use Mesh Networking for IoT?**

While wireless mesh networking technologies have been around for some time, only recently has the power of mesh reached a point of maturity alongside high availability from chip and silicon vendors. With newer approachable costs, wireless mesh networking has become ideal for IoT builders. And with the rise of connected homes and industry support on open source resources like Thread, Mesh is now truly accessible while being low-cost enough to scale for production. As such, wireless mesh networking is becoming a much more viable, real choice for industrial and commercial IoT applications. It can provide additional services in a system where extending a connection between two nodes is limited:

  1. **Smart cities** -- Wireless mesh networking is great for extending radio signals through parking garages, campus grounds, business parks, and other outdoor facilities. Parking garages that utilize space availability checkers benefit greatly from mesh networks because they can extend the signal throughout the whole space, and be able to communicate when a spot has been taken by other clients.
  2. **Healthcare equipment** -- Wireless mesh networks can help monitor and locate medical devices quickly. They can also act as a backup for medical equipment that always needs to remain online. If one node loses connectivity, another node can step in to keep the connection alive.
  3. **Smart home** -- Wireless mesh networks can help you track and manage temperatures across your house. Setup one powered gateway and use temperature sensors and Mesh-enabled nodes in each room to capture live data and adjust settings automatically.
  4. **Farming** -- Wireless mesh networking is also great for tracking sun exposure and water levels across your crops. You can scale at a low cost with Mesh-enabled nodes across a whole acreage to create a cellular-connected IoT farm.
  5. **Industrial internet** -- Wireless mesh networking is also great for tracking pallets and monitoring large physical objects with a highly reliable wireless connectivity network. With wireless mesh networks, you can easily track key data across your factory floor, and across multiple locations to identify issues before they happen.

## Is Wireless Mesh Networking Right for You?

When using wireless mesh networks for your IoT project, it is important that you consider these three core variables: **installation**, **device management**, and **support**.

  1. **Installation** -- This aspect entirely depends upon your intended application. You need to ask yourself if you actually needed a distributed set of mesh nodes for your use case. If you intend to implement mesh for commercial or industrial applications, you should set up a small-scale, mesh network to determine the efficiency of the system before deploying a mesh networking system at large.
  2. **Device management -- **When comparing mesh solutions, it's important to find one that allows you to manage fleets of devices, monitor event logs, perform diagnostics and send updates wirelessly.
  3. **Support -- **When selecting a mesh-solution, it's also important to consider the community surrounding it. Mesh networking solutions with limited adoption will have fewer resources available to aid you in development.

## Looking Beyond Mesh Networking

If you're looking to implement wireless mesh-networking into your IoT infrastructure, you must examine the [whole IoT system](https://dzone.com/articles/the-6-complexities-of-hosting-a-managed-iotnbspser) and not just a singular component. To build any IoT product or infrastructure you need hardware, software, and connectivity. To integrate these three components, you must [research IoT platforms](https://dzone.com/articles/cake-eating-contest) that can provide these components to you and [consult IoT domain experts](https://dzone.com/articles/the-5-domain-experts-you-need-to-build-an-iot-device) to help you scope these the three complexities.

## The Bottom Line

Mesh networking is a critical component for IoT architecture because it enables devices to cover more ground and collect more data. Companies must decide if mesh networking is an efficient and effective way to scale their local network's reach, or if relying on traditional Wi-Fi and cellular connections are sufficient for their communication systems.

Opinions expressed by DZone contributors are their own.
