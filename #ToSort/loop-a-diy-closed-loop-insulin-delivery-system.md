# Loop: A DIY Closed-Loop Insulin Delivery System

_Captured: 2018-08-18 at 15:41 from [blog.hackster.io](https://blog.hackster.io/loop-a-diy-closed-loop-insulin-delivery-system-17a6182a70?mc_cid=1735a09106&mc_eid=1c68da4188)_

There are plenty of mobile medical devices on the market that can monitor everything from oxygen in the blood to cardiac stress. Most of these have been regulated by the FDA to enforce safety and reliability when functioning. As you might imagine, makers and engineers have taken medical technology to create DIY [biohacking](https://en.wikipedia.org/wiki/Do-it-yourself_biology) projects, including the Loop community who specialize in closed-loop insulin delivery systems (AKA DIY pancreas) for diabetics.

![](https://cdn-images-1.medium.com/freeze/max/60/1*MJLAeEBanLqo9mc90gPgHw.jpeg?q=20)![](https://cdn-images-1.medium.com/max/1600/1*MJLAeEBanLqo9mc90gPgHw.jpeg)

> _All that's needed for a DIY pancreas is a CGM, a compatible insulin pump, RileyLink, smartphone, and an open source app. (📷:_

Loop is an automated insulin delivery system that connects a continuous glucose monitor (CGM) along with a compatible insulin pump to your phone for automated insulin adjustments. Diabetics rely on testing the amount of blood sugar in their system at certain times during both day and night, and since those levels can fluctuate, the amount of insulin needed also varies. The Loop system monitors blood sugar levels and auto-doses the user with the correct insulin amount based on the collected data.

Building the system is remarkably simple as long as you have the right equipment, and while there are many Loop platforms found online, [Loop Docs](https://loopkit.github.io/loopdocs/) (loopkit.github.io) has easy to follow instructions on what hardware and apps are best to use for this project.

As mentioned earlier, building your own Loop requires a compatible CGM (Dexcom G5, or Dexcom G4+share, or Medtronic Enlite), compatible insulin pump with correct firmware (Medtronic 515/715 and 522/722), a RileyLink BLE custom communication platform (bridges communication between pump, CMG, and iPhone), an iPhone, and an open source [app](https://github.com/LoopKit/Loop).

It should be noted that the [RileyLink](https://getrileylink.org/product/rileylink916/?v=79cba1185463) can be purchased fully assembled with battery and case, or you can make it yourself with readily available design files [found on GitHub](https://github.com/ps2/rileylink/tree/master/hardware). Also, the system only works with the iPhone and has yet to be ported over to Android-based smartphones. As a final warning, the FDA has not approved (or will never) the building of DIY biohacks, so a level of caution should be taken if you decide to create your own.
