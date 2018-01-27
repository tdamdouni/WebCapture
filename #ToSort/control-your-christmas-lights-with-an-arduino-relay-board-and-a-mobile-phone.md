# Control your Christmas lights with an Arduino relay board and a mobile phone

_Captured: 2017-11-12 at 21:50 from [www.embedded-computing.com](http://www.embedded-computing.com/iot/control-your-christmas-lights-with-an-arduino-relay-board-and-a-mobile-phone)_

![](http://me.opensystemsmedia.com/post/osm_uberflip/get_uberflip_item_thumbnail.php?item_id=380891122)

The Christmas Light Controller is a fun project that lets you provide public access to your outdoor lights during the holiday season - perfect for homeowners and parties, where visitors can select a number of lighting transitions via a mobile phone.

The DIY project requires a basic Arduino relay board, flashing the ready to use Arduino firmware in the relay board, setting up your own online IoT server, and configuring the solution. Then, you can let visitors and neighbors securely control your outdoor lights by simply navigating to your domain name using a browser on their mobile phones. The web-based light controller user interface is designed to be used by multiple visitors at the same time and updates in real time across all connected browsers.

# Ready-to-use ESP8266 Wi-Fi Arduino relay board

The ready-to-use Light Controller firmware is designed for the ESP8266, a low-cost Wi-Fi chip with full TCP/IP stack and MCU. A relay board with an embedded ESP8266 chip can be purchased on, for example, eBay for $20. The Arduino Light Controller firmware (C Code) can be compiled and uploaded to the ESP8266 by using the free Arduino development environment.

The following figure shows a ready to use ESP8266 WiFi relay board. The board can be wired directly to the mains and to the Christmas lights.

# ![](https://content.cdntwrk.com/files/aHViPTYzODY3JmNtZD1pdGVtZWRpdG9yaW1hZ2UmZmlsZW5hbWU9aXRlbWVkaXRvcmltYWdlXzVhMDBmNzdiYmU3YzYuanBnJnZlcnNpb249MDAwMCZzaWc9M2VjYmI5ODNlYmI0ZDdmM2U5MmJlN2E2N2M3MjRkNTY%253D)

# Online IoT server

The Light Controller firmware for the ESP8266 is designed to act as an IoT edge node and requires a server solution. The server solution includes the IoT communication module and a web user interface for controlling connected edge nodes. You can run the server software on your own computer, such as your own PC, but that limits the use of the Light Controller solution. The benefit of installing the Light Controller solution on an online server is that it enables easy and secure public access to the Light Controller's public user interface. Any person can use their mobile phone and control the lights without requiring access to your local network. If the server is running on your local network, only users with access to your private network can control the lights.

Most IoT cloud server solutions, whether they provide ready-to-use hosted services or not, are based on a standard Virtual Private Server (VPS). Most developers probably think about Amazon or Microsoft Azure's services when considering the server side of their IoT solution. These high-end services are great if you need to scale up to millions of connected devices. However, for most small-scale operations and DIY projects, a low-cost VPS is more than adequate.

The website [lowendbox.com](https://lowendbox.com) provides reviews for low-cost Virtual Private Servers and is a great place to start when selecting a VPS. We found a $12/year VPS that is more than sufficient for running the Light Controller server solution. With this VPS, we were able to connect up to 10,000 Light Controller edge nodes. Connecting more edge nodes requires more memory, but the VPS we selected has memory limitations (64MB). In any event, you will most likely connect only one or two ESP8266 Light Controller edge nodes to the online server.

All VPS providers, including low cost providers, typically provide a web-based user interface from where you can manage your VPS. The web-based control panel provides services such as selecting and installing/re-installing the operating system. The operating system of choice is typically a flavor of Linux. After installing the Linux operating system using the web interface, the server will be online and be ready for you to log on and manage.

The server-side Light Controller solution consists of two components: an IoT-ready web/application server engine called the Mako Server and the Light Controller App. The [Mako Server](https://makoserver.net/) is a pre-compiled [Barracuda App Server](https://realtimelogic.com/products/barracuda-application-server/) designed for educational purposes. The Light Controller App's server-side code is designed in the Lua scripting language and runs on top of the Mako Server's application engine.

## IoT security

A general problem with IoT protocols is that they typically cannot be used without authentication since this would leave the door completely open. However, the Light Controller app would not be very user-friendly if visitors were forced to register and login prior to being able to control the lights. We wanted the Light Controller app to be user friendly; therefore, the Light Controller solution is designed to enforce strict authorization, but not authentication, for the IoT protocol.

The light controller security concept was inspired by the article [Have we forgotten what the ancients taught us in building defense systems?](http://www.embedded-computing.com/articles/have-we-forgotten-what-the-ancients-taught-us-in-building-defense-systems) Based on this article, the Light Controller server solution is designed to: (1) work in stealth mode, and (2) enforce strict authorization. Although authentication would have added one additional line of defense, we wanted the solution to be user friendly, and the solution is designed to be sufficiently secure without having to use authentication.

## Getting started

Navigate to the [Christmas Light Controller page](https://makoserver.net/apps/LightController/) on the Mako Server website, and follow the instructions. Have fun, and happy IoT holidays.

Wilfred Nilsen, Founder & CTO of Real Time Logic, has 27 years of experience in designing embedded network software. Motivated by a vision of a connected embedded systems, he designed the Barracuda App Server with its suite of secure IoT protocols, tailoring it for the small footprint, real-time needs of embedded microcontrollers and microprocessors.
