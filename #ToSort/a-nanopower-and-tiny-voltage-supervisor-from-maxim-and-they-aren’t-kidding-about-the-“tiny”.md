# A nanoPower and Tiny Voltage Supervisor from Maxim (and They Aren’t Kidding about the “Tiny”)

_Captured: 2017-11-18 at 14:18 from [www.allaboutcircuits.com](https://www.allaboutcircuits.com/news/nanopower-tiny-voltage-supervisor-maxim-integrated-max16140/)_

In this article, we take a look at the MAX16140, a tiny device that uses a tiny amount of current, but one that promises a lot.

The chosen term "tiny" is an understatement when describing the physical size of the [MAX16140](https://datasheets.maximintegrated.com/en/ds/MAX16140.pdf). At 0.78mm × 0.78mm × 0.5mm, this IC is unbelievably small. If you're looking for a voltage supervisor to be hand-placed, just keep on looking because--unless you're a brain surgeon or your name is Data, from _Star Trek--_you most likely won't possess the steady hand or the patience needed for placing this teeny-tiny IC, meaning you'll definitely need pick-and-place automation equipment.

![](https://www.allaboutcircuits.com/uploads/articles/MAX16140_.jpg)

> _The MAX16140 (not to scale). Image from Mouser._

The advertised tiny--or _nanoPower_, as Maxim refers to it--amount of quiescent current required to operate this device is a mere 370nA. Keep in mind, however, that this typical spec is valid only at 25°C. But still, the quiescent current levels at elevated temperatures and voltages are impressive nonetheless (see image below).

##### ![](https://www.allaboutcircuits.com/uploads/articles/MAX16140_temp_vs_current.jpg)

> _Figure 1. Supply Current vs. Supply Voltage. Image taken from the datasheet._

### Factory-Programmed ICs

Although this voltage supervisor has a relatively wide operating voltage range, from 1.7V to 5.5V, this IC can't monitor supply voltages up to 5.5V. Rather, it's promoted as being able to monitor voltages ranging from 1.7V to 4.85V with very small, impressively small, increments of 50mV. The downside is that this device is not made for end-user customization; you must order the pre-programmed (i.e., factory-programmed) IC with your desired settings. And if you're hoping to pinpoint the exact voltage threshold for your design through trial and error, then you would need to order a variety of different, pre-programmed, voltage threshold settings. Fortunately, Maxim has made this selection process easy via their Selector Guide (see image below).

![](https://www.allaboutcircuits.com/uploads/articles/MAX16140_selector_guide.jpg)

> _Figure 2. The selector guide. Image taken from the datasheet._

### Be Careful with Copy and Paste

Maxim has been generous with providing detailed information about this device, including reset, voltage threshold, and time-delay specs, as well as explanations of the IC's pins (technically called "bumps"), and application information such as power supply bypassing and grounding ([page 9](https://datasheets.maximintegrated.com/en/ds/MAX16140.pdf#page=9) of the datasheet).

However, they made a goof with their supply current vs. supply voltage graph. Apparently, this device can operate from a _supply voltage_ of -40V to an astounding 125V! See figure below. They forgot to re-label the graph's title to Supply Current vs. Temperature, and then also to change the graph's x-axis label.

![](https://www.allaboutcircuits.com/uploads/articles/MAX16140_supply_current_vs_voltage-temperature.jpg)

> _Figure 3. A documentation goof (-40 to 125 supply voltage range). Image taken from the datasheet._

### Manual Reset--A Useful Feature

It's nice to see that Maxim realizes that these ICs, when added to a design, will eventually require manual testing. The manual reset input (MR) feature was added specifically for this purpose.

According to the [datasheet](https://datasheets.maximintegrated.com/en/ds/MAX16140.pdf), the factory-programmable manual reset input capability allows "the operator, a test technician, or external logic circuit to initiate a reset" via a rising-edge, a falling-edge, an active-low, or an active-high input signal. From my own experience as a test and validation engineer, I can tell you that these MR options will be very valuable when ringing out bugs or when approaching other troubleshooting, or management-driven feature creep…smiley face, issues. Refer to Figure 2 above for the factory-programmable MR input configuration options.

### Wafer-Level Package Information

If you've never used a WLP (wafer-level package)--this is the magic that allows these devices to be so tiny--then you'll want to get educated on how to properly design your PCB for accommodating them, to make sure your board house has the capabilities for making appropriate landing pads, and (this is critically important) to ensure your assembly house (i.e., the pick-and-place machines) can confidently handle and place these devices. Fortunately, Maxim has provided, within the datasheet, a WLP land pattern application note. Unfortunately, the datasheet link DOESN'T WORK! Luckily, I was able to quickly locate the [app note](https://pdfserv.maximintegrated.com/en/an/AN1891.pdf) thanks to Mr. Google.

One final note: I'll share a lesson with you that I gained through experience when using WLPs. It's always a good idea, actually a great idea, to closely surround a WLP device with other devices (resistors, caps, other more robust ICs, etc.). The goal here is simply protection--WLPs can easily (and literally) be knocked off a PCB merely by handling, even carefully handling, the PCB. And if you don't have any spare or otherwise convenient devices to protect the WLP with, then add some inexpensive surface-mount resistors or caps, and just leave their terminals unconnected.

Have you had a chance to use these new voltage supervisors? If so, leave a comment and tell us about your experiences.
