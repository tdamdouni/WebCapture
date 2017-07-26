# How to be an automobile software engineer — Part 3

_Captured: 2016-03-22 at 12:39 from [medium.com](https://medium.com/@viktorschepik/how-to-be-an-automobile-software-engineer-part-3-2a6df6582c06#.7peo3cvrj)_

#### The architecture of a microcontroller

![](https://cdn-images-1.medium.com/max/800/1*5l32i7xhXw0fx0oNMhvCfA.png)

The last part of this series was named „What drives automotive software architecture?" and I haven't emphasized the aspect of a constrained microcontroller yet. The architecture and the constraints of a microcontroller affect the software architecture massively. In this part of the series I want you to get a feeling about this aspect of automobile software engineering.

In case you missed Part 2:

Microcontrollers are CPUs with some extras which are often called peripherals. These peripherals are located on the same chip as the CPU and take care of connections to the network, directly connected sensors and to devices like electrical motors.

You typically connect some sensors like temperature sensors directly to the A/D converter (Analog/Digital) of the microcontroller. The A/D converter peripheral converts analog voltage values like 3.5 V to a digital number like 35. And they can do this periodically and very fast, e.g., every 100 microseconds.

Want to know a sample usage for A/D conversion? Here it comes: Software in a car will monitor the battery voltage in order to shut down nicely when the voltage goes down below a critical boundary. Otherwise, some hardware components will stop working correctly.

Some time ago I had to implement such a monitor component and I had to consider several different low-voltage-boundaries. There was one boundary where we had to stop network communication because the CAN component would not work correctly. Another one determined when we had to put the electric motor on standby because otherwise it would pull down the power supply of other devices in the car. Then you need another voltage boundary for going back to normal behavior. If I had chosen the same boundary for going up and down the steering system would bounce between off and on because battery voltage often jitters. A state machine with separate conditions for going up and down lends itself to be the solution to this problem.

![](https://cdn-images-1.medium.com/max/800/1*RMjIUcvd6B2rnUvW3NLNAg.png)

> _Voltage Monitoring State Machine_

The mentioned battery voltage boundaries are fictitious. Any resemblance to real cars, still driving or crashed, is purely coincidental. When you plot battery voltage of a car you get a wiggly line depending on the current state of other systems in a car (e.g. the combustion engine). The following battery voltage plot shows when the system changes state. You will surely figure out how it treats that "voltage jittering".

![](https://cdn-images-1.medium.com/max/800/1*QFKglRPTQVBEZvcCEpNwew.png)

> _Voltage Monitoring Behavior_

Let's go back to our microcontroller. Almost all input peripherals of a microcontroller put their data into buffers which can be read by the software by reading values from certain memory addresses. That means that the peripherals including their buffers are mapped into the microcontroller memory at certain addresses. The way to deal with this in C programming is to define a pointer to, let's say, the A/D data:

You can control and configure the peripherals also by writing data to certain memory addresses.

Overall it is quite easy for the software to access and control the peripherals of a microcontroller. At the first glance. The challenges arise when you stumble over the timing aspects of these peripherals.

#### Constraints of a microcontroller

If you are used to web or desktop application development you will be shocked to hear about the resources available to embedded developers. Two prominent examples of microcontrollers for use in steering systems are the Renesas V850 family

and the Freescale MPC5xxx family

The CPU runs e.g. with 80-160 MHz and 40-80 KB RAM! Yes, it's KB and not GB. Compare the RAM size of the microcontroller (80 KB), shown as a white pixel, with that of a normal PC (8GB), shown as the blue area:

![](https://cdn-images-1.medium.com/max/800/1*WIsEqhfE8vi7RjXkA_1cTw.png)

> _81,920 (white area) vs. 8,589,934,592 Bytes (blue area)_

Therefore, a JVM is not quite feasible for this kind of microcontroller. It is plain old C that is used as a programming language. And a lot of stuff that is normally done during runtime is determined before the compiler runs. The operating system is configured exactly for one system and the configuration results in generated source code. You cannot spawn a process or thread during runtime. The same is true with memory allocation, especially in safety-critical systems. There is no memory allocation during runtime since you could run out of memory. That way you would kill your software application and affect the car driver in an unpleasant way. Instead, you try to predetermine everything that will be needed in the form of resources like memory and CPU power.

Perhaps you wonder how you could load a program into 80 KB of RAM and run it. The truth is that the program is stored in ROM (Read Only Memory) and executed from there. It is not loaded into RAM as it happens usually in PCs. ROM size is e.g. 1 MB so that you can store a decent program size and your constant values there.

Additionally, you find NVRAM (Non-Volatile RAM) inside of a microcontroller where your program can store values that you need after a switch-off / -on.

#### Implications

What are the implications of the architecture and constraints of microcontrollers?

  * You as an architect need to care about a lot of low-level details.
  * It is tough to stick consequently to layers in software architecture.
  * The software build process gets quite complex.
  * Developer tools like profilers that must enhance the program in order to work are constrained and difficult to integrate.
  * And some more …

I hope you got a feeling about some forces driving the software architecture of automobile software. It would be too tedious to present all of them. You have to experience them as always in software engineering, regardless of the type of software you are building.
