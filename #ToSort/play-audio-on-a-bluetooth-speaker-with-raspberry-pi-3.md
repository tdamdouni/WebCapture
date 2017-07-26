# Play audio on a Bluetooth speaker with Raspberry Pi 3

_Captured: 2017-05-19 at 15:38 from [www.raspberrypi.org](https://www.raspberrypi.org/magpi/bluetooth-audio-raspberry-pi-3/)_

![](https://www.raspberrypi.org/magpi/wp-content/uploads/2016/05/BluetoothLead.jpg)

> _An oft-requested feature, Bluetooth support on the Raspberry Pi 3 board - along with its wireless LAN capability - has been pretty well received in the Pi and maker communities at large. How can you use it, though?_

In this tutorial, we'll cover the basics of how to get your Bluetooth up and running on the Pi 3, and how to connect to a Bluetooth speaker so you can play all your smooth Sonic Pi tunes that you've been learning from Sam Aaron's tutorials.

**STEP-01** Set up the Raspberry Pi

While Bluetooth is on the Raspberry Pi 3, you need to install a few bits of software to make sure it works properly. It's best to start by making sure your version of Raspbian Jessie (this won't work on Wheezy) is up to date. Open the terminal and begin with:

Follow this up by installing the Raspberry Pi Bluetooth software and the excellent Blueman Bluetooth manager:

You may need to reboot after this, but you'll probably be fine to carry on to the next step.

**STEP-02** Set up your Bluetooth speaker

Make sure your Bluetooth speaker is all charged up and ready to go, then switch it on. Ours has a satisfying beep once you do so. If there's a syncing button or sequence for it to start searching to pair with devices, press it/do it and head back to the Raspberry Pi. If you want to check whether the speaker is actually looking, you could always find out if a mobile phone or tablet is able to see it. Don't pair with it, though, as that might cause problems in the future.

**STEP-03** Connect the speaker up

Open up Blueman by going to the program menu, Preferences, and Bluetooth Manager. As long as the speaker is still trying to sync, clicking Search should make it show up in the interface. Right-click on it, then hit Pair. It should connect to the device, shown by a few information bars on the connection strength - if it then suddenly disconnects straight afterwards, you may need to right-click on it again and hit Connect. Test it out by playing a video on YouTube; it may work straight away like this!

**STEP-04** More setup

Depending on how your Pi is set up, the Bluetooth audio might not work at step 3. If this is the case, it's best to install some extra software to try to get it working. Open up the terminal again and install PulseAudio and its Bluetooth module:

If you open the PulseAudio panel now, it may not show much information, especially whether or not you can switch to the Bluetooth speaker. You'll more than likely need to reboot the Raspberry Pi - do that now!

**STEP-05** Connecting with PulseAudio

After the Raspberry Pi has booted back up, check the Volume Control option in the Sound & Video category of the program menu. On output devices, it should list bcm2835 ALSA as the default output. Go and connect or re-pair with the Bluetooth audio device and it should then be picked up as an option in the Volume Control. Try playing a YouTube video again: you may need to mute ALSA and set the Bluetooth device as a fallback, but it should start playing the audio!

**STEP-06** Bluetooth uses

There are some quite obvious uses for Bluetooth speaker connections: not all monitors have audio out, so this solves that issue. This means videos, games, and music (especially the kind from Sonic Pi) are now available to you. You could also incorporate it into a project and create an internet radio player for yourself, activated with the touch of a button. It could be used in a scary Halloween decoration that houses multiple screams and whispers. There's a lot you can do with this new functionality!

### Subscribe and never miss an issue

![](https://www.raspberrypi.org/magpi/wp-content/uploads/2017/02/New-Subs-Banner_new.png)

> _Get a free Pi Zero W with every twelve-month print subscription_

Get a a brand new Raspberry Pi Zero W, a case for it, and a selection of adapter cables with a [twelve-month print subscription](https://www.raspberrypi.org/magpi/subscribe/) to The MagPi!
