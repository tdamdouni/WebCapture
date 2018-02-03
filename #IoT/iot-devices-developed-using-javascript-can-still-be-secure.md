# IoT Devices Developed Using JavaScript Can Still be Secure

_Captured: 2018-01-30 at 15:22 from [dzone.com](https://dzone.com/articles/keeping-the-javascript-based-iot-devices-secure?edition=359097&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202018-01-30)_

The vision for the Internet of Things is an exciting world where simple objects are interconnected to exchange data and collaborate to provide advanced services. To make objects secure and seamlessly connected, the [Open Connectivity Foundation (OCF)](https://openconnectivity.org/) develops and ratifies specifications for device interoperability regardless of the manufacturers and implementations.

The open source project [IoTivity](https://www.iotivity.org/) delivers a reference implementation of the OCF specifications, providing a foundation for developers to create interoperable devices. The open source project [iotivity-node](https://github.com/otcshare/iotivity-node) provides the [Node.js](https://nodejs.org/) binding to IoTivity for fast prototyping OCF devices using JavaScript.

Together, these projects not only allow you to quickly develop an IoT device, but also leverage the IoTivity security features to protect the device from unauthorized accesses. This article will walk you through an exercise to show you how to use IoTivity security framework to quickly and securely prototype an OCF device using JavaScript.

## Overview

Hackers used the Internet to break into a bank's terminal server and issued commands to an ATM (Automated Teller Machine) to withdraw money remotely. Although they were in different countries, both the terminal and ATM were considered to be on the same private network. However, because these devices were not actually in a physically isolated network, software security threats to them put the overall system at risk.

In the emerging IoT space, more and more devices join the network, and technologies are scaling up from smart homes and smart buildings to factory automation and all the way to smart city applications. Even on a simple home network, unless the IoT devices are completely physically isolated from the outside world, they may be hijacked by unauthorized people due to unsecured IoT software running on the devices.

OCF defined its specifications after reviewing IoT security requirements. The goal of the OCF security architecture is to protect the resources hosted on the server device, providing access only to the client devices subject to a set of access control and authorization mechanisms. In addition, end-to-end device interactions can be protected using session protection protocols such as DTLS (Datagram Transport Layer Security) and data encryption methods as shown in Figure 1.

![Image title](https://dzone.com/storage/temp/7537480-fig1.png)

> _Figure 1: OCF Security Architecture_

In the OCF security architecture, the top-most application resources are protected through the implementation of access control, authentication, and confidentiality protection. The resource access control relies on a set of predefined access policies in the form of Access Control Entries (ACE), which define permissions required to access a specific resource along with an optional validity period for the granted permission. In the following sections, I will take a Node.js based IoTivity virtual server as an example, and explain the steps to grant its accesses only to the authorized client.

## Prerequisites

In this tutorial, a container image that contains the software of an OCF Server, an OCF Client, and an Onboarding Tool is created, so that the security exploration can be done in a sandbox environment. The container technology is an operating system level virtualization, which allows running isolated apps on supported platforms regardless of the environment. [Docker](https://www.docker.com/), a popular software technology providing containers, is available on Windows, Linux, and Mac. Please reference the [Docker installation guide](https://docs.docker.com/engine/installation/) to set up Docker on your development platform, the Linux commands shown in the code block below are provided for your reference.

### Clone and Build the Container

Clone the container Dockerfile and example scripts from the GitHub repository and build the container image with the following commands.

The build will take a while as it pulls all the ingredients from the Internet and builds the software inside a container. Also note that in addition to the disk space required for Docker, make sure you have at least 20 GB available for the docker daemon to store the built image containing IoTivity programs, Android SDK, etc.

### How iotivity-node Facilitates Server Implementation

While the Docker building the container image, let's take a closer look at how to create an OCF server using JavaScript that can be discovered by other OCF devices. The following code snippet shows the skeleton of a server implementation hosting a resource at URL `/a/led` .
    
    
    var device = require('iotivity-node'),

The above script requires the `iotivity-node` module, which provides Node.js binding for IoTivity for fast prototyping of OCF devices using JavaScript. The `register()` method of the `server` object registers a resource in the OCF network. The argument passed to the method is an object that contains the properties represent the hosting resource.

After registering the resource to the network successfully, remote devices can discover this resource and get or set the representation of the resource. The requests will be processed by the `getRepresentation()` and `setRepresentation()` callbacks in below code snippet respectively.

### Run the Docker Image

Once the Docker build is complete, run the container image with the following command to mount the folders containing the example scripts.

We will be using the example scripts in a container to exercise the IoTivity security. The above command instructs the host to connect to network port 5901, as the image will start a VNC server for user interactions. The --privileged argument is required by the Android x86 emulator.

Set the password for the created VNC session when the container is running for the first time. You will need to enter that password whenever you connect to the container using any VNC remote desktop client software.

Launch a VNC client software to connect to the container. Some operating systems may not have VNC client software included with the package, you can download and install any third party VNC client that is compatible with your operating system.

Run the Android emulator with the `start-emulator.sh` script from the VNC session connecting to the container.

![Launch Android emulator inside a container](https://dzone.com/storage/temp/7560783-emulator.png)

> _Figure 2: Launch Android emulator inside a container_

If you are launching the emulator for the first time, enter the command below to install the companion app to the emulator. The companion app acts as the OCF native Client. It is also an onboarding tool for retrieving the resource state of the virtual Server and provisioning devices.

## Start the Server

Enter the following commands to start hosting an [OCF binary switch](https://oneiota.org/revisions/1393) virtual resource on the server.

Take note on the `Device ID` field shown in Figure 3, it's a unique identifier of the OCF stack instance. The value may vary and will be changed after we reset the SVR (Security Virtual Resource) database in the persistent storage later.

![Image title](https://dzone.com/storage/temp/7560821-server.png)

> _Figure 3: Install the Companion app and start hosting a virtual OCF Server_

In the OCF access control model, a resource instance must have an associated access control policy, otherwise the resource is inaccessible. Since we haven't yet set up the proper Access Control Entries (ACE) in Server's SVR database for accessing the resource, expect to see an `UNAUTHORIZED_REQ` error message while accessing the binary switch resource from the companion app, as shown in Figure 4 below.

![Image title](https://dzone.com/storage/temp/7560836-unauthorized.png)

> _Figure 4: Access the Virtual Server from the Companion app_

## Access to the Server

Secure Resource Manager (SRM) plays a key role in the OCF security architecture, as it authenticates incoming requests received via the secure port, and manages security resources such as SVR, Access Control Lists (ACL), credentials and device owner transfer state.

On receiving requests for a hosted resource, if the request arrives over the secured port, only authorized requestors, known as the "subject" will be used to match ACL entries. Access is denied if there is no ACE matched. If the request arrives over the unsecured port, the only ACL policies allowed are either those ACEs that use an anonymous connection type, or a subject wildcard that matches any anonymous requests.

In the OCF security framework, the access policies may be stored by a local ACL or an Access Manager Service (AMS). This tutorial uses local ACL mechanism for simplicity.

The SVR in IoTivity software implementation optionally takes a configuration file in CBOR (Concise Binary Object Representation) format during the initialization, and a `json2cbor` utility is designed to generate the binary configuration file from a human readable JSON (JavaScript Object Notation) file. In addition, a wrapper script `init-svr-db.sh` is provided to simplify the SVR database creation process.

Press `CTRL-C` to stop running the Server script, and re-launch the Server after setting up the default SVR database with the following commands.

The current Server script does not specify the use of secure endpoints for communications, so the companion app sends the access request to the Server over an unsecured channel. On receiving the request, the Server treats the request as anonymous, and no device UUID or role ID is associated with that request. The Server then consults the ACL and looks for an ACE matching any configured access policy.

![Image title](https://dzone.com/storage/temp/7560856-anon-clear.png)

> _Figure 5: Allowing anonymous access to the Server_

## Access Authentication

In OCF terminology, the device acting as the Server holds and controls resources, providing the device acting as a Client access to those resources, subject to a set of security mechanisms. So, let's open a new window and introduce the Client to our experiment with the following commands to set up its SVR database and launch the Client script.

![Image title](https://dzone.com/storage/temp/7560897-unauthorized-client.png)

> _Figure 6: Access the Server from a new OCF Client_

Though the Client can change the resource state of the Server, it doesn't seem right that a new Client can access the existing Server without receiving an acknowledgment!

### Use a Secured Endpoint

Let's review the default SVR database named `oic_svr_db.json`, which we configured for the Server. The `acl` section contains a list of ACE access policies that govern the subjects and operations allowed on the resources. Though access control mechanisms can be subject-based, role-based, or connection-based, we only apply a connection-based access control mechanism in this tutorial for simplicity.

The first four ACE policies instruct the SRM to allow the resource discovery and the ownership transfer requests through either secured port or unsecured port, but the fifth ACE policy grants the read/write accesses to any requests from unsecured anonymous connections.

To properly manage the accesses on the Server, instead of configuring the ACE to allow anonymous connections in the default SVR database, we need to modify the configuration to allow only encrypted connections as the first step.

Launch the pre-included `geany` editor to modify the `subject` field of the corresponding ACE from `anon-clear` to `auth-crypt` and reset the SVR database.

![Image title](https://dzone.com/storage/temp/7560928-edit-svr-db.png)

> _Figure 7: The ACE property to be revised to accept requests through a secured channel_

To enforce the use of a mutually authenticated secure channel for exchanging messages, the Server must set the `secure` property of the hosting resource during the resource registration. The `oic.sec.cred` resource in the SVR database on each device should also hold the credentials used for mutual authentication and certificate validation. The credential of the Client will be exchanged and installed on the Server while pairing the two devices by the companion app.

Launch the `geany` editor to change the `secure` property of the resource server from `false` to `true`, as shown in Figure 8 below.

![Image title](https://dzone.com/storage/temp/7560938-set-secure.png)

> _Figure 8: Properties used by the Server during the resource registration_

### Onboarding Unowned Devices

Before a device can interact with other devices in an OCF environment, it must be onboarded appropriately. The onboarding process starts by configuring the ownership of the device, thus only the legitimate user who purchases the device can establish its ownership using the Onboarding Tool (OBT). Once ownership is established, the OBT becomes the mechanism for provisioning the device. At the end of the onboarding process, the device is ready for normal operations.

To establish ownership with a device using the companion app, select the `Provisioning` action in the control panel to discover both owned and unowned devices in the OCF network as shown in Figure 9.

![Image title](https://dzone.com/storage/temp/7560949-discovering.png)

> _Figure 9: Use the Companion app to discover unowned OCF devices_

Once an unowned/new device is discovered, press the associated button to assert the companion app as the owner and manager of the device. The companion app uses one of the Owner Transfer methods (OxM) supported by the device to securely establish trust in the device, authorize the companion app to manage the device, and prepare the device for provisioning. An owner credential is provisioned to the device, which allows the device and the companion app to mutually authenticate during subsequent interactions.

![Image title](https://dzone.com/storage/temp/7560962-oxm.png)

> _Figure 10: Use the Companion app to establish ownership with the unowned Server_

### Pair the Client to the Server

After both the Client and the Server devices are onboarded, the credential of the companion app has been installed to the `oic.sec.cred` resource of both devices, the companion app is now trusted by both the Client and the Server. However, in order to have the Client and the Server interact over a mutually authenticated secure channel, they need to have each other's credentials.

Identify the Client and the Server devices by the `Device ID` with the companion app. Click the checkboxes of the desired devices, and press the button in the menu bar to pair the selected devices. The companion app will install the peer credential to each device to achieve mutually trusted status between the Client and the Server.

![Image title](https://dzone.com/storage/temp/7560965-pairwise.png)

> _Figure 11: Pairing the Client and the Server_

![Image title](https://dzone.com/storage/temp/7560979-secured.png)

> _Figure 12: The managed Client accesses to the Server through a secured channel_

## Summary

After completing the onboarding process and pairing the Client and the Server, the resource hosted on the Server can be retrieved and updated by the Client, as shown in Figure 12. Other Clients joining the network need to go through the same authentication process before they can access the Server.

Through these technologies, including mutual authentication, per resource access control, data transport layer protection mechanism, and more, OCF ensures the robustness of the resource confidentiality protection and message integrity among IoT devices. Reference the [OCF Security Specification](https://openconnectivity.org/specs/OCF_Security_Specification_v1.3.0.pdf) for more detailed information.
