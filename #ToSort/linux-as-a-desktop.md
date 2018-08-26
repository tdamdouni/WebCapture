# Linux as a Desktop

_Captured: 2018-06-19 at 19:47 from [dzone.com](https://dzone.com/articles/linux-as-a-desktop?edition=383226&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-06-19)_

DON'T STRESS! Assess your OSS. [Get your free code scanner from Flexera](https://dzone.com/go?i=294429&u=https%3A%2F%2Finfo.flexerasoftware.com%2FSCA-EVAL-FLexNet-Code-Aware-OSS-Scanner%3Futm_source%3Ddzone%26utm_medium%3Dfnca-security-banner%26utm_campaign%3Ddzone-fnca-security-banner-may2018%26id%3Ddzone-fnca-security-banner-May2018). [FlexNet Code Aware](https://dzone.com/go?i=294429&u=https%3A%2F%2Finfo.flexerasoftware.com%2FSCA-EVAL-FLexNet-Code-Aware-OSS-Scanner%3Futm_source%3Ddzone%26utm_medium%3Dfnca-security-banner%26utm_campaign%3Ddzone-fnca-security-banner-may2018%26id%3Ddzone-fnca-security-banner-May2018) scans Java, NuGet, and NPM packages.

## The Goal

Since my first encounter with Linux, around 2000, I made several attempts to adopt it as a real and productive desktop environment for the enterprise.

However, for a number of practical reasons, after a while (some days or weeks), I always resigned and got back to Windows.

Every time there were problems here and there that accumulated one after another and made me think, "Why on the earth do I keep on trying to switch to Linux when I just don't have all these problems with Windows?"

## The Problems

Which problems? Well, sometimes problems with hardware management (WiFi connection, unrecognized USB printers, problems with multiple monitors with different resolutions, HiDPI monitors, etc..) while others with software (Skype missing features or bad conversation quality, dealing with advanced Excel, Word or Powerpoint documents received from colleagues or customers, Windows-friendly VPN clients needed to connect with customers, the forever missing Google Drive client for Linux, the Eclipse visual designer (WindowBuilder) half broken and a number of Windows utilities, for editing or finding files and contents, for capturing screen areas, for analyzing disk usage, taking notes and so on, that I was just accustomed to and for whom I wasn't able to find Linux effective counterparts.

## Why?

So, after all this, why one should still keep on trying and use Linux? Here are some reasons:

  1. it's **free**
  2. it's **open source**
  3. it's **highly customizable**
  4. Windows license policies are becoming more and more locking, e.g. see here 
    * https://www.cio.com/article/2949626/windows/the-takeaway-the-devil-in-the-details-of-the-windows-10-license.html
    * https://youtu.be/JE4SwkJ0Fys?t=206

## Latest Experience

This post is about my latest experience in switching from Windows to Linux. It's more than a year now that I am using Linux as desktop daily on several projects, sharing documents and environments with Windows colleagues and customers; I don't know if I will resign again at some point, but chances are this time is the right one.

Here I will try to put together all the difficulties that I encountered, the choices I made, the solutions adopted, in the hope that this may inspire other people to make this step.

## Which Distro?

As I said at the beginning of this post my first attempts to switch to Linux started almost 20 years ago. Since then, on every PC or laptop I was working on, I always kept some free partition on the disk and there installed and removed several Linux distros in dual boot with Windows.

In more recent years I tried Ubuntu and Kubuntu (in several versions and flavors), Linux Mint and KDE Neon. Every distro had its own good and bad points, but sooner or later the latter were too much to cope with.

Sometimes the problems were after all somehow limited, but something in the look and feel (menus, fonts, icons, window borders, scrollbars, etc.. ) was not satisfying enough.

## A Virtual Parallel Experience with CentOS 6

In the meanwhile, I had to work on a CentOS 6 environment for a customer. In order to minimize problems and to be able to easily backup and restore this environment, I decided to install it as a VirtualBox instance.

The more I was using this virtual CentOS 6 installation, the more I started thinking "This distro is indeed quite good; I like it in several aspects, so why not give it a try for a non-virtual, but real (always in dual boot with Windows of course) installation?"

So I did it! And installed the latest CentOS (7.3 at that time).

## A New Non-Virtual Experience with Centos 7

So here it is: CentOS 7 with its default GNOME desktop environment...

![](https://caselli.files.wordpress.com/2017/11/selection_003.png)

> _...but there exist other desktop environments, other themes, icon packs and so on._

## Which Desktop Environment?

My Dell Precision M3800 laptop comes with a 3200×1800HiDPI resolution.

In this case, the default installation detects the correct resolution, but sets the Scaling Factor at value 2, so to have readable fonts and a good look and feel. In fact, one can appreciate the super high resolution of every graphic detail.

However, I also usually work with an external 1920×1080 monitor and here we are with the first problems!

## CentOS GNOME & Mixed HiDPI and non-HiDPI resolution monitors

In fact I was in the situation where I either had a good look and feel on laptop display but huge characters and windows in the external monitor (due to the scaling factor=2) or (setting the scaling factor to 1) a good look and feel on the external monitor but tiny and unreadable characters on the laptop display.

Yes, it seems that the scaling factor is global instead than being per-display.

I also tried playing with setting the laptop display resolution to 1920×1080, but still, there were problems.

## An Alternative Desktop Environment: MATE

So I discovered MATE Desktop Environment. MATE doesn't try to handle HiDPI displays and scaling factor, so setting a 1920×1080 resolution for both displays was a stable and satisfying solution.

After having tested many desktop environments in many situations I must say that MATE is one of the most stable, reliable and also lightweight desktop environments. It's not much customizable and it lacks some features; for example, pressing the Window key doesn't show you the search tool, which is a nice way to launch an application just by start typing its name. Also the Alt-Tab for windows switching is quite basic and not customizable, but still it's a very, very good desktop environment.

If you are struggling with multiple monitors or just want a rock solid desktop environment, go for MATE.

## Other Desktop Environments

Looking for a lightweight DE you may hit LXDE, Xfce or LXQt: well, I've found they are too minimal, with a somehow poor look and feel.

In addition, their resource consumption was not so lower than MATE, so I discarded them.

On the not-so-lightweight side, other than GNOME, there is Cinnamon, which is very interesting if you are looking for a highly customizable DE, with great effects.

I tried also KDE (also not a lightweight DE), in its recent Plasma version, but somehow it didn't convince me.

## Two Stories

In the following articles, I will put together all the details about the two (great) main Linux experiences that fit my needs (indeed the mixed HiDPI and non-HiDPI monitors problem was the main constraint). In fact, I was best satisfied with the following two combinations. Here I sum up the main characteristics and my impressions, then you'll find more details on specific articles about each of them.

1) CentOS 7.4 + MATE

As I wrote before, I started in November 2016 with CentOS 7.3, then in September 2017 installed CentOS 7.4. Now I know that CentOS 7.5 is available, but didn't tried it yet. With CentOS 7.3/7.4 I choose MATE as DE.

CentOS comes with Nouveau video driver, the open source driver for NVIDIA graphics cards: this is not usually a problem, unless you want to use some specific feature of NVIDIA GPUs (like CUDA libraries for Deep Learning for example).

There are guides about installing the NVIDIA drivers on CentOS, but I found them extremely complicated and often ended up without the graphical part of my operating system!!

CentOS uses XFS as filesystem and doesn't handle NTFS out-of-the-box, so if you have (like me) a dual boot with Windows, after the installation you will have to install ntfs-3g package for handling NTFS and then re-generate the GRUB files, otherwise at reboot you'll see only Linux and not while the Windows entry will be missing! Don't worry: you haven't lost Windows; just install the above package, proceed with the Grub regeneration and restart.

2) Ubuntu 18.04 + GNOME (default)

Ubuntu (independently from the version) also comes with Nouveau video driver as the default for NVIDIA cards, but here the difference is that you can easily switch to NVIDIA drivers.

This distro uses Ext4 as filesystem and NTFS is handled just out-of-the-box, so if you have a dual boot with Windows at the restart after the installation you'll find Windows entry available without special procedures!

In general, Ubuntu uses newer packages (for instance with 18.04 I now have kernel 4.15) but however it's still very stable; it's mainly used for desktops.

Recently Canonical (the company behind Ubuntu) decided to switch back to GNOME as default desktop environment, abandoning Unity.

So, while with 16.04 you get Unity as DE, with 18.04 version you get GNOME.

Well, I must say that this GNOME (the one in Ubuntu 18.04) is very satisfying!  
I like the windows (with previews) switching feature that comes out-of-the-box when you press the Windows key.

I like the popup that appears when I insert the headset jack for choosing the microphone source (with MATE you have to remember do it manually).

Moreover the mixed HiDPI and non-HiDPI monitors problem just vanishes since this version handles the Scale Factor separately for each monitor!

So, for now, I am using Ubuntu 18.04 + default GNOME with great satisfaction, but I consider CentOS + MATE also a very interesting set for a productive desktop (one day I should also try the latest CentOS 7.5, maybe the GNOME experience could be even better!).

[Try FlexNet Code Aware Today](https://dzone.com/go?i=294430&u=https%3A%2F%2Finfo.flexerasoftware.com%2FSCA-EVAL-FLexNet-Code-Aware-OSS-Scanner%3Futm_source%3Ddzone%26utm_medium%3Dfnca-security-banner%26utm_campaign%3Ddzone-fnca-security-banner-may2018%26id%3Ddzone-fnca-security-banner-May2018)! A [free scan tool](https://dzone.com/go?i=294430&u=https%3A%2F%2Finfo.flexerasoftware.com%2FSCA-EVAL-FLexNet-Code-Aware-OSS-Scanner%3Futm_source%3Ddzone%26utm_medium%3Dfnca-security-banner%26utm_campaign%3Ddzone-fnca-security-banner-may2018%26id%3Ddzone-fnca-security-banner-May2018) for developers. Scan Java, NuGet, and NPM packages for open source security and license compliance issues.

Topics:

linux ,windows ,open source ,ubuntu ,linux desktop ,distros ,centos 7 ,desktop environment
