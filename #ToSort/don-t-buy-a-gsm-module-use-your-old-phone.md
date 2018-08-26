# Don't Buy a GSM Module, Use Your Old Phone!

_Captured: 2018-03-23 at 19:10 from [www.hackster.io](https://www.hackster.io/BuildItDR/don-t-buy-a-gsm-module-use-your-old-phone-4b0d4b?utm_source=Hackster.io+newsletter&utm_campaign=fe36349df9-EMAIL_CAMPAIGN_2017_07_26&utm_medium=email&utm_term=0_6ff81e3e5b-fe36349df9-141949901&mc_cid=fe36349df9&mc_eid=1c68da4188)_

![Don't Buy a GSM Module, Use Your Old Phone!](https://hackster.imgix.net/uploads/attachments/450655/bitmap121212_bgl871jsT1.png?auto=compress%2Cformat&w=900&h=675&fit=min)

![](https://hackster.imgix.net/uploads/attachments/450657/11111_xoWH6loL99.gif?auto=compress%2Cformat&w=680&h=510&fit=max)

So recently I've been doing a lot of wireless projects, mostly based around a Bluetooth module but since then I've wanted to move on and start making my projects SMS or phone call controlled which is almost just as easy with the help of a GSM module, however, a problem occurred... They're expensive! And so that got me thinking a phone is just a GSM module with more features and I've got a few phones just lying around in my draw, lets just use one of those as a GSM module and that's what we are going to be looking at in this project.

![](https://hackster.imgix.net/uploads/attachments/450663/capture2_XHcD8WkzF6.PNG?auto=compress%2Cformat&w=680&h=510&fit=max)

![](https://hackster.imgix.net/uploads/attachments/450665/capture_L6u96jmseY.PNG?auto=compress%2Cformat&w=680&h=510&fit=max)

So actually salvaging the GSM module from a phone is very hard to do and would take a lot of time and skill so in this project we are going to be taking a slightly different approach.

Whenever a phone receives an SMS or Phone call it either lights up, buzzes or makes a sound. Now knowing this we can take advantage of these features with an Arduino, we will do this by tapping into the phones rumble motor which is used to make it vibrate and then use an Arduino to read data and see when the motor is supplied power thus allowing the Arduino to see went the phone receives an SMS or phone call.

This, of course, isn't as good as having a real GSM module as you can see what data is coming through or be able to send data back but it is a cheap option if you have a bunch of phones just lying around collecting dust.

![](https://hackster.imgix.net/uploads/attachments/450668/capture4_skM4GrTfDG.PNG?auto=compress%2Cformat&w=680&h=510&fit=max)

![](https://hackster.imgix.net/uploads/attachments/450667/capture5_9QF684PYU4.PNG?auto=compress%2Cformat&w=680&h=510&fit=max)

![](https://hackster.imgix.net/uploads/attachments/450666/capture3_ybB7eqWDnK.PNG?auto=compress%2Cformat&w=680&h=510&fit=max)

So this is a pretty simple project so we won't be needing many parts, all we need is the following:

  * Any sort of old phone (I'm using an old blackberry)
  * Some LEDs
  * A Simcard

Now with the way I've set it up the phone it will only be making an LED blink when it receives an SMS, I've done this just to get the point across, I hope to use this in a future project to control the lighting in my room.

![](https://hackster.imgix.net/uploads/attachments/450674/giphy_QxFlX6c3kU.gif?auto=compress%2Cformat&w=680&h=510&fit=max)

![](https://hackster.imgix.net/uploads/attachments/450670/capture6_idn9M4Ps3a.PNG?auto=compress%2Cformat&w=680&h=510&fit=max)

Okay so the goal of this step is to take the phone apart to the point where we can access the rumble motor, now this is different for every phone but for the most part, you can just google the part number of the phone to see where the rumble motor is.

Once you've found it we are going to need to solder two wires to each terminal of the rumble motor. Now, this can be tricky as on most phones use tiny surface-mount components, the key is just to use minimal amounts of solder and very small wires. Once the wires are soldered on we need to connect them to a multimeter for two reasons, firstly we want to see what kind of voltage the phone is supplying and secondly is to figure out which wire is negative and which is positive. I found on my blackberry curve the phone supplied about 1.5 Volts to the motor which will great with the Arduino.

![](https://hackster.imgix.net/uploads/attachments/450671/led3_XNoPFy0HaE.png?auto=compress%2Cformat&w=680&h=510&fit=max)

Again the wiring is pretty simple all we need to do is connect everything as follows.

The ground pin on the motor gets connected to the ground pin on the Arduino then the positive pin on the motor gets connected to A0 on the Arduino and then lastly the cathode (-) of the LED gets connected to ground on the Arduino and the Anode (+) gets connected to pin 7.

With that done we can upload the code.

Again the code is also really simple and pretty easy to understand.

In the void setup, we are saying that we say that pin 7 is going to act as an output as this will be our LED pin, then down in the void loop, we say that sensorValue is the analog value of pin A0 which is then used in an if statement.

This if statement states that if the sensorValue is above 50 to turn on pin 7 which is the LED pin and send back "Rumble On" to the serial monitor and if the sensorValue is below 50 to keep the LED off and send back "Rumble Off" to the serial monitor.

Open the code in the Arduino IDE, upload it to your board and give it a test.

![](https://hackster.imgix.net/uploads/attachments/450673/capture1_Qitm5v15Zh.PNG?auto=compress%2Cformat&w=680&h=510&fit=max)

So now with everything done lets take a look at what everything does, when we send the phone an SMS it sends the signal to the rumble motor which then sends the signal to the Arduino, turning on the LED and sending the Rumble On to the serial monitor.

Now I made this project because I plan to use it in my future project which is making an SMS controlled light for my room but you could really use this anywhere, for example, we could use it in the wireless Arduino controlled blinds from a past project or even the wireless Arduino door lock.

As always if you have any questions ill be happy to answer them and thanks for checking out my project!
