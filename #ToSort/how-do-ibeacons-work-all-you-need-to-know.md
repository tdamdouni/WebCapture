# How Do iBeacons Work? All You Need To Know

_Captured: 2017-10-07 at 16:01 from [blog.beacongrid.com](https://blog.beacongrid.com/blog/how-do-ibeacons-work?utm_campaign=Blog%20Campaign&utm_content=60837889&utm_medium=social&utm_source=twitter)_

  * ![close up of businessman hand showing texture the world with digital social media network diagram concept Elements of this image furnished by NASA](https://blog.beacongrid.com/hs-fs/hubfs/close%20up%20of%20businessman%20hand%20showing%20texture%20the%20world%20with%20digital%20social%20media%20network%20diagram%20concept%20Elements%20of%20this%20image%20furnished%20by%20NASA-1.jpeg?t=1506443545583&width=2133&name=close%20up%20of%20businessman%20hand%20showing%20texture%20the%20world%20with%20digital%20social%20media%20network%20diagram%20concept%20Elements%20of%20this%20image%20furnished%20by%20NASA-1.jpeg)

> _close up of businessman hand showing texture the world with digital social media network diagram concept Elements of this image furnished by NASA_

In 2012, if you had heard the word "beacon," you might have thought of a lighthouse by the sea or the metaphor "a beacon of hope."

The other beacon, the one we're interested in, is the Bluetooth low energy (BLE) beacon that has recently become[ trendy](https://blog.beaconstac.com/2016/08/top-ibeacon-trends-for-2016/). BLE beacons were popularized by Apple in 2013 when the company unveiled its ibeacon protocol specifying how to use the ibeacon. From there, companies like BeaconGrid have created their own ibeacons that have been proliferated across a variety of industries for versatile uses.

The ibeacon works in a simple way: transmitting BLE signals to BLE-capable devices to induce some sort of action. In conjunction with apps, ibeacons can determine where your device is located within a venue, valuable information that can be used in personalized marketing, navigation, provision of certain accesses, and more. These small hardware devices potentially fill in a need that was unable to be filled by more established locational services, like GPS and WiFi.

[Compared to Eddystone](https://blog.beacongrid.com/blog/5-key-eddystone-beacons-facts), another beacon format, ibeacon is easier to configure and begin using. It is the best option when iOS devices are the majority on the receiving end of beacon signals. As one of the main options, the ibeacon protocol is essential knowledge for anyone who wants to deploy beacons.

**iBeacon aspects: How do ibeacons work? **

iBeacons work by broadcasting a UUID (universally unique identifier) using Bluetooth Low Energy. The UUID is then picked up by an application that can read the value and do something with it, such as determine the location of the user's device or send a notification.

As simple as this function seems, it can get complex. Below, we discuss the configurable parameters of the ibeacon and its partner component, the app.

**Identifiers**

The ibeacon consists of three types of identifiers:

  * Proximity UUID - The proximity UUID differentiates iBeacons from one another. No iBeacon should have the same UUID.
  * Major (optional) - The major value can be used to tag beacons in different groups, e.g. 1 for Boston and 2 for Los Angeles.
  * Minor (optional) - The minor value can also be used to group beacons, e.g. 4 for first floor and 5 for second floor.

The only one that is required for the beacon to work is the UUID. The ID constitutes the extent of data that is broadcasted by a beacon signal.

**Transmission power**

Also known as TX power, transmission power indicates the power of the signals broadcasted by the beacon and is used to tell you how far you are from the beacon. In the beacon protocol, it is the measured signal strength at 1 meter away from the receiving device, or the RSSI at 1 meter.

Many beacons allow you to configure the TX power, and by doing so, changing how far the signals can reach.

**RSSI**

The Received Signal Strength Indication (RSSI) refers to the signal reading that shows up on a recipient device as it picks up a beacon signal and is used with the TX power to calculate the user's location. If the device moves further away from the beacon, the RSSI reliably decreases, and if it moves closer, the RSSI increases. A more detailed explanation of the math can be found [here](http://mobileenterprisestrategies.blogspot.com/2014/05/how-ibeacons-work-for-indoor-location.html).

The RSSI is less configurable and more of a signal that is detected by the receiving device.

**Transmission Interval**

The transmission interval indicates the time interval between the beacon's signals, or how long the beacon "blinks" between transmissions. Beacon devices will often provide the option to configure the Transmission Interval between the values of 100ms (milliseconds) and 1000ms. The lower value correlates with stronger signal stability and greater energy use.

Apple's iBeacon standard calls for an optimal broadcast interval of 100 ms, but this value can be a drain on energy.

**Apps**

iBeacons wouldn't have much function without compatible apps that can unpack the information in the signals and do something from it. Apps use the UUID and readings like the TX power and RSSI to arrive at a proximity location for the user. Apps can also translate this information into user-friendly language, such as "first floor, room 12" or "in the ballroom."

**Core Language framework**

The programming of apps can be a complex process requiring understanding of frameworks, classes, datatypes and other aspects of the programming for mobile apps. One of the main aspects to understand is the [Core Location framework](https://developer.apple.com/reference/corelocation), which lets you determine the current location or orientation of a device. The framework allows the app to use information such as UUID values from iBeacons and to monitor for when the device comes within ibeacon range. It can be used to prompt an action on the device when it is triggered.

Because the Core Location framework is only accessible by iOS apps, iBeacons are most compatible with iOS. iBeacon signals, can be used by Android apps but with varying success. For example, Android apps are unable to be "woken up" from a dormant state by iBeacon signals.

In conclusion, here are a few takeaways from this section:

  * iBeacons broadcast a UUID and can be configured for TX power and Transmission Interval.
  * iBeacons broadcast one-way. This means that they don't collect information from user devices, although the apps on users' phones can. 
  * iBeacons are just half of the equation. The apps that are used with the hardware are just as important (and often more complex to set up) for the beacon's main functions.
  * iBeacons are more compatible with iOS than Android apps.

Learn more about iBeacon's protocol [here](http://www.cisco.com/c/dam/en/us/solutions/collateral/enterprise-networks/connected-mobile-experiences/ibeacon_faq.pdf).

**An ibeacon challenge: Interference**

Deploying technology in the field doesn't come without challenges. One of the main problems with ibeacons is [interference](http://www.enterpriseappstoday.com/crm/implementing-ibeacons-watch-out-for-5-gotchas.html), or the disturbance of signal transmissions caused by unwanted signals from other sources or other beacons.

Bluetooth low energy is a relatively weak signal that can be cancelled out when it clashes with stronger waves from microwave ovens, DECT phones, etc.. Obstacles in the environment, such as walls or large numbers of people or furniture, can create unstable or weakened BLE signals that fall short of their expected ibeacon range. The result might be gaps in signal coverage in the environment. We've written a great beacon deployment consideration article discussing the best practices for beacon placement.

The placement of ibeacons can also generate sources of interference. When beacons are placed too close together, they can create signal overlap. The result is that your mobile app might detect one beacon, and then a second, and toggle between the two. Your app could also give you misreadings of your location, thinking that it's close to a beacon and then far.

While interference is troubling, an advantage to BLE signals is that they exhibit [no interference with WiFi](https://locatify.com/blog/ble-beacons-they-can-coexist/) signals, allowing them to be used at the same time. In fact, BeaconGrid has leveraged this point to create products, like this [outlet](https://www.beacongrid.com/outlet.html), that can work as beacons or sensors by using BLE and WiFi signals.

**Use cases of ibeacons**

**![BallnRoll](https://lh6.googleusercontent.com/xSHJDsVlyNi0n7tuDiGtOYUaFX6D1PWmyCOp1LRSPcOcN4z7wZeSD1L0xBnfv5kLeyRVlW73yD36JeWNiPM9NC-c-kjrILjvZsv23e6dxde2PNGZZmXaE0A7-lFiq8idZe2GF3Da)**

Source: [BallnRoll](http://ballnroll.com/2014/05/new-technology-that-changes-how-well-watch-the-game/)

The list of ibeacon use cases is lengthy and growing. Here are just a handful of applications:

**Asset tracking and operations**

Asset tracking involves associating items or persons with beacons to monitor their location. This information can be useful in ensuring items or persons are allocated efficiently. BeaconGrid's [Real-time location system](https://www.beacongrid.com/presence.html) (RTLS) is tailored for asset tracking and operations. Assets are tagged with or given cards/keys imbedded with beacon technology, which are then tracked by sensors that detect the assets and derive their location at all times within a venue.**   
**

_Be sure to check out our case study on the usage of iBeacons in universities_

**Improved navigation**

![Drone using beacon technology](https://blog.beacongrid.com/hs-fs/hubfs/drone%20bg.png?t=1506443545583&width=960&name=drone%20bg.png)

> _Drone using beacon technology_

The locating ability of ibeacons makes them a powerful aid in navigation. In 2015, [Google invested $1 million in a Wayfindr project](https://techcrunch.com/2015/12/03/wayfindr-open-standard/) that helps blind and visually impaired people move around independently. This project is one of a host of initiatives to improve navigation with beacon technology. BeaconGrid has used its beacons to help a company refine [drone navigation](https://www.beacongrid.com/uses.html).

**Proximity and customized marketing**

Proximity marketing is the idea of engaging customers the moment. Information about the shopper's in-store location can be leveraged to send them deals based on where they are and even their shopping history. Retail marketing is an industry where we already see [a rippling impact](https://www.salesforce.com/blog/2016/01/retail-marketing-trends.html) by ibeacons.

**Smart transportation**

A [recent use case by a Brazilian transportation system](http://www.information-age.com/mobile-technology-transforming-local-transport-brazil-123464794/), BHTrans, shows how ibeacons can be integrated with other technology to improve the efficiency of public transportation. The city found that buses were sometimes overpacked or under-utilized but lacked data on congestion patterns to solve the issue. By integrating beacons at bus stops or on buses, and encouraging its users to submit reports of congestion on the app, BHTrans will be able to amass data, send more buses during congested times and ultimately improve customer experience.

**BeaconGrid is expanding**

There are so many use cases of ibeacons that aren't listed. BeaconGrid has been involved in the above cases and more, including access control, automatic attendance and monitoring in retirement communities [Learn more](https://www.beacongrid.com/uses.html) about the various projects that have involved BeaconGrid. We can't wait to be part of your enterprise.
