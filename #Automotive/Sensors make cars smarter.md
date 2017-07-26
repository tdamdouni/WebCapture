http://www.designnews.com/document.asp?doc_id=225450&dfpPParams=ind_184,industry_auto,aid_225450&dfpLayout=article&dfpPParams=ind_184,industry_auto,aid_225450&dfpLayout=article

Sensors make cars smarter

Under the thin metal skin of a modern automobile, a multitude of sensors gathers information so essential that without it the vehicle won't run. The sensors continuously monitor hundreds of vital signs such as ignition and valve timing; exhaust quality; throttle position; intake air temperature and pressure; wheel slippage; tire inflation; steering-wheel position; and even linear and lateral velocity and acceleration.

Next generation automobiles--those due to hit the road in the next five years--will have sensors that do even more. By the year 2002, as you cruise down the road in your new car, sensors will surreptitiously test the condition of the engine oil and battery charge, measure the real-time combustion pressure in each cylinder, calculate the instantaneous torque of the engine, determine the size and position of front-seat passengers, and even scan the road ahead with radar to look for hazards. Engineers are developing or testing sensors to perform those tasks and more today.

Presented here are examples of a few near-term automotive-sensor developments.

Automobiles present engineers with enormous opportunities for future sensor development.
Chassis controllers. A sensor area receiving a great deal of attention falls under the general umbrella of "vehicle stability enhancement." Cadillac calls its entry into this category Stabili-TRAK. And it includes Systron Donner's (Concord, CA) automotive quartz rate sensor, or AQRS. The sensor incorporates the company's patented Gyro-ChipTM technology to measure the car's yaw rate. By combining this measurement with those for steering angle and lateral acceleration, StabiliTRAK can compare actual vehicle dynamics to the driver's intentions, and then gently apply the ABS and traction-control systems to "nudge" the car back in to the expected line.

The GyroChip consists of a microminiature double-ended tuning fork fabricated via photolithography from piezoelectric quartz. An oscillator powers one of the tuning forks--the drive tines--at resonance. And as long as the GyroChip is stationary, the other set of tines--the pickup tines--do not oscillate. As soon as the chip is rotated, however, the pickup tines respond to Coriolis force and begin to oscillate perpendicular to the drive tines and with a magnitude that is proportional to the rotational rate. An amplifier and demodulator convert the signals from the pickup tines to plus or minus DC voltage that is then used by the StabiliTRAK system.

Systron Donner shipped AQRS sensors for the entire production run of 1997 Cadillacs without a single return from the factory, they say. With quality seemingly solved, the goal now is to cut the price to make the sensor more attractive to less expensive cars. "We've got the leading technology," says Phil Lees, automotive sales engineer, "and we're increasing our factory automation to penetrate further into the market."

They'll face competition along the way. Several other companies are offering or pursuing yaw-rate sensors, including Delco Electronics (Kokomo, IN) which revealed to Design News that its engineers are busy developing a micromachined silicon yaw-rate sensor of their own.

Vehicle stability systems such as StabiliTRAK also need a way to measure steering angle. One such entry into this arena comes from ITT Automotive (Auburn Hills, MI). While it does not appear on today's Cadillacs, it will be introduced on several '98 Audi models.

The quartz pickup tines on Systron Donner’s GyroChip respond to Coriolis force to gather yaw-rate information for Cadillac’s StabiliTRAK stability control system.
It operates by passing an LED light beam between a pair of transmitter/receiver elements. A disk with irregularly-spaced slots passes between the elements, alternately blocking and passing the light beam as the steering wheel--and the disk attached to the shaft--rotate. The irregularly spaced slots provide the system with absolute-position information about the steering wheel within about 1 degree. Engineers chose an optoelectronic system partly to avoid problems with possible interference from magnetic fields. "We think it is the most effective and reliable method of measuring steering angle for something that is part of a safety system," says Allen Schwartz, chief engineer at ITT.

Tire telltale. Yaw sensors are far from the only silicon-based sensors on today's cars. Peel back the tires on the new C5 Corvette or Chrysler Prowler, and you'll find micromachined pressure sensors integrated into the tire valve stems mounted to the alloy wheels. Developed by Schrader Electronics (Antrim, N. Ireland) the remote tire pressure monitoring system (RTPMS) gathers inflation information on the fly and transmits the data to a receiver in the car for display on the dash.

