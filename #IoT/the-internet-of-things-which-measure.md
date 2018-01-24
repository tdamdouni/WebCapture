# The Internet of Things Which Measure

_Captured: 2017-10-10 at 15:13 from [dzone.com](https://dzone.com/articles/the-internet-of-things-which-measure?edition=329543&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202017-10-10)_

Discover why [Bluetooth mesh](https://dzone.com/go?i=250336&u=https%3A%2F%2Fwww.bluetooth.com%2Fwhat-is-bluetooth-technology%2Fhow-it-works%2Fle-mesh%3Futm_campaign%3Dmesh%26utm_source%3Ddzone%26utm_medium%3Dpre-post-article-text%26utm_term%3Dbluetooth-mesh%26utm_content%3Doct-pre-post-mesh-section) is the next evolution of IoT solutions. Download the [mesh overview](https://dzone.com/go?i=250336&u=https%3A%2F%2Fwww.bluetooth.com%2Fwhat-is-bluetooth-technology%2Fhow-it-works%2Fle-mesh%2Fmesh-tech%3Futm_campaign%3Dmesh%26utm_source%3Ddzone%26utm_medium%3Dpre-post-article-text%26utm_term%3Dtech-overview%26utm_content%3Doct-pre-post-mesh-tech).

I went back and forth over this title versus, "The Internet of Measuring Thingies," but neither seemed to communicate what I was trying to say. So here it is spelled out in way too many words for a title.

The Internet is full of things that have the ability to measure other things. Those things being measured might be temperature, pressure, voltage, and so on.

One example is my ecobee thermostat, which has a thing to measure the temperature in my house, along with software which controls my heater. The software in ecobee is smarter than a standard thermostat in that it can control the future. Part of the programming is to tell the thermostat when you want your house to reach a certain temperature, for example when you get up in the morning, and the software will use information from several sources to help it determine when it should command the heater to fire up. To perform this feat of magic, the software has access to information outside of its immediate span of control:

  1. Using your location and information sourced from the Internet, it knows the weather conditions and the temperature outside of your home.

  2. Using historical data from your own home, it knows how long the heater needs to run to move from a source temperature to a target temperature based on the outside weather and temperature.

  3. Ecobee also knows how #2 can be changed if it does some temperature "tweaking" before your target time. In other words, if ecobee can run the heater for short periods of time to keep the house warmer than the minimum set temperature, can it meet your target temperature at the target time with less overall use of energy?

You can see that a lot is involved here. But what happens if one of the measurements is off? For example, if the time is incorrect, ecobee might turn on the heat late causing me to stay bundled in bed even though I need to get up to go to work. Or if the inside temperature is off a few degrees, ecobee could make the house warmer than it needs to be, wasting energy.

## The Industrial Revolution

Let's take this up a notch to a more industrial scale. You may have read about the Stuxnet worm and how it compromised hundreds of Iranian uranium-processing centrifuges. What you may not know is that it adjusted the rotation speed from the normal 63,000 rpm by one-third to 84,600 rpm for fifteen minutes, thus causing them to fail.

But what if the perpetrators of Stuxnet couldn't get to the computer control systems? Why not cause the measurement system to send the wrong reading? In this example, the centrifuges are running at the correct speed, but the speed sensors have been modified to under-report by about a third, so that the computer orders them to speed up.

## Kill the Messenger

In his book [Protecting Industrial Control Systems from Electronic Threats](https://www.amazon.com/Protecting-Industrial-Control-Systems-Electronic/dp/1606501976), Joseph Weiss says that the field controllers, sensors, and emission controls which measure many of our industrial control systems are easy to attack because they are often in remote, under-secured locations.

Just like the Iranian centrifuges were destroyed, altering the readings sent back by many sensors could cause catastrophic failure. Imagine if a gas pressure sensor was sending under pressure readings to the control computer, which kept raising the pressure to meet the requirements. Something like the [recent explosion](https://www.youtube.com/watch?v=EZ6YbUrnxVM) in San Bruno, CA could happen; massive property damage due to a gas line which couldn't handle excessive pressure.

Weiss says the problem is due to the fact that field controllers, sensors, and emission controls are not authenticated, and whatever they send is accepted as the truth.

## Take Action Now

In his book, Mr. Weiss makes a compelling case for advancing higher education in the industrial control field and the need for new certification programs. Taking the idea further, there are other potentially valuable principles to improve IoT safety:

Industrial control sensors could be built with unchanging electronic serial numbers while the firmware and software could be hashed and signed with cryptographic certificates.

  * If a new sensor appears it should be authenticated. If the authentication fails, the sensor data should be ignored but reported.

  * If an existing sensor goes offline and comes back online without authorization, an alarm should be raised and the reason investigated.

  * When an existing sensor comes back online, it should be authenticated. If unauthorized re-programming has taken place, the authentication should fail.

The IoT revolution is here. Risks and all.

Take a deep dive into [Bluetooth mesh](https://dzone.com/go?i=250337&u=https%3A%2F%2Fwww.bluetooth.com%2Fwhat-is-bluetooth-technology%2Fhow-it-works%2Fle-mesh%3Futm_campaign%3Dmesh%26utm_source%3Ddzone%26utm_medium%3Dpre-post-article-text%26utm_term%3Dbluetooth-mesh%26utm_content%3Doct-pre-post-mesh-section). Read the [tech overview](https://dzone.com/go?i=250337&u=https%3A%2F%2Fwww.bluetooth.com%2Fwhat-is-bluetooth-technology%2Fhow-it-works%2Fle-mesh%2Fmesh-tech%3Futm_campaign%3Dmesh%26utm_source%3Ddzone%26utm_medium%3Dpre-post-article-text%26utm_term%3Dtech-overview%26utm_content%3Doct-pre-post-mesh-tech) and discover new IoT innovations.
