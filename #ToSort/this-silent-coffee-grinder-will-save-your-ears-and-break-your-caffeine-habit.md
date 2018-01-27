# This silent coffee grinder will save your ears and break your caffeine habit

_Captured: 2017-12-21 at 20:16 from [www.theverge.com](https://www.theverge.com/circuitbreaker/2017/12/20/16798042/diy-silent-programmable-coffee-grinder)_

Mornings are hard for a caffeine addict. The headaches and grumpiness are bad enough, but then you have to deal with the noise of the grinder before you get the anti-migraine juice you so desperately crave.

This silent coffee grinder uses a hand grinder and a strong motor to grind coffee slowly and quietly. It connects to the internet, so you can set it to run automatically or run it from your phone. You can even set it to grind less and less coffee over time, imperceptibly reducing your caffeine intake until you're back to more tolerable levels of dependence, or breaking the coffee habit entirely.

The best part? You can build it yourself! Check out the instructions below. If you have questions about the build or are looking for more hacks, find me on Twitter at [@christinesunu](https://twitter.com/christinesunu) or check out [hackpretty.com](http://hackpretty.com).

  * Motor (I used a 12V, 10RPM motor)
  * #6 ⅜ Inch Flat Head Screws (x4)
  * 4-40 ½ Inch Flat Head Screws (x4)
  * Breadboard
  * MOSFET (I used a 30N06L)
  * Particle Electron
  * Jumper Wires
  * Alligator Clip Jumper Wire
  * Barrel Jack Cable Connector Plug
  * 12V Power Supply
  * Electrical Tape

Side note: This is a no-solder project meant to work with a few 3D-printed parts. I'm currently working on something a bit more robust, for those of you who want more solder and metal. If you're interested, [get in touch](https://www.hackpretty.com/contact)!

### Build It!

Get your prints started. (This may take a while.)

In the meantime, set up your Electron using the tutorials in the [Particle Docs](http://docs.particle.io). Copy and flash [this firmware](https://go.particle.io/shared_apps/5a2f078a5ec586b022001613) to your Electron.

Cut an alligator clip wire in half and strip the ends. Screw one alligator clip into the + terminal and the other into the - terminal of the MOTOR terminals of the motor controller.

Screw a male-male jumper wire into the - terminal of the POWER IN terminal of the motor controller. Screw a different wire into the + terminal.

![](https://cdn.vox-cdn.com/thumbor/zJIiW6u3QeD816grV82qpN0r5Go=/800x0/filters:no_upscale\(\)/cdn.vox-cdn.com/uploads/chorus_asset/file/9899715/v_IMG_2431.jpg)

If you were to clip the alligator leads to the motor now and plug the jumper wires into power and ground, you could turn on the motor by clicking the button. When you click the button, it sends a signal to the motor controller to turn on. We're going to "hack" into the button, cutting the signal to the motor controller and sending our own signal instead. To do that, we'll need to make it possible for us to plug the red wire connecting to the button into the breadboard.

Find the red wire leading to the button. Cut it in half and strip the ends. Cut a jumper wire in half and strip those ends as well. Splice in a male header on the end of the wire leading back to the display. Splice the other male header onto the end of the wire leading back to the button. You can do this without solder by twisting the ends together and wrapping them with electrical tape.

![](https://cdn.vox-cdn.com/thumbor/Uzeq7-gjuSlAP1yEJS1nVm00-pg=/800x0/filters:no_upscale\(\)/cdn.vox-cdn.com/uploads/chorus_asset/file/9899717/v_IMG_2434.jpg)

Wire up your parts like this:

![](https://cdn.vox-cdn.com/thumbor/hQUy_rRPLc0DJ8hEQkrLDqzgwkI=/800x0/filters:no_upscale\(\)/cdn.vox-cdn.com/uploads/chorus_asset/file/9899725/wiring_diagram.png)

![](https://cdn.vox-cdn.com/thumbor/n4tZomj943A0bmZcAQUDa6dxpiY=/800x0/filters:no_upscale\(\)/cdn.vox-cdn.com/uploads/chorus_asset/file/9899731/v_IMG_2460.jpg)

Now it is time to upgrade our hand grinder. Get your 3D printed parts and clean off any supports. Fully dismantle your grinder into these pieces:

![](https://cdn.vox-cdn.com/thumbor/lNNSgTXWlnR90h9naQRGlEglfcM=/400x0/filters:no_upscale\(\)/cdn.vox-cdn.com/uploads/chorus_asset/file/9899735/v_IMG_2435.jpg)

> _Screw the motor into the lid using your four 4-40 machine screws._

![](https://cdn.vox-cdn.com/thumbor/vC103rL-fd4hKh5o6aFTH-Dx0-s=/400x0/filters:no_upscale\(\)/cdn.vox-cdn.com/uploads/chorus_asset/file/9899737/v_IMG_2437.jpg)

![](https://cdn.vox-cdn.com/thumbor/bAcMNlDUQT0ZcKvk3m088HxwwB4=/400x0/filters:no_upscale\(\)/cdn.vox-cdn.com/uploads/chorus_asset/file/9899739/v_IMG_2440.jpg)

![](https://cdn.vox-cdn.com/thumbor/RiuFCrlHgMqEaUmaz5wNUlUQy4Y=/400x0/filters:no_upscale\(\)/cdn.vox-cdn.com/uploads/chorus_asset/file/9899741/v_IMG_2438.jpg)

Secure your motor adapter to your motor, sandwiching the lid between the motor and adapter. Make sure that the flat side of the adapter is exposed, and that the motor's turbine is flush with the end of the adapter.

![](https://cdn.vox-cdn.com/thumbor/xwLfPK1R9f8RSOF2Y8bKJp7M3Ts=/800x0/filters:no_upscale\(\)/cdn.vox-cdn.com/uploads/chorus_asset/file/9899747/v_IMG_2442.jpg)

Secure the printed barrel to the motor adapter, using your four #6 screws.

![](https://cdn.vox-cdn.com/thumbor/YftR1LGL24yIIr2MJ3Hl5-RcTx8=/800x0/filters:no_upscale\(\)/cdn.vox-cdn.com/uploads/chorus_asset/file/9899749/v_IMG_2445.jpg)

Find the metal prongs from your grinder. Put them into the printed barrel, prongs facing out. Secure this part using the half-circle inserts for the barrel grinder.

![](https://cdn.vox-cdn.com/thumbor/ukLulb36gpjiA6ocY10NNlyH-lM=/800x0/filters:no_upscale\(\)/cdn.vox-cdn.com/uploads/chorus_asset/file/9899753/v_IMG_2447.jpg)

![](https://cdn.vox-cdn.com/thumbor/rhdGvWeK_jctV06pDhVbRdbGOjg=/400x0/filters:no_upscale\(\)/cdn.vox-cdn.com/uploads/chorus_asset/file/9899757/v_IMG_2449.jpg)

> _Screw the burr grinder into the top of the funnel. Fill with coffee._

![](https://cdn.vox-cdn.com/thumbor/QGXeMy-jpeZzBpqUlMFE9cp1aWg=/400x0/filters:no_upscale\(\)/cdn.vox-cdn.com/uploads/chorus_asset/file/9899755/v_IMG_2448.jpg)

![](https://cdn.vox-cdn.com/thumbor/4hzwsF_fFTQTvNCLKzjyvAReNNg=/800x0/filters:no_upscale\(\)/cdn.vox-cdn.com/uploads/chorus_asset/file/9899761/v_IMG_2453.jpg)

Carefully set and screw down the lid.

![](https://cdn.vox-cdn.com/thumbor/De1QZ3YfN5yD0lvMfMRx967WiMU=/800x0/filters:no_upscale\(\)/cdn.vox-cdn.com/uploads/chorus_asset/file/9899763/v_IMG_2454.jpg)

![](https://cdn.vox-cdn.com/thumbor/WiLuQJwvSRVeVGWLNAuMbCm4tSM=/800x0/filters:no_upscale\(\)/cdn.vox-cdn.com/uploads/chorus_asset/file/9899771/v_IMG_2457.jpg)

Clip your alligator leads onto the motor and turn it on. You can set off the grinder by clicking the button manually, or by triggering the grinder using functions online. Adjust the potentiometer to the lowest percentage at which it will still grind.

![](https://cdn.vox-cdn.com/thumbor/hYcsr4C7x4sxtlXma6_blx4MFzU=/800x0/filters:no_upscale\(\)/cdn.vox-cdn.com/uploads/chorus_asset/file/9899777/v_IMG_2458.jpg)

Feel free to encase your electronics in interesting enclosures!

![](https://cdn.vox-cdn.com/thumbor/8-VQuS1lc8PzGnlXjTtdJnwCbFY=/800x0/filters:no_upscale\(\)/cdn.vox-cdn.com/uploads/chorus_asset/file/9899779/v_IMG_2461.jpg)

![](https://cdn.vox-cdn.com/thumbor/_Nhfa2RlDSgGOgVAQRxcoLrjeZQ=/400x0/filters:no_upscale\(\)/cdn.vox-cdn.com/uploads/chorus_asset/file/9899789/v_IMG_2463.jpg)

![](https://cdn.vox-cdn.com/thumbor/MuCenY1iJ4YNJPWpfWo54A_TnJs=/400x0/filters:no_upscale\(\)/cdn.vox-cdn.com/uploads/chorus_asset/file/9899791/v_IMG_2470.jpg)

![](https://cdn.vox-cdn.com/thumbor/QAF-7mYLLHURU-ZbUNFgbYxYGmM=/800x0/filters:no_upscale\(\)/cdn.vox-cdn.com/uploads/chorus_asset/file/9899793/v_IMG_2467.jpg)

Now you're ready to grind coffee silently!

You can change the amount of coffee your grinder makes each day by changing the `grindTimeList` variable. To schedule your coffee each week, change this list to reflect the number of minutes your bot should grind each day, starting with Monday. Then, re-flash the code to your Electron.

You can also change the time your coffee grinder goes off by changing the `coffeeHour` variable, which is a weekly schedule keeping track of when the grinder should go off. Don't forget to set `timezone` to your time zone's UTC offset.

If you prefer to use Google Calendar to set off your grinder, set up an account on [IFTTT](http://ifttt.com). Set up an applet like this one:

![](https://cdn.vox-cdn.com/thumbor/Ve600URrklN9c7MhYzq4zQ7k2xA=/800x0/filters:no_upscale\(\)/cdn.vox-cdn.com/uploads/chorus_asset/file/9903043/b.jpg)

This will allow you to grind coffee up to 45 minutes before any "coffeebot" calendar appointment. The number of minutes it should grind ought to be placed in the event's description:

![](https://cdn.vox-cdn.com/thumbor/txh1eRWfmoATbM03p1hbbR28iV0=/800x0/filters:no_upscale\(\)/cdn.vox-cdn.com/uploads/chorus_asset/file/9899827/coffeebot_google_calendar.png)

Happy caffeining!