It uses a version of the model NPP-301 pressure sensor from Lucas Novasensor (Fremont, CA). Containing an ultra-small Silicon Fusion Bonded piezoresistive chip in a plastic, surface-mount package, the sensor produces a voltage output that is linearly proportional to the input pressure. Engineers at Schrader incorporate the sensor into an injection-molded plastic housing which also contains an ASIC, a radio transmitter section, a centrifugal switch, and a lithium battery, all potted for durability.

Begin driving the vehicle and the centrifugal switch places the RTPMS in "driving mode" in which pressure readings are gathered every 30 seconds and transmitted every 15 minutes. Should a rapid pressure change occur, the system increases transmissions to 30-second intervals as well. Driving mode contrasts with "stationary mode" in which the system wakes up every 15 minutes to take pressure readings, transmitting to the receiver once an hour. Engineers chose these discrete information gathering and transmission routines as a way to maintain performance while obtaining a ten-year battery life.

In the US, RTPMS broadcasts its bitstream of pressure data at 315 MHz, a frequency set aside by the FCC for on-car telemetry systems. In Europe, the favored channel is 433.92 MHz.

Accuracy is claimed to be ±2% full scale between 0 and 50C with a resolution of 1 psi. Still, the biggest engineering challenge wasn't designing a system to gather pressure data, but rather transmitting it. "You don't normally think about designing an RF transmitter that whirls around in a wheel at 60 mph and must transmit through a steel lattice--effectively a Faraday cage--to a receiver which is partly shielded by a metal body, now do you?" says Alastair Johnston, RTPMS marketing manager at Schrader. "It took us five years to develop the system, and it was definitely loads of fun."

Sight from sound. Parking isn't normally considered a life and death driving situation, but the combination of low-speed maneuvers and small children or pets isn't always a good one. Though marketed strictly as a parking aid for snuggling into tight spots and not as a safety system, ITT Automotive's (Auburn Hills, MI) Park Assist can serve double duty in the battle to keep bruises off both bumpers and bodies. Currently manufactured in Bietigheim, Germany, the sensors will also begin rolling off an ITT production line in Rio Bravo, Mexico later this year.

Available on BMW's 7-Series and the '98 Audi A6, Park Assist uses an array of eight ultrasonic sensors to measure distance to objects in front of or behind the car. By combining information from multiple sensors the system can triangulate the position of objects in three dimensions. Its range is 1.5 meters with an accuracy of 1 cm.

The transducers mount behind the bumper fascia and transmit and receive ultrasonic pulses at 38.4 KHz through 12 mm × 17 mm openings. "We chose 38.4 KHz because the dispersion is dependent on frequency," Schwartz explains, "and it gives the right cone of coverage without false readings from things like speed bumps." Each pulse lasts about 2 msec and repeats at 100 msec intervals.

Inside the car, the system informs the driver via a series of audible beeps that increase in frequency as the distance decreases until the sound becomes continuous at a distance of 25 cm. Though any acoustic-based system can be affected by dirt, snow, even thinning air at elevation, Schwartz notes that the transducers are powerful and sensitive enough to cover the 1.5-m range without any electronic compensation. "You can backup towards a wire sticking out of the ground," he says, "and with this system, you'll know it."

  To learn more about some of the advanced automotive-sensor concepts presented here, attend the "Automotive Sensors--Technologies and Applications" session at Sensors Expo Detroit, on October 21, 1997, from 9 a.m.-12 p.m. Details can be found on the Internet at http://www.expocon.com.

Performance under pressure

For decades, engineers have leveraged cylinder-pressure readings to design internal-combustion engines and tune the engine management systems. Soon, this powerful but bulky and expensive tool may find its way under the hood of every production car. And the advantages would be enormous.

"Combustion-pressure sensors are an example where you get a tremendous amount of information from one sensor," says Bob Schumacher, director of the Automotive Electronics Division at Delco Electronics (Kokomo, IN). They would allow engine control to occur in real time and permit the detection of optimal spark and valve timing, resulting in reduced emissions and maximum efficiency, power, and engine life. Along the way "you might be able to eliminate the crankshaft position sensor, misfire sensor, and knock sensor," Schumacher says.

An example of such a sensor has been patented by Marek Wlodarczyk, president and CEO of Optrand (Plymouth, MI). He claims that his fiber-optic pressure sensor can withstand a lifetime of hot, high-pressure measuring--perhaps half a billion pressure cycles--and yet in volume, cost less than $10 each.

