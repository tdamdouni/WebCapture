# What should be a good language interpreter to implement into a Microcontroller

_Captured: 2017-01-19 at 21:14 from [forum.omz-software.com](https://forum.omz-software.com/topic/3791/what-should-be-a-good-language-interpreter-to-implement-into-a-microcontroller/3)_

Hello [@Buafeer](https://forum.omz-software.com/user/buafeer). I am a hardware design engineer and have used all different types of microcontrollers.  
The atsam4s16b is a very good microntroller. With this device, you are kind of tied to C. Atme'ls design studio offers the option of C++ but that may be it. <http://www.atmel.com/tools/ATMELSTUDIO.aspx>

The first thing I can tell you is that if you are wanting to use a microcontroller and are trying to avoid C, then you are in trouble. C is the primary language for embedded microcontrollers as it has low overhead. The biggest reason for using C on a microcontroller is the small latency between executing a function and access to the physical IC pins. For example, if a microcontroller had the duty of responding to an input super fast (micro or milliseconds), say HI-FI audio streaming, python would be less able to do this on a device running at 120MHz, where C can do it efficiently. If there was an application that required even faster execution, say, airbag deployment in an automobile accident (micro or nano seconds), C wouldn't even be fast enough, and that is where assembly language comes in handy. On product designs, I have combined microcontrollers with raspberry pis to get the best of both worlds, especially if advanced graphics, USB or ethernet are required.

Remember, microcontrollers have tight resources such flash memory in the KB range. For example, the premium PIC Microchip microcontroller (PIC32MX) has only 512KB of 32 Bit flash and that is considered good. Loading a high level language on one (which is not easily possible) would eat the flash up in no time. If you absolutely want to stay away from C, then you need an embedded computer such as the Raspberry Pi or the official Micro Python board as [@ccc](https://forum.omz-software.com/user/ccc) shown. This is why choosing the right microcontroller is important. In the last few years, RToS (real time operating systems) have become popular on microcontrollers, but have expensive IDEs and require very high end microcontroller hardware running like at 400Mhz, as sold by Renesas and ST Microelectronics. It all depends on the application. The old classic iPod with capacitive touch wheel was controlled by a Cypress Semiconductor microcontroller using C. The new Apple pencil uses a ST Microelectronics STML151UCY6 Ultra-low-power 32-bit RISC ARM-based Cortex-M3 MCU written in a lower level language.

Below are some microcontroller platforms that make use C exclusively:

<https://www.arduino.cc/> \- the easiset way to use C on a microcontroller, lots of online examples and community support.

<http://www.cypress.com/products/32-bit-arm-cortex-m-psoc> \- uses the least amount of C as there is a drag and drop interface.

<https://www.microchip.com/design-centers/32-bit-mpus> \- very popular and lots of options, but very C heavy.

To avoid C and stay embedded:  
<https://store.micropython.org/#/store> \- a microcontroller with Python.

<https://www.raspberrypi.org/> \- A real embedded conputer running python.
