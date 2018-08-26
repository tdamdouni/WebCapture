# Generating a High DC Output Voltage from a Low Input Supply

_Captured: 2018-02-23 at 18:59 from [www.digikey.com](https://www.digikey.com/en/articles/techzone/2018/jan/generating-a-high-dc-output-voltage-from-a-low-input-supply?utm_source=facebook&utm_medium=social&utm_campaign=tzpwrsol)_

Contributed By Digi-Key's North American Editors

Driven by portable and wearable applications, the trend in many designs is moving firmly in the direction of supply voltages of 3.6 volts or lower. However, many portable devices have specific functions that require higher voltages, requiring designers to up-convert to the required levels as efficiently as possible through optimal implementation of DC-DC boost converters.

This article will review the purpose of boost DC-DC regulators and describe their topology. It will then introduce example devices and discuss the design techniques and tradeoffs needed to develop the optimum design for a portable or wearable application.

## The role of DC-DC boost converters

A typical wearable or otherwise portable device uses a Li-ion cell with a nominal output of 3.6 volts DC. Most battery-powered applications rely on one or several Li-ion cells connected in series as their primary supply voltage. While this suffices for many applications, laptops, tablets, and other mobile devices have specific functions that require much higher voltages.

Examples include drivers for white light emitting diode (LED) backlights, RF transceivers, precision analog circuits, and bias circuits for the avalanche photodiodes (APDs) found in optical receivers. A step-up or boost DC-DC regulator meets these application demands by transforming a low input voltage to a higher output voltage.

## A typical boost converter topology

The key components of a boost regulator are an inductor; a semiconductor switch, most commonly a power MOSFET; a rectifier diode; an integrated circuit (IC) control block; and input and output capacitors (Figure 1).

![Diagram of basic boost regulator configuration](https://www.digikey.com/-/media/Images/Article%20Library/TechZone%20Articles/2018/January/Generating%20a%20High%20DC%20Output%20Voltage%20from%20a%20Low%20Input%20Supply/article-2018january-generating-a-high-dc-fig1.jpg?ts=ae55d43d-2b1b-4bb2-bfa9-7f5d4f740bc2&h=181&w=500&la=en-US)

> _Figure 1: The basic boost regulator configuration, showing the direction of current flow when the switch is open and closed (Image source: Digi-Key Electronics, based on source material from Texas Instruments)_

With VIN applied and the power switch closed, current flows through the inductor along the blue path to ground. The inductor stores energy in its magnetic field. The diode is reverse biased, and the voltage across the output capacitor drops as its stored energy supplies the load.

Conversely, when the power switch is open, the current flows along the red path as the collapsing magnetic field generates a positive voltage and transfers the inductor energy through the forward biased diode to charge the output capacitor and supply the load.

By varying the duty cycle of the power switch, the control block maintains a constant output voltage in response to input voltage variations and changes in load. A resistive divider at the output can provide the control block with voltage feedback for adjusting the duty cycle and maintaining the desired output voltage value.

In addition to these basic functions, integrated designs also include a selection of protection features to guard against over temperature, an output short-circuit, an open load condition, input overcurrent, and more.

A common refinement to the basic circuit substitutes a second MOSFET for the diode. The second MOSFET functions as a synchronous rectifier, turning on when the power switch turns off. Its lower voltage drop reduces power dissipation, increasing the efficiency of the regulator.

A synchronous design is an advantage in a battery-powered device, in which higher efficiency equates to longer battery life. In addition, portables and wearables are usually space constrained, so boost converters for these applications often feature a high level of integration. Including the power components in the package restricts the current that can be delivered, but this is acceptable in a battery-powered design. Many such applications spend extended periods in shutdown mode, making ultra-low quiescent current consumption critical.

The [TPS610993YFFT](https://www.digikey.com/product-detail/en/texas-instruments/TPS610993YFFT/296-47105-1-ND/7596486) from Texas Instruments is an example of a low-power boost regulator (Figure 2). It is a synchronous device that consumes only one microampere (µA) of quiescent current, but it can deliver up to 800 milliamperes (mA) and generate an output voltage of 3.0 volts with an input voltage as low as 0.7 volts. The device is designed to maximize operating efficiency under light loads. It can operate with either an alkaline battery or a rechargeable type such as NiMH or Li-ion.

![Diagram of Texas Instruments TPS61099x family](https://www.digikey.com/-/media/Images/Article%20Library/TechZone%20Articles/2018/January/Generating%20a%20High%20DC%20Output%20Voltage%20from%20a%20Low%20Input%20Supply/article-2018january-generating-a-high-dc-fig2.jpg?ts=a1f100b2-7253-4d92-ab58-881bc6281eb7&h=145&w=550&la=en-US)

> _Figure 2: The TPS61099x family can deliver up to 5.5 volts from an input voltage of 0.7 volts. (Image source: Texas Instruments)_

The TPS610993 integrates both the power switch and the synchronous rectifier into a 6-ball wafer chip scale package (WCSP) measuring only 1.23 millimeters x 0.88 millimeters. Its small size makes it suitable for optical heart rate monitors, memory liquid crystal display (LCD) bias drivers, and similarly space-constrained applications. The device is a member of the TPS61099x family of products, with output voltages ranging from 1.8 volts to 5.5 volts.

To produce a higher voltage for smartphone camera flash circuits or battery-powered LED lights, [Microchip Technology's](https://www.digikey.com/en/supplier-centers/m/microchip-technology) [MCP1665](https://www.digikey.com/product-detail/en/microchip-technology/MCP1665T-E-MRA/MCP1665T-E-MRACT-ND/7928245) takes a different approach: it integrates a 36 volt, 100 milliohm (mΩ) NMOS power switch, but uses an external diode in a non-synchronous topology.

![Diagram of Microchip’s MCP1665](https://www.digikey.com/-/media/Images/Article%20Library/TechZone%20Articles/2018/January/Generating%20a%20High%20DC%20Output%20Voltage%20from%20a%20Low%20Input%20Supply/article-2018january-generating-a-high-dc-fig3.jpg?ts=78498d09-60b0-42ae-926c-cdd338dbfabc&la=en-US)

> _Microchip's MCP1665_

F_igure 3: Microchip's MCP1665 can produce up to 32 volts from a Li-ion, NiMH, or NiCd battery. (Image source: Microchip Technology)_

This device can deliver up to 1000 milliamperes from a 5 volt supply and includes features such as controlled start-up voltage, a choice of operating modes, and a switching frequency of 500 kilohertz (kHz); the peak current mode architecture achieves high efficiency over a wide load range.

In some boost applications, maintaining the output voltage at a set value is not the primary design goal. In an LED backlight driver, the desired LED brightness is a function of the current through the LED string, so the current flowing through a shunt resistor forms the feedback voltage to the controller and determines the boost voltage. The [AP3019AKTR-G1](https://www.digikey.com/product-detail/en/diodes-incorporated/AP3019AKTR-G1/AP3019AKTR-G1DICT-ND/7708820) from [Diodes Incorporated](https://www.digikey.com/en/supplier-centers/d/diodes) is an example of a boost converter optimized for driving a string of up to eight LEDs for backlight applications (Figure 4).

![Diagram of Diodes AP3019A driver includes specialized features](https://www.digikey.com/-/media/Images/Article%20Library/TechZone%20Articles/2018/January/Generating%20a%20High%20DC%20Output%20Voltage%20from%20a%20Low%20Input%20Supply/article-2018january-generating-a-high-dc-fig4.jpg?ts=07b0efc9-04d2-4ff3-b5b0-e15c5e161457&la=en-US)

> _Figure 4: Operating at a typical switching frequency of 1.2 MHz, the AP3019A driver includes specialized features to control the brightness of an LED backlight string. (Image source: Diodes Incorporated)_

Optimized for space-constrained applications, the device includes both the power switch and the diode internally, and a switching frequency of 1.2 MHz allows the use of tiny external components. The AP3019A can supply up to 550 mA in a SOT-23-6 package.

The CTRL pin is a specialized Shutdown and Dimming input: connecting the pin to 1.8 volts or higher enables the device; 0.5 volts or less disables the device; and applying a pulse-width modulated (PWM) signal allows the implementation of LED brightness control.

## Follow these design tips to optimize efficiency

In some of the devices already discussed, the manufacturer has already fixed some of the parameters internally, but a designer typically has several available trade-offs to optimize the conversion efficiency. In addition, care must be taken to select the correct external components according to the guidelines that follow.

_Switching frequency:_ Although the switching frequency does not affect the output voltage directly, it does have a significant effect on the power supply design. In general, a higher switching frequency allows the designer to use a smaller inductor and smaller capacitors for a given application. The inductor size is primarily determined by the amount of allowable ripple current. For a given inductance, the ripple current decreases as the switching frequency increases: given a choice of several devices, a designer can trade off increased switching frequency for a smaller inductor while maintaining the same amount of ripple current.

Higher frequency operation gives the switching regulator greater bandwidth, shortening the transient response time. The smaller inductor also reduces the size and cost of the power supply.

_Inductor selection:_ The inductor is a key component of the boost regulator: it stores energy during the on-time of the power switch and transfers energy to the output through the output rectifier diode during the off time.

The designer must make a trade-off between low inductor current ripple and high efficiency. A lower value inductor has a higher saturation current and a lower series resistance for a given physical size, but the lower inductance results in higher peak currents that can lead to reduced efficiency, higher ripple, and increased noise.

When selecting a suitable inductor, the rated saturation current of the inductor must be greater than the peak inductor current, and the inductor's RMS current rating must be greater than the maximum DC input current to the regulator.

Most boost regulator data sheets include inductor recommendations for different load currents and voltages: the data sheet for Microchip's MCP1665, discussed earlier, recommends the [Panasonic Electronic Components](https://www.digikey.com/en/supplier-centers/p/panasonic) [ELL-8TP4R7NB](https://www.digikey.com/product-detail/en/panasonic-electronic-components/ELL-8TP4R7NB/PCD2442CT-ND/5673829) 4.7 microhenry (µH) inductor for output voltages below 15 volts, but the [Wurth Electronics](https://www.digikey.com/en/supplier-centers/w/wurth-electronics) [7447714100](https://www.digikey.com/product-detail/en/wurth-electronics-inc/7447714100/732-2988-1-ND/2626112) 10 µH inductor for higher output voltages.

## Diode selection

In a non-synchronous design, a Schottky diode, with its lower forward voltage, should be used to reduce losses. The diode's average forward current rating must be equal to or higher than the maximum output current. The diode's peak repetitive forward current rating must be equal to or higher than the inductor peak current, and the diode's reverse breakdown voltage must be higher than the internal power switch rating voltage.

The MCP1665, for example, has a 36 volt internal switch and can deliver up to 1 ampere. Microchip therefore recommends the [STPS2L40VU](https://www.digikey.com/product-detail/en/stmicroelectronics/STPS2L40U/497-5574-1-ND/1209743) Schottky diode from [STMicroelectronics](https://www.digikey.com/en/supplier-centers/s/stmicroelectronics), a device with a 40 volt reverse breakdown voltage and a forward current of 2 amperes.

At high temperatures, the diode's leakage current can also have a significant effect on the converter's operational efficiency. For high currents and high ambient temperatures, use a diode with good thermal characteristics.

_Input and output capacitors:_ In the boost topology, the inductor acts to smooth out the transient demands placed on the power circuit supplying the regulator circuit, reducing the input filtering required. A ceramic capacitor with an X5R rating is often sufficient for an operating temperature of +85°C, but low ESR X7R capacitors may be needed for +125°C operation.

If the impedance of the power source is too high to maintain the input voltage above the undervoltage lockout threshold under high load steps, an additional electrolytic or tantalum capacitor may also be required.

On the load side, the output capacitor reduces load ripple and helps provide a stable output voltage during load transients. A ceramic X7R capacitor is recommended for the output capacitor: other types may have a high ESR that reduces the converter efficiency.

The DC rating of the capacitor should be comfortably above the maximum output voltage VOUT since ceramic capacitors lose effectiveness when operated close to their maximum voltage. Consult the data sheet for recommendations on capacitor selection.

_Boost regulator layout considerations:_ Due to its high-speed switching characteristics, the boost regulator performance is very sensitive to PCB layout: parasitic inductance and capacitance can cause high output ripple, poor output regulation, excessive electromagnetic interference (EMI), and even result in failure due to a high voltage spike.

The designer should therefore pay close attention to the PCB layout by following these tips:

  1. The output capacitors should be located close to the device, and connected with short and wide traces to minimize parasitic inductance that can cause voltage ringing and spikes. Multiple vias help reduce parasitic capacitance.
  2. After placing the output capacitor, locate the inductor close to the IC to reduce radiated EMI. Since the SW node (see Figures 2, 3, 4) is electrically noisy, route the feedback (FB) signal and other sensitive traces well away from this node. 
  3. The ground node of the input capacitor should also be close to the IC power ground pin to minimize the loop area. 
  4. For best thermal performance, the layout should include thermal vias from the device thermal pad (if applicable) down to the ground plane; these improve heat dissipation and reduce the risk of thermal shutdown. 
  5. The power ground, signal ground, and thermal pad should be connected together at a single low impedance ground point.

## Online design tools speed the design process

An effective power supply design requires expertise in multiple areas, including component evaluation and selection, magnetics, compensation circuit design, optimization, thermal analysis, layout, and more.

Recognizing the complexity, several power semiconductor suppliers provide helpful online design tools that guide engineers through the steps needed for a successful design.

Texas Instruments offers multiple tools. Power Stage Designer™, for example, helps in the design of the most commonly used switching power supplies. For boost converters, there is a choice of boost, buck-boost, and SEPIC topologies. After picking a proposed topology, the program helps the designer compare the performance of different power FETs, pick a bulk capacitor, determine the compensation network, plus perform other design functions.

ADI offers the ADIsimPower™ design toolset, which helps a designer generate a full schematic and bill of materials (BOM), as well as calculate circuit performance. ADIsimPower can optimize designs for cost, area, efficiency, or parts count, while taking into consideration the operating conditions and limitations of the IC and external components.

## Conclusion

By enabling the use of higher voltage circuit functions, the boost regulator plays a valuable role in battery powered portable and wearable designs. However, designers must choose a device that fits the required boost application, and pay attention to a number of key design tradeoffs and best practices.

Disclaimer: The opinions, beliefs, and viewpoints expressed by the various authors and/or forum participants on this website do not necessarily reflect the opinions, beliefs, and viewpoints of Digi-Key Electronics or official policies of Digi-Key Electronics.