It works by delivering LED light down one of two optical fibers aimed at a tiny mirrored diaphragm exposed to the cylinder pressure. The light reflects off the back of the diaphragm and is gathered by the second fiber for analysis. Pressure changes deflect the diaphragm and alter the amount of reflected light entering the second fiber, providing a means of measuring the pressure acting on the diaphragm.

A proprietary "auto referencing technique" regulates the system's LED light output in response to natural fluctuations in transmission efficiency due to temperature, cable bends, connector losses, and aging cable, which would otherwise make the system unusable. "The auto-referencing method is one of the brilliant aspects of this design," says Andrew Gorayski, director of marketing.

The company has also developed a simple way of incorporating their sensor into an engine. By integrating it into a sparkplug, fuel injector, or diesel glow plug, auto manufacturers can incorporate Optrand's combustion-pressure sensor into the engine without having to add another hole in the cylinder head.

Currently, the company has examples running on oil-pipeline stationary engines, where they provide diagnostic and health information that helps predict component failures and reduce downtime.

Capacitive sensor measures oil quality

A unique oil-quality sensor under evaluation by Cummins, Detroit Diesel, and BMW, may someday signal drivers when their oil needs changing. It's based on a low-cost ceramic capacitive sensor that measures variations in the dielectric constant of the oil. New motor oil has a dielectric constant of about 2.19, but after about 400 hours use, the antioxidant additives in the oil break down and the value climbs to roughly 3.20.

The sensor works much like any capacitive sensor. The substance to be measured (oil) passes freely between two small, parallel metal plates spaced roughly 0.010 to 0.020 inches apart. With the area and spacing known, the capacitance value becomes a function only of two values: the dielectric constant of the oil itself, and one major stumbling block--temperature.

"Nobody knew how to block off the temperature effect and only measure the aging of the oil," says Kyong M. Park, vice president of R&D at Kavlico (Moorpark, CA), the sensor's manufacturer. His patented solution: incorporate an analog signal conditioner consisting of feedback resistors for offsets and gain, and select one resistor that changes resistance in direct proportion to oil's dielectric-constant variation with temperature.

Park also overcame a soot contamination problem present in diesel engines. "We developed a special silicon-based coating to prevent the soot from sticking to the sensor," he explains.

A serendipitous advantage of the Kavlico sensor is that water contamination-a fairly common and damaging situation-can also be detected because the dielectric constant of water is 87. "A one-percent contamination of the oil with water or coolant will increase the dielectric constant enough to trigger an alarm," says Park.

Kavlico isn't the only company working on an oil-quality sensor. Control Devices (Standish, ME) has joined forces with the University of Maine to produce one; Sandia National Laboratory has a sensor in development; and SRI International (Menlo Park, CA) has produced a laboratory prototype for a auto-manufacturer customer. Park isn't worried. "{Other methods} measure the oil's acidity, which is less reliable," he says.

Surprisingly, the capacitive concept isn't new. "I remember reading a Popular Science article 30 years ago about this," says Park. "But nobody ever made a production sensor before that could do it."

A new spin on rotary sensors

Lots of things revolve or turn inside an automobile, the crankshaft, the camshaft, the throttle plate, and the wheels, to name just a few. And Bob Bicking, senior engineering fellow at Honeywell Microswitch (Freeport, IL), is working on sensors that will measure their speed and position more accurately and more cheaply than those used today.

For crankshaft/camshaft position sensing, the company has a device still in R&D called the 1.5Q. "The 'Q' stands for quick start," says Bicking. And the sensor's goal it to enable the engine to start quicker for lower emissions.

It improves on existing technologies that are very sensitive to the spacing between the sensor and a magnetic target on the rotary shaft. "This one measures the signal amplitude and adaptively sets the switching point based on the amplitude," he says, thus accommodating a wide range of assembly tolerances without loss in performance.

A second sensing technology, set for probable market entry in 1999 cars, is a Hall-Effect sensor for ABS that operates all the way down to zero wheel speed. It improves upon the variable reluctance sensors commonly used today which output a signal directly proportional to speed. Below about 5 mph they quit supplying information, making them unsuitable for advanced stability and traction-control systems. Bicking envisions the Hall-Effect sensor ultimately replacing the speedometer sensor and even being used for dead-reckoning navigation systems.


You can reach the following companies mentioned in this feature on the Internet. Please tell them that you were referred by Design News.

Delco Electronics:http://www.delco.com

ITT Automotive: http://www.ittautomotive.com

Kavlico: http://www.kavlico.com

Lucas Novasensor: http://www.novasensor.com

Optrand: http://www.optrand.com

Systron Donner: http://www.systron.com
