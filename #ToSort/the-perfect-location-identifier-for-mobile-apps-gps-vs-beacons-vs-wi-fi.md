# The Perfect Location Identifier for Mobile Apps: GPS vs. Beacons vs. Wi-Fi

_Captured: 2017-07-13 at 11:06 from [dzone.com](https://dzone.com/articles/the-perfect-location-identifier-for-mobile-apps-gp?edition=308191&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-12)_

[Launching an app doesn't need to be daunting.](https://dzone.com/go?i=204132&u=http%3A%2F%2Finfo.perfectomobile.com%2Febook-mobile-app-testing-best-practices.html%3Futm_source%3Dbgm-dzonespon) Whether you're just getting started or need a refresher on mobile app testing best practices, [this guide is your resource!](https://dzone.com/go?i=204132&u=http%3A%2F%2Finfo.perfectomobile.com%2Febook-mobile-app-testing-best-practices.html%3Futm_source%3Dbgm-dzonespon) Brought to you in partnership with [Perfecto](https://dzone.com/go?i=204132&u=http%3A%2F%2Finfo.perfectomobile.com%2Febook-mobile-app-testing-best-practices.html%3Futm_source%3Dbgm-dzonespon).

How often do you search for nearby cafes, movie theaters, or doctors on the internet? The results are more than satisfactory most of the time, provided "Location" is switched on on your device. A GPS chip embedded in your smartphone, when enabled, tracks your location based on the coordinate axis there. A mobile application or web application like Google Maps then maps that information on real world maps, showing exactly where you are. A GPS device needs a continuous link to one or more satellites, in clear sky, to enable its action. That means GPS functionality tends to suffer in indoor conditions or on a cloudy evening.

Mobile applications these days require a location to enhance personalization and makes the user experience more relevant. As a result, mobile app developers are leveraging various new and traditional technologies and methods to make sure a location is available all the time for their apps, whether the device is indoors, outdoors, or it's pouring like there is no tomorrow.

A comparatively newer technology Beacon is very well considered the "GPS of indoor spaces" due to its precise-to-millimeters location accuracy. The adoption of Beacon technology is considerably lower when compared to other location-detection technologies like GPS, Wi-Fi, and RFID, but it's catching on fast as more and more marketers have to come to realize its business value.

Wi-Fi has long been used to improve GPS location. The relative position of a device related to a nearby Wi-Fi hotspot leads to a calibrated position even on a cloudy day or in a partially enclosed space.

Let's compare GPS, Wi-Fi and Beacon technology and conclude which one a mobile developer should include in their app for the most reliable, precise location detection.

## GPS

GPS (or a similar satellite navigation system like the Russian GLONASS and the European Union's Galileo) is the backbone of any outdoor location detection system in the world. GPS powers everything from [bus map navigation](https://www.peerbits.com/case-studies/busmaps-navigation-app.html) (by means of a web mapping app like Garmin) to local search results (with the help of a web search engine like Yahoo! Local Search).

![GPS Location](https://11m5ki43y82budjol1gjvv5s-wpengine.netdna-ssl.com/wp-content/uploads/2017/07/GPS-Location.jpg)

However, as I mentioned earlier, GPS devices are next to useless when an obstruction blocks the satellite link with the device. The obstruction could be anything from a rooftop to clouds.

Geofencing is relatively a new method that inspects location data received from GPS chip inside a smartphone to trigger an action. Many iOS and Android apps today include geofencing APIs to send location-based notifications. The location awareness is generally configured in the app with the help of integrated Maps APIs like the [Google Maps Android API](https://developers.google.com/maps/documentation/android-api/intro).

Geofencing works without any glitches when the defined virtual perimeter or the geofenced area is outdoors, or when the weather is fine. However, as soon as the geofence moves to an enclosed area like a movie theater, the geofence ceases to exist. That means if you updated your movie booking app to direct the viewers to their respective seat by setting virtual boundary across every seat, expect to see a reasonable drop in your App Store ratings.

## Wi-Fi

Wi-Fi wasn't originally developed to detect location. In fact, it was presumed to be a failure in its initial years. When Intel made it a standard across its entire range of laptops, the adoption rate rose exponentially. Educational campuses became adopters and with Wi-Fi routers in mass production and costs falling, Wi-Fi became a global phenomenon.

If you live in a well-inhabited neighborhood, finding 10-20 hotspots on your smartphone screen is not surprising anymore. Wi-Fi is so commonplace these days that app developers assume that a user will always be surrounded by Wi-Fi hotspots.

Finding the location of a smartphone relative to a fixed Wi-Fi hotspot is as easy as adding a line of code to calculate the distance between. With some clever coding, GPS together with indoor Wi-Fi setup can be made to map enclosed spaces like a mall. If you're passing by a Zara store in the aisle, a nearby Wi-Fi hotspot can send you a notification with a coupon code. The entire mechanism can be made to work without an app provided that Wi-Fi radio is active on that device.

## Beacon Technology

Google Eddystone and Apple's iBeacon are the cornerstones of Beacon technology enabled by Bluetooth Low Energy (BLE). Beacon technology can be added to an existing Android or iOS app by means of the aforementioned Beacon profiles.

Mobile apps with either of the Beacon profiles enabled let your device connect to miniature BLE devices normally placed in retail spaces and similar indoor commercial spaces. When a person enters such a space such as a neighboring supermarket with beacons installed, the device in his pocket captures transmitted Bluetooth signals in an encoded form, to be decoded by a Beacon-enabled app.

![iBeacon technology](https://11m5ki43y82budjol1gjvv5s-wpengine.netdna-ssl.com/wp-content/uploads/2017/07/iBeacon-technology.jpg)

If the app can decode the signals, it calculates the absolute position of the device user with respect to the beacon inside the supermarket and sends them a location-aware notification. For example, the app can coordinate with the nearest beacon to send an exclusive offer every time a person is at the shampoo section of the market.

But no technology is perfect. What if the supermarket approaches a Walmart in size, the owner has to install far more devices than he can afford. The range of BLE is 328 feet. Imagine how many devices an over-ambitious perpetuator could install in the larger-than-life 5.9 million square foot Dubai Mall.

But then again, not every commercial space is Dubai Mall. For small to medium commercial or hospitality space, there is no better location identifier than a BLE equipped beacon for your app if it is meant to give direction to shoppers in a retail space.

## Developing Multilingual Mobile Apps

Apps today, by large, tend to have GPS and Wi-Fi based location enabled by default. Since beacons are a relatively new technology, app adoption is still in a nascent state and will grow as more and more retail spaces embrace this simple mobile app technology for business gains.

Unlike Wi-Fi and GPS, beacons don't need dedicated hardware as almost every smartphone, even dumb phones, have a Bluetooth radio included.

The industry expects increased production to lead to increased demand and support from both Apple and Google, and the price of beacon devices will drop sooner than later, which will make even more retailers and hospitality install beacon devices on their premises.

Meanwhile, marketers must prepare for the next revolution called "location-based retail marketing" encapsulated in BLE technology.

This is probably the best time to update your retail mobility app to beacons or, if you're building one from scratch, think "beacon" when you think "location."

[Keep up with the latest DevTest Jargon](https://dzone.com/go?i=204133&u=http%3A%2F%2Finfo.perfectomobile.com%2Fmobile-devtest-dictionary.html%3Futm_source%3Dmmg-dzonespon) with the latest Mobile DevTest Dictionary. Brought to you in partnership with [Perfecto](https://dzone.com/go?i=204133&u=http%3A%2F%2Finfo.perfectomobile.com%2Fmobile-devtest-dictionary.html%3Futm_source%3Dmmg-dzonespon).
