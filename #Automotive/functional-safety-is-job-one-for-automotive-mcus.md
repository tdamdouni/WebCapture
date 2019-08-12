# Functional Safety Is Job One for Automotive MCUs

_Captured: 2019-04-03 at 14:33 from [www.digikey.com](https://www.digikey.com/en/articles/techzone/2015/sep/functional-safety-is-job-one-for-automotive-mcus)_

The complexity and sophistication of automotive technology keeps presenting new challenges for all chipmakers, not the least of which are MCU companies. Safety is "Job One" and how to ensure safe vehicles is a massive undertaking.

Improved noise immunity and robustness, error detection, and on-chip backup systems to help recover from unexpected events are more than important automotive MCU features--they are also required in order to achieve industry-standard certifications. Virtually all automotive sub-systems have some aspect of safety involved. As a result, meeting functional safety requirements can be challenging for system designers, especially since they concurrently have to manage growing application complexity. The basic approach is to architect systems to either prevent dangerous failures entirely or to control them when they occur.

To that end and true to the rigor that is characteristic of the automotive industry, functional safety is well defined. The functional safety standard IEC 61508 and its automotive adaptation ISO 26262 were created to ensure acceptable levels of safety. IEC 61508 defines four general Safety Integrity Levels (SILs) across many industries with SIL 4 being the most stringent level.

ISO 26262--adopted in 2011--takes safety requirements to a deeper level. It defines four Automotive Safety Integrity Levels (ASILs) with ASIL D ranking as the most stringent safety level. Each level corresponds to a range of target likelihood of failures of a safety function.

ISO 26262 also defines a series of steps to assign an acceptable level of risk for a system, to minimize errors during the product development process, and to determine if the end product achieves the required level of functional safety.

From the beginning of the design process, evidence must be collected to show that the product has been developed according to ISO 26262 standards. Deviations must be identified and documented to ensure that adequate alternative measures are used. New tools from companies such as Liverpool Data Research Associates in England and Yogitech in Italy have been developed to support functional safety compliance and documentation.

Although the failure rate of individual chips is quite low, the number of chips in an automobile significantly increases the potential for failures. Functional safety is the ability of an electronic system to detect when there is a fault, make the driver aware of the fault, and put the vehicle in a mode that allows the driver to maintain safe control.

Hardware and software are equally involved. For example, the appropriate response to an accidental airbag deployment would engage diagnostics that identify the fault, provide the ability to stop deployment automatically, and inform the driver that the system is not working properly by activating a warning light.

**Role of the MCU**

Because they are involved in monitoring, control, and other intelligent functions, MCUs have a key role in ensuring functional safety. There is more than one path to achieving functional safety at the component level. [Microchip Technology](https://www.digikey.com/Suppliers/US/Microchip-Technology.page?lang=en), for example, has extended its 16-bit PIC MCU architecture, [STMicroelectronics](https://www.digikey.com/Suppliers/US/STMicroelectronics.page?lang=en) has opted to use and enhance 32-bit ARM core architectures, and [Freescale Semiconductor](https://www.digikey.com/Suppliers/US/Freescale-Semiconductor.page?lang=en) has customized its 32-bit PowerPC core. (The merger with NXP Semiconductors also brings an automotive product portfolio based on 32-bit ARM cores into the product mix and it will be interesting to see how the merged company deals with the situation.)

The different approaches of the three companies are also revealed in the component selection process they offer. To narrow choices for designers, Microchip Technology has taken the approach of identifying functional safety features and identifying the members of its MCU families as having those features.

Because some automobile subsystems--such as door locks--are often relatively simple, Microchip has met functional safety requirements in members of its 8-bit [PIC10FXXX](https://www.digikey.com/product-search/en/integrated-circuits-ics/embedded-microcontrollers/2556109?k=PIC10F) family as well as the [PIC12FXXX](https://www.digikey.com/product-search/en/integrated-circuits-ics/embedded-microcontrollers/2556109?k=PIC12F&stock=1), [PIC16FXXX](https://www.digikey.com/product-search/en/integrated-circuits-ics/embedded-microcontrollers/2556109?k=PIC16F&stock=1), and [PIC18FXXX](https://www.digikey.com/product-search/en/integrated-circuits-ics/embedded-microcontrollers/2556109?k=PIC18F&stock=1) families. For subsystems requiring higher processing performance or on-chip memory requirements, Microchip has identified its 16-bit [PIC24XXX](https://www.digikey.com/product-search/en/integrated-circuits-ics/embedded-microcontrollers/2556109?k=PIC24F&stock=1) family and it [dsPIC33XXX](https://www.digikey.com/product-search/en/integrated-circuits-ics/embedded-microcontrollers/2556109?k=dsPIC33&stock=1) family as its performance leaders. The dsPIC DSC architecture, in particular, provides digital-signal processing capabilities using 40-bit accumulators for very-high intermediate arithmetic precision. A table of MCU features relevant to functional safety and a general designation of how the families conform is shown in Figure 1.

![Image of Microchip Technology’s functional safety lineup for its PIC24XXX and dsPIC33 families](https://www.digikey.com/-/media/Images/Article%20Library/TechZone%20Articles/2015/September/Functional%20Safety%20Is%20Job%20One%20for%20Automotive%20MCUs/article-2015september-functional-safety-fig1.jpg?la=en&ts=3a48225a-6a73-4091-b797-8d7d2da27895)

> _Microchip Technology's functional safety lineup for its PIC24XXX and dsPIC33 families_

_Figure 1: Microchip Technology's functional safety lineup for its PIC24XXX and dsPIC33 families. (Courtesy of Microchip Technology)_

Three familiar functions are Flash memory with embedded Error Correcting Code (ECC) for increased reliability and safety, Cyclic Redundancy Checking (CRC), and a high-precision Deadman Timer (DMT) that monitors the health of application software by requiring periodic timer interrupts within a user-specified timing window.

The LDRA Compliance Management Tool Suite at the bottom of the list in Figure 1 is provided by Liverpool Data Research Associates, a supplier of software analysis, test, and requirements traceability tools--and a pioneer in static and dynamic software analysis. The tool suite handles functional safety compliance management, software verification, source-code analysis, and test tools. It works seamlessly with Microchip's MPLAB X Integrated Development Environment and MPLAB XC compilers.

Microchip developed its 16-bit dsPIC33 EV family of Digital Signal Controllers (DSCs) specifically for high-noise environments such as automotive applications and white goods appliances. Whereas operating voltages are generally decreasing in MCU applications, Microchip uses 5 V in its dsPIC33 EV family to improve noise immunity and robustness.

It is also the first dsPIC DSC family with ECC; and the dsPIC33EV devices also include CRC, DMT, and Windowed Watchdog Timer (WWDT) peripherals, as well as a backup system oscillator and certified Class B software.

Other features relevant to automotive applications include: 70 MIPS performance, which allows it to execute smart-sensor algorithms; under-voltage protection, and 150°C operation for under-the-hood systems.

The [DSPIC33EV32GM002-E/SO](https://www.digikey.com/product-detail/en/DSPIC33EV32GM002-E%2FSO/DSPIC33EV32GM002-E%2FSO-ND/5252345) integrates all of these features. Microchip also offers the [DM330018 dsPIC33EV 5V CAN-LIN Starter Kit](https://www.digikey.com/product-detail/en/DM330018/DM330018-ND/5050775), a stand-alone demonstration board for exploring three automotive and industrial serial-data formats (CAN, LIN, and SENT).

A block diagram of the DSPIC33EV32GM002-E/SO is shown is Figure 2.

![Image of Microchip dsPIC33EV family addresses automotive with 5 V operation](https://www.digikey.com/-/media/Images/Article%20Library/TechZone%20Articles/2015/September/Functional%20Safety%20Is%20Job%20One%20for%20Automotive%20MCUs/article-2015september-functional-safety-fig2.jpg?la=en&ts=687a87b8-81ce-4211-9234-b57fc000a773)

> _Figure 2: The dsPIC33EV family addresses automotive with 5 V operation and specialized peripherals. (Courtesy of Microchip Technology)_

**STMicroelectronics**

STMicroelectronics--one of the top four market leaders in automotive MCUs--has organized its automotive product portfolio around a customized version of its 32-bit Power Architecture, which in turn is based on ARM cores.

The SPC56 family provides a wide range of cores, peripherals, memory, and package options. Prominent Power Architecture features include: high-performance peripherals; up to 12 bit ADCs; true 3.3 V to 5 V I/Os; and CAN, LIN, FlexRay, and Ethernet communications capability.

Single- and dual-core processors are available that run on 32-150 MHz clocks and integrate as much as 4 MB of Flash memory. Specific safety considerations include ECC Flash memory, compliance with ISO 26262 for ASIL-D safety, and both Lock Step (LSM) and Decoupled Parallel (DPM) operating modes for the dual-core MCUs.

There are seven automotive grade lines, all of which have built-in functional safety features. They are: SPC56 D, B, C, P, L, M, and A.

  * SPC56D - Base element of the family to address automotive applications that are migrating from an 8-bit to 32-bit solution
  * SPC56B - Dedicated to body and convenience applications
  * SPC56C - For gateway applications that require connections to multiple in-vehicle networks supporting various protocols from LIN, SPI, UART, CAN to FlexRay, and Ethernet
  * SPC56P - Designed for cost-competitive motor control and safety applications
  * SPC56L - Covers a wide range of automotive applications that must meet ISO 26262 up to the most stringent ASIL-D level with a single MCU
  * SPC56M - Entry-level solution for engine and transmission control
  * SPC56A - Dedicated to the specific needs of propulsion- and transmission-control applications

The most recent addition to STMicro's automotive MCU lineup is the SPC58NE product line, which combines two high-performance dual-issue cores with up to 6 MB of Flash memory and 768 kB RAM. The multiple cores ensure redundancy as a means of meeting safety and security requirements. Eight CAN (Controller Area Network) interfaces are also integrated.

Until the SPC58NE products are in production, a good example of STMicro's high-end MCUs for safety applications is the [SPC564A80L7CFAR](https://www.digikey.com/product-detail/en/SPC564A80L7CFAR/497-11621-2-ND/2746832). Customized for engine control and transmission control, it is based on the e200zz4d core and offers 4 MB Flash with ECC, 192 kB internal RAM with ECC and CAN, EBI/EMI, LIN, SCI, and SPI interfaces.

**Freescale**

The recent merger of NXP Semiconductors and Freescale Semiconductor creates an entity that is likely to have the largest market share in automotive ICs, including the MCU subcategory. Freescale designed its 32-bit [Qorivva 56xx](https://www.digikey.com/product-search/en/integrated-circuits-ics/embedded-microcontrollers/2556109?k=Qorivva%2056) automotive MCUs specifically to address the requirements of the ISO 26262 safety standards. Based on the Power Architecture technology, Qorivva [MPC5xx](https://www.digikey.com/product-search/en/integrated-circuits-ics/embedded-microcontrollers/2556109?k=MPC5xx) MCUs are built around one or two PowerPC cores supported by integrated analog and power management functions as well as sensors optimized for safety-critical applications.

Among the MCU-specific safety features are: lockstep cores that support a software environment for redundant processing and calculations; ECC on memories; redundant functions; monitors; built-in self-test and fault detection and control. Analog- and power-management safety functions include: voltage monitors, advanced watchdog timers, and built-in self-test. Specialized sensors featured timing checkers, digital scan of signal chains, ECC on memories, and the DSI3 (Distributed System Interface) and PSI5 (Peripheral Sensor Interface) data interfaces that conform to international standards for safety critical communication.

Freescale offers a starter kit, the [TRK-USB-MPC5643L](https://www.digikey.com/product-detail/en/TRK-USB-MPC5643L/TRK-USB-MPC5643L-ND/4234025) for its dual-core, 32-bit MPC5643L, which specifically targets high-end ISO 26262-compliant automotive applications. The MCU has been certified by exida, an independent accredited assessor in functional safety and security. The ISO 26262 consists of 10 parts, including clauses for hardware, software, their integration, and the development and production processes. Since the MPC5643L MCU is just one component in such systems, the assessment scope included all relevant clauses of ISO 26262 that were identified as applicable to an MCU.

A block diagram of MPC5643L is shown in Figure 3.
