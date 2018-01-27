# Building the World’s Greatest Smart Alarm Clock

_Captured: 2017-11-24 at 09:41 from [www.vmwareinfo.com](http://www.vmwareinfo.com/2017/11/building-worlds-greatest-smart-alarm.html?utm_source=feedburner&utm_medium=twitter&utm_campaign=Feed:+IPMer+(vCloudInfo.com)&m=1)_

![image](https://lh3.googleusercontent.com/-f7nWpZEfq1Y/WhXOCQ-UOwI/AAAAAAADfIg/w4IgDKE76mogIZhznXQ9SwcgdxxP19kNACHMYCw/image_thumb%255B8%255D?imgmax=800)

We live in a [Smart Home](https://github.com/CCOSTAN/Home-AssistantConfig#-home-assistant-config-by-ccostan) and right next to our [SleepIQ](http://amzn.to/2kxdXXI) Wi-Fi enabled bed is the oldest alarm clock on the planet. It is your standard radio alarm clock from the 1980s that is either too bright or too dim, never programmed correctly and goes out of sync with the world twice a year with daylight savings. It has absolutely no smarts to it at all. In fact, most of the time, it was just the visual timepiece and the [iPhone](http://www.vmwareinfo.com/search/label/iPhone) next to it provides the REAL alarm functionality.

I set out to fix this with [Home Assistant](https://github.com/CCOSTAN/Home-AssistantConfig#-home-assistant-config-by-ccostan).

Building on the current [Alarm System](http://www.vmwareinfo.com/2017/06/building-my-home-alarm-system-hardware.html) project using [FloorPlan](https://github.com/pkozul/ha-floorplan-kiosk) and the [Fire Tablets](http://www.vmwareinfo.com/2017/07/visualizing-smart-home-using-home.html), I started the creation of a Home Assistant powered Smart Alarm clock.

> **_Parts List:_**

First up, my friend Steve hooked [me](http://about.me/ccostan) up with a great looking SVG design for the Alarm Clock.

![image](https://lh3.googleusercontent.com/-NHabCwuk_4s/WheWLsNF5JI/AAAAAAADfSs/AgvltdQw9YQFlFTgcbRFa8RU7YQyDLWoQCHMYCw/image_thumb%255B3%255D?imgmax=800)

> _You can find all the Floorplan project files here:_

<https://github.com/CCOSTAN/Home-AssistantConfig/tree/master/www/custom_ui/floorplan>

The automation files are set up in a package format for easy drop in:   
<https://github.com/CCOSTAN/Home-AssistantConfig/blob/master/packages/alarm_clock.yaml>

So what does the Clock do? It does the obvious stuff -

  * Displays time and date
  * Plays streaming music on alarm trigger
  * Snoozes
  * Displays the weather
  * Displays the indoor Nest temperatures
  * Shows an live image of the Front Door via the [SkyBell HD](http://amzn.to/2dcexIB) Doorbell. 

So what else can it do?

  * It uses the Fire Tablet's motion sensing (via camera) to detect motion and wake up the screen saver. Great for bathroom trips in the middle of the night. 
  * It uses Home Assistant logic to know if it's a school day or not (Summer Vacations, Holidays and Weekday/Weekends). 
  * Leverages the bed sensors to know when you get up at night (turn on guide lights and display time and then fade to black when back in bed) and then when you get out of bed for good in the morning (turn off the radio/snooze and trigger the morning routines). 
  * Get Alert [TTS](http://www.vmwareinfo.com/2017/07/giving-voice-to-smart-home.html) Notifications from the system right to the bedside without broadcasting to the whole house. ([Security](http://www.vmwareinfo.com/search/label/Security) events - Doors, Garage doors, windows etc..)
  * Fully integrated with Alexa via Emulated [Hue](http://amzn.to/2eoQTJy) component since we use _input_booleans_ for most buttons. 
  * Fully customizable with Home Assistant (like turning on lights, starting coffee maker, warming up your Tesla, etc. )

The secret sauce behind a lot of the cool _Media Player _features is the new custom component built by [Petar Kozul](https://github.com/pkozul). This exposes [Fully Kiosk Browser](http://www.ozerov.de/fully-kiosk-browser/) (recommended for Floorplan) to Home Assistant as a fully fledged Media Player.

Grab the Custom Component here:   
<https://github.com/CCOSTAN/Home-AssistantConfig/tree/master/custom_components/media_player>

With full Media Player capabilities exposed, we can use the Fire Tablets for both music, TTS notifications, [Cuckoo Clock](https://github.com/CCOSTAN/Home-AssistantConfig/blob/master/automation/System/CucKoo_Clock.yaml) sounds as well as grab a slew of attributes on the Tablet for future use.

![image](https://lh3.googleusercontent.com/-IE0-2Wl-FOs/WhXORZlIrfI/AAAAAAADfIw/IMT2fZ5r3Y8SRKazaWXLQpJ2R2PFl6VXQCHMYCw/image_thumb%255B16%255D?imgmax=800)

If you haven't given your Home Assistant Voice yet, this is a great way to get a TTS target at a super low entry price (I think for Black Friday you will see the Fire Tablet 7s for $30 or less).

Here is a quick video demo of the clock: (Thanks again for the intro Steve!)

Happy Thanksgiving Everyone! Enjoy Black Friday [Shopping Deals](http://amzn.to/2iH7AzU)!

-Carlo
