# Embedded vs. Non-Embedded Operating Systems

_Captured: 2018-07-03 at 23:21 from [dzone.com](https://dzone.com/articles/embedded-vs-non-embedded-operating-systems)_

What are embedded devices? If you have used electronic devices, such as a smartphone or a home appliance, chances are you have already come across these devices. In simple terms, embedded devices are "simple" devices designed to perform a specific task. In embedded development, these devices play an irreplaceable role in driving or running a simple single-task environment.

## Device Driver Without an Operating System (Bare Metal Devices)

Not every computer needs an OS to run; in many cases, an OS is not necessary. For functions that are relatively simple and for which the control is not complicated, single-task architectures are perfectly capable of supporting their work. These tasks may involve turning a device on/off or keeping track of time (with a quartz timer).

Some real-life examples of embedded systems include transit card readers, refrigerators, microwaves, and simple mobile phones. Other than these, computers that do not require complex tasks, such as multi-task scheduling, file systems, or memory management, do not depend on OS.

The typical software architecture in such systems comprises of an infinite loop device interruption test, polling the device. Bare metal devices achieve something a bit similar to a single chip device or microcontroller (MCU). If the bare metal device has a driver included, it should be competent for microcontroller work.

In such systems, although there is no operating system, a device driver must still exist. In general, each device driver gets defined as a software module containing .h files and .c files. The former represents the device-driven data structure and declares external functions, and the latter implements the device driver. Their primary purpose is to configure the GPIO (General-Purpose Input/Output), serial control register, and serial I/O register. We define these configurations with their functions, such as serialSend, for sending data from the serial port.

If other modules need to use this device, all you need to do is add the device-driven header file serial.h. Subsequently, you call one of the external interface functions. For instance, if we want to send the string "Hello World" from the serial port, we use the function SerialSend ("Hello World", 11).

Thus, in the absence of an operating system, the device-driven interface is submitted directly to the application software, and the application software directly accesses the device-driven interface without crossing any hierarchy. Device drivers also include interface functions that work directly with the functionality of the hardware without any additional functionality.

Some people feel it is unreasonable to be asked to design a single task system, which is device-driven, at the same level as a specific application software module (i.e., the application also gets implemented in serial.c, for example). This is apparently unreasonable and does not meet the requirements of high-cohesion low-coupling in software design.

Another "unreasonable" design, according to some, is to directly manipulate hardware registers in the application. For example, a single main.c, all functions get implemented in a single function package and no other interface or package function is required, rather than a separate design driver module. The purpose of this design is that the system does not exist or it fails to take full advantage of reusable driver code.

## Operating Systems With Device Drivers

The device drivers in non-embedded operating systems run directly on the hardware and do not get associated with any operating system. When the system contains the operating system, what will the device driver be like?

Firstly, a non-embedded operating system's device-driven hardware's operation may still be essential. Without this part, the device driver and the hardware cannot interact with each other.

Secondly, we also need to incorporate device drivers into the kernel. To practically achieve this convergence, we must design the interface to the operating system kernel in all device drivers. The OS dictates these kinds of interfaces and is structurally and independently device-specific for a class of devices.

Thus, when the system has an OS, the device driver becomes a link connecting the hardware and the kernel. The presence of an OS will inevitably require device drivers to attach more code and functionality, turning the single "drive hardware device action" into a module for interacting with the hardware from inside the operating system.

It is presented as an operating system API and will no longer provide a direct interface for application software engineers. After getting an operating system, the device driver becomes increasingly more complicated. The question is, what should an operating system be doing in this case?

First of all, a complex software system needs to deal with multiple concurrent tasks. If there is no operating system, it is challenging to accomplish multi-task concurrency. Second, operating systems give us memory management mechanisms.

To use a typical example, most MMU-based processors, Windows, Linux, and other conventional operating systems support each process to access 4GB of memory individually. To sum up, what are the advantages an OS brings to the device driver?

The OS creates problems for the device driver to achieve the purpose of providing a convenient operation to higher level applications. If all device drivers are designed with the idea that the operating system provides a device-independent interface, the application will have access to a variety of devices using a unified system call interface. For UNIX's VxWorks, Linux, and other operating systems, applications can read and write files and access different character devices and block devices through the write(), and read() functions. This is regardless of the specific type of device and work, which becomes extremely convenient.

## Conclusion

To conclude, we discussed the design and features of both embedded and non-embedded operating systems. We mentioned the types of computers which require an OS to perform tasks, especially multi-tasking systems, and the ones which do not need an OS to work, such as refrigerators and microwaves. Moreover, we talked about the functionality and behavior of device drivers in the presence or absence of an OS in the system.

### Like This Article? Read More From DZone

Topics:

linux ,architechture ,trends ,internet of things ,smart devices ,IoT ,bare metal servers ,device drivers
