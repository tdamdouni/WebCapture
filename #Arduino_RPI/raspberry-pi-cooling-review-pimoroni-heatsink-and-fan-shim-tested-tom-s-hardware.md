# Raspberry Pi 4 Cooling Review: Pimoroni Heatsink and Fan Shim Tested - Tom's Hardware

_Captured: 2019-07-21 at 20:51 from [www.tomshardware.com](https://www.tomshardware.com/reviews/pimoroni-fan-shim-heatsink-raspberry-pi-4,6219.html)_

The [Raspberry Pi 4](https://www.tomshardware.com/reviews/raspberry-pi-4-b,6193.html) is a powerful beast, running considerably warmer than its predecessors. While the official Raspberry Pi Power-over-Ethernet (PoE) HAT add-on includes a built-in fan that can cool things down, there are cheaper options for those who don’t need PoE support - like a passive heatsink or active Fan Shim accessory from Pimoroni.

![Thermal Image of Raspberry Pi 4. \(Credit: Gareth Halfacree\)](https://img.purch.com/pimoroni-stock-thermal-png/w/711/aHR0cDovL21lZGlhLmJlc3RvZm1pY3JvLmNvbS9XL0kvODQ0ODY2L29yaWdpbmFsL3BpbW9yb25pLXN0b2NrLXRoZXJtYWwucG5n)Thermal Image of Raspberry Pi 4. (Credit: Gareth Halfacree)

These affordable accessories allow you to limit or completely eliminate thermal throttling so that you can get maximum performance from your Raspberry Pi 4, no matter what the workload, even if you are overclocked. While the $2.50 / £2.40 heatsink is convenient and helpful, our tests show that the Pimoroni Fan Shim ($10 / £9.60) is much more effective. However, it is incompatible with some hats and won’t help in a totally enclosed case.

Advertisement

### The Problem: Thermal Throttling

When the Raspberry Pi 4’s system-on-chip (SoC) gets to a certain temperature - just above 80 degrees Celsius - it lowers its operating speed to protect itself from harm. For anyone using the Raspberry Pi 4 for short, computationally bursty tasks like browsing the web, editing a document, or programming in Scratch or Python, it’s not a problem. Under sustained load, though, the CPU throttling can have a real impact on performance.

![](https://img.purch.com/thermal-throttling-unmodified-raspberry-pi-4-th-png/w/711/aHR0cDovL21lZGlhLmJlc3RvZm1pY3JvLmNvbS9XL1UvODQ0ODc4L29yaWdpbmFsL1RoZXJtYWwtVGhyb3R0bGluZy1Vbm1vZGlmaWVkLVJhc3BiZXJyeS1QaS00X1RILnBuZw==)

The above graph shows a Raspberry Pi 4, uncased in the open air, running an intensive CPU and GPU workload for ten minutes. The temperature soon reaches the throttle point, and the CPU frequency can be seen dropping from the stock 1.5GHz down to 1GHz after three minutes and 43 seconds - though quickly popping back up again as the temperature falls. This up-and-down clocking behaviour runs right through to the end of the test, when the load is removed and the CPU can drop back down to its idle speed of 600MHz to recover properly.

The problem is only exacerbated if you overclock your Pi: boosting the CPU or GPU clock requires extra power, and that extra power becomes extra heat. An overclocked Raspberry Pi 4 will, all things being equal, begin throttling faster than one running at stock, and is likely to spend more time at its throttled speeds.

### The Passive Solution: The Pimoroni Heatsink

Adding a heatsink - a simple piece of heat-conductive metal, typically shaped into fins, which works to conduct heat away from the SoC and spread it across a larger surface area for improved transfer to the surrounding air - has long been a common upgrade for Raspberry Pi enthusiasts. The Pimoroni heatsink, specifically shaped for the Raspberry Pi, has a larger footprint than most - barely squeezing in between the Display Serial Interface (DSI) connector at the left and Camera Serial Interface (CSI) connector at the centre-bottom - in exchange for a low height which allows it to fit under full-size HAT accessories, though at the cost of losing much of its free airflow.

![](https://img.purch.com/pimoroni-heatsink-hero-png/w/711/aHR0cDovL21lZGlhLmJlc3RvZm1pY3JvLmNvbS9XL0YvODQ0ODYzL29yaWdpbmFsL3BpbW9yb25pLWhlYXRzaW5rLWhlcm8ucG5n)

The heatsink option has a couple of advantages over an active solution: it’s entirely silent, for one, and it’s extremely low cost at $2.52/£2.40. The price includes an adhesive strip on the rear, but oddly Pimoroni hasn’t opted for a true thermal interface material (TIM); instead, the adhesive strip is 3M Double Coated Tissue Tape 9448A - not typically used for adhering heatsinks to chips, but noted by its manufacturer for standing up well to high temperatures. Those using a Pimoroni Pibow Raspberry Pi 4 case will also find a new cutout in the top panel, which provides room for the heatsink to breathe.

![](https://img.purch.com/thermal-throttling-heatsink-passive-th-png/w/711/aHR0cDovL21lZGlhLmJlc3RvZm1pY3JvLmNvbS9XL1QvODQ0ODc3L29yaWdpbmFsL1RoZXJtYWwtVGhyb3R0bGluZy1IZWF0c2luay1QYXNzaXZlLV9USC5wbmc=)

Installing the heatsink and running the same benchmark as above shows a definite impact: the Raspberry Pi 4 starts off at a marginally lower temperature and ramps up on a slower, shallower curve. It’s the throttling where the biggest impact can be seen: thanks to the large aluminum lump and its increased surface area it takes nearly eight and a half minutes of sustained load for the Raspberry Pi 4’s CPU to begin throttling - a serious improvement over the stock unit’s three minutes and 43 seconds.

![Thermal Image of Raspberry Pi 4 with Heat Sink Cooling. \(Credit: Gareth Halfacree\)](https://img.purch.com/pimoroni-heatsink-thermal-png/w/711/aHR0cDovL21lZGlhLmJlc3RvZm1pY3JvLmNvbS9XL0cvODQ0ODY0L29yaWdpbmFsL3BpbW9yb25pLWhlYXRzaW5rLXRoZXJtYWwucG5n)Thermal Image of Raspberry Pi 4 with Heat Sink Cooling. (Credit: Gareth Halfacree)

It’s not enough to entirely prevent throttling, though - which is where the active option comes in.

### The Active Solution: The Pimoroni Fan Shim

The Fan Shim is a small, oddly-shaped PCB which comes bundled with a 30mm fan. Once assembled - a case of two bolts, four nuts, and clipping in the fan’s power header to a connector on the PCB - the entire assembly can be slipped over the Raspberry Pi’s GPIO header. Unlike fan add-ons costing less than the $10.08/£9.60 of the Fan Shim, it’s also possible to control the fan via software - with an example program included - while there’s a tactile button and user-addressable RGB LED on the board for good measure, though the button won’t work on the Raspberry Pi 4 until an updated GPIO Zero Python library is made available.

In theory, the slim PCB of the Fan Shim means it can be used at the same time as most HATs - though not any relying on GPIO Pin BCM18, which includes any audio add-ons using I2S audio connectivity like Pimoroni’s own pHAT DAC. Installing a full-size hat does block direct airflow into the fan from above, but there’s enough of a gap for it to still be capable of effective cooling; an optional Booster Header accessory raises the HAT to improve things further. As with the heatsink option, the new Pibow case includes a cut-out for the Fan Shim and fan.

![](https://img.purch.com/thermal-throttling-fan-shim-always-on-th-png/w/711/aHR0cDovL21lZGlhLmJlc3RvZm1pY3JvLmNvbS9XL1AvODQ0ODczL29yaWdpbmFsL1RoZXJtYWwtVGhyb3R0bGluZy1GYW4tU2hpbS1BbHdheXMtT24tX1RILnBuZw==)

By default, the Fan Shim spins up to its full 4,200 RPM as soon as the Raspberry Pi is switched on. In this mode, its cooling performance is extremely impressive: the SoC idles at around 37 degrees Celcius in a 24.5 degrees Celcius ambient environment, and remains below 55 degrees Celsius throughout the test. This is well below the 80 degrees Celcius throttle point of the Raspberry Pi 4’s BCM2711B0 SoC, so no throttle operations are recorded - the CPU runs at its full 1.5GHz throughout. There is a cost, however: the fan pulls an additional 0.6W from the power supply while running.

![Thermal Image of Raspberry Pi 4 with Fan Shim Cooling. \(Credit: Gareth Halfacree\)](https://img.purch.com/pimoroni-fanshim-thermal-png/w/711/aHR0cDovL21lZGlhLmJlc3RvZm1pY3JvLmNvbS9XL0gvODQ0ODY1L29yaWdpbmFsL3BpbW9yb25pLWZhbnNoaW0tdGhlcm1hbC5wbmc=)Thermal Image of Raspberry Pi 4 with Fan Shim Cooling. (Credit: Gareth Halfacree)

There’s plenty of headroom in the Fan Shim’s cooling performance, too: even an overclocked Raspberry Pi 4 can be kept from hitting its thermal throttle point, making it a must-have for anyone seeking to eke out peak performance from their Pi.

### Software-Controlled Cooling

The Fan Shim has another operating mode, however: software control via a Python-based application programming interface (API). Using this, it’s possible to turn the fan on and off - though not to vary its speed, other than by turning it on and off in rapid succession to simulate a pulse-width modulation (PWM) signal - and to make use of the tactile switch and RGB LED.

A sample program is included which sets an upper temperature limit and a hysteresis temperature, which Pimoroni recommends be set at 65 degrees Celsius and 5 degrees Celsius respectively. When running with these settings, the fan switches on - and the RGB LED toggles from red to green - at 65 degrees Celsius then cools until 60 degrees Celsius is reached before turning off and waiting for the temperature to rise again.

![](https://img.purch.com/thermal-throttling-fan-shim-software-control-th-png/w/711/aHR0cDovL21lZGlhLmJlc3RvZm1pY3JvLmNvbS9XL1MvODQ0ODc2L29yaWdpbmFsL1RoZXJtYWwtVGhyb3R0bGluZy1GYW4tU2hpbS1Tb2Z0d2FyZS1Db250cm9sLV9USC5wbmc=)

Here the Raspberry Pi idles at the same temperature as its uncooled, stock incarnation: around 50 degrees Celsius. The fan doesn’t spin up until the temperature hits 65 degrees Celsius, and then spends the rest of the test toggling on and off in order to keep the Raspberry Pi 4 below its target temperature. It does so admirably: as with the always-on mode, the SoC is kept far from its throttle point, and the ten-minute test completes without a single throttle operation being recorded. The same is also true when overclocked, though the fan will kick in more quickly and more often to compensate for the additional heat.

### Combined Cooling

Most desktop and laptops computers don’t rely on only a heatsink or only a fan; they use a combination of both, and it’s possible to do so with the Fan Shim and heatsink too - though it is not recommended by Pimoroni itself, which carried out its own testing and counterintuitively found the combination cooled less effectively than simply using the Fan Shim alone.

There’s only one way to verify that, mind you: to carry out the same test ourselves. The Pimoroni heatsink with Fan Shim connected on top is a combination which really necessitates the installation of pin extensions or Pimoroni’s Booster Header to the GPIO header; without them, there’s not enough pin for the Fan Shim to grip and it runs the risk of falling off - potentially shorting out the GPIO pins on its way, damaging the Raspberry Pi 4.

![](https://img.purch.com/thermal-throttling-heatsink-and-fan-shim-active-th-png/w/711/aHR0cDovL21lZGlhLmJlc3RvZm1pY3JvLmNvbS9XL1IvODQ0ODc1L29yaWdpbmFsL1RoZXJtYWwtVGhyb3R0bGluZy1IZWF0c2luay1hbmQtRmFuLVNoaW0tQWN0aXZlLV9USC5wbmc=)

For this test, the Fan Shim is left in software-controlled mode with the same temperature target of 65 degree Celcius as before. The result is a graph looking remarkably similar to using the Fan Shim alone, only stretched: the heatsink effectively stores up the heat generated by the SoC, slowing down the time until the Fan Shim needs to switch on; the downside is it also slows down the time it needs to switch off again afterwards. In terms of actual performance, though, there’s little difference: once again the SoC is cooled to the point where it doesn’t need to throttle the CPU to protect itself.

### The Performance Impact

Being able to prevent your Raspberry Pi 4 from throttling has a measurable impact on performance, though how measurable will depend entirely on how badly it’s throttling. In our test environment, which was at a stable 24.5 degrees Celcius throughout, the throttling wasn’t terrible: while the CPU did frequently drop to 1GHz under sustained load, it would quickly pop back up to 1.5GHz again. In a warmer environment the throttling would happen sooner and be sustained for longer, meaning the cooling accessories would have a greater impact on measured performance.

For this test, the Raspberry Pi 4 is instructed to compress an 8GB file stored on a USB 3.0 SSD, using the multi-threaded lbzip2 compression utility, while the time it takes is measured. Compressing such a large file on the Raspberry Pi 4 typically takes around twenty minutes, roughly double the synthetic load from the throttle testing, and on an uncooled Raspberry Pi triggers thermal throttling.

![](https://img.purch.com/file-compression-benchmark-th-png/w/711/aHR0cDovL21lZGlhLmJlc3RvZm1pY3JvLmNvbS9XL1EvODQ0ODc0L29yaWdpbmFsL0ZpbGUtQ29tcHJlc3Npb24tQmVuY2htYXJrX1RILnBuZw==)

There’s not a huge amount between them, but the Fan Shim definitely has an impact: the compression operation took 22 minutes and 14 seconds on an uncooled Raspberry Pi 4 but completed in 20 minutes and four seconds with the Fan Shim attached, saving over two minutes - just shy of a ten percent performance gain. Had the operation gone on longer, or taken place in a hotter environment, the difference would be greater.

For those who don’t like the idea of adding a spinning fan to their Raspberry Pi 4, the heatsink is a realistic alternative: with just the heatsink attached the benchmark completed in 20 minutes and 23 seconds - a respectable eight percent boost over uncooled stock, lagging just slightly behind the Fan Shim. Unlike the Fan Shim, though, the heatsink is unlikely to offer the same gains in a hot environment, where it can’t bleed off the heat it is conducting quickly enough, or for sustained workloads in excess of twenty minutes.

The combined Fan Shim and heatsink option, meanwhile, performed within the margin of error identically to using the Fan Shim alone - meaning unless you want to reduce the amount of time the fan spends toggling on and off, which you could also achieve in software by increasing the hysteresis temperature, there’s little real-world point to combining the two.

### Bottom Line

If your Raspberry Pi 4 is used for sustained workloads, you’re going to need some form of cooling to get the most out of it. While the passive heatsink option is simple and cheap, it’s only a partial solution; the Fan Shim, by contrast, solves the problem completely - or, at least, mostly.

The caveat which prevents it from being truly “completely” solved: the Fan Shim is only effective in a relatively open environment, or when used with cases like Pimoroni’s own Pibow which keep it uncovered. If installed in an enclosed case like the Official Raspberry Pi 4 Case, the Fan Shim can only do so much and throttling under sustained workloads may still be a problem. The solution: look for cases with ventilation, or take a drill to the Official Case to create your own.

Certain heavy workloads and enclosed environments aside, though, neither active nor passive cooling accessories are strictly necessary on the Raspberry Pi 4: even when hitting its thermal throttle point it’s still an impressively powerful upgrade from its predecessors, and running hot is unlikely to do the boards any permanent damage - the 80 degrees Celsius throttle point being comfortably below the components’ maximum rated operating temperatures.

The [Raspberry Pi 4 Heatsink](https://shop.pimoroni.com/products/raspberry-pi-4-heatsink) and [Fan Shim](https://shop.pimoroni.com/products/fan-shim) are available from Pimoroni now.

Raspberry Pi 4 Review: The New Gold Standard for Single-Board Computing

The long-anticipated Raspberry Pi 4 takes Pi to another level, with performance that’s good enough to use in a pinch as a desktop PC, plus the ability to output 4K video at 60 Hz or power dual monitors.

Next Up

Overclocked | AMD Ryzen Embedded Mini-ITX Build Preview

01:37

https://www.tomshardware.com/reviews/pimoroni-fan-shim-heatsink-raspberry-pi-4,6219.html?jwsource=cl
