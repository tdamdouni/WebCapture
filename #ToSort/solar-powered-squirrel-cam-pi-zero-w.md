# Solar-Powered Squirrel Cam (Pi Zero W)

_Captured: 2018-04-07 at 08:48 from [www.hackster.io](https://www.hackster.io/reichley/solar-powered-squirrel-cam-pi-zero-w-797db4)_

![Solar-Powered Squirrel Cam \(Pi Zero W\)](https://hackster.imgix.net/uploads/attachments/459033/squirrel2374_93S8Sgy7XG.jpg?auto=compress%2Cformat&w=900&h=675&fit=min)

I live half a mile above sea level and am SURROUNDED by animals...Bears, Fox, Turkeys, Deer, Squirrels, Birds. Spring has arrived and there are LOADS of squirrels running around. I was in the building mood and, being a nerd, wished to combine a common woodworking project with the connectivity and observability provided by single-board computers (and their camera add-ons). And now I give you Squirrelhaus/Squirrelcam!

The first step was sketching out how big I wanted the squirrel haus to be, where I wanted to place the camera, and whether the haus would be tied to an outlet (and, therefore tethered to the house's grid) or autonomous via some solar panels, lithium battery charging modules, and 18650 batteries...I'm big on autonomy and renewable energy so I opted for the latter.

Below are the haus measurements...I had 1/2" pine sitting around but I'm sure a haus made of something thinner would withstand some panels, a protoboard, some batteries, etc.

![](https://hackster.imgix.net/uploads/attachments/459086/squirrel2399_aomngvStZ3.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

> _I originally planned to alternate solar panels and plexiglass (for lighting and energy) but scrapped the plexiglass to boost my solar powerhouse._

The base of the haus was measured out so as to fit atop/hug a deck rail built out of 2" x 6"s. After measuring the size of the panels I had (5.1" x 5.9", 5V 500mAh max 2.5W) I knew how big the roof of the haus had to be to accommodate panels to cover both sides of the roof. I also bypassed an optional feeder square in the center/top due to concerns over sealing and weatherizing. The convenience wasn't worth it, especially when there'd be more than enough room between the base and the lowest point of the roof to put in food.

Below is the finished frame with a few coats of gel stain and a couple coats of shellac.

;

;

![](https://hackster.imgix.net/uploads/attachments/459091/squirrel2329_2IDmqifMtd.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

1 / 2 • holes in roof for the + and - wires from the solar panels

The next step would be wiring up the panels with enough slack to be able to both attach to the protoboard and later pull away to add liquid nails before affixing to roof and holding in place overnight with a vice. I also wired up the 4 tp4056 lithium charging modules and the 4 18650 battery holders. The positive inputs to the charging circuits (from the solar panels) requires a blocking diode (1N4001) in series so as to not allow current from the batteries to flow through the panels at night when no voltage is present at/on the panels.

**IMPORTANT NOTE: I wired the charging module circuits together in parallel so the 3.7-4.2V 2600 mAh batteries would keep at one voltage but bring a punch of cumulative current/capacity...maxing out at 10400 mAh. Also, as I didn't have a charging module that'd charge several batteries with one input source I opted for the safe "1 panel per module/battery"**

;

;

![](https://hackster.imgix.net/uploads/attachments/459103/squirrel2334_RXq4G5f1HW.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

I then soldered in the attiny85 breadboard socket onto the protoboard (more below on the attiny85) along with the blocking diodes. After wiring the panels into the lithium charger inputs I was visually able to test my wiring by placing both sides of the haus into adequate sunlight and observe the red module "charging" LEDs illuminating.

;

;

![](https://hackster.imgix.net/uploads/attachments/459108/squirrel2345_d4tKdjMzBL.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

Many sites have tested the pi zero W's power consumption. In this case, we'd be streaming 1080p video while it's on and connected to wifi so I had to take that into account. Overall the device(s) take around 225-250 mAh. THEORETICALLY, if the pi were to run 24/7 it'd need 6000 mAh of juice. Since the 4 batteries only supply 10400 mAh you'd get less than 2 days of use out of the haus. Ah, but I added 4 panels, right? Assuming I'll only receive ~4 "great" hours of sunlight a day and also assuming no more than 250 mAh per panel per hour that'll only replenish around 4000 of the 6000 mAh used for the 24 hour period. And that assumption is for a "great" day of sun. If it were partially sunny or overcast I'd expect ~100 mAh (or less) per panel per hour. How do I reduce the consumption of the pi zero/camera? And does it even make sense to stream in the dark? In comes the LiPo SHIM, the BH1750, and the ATTINY85.

The purpose of the LiPo SHIM is twofold. First, the pi zero operates on 5V BUT my batteries are only pushing 4.15V (when fully charged). The SHIM bumps LiPo inputs up to 5V while maintaining a 96% efficiency rate! Sure, there are cheaper boost converters out there...But most are only 70-80% efficient. Not acceptable in this case since I'm already in an energy consumption/production bind. The 2nd purpose of the SHIM is the nifty "enable" pin. When pulled to ground, the SHIM cuts power to the pi. This is where the ATTINY85 and BH1750 shine.

By measuring the outside lux (shooting for 100 lux which is equal to an overcast day) every 5 minutes I'm able to determine IF the environment is light enough to produce decent footage of streaming video or if it's too overcast, early, or late in the day and should instead shut down the pi. But I need to keep the ATTINY85 pin output held either high or low so I won't be able to sleep the ATTINY. No worries, though. When active and either measuring or in the delay portion of the code the ATTINY it (and the BH1750) use no more than 1.05 mAh. Over 24 hours 24 mAh is A LOT LESS than say...2500-3500 mAh from the pi running when it won't be effectively shooting watchable video. I've provided the code I loaded onto the ATTINY [using the Arduino IDE] below.

![](https://hackster.imgix.net/uploads/attachments/459512/squirrel2352_B22BPqw6LS.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

Below you'll find the Arduino IDE code I wrote and uploaded to the ATTINY85. The ATTINY reads the lux from the BH1750 every 5 minutes (delay in between). If the lux is **UNDER** 100 the output of pin 3 is **LOW** and if lux above 100 the output is **HIGH.** The low output on the enable pin of the LiPo SHIM cuts power to the pi. The high output allows the LiPo to send power the pi/camera. The circuit schematic is also below. I didn't have time to create the LiPo SHIM part so the note will have to suffice as a placeholder.
    
    
    // Thanks to:
    // Spence Konde for his ATTinyCore library!
    // https://github.com/SpenceKonde/ATTinyCore
    // and 
    // claws for his BH1750 library!
    // https://github.com/claws/BH1750
    #include <Wire.h>
    #include <BH1750.h>
    BH1750 lightMeter;
    const int enablePin = 3;
    void setup(){
     pinMode(enablePin, OUTPUT);
     digitalWrite(enablePin, HIGH);
     Wire.begin();
     delay(125);
     lightMeter.begin(BH1750::ONE_TIME_HIGH_RES_MODE);
    }
    void loop() {
     delay(125);
     // READ FROM BH1750
     uint16_t lux = lightMeter.readLightLevel();
     if (lux < 100) {
       digitalWrite(enablePin, LOW);
     } else {
       digitalWrite(enablePin, HIGH);
     }
     delay(60000 * 5);
    }
    

![](https://hackster.imgix.net/uploads/attachments/459866/squirrel_haus_schematic_jKcM8KOoJf.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

> _squirrel haus schematic_

The camera software I ended up using was Calin Crisan's [motioneyeos](https://github.com/ccrisan/motioneyeos). It's a GREAT read-only linux distro for use in/on many single-board computers. Please refer to his Github wiki for [install](https://github.com/ccrisan/motioneyeos/wiki/Installation) and setup instructions. I didn't modify/edit anything beyond basic network configuration and motion capture settings. Below is the finished product...and a screenshot from my fully-functional squirrel haus cam!

![](https://hackster.imgix.net/uploads/attachments/459873/img_2431_2B1DEScI8P.JPG?auto=compress%2Cformat&w=680&h=510&fit=max)

> _squirrel haus cam_

![](https://hackster.imgix.net/uploads/attachments/459875/img_2401_tzJeKNeXyS.JPG?auto=compress%2Cformat&w=680&h=510&fit=max)

> _view from the cam_
