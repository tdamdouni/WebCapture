# Augmented-reality projection lamp with Raspberry Pi and Android Things

_Captured: 2018-05-11 at 16:48 from [www.raspberrypi.org](https://www.raspberrypi.org/blog/augmented-reality-projector/?contactID=597763cf47fbc0f7fccab6d8&emailID=5af592b4597ed771f9ee971e&utm_campaign=Newsletter+11.05.18_5af592b4597ed771f9ee971e&utm_medium=email&utm_source=newsletter)_

If your day has been a little fraught so far, watch this video. It opens with a tableau of methodically laid-out components and then shows them soldered, screwed, and slotted neatly into place. Everything fits perfectly; nothing needs percussive adjustment. Then it shows us glimpses of an AR future just like the one promised in the less dystopian comics and TV programmes of my 1980s childhood. It is all very soothing, and exactly what I needed.

## Creating augmented reality with projection

We've seen plenty of [Raspberry Pi IoT](https://www.raspberrypi.org/blog/getting-started-with-iot/) builds that are smart devices for the home; they add computing power to things like lights, door locks, or toasters to make these objects interact with humans and with their environment in new ways. [Nord Projects](http://nordprojects.co/)' _[Lantern](https://experiments.withgoogle.com/lantern)_ takes a different approach. In their words, it:

> imagines a future where projections are used to present ambient information, and relevant UI within everyday objects. Point it at a clock to show your appointments, or point to speaker to display the currently playing song. Unlike a screen, when Lantern's projections are no longer needed, they simply fade away.

_Lantern_ is set up so that you can connect your wireless device to it using Google Nearby. This means there's no need to create an account before you can dive into augmented reality.

![Lantern Raspberry Pi powered projector lamp](https://www.raspberrypi.org/app/uploads/2018/05/lantern.gif)

> _Your own open-source AR lamp_

Nord Projects collaborated on _Lantern_ with Google's Android Things team. They've made it fully open-source, so you can find the code on [GitHub](https://github.com/nordprojects/lantern) and also download their parts list, which includes a Pi, an IKEA lamp, an accelerometer, and a laser projector. Build instructions are at [hackster.io](https://www.hackster.io/nord-projects/lantern-9f0c28) and on GitHub.

This is a particularly clear tutorial, very well illustrated with photos and GIFs, and once you've sourced and 3D-printed all of the components, you shouldn't need a whole lot of experience to put everything together successfully. Since everything is open-source, though, if you want to adapt it -- for example, if you'd like to source a less costly projector than the snazzy one used here -- you can do that too.

![components of Lantern Raspberry Pi powered augmented reality projector lamp](https://www.raspberrypi.org/app/uploads/2018/05/lantern2.jpg)

The instructions walk you through the mechanical build and the wiring, as well as installing Android Things and Nord Projects' custom software on the Raspberry Pi. Once you've set everything up, an accelerometer connected to the Pi's GPIO pins lets the lamp know which surface it is pointing at. A companion app on your mobile device lets you choose from the mini apps that work on that surface to select the projection you want.

The designers are making several mini apps available for _Lantern_, including the charmingly named _Space Porthole_: this uses [Processing](https://www.raspberrypi.org/blog/processing-making-art-code/) and your local longitude and latitude to project onto your ceiling the stars you'd see if you punched a hole through to the sky, if it were night time, and clear weather. Wouldn't you rather look at that than deal with the ant problem in your kitchen or tackle your GitHub notifications?

What would you like to project onto your living environment? Let us know in the comments!
