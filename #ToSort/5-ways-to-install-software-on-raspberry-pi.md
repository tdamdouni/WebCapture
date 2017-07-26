# 5 Ways To Install Software On Raspberry Pi

_Captured: 2017-04-18 at 10:15 from [www.makeuseof.com](http://www.makeuseof.com/tag/three-ways-to-install-software-on-raspberry-pi/)_

Getting your hands on a Raspberry Pi opens up a remarkable world of computing projects - from media centers and NAS boxes to Android emulation, robotics, retro gaming, and software development.

To do these things, you'll need to know how to install software on the Pi. Typically shipping without a microSD card, this also means you'll need to know how to install the main software: the operating system.

Neither of these tasks is particularly difficult, but if the Raspberry Pi is your first taste of Linux, they might seem unfamiliar.

## 1\. A New Operating System

The installation of an operating system for the Raspberry Pi is particularly unusual. However, as it is the first thing you need to do if you want to get your Pi up and running, you'll need to get a handle on it.

![5 Ways To Install Software On Raspberry Pi muo rpi noobs sdformat noobsui](http://cdn.makeuseof.com/wp-content/uploads/2013/11/muo-rpi-noobs-sdformat-noobsui.jpg?edc8eb)

Unless you have a [pre-installed microSD card with NOOBS](http://www.makeuseof.com/tag/how-noobs-for-raspberry-pi-can-help-first-time-users/) ready to insert into your Pi, installing an operating system requires a Windows, Mac or Linux computer. Without a third-party microSD card, it's up to you to download a suitable operating system and load it onto the card.

Once this has been done, the card should be inserted into the Raspberry Pi and the device booted up. Installation will then begin as the operating system is unpacked and organized into the necessary directories. After this has happened, the chosen OS will boot. Several operating systems are available for the Raspberry Pi, including the Debian-based [Raspbian Jessie](http://www.makeuseof.com/tag/5-ways-new-raspbian-jessie-makes-raspberry-pi-even-easier-use/), and the [various versions of Kodi](http://www.makeuseof.com/tag/kodi-raspberry-pi-media-center/).

You'll find [full details on installing Raspbian](http://www.makeuseof.com/tag/optimize-the-power-of-your-raspberry-pi-with-raspbian/), here on MakeUseOf. Various [other Raspberry Pi operating systems](http://www.makeuseof.com/tag/7-operating-systems-you-can-run-with-raspberry-pi/) are also available, though nearly of our projects assume you're running the default Raspbian.

## 2\. Using APT in the Command Line

Perhaps the most common means of installing software on a Raspberry Pi is to use the command line.

![5 Ways To Install Software On Raspberry Pi muo diy waysinstallsoftwarepi apt](http://cdn.makeuseof.com/wp-content/uploads/2017/04/muo-diy-waysinstallsoftwarepi-apt.png?edc8eb)

The apt utility is built into Debian-based operating systems (like Raspbian Jessie), and you can use the **apt-get** command to find the package you're looking for, like this:
    
    
    sudo apt-get install [packagename]

So, if I was to install PHP on my Raspberry Pi, the command I'd use would be:
    
    
    sudo apt-get install php5

After the package repositories have been checked, you'll be asked to confirm installation. Minutes later, the software will be installed.

The repositories that are selected by default are where you'll find compatible, stable software. If you're looking for other software, other repositories can be added, but software installed from these may not deliver reliable results.

## 3\. Add/Remove Software for Raspberry Pi

Another way of installing software on your Raspberry Pi is via the graphical package manager. Many Linux operating systems come with a package manager installed, and as of Raspbian Jessie, so does Raspbian.

![5 Ways To Install Software On Raspberry Pi muo diy waysinstallsoftwarepi add remove](http://cdn.makeuseof.com/wp-content/uploads/2017/04/muo-diy-waysinstallsoftwarepi-add-remove.png?edc8eb)

You'll find **Add/Remove Software** via **Menu > Preferences**. A modified version of GNOME Packages from other distros, if your Raspbian version doesn't have it for some reason, open a Terminal and enter:
    
    
    sudo apt-get install pi-package
    

Add/Remove Software is a straightforward, intuitive tool that lets you browse for apps and utilities via the category buttons in the left-hand pane. Once you have found the software you want to install, simply check the box, then click **Apply,** and **OK** to download and install. Multiple packages can be installed if so desired.

Removing software is a case of clearing the checks, and clicking **Apply** and **OK. **You'll find games, alternative desktops, fonts, browsers, multimedia tools and much more using Add/Remove Software. This is a welcome addition to Raspbian, and replaces the abandoned Pi Store.

## 4\. Install Software with Python

If you cannot find what you're looking for in the Raspbian archives, check packages in the Python Packages Index (PyPI). This is installed by default in Raspbian Jessie, where you can use the pip tool in the command line.

You can upgrade your Raspberry Pi to the latest operating system version to use pip, or install manually:
    
    
    sudo apt-get install python3-pip

…for Python 3, or
    
    
    sudo apt-get install python-pip

…for Python 2.

Usage differs between the two: pip3 for the more recent Python 3, or simply pip for Python 2.
    
    
    pip3 install [packagename]

or
    
    
    pip install [packagename]

Should you need to uninstall these (you probably won't), use
    
    
    pip3 uninstall

or
    
    
    pip uninstall

Because so much coding is done by the community in Python, it's useful to have pip installed.

## 5\. Rub Some Ruby Software Gems

In a similar way, you might want to run software written in the ruby programming language. Appropriately enough, these scripts are called "gems" and can be installed on a Raspberry Pi after the **rubygems** software has been installed.
    
    
    sudo apt-get install rubygems

Finally, a gem can then be installed with:
    
    
    sudo gem install [packagename]

You can find a list of gems at [www.rubygems.org/gems](http://www.rubygems.org/gems). Many scripts are available, including the static website building tool - Jekyll.

## Enhance Your Raspberry Pi with Software

Installing software on your Raspberry Pi turns the little box of tricks into a portable, compact computer that can be used for a range of fascinating projects.

![5 Ways To Install Software On Raspberry Pi muo diy rpi3 pcb](http://cdn.makeuseof.com/wp-content/uploads/2016/03/muo-diy-rpi3-pcb.jpg?edc8eb)

We're not just talking about [broadcasting your own radio station](http://www.makeuseof.com/tag/broadcast-fm-radio-station-raspberry-pi/), or [photographing the night sky](http://www.makeuseof.com/tag/meteors-planets-ufos-raspberry-pi-camera/), either. The Raspberry Pi can be used for [retro video games](http://www.makeuseof.com/tag/retro-gaming-on-the-raspberry-pi-everything-you-need-to-know-si/), while the later versions are suitable for use as a [modest desktop PC](http://www.makeuseof.com/tag/use-your-raspberry-pi-like-a-desktop-pc/).

While there is a learning curve to be overcome in using the command line, it's good practice for anyone with an interest in coding. This, after all, is the very purpose that the Raspberry Pi was created for!

**What is your preferred method for installing software on the Raspberry Pi? Tell us in the comments!**
