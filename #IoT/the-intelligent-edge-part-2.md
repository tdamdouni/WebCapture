# The Intelligent Edge (Part 2)

_Captured: 2017-12-19 at 17:27 from [dzone.com](https://dzone.com/articles/the-intelligent-edge-part-2)_

[Download Red Hat's blueprint for building an open IoT platform](https://dzone.com/go?i=250323&u=https%3A%2F%2Fwww.redhat.com%2Fen%2Fresources%2Fintelligent-systems-solution-internet-things)--open source from cloud to gateways to devices.

[This is a continuation of the blog series: The Intelligent Edge](https://dzone.com/articles/freewave-blog-series-the-intelligent-edge).

## **Novice App Dev: A Q&A With Greg Corey from FreeWave Technologies**

The Internet of Things (IoT) has changed the consumer world in ways no one ever imagined. By placing intelligence in the IoT network, the "Thing" can do whatever we want it to do. Now, industrial companies are seeking to take advantage of this edge-deployed intelligence in order to maximize profits, improve safety, and streamline operations. In addition to the challenges IoT technology had to overcome such as cybersecurity, scalability and interoperability, Industrial IoT (IIoT) must also focus on reliability, ruggedness,and more.

In the second installment of "The Intelligent Edge," we sat down with Greg Corey, [FreeWave](http://www.freewave.com/#) systems engineer, to talk about his new app - [ZumDash](http://www.freewave.com/zumdash-demo/) - and the future of app development of the Internet of Things.

**FreeWave**: Can you talk about how you got involved in IoT app development and what that means from an Industrial IoT perspective?

**Greg**: I got involved with IoT app development when we [FreeWave] started the ZumIQ project. IoT app development revolves around developing software to interconnect devices, and there's a huge need for that in the industrial space known as the IIoT. So, I started working with some graphical JavaScript-based environments like Node-RED, and I realized that this quickly allowed me to solve problems that were facing our customers.

**FreeWave**: Are Node-RED and JavaScript the primary languages being used right now to develop those apps?

**Greg**: Yes, mostly you'll see a lot of Python stuff, a lot of Java, and hence JavaScript, and then you'll see some stuff written in C as well, but, really, the web-based languages have taken off. People write apps in Java and PHP for the most part. And then Node-RED is a graphical frontend for JavaScript.

**FreeWave**: Can you talk a little bit about the app that you developed for FreeWave - ZumDash - and where it resides within an IIoT network?

**Greg**: So, FreeWave has traditionally made radio products where you just put data in and out of the system and that's all it does. It's just a complicated replacement for a physical cable. With the new ZumIQ platform, it allows us to add a lot of intelligence at the Edge of these networks where a radio is functioning much more than just a radio. It's actually an application development environment. It's an application platform. So, the app that I developed, I wanted to showcase the radio's capabilities at the Edge of the network, and specifically, there's a few other things I wanted to show.

I wanted to show data storage: so, actually, it's recording data on the radio itself. I wanted to show the display of that data in a dashboard format. I wanted to show communication, so the radio can still act as a radio and then you can have email alerts and other alerts based on data points. And then I wanted to show logic as well: If This Then That. So, to be able to read a sensor value and if it's within a certain range to then take action on it. So, the app that I built was really meant to showcase those four things: data storage, dashboard, communication, and logic.

**FreeWave**: So, for the storage part, how often are people trying to actually store data on those Edge devices as opposed to having them just be conduits for the data transmission? Is that a different way of approaching it?

**Greg**: Yeah, it's a different way of approaching it, and what it allows you to do is free up network capacity. So, if you're continuously sending and receiving data from the field to a central source, you're using throughput and bandwidth on that network. With some of these Edge networks, it could be in something that's moving on the ground and there's not a very high antenna height; it could be a really noisy environment; there could be a lot of metal obstructions in the way. Sometimes, in the industrial realm, the networks aren't as rock solid as you would want them to be, or there's limited capacity for connectivity. So, by moving some data storage operation to the Edge, we can then free up our network capacity for other resources.

**FreeWave**: So then from there are you able to run analytics on that Edge device to filter out some of the data that you don't need?

**Greg**: Yeah. Iin ZumDash there's a frontend on it that I use. Using the frontend, you can remotely log into the radio, you can examine every piece of data the radio has recorded, and you can do that graphically. Then, you can build charts based upon that data, and then you can also export to Excel. So, all the data that resides on the radio in the MySQL database is available for analytics remotely, on demand.

**FreeWave**: Does this have a dual track function where you can store data and look at it later, but you can also get the data in real-time if you need it?

**Greg**: Yes, and also, how often the app records data to the database is configurable. You can look at configured intervals. The quickest time I can do at the moment is five seconds. So, every five seconds it'll record data from six different sensors.

**FreeWave**: Why was the dashboard display an important part of this app?

**Greg**: It allows easy access to data. Let's say there's a problem and you want check on the status of a device. I don't want to have to look through logs or something like that. I want that data easily displayable. So, adding the dashboard allows anybody to be able to log in and immediately look at the common things that you look for in a device status.

**FreeWave**: It seems like something that we've been talking about with regard to Node-RED and some of these other components of building out an IoT network today, is that you have to be prepared for people that aren't necessarily trained with a computer engineering background to be able to access and use these things. Is that dashboard and the idea of developing in a Node-RED setting, is that to kind of split the difference a little bit and help out with that usability?

**Greg**: Yes, it is. So, Node-RED has these different dashboard modules built into it that allow you to pipe any data easily to a dashboard, and that way you don't have to look through logs or anything like that. It does help with usability. And, like I said, I'll give you access to the actual app and you can look at it and see how intuitive it is to use in the frontend. You can make it as simple or as complex as you want it to be.

**FreeWave**: For the communication component, it still has to function kind of as a traditional like radio platform, right? Why does it need to have that dual function?

**Greg**: The core purpose of a FreeWave radio is to be able to transmit and receive data in any environment in an industrial setting. The communication backbone forms the primary role of the product so you could put data in and data out of it. Then, the ZumIQ platform allows you to interact with that data itself.

**FreeWave**: For the final component, the logic side of things, why is that important?

**Greg**: It's the core of any computer application, the software: If This Then That. That's not anything necessarily groundbreaking in the industrial space. There are lot of ways you can accomplish, "If This Then That." From an automated perspective of electronics, you can do it remotely on-site with other devices, or sometimes they even send that data to a central location and then make the decision there on what to do with it. And the more control you add to the Edge of the network the less likely there are to be communication failures in that message. So, the smarter the device is at the Edge, the quicker you can make a decision, and the more resilient. That's going to be the problem that you could encounter, because you're eliminating, essentially, the middleman.

**FreeWave**: It seems like you're probably dealing with even bigger datasets than in the past though. Is that something you have to think about as well for functionality?

**Greg**: Yes. For example, I was just looking at one of the database tables for a level of fluid, and there are 230,000 entries in that the database has been running for the past two weeks. On the ZumDash, there is a storage space indicator on the app to let you know how much storage you have. We can always expand the storage on ZumIQ in the future if we need it, but currently we have about 500 Megabytes available for database storage and for writing the sensor data that will function with the fastest write rate that'll last you a couple months to a couple years in some situations. And you can control it as well. I wanted to, say, only take the average value from the last 10 values, I could strip that down if I wanted to very easily.

**FreeWave**: What are some of the, you know, application possibilities for ZumDash? What did you develop it for originally? And then where do you see some of the top use-case possibilities?

**Greg**: I originally developed this as an oil and gas application to measure water or oil in a storage tank. You can use that in any process-related industry for level measurement, but I originally wrote it for oil and gas, specifically looking at water and oil levels. And there's other systems that currently do that in oil and gas but there isn't just a radio solution that does it. You have to buy all these other hardware devices to accomplish that. The thing about this is it's super adaptable. You can point it to any dataset you want and then display that data, record it, make decisions on it. So, any numerical value from anywhere. It doesn't specifically need to be a tank level. But, it could have other applications like rainwater farms. We have some customers in New Mexico that have ranches and they have their own water systems that are off the grid, and they use this to monitor water in those tanks for how much they have on site. You can also use this, for example, in an educational setting. So, if you're doing a research project on snow melt, or rainfall, or any other type of environmental metric that has sensors you can bring that into this also.

Join us next week as we continue this Q&A with Greg Corey as we explore lessons learned, high level industry impacts, trends and challenges, and a sneak peek at what's to come in industrial app dev for edge intelligence.

**Stay tuned for Part II of this interview next week!**

[Build an open IoT platform](https://dzone.com/go?i=250322&u=https%3A%2F%2Fwww.redhat.com%2Fen%2Fresources%2Fintelligent-systems-solution-internet-things) with Red Hat--keep it flexible with open source software.
