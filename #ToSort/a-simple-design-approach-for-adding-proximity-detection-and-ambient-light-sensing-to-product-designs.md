# A Simple Design Approach for Adding Proximity Detection and Ambient Light Sensing to Product Designs

_Captured: 2017-11-30 at 10:33 from [www.digikey.com](https://www.digikey.com/en/articles/techzone/2017/nov/a-simple-design-approach-for-adding-proximity-detection?WT.z_sm_link=tzsnnsr&utm_source=twitter&utm_medium=social&utm_campaign=tzsnnsr)_

Proximity sensing offers an additional dimension to the human machine interface (HMI) with its ability to detect the approach of users. Combined with ambient light sensing, light-based proximity detection can enable automatic activation of systems and their displays in office equipment and consumer products.

For many developers, implementing light-based proximity sensing brings multiple challenges, ranging from suitability of the sensor spectral sensitivity, to interface design and mechanical placement of sensors and light sources. However, an integrated solution from [Vishay Semiconductor](https://www.digikey.com/en/supplier-centers/v/vishay-semi-opto) addresses these requirements.

This article will describe the application and design challenges of proximity sensing before showing how Vishay's solution lets developers easily add proximity detection capabilities to their designs.

## Features and challenges of proximity sensing

Proximity sensing is an enabling feature for applications ranging from automotive safety to consumer products. To meet the unique requirements of each application, developers implement proximity sensing using dramatically different technologies. In automotive safety applications, for example, developers typically use [time-of-flight methods](https://www.digikey.com/en/articles/techzone/2017/jan/simplifying-time-of-flight-distance-measurements) (ToF) capable of delivering very fast response at extended distances. In contrast, mobile phone developers often rely on [capacitive-based approaches](https://www.digikey.com/en/articles/techzone/2016/dec/simplifying-capacitive-touch-sensor-design-cypress-cy8ckit) to automatically turn off the phone display as it nears the user's face.

For many other applications, developers can meet proximity detection requirements with more conventional light sensing methods that translate reflected light levels to distance. These methods offer a cost-effective solution able to detect users at distances greater than possible with capacitive methods, but not at the extended range or fast response of ToF methods.

By measuring light reflected from an approaching user, the control system can activate the product when the user moves within a specified distance. At the same time, a product that turns on automatically also needs to provide a display that turns on at illumination levels appropriate to ambient lighting levels. As consumers demand smarter products, developers need solutions able to meet requirements for proximity detection and ambient light sensing with minimal impact on product design and integration.

## Double duty

The Vishay [VCNL4200](https://www.digikey.com/product-detail/en/vishay-semiconductor-opto-division/VCNL4200/VCNL4200CT-ND/7394602) addresses these requirements by combining a proximity sensor and ambient light sensor in a single module. By providing both proximity detection and ambient light sensing, the module serves as a ready solution for applications such as automatic display activation and brightness control, smart appliance activation, lighting control, object detection, and more.

Designed to simplify integration in diverse applications, the Vishay VCNL4200 includes all of the optical and electronic subsystems required to support proximity sensing (PS) and ambient light sensing (ALS). Built-in lenses help provide tightly focused angles of ±15° and ±30° for the infrared emitter (IRED) and photodetectors, respectively. Because these optical components are integrated in the same package, engineers building the physical design for their systems only need to ensure that IRED and photodiodes use openings large enough to accommodate their respective angles. Depending on the distance between the VCNL4200's lenses and any external cover, these openings need only be a couple of millimeters in diameter.

Beyond those mechanical considerations for the optical subsystems, the optical characteristics of the PS and ALS features require no further effort by the designer. While the PS system operates with a center spectral frequency of 940 nanometers (nm), the ALS system provides a spectral response closely resembling the human eye with its center frequency peaking around 550 nm (Figure 1).

![Graph of Vishay VCNL4200 ambient light sensor](https://www.digikey.com/-/media/Images/Article%20Library/TechZone%20Articles/2017/November/A%20Simple%20Design%20Approach%20for%20Adding%20Proximity%20Detection/article-2017november-a-simple-design-approach-fig1.jpg?ts=61d3d481-9119-44f6-9912-0c2b08443ef2&la=en-US)

> _Vishay VCNL4200 ambient light sensor_

_Figure 1: Wafer-level interference filters enable the Vishay VCNL4200 ambient light sensor to deliver measurements consistent with illumination levels perceived by the human eye. (Image source: Vishay Semiconductor)_

Vishay achieves this photopic spectral response using its proprietary Filtron technology, which builds appropriate interference filters on the die itself using standard CMOS semiconductor process technology. As a result, the ALS system measures ambient light intensity consistent with the intensity a human would perceive.

Along with their separate spectral responses, the PS and ALS subsystems operate independently using separate components. For proximity measurement, the device uses a matched IRED and photodiode and dedicated 12-bit/16-bit analog-to-digital converter (ADC) for producing PS values. For ambient light sensing, the device provides a separate photodiode and dedicated 16-bit ADC for generating ALS values.

Operating in parallel, the device's proximity and ambient light sensors each support different modes of operation. Developers can use the device as a pure sensor to measure ambient light levels, or relative intensity of reflected infrared light for use in their own algorithms. For example, the device's PS function provides reflected light values inversely proportional to distance (Figure 2). As the figure illustrates, the PS system can saturate at very close distances, limiting its effectiveness in measurement applications that might be better served by capacitive methods.

![Graph of Vishay VCNL4200 proximity sensor delivers proximity values inversely proportional to distance](https://www.digikey.com/-/media/Images/Article%20Library/TechZone%20Articles/2017/November/A%20Simple%20Design%20Approach%20for%20Adding%20Proximity%20Detection/article-2017november-a-simple-design-approach-fig2.jpg?ts=577bac4f-41b6-400a-9d72-58b14798c889&la=en-US)

> _Vishay VCNL4200 proximity sensor delivers proximity values inversely proportional to distance_

_Figure 2: At a given setting of pulse length (9T = 240 microseconds (μs)) and pulse repetition (MPS=8), the Vishay VCNL4200 proximity sensor delivers proximity values inversely proportional to distance not only at short range (A) but even at ranges extending over 1.5 meters (B). (Image source: Vishay Semiconductors)_

## Proximity interrupts

The VCNL4200 provides an even simpler approach for applications that only need to detect that a user has approached within a specified distance. Here, developers set device registers to suitable thresholds and specify the number of consecutive measurements required before the device recognizes a threshold event. During a typical measurement sequence, the device sends an interrupt signal to a host MCU whenever the measured proximity values exceed an upper threshold value, or drop below a lower threshold value after N consecutive occurrences (Figure 3). As a result, designers can put the host MCU in a low-power state between proximity events, conserving overall system power.

![Graph of programming the Vishay VCNL4200 to issue interrupts \(“D” and “E”\)](https://www.digikey.com/-/media/Images/Article%20Library/TechZone%20Articles/2017/November/A%20Simple%20Design%20Approach%20for%20Adding%20Proximity%20Detection/article-2017november-a-simple-design-approach-fig3.jpg?ts=44e5c76d-c5d7-4f8f-b20e-fe47e4f0c9bf&h=374&w=576&la=en-US)

> _Figure 3: Developers can program the VCNL4200 to issue interrupts ("D" and "E") whenever proximity values exceed a threshold after N consecutive measurements ("D") or fall below a threshold ("F") while ignoring transient events ("B"). (Image source: Vishay Semiconductors)_

Using this interrupt-driven approach, developers set values for upper and lower thresholds after device power up (step "A" in the figure). By setting the number of required consecutive occurrences to some value N>1, the device can ignore single events ("B"), allowing the MCU to remain in a low-power state even in those situations. When proximity values do exceed the threshold ("C"), the device issues an interrupt after a period corresponding to N consecutive measurements ("D").

After the interrupt wakes the MCU, the MCU would clear the interrupt ("E") and complete the operations associated with proximity detection. In a consumer appliance, for example, these operations might include turning on the appliance and its display, using ambient light sensing to set the display brightness.

When the proximity values later fall, indicating the user has moved away, the device would issue another interrupt ("F"), allowing the host MCU to take appropriate action such as shutting down the appliance and its display.

## Minimal development

Developers can implement this type of functionality with relatively little effort. The hardware interface requires only a few additional components to complete the design (Figure 4). Along with decoupling capacitors, developers need to add a small driver such as a Vishay [SI2301](https://www.digikey.com/product-detail/en/vishay-siliconix/SI2301CDS-T1-GE3/SI2301CDS-T1-GE3CT-ND/1978876) PMOS FET powered by a 3.8 to 5.5 volt VIRED source.

![Diagram of Vishay VCNL4200 sensor design](https://www.digikey.com/-/media/Images/Article%20Library/TechZone%20Articles/2017/November/A%20Simple%20Design%20Approach%20for%20Adding%20Proximity%20Detection/article-2017november-a-simple-design-approach-fig4.jpg?ts=4033ed6e-aaba-454c-94de-bec57cb1f2da&la=en-US)

> _Vishay VCNL4200 sensor design_

_Figure 4: Designers complete the VCNL4200 sensor design with only a few additional components including a Vishay SI2301 PMOS FET used to drive current pulses to the integrated infrared emitter at current levels set by the value of RLED. (Image source: Vishay Semiconductors)_

The internal LED gate driver uses the device's LED cathode output to pulse the external FET, which in turn applies the current pulses to the internal infrared emitter (LED+) at a current level controlled by an external resistor (RLED) connected to the LED- pin. On the processor side, the VCNL4200 interrupt line (INT) and I2C lines connect to corresponding MCU pins.

The command interface is similarly straightforward. Device command codes provide read access to PS and ALS sensor output data, as well as read and write access to the separate configuration registers for the two sensor subsystems. Developers use a simple transaction protocol to read and write these registers across the I2C bus (Figure 5).

![Image of host MCU controls the VCNL4200 sensor across the I2C](https://www.digikey.com/-/media/Images/Article%20Library/TechZone%20Articles/2017/November/A%20Simple%20Design%20Approach%20for%20Adding%20Proximity%20Detection/article-2017november-a-simple-design-approach-fig5.jpg?ts=dce1aa47-5cfa-44c0-968e-ffec82434cf7&la=en-US)

> _Figure 5: The host MCU controls the VCNL4200 sensor across the I2C bus using a simple write (A) and read (B) protocol that intersperses sensor responses (gray) with host requests (white). (Image source: Vishay Semiconductors)_

Here, the bus master (typically, the host MCU) initiates a write sequence by sending the slave address, a write cycle ("W" in Figure 5), a command code, and the low and high bytes of a 16-bit word (Figure 5A). Reading data from the VCNL4200 involves two steps where the bus master first writes the appropriate read command code to the VCNL4200, and then initiates ("S" in Figure 5B) a read cycle ("Rd") to acquire the data (Figure 5B). The bus transaction protocol includes acknowledgements by the VCNL4200 (shaded "A") and bus master ("A" and "N").

In practice, developers generally need program only a few settings in configuration registers for typical applications. For proximity sensing, developers would set the integration time to values ranging from about 30 μs (PS_IT = 1T) up to 240 microseconds (μs) (PS_IT = 9T) and duty ratio (PS_DUTY) to values ranging from 1/160 to 1/1280.

Using different duty ratio settings, developers can control response time and power consumption of the sensor. At maximum duty ratio (1/160), the device would measure at a faster rate, but increase its power consumption. For example, using an RLED of 2.7 Ω would result in 800 milliamp (mA) current pulses. At 1/160 duty cycle, the VCNL4200 would perform a measurement every 5 ms, but average current consumption would be 800/160 = 5 mA. At minimum duty cycle (1/1280), sensor measurements would only occur every 300 ms, but average power consumption would drop nearly an order of magnitude.

## Development platforms

To help developers work through the VCNL4020's configuration options, Vishay offers a [sensor starter kit](https://www.digikey.com/product-detail/en/vishay-semiconductor-opto-division/SENSORSTARTERKIT/SENSORSTARTERKIT-ND/5125774) that provides an evaluation software program, USB dongle, and a sensor board that plugs into the dongle. Although the kit comes with a [VCNL4020](https://www.digikey.com/products/en/sensors-transducers/optical-sensors-ambient-light-ir-uv-sensors/536?k=VCNL4020&pv7=2&FV=ffe00218&) sensor board, developers can receive a free VCNL4200 sensor board [by contacting Vishay sensor tech support](mailto:sensorstechsupport@vishay.com).

After attaching the sensor board to the USB dongle, developers can run the evaluation software program to study the impact of different register settings on sensor characteristics and performance.

For custom designs, engineers can combine a development board such as an [Arduino](https://www.digikey.com/products/en/development-boards-kits-programmers/evaluation-boards-embedded-mcu-dsp/786?k=arduino&v=1050&FV=1f140000%2Cffe00312%2C380085e&nstock=1) with the sensor board to speed design, or build their own support circuitry as described in Figure 4. Third-party [open-source software](https://github.com/ChicagoRobotics/CRC_VCNL4200) provides the necessary register definitions (Listing 1).

`//Register declarations`

`#define VCNL4200_I2CADDR 0x51`

`#define VCNL4200_ALS_CONF_REG 0x00`

`#define VCNL4200_ALS_THDH_REG 0x01 //Ambient Light Sensor Threshold Data High`

`#define VCNL4200_ALS_THDL_REG 0x02 //Ambient Light Sensor Threshold Data Low`

`#define VCNL4200_PS_CONF1_CONF2_REG 0x03`

`#define VCNL4200_PS_CONF3_MS_REG 0x04 //Conf3 and Mode Select`

`#define VCNL4200_PS_CANC_REG 0x05`

`#define VCNL4200_PS_THDL_REG 0x06 //Proximity Sensor Threshold Data Low`

`#define VCNL4200_PS_THDH_REG 0x07 //Proximity Sensor Threshold Data High`

`#define VCNL4200_PROXIMITY_REG 0x08`

`#define VCNL4200_AMBIENT_REG 0x09`

`#define VCNL4200_WHITE_REG 0x0A`

`#define VCNL4200_INT_FLAG_REG 0x0D`

`#define VCNL4200_DeviceID_REG 0x0E`

_Listing 1: To use proximity sensing and ambient light sensing in their own designs, developers can turn to open-source software that provides a basic framework such as VCNL4020 register defines. (Code source: GitHub open-source repo)_

Third-party software also demonstrates use of the [Arduino Wire library](https://www.arduino.cc/en/Reference/Wire) in implementing the simple command protocol for functions such as proximity sensing (Listing 2).

`uint16_t CRC_VCNL4200::readData(uint8_t command_code)`

`{`

`            uint16_t reading;`

`            Wire.beginTransmission(_i2caddr);`

`            Wire.write(command_code);`

`            Wire.endTransmission(false);`

`            Wire.requestFrom(_i2caddr, uint8_t(2));`

`            while (!Wire.available());`

`            uint8_t byteLow = Wire.read();`

`            while (!Wire.available());`

`            uint16_t byteHigh = Wire.read();`

`            reading = (byteHigh <<= 8) + byteLow;`

`            return reading;`

`}`

`            .`

`            .`

`            .`

`uint16_t CRC_VCNL4200::getProximity() {`

`            return readData(VCNL4200_PROXIMITY_REG);`

`}`

_Listing 2: An open-source repo includes code that demonstrates use of the Arduino Wire library for implementing VCNL4020 features such as proximity sensing. (Code source: GitHub open-source repo)_

## Conclusion

Although developers can turn to a variety of proximity detection technologies, simple reflective measurement provides a cost-effective solution for many designers targeting business and consumer products. By combining proximity detection with ambient light measurement, developers can build products able to sense the approach of users and automatically activate displays at the appropriate brightness level.

Containing integrated support for both proximity sensing and ambient light sensing, the VCNL4020 lets developers implement these features with little additional effort.

Disclaimer: The opinions, beliefs, and viewpoints expressed by the various authors and/or forum participants on this website do not necessarily reflect the opinions, beliefs, and viewpoints of Digi-Key Electronics or official policies of Digi-Key Electronics.
