# Introduction to Electronic Sensors

_Captured: 2018-07-27 at 07:41 from [blog.hackster.io](https://blog.hackster.io/introduction-to-electronic-sensors-6d3a2e72ab98?mc_cid=b05b143225&mc_eid=1c68da4188)_

Electronic sensors can detect everything from light to distance to acceleration. Sensors are how a product senses anything in the real-world, and there is an almost endless array of them available.

Sensors measure real-world quantities, which are then converted into an electrical signal. Actuators, on the other hand, take an electrical signal and convert it into a physical form. For example, motors and speakers are two of the most basic types of actuators.

![](https://cdn-images-1.medium.com/freeze/max/60/0*MrHXKP5eXX3K6otL.jpg?q=20)![](https://cdn-images-1.medium.com/max/1600/0*MrHXKP5eXX3K6otL.jpg)

_This article was originally published on PredictableDesigns.com where electronics and entrepreneurship intersect. Download their free cheat sheet _**_[15 Steps to Develop Your New Electronic Hardware Product_**](http://predictabledesigns.com/15-steps-develop-your-new-electronic-hardware-product/?utm_source=Hackster)**_._**

Sensors are sometimes referred to as input transducers, and actuators as output transducers. Transducer is a very broad term that refers to any device that converts between an electrical quantity and a real-word quantity.

There is such a huge variety of sensors that it would be overwhelming to describe in detail how they all work. Instead, in this article I will give you an overview of the types of sensors most commonly used in consumer applications.

**NOTE: **This is a long, very detailed article so here's a **[free PDF version**](https://predictabledesigns.com/pdf-introduction-to-electronic-sensors/?utm_source=Hackster) of it for easy reading and future reference (includes printer friendly version too).

#### Analog vs. Digital

There are many ways to categorize sensors. One of the most basic ways is [analog versus digital](https://learn.sparkfun.com/tutorials/analog-vs-digital). The difference between analog and digital sensors relates to how the sensor outputs the measured data. It rarely has anything to do with the sensing mechanism itself (motor encoders being a notable exception).

For example, many sensors provide a voltage that varies proportionately with the quantity being measured. This voltage is an analog signal that varies continuously between two voltage thresholds.

> __Figure 1: An Analog-to-Digital Converter (ADC) takes an analog input and outputs a digital signal.__

When that analog voltage is fed into an analog-to-digital converter (ADC) it will be converted into a digital signal. If this ADC is built into the sensor itself then that sensor is digital.

If this ADC is instead located somewhere outside the sensor (typically inside the system microcontroller or an ADC chip) then the sensor is analog.

Digital sensors are usually preferable if their price and specifications are acceptable. This is because digital sensors are less susceptible to electrical interference and they have a lower design risk.

#### Sound

One of the most prevalent types of sensors are sound sensors, better known as microphones. A microphone converts the air pressure variations of a sound wave into an electrical signal.

> __Figure 2: Conversion of audio information into an analog electrical signal followed by analog-to-digital conversion (ADC). The audio is processed digitally then eventually converted back into analog by a digital-to-analog converter (DAC) to drive a speaker.__

There are several different ways of accomplishing this audio-to-electrical conversion but the most common [types of microphones](http://www.shure.com/americas/support/find-an-answer/difference-between-a-dynamic-and-condenser-microphone) are: dynamic microphones, condenser microphones, and piezoelectric microphones.

A dynamic microphone uses a coil suspended in a magnetic field. A condenser microphone uses a vibrating diaphragm as the plate of a capacitor, and a piezoelectric microphone uses a crystal.

One of the most common types of condenser microphones is the electret microphones. They also happen to be one of the cheapest types of microphones.

MEMS microphones are extremely small microphones fabricated on a silicon chip and are usually based on a condenser microphone design. Many MEMS microphones also embed an analog-to-digital (ADC) converter thus providing a digital output.

#### Temperature

Temperature sensors are the most commonly used type of sensor. This is partially due to the fact that so many microchips include simple, built-in, temperature sensors that will shut a chip down if it begins to overheat.

The three most common types of [temperature measurement sensors](http://www.enercorp.com/temp/Thermistors_comparision.html) are: thermistors, RTD's, and thermocouples.

A thermistor is a device made from a metal oxide material that decreases in resistance as temperature increases. Because of this reverse effect thermistors are also referred to as a Negative Temperature Coefficient (NTC) sensor.

The primary advantage of thermistors is they are cheap and easy to use. The critical disadvantage of thermistors is they are very non-linear. This non-linearity limits the temperature range in which they can accurately be used.

However, unless you require extremely high accuracy, or measurements higher than hundreds of degrees, then thermistors are likely the best choice for your product.

Resistance Temperature Detectors (RTD) and thermocouples are primarily used in industrial applications where accuracy and the ability to measure very high temperatures is more critical. RTDs are the most accurate temperature sensor, but also the most expensive.

Thermocouples are primarily used in industrial applications above 600° C.

#### Humidity

Humidity sensors measure relative humidity. They are coupled together with a temperature sensor, because to measure relative humidity you must know the temperature.

Relative humidity is a percentage that refers to how much water the air is holding compared to the maximum amount the air can hold. It is a measurement of the evaporating power of the air.

The higher the temperature the more water air can hold. This means that temperature has a direct impact on the measurement of relative humidity.

#### Barometric Pressure

Barometric pressure sensors are widely available. Since barometric pressure decreases as you go up in altitude, they are commonly used to measure altitude.

On the other hand, since pressure increases as you go deeper under water, barometric sensors can also be used for measuring water depth. Finally, barometric pressure sensors are used for weather forecasting devices.

#### Force / Weight

The most common device for measuring force or weight is called a [strain gauge](https://predictabledesigns.com/introduction-to-load-cell-conditioning-circuits/). A strain gauge is basically a piece of metal that bends a small amount when a force is applied to it. This bending changes the resistance of the metal which can then be measured and converted into a weight.

> __Figure 3: Pictorial showing how a strain gauge works.__

The change in resistance for a strain gauge when bent is extremely small, so strain gauges are formed into what is called a Wheatstone bridge. Wheatstone bridges are very accurate electrical circuits used to measure very small changes in a resistance.

#### Electrical Current

Current sensors are typically an internal sensor used to measure current somewhere else on the same PCB. Of course there are exceptions, like a multi-meter used to measure current.

The standard method of measuring current is to use a small, sense resistor. The current you wish to measure passes through this resistor and creates a voltage drop across the resistor which can be measured. This voltage drop can then be used to calculate the current through the resistor using Ohm's Law.

#### Gases

There are electronic sensors available that can measure numerous different gases. Some of the most common gas sensors are for detecting carbon monoxide, carbon dioxide, and oxygen. But you can also find sensors for detecting everything from hydrogen to hydrocarbons.

#### Accelerometer

Accelerometers measure _proper acceleration_, which is acceleration in relation to free fall. For example, an accelerometer in free fall will actually measure zero acceleration, whereas a stationary accelerometer will measure 9.8 m/s2due to the Earth's gravity (defined as 1-g).

One of Albert Einstein's great discoveries was that acceleration and gravity are equivalent (hence the name _equivalence principle_).

Most accelerometers measure acceleration along three axes and can determine orientation in reference to the vertical direction of gravity.

By detecting the direction of Earth's gravity it's possible to determine the accelerometer's tilt angle using simple trigonometry. This is how smartphones detect whether you are holding the phone in portrait or landscape mode.

An accelerometer can only measure vertical orientation in relation to gravity, but not detect lateral orientation such as measured by a compass.

Accelerometers are also used to detect vibration, impacts, changes in direction or orientation, or if the device is dropped.

#### Gyroscope

Gyroscopes measure angular velocity (rate of rotation). They do not measure absolute orientation.

Like accelerometers, [gyroscopes](https://www.livescience.com/40103-accelerometer-vs-gyroscope.html) are usually tri-axial and measure angular velocity along three axes. Gyroscopes are many times combined together with a 3-axis accelerometer to form what is known as a 6-axis _Inertial Measurement Unit_ (IMU).

Initially, IMU's were used primarily in unmanned aircraft and satellites. Now they are used extensively in consumer electronic products like smart phones, fitness trackers, drones, and any device that needs to detect how it moves through space.

#### Magnetometer

A magnetometer is essentially an electronic compass that measures lateral orientation. As its name implies, a magnetometer measures the strength and direction of any magnetic field, but it is mainly used to measure the Earth's magnetic field just like a compass.

Tri-axial magnetometers are commonly combined with a 3-axis accelerometer and a 3-axis gyroscope to form a 9-axis IMU.

### Object Detection and Distance Measurement

#### Inductive / Capacitive

Capacitive sensors use an electric field to detect a nearby object, whereas inductive sensors use a magnetic field. Because of this difference an inductive sensor can only detect metal objects, whereas a capacitive sensor is able to detect both metal and non-metal objects.

Both inductive and capacitive sensors have very limited sensing distances up to about 60 mm.

#### Ultrasonic

Ultrasonic sensors work using sound waves with a frequency significantly above the range of human hearing. The most common applications for ultrasonic sensors are object detection and [distance measurement](https://learn.sparkfun.com/tutorials/sparkfun-inventors-kit-experiment-guide---v40/circuit-3b-distance-sensor). When used to detect objects under water, or to measure water depth, an ultrasonic sensor is referred to as _sonar_.

Unlike the passive sensors described previously, an ultrasonic sensor is really a bi-directional transducer that includes both a sensor (microphone) and an actuator (speaker).

Ultrasonic sensors contain an ultrasonic speaker that sends out ultrasonic sound waves. These waves propagate from the speaker until they hit an object. They then bounce back toward the sensor.

> __Figure 4: Pictorial showing echolocation using an HC-SR04 ultrasonic module.__

The actual sensor then detects these returned audio waves. By measuring the total travel time of those audio waves it's relatively easy to calculate the distance from that object since sound waves travel at a known speed. This is called echolocation and is the same process used by bats and dolphins.

Consumer grade ultrasonic sensors can typically detect objects at distances anywhere from a couple centimeters up to 10 meters.

The HC-SR04 is a very common ultrasonic module commonly used by makers, but also appropriate for higher volume production. It is a simple, low-cost module that includes both the ultrasonic sensor (microphone) and actuator (speaker). It has a range from 2 cm up to 4 m.

#### Light Sensors

Light sensors are an extremely broad sensor classification that covers a huge number of applications. One of the simplest applications of a light sensor is to detect ambient light levels. For example, outdoor lights that turn on automatically at dusk use a light sensor.

Semiconductor photodiodes and phototransistors are the two most common types of light sensors. When photons of light strike the device they generate electrons which produce an electrical current. This current can be easily measured and converted into a measurement of the ambient light.

Another common application of a light sensor, without a corresponding light emitter, is known as passive infrared (PIR) sensing. They are called passive because they do not emit infrared, they only detect it.

> __Figure 5: Example of a motion activated PIR sensor with a Fresnel lens.__

A PIR sensor measures the infrared light radiating from warm objects in its field of view. Any object above absolute zero (-273° C) emits electromagnetic radiation (usually infrared) which can be detected by an light sensor.

PIR sensors are most commonly used to detect the motion of people, animals or objects. Motion-activated outdoor lighting and burglar alarm systems use PIR sensors.

Most PIR sensors are coupled with a special type of optical lens called a Fresnel lens. This lens breaks the sensors field of view into segments so the sensor can detect small increments of motion.

Many of the really cool capabilities of light sensors shine (no pun intended) when coupled with a light emitter (actuator).

The simplest application is for detecting when an object passes between the transmitter and the sensor thus breaking the light beam. Typically, infrared light is used which isn't visible to the human eye. This is how most garage door openers detect if something is in the way of the door closing.

Light transmitter/sensor combos are also used as optical encoders to measure the position and speed of a motor. A pattern of openings allows light to shine through when the motor is at specific positions. Light sensors on the other side detect the light passing through these holes allowing the system to determine the rotational position of the motor.

#### Time-of-Flight / LiDAR

In the past, if you wanted to measure the distance to a nearby object, ultrasonic sensors were your only option. You will recall that ultrasonic sensors measure distance by timing the sound waves reflected off the detected object.

Measuring relatively short distances with light is much more complex, due to the difference between the speed of light and the speed of sound. Sound travels around 750 miles per hour, whereas light travels almost a million times faster at an incredible 186,000 miles per second!

But special light sensors called Time-of-Flight sensors are now available that can accurately measure distance by timing the flight time of the light beam. Semiconductors didn't became fast enough to make this possible until the 2000's.

ST Microelectronics offers two very impressive, low-cost [ToF sensors](https://www.st.com/en/imaging-and-photonics-solutions/proximity-sensors.html?querycriteria=productId=SC1934). The ST VL53L0X claims to be the world's smallest ToF sensor measuring just slightly over 2 mm x 4 mm x 1 mm. Their longer range VL53L1X model is a fraction of a millimeter larger on each dimension but increases the operating range from 2 meters to 4 meters.

LiDAR is an acronym for _light detection and ranging_, or a combination of the words _light _and_ radar_. LiDAR uses ToF sensors to map out a 2D or 3D area. For example, if you mount a ToF sensor on a rotating motor you can accurately map out a 360 degree area of nearby objects. Even more complex systems can perform this scanning in 3 dimensions, serving as a 3D scanner.

Many sensors may claim to be LiDAR but in reality they use lower cost LED light emitters, whereas true LiDAR solutions use lasers to generate the narrow beam required for accurate 2D/3D mapping applications.

#### Gesture Sensors

Another use of light sensors is for detecting human gestures. Advanced video game systems use lasers, specialized cameras, and fast processors to detect complex gestures like hitting a baseball.

> __Figure 6: Video games and virtual reality applications use advanced gesture recognition.__

Such advanced gesture sensors are not appropriate for more simple gesture detection applications. For simple gesture sensors that can be easily integrated with a microcontroller, it is best to instead use less costly infrared LED emitters.

A simple gesture sensor may have two IR emitters with a sensor in the middle. This type of sensor can detect when and in what direction an object passes by. This allows implementation of simple gestures like a hand swipe.

The ST VL53L0X time-of-flight sensor that I mentioned above can also be used for simple gesture detection.

### Conclusion

This article has given you a general overview of most types of sensors commonly used in consumer electronic products (and some industrial applications).

Now that you know what type of sensors are realistically available you can learn more about the specific ones needed for your project. Here's a nice [tutorial series](https://www.electronics-tutorials.ws/io/io_1.html) for learning more specific, technical details about the most frequently used sensors.
