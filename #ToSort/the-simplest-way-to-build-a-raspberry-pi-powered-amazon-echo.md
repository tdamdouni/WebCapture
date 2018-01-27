# The Simplest Way to Build A Raspberry Pi-Powered Amazon Echo

_Captured: 2018-01-18 at 14:46 from [lifehacker.com](https://lifehacker.com/the-simplest-way-to-build-a-raspberry-pi-powered-amazon-1794218212)_

A while back we detailed how to make your own [Amazon Echo device using a Raspberry Pi](https://lifehacker.com/how-to-build-your-own-amazon-echo-with-a-raspberry-pi-1787726931), but if anything went wrong with it, you'd have to manually reboot the whole thing. It was a pain in the butt. Now, there's an easier way to make your own Echo.

What exactly is different about this version? First off, the end result is basically the same: you can activate your DIY Echo by saying the wake word "Alexa," and the device works just [like a real Echo](https://lifehacker.com/the-seven-best-things-you-can-do-with-an-amazon-echo-1766989219).

The installation process here is different though. Instead of using [Amazon's official resources](https://github.com/alexa/alexa-avs-sample-app), we'll use a GitHub project called [Alexa Pi](https://github.com/alexa-pi/AlexaPi). This installs the exact same Alexa voice service that Amazon uses on the Echo onto your Raspberry Pi. With this version of the project, if something goes wrong, the Alexa service will start automatically when you restart your Raspberry Pi. This is _much better_ than the previous project that requires you to restart the service manually by opening three different Terminal windows. Beyond that, this method also supports other development boards, like the [Orange Pi](http://www.orangepi.org/) and [C.H.I.P](https://lifehacker.com/affordable-electronics-board-showdown-raspberry-pi-zer-1786409766).

Obviously this isn't a cheaper system than something like the [Echo Dot](https://www.amazon.com/All-New-Amazon-Echo-Dot-Add-Alexa-To-Any-Room/dp/B01DFKC2SO?tag=lifehackeramzn-20&ascsubtag=f85f4f70aec70134afc910a3e85035c62779b4ef&rawdata=\[t|link\[p|1794218212\[a|B01DFKC2SO\[au|5716493564230329059\[b|lifehacker), but it is fully customizable and a great project if you already have the materials sitting around. With that, let's get to it.

### What You Need

As you'd expect, you'll need a Raspberry Pi alongside a handful of parts:

  * [A Raspberry Pi 3](https://www.amazon.com/Raspberry-Pi-RASP-PI-3-Model-Motherboard/dp/B01CD5VC92/ref=sr_1_2?s=pc&ie=UTF8&qid=1476306172&sr=1-2&keywords=raspberry%2Bpi%2B3ascsubtag=f7d2f55406f42a5f838be7748b3449559876cab0&rawdata=%5Br%7Chttps%3A%2F%2Fwww.google.com%2F%5Bt%7Clink%5Bp%7C1787726931%5Ba%7CB01CD5VC92%5Bau%7C5716493564230329059%5Bb%7Clifehacker&tag=lifehackeramzn-20&ascsubtag=5914db7a1135d80a0233cbee70e35914da6ee2ab&rawdata=\[t|link\[p|1794218212\[a|B01CD5VC92\[au|5716493564230329059\[b|lifehacker) (recommended), [Raspberry Pi Zero W](https://www.raspberrypi.org/products/pi-zero-w/), or [Raspberry Pi 2 ](https://www.amazon.com/Raspberry-Pi-Model-Project-Board/dp/B00T2U7R7I/ref=sr_1_3?s=pc&ie=UTF8&qid=1476306182&sr=1-3&keywords=raspberry%2Bpi%2B2ascsubtag=e3849a60166ac7fb8ea9e2cdfdcacb5816901a91&rawdata=%5Br%7Chttps%3A%2F%2Fwww.google.com%2F%5Bt%7Clink%5Bp%7C1787726931%5Ba%7CB00T2U7R7I%5Bau%7C5716493564230329059%5Bb%7Clifehacker&tag=lifehackeramzn-20&ascsubtag=93ae155dac1023c31e703727be409ab8e749e29f&rawdata=\[t|link\[p|1794218212\[a|B00T2U7R7I\[au|5716493564230329059\[b|lifehacker)(you'll also need a USB Wi-FI adapter with the Model 2) with Raspbian installed and Wi-Fi set up. If you haven't installed Raspbian before, [our guide covers everything you need to know](http://lifehacker.com/the-always-up-to-date-guide-to-setting-up-your-raspberr-1781419054). While I'm going to concentrate on installing this on the Raspberry Pi, a number of other devices are supported. You can find[ a whole list here](https://github.com/alexa-pi/AlexaPi/wiki/Devices). I ran the installation on a C.H.I.P. as well just out of curiosity and it worked fine.  

  * A USB Microphone (I used this [cheap $6 mic](https://www.amazon.com/dp/B00IR8R7WQ?rawdata=%5Br%7Chttps%3A%2F%2Fwww.google.com%2F%5Bt%7Clink%5Bp%7C1787726931%5Ba%7CB00IR8R7WQ%5Bau%7C5716493564230329059%5Bb%7Clifehacker&tag=lifehackeramzn-20&ascsubtag=ac8268282a8f013ca8e5947a2eb2de11853fec68&rawdata=\[t|link\[p|1794218212\[a|B00IR8R7WQ\[au|5716493564230329059\[b|lifehacker), but pretty much any USB mic seems to work. The [$8 Playstation Eye](https://www.amazon.com/PlayStation-Eye-3/dp/B000VTQ3LU/?rawdata=%5Br%7Chttps%3A%2F%2Fwww.google.com%2F%5Bt%7Clink%5Bp%7C1787726931%5Ba%7CB000VTQ3LU%5Bau%7C5716493564230329059%5Bb%7Clifehacker&tag=lifehackeramzn-20&ascsubtag=1f5be43e0e6b645afb36899f3b4853ca9de32853&rawdata=\[t|link\[p|1794218212\[a|B000VTQ3LU\[au|5716493564230329059\[b|lifehacker) seems to work especially well if you're looking for a slight upgrade) If you're using the Raspberry Pi Zero W you'll also need a [MicroUSB-USB adapter](https://www.amazon.com/Ksmile-Female-Adapter-SamSung-tablets/dp/B01C6032G0/ref=sr_1_2?s=electronics&ie=UTF8&qid=1491931594&sr=1-2&keywords=microusb+to+usb&tag=lifehackeramzn-20&ascsubtag=070f0e80f29026ed2a8bb15596b6ee725bcc7c1b&rawdata=\[t|link\[p|1794218212\[a|B01C6032G0\[au|5716493564230329059\[b|lifehacker).
  * Speakers (any powered speaker does the job, I decided to use a [UE Mini Boom](https://www.amazon.com/MINI-BOOM-Wireless-Bluetooth-Speaker/dp/B01IC263QC/ref=sr_1_2?s=electronics&ie=UTF8&qid=1476287163&sr=1-2&keywords=ue%2Bmini%2Bboomascsubtag=356a9dae356396d1a6aa8ac642898347492b2535&rawdata=%5Br%7Chttps%3A%2F%2Fwww.google.com%2F%5Bt%7Clink%5Bp%7C1787726931%5Ba%7CB01IC263QC%5Bau%7C5716493564230329059%5Bb%7Clifehacker&tag=lifehackeramzn-20&ascsubtag=664dfb1a9b7739d3260b99196c1fcdc4af0959a2&rawdata=\[t|link\[p|1794218212\[a|B01IC263QC\[au|5716493564230329059\[b|lifehacker) because I already owned it and even when it's plugged into the Pi, it still works as a Bluetooth speaker).
  * A Keyboard and Mouse for setup (or use SSH, [Adafruit's Pi Finder](https://lifehacker.com/the-raspberry-pi-finder-easily-locates-your-pis-ip-addr-1702081021) makes this project much easier to do from your main computer because you can copy/paste the longer commands).

Now that you have everything gathered up, connected, and plugged in, let's build this sucker.

### Step One: Register for a Free Amazon Developer Account

Before you do anything, you'll need to register for a free [Amazon Developer Account](https://developer.amazon.com/?rawdata=%5Br%7Chttps%3A%2F%2Fwww.google.com%2F%5Bt%7Clink%5Bp%7C1787726931%5Bau%7C5716493564230329059%5Bb%7Clifehacker&tag=lifehackeramzn-20&ascsubtag=96a7f719de987600422f3ff283e46a0f5ccfd751&rawdata=\[t|link\[p|1794218212\[au|5716493564230329059\[b|lifehacker), then create a profile for your DIY Echo. If you've already done this because you made the previous version of the DIY Echo, note that sections 10-13 are slightly different, so you'll want to change those details. Otherwise, this is pretty straightforward even though it takes a lot of clicks:

  1. Click on the Alexa Tab.
  2. Click Register a Product Type > Device.
  3. Name your device type and display name (I arbitrarily chose "Pi2" for both, though you can enter pretty much whatever you want here), then click Next.
  4. On the Security Profile screen, click "Create new profile."
  5. Under the General tab, next to "Security Profile Name" name your profile. Do the same for the description. Click Next.
  6. Make a note of the Product ID, Client ID, and Client Secret that the site generates for you.
  7. Click the Web Settings tab, then click the Edit button next to the profile dropdown.
  8. Next to Allowed Origins, click, "Add Another" and type in: `http://localhost:5050`.
  9. Click "Add Another," then type in `http://your.raspberrypi.ip.address:5050` but replace with `your.raspberrypi.ip.address` with your Raspberry Pi's IP address. You can find your Pi's IP address using the [Pi Finder tool detailed here](https://lifehacker.com/how-to-control-your-raspberry-pi-from-any-computer-usin-1788592777).
  10. Next to Allowed Return URLs, click "Add Another" and type in: `http://localhost:5050/code`
  11. Click "Add Another" and add in `http://your.raspberrypi.ip.address:5050/code` once again replacing `your.raspberrypi.ip.address` with your own info. Click Next when you're done.  

  12. The Device Details tab is next. It doesn't matter much what you enter here. Pick a category, write a description, pick an expected timeline, and enter a 0 on the form next to how many devices you plan on using this on. Click Next.
  13. Finally, you can choose to add in Amazon Music here. This does **not **work on the Pi powered device, so leave it checked as "No." Click Save.

Now you have an Amazon Developer Account and you've created a profile for your Pi-powered Echo. It's time to head over to the Raspberry Pi and get Alexa working.

### Step Two: Install Git and AlexaPi

Next up, you'll need to fire up Terminal on your Raspberry Pi because we're going to do the entirety of this project in the command line. Before you start the installation you need to update and install a couple things:

  1. Type in `sudo apt-get install update` and press Enter to make sure your version of Raspbian is up to date. Let it do its thing here.
  2. Type in` sudo apt-get install git` and press Enter to install Git. Again, let it do its thing.
  3. Type in `cd /opt` and press Enter to change the directory.
  4. Finally, type in `sudo git clone https://github.com/alexa-pi/AlexaPi.git` and press Enter to clone the AlexaPi GitHub repository. Again, give it a second to download and do its thing.

That's it for the downloading portion, onward to actually installing it.

### Step Three: Run the AlexaPi Installation Script

Next, you'll run an installation script. This automates the installation of everything else you need to get your Echo up and running.

  1. Type in `sudo ./AlexaPi/src/scripts/setup.sh` and press Enter.
  2. You'll be asked a series of questions. If you're using the Raspberry Pi, just press Enter for both the operating system and device prompts. The last question asks if you want to add AirPlay support. If you have an iOS device, this makes it so you can easily stream music from your iPhone to your DIY Echo over Airplay. The script will then download a bunch of software for the next 5-10 minutes, so go ahead and relax for a bit. 
  3. Eventually, you'll be asked to enter in your Amazon developer information. Type in the Device Type ID and Security Profile Description you made way back in step one (we used AlexaPi). Next, you'll need to enter in all those long, complicated numbers for your Profile ID, Client ID, Client Secret.
  4. Finally, the last thing you need to do is authorize your device. You only need to do this once. Head back to your main computer and open up a web browser. Than type in `http://your.raspberrypi.ip.address:5050` replacing `your.raspberryi.ip.address` with your Raspberry Pi's IP address from earlier. You'll then need to log into your Amazon account. After that, you'll see an authorization token.

That's it, the Alexa voice service is now installed on your Raspberry Pi. You just need to start the service. You can either just reboot your device completely, or type in `sudo systemctl start AlexaPi.service` and press Enter to start it.

Go ahead and try it, say "Alexa" into the mic, and it should reply back with a "Yes?" If it's not working, you can type in `sudo systemctl status AlexaPi.service` and press Enter to check the status. Alexa will start up automatically when you reboot your device or if the power goes out for some reason, so you shouldn't ever have to think about it again.
