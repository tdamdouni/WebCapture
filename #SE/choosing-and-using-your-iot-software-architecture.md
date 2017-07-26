# Choosing and Using Your IoT Software Architecture

_Captured: 2017-05-13 at 10:47 from [dzone.com](https://dzone.com/articles/iot-software-architecture?oid=twitter&utm_content=buffera1c78&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

When we put together an IoT system, we have a few options. Are we going to build a full embedded system? Use a real-time OS? use embedded Linux? What?

These are really good questions and are heavily dependent on the application for your device. If the device has hard real-time constraints, maybe embedded Linux isn't the best choice. If the board is custom, and you can't easily reuse software for your system, you might be stuck rolling your own. But in most cases today, embedded Linux is, at worst, a strong option, and usually the right choice. It has robust tooling, doesn't cost a fortune to support or build, and supports a wide range of hardware. Using tools like Buildroot and Yocto make integrating networking support and strong encryption much easier than they've been in the past, too.

Okay, so you've decided to use embedded Linux. What then?

Well, we have lots of options. We need to decide how we're going to package our system, how we're going to deploy it, and how we're going to update it. How we're going to test it. How we're going to monitor it -- if we are. How we can debug problems on deployed devices. How we'll handle errors.

And these don't even begin to discuss functionality yet.

We've established the system architecture at this point -- we're using embedded Linux. Communication is over TCP/IP (or perhaps some other application-level protocol like HTTP). We're going to encrypt our traffic (right?). But what about application architecture?

So when we look at architecture generally, we have a couple of sub-disciplines. Here, we want to look at two in particular -- application architecture and technology architecture. Here, application architecture is the logical architecture of the application -- how components will be partitioned, how they'll be used, that kind of thing. This differs from design, which is much closer to coding the components. Technical architecture outlines the technology we'll use and how that technology maps onto the application. Some folks will tell you that the technology doesn't ever impact the application architecture -- those people are wrong. The technology architecture will certainly have an impact on the application architecture, as the application architecture will influence the technology used. And it should -- but don't go overboard.

You don't want to make these the same thing, after all. Application architecture shouldn't change as much as the technologies used. You should be able to bring new technology into your system as appropriate based on the overall application architecture.

Next time, we'll start to go into how you do this, and start establishing some common patterns you'll want to use.

### Like This Article? Read More From DZone

Opinions expressed by DZone contributors are their own.
