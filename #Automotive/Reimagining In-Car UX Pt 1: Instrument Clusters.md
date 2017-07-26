# Reimagining In-Car UX Pt 1: Instrument Clusters

_Captured: 2016-11-05 at 09:11 from [uxdesign.cc](https://uxdesign.cc/re-imagining-instrument-clusters-in-cars-be0bb4afd5b6?source=userActivityShare-c79006fee040-1478333453)_

![](https://cdn-images-1.medium.com/freeze/max/30/1*fpv07jWNuR6uBbAI77ZhSw.png?q=20)![](https://cdn-images-1.medium.com/max/2000/1*fpv07jWNuR6uBbAI77ZhSw.png)

This project started as a solution to one of my biggest pet-peeves with controls within vehicles. Automobiles have been evolving over time, and with 17-inch touchscreen displays within cars, the way humans interact with the vehicle has been changing too. A driver's primary focus usually is considered to be driving and navigating the car safely. With the advent of multiple features creeping into vehicles that enable the drivers to even Tweet while driving, there seems to be a drift from what is a priority while driving. The self-driving cars are here, sure, but not yet entirely. The roads have a very few cars that drive themselves, and that for very limited stretches, but the majority is still driven by humans, and are prone to human mistakes. My intention was to get into the space of driver-machine interaction and find potential opportunity spaces for improvement of existing systems.

### Current Landscape

To get a feel of what the current experience within vehicles looks like, I decided to do a quick study of the different existing technologies within vehicles that address various aspects of a driving experience.

Tesla currently in Model S boasts a 17 inch screen as the central console, and a digital instrument cluster that displays information such as mileage, power consumption/efficiency, projected mileage and stats over time as graphical visualization. There seems to be an overload of information on the screen, and the complete functioning of the vehicle can be modified on, on the central console. Yes, Tesla cars are going to drive themselves soon, but how much of screen-time do they require now?

[Navdy](https://www.navdy.com) is a heads-up display (HUD) and voice controlled solution to navigation, phone and music control. It possesses capabilities such as posting an update on Twitter, Facebook etc and reading notifications of one's mobile device. It consits of gestures to answer, end and make calls. The gestures require one to take their hands off the wheel.

#### Mazda 3/Audi

Sleek circular analog controls that are present in the Mazda 3 and some models of Audi help the driver with easy navigation between menus on the screen. This again, requires the driver to shift their hand position away from the steering wheel. There exists multiple tiny buttons around the analog knob which requires precision for very particular functions such as navigation, change in volume and returning to previous menu items. This change in functions while driving can be quite arduous a task and sometimes even lethal.

Based on some primary research, I noticed that looking at warnings, indications and other information on the instrument cluster (IC) required the least attention off of the road. Controls on the steering wheel are literally quite "handy" and incase of an emergency when the road requires the driver's attention, the hands are still on the wheel to maneuver to safety.

So I decided to breakdown the existing instrument cluster and understand what are the different items that are displayed behind the steering wheel. I observed multiple instrument clusters and listed the most common indicators present .

  * Tachometer  
The meter on the IC that specifies the revolutions per minute the engine revs at.
  * Warnings  
Warnings such as door ajar, seatbelt indication, check-engine, park-mode/handbrake initiated
  * Modes -- Drive, Parking, Neutral & Reverse
  * Indicators  
Status indicators such as headlight mode, hi-beam mode, fuel indication etc
  * Mileage  
The projected mileage for which the vehicle can travel.

I decided to talk to people to understand what their perception of the instrument cluster is, what information they look for currently, what are some of the existing pain-points in the car they owned, and what are some of the activities they perform that could be potentially dangerous while driving.

I interviewed a few people who have been driving in the United States for over five years, and are quite seasoned to the roads and conditions here. All the drivers mentioned they use their phones while they drive specifically for checking routes to a place or attending/making calls. Most of them had their phones paired to their music system and used their phones to control music as well. An interesting insight from talking to them was that none out of the five paid much heed to the tachometer on the instrument cluster. The interviewees had pretty interesting things to say about the tachometer --

> "I understand the need of the tachometer on a manual transmission, but I have never quite looked at the big dial there ever since I have been driving automatic transmission." -- Interviewee 1

> "I have never quite looked at that portion. Now that you ask me, I think that information is quite pointless to me." -- Interviewee 2

> "Probably on a climb I look at the meter to understand how my car is fairing, but otherwise when I drive within the city, I hardly notice its existence." -- Interviewee 3

On talking to them about their activities in the vehicle, I noticed that their existing systems only allow them to increase/decrease volume and answer phone calls without taking the hands off the wheel; for every other action such as -- changing music, calling a person from their favorites/recent list, changing music source etc -- all required a conscious effort by changing their line of sight to the console at the center.

On understanding pain-points and observing potential hazardous scenarios that could occur because of existing systems, I decided to work on a system that does not require the driver to take their hands off the wheel, thereby aiding in maintaining their attention on the road without distracted attention. Voice controlled systems such as Navdy helps with keeping the attention on the road, but the overwhelming features such as the ability to Tweet, update Facebook status and check phone notifications encourages bad behavior while driving. I thought of alleviating this problem by giving the driver access to important information contextually and on demand.

The console is divided into three segments; the first and the third segments can be controlled with direct mapping of controls which would be located on the steering wheel. The center/second segment is for consumption of data alone. Both the controls have a method to activate voice control that acts as a trigger for the system to start listening to the driver for commands.

> _The console is divided into three segments -- 1\. On the left is the map and navigation 2. At the center is the information segment that consists of information that is relevant to the current status of the vehicle. 3. On the right is the control segment where one can change music, call recent/favorite contacts and check weather at checkpoints of weather change._

There exists two controls, one located on the left side of the steering and the other on the right. They are directly mapped on to the first and third segments of the instrument cluster.

A simple dial-shaped control with a central button which when long pressed activates voice control (just like how Siri works) -- on pressing the central button on the left dial, the system listens for specifically commands pertaining to map/navigation to places.

The control on the right is a tad-bit more complex than the one on the left, but its limited functionality makes it easy to comprehend and use. The central button works the left-control -- it is voice controlled on long press, and this is a lot more intelligent and context aware. It helps with changing music source, calling people from favorites, playing songs from the selected source and also checking the weather based on the time mentioned. There exists controls to quickly increase/decrease the volume and ways to attend or decline calls.

The warning systems are embedded within the information segment where it informs drivers if they are over-speeding -- this information is obtained from the current location and its respective speed-limit. Other indicators such as check-engine, parking brakes, seat-belt warning and door-ajar warnings are indicated at the bottom section of the screen. There exists an indication of the projected range the vehicle can travel before it runs out of gas/power.

As a driver gets into the vehicle and turns the vehicle on, all she sees is the central segment. The other two segments are blank and are not active until the driver wants them to be. This helps with focusing on the road more by keeping the distraction to a minimum.

The navigation is embedded within the instrument cluster. This does not require the driver to look at phone, or any other device located elsewhere. This is positioned right within the line-of-sight of the driver and makes navigation easier when guided by voice.

> _The driver long presses the control on the left, dictates the destination, the system suggests location to navigate to and the driver selects one._

The warnings in the vehicle stand-out from the other elements thereby making it hard to miss.

Music control, recently contacted list from one's phonebook and the weather details can be accessed. The music and contact list is synced to one's phone and accessed from the paired device. The weather list indicates the points of the day when there is a significant change in weather/temperature.

> _The right segment is not visible until the driver taps on the dial on the right. Shifting between the tab options of Music, Phone and Weather follows a very natural action where one just slides right to get to the next tab, and left to get to the previous tab._

The voice control across the tabs is common, and the system understands if the command is directed towards Music, Phone or Weather.

> _This command brings up options to change the music source, the generated list is based on the applications installed on the device that is paired with the system._

The idea behind this instrument cluster reimagination is to provide a distraction-free environment that puts _concentration on the road _at the forefront of the priority list. By eliminating elements such as the tachometer, by creating an experience where the IC is passive in nature, and a voice controlled system that enables drivers to perform common actions without taking their eyes off the road, this system aims at creating a safer experience while driving.

In consequent parts of this series, I aim to rethink the way humans interact with interfaces within cars. In addition, by looking through a systemic lens, I aim to reimagine the nature of car consoles as well.
