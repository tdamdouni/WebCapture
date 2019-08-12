# Teardown Tuesday: Bluetooth Keyboard

_Captured: 2018-11-15 at 18:18 from [www.allaboutcircuits.com](https://www.allaboutcircuits.com/news/teardown-tuesday-bluetooth-keyboard/)_

Touchscreens may be popular but physical keyboards are still one of the preferred methods for text input, especially when it's wireless. In this teardown, we will look at the innards of a Bluetooth keyboard.

### The Keyboard

The Bluetooth keyboard uses the traditional QWERTY layout, various function buttons, and a touchpad in the middle for mouse control (making the keyboard more of a key-mouse, really).

![](https://www.allaboutcircuits.com/uploads/articles/Bluetooth_Keyboard_-_1_The_Keyboard.JPG)

> _The Bluetooth keyboard_

The keyboard is surprisingly small (approximately 20cm in length) and all the buttons on the keyboard are tactile and not rubber membrane.

_![](https://www.allaboutcircuits.com/uploads/articles/Bluetooth_Keyboard_-_2_Size_comparason.JPG)_

> _Size comparison of the Bluetooth keyboard_

The front of the keyboard contains a USB charging port and the back contains various other buttons including on and off.

![](https://www.allaboutcircuits.com/uploads/articles/Bluetooth_Keyboard_-_7_USB_Charge_Port.JPG)

> _USB charging port_

_![](https://www.allaboutcircuits.com/uploads/articles/Bluetooth_Keyboard_-_8_Back_Buttons.JPG)_

> _Back buttons_

The underside of the keyboard contains the logo of the company that produced the device (Jelly Comb) and there are no visible screws or fittings keeping the unit together.

_![](https://www.allaboutcircuits.com/uploads/articles/Bluetooth_Keyboard_-_6_Logo.JPG)_

> _Back of the keyboard_

### Internal Access and the Battery

Getting access to the internals of the keyboard was very easy. Only a small flat head screwdriver was needed to pry the bottom off. The battery and internal PCB are immediately revealed including some interesting ICs and PCB routing techniques.

![](https://www.allaboutcircuits.com/uploads/articles/Bluetooth_Keyboard_-_9_Back_cover_off.JPG)

> _Cover removed_

_![](https://www.allaboutcircuits.com/uploads/articles/Bluetooth_Keyboard_-_10_Battery_Removed.JPG)_

> _Battery removed from the main PCB_

The PCB, itself, is held down with four incredibly tiny screwdrivers that were nearly problematic (luckily, I had a flathead small enough). Interestingly, the PCB has boxes on the component legend that indicate the position of the screws (probably to help the production lines know where to put the tiny screws).

_![](https://www.allaboutcircuits.com/uploads/articles/Bluetooth_Keyboard_-_20_Screw_Size.JPG)_

> _Size comparison of the screws that hold the PCB down_

The battery, itself, is a lithium-ion type but the battery itself has no printed information as to its voltage output or capacity. Considering the small modern ICs used on the keyboard and the use of USB charging, it is fair to say that the voltage supply pins on the ICs will be approximately 3.3V. Therefore, the battery could be a 3.7V with a 1Whr (~330mAh) capacity.

##### ![](https://www.allaboutcircuits.com/uploads/articles/Bluetooth_Keyboard_-_19_Battery.JPG)

> _The unidentified lithium-ion battery_

  


### The Main PCB

The PCB has two main ICs visible from the underside, many ground/power planes, and other components such as a USB connector, capacitors, resistors, and various semiconductors.

The left side of the PCB shows many horizontal traces with multiple via points as well as various test points. The horizontal traces are most likely for the routing of the keyboard matrix that will be found on the opposite side of the PCB.

This PCB appears to be made of two layers which explains the use of traces and planes on the same side. If a four-layer board were used, the PCB would most likely have used either the inner layers as power/ground planes and the output layers for traces or the other way around.

![](https://www.allaboutcircuits.com/uploads/articles/Bluetooth_Keyboard_-_11_Left_PCB_Side.JPG)

> _The horizontal traces, test pads, and various horizontal traces_

The center of the PCB shows a really interesting pattern (located directly under the touchpad) of a hatched ground plane as opposed to being filled.

![](https://www.allaboutcircuits.com/uploads/articles/Bluetooth_Keyboard_-_12_Center_of_PCB.JPG)

> _The main IC and the large hatched ground plane_

This area of the PCB also houses an IC with the identification [eKT2101](http://www.emc.com.tw/eng/8bit_prod_dsc.asp?gid=&tid=000004&tt=8bit_tphs_ds&nn=Touch+Sensor+IC+-+High+Sensitivity) QN32 which, thankfully, is an off-the-shelf capacitive touch IC microcontroller. The SoC has an 8-bit RISC microcontroller and includes many peripherals including an SPI slave port and an I2C slave port. The chip, while containing an internal CPU, is more of a sensor than a microcontroller as it is accessed externally by other devices for capacitive readings. Nearby the IC are also various pads including SCL and DATA which suggests that this device is in I2C mode as opposed to SPI mode. This also potentially allows for a user to hack this device and take readings from the IC.

_![](https://www.allaboutcircuits.com/uploads/articles/Bluetooth_Keyboard_-_14_IC_1.JPG)_

> _The eKT2101 capacitive touch IC_

The second major IC on the underside of the PCB is located on the far right side and has the identification of BEKEN [BK3231Q](http://www.bekencorp.com/en/Botong.Asp?Parent_id=2&Class_id=8&Id=85). This IC is a Bluetooth microcontroller containing many peripherals including a timer, PWM, WDT, ADC, UART, I2C, SPI, and GPIO. The core of the microcontroller is an [ARM968E-S](http://infocenter.arm.com/help/topic/com.arm.doc.ddi0311d/DDI0311.pdf) and has 32KB RAM and 256KB of FLASH ROM. It is becoming increasingly common for designers to integrate their entire design into a single wireless controller as doesn't require a separate module, saving money.

![](https://www.allaboutcircuits.com/uploads/articles/Bluetooth_Keyboard_-_13_Right_PCB_Side.JPG)

> _The Bluetooth area of the PCB_

The controller shown here also has two pads nearby labeled as RX1 and TX1, which will most likely be for debugging (such as viewing AT commands). The IC also has a missing J4 component, which is probably the remanence of the prototyping stage where a small four-way jumper switch used to be which may have changed internal options for testing and programming of the controller.

_![](https://www.allaboutcircuits.com/uploads/articles/Bluetooth_Keyboard_-_16_Antenna.JPG)_

> _The IC and other external components including the PCB antenna_

The USB charging port has various components nearby, including three resistors, two capacitors, and a six-pin surface mount device. The device has the identification of HXN MH which does not return any credible answers as to what the IC actually is.

However, considering the use of two capacitors (one on the input and one on the output) and a few resistors, this device may be a lithium-ion charging IC that uses an internal linear regulator whose voltage output depends on the external resistors. Linear regulators, while potentially wasteful, would work well in this circuit considering that the power comes from an external USB host (most likely a phone charger) where power is abundant.

![](https://www.allaboutcircuits.com/uploads/articles/Bluetooth_Keyboard_-_18_USB_Part.JPG)

> _The USB charging port and power related components_

### Topside of the Main PCB

The PCB is held down by four screws and multiple tabs that make it difficult to removed. Thankfully, this is a teardown and not a repair so a small bit of force is entirely acceptable here.

The top side of the PCB shows many surface-mount tactile switches, a few LEDs, and the capacitive touchpad. The touchpad, itself, consists of a plastic layer with an interesting array of exposed traces in a diamond pattern underneath.

![](https://www.allaboutcircuits.com/uploads/articles/Bluetooth_Keyboard_-_21_Underside_PCB.JPG)

> _Top side of the PCB showing the buttons and touch pad_

_![](https://www.allaboutcircuits.com/uploads/articles/Bluetooth_Keyboard_-_22_Buttons.JPG)_

> _Close up of the tactile switches_

The plastic layer is easily peeled away and the exposed metal underneath is tinned plated. While it may seem that the tin plating is orange in color, it is actually silver and just reflecting the light off the roof which is made of chipboard.

_![](https://www.allaboutcircuits.com/uploads/articles/Bluetooth_Keyboard_-_24_Under_touch_pad.JPG)_

> _Touchpad with the plastic removed_

### Transparent Layer View

One feature that would be fantastic to have on teardowns would be an X-ray view of the PCB. Unfortunately, I do not own such equipment but the next best thing that can be offered is a bright light being shown through the PCB to give perspective on routing and traces.

![](https://www.allaboutcircuits.com/uploads/articles/Bluetooth_Keyboard_-_26_False_XRay.JPG)

> _The Bluetooth IC area_

_![](https://www.allaboutcircuits.com/uploads/articles/Bluetooth_Keyboard_-_27_False_XRay2.JPG)_

> _Another PCB layer image_

_![](https://www.allaboutcircuits.com/uploads/articles/Bluetooth_Keyboard_-_28_False_XRay3.JPG)_

> _Bluetooth tooth antenna and tactile switches_

### Summary

Once again, we see another demonstration of a near single-chip solution. Future devices could possibly only consist of one semiconductor and IO devices. Such solutions, while usually specific, are incredibly cheap and make production very easy to perform. Single-chip solutions also help with electromagnetic compatibility control as most of the noise is restricted to one part, its powerlines, and its in and outgoing connections.

**Next Teardown: [Mini Network Router](https://www.allaboutcircuits.com/news/teardown-tuesday-mini-network-router/)**
