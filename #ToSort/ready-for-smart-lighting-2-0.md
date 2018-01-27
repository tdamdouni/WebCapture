# Ready for Smart Lighting 2.0?

_Captured: 2017-12-06 at 12:50 from [www.digikey.com](https://www.digikey.com/en/articles/techzone/2017/dec/ready-for-smart-lighting-20?WT.z_sm_link=tzsmrtlgt&utm_source=twitter&utm_medium=social&utm_campaign=tzsmrtlgt)_

## Introduction: can smart lighting be even smarter?

The essentially digital nature of LED lighting has greatly enhanced controllability, which can be used to achieve a wide variety of lighting effects from dimming and color changing to occupancy-based behavior. Lighting has become smart and responsive, but when teamed with the emerging Internet of Things (IoT), it could support greater functionality if additional sensors are implemented. For example, streetlights equipped with cameras, proximity sensors, or air quality sensors could aid the management of smart cities. Sensors embedded in domestic light fixtures could enhance hazard detection or emergency calling.

The question as to how new generations of smarter lights can be introduced cost effectively to existing networks needs to be addressed. The IoT is a fast moving field, but owners fitting new LED lighting today are expecting to run their lights for a long period before upgrading in order to maximize their return on investment. The time could be right for new, smarter lighting, featuring versatile and upgradeable sensor interfaces, ready to leverage the pace of progress in the Cloud to deliver even greater value for users.

## Lighting and the IoT

Smart lighting is broadly understood to cover automation of lamp responses, such as dimming or on/off control to enhance user comfort and save energy. An ambient light sensor (ALS) can be used to detect the amount of natural light available, allowing the lamp's output to be adjusted accordingly. It must be located close to the lamp to give a relevant indication of the ambient conditions, but also positioned to minimize exposure to the lamp's own light to prevent spurious dimming and brightening.

[Maxim Integrated](https://www.digikey.com/en/supplier-centers/m/maxim-integrated) has shown how to design an ALS like the [MAX44009](https://www.digikey.com/product-detail/en/maxim-integrated/MAX44009EDT-T/MAX44009EDT-TCT-ND/2606396) into an outdoor lamp fitting, as illustrated in Figure 1. The system is based on the [Microchip](https://www.digikey.com/en/supplier-centers/m/microchip-technology) [PIC18LF4520](https://www.digikey.com/product-detail/en/microchip-technology/PIC18LF4520-I-PT/PIC18LF4520-I-PT-ND/613301) microcontroller. The hardware is relatively simple with a straightforward two-wire connection between the MCU and the sensor. The reference design mounts the ALS on a separate PCB to allow optimal sensor positioning.

![Diagram of ALS to create a smart lighting fixture](https://www.digikey.com/-/media/Images/Article%20Library/TechZone%20Articles/2017/December/Ready%20for%20Smart%20Lighting%202.0/article-2017december-ready-for-smart-fig1.jpg?ts=b5df00b9-305e-4205-a5b9-6161c604b38d&la=en-US)

> _Figure 1: Integrating an ALS to create a smart lighting fixture._

The intelligent lighting controller software, as shown in the flowchart of Figure 2, measures ambient light, tracks time, and allows Lux threshold and morning and evening switch-on times to be programmed via a simple user interface. This comprises a pushbutton with two 7-segment displays and indicator LEDs. The controller software is available in hex format in the Maxim application note [AN5320](http://www.maximintegrated.com/an5320-software).

![Flowchart for software control of ALS enhanced lighting](https://www.digikey.com/-/media/Images/Article%20Library/TechZone%20Articles/2017/December/Ready%20for%20Smart%20Lighting%202.0/article-2017december-ready-for-smart-fig2.jpg?ts=b345c77c-40a2-417f-ab4d-25fa6bcad128&h=481&w=600&la=en-US)

> _Figure 2: Flowchart for software control of ALS enhanced lighting._

An ALS is valuable for monitoring the intensity of ambient light close to the lamp it is managing. Occupancy detection using PIR sensors, on the other hand, can be used to turn relatively remote lamps on or off in areas such as office suites, retail spaces, factory units, or the home. A PIR sensor can be connected directly to the lamp, similar to an ALS sensor. Alternatively, an array of sensors can support more advanced functions such as illuminating segments of a corridor as an occupant walks through, or selectively illuminating zones in a warehouse as workers enter to retrieve goods from specific locations.

## Proximity sensor as cloud-connected IoT endpoint

[Texas Instruments](https://www.digikey.com/en/supplier-centers/t/texas-instruments) has suggested a way of implementing PIR sensors as Cloud-connected IoT endpoints to send occupancy data to a Cloud application.

TI's reference design is based on the [CC1310](https://www.digikey.com/product-detail/en/texas-instruments/CC1310F64RSMR/296-43208-1-ND/5764596) SimpleLink™ ultra-low-power sub-1 GHz wireless microcontroller. The [LPV802](https://www.digikey.com/product-detail/en/texas-instruments/LPV802DGKT/296-44749-1-ND/6196035) dual op-amp and [TLV3691](https://www.digikey.com/product-detail/en/texas-instruments/TLV3691IDCKR/296-37910-1-ND/4900957) dual comparator chosen for conditioning the analog PIR sensor signals are nanopower devices selected to minimize overall power consumption and allow the sensor to operate independently from a coin cell for several years. The TLV3691 comparators, acting as a window, distinguish movement from noise and generate an interrupt for the CPU when movement is detected. This enables the MCU to operate in power-saving modes to prolong battery life, and wake only when needed to send messages back to a remote host. Figure 3 shows a functional block diagram of the sensor node.

The CC1310 is a multi-standard device capable of supporting various radio protocols, and comes with wM-Bus and IEEE 802.15.4g stacks. The reference design uses an application based on the IEEE 802.15.4 stack to handle the sensing algorithm and sub-1 GHz communications between the gateway and the sensor node.

![Image of TI reference design for movement sensor as Cloud-connected IoT endpoint](https://www.digikey.com/-/media/Images/Article%20Library/TechZone%20Articles/2017/December/Ready%20for%20Smart%20Lighting%202.0/article-2017december-ready-for-smart-fig3.jpg?ts=ae4a0e4f-1f55-4818-b652-62d2b5193644&h=207&w=450&la=en-US)

> _Figure 3: TI reference design for movement sensor as Cloud-connected IoT endpoint._

## Getting more from smart lighting, through the IoT

By connecting sensors to the Cloud, their data can be used in a variety of ways beyond simply managing lighting or other services such as heating or ventilation. It can also be used to monitor usage patterns such as identifying areas or times when activity is greater or less than normal. Sophisticated security applications are possible as well. Whereas PIR sensors could be used to activate an intruder alarm directly, a Cloud application can coordinate more complex responses, such as sending SMS alerts to key personnel, time-stamping and recording the intrusion, and then executing a controlled lockdown.

This enhanced use of data related to smart lighting can support a wide variety of lighting scenarios. The light housing can provide an ideal place to position the sensors as they are usually mounted above the area where activity is taking place, and have a broad and unimpeded field of view. Visual sensors such as CMOS cameras can also benefit from the lamp's light to capture high quality images.

Sensor-rich lighting can have applications either inside or outside. In a smart city, streetlamps can monitor traffic flow and road usage. Cloud applications can extract valuable information about the effect of road work, changes in traffic light sequences, and coordinate turning off streetlamps to optimize energy savings without compromising the safety of citizens. Streetlamps are also an ideal place to position cameras or other sensors for detecting vehicles to monitor controlled parking zones and guide enforcement staff. Conversely, parking information could be provided as a service to drivers, to help find available parking spaces to reduce congestion and avoid unnecessary exhaust emissions.

Smart, connected lighting can also be combined with sensors in homes or workplaces to provide an additional visual indication in the event of an emergency. This could be useful for people with hearing difficulties, or to indicate to those outside the building that help may be needed.

## Making use of data

Throughout smart cities, lamp maintenance can be difficult to manage and expensive to implement. When connected to the IoT, a lamp equipped to detect its own failure can instantly inform the relevant maintenance authority that replacement or repair is necessary. Sensors can be designed to detect other faults such as a broken or dirty lens requiring replacement or cleaning.

Data collected through smart lighting can provide valuable information for utility companies to help plan services and identify peak demand time frames. Power consumption data can also be useful to government agencies for energy surveys.

## Should all lighting be ready for the IoT?

Numerous opportunities to build diverse types of sensors into advanced light fittings have been suggested, and many others may become apparent in the future as the power and reach of the IoT continues to extend. It is easy to envisage a time when large numbers of lamps may need to be upgraded with additional sensors.

The IoT-Ready™ Alliance has suggested the time is right to define standardized sensor interfaces to make upgrading as easy as possible. The group has argued that the LED lamps being fitted today are designed to have typical lifetimes of around 15 years, while IoT technology is advancing rapidly and will drive demand for multiple upgrades during the typical life of LED fixtures. It suggests that changing the complete fixture to add new IoT-connected features will be uneconomical and unnecessarily expensive. By readying new LED lamps for integration with the IoT such expense can be avoided. The Alliance's goal is to establish a cost-effective, low-impact means of changing sensors, allowing them to be easily added or upgraded. To achieve this, the group intends to define electrical interfaces, connectors, and mechanical form factors.

It remains to be seen whether this initiative will gain traction among major lighting vendors and designers. On the other hand, some companies may be minded to "go it alone" and develop a proprietary solution, and then lobby to make their specification a de facto standard. Either way, the industry's understanding of the term "smart lighting" could be due for an upgrade if new, sensor rich lamps that can be easily connected to the Cloud begin to enter the market.

## Conclusion

Like many new innovations, smart lighting offers compelling benefits in the immediate term, although the capabilities could significantly evolve to deliver even greater benefits in the future. Since IoT technology is advancing at a fast pace, the lighting industry needs to move quickly to keep pace.

Disclaimer: The opinions, beliefs, and viewpoints expressed by the various authors and/or forum participants on this website do not necessarily reflect the opinions, beliefs, and viewpoints of Digi-Key Electronics or official policies of Digi-Key Electronics.
