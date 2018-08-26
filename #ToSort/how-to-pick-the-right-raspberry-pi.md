# How to Pick the Right Raspberry Pi

_Captured: 2018-05-19 at 19:46 from [www.digikey.com](https://www.digikey.com/en/maker/blogs/2018/how-to-pick-the-right-raspberry-pi?utm_source=twitter&utm_medium=Social&utm_campaign=makerpost)_

### ![How to Pick the Right Raspberry Pi](https://www.digikey.com/-/media/MakerIO/Images/blogs/2018/How%20to%20Pick%20the%20Right%20Raspberry%20Pi/Cover.jpg?la=en&ts=4fff9acf-9a7f-4ded-a194-589e6dc9ac45)

Raspberry Pi models are great, but there are several to choose from. So, which one should you choose for your next Raspberry Pi project?

### Part Numbers

### There's No Such Thing As _the_ Raspberry Pi!

When people talk about the Raspberry Pi, they usually have this idea of a small credit card computer that has various I/O ports and can replace a PC for most typical applications, including document writing, surfing the web, and writing programs. However, as it turns out, there is no single computer called the Raspberry Pi! Raspberry Pi refers to a series of computers produced by the Raspberry Pi Foundation.

So, you have decided that you are going to design and build a Raspberry Pi project, but you are not sure which Pi is right for you. Luckily for you, in this article, we'll look at different Pi models on the market, compare them, and see how each Pi is unique in its own way.

### Decide Your Requirements

When you are in the process of making a decision, you usually write down your requirements; computers are no exception! Your first task is to determine what is most important for your project. Such requirements can usually be reduced to the following list.

  * Speed: Processing power of the system
  * Memory: How much RAM and ROM or HD space the system has
  * Size and weight: The physical size and weight of the computing system
  * Cost: The financial cost of the system
  * I/O: How much I/O support is available

### Speed

Speed is sometimes one of the most important factors in a computing scenario. The faster a computer is, the more work it can do before slowing down and becoming unresponsive. The Raspberry Pi range of computers is very fast, compared to microcontrollers such as PIC, AVR, and STM, but there is a noticeable difference between Pi computers.

The first Raspberry Pi computer, the model B, features a quad-core 32-bit ARM Cortex processor, whereas the cheaper version, which was released shortly after the B, the model A, has a single-core 700MHz ARM processor. This means the Raspberry Pi B can do four things simultaneously across its separate cores, but tasks on a single core on the model B will be approximately 30 percent faster than on the A (that, however, is one big assumption for many reasons). The later models, such as the Raspberry Pi 3 B, have a 1.2Ghz 64-bit quad-core processor, which is not only faster than the Raspberry Pi 2, but it can handle larger data sizes. Other Pi computers, such as the Compute range, have similar core speeds, ranging from 700MHz to 1.2GHz.

### Memory

Memory can be critical in a computing environment if you need to run large programs. For example, operating systems are notorious for using large amounts of RAM. So, if one is going to be used, maximizing RAM would not be a bad move. The Raspberry Pi A computer has between 256MB and 512MB of RAM, whereas the Raspberry 2 and 3B have 1GB; however, this is shared with the GPU. The Compute devices' RAM size ranges from 512MB to 1GB, with the more advanced computers having the most memory. Therefore, if RAM is important, you may need to look at the top-of-the-range Raspberry Pi computers, such as the Raspberry 3 B or Compute Module 3.

### Size and Weight

For most users, this requirement may not apply, because all Raspberry computers are already very small and light. However, some projects may have strict requirements, in which case the Raspberry Pi Compute may come out on top. However, the Compute modules come in DDR like packages, which means they need a host PCB to fit into so they can be connected to I/O devices, as well as power. This may end up being larger and heavier than just using a Raspberry Pi A or B. The Raspberry Pi Zero is the smallest Pi computer available that also contains I/O, including USB, HDMI, and an SD card slot. However, the Zero has lower RAM and processing capabilities than the Raspberry 3 B.

### I/O

If you want your computer to perform office tasks, such as writing letters and sending emails, then using a laptop or PC will be the ideal choice. Raspberry Pi computers are used usually because there is a need for I/O. The Raspberry Pi A and B computers are very good for connecting to external circuits and devices since they contain pin headers. The 1 A has 8 GPIO, while the +1 A and B computers have 17 GPIO. The Compute module has the most GPIO, with up to 46 GPIO, which make them useful for industrial applications. Interestingly, the Raspberry Pi Zero, despite its cost and size, has 17 GPIO, just like the model B.

### Networking

Comparing GPIO, memory, and CPU processing power is all fine and good, but arguably the most important difference between the different Raspberry Pi computers is their network capabilities. The first models, the A and A+, lack any networking capabilities at all, whereas the model 1 B and 2 B have an ethernet port. But not every location has ethernet access, which is where the model 3 B comes in with an integrated wireless network adaptor. Users of the model 3 B who wanted to pass CE and FCC conformity had some issues due to the integrated Wi-Fi IC, which is why the Raspberry Pi foundation developed the more recent model 3 B+, which houses the Wi-Fi circuitry in a metal shield and is designed to meet CE and FCC requirements. The Compute module and Zero models do not come with internet capabilities, with the exception of the Zero Wireless, which also has an integrated Wi-Fi module.

### Models

When looking at the different Raspberry Pi computers available, you may notice that some models have a "+" in their name. This inclusion usually indicates improvements in the design. For example, the Raspberry Pi model A has 256MB RAM, whereas the Raspberry Pi model A+ has 512MB RAM, a microSD slot, and more GPIO. The Raspberry Pi 2 Model B has two USB ports and two mounting holes, whereas the Model B + has four USB ports, four mounting ports, a faster CPU, increased GPIO, and less power consumption.

### So, Which One?

So after exploring these requirements, which Pi should you pick?

**Raspberry Pi Model A:** Use this model for a low-cost project that needs a complete computer with no networking capabilities and decent I/O support

**Raspberry Pi Model B:** This model can be used for a project where price is no object and the most powerful Pi is needed. This model also contains easy-to-use I/O, so it is suitable for first Pi projects.

**Raspberry Pi Compute:** This model is best for industrial applications where many I/O lines are needed. This model also maintains strong CPU capabilities.

**Raspberry Pi Zero:** This model is best for an ultra low-cost, tiny-space-constrained project that requires a fully functioning computer and would benefit from wireless connectivity.

**Rapsberry Pi Platform** **RAM** **Processor** **USB** **Ethernet** **Wi-Fi** **Bluetooth** **HDMI** **Other Video** **MicroSD**

[Rapsberry Pi A+](https://www.digikey.com/product-detail/en/raspberry-pi/RASPBERRY-PI-A/1690-1006-ND/6152805)
512MB
700 MHz ARM11
1 Port
-
-
-
Yes
DSI, Composite
Yes

[Rapsberry Pi B+](https://www.digikey.com/product-detail/en/raspberry-pi/RASPBERRY-PI-B/1690-1014-ND/6235381)
512MB
700 MHz ARM11
4 Ports
10/100Mbps
-
-
Yes
DSI, Composite
Yes

[Rapsberry Pi 2 B](https://www.digikey.com/product-detail/en/raspberry-pi/RASPBERRY-PI-2-MODEL-B/1690-1005-ND/6152804)
1GB
900 MHz Quad-Core ARM Cortex-A7
4 Ports
10/100Mbps
-
-
Yes
DSI, Composite
Yes

[Rapsberry Pi 3 B](https://www.digikey.com/product-detail/en/raspberry-pi/RASPBERRY-PI-3/1690-1000-ND/6152799)
1GB
1.2 GHz, Quad-Core 64-bit ARM Cortex A53
4 Ports
10/100Mbps
802.11n
4.1
Yes
DSI, Composite
Yes

[Rapsberry Pi 3 B+](https://www.digikey.com/product-detail/en/raspberry-pi/RASPBERRY-PI-3-MODEL-B/1690-1025-ND/8571724)
1GB
1.4 GHz 64-bit ARM Cortex A53
4 Ports
300/Mbps/PoE
802.11ac
4.2
Yes
DSI, Composite
Yes

[Rapsberry Pi Zero](https://www.digikey.com/product-detail/en/pi-supply/RPI-030/1910-1001-ND/8136034)
512MB
1 GHz single-core ARM11
1 Micro USB
-
-
-
Mini-HDMI
-
Yes

[Rapsberry Pi Zero Wireless](https://www.digikey.com/product-detail/en/pi-supply/RPI-029/1910-1000-ND/8136033)
512MB
1 GHz single-core ARM11
1 Micro USB
-
802.11n
4.1
Mini-HDMI
-
Yes
