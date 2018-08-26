# How to Choose a Microcontroller for IoT

_Captured: 2018-07-03 at 23:08 from [dzone.com](https://dzone.com/articles/how-to-choose-a-microcontroller-for-iot?edition=385192&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202018-07-03)_

Most IoT applications require more than just adding a sensor to a physical object. When people talk about 'smart objects,' they are usually talking about the addition of an Internet-connected [microcontroller](https://en.wikipedia.org/wiki/Microcontroller) (also known as an **MCU**).

Microcontrollers can be thought of as tiny computers that are added to any physical object or space to give it a 'brain.' They contain one or more [computer processors](https://en.wikipedia.org/wiki/Central_processing_unit), along with [memory](https://en.wikipedia.org/wiki/Computer_memory) and programmable [input/output](https://en.wikipedia.org/wiki/Input/output) peripherals -- all in a single integrated circuit.

MCUs are different from the [microprocessors](https://en.wikipedia.org/wiki/Microprocessor) that are found in personal computers because they are specifically designed for [embedded applications](https://temboo.com/iot-applications) where computing is not the sole purpose of the application.

While MCUs have less capability than a standard computer processor, their low cost makes them a more practical option for adding computing capabilities to an object, space, or process that doesn't have them.

Think of something like a warehouse, bridge, or [industrial machine](https://temboo.com/manufacturing) that typically doesn't contain a computer. In cases like these, adding an Internet-connected microcontroller provides enough computing power to enhance these things without adding the higher cost and complexity of standard computer processors.

## Key Features of Microcontrollers

![Image title](https://dzone.com/storage/temp/9601869-microcontrollers-x-3.jpg)

In order to be able to determine which microcontroller will work the best with your application, you'll need to know some of the key features of microcontrollers and what they do. Below are some of the specs that you'll encounter and need to make sense of when looking at a data sheet for an MCU:

  * **Bits**: Microcontrollers are typically sold by the number of bits that they offer. This impacts the speed at which they are able to perform non-trivial computations.

  * **RAM**: RAM is a fast-access memory that does not retain data in an absence of power. All MCUs come with certain amounts of RAM, which allows your microcontroller to quickly perform various actions. The more you have, the better, but the added RAM increases the cost of the MCU.

  * **Flash**: Flash is computer memory that retains data in the absence of power. At least some of this is essential, and it's very useful for features like offline storage.

  * **GPIO**: GPIO stands for general-purpose input/output pins. These are the pins that you will use for connecting your sensors and actuators to the MCU and the internet. The number of pins can range from one to the hundreds, depending on the microcontroller.

  * **Connectivity:** This is how the board (and application) connects to the Internet via Wi-Fi, Ethernet, or some other means. This is an important aspect of connected sensor applications, so we'll go over this topic in greater detail later.
  * **Power consumption:** Power consumption is critically important for connected sensor applications, particularly when your device has to rely on something like a battery or solar power. This spec will tell you how power hungry the MCU is by default and whether or not it supports power-conscious programming techniques.
  * **Development tools and community:** It's important that there is a mature set of tools, documentation, and community support to help build programs that will run on the MCU you select for your application.

## Microcontroller Operating Systems

Now, let's talk about the operating system that runs on top of the Microcontroller hardware. In the same way that personal computers run an operating system like Windows, MCUs run an operating system, too.

You have three main options:

  * **Bare Metal** means that there is, in fact, no operating system. This was the original approach to working with microcontrollers, and it's still quite popular because it's cost-effective and efficient. The main downside to this option is that it provides less support for the developer of the software.

  * **RTOS** stands for "Real-Time Operating System." An RTOS system provides exact guarantees in regards to the time in which operations will complete. This is critical for coordinating physical machinery.

  * **Linux** is much easier to program and connect to the Internet. It behaves more like a "real computer" as the average person might know it, which is great for many of the reasons previously stated. However, because of this, it does not provide any timing guarantees.

**Bare Metal**

**RTOS**

**Linux**

The original and simplest approach

Provides guarantees for the timing of processing with input/output events

Popular open-source operating system based on UNIX, originally for personal computers

No operating system

Program runs within the operating system

Significantly more accessible and easier to program

Code talks directly to the computing components

Have the ability to suspend a task and have a high-priority task execute

Robust community of people who can help with support

Limited programming support

Quick to set up but time-consuming to debug

More difficult to get real-time performance

## Development Boards

![Image title](https://dzone.com/storage/temp/9601895-development-boards-x-3.jpg)

MCUs are most commonly brought along with what is known as a "**development board**." A development board provides everything necessary to program the MCU. They're the perfect starting point for building connected systems.

Development boards are printed circuit boards containing an MCU and the supporting components needed to program the MCU.

They include things like a power source, support for connecting sensors, and sometimes even onboard sensors and actuators.

They're useful for prototyping before final manufacture of a custom solution and popular for various engineers working on embedded systems development.

Development boards enable users to quickly connect sensors and actuators (if they're not already included on the board) and their accompanying software facilitates the creation and deployment of code.

## Choosing a Microcontroller for Your IoT System

There are many different development boards and microcontrollers available from a variety of companies: [TI](http://www.ti.com/wireless-connectivity/simplelink-solutions/overview/overview.html), [Samsung](https://www.artik.io/), [Arduino](https://www.arduino.cc/), [Raspberry Pi](https://www.raspberrypi.org/) and more. Choosing which one is right for you depends on a number of factors that vary depending on the nature of your application.

![Image title](https://dzone.com/storage/temp/9601900-system-illustration.png)

  * **Compatibility**: Does the MCU support the sensors and actuators you want to use? Depending on your sensors and actuators, you might need many or just a few ports. You'll want to make sure that you have enough input/output ports available.

  * **Architecture:** Is the architecture sophisticated enough to handle the complexity of your program? Most applications use either ARM, MIPS, or X86. Choosing one depends on the functional requirements of your application and how much computing power your system needs.
  * **Memory**: Does the MCU come with enough memory - RAM and Flash - for your program? It is highly recommended that you choose an MCU with a comfortable amount of extra memory for future updates. This will save you time, money, and some major headaches in the long run!
  * **Availability**: Can you easily get the MCU that you want and in the quantity that you need? This is important to consider at the beginning of the process, especially if you plan on scaling up your system later on.
  * **Power**: How much power will the MCU need? Will it need to be wired or can you use batteries? Energy efficiency is extremely important to consider for industrial IoT applications because you'll want to minimize the need for sending maintenance crews to inspect edge infrastructure.
  * **Cost**: How much does each unit cost? Does the price make sense based on the value it will deliver? Again, you'll want to think about scaling the project up later on. Make sure that your IoT budget support including more of the MCUs you choose.
  * **Development Kit**: Is a development kit available? Development kits are an excellent way to get started with the MCU you choose because they are designed to give customers an out-of-box experience. This will make the development of your IoT application much easier!
  * **Development Support**: Is good documentation for your MCU available? What is the community surrounding this board like? These factors are crucial in order to make informed decisions on how to use your MCU properly. A good online community can help guide you when you are stuck or encounter a problem with your implementation.

At the end of the day, you can and should do your research in order to make an informed decision. But, as with all new technology, you'll learn as you experiment.
