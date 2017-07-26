# Making Your Own RPi Power Button

_Captured: 2017-07-11 at 22:20 from [dzone.com](https://dzone.com/articles/making-your-own-rpi-power-button?edition=306252&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-11)_

Address your [IoT software testing](https://dzone.com/go?i=227243&u=https%3A%2F%2Fwww.parasoft.com%2Fiot) needs - improve quality, security, safety, and compliance across the development lifecycle.

This post describes an easy way to add a power button to a Raspberry Pi that:

  * Only needs a button and wires, no other components.
  * Allows for both a graceful shutdown _and_ start up.
  * Only needs a modification of config files and does not need a dedicated daemon to read GPIO pins.

There are two caveats:

  * This shuts down in the same way as `shutdown -h now` or `halt` does. It does not completely cut the power (like some hardware add-ons do).
  * To allow powerup, the I²C SCL pin (aka GPIO3) must be used, conflicting with externally added I²C devices.

If you want to get started right away, skip to the "Setting this up" section below.

## Powering Down Your Pi

To gracefully power down a Raspberry Pi (or any Linux system), it has to be _shut down_ before the cutting power. On the RPi, which has no power button, this means using SSH to log in and running a shutdown command. Or, as everybody usually does, cutting the power and accepting the risk of data corruption.

Googling around shows a ton of solutions to this problem where a button is connected to a GPIO pin. The GPIO pin is monitored and, when it changes, a shutdown command is given.

However, _all_ of these seem to involve a custom daemon, usually written in Python, to monitor the GPIO pin. A separate daemon just for handling the power button does not sound great, and if it is not apt-get installable, it seems too fragile for my tastes. Ideally, this should be handled by standard system components only.

Another thing is that a lot of these tutorials recommend wiring a pullup or pulldown resistor along with the button, though the Raspberry Pi has built-in pullups and pulldowns on all of its I/O pins that can just as easily be used.

## Shutdown Using `systemd-logind`

Having a shutdown button connected to a GPIO pin is probably not so uncommon, so I Googled some more. I came across the `70-power-switch.rules` udev file from systemd-logind, which adds the "power-switch" tag to some kernel event sources representing dedicated power buttons. Since v225 does this for selected GPIO sources as well ([commit](https://github.com/systemd/systemd/commit/405e116f57b1cf33d4ca0294ab045a9f709bbc96)), a bit of digging shows that:

  * The udev rules add the "power-switch" tag to selected devices. Udev does not use these tags itself, but other programs can.
  * The "power-switch" udev tag causes `systemd-logind` to open the event source as a _possible_ source of power events.
  * When a `[KEY_POWER`](https://github.com/torvalds/linux/blob/v4.12/include/uapi/linux/input-event-codes.h#L190) keypress is received, `systemd-logind` [initiates a shutdown](https://github.com/systemd/systemd/blob/v233/src/login/logind-button.c#L154-L162). It also handles some suspend-related keys.
  * Since last week, `70-power-switch.rules` tags all event sources as "power-switch" ([commit](https://github.com/systemd/systemd/commit/5b987a4e3e98f30b324ce75e07116ea8908bdf44)) and lets `systemd-logind` figure out which could potentially fire `KEY_POWER` events ([commit](https://github.com/systemd/systemd/commit/2546b70a5e507bd1e00fc7ea0e2ed24cd77349af)) and monitor only those (though this change does not really change things for this use case).

## Linux `gpio-keys` Driver

So, how do we let a GPIO pin generate a `KEY_POWER` event? The first logind commit linked above has an example [device tree](http://en.wikipedia.org/wiki/Device_tree) snippet that sets up the kernel `[gpio-keys`](https://www.kernel.org/doc/Documentation/devicetree/bindings/input/gpio-keys.txt) driver, which does exactly that: Generate key events based on GPIO changes.

Normally, the devicetree is fixed when compiling the kernel, but using a devicetree overlay (see the RPi [device tree docs](https://www.raspberrypi.org/documentation/configuration/device-tree.md)) we can insert extra configuration at boot time. I found [an example](http://blog.gegg.us/2017/01/setting-up-a-gpio-button-keyboard-on-a-raspberry-pi/) that ties multiple buttons to GPIO pins and configures them as a tiny keyboard. Then I found an example in the `[gpio-button` package](https://github.com/fivdi/gpio-button) that does the same with a single button and also shows how to configure a pulldown on the pin.

I've created a [devicetree overlay](http://www.stderr.nl/static/files/Hardware/RaspberryPi/gpio-shutdown-overlay.dts) based on that example that sets up the `gpio-keys` driver with a single GPIO to trigger a `KEY_POWER` event. The overlay is just a text file, and I added elaborate comments, so look inside if you are curious. Instructions on installing this overlay are at the end of this post.

## Waking Up

With the above, you get a shutdown button: Press it to initiate a clean shutdown procedure, after which the Raspberry Pi will turn off (note that it does not completely cut power, that would require additional hardware. Instead, the system goes into a very deep sleep configuration while still drawing some current).

After shutdown, starting the system back up means removing and reinserting the USB cable to momentarily cut power. This begs the question: Can you not start the system again through one of the GPIO pins?

I found [one post](http://raspi.tv/2012/making-a-reset-switch-for-your-rev-2-raspberry-pi) that pointed out the RUN pin, present on RPi 2 and up, which can be shorted to GND to reset the CPU (_without_ a clean shutdown!), but can also power the system up. However, having two buttons, along with the risk of accidentally pressing reset instead of shutdown did not seem appealing to me.

After more digging, I found [a forum post](https://www.raspberrypi.org/forums/viewtopic.php?f=29&t=24682) saying that shorting GPIO3 to GND wakes up the RPi after shutdown. It also says GPIO1 should work, but I do not think any RPi makes that pin available, so I haven't tested that. Official docs on this feature seem to be lacking, I found one RPi makes that pin available, so I haven't tested that. Official docs on this feature seem to be lacking, I found one [note on the elinux.org wiki](http://elinux.org/RPI_safe_mode#Wake_from_Halt.5B1.5D) saying `bootcode.bin` (version 12/04/2012 and later) puts the system in sleep mode and starts the system when GPIO3 goes low.

Since GPIO3 is also a normal IO pin, this is perfect: By configuring the shutdown handling on GPIO3, the same button can be used to shutdown _and_ wake up. Note that GPIO3 is also an I²C pin, so if you need to also connect I²C-devices, another pin must be used for shutdown and you cannot use the wakeup feature. Also note that GPIO3 (and GPIO2) have external pullups, at least on the RPi Zero.

## Setting This Up

  1. Get and build the DT overlay. If a file `/boot/overlays/gpio-shutdown.dtbo` is already available on your system, you can skip this step. Download the [devicetree overlay file](http://www.stderr.nl/static/files/Hardware/RaspberryPi/gpio-shutdown-overlay.dts). The easiest is to run wget on the Raspberry Pi itself:  
Compile the devicetreefile:  
[Ignore](https://www.raspberrypi.org/forums/viewtopic.php?f=28&t=140835#p982853) any "`Warning (unit_address_vs_reg): Node /fragment@0 has a unit name,   
but no reg property`" messages you might get. Copy the compiled file to /boot/overlays where the loader can find it:
  2. If running a systemd older than v225 (check with `systemd --version`), create a file called `/etc/udev/rules.d/99-gpio-power.rules` containing these lines
    
        ACTION!="REMOVE", SUBSYSTEM=="input", KERNEL=="event*", SUBSYSTEMS=="platform", \
    
            DRIVERS=="gpio-keys", ATTRS{keys}=="116", TAG+="power-switch"

On systemd v225 and above, this should not be needed, but I have not tested this.
  3. Reboot

Then, if you connect a button to GPIO3 and GND (pin 5 and 6 on the 40-pin header), you can let your Raspberry shutdown and startup using this button.

All this was tested on an RPi Zero W, RPi B, and RPi B+.

This overlay was [merged](https://github.com/raspberrypi/linux/pull/2103) into the official kernel repository, so in the future, step 1 above should no longer be needed. When the stretch is released for the RPi with a newer systemd version, that would only leave a simple modification to `/boot/config.txt` to set this up!

Accelerate the delivery of high-quality software in the connected IoT era through an integrated analysis, testing, security, and analytics platform. Parasoft's [comprehensive portfolio of testing tools](https://dzone.com/go?i=227244&u=https%3A%2F%2Fwww.parasoft.com%2Fiot)automates time-consuming testing tasks and provides management with intelligent analytics and reporting so they can focus on what matters.
