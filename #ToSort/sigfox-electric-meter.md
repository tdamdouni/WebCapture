# Sigfox Electric Meter

_Captured: 2017-09-10 at 18:38 from [www.instructables.com](http://www.instructables.com/id/Sigfox-Electrical-Meter/)_

![Sigfox Electric Meter](https://cdn.instructables.com/FVA/88CY/IOT2UCTN/FVA88CYIOT2UCTN.MEDIUM.jpg)

**Description:**

This project will show you how to get your electricity consumption using a small device plugged onto your electrical meter. Note that it only works with the "Compteur Electrique Triphase agree EDF, ECS, 60A / 40KWh Multi Tarifs". This model is very common in France.

Basically, on this electric meter, a LED blinks every time a Wh is consumed. So the idea is to record this blink and link it to a counter and then every hour send it to a server using Sigfox network.

**Which microcontrollers will be used?**

We will be using the Akeru dev kit.

Other dev kits are available on Sigfox Partners Network.

**Does it work on all electric meters?**

No unfortunately, it only works on the "Compteur Electrique Triphase agree EDF, ECS, 60A / 40KWh Multi Tarifs" which are very common in France. Feel free to try to adapt it and share your solutions!

**How long does it take to make it?**

All the source code is available on Github. So, within an hour or two, you will be able to make it work.  
If you want to print the adapter, I have been using 3D hubs and I received it in two days.

**Do I need any previous knowledge?**

You don't need any previous knowledge although knowing Arduino and CAD design is a plus.

**Who am I?**

My name is Louis Moreau, I'm an intern at Sigfox. My mission is to create prototypes and PoC using Sigfox network. I want these projects to be fun and instructive. I want to show you how easy is it to develop the first steps of your ideas. I will try to make this tutorial as complete as I can. Do not hesitate to ask me for more details if needed : Github

**Contrib:**

Emmanuel Nhan ([@nhanmanu](https://twitter.com/nhanmanu))

## Step 1: Understand Sigfox

**What is Sigfox?**

Sigfox is a connectivity solution dedicated to the Internet of Things. The operated network is currently operating in [+15 countries](http://www.sigfox.com/coverage), on every continent.   
Focused on tiny messages (up to 12 bytes) & low energy consumption, it currently powers 7 million devices. Various Sigfox-compatible technical solutions are[ available](https://partners.sigfox.com/search/products?or%5Bcategories%5D%5B0%5D=kit), from different silicon vendors. This project uses an Arduino shield from Atmel (see below)

## Step 2: Hardware Requirements

![Hardware Requirements](https://cdn.instructables.com/FBB/I9S2/IOT2UBRI/FBBI9S2IOT2UBRI.MEDIUM.jpg)

![2016-05-30 10.34.24.jpg](https://cdn.instructables.com/FZW/9ATA/IOT2UC25/FZW9ATAIOT2UC25.SMALL.jpg)

![2016-05-30 10.33.52.jpg](https://cdn.instructables.com/FWE/G04V/IOT2UC3K/FWEG04VIOT2UC3K.SMALL.jpg)

![2016-05-30 10.34.03.jpg](https://cdn.instructables.com/FEE/EWNA/IOT2UC3N/FEEEWNAIOT2UC3N.SMALL.jpg)

![3D Printing](https://cdn.instructables.com/FDI/OQTO/IOT2UYMQ/FDIOQTOIOT2UYMQ.MEDIUM.jpg)

![Capture du 2016-05-30 11-51-10.png](https://cdn.instructables.com/FUX/J09L/IOT2UCNQ/FUXJ09LIOT2UCNQ.MEDIUM.jpg)

![Arduino Code](https://cdn.instructables.com/FBT/MGR5/IOT2ULFL/FBTMGR5IOT2ULFL.MEDIUM.jpg)

![Using the Sigfox Backend](https://cdn.instructables.com/FEV/SIY2/IOT2UM8Q/FEVSIY2IOT2UM8Q.MEDIUM.jpg)

![View Your Data Using TheThings.io](https://cdn.instructables.com/FTB/Y94C/IOT2UVAT/FTBY94CIOT2UVAT.MEDIUM.jpg)

![Capture du 2016-05-30 16-43-35.png](https://cdn.instructables.com/FP1/S6UM/IOT2UVAU/FP1S6UMIOT2UVAU.MEDIUM.jpg)

![Create a Callback in Sigfox Backend](https://cdn.instructables.com/FUI/AS6U/IOT2UWVD/FUIAS6UIOT2UWVD.MEDIUM.jpg)

![Going Further](https://cdn.instructables.com/FX7/BS9K/IOT2UYK7/FX7BS9KIOT2UYK7.MEDIUM.jpg)

![IMG_20150826_111020.jpg](https://cdn.instructables.com/FCW/1YD6/IOT2UYL2/FCW1YD6IOT2UYL2.MEDIUM.jpg)
