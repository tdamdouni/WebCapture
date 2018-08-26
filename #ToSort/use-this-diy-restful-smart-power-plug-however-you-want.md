# Use This DIY RESTful Smart Power Plug However You Want

_Captured: 2018-06-29 at 08:24 from [blog.hackster.io](https://blog.hackster.io/use-this-diy-restful-smart-power-plug-however-you-want-be47d17b9365?mc_cid=7d901795d1&mc_eid=1c68da4188)_

Smart power plugs are probably the first home automation devices people buy when they get started with IoT. It's convenient to just ask your home voice assistant to turn off a light instead of having to walk all the way over to the switch on the wall. But, virtually all of the smart plugs on the market use proprietary communication protocols. If that doesn't appeal to you, there is an alternative: [this RESTful DIY smart plug](https://hackaday.io/project/159067-restful-smart-power-plug).

![](https://cdn-images-1.medium.com/freeze/max/60/1*MKCpktgHa8_qPue60XU66g.jpeg?q=20)![](https://cdn-images-1.medium.com/max/1600/1*MKCpktgHa8_qPue60XU66g.jpeg)

Ricky Zhang designed the open communication smart plug after becoming frustrated by the consumer options that are currently available. He wanted a smart plug for his [3D printer](https://www.hackster.io/3d-printing) that would automatically switch off if his smoke detector is triggered, which is a smart safety feature. But, all of the consumer smart plug models he could find used proprietary communication protocols that pass through the internet-based [IoT systems](https://www.hackster.io/iot). Going through the internet opens the system up to hacking, and at the very least could fail if the internet connection is lost.

Zhang's solution was to create [an ESP8266](https://www.hackster.io/esp)-based smart plug that uses a REST (representational state transfer) API framework called bREST that he wrote himself. The protocol is open, and works over a local network without going out to the internet at all. And, because [the RESTful communication](https://www.hackster.io/communication) is system agnostic, it can work with whatever you want to use for control. Other than the ESP8266, you just need an AC-to-DC transformer, an AC outlet and enclosure, and a mechanical relay. If you shop around and order enough parts to build a few smart plugs, each one should cost you less than $15.
