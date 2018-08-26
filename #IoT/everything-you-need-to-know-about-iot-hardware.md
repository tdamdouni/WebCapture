# Everything You Need to Know About IoT Hardware

_Captured: 2018-04-25 at 07:32 from [dzone.com](https://dzone.com/articles/everything-you-need-to-know-about-iot-hardware?edition=375219&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202018-04-24)_

Hello! After joining Talend four months ago, I'm now getting around to publishing my first article. Since this is my first entry, I decided to dive into the details on one of my favorite topics: the Internet of Things. This is the first entry in a series I'll be writing around the Internet of Things where we'll go over all the parts of an IoT project, starting from the edge device, continuing to data ingestion and its integration to business applications. If you scroll around the internet on any tech site, you'll find a lot of articles about IoT out there. We've even done some pretty heavy writing on Talend's website so I'll try not to make this one _yet another IoT article!_

**Note**: I really recommend that you have a look at a few of the articles:

![](https://www.talend.com/wp-content/uploads/IoT-Growth-Graphic.png)

## **The Internet of Things: Hardware Considerations**

The purpose of this first article is to introduce the fundamental concepts around the Internet of Things but from a device point-of-view -- more precisely, the kind of hardware you will be dealing with rather than simply looking at the data collection or software aspects.

I'm not going to sum up everything that you'd be able to find on your own, but rather, I'll try to explain basic things you need to take into consideration when you are just getting started -- because it's the wild wild west out there. There are a lot of devices, different types of microcontrollers, and programming paradigms to choose from. Before we start really getting into this, we should ask ourselves a couple of questions:

### **Why All the Buzz Around the Internet of Things?**

When you look at predictions around the growth in the IoT market, you see a correlation between the growth of connected devices and the growth of data volumes.

The mass adoption of this technology means it could potentially change the society we are living in. For those who think that it's "utopic," I really recommend you to read Jeremy Rifkin's' book _[The Zero Marginal Cost Society..._](https://www.amazon.com/Zero-Marginal-Cost-Society-Collaborative/dp/1137280115/ref=sr_1_1?ie=UTF8&qid=1521814704&sr=8-1&keywords=zero+marginal+cost+society) and you'll see that we are not that far from becoming a "collaborative common society."

All types of companies from startups to major enterprises like GE are seizing this new market opportunity and have developed what they call "self-service solutions" and platforms ready for you to tackle IoT head-on. However, these tend to fall short because it's most likely going to be proprietary tech, built for specific needs and requiring intensive development.

### **OK, Alright, but Why Now?**

![](https://www.talend.com/wp-content/uploads/Ubiquitous-Computing-Graphic.png)

> _I believe we are currently in the era where three technology forces are converging._

  1. **Data**: It's the "Big Bang" for data and analytics and we have the technology to ingest and store the massive amount of data using open source technologies such as Hadoop and its ecosystem as well as running batch, interactive or real-time analytics also using open source frameworks such as MapReduce and Apache Spark.
  2. **Cloud**: What started as SaaS has fully evolved and matured into full infrastructures and platforms. We are now only a few clicks and minutes away from creating an entire IT infrastructure and business solution in the cloud.
  3. **Electronics/Robotics**: We see a lot of innovation in sensors capturing new types of data around our movement and our environment. You can easily start on a robotics project with your kid using a cheap and accessible development board. Moreover, anyone can start prototyping any innovative idea and get it crowd founded.

## Ubiquitous Computing: The Start of IoT

![](https://www.talend.com/wp-content/uploads/IoT-Graphic-Talend-3.png)

OK, so let's start at the beginning now that we understand the market opportunity. The Internet of Things is not new. Originally, ubiquitous computing, coined by Mark Weiser in 1991, as "the computer for the 21st century" referred to a paradigm shift in which a general-purpose machine (the PC) will be replaced by a large number of specialized computers, which are embedded into everyday objects. A typical application for this is the smart home. So, Ubiquitous Computing as a vision was much more than technology, it dealt with the question of how users would interact with an environment that is physical but enriched with computing at the same time.

Simply put, ubiquitous computing is everywhere. Pervasive computing is somewhere (like your desktop). In practice, I don't think there is much difference and they are just different terms to describe the same computing models.

Ubiquitous or pervasive computing is a concept in computer science and engineering where computing is made to appear everywhere and anywhere. In contrast to desktop computing, ubiquitous computing can occur using any device, in any location, and in any format. A user interacts with the computer, which can exist in many different forms, including laptop computers, tablets, and terminals in everyday objects such as a fridge or a TV.

## **The Internet of Things**

The term "Internet of Things" was coined by Kevin Ashton in 1999. The Internet of Things is really more of a marketing buzzword. I would consider it to be an application of pervasive or ubiquitous computing. In this paradigm, common everyday devices and objects are assumed to be smart computing devices connected to the Internet and capable of communication with users and other similar devices. The Internet of Things was originally thought as extending the principles of the Internet as a network organization concept to physical things.

Whereas ubiquitous computing was designed to make objects intelligent and create richer interaction, the Internet of Things was much more focused on virtual representations of automatically identifiable objects.

When Kevin Ashton stated, "We're physical, and so is our environment. Our economy, society, and survival aren't based on ideas or information -- they're based on things. You can't eat bits, burn them to stay warm or put them in your gas tank," I believe he was trying to tell us not to forget that today's computers -- and, therefore, the Internet -- are almost wholly dependent on human beings for information.

Almost all of the data available on the Internet was first captured and created by human beings -- by typing, pressing a record button, taking a digital picture. The problem is, people have limited time, attention and accuracy-all of which means they are not very good at capturing data about things in the real world and that why we are using electronics to do that.

Now that we better understand the concept, let's dive into the types of hardware that make the IoT concept actually work in the real world.

![](https://www.talend.com/wp-content/uploads/System-on-a-Chip.png)

## **What Are the "Things" in IoT?**

### **System On Chip (SOC)**

![](https://www.talend.com/wp-content/uploads/Logic-Controller-and-Terminal-Unit.png)

SOC are electronic systems that integrate a Microcontroller Unit (MCU) as one of its components. It typically runs on a single MCU and can be 8, 16, 32 bits. It also exposes General Purpose Inputs/Outputs (GPIO) and is programmable using a toolchain that compiles the code (Firmware) and loads it in the MCU's permanent memory (SDRAM).

The most popular board for the past seven years has been the Arduino, Atmel, then ARM-based development board that comes with an integrated development environment (Arduino IDE), simple programming paradigm and the most common and widely spread form factor.

Another SOC became very popular few years after, the Node-MCU or ESP-01 or ESP8266. It's a kind of smaller, cheaper and lower consumption Arduino Uno on Steroids. It has more memory, a faster processor, embedded Wi-Fi but less GPIO. It is bit trickier to start programming it but it integrates nicely with the Arduino IDE. You can get started by having a look [here](https://github.com/esp8266/Arduino).

We've recently seen some market consolidation in this space as Atmel was bought by Microchips and [ARM by Softbank](https://www.theverge.com/2016/9/5/12798302/softbank-arm-acquisition-complete).

### **Industrial Microcontroller (PLC and RTU)**

In the industrial world, digital computers have to be rugged and adapted for the control of manufacturing processes, such as assembly lines, or robotic devices or any activity that requires high-reliability control and ease of programming and process fault diagnosis. There are two well-known types of Microcontrollers you should know. The Programmable Logic Controller and the Remote Terminal Unit.

![](https://www.talend.com/wp-content/uploads/Single-Board-Computer.png)

A Programmable Logic Controller (PLC) is basically a gigantic microcontroller. It does the same things a microcontroller can do, but with higher speed, performance, and reliability where a microcontroller is really just a tiny low power CPU or computer with some output registers wired to pins.

![](https://www.talend.com/wp-content/uploads/Raspberry-Pi-and-Onion.png)

A Remote Terminal Unit (RTU) is a microprocessor-controlled electronic device that interfaces objects in the physical world to a distributed control system by transmitting telemetry data to the system and/or altering the state of connected objects based on control messages received from the system.

The Functions of RTUs and PLCs pretty much overlap, but in terms of usage, RTUs tend to be a better fit for wide geographic telemetry, while PLCs are best suited for local area control.

### **Single Board Computer (SBC)**

A single-board computer (SBC) is a complete computer built on a single circuit board, with a microprocessor(s), memory, input/output (I/O) and other features required of a functional computer. Single-board computers were made as demonstration or development systems, for educational systems, or for use as embedded computer controllers. Many types of home computers or portable computers integrate all their functions onto a single printed circuit board. Unlike a desktop personal computer, single board computers often do not rely on expansion slots for peripheral functions.

The first true single-board computer was born in 1976 called the "dyna-micro" was based on the Intel C8080A, and also used Intel's first EPROM, the C1702A. SBCs also figured heavily in the early history of home computers, for example in the Acorn Electron and the BBC Micro. Other typical early single board computers like the KIM-1 were often shipped without an enclosure, which had to be added by the owner.

Nowadays we see a lot of those SBC on the market but in my opinion, two families are standing out from the crowd: the Raspberry Pi and the Onion Omega.

The Raspberry Pi is an SBC was developed in the United Kingdom by the Raspberry Pi Foundation to promote the teaching of basic computer science in schools and in developing countries. The original model became far more popular than anticipated, selling outside its target market for uses such as robotics, the Internet of Things...

Several generations of Raspberry Pi have been released. All models feature a Broadcom system on a chip (SoC) with an integrated ARM compatible central processing unit (CPU) and on-chip graphics processing unit (GPU).

The Omega is a personal single-board computer created by a startup company called _Onion_, released on Kickstarter. It is advertised as "the world's smallest Linux Server". The system combines the tiny form factor and power-efficiency of the Arduino, with the power and flexibilities of the Raspberry Pi, you can find this SBU in a lot of device around, if you own a D-Link router you'll find out that it is powered by an Onion Omega.

## **Conclusion**

Let's face it: microcontrollers, computers, smartphones, wearables, and the Internet of Things are already playing a big part in our day-to-day life whether we interact with them or "they're acting as an invisible servant." Is this going to change the world? It kind of already does and it's not going to stop here.

Now that we know a bit more about the concepts and the history of the IoT from a device perspective, stay tuned for the next episode of the series that will be about the wild world of the Internet of things Networks and messaging protocols.
