# Make Your Pi a (Local) Cloud Server!

_Captured: 2017-12-01 at 18:54 from [www.instructables.com](http://www.instructables.com/id/Make-Your-Pi-a-Local-Cloud-Server/)_

![](https://cdn.instructables.com/F52/NPFL/JACTWSZU/F52NPFLJACTWSZU.MEDIUM.jpg)

**Save and access docs and photos and music on your own local Pi Cloud server!** The best part: you can use it if, or when, the Internet goes down (or if you're in a remote spot & want access to Wikipedia). Oh hey, and if your friend gets one and they live close (*ahem*80ft*ahem*), you can share stuff with them and make your own personal chat line!

That gets me thinking.. if enough folks built Pi Cloud servers, we could crowdsource the Internet! That would be an 11/10 on a scale of greatness. With the new models of the Raspberry Pi computer, it's possible and not even expensive! (What! Tell me more!)

**This tutorial will show you how to set up a short-range (~ 80 ft) WiFi Access Point and a personal web server **('bringin it back to HTML bbies). You can set this up as a (closed) local network only (i.e. your own personal "cloud" backup device), or broadcast it to the rest of the world! (..if you do this be sure you know network security.)

That said, assuming you have a [basic knowledge of the Pi](http://foxbotindustries.com/intro-headless-raspberry-pi/), here's the breakdown:

**Read Time:** ~ 40 min

**Build Time**: ~ 60 min (less if you are experienced w/ Linux)

**Cost**: ~ $35 (for the Pi 3)

_If you're interested in helping to kickstart a people's Internet,** share it **w/ your friends & family & everyone you know (or build it for them!). If you build this project please** mark that you've built it **so we can get a sense of how many folks have the infrastructure we need to actually make a full-fledged people's Internet**. Lastly, follow me to stay updated** (I am reaching out to some folks to try to get this to be a real thing, please feel free to contact me if you can help and/or take this on, it is open-source!). _

## Step 1: New to Linux & Terminal Programming?

![](https://cdn.instructables.com/F6J/XDKM/JACTQJ7I/F6JXDKMJACTQJ7I.MEDIUM.jpg)

We'll need to be able to access our Pi remotely (e.g. via SSH). If you're like "wtf is that", **[check out this introductory tutorial**](http://foxbotindustries.com/intro-headless-raspberry-pi/)for a more thorough overview on how to set up the Raspberry Pi 3 and some quick Linux terminal programming.

**This approach to the Pi Access Point* and web server** uses the Jessie Lite OS. If you follow this tutorial line-by-line, you will need this specific version of Linux.**

Lastly, this tutorial is built off of the [Adafruit Digital Free Library tutorial](https://learn.adafruit.com/digital-free-library/what-youll-need), so check that tutorial if you run into any issues (or leave a comment and myself or another helpful folk will attempt to answer your question :) )

(Also, this might feel a bit long, so I've included various cute puppy photos throughout to keep you motivated :D)

_*An Access Point is hardware device that allows a WiFi device (e.g. smartphone) to connect to a wired network (e.g. router)._

_**A web server is a computer that delivers a web page. When you go to your favorite websites, you type in "www.wikipedia.org" which takes you to the IP address for the web server and displays public information._

_Warning: it is recommended to run your Pi as a** local network only **(i.e. do not connect the Pi to the broader World Wide Web) as t__he WPA2 password protocol may not be secure._

## Step 2: Materials

![](https://cdn.instructables.com/FAM/24MN/JA8JMZQS/FAM24MNJA8JMZQS.MEDIUM.jpg)

![](https://cdn.instructables.com/FXG/LW82/JACTQ7IP/FXGLW82JACTQ7IP.MEDIUM.jpg)

![](https://cdn.instructables.com/FGU/2SN7/JA8JMXHU/FGU2SN7JA8JMXHU.MEDIUM.jpg)

![](https://cdn.instructables.com/F2X/V56T/JA8JN25W/F2XV56TJA8JN25W.MEDIUM.jpg)

![](https://cdn.instructables.com/FFQ/QZIM/JACTQTZJ/FFQQZIMJACTQTZJ.MEDIUM.jpg)

![](https://cdn.instructables.com/FRV/5FCP/JACTQZVE/FRV5FCPJACTQZVE.MEDIUM.jpg)

![](https://cdn.instructables.com/FNK/X1CC/JACTWPDJ/FNKX1CCJACTWPDJ.MEDIUM.jpg)

![](https://cdn.instructables.com/FI5/E12K/JACTQ2Q3/FI5E12KJACTQ2Q3.MEDIUM.jpg)

![](https://cdn.instructables.com/FKO/M4W0/JACTWPG3/FKOM4W0JACTWPG3.MEDIUM.jpg)

![](https://cdn.instructables.com/FLP/U1ZZ/JACTQ2Q7/FLPU1ZZJACTQ2Q7.MEDIUM.jpg)

![](https://cdn.instructables.com/F4T/98RH/JACTQ782/F4T98RHJACTQ782.MEDIUM.jpg)

![](https://cdn.instructables.com/FNB/V9KB/JACTQ2Q8/FNBV9KBJACTQ2Q8.MEDIUM.jpg)

![](https://cdn.instructables.com/FMO/JBU6/JACTQK7G/FMOJBU6JACTQK7G.MEDIUM.jpg)

![](https://cdn.instructables.com/FR7/FRJZ/JACTQ2Q4/FR7FRJZJACTQ2Q4.MEDIUM.jpg)

![](https://cdn.instructables.com/FH7/Q652/JACTQ2Q5/FH7Q652JACTQ2Q5.SMALL.jpg)

![](https://cdn.instructables.com/FZU/AP65/JACTQ2Q6/FZUAP65JACTQ2Q6.SMALL.jpg)

![](https://cdn.instructables.com/FEC/VNGN/JACTQ2Q2/FECVNGNJACTQ2Q2.MEDIUM.jpg)

![](https://cdn.instructables.com/FW1/4UGN/JACTQK66/FW14UGNJACTQK66.MEDIUM.jpg)

![](https://cdn.instructables.com/FSU/BH54/JACTSSF6/FSUBH54JACTSSF6.MEDIUM.jpg)

![](https://cdn.instructables.com/FDG/QJ9R/JACTQZVF/FDGQJ9RJACTQZVF.MEDIUM.jpg)

![](https://cdn.instructables.com/FJN/8CYA/JACTQ780/FJN8CYAJACTQ780.MEDIUM.jpg)

![](https://cdn.instructables.com/FTX/W3SG/JA8JMXBW/FTXW3SGJA8JMXBW.MEDIUM.jpg)

![](https://cdn.instructables.com/FB7/NZOM/JACTWU16/FB7NZOMJACTWU16.MEDIUM.jpg)

![](https://cdn.instructables.com/FPI/LQQ3/JACTWUAA/FPILQQ3JACTWUAA.MEDIUM.jpg)

![](https://cdn.instructables.com/FXY/O1C6/JACTWUEW/FXYO1C6JACTWUEW.MEDIUM.jpg)

![](https://cdn.instructables.com/F8Y/4TVG/JACTWSP4/F8Y4TVGJACTWSP4.MEDIUM.jpg)

![](https://cdn.instructables.com/FH5/UTAB/JA8JN2HC/FH5UTABJA8JN2HC.MEDIUM.jpg)

![](https://cdn.instructables.com/FEB/0H91/JACTQK2P/FEB0H91JACTQK2P.MEDIUM.jpg)
