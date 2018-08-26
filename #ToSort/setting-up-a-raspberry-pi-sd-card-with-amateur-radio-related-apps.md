# Setting Up a Raspberry Pi SD Card With Amateur Radio-Related Apps

_Captured: 2018-07-17 at 19:12 from [dzone.com](https://dzone.com/articles/setting-up-a-raspberry-pi-sd-card-with-some-amateu?edition=385243&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202018-07-17)_

A friend of mine asked if I could set up an SD Card for her Raspberry Pi and include a few Amateur Radio apps. Rather than just install a bunch of random apps and hand it back, I thought that it might be useful to document the setup steps for others, in case anyone else is interested in doing something similar.

First, you will need to install an OS. The SD card was blank, so I installed the Raspbian from here: <https://www.raspberrypi.org/downloads/raspbian/>.

Then, I wrote the `.img` to the SD card with the `dd` utility. If on Windows, there are utilities you can download to help you burn an image to an SD card, you made need to use Google for help with these.

With my LG monitor, it doesn't recognize the HDMI output from the Pi unless you tweak the settings in `config.txt` to boost the output signal. I've covered this before [here](https://www.kevinhooke.com/2016/04/12/raspberry-pi-bootconfig-txt-for-lg-e2341-monitor/).

Booting up for the first time, the keyboard is configured by default for ` GB_en locale` and a UK keyboard layout. This makes it difficult to find some symbols on a US keyboard like '$', so I have notes on how to switch this to `US_en` using the raspi-config [here](https://www.kevinhooke.com/2015/07/20/setting-raspberry-pi-raspbian-default-locale-and-keyboard-settings/).

By default, Raspbian is configured to boot to a graphical desktop and to log in automatically with the default user ID/password (pi/raspberry) - you should change your password on the first boot. You can change this option in raspi-config, too, if you'd like to boot to a shell or require a login at boot.

After the first boot and the initial setup described above, the list of apps I thought would be useful to install is most of what I covered in [my July 2016 presentation](https://www.kevinhooke.com/2016/07/05/amateur-radio-related-uses-for-the-raspberry-pi-slides/) at one of our RCARS club meetings on using a Raspberry Pi with Amateur Radio. Here are each of the apps that I installed and how to start/use them:

  * Installed xlog: 
    * sudo apt-get install xlog
    * To start, double-click the icon on the desktop
  * Installed cqrlog 
    * sudo apt-get install cqrlog
    * To start, double-click the icon on the desktop

There are many things you can do with RTL-SDR. You'll need an RTL-SDR dongle to take advantage of these. Furthermore, here's a couple of examples. Most of these are command line only, from the Terminal, which you can open from the desktop here:

![](https://i2.wp.com/www.kevinhooke.com/wp-content/uploads/2018/07/img_5b457123f0a72.png?w=525&ssl=1)

Dump1090 receives and decodes ADS-B transponder signals from airplanes flying overhead (depending on your antenna, within about a 100-mile radius) on 1.090Ghz. To run, there's a couple of different modes:

  * 'Interactive' mode is started like this from a terminal. First, it will include 'cd dump1090,' then:

  * `./dump1090 -interactive`

You'll see a display like this that updates every second, showing decoded information from the received ADS-B transponder signals:

![](https://i2.wp.com/www.kevinhooke.com/wp-content/uploads/2018/07/img_5b4571f94dda9.png?w=525&ssl=1)

'Net' mode displays the received signals via a webpage. You'll need the Pi to be on a network, either wired or via Wi-Fi, and you'll need to know your Pi's IP address (which you can find by running 'ifconfig' in a Terminal). Run this with:

`./dump1090 -net -quiet`

And, then, point a browser at your Pi's IP address on port 8080 (e.g. assuming your IP is 192.168.1.75, http://192.168.1.75:8080), and you'll see the received signals plotted like this:

![](https://i1.wp.com/www.kevinhooke.com/wp-content/uploads/2018/07/img_5b45758f9dde6.png?w=525&ssl=1)

The received signals, including latitude and longitude, are plotted on the map. Other signals with no location information are displayed in the table on the right.

Other things you can do with the RTL-SDR utils: `rtl_fm` allows you to tune to a specific frequency and decode the FM modulation. With a combination of piping the data to your audio out if you have speakers attached to the Pi's audio output, you can receive FM signals and output the audio like this (scroll to the right for the whole command):

This tunes the RTL-SDR to 96.9Mhz, uses wideband FM, a sample rate (I think) of 200000, pipes the audio '|' into aplay to play the audio stream. Take a look at the RTL-SDR docs [here](https://osmocom.org/projects/rtl-sdr/wiki/Rtl-sdr) for more on those options.

Hopefully, this will help get you started! For future reference, I have a number of other beginner Raspberry Pi posts [here](https://www.kevinhooke.com/2016/02/02/setting-up-your-new-raspberry-pi/).

Topics:

iot ,tutorial ,rtl sdr ,sdr ,rtl ,raspberry pi ,sd card
