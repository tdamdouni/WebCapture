# Can White Hats Protect Us From the Internet of Things?

_Captured: 2017-08-15 at 19:52 from [dzone.com](https://dzone.com/articles/can-white-hats-protect-us-from-the-internet-of-thi?edition=316416&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-15)_

Address your unique [security needs at every stage](https://dzone.com/go?i=216224&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity.html%3Fcmp%3DDZone-SIG-pre) of the software development life cycle. Brought to you in partnership with [Synopsys](https://dzone.com/go?i=216224&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity.html%3Fcmp%3DDZone-SIG-pre).

Anyone who writes about the Internet of Things has a guilty secret: a shameless repository of glee reserved for reports of hacked hardware, the wearer the better. Thanks to the hard work of cybersecurity white hats and researchers we have a glut of tales of their hackings of connected hardware to keep us warm at night. The ubiquity of the Internet of Things means that anything and everything becoming connected from [toilets](http://www.homedepot.com/p/OVE-Decors-Smart-1-piece-1-28-GPF-Elongated-Toilet-and-Bidet-with-Seat-in-White-667580/205451228) to [hair brushes](http://www.kerastase-usa.com/connected-brush), meaning it's open season for those of us with a touch of schadenfreude towards poorly secured IoT. Here are some of my all time favorite IoT hackings, to keep you up at night:

## **Connected Sex Toys**

![Image title](https://dzone.com/storage/temp/6222116-images-1.jpeg)

The weird and wonderful world of smart sex toys is no stranger to security woes, with a tech company [Standard Innovation](http://www.standardinnovation.com/) (parent of We-Vibe) ordered to pay a total of C$4 million to owners of a smart vibrator, the [We-Vibe 4 Plus](http://we-vibe.com/we-vibe-4-plus). The smart vibrator was released two years ago and is marketed towards couples spending time apart. It's Bluetooth- and Wi-Fi compatible and able to be controlled remotely by either partner using a cellphone app called We-Connect. This allows users to control the toy's intensity and vibration patterns. Other features built into the app include private text messages and video calls. A privacy breach emerged at the 2016 [DefCon](https://www.defcon.org/) conference when hackers revealed that the way the vibrator connects with its controlling app wasn't secure - making it possible to remotely seize control of the vibrator and activate it at will. The pair also discovered that the app itself was sending the temperature of the device back to Standard Innovation every minute, and any time the intensity of the vibration changed -- in effect providing data of when and how often someone is using the vibrator. Clear proof that hardware companies do a lousy job at self-policing, security company [Pen Test Partners](https://www.pentestpartners.com/blog/vulnerable-wi-fi-dildo-camera-endoscope-yes-really/) released finding this year that the [Siime Eye dildo camera endoscope](http://www.svakom.net/Siime-Eye/) (yep that's a thing) can be easily penetrated by unforeseen forces to access video data of users thanks to a range of rather bizarre shortcomings.

The Wi-Fi-enabled vibrator comes with a built-in camera for live streaming and an interface that can be hacked by anyone within Wi-Fi range. The web interface of the vibrator is equipped with preset access data (user:, adminpassword blank:), which allows access to the videos of the camera in the radio area of the vibrator. The SSID of the WLAN access point is named directly after the device (meaning there are ample instructions on how to view these videos online). Pen Test attempted to contact the company multiple times without response.

## **Car Hackings Aplenty**

![TeslaHack](https://passportloverblog.files.wordpress.com/2017/08/teslahack.jpg)

Last year we saw [Chinese security researchers](http://keenlab.tencent.com/en/2016/09/19/Keen-Security-Lab-of-Tencent-Car-Hacking-Research-Remote-Attack-to-Tesla-Cars/) take remote control of a Tesla Model S from 12 miles away, targeting the car's breaks, locks, and dashboard computer screen. The vulnerability compromised the CAN bus that controlled many vehicle systems in the car. It required the car to be connected to a malicious WiFi hotspot to take control and worked via the in-car web browser. The vulnerability was confirmed by Tesla's product security team who worked to address the problem.

Tesla was then hacked _again_ in November[ by researchers at Promon](https://promon.co/blog/tesla-cars-can-be-stolen-by-hacking-the-app/), revealing that their experts were able to take full control of a Tesla vehicle, including locating and tracking the car, opening the doors and enabling its keyless driving functionality. Crucially, this was all done by attacking and taking control over the Tesla app and underlines the vital importance of watertight app security.

Tesla cars aren't the only vehicles subject to hacking by researchers. Last year, researchers discovered the [Mitsubishi Outlander](https://www.pentestpartners.com/security-blog/hacking-the-mitsubishi-outlander-phev-hybrid-suv/) hybrid car and [Nissan Leap Cars](https://www.troyhunt.com/controlling-vehicle-features-of-nissan/) were vulnerable to hacking.

Earlier this year, Charlie Miller and Chris Valasek released [all their research](http://illmatics.com/carhacking.html) including (but not limited to) how they hacked a Jeep Cherokee after the newest firmware updates which were rolled out in response to their [hacking of a Cherokee](https://www.theguardian.com/technology/2015/jul/21/jeep-owners-urged-update-car-software-hackers-remote-control) in 2015 where they were able to wirelessly take control of a Jeep using a WiFi connected laptop, enabling them to cut the breaks and transmission (yes, they were able to hack it twice). Those level 5 self-driving cars aren't looking so appealing anymore, hey?

## **Coffee Pot Hacking**

![Screen Shot 2017-08-09 at 12.14.54](https://passportloverblog.files.wordpress.com/2017/08/screen-shot-2017-08-09-at-12-14-54.jpg)

Sometimes it's the little things that resonate and make your day better. In February, Simone Margaritelli, a security researcher at Zimperium, [shared](https://www.evilsocket.net/2016/10/09/IoCOFFEE-Reversing-the-Smarter-Coffee-IoT-machine-protocol-to-make-coffee-using-terminal/) how he was able to hack a [Smarter](https://smarter.am/) coffee machine, a coffee machine that you can control over your home WiFi network using a mobile app.

Ultimately, he was able to decipher how to control the coffee maker directly from the terminal prompt of hi desktop computer, eliminating the need for the mobile app altogether. "By doing so, I was able to successfully automate the coffee-making process that turns caffeine into computer code with unparalleled efficiency--right from my own desktop." Nice one.

## **Connected Health Hacking**

![042514_1605_HckingImpla4](https://passportloverblog.files.wordpress.com/2017/08/042514_1605_hckingimpla4.jpg)

Barnaby Jack was a New Zealand hacker, programmer, and security expert. At the McAfee FOCUS 11 conference in 2011, he [demonstrated the wireless hacking of insulin pumps](https://www.cso.com.au/article/404909/lethal_medical_device_hack_taken_next_level/), one worn by a diabetic friend and another of the same model on a bench set up for demonstration. Interfacing the pumps with a high-gain antenna, he obtained complete control of the pumps without any prior knowledge of their serial numbers, up to being able to cause the demonstration pump to repeatedly deliver its maximum dose of 25 units until its entire reservoir of 300 units was depleted, amounting to many times a lethal dose if delivered to a typical patient.

In 2012, Barnaby Jack showed the Melbourne audience at the[ Ruxcon BreakPoint security conference](https://www.theregister.co.uk/2012/10/17/pacemakers_open_to_wireless_attack/) that a pacemaker could be hacked to kill, by reverse-engineering a pacemaker transmitter that could deliver deadly electric shocks. Unfortunately, we never got to see what he'd make of the latest botnet and ransomware attacks and the proliferation of IoT into everyday life, he died of a drug overdose in 2013.

## **Wind Turbines**

![Wind_turbine_Holderness](https://passportloverblog.files.wordpress.com/2017/08/wind_turbine_holderness.jpg)

This year, researchers from Tulsa University shared with [Wired](https://www.wired.com/story/wind-turbine-hack/) how easy it is to hack a wind farm. They physically broke into the wind farm's control box, quickly unplugged a network cable, and inserted it into a Raspberry Pi minicomputer that had been fitted with a WiFi antenna. Jason Staggs then "switched on the Pi and attached another Ethernet cable from the minicomputer into an open port on a programmable automation controller, a microwave-sized computer that controlled the turbine."

From a remote distance, the researchers were able, via the IP address and a couple of commands on a MacBook, to stop the wind turbine from turning. They were able to enact similar actions at wind farms around the country with the permission of wind energy companies and found that the turbines and control systems they hacked, lacked almost any authentication or segmentation that would prevent a computer within the same network from sending valid commands.

Wired [reported](https://www.wired.com/story/wind-turbine-hack/) that in every case the researchers could send commands to the entire network of turbines by planting their radio-controlled Raspberry Pi in the server closet of just one of the machines in the field.

Thanks to the good work of white hat hackers and security researchers, I could easily write a monthly article on the latest hacks. These aren't isolated incidents, just a snapshot of how bad IoT security is. While I love the insight and innovation that IoT provides to us all, I despair that good security isn't at the forefront of production from the get go and instead is treated as an afterthought by many vendors, if it's considered at all.

Find out how [Synopsys](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity.html%3Fcmp%3Ddzone-sig-post) can help you build security and quality into your SDLC and supply chain. We offer [application testing and remediation expertise](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity%2Fsecurity-testing.html%3Fcmp%3Ddzone-sig-post), guidance for [structuring a software security initiative](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity%2Fsoftware-security-strategy.html%3Fcmp%3Ddzone-sig-post), training, and [professional services](https://dzone.com/go?i=216225&u=https%3A%2F%2Fwww.synopsys.com%2Fsoftware-integrity%2Fsoftware-security-services.html%3Fcmp%3Ddzone-sig-post) for a proactive approach to application security.

Opinions expressed by DZone contributors are their own.
