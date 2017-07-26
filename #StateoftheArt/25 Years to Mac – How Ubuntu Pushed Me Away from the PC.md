# 25 Years to Mac – How Ubuntu Pushed Me Away from the PC

_Captured: 2015-11-19 at 14:09 from [randomdrake.com](http://randomdrake.com/2013/02/23/25-years-to-mac-how-ubuntu-pushed-me-away-from-the-pc/)_

After being on computers for 25 years, I did something I've never done before: I purchased a Mac. For the last 10 or so years, I've owned PCs or laptops that were setup to boot to Windows or some flavor of Linux. That flavor of Linux has been Ubuntu for a long time. Until 12.04, and [Unity](http://en.wikipedia.org/wiki/Unity_\(user_interface\)) came along, this was a pretty happy experience. I stuck in the 10.x versions, only dabbling in the 11.x versions until 12.04 came out. I've written many blog posts regarding Ubuntu and the use of Ubuntu over the years. I've even [written open source software](https://github.com/randomdrake/nasa-apod-desktop) for it. You could even say I was a fanboi for a while, trying to push all my friends and family away from the evil of Mac or Windows to the open beauty that was Ubuntu.

Over my years of computing, I too had developed a completely biased sense against the Apple ecosystem. The oft-touted cries of "walled garden" or "my device, my rules" or "locked into Apple" arguments were valid to me. I couldn't, for the life of me, understand why people were paying so much money for something that seemed so obviously wrong. My mind has been changed and I would like to share the story of how it happened since I'm much, much happier for it.

Here's a screenshot of the very last time I booted into my Ubuntu installation to push some files onto an external drive:

![Goodbye Ubuntu](http://randomdrake.com/wp-content/uploads/2013/02/goodbyeubuntu.jpg)

> _[Goodbye Ubuntu](http://randomdrake.com/wp-content/uploads/2013/02/goodbyeubuntu.jpg)_

This is representative of the constant, buggy struggle that Ubuntu became for me. All I had was a dual monitor setup on an NVIDIA card with an Intel chipset. Nothing particularly special or weird, it was a rig I had built to play Battlefield 3 back when I used to still be a gamer. I decided that, in addition to my laptop being a dual-boot machine, I needed my PC to dual-boot since I would be working from home.

## The Struggle

The first struggle came when trying to setup a wireless USB adapter. I was able to find a driver and fire up the abomination that was [NDISwrapper](http://en.wikipedia.org/wiki/NDISwrapper). Unfortunately, I had to end up Googling around for hours to find a solution consisting of modifying the driver itself before the USB adapter would work. Once it was actually working, it would just randomly stop every once in a while. This never occurred in Windows. This required me to remove and re-insert the USB adapter, constantly. I actually moved my PC onto my desk instead of on the floor because I got sick of bending over to take care of this.

Next, came the display. Ubuntu, for some reason, labeled my two monitors as "Laptop" and treated it as a single screen. This meant I could not use the regular display configuration. I was forced to use the [NVIDIA display configuration utility](https://launchpad.net/ubuntu/+source/nvidia-settings). This also meant I constantly struggled with apps not knowing how to go to a full screen properly, weird issues dragging windows around, and other oddities.

Onto the window manager. Beyond the frequent crashing for no particular reason, there were constant glitches. Leave the computer for a while and come back? Title bars for windows would become glitchy and unreadable. Restoring a window from being minimized? Sometimes it'll just be white. Go ahead and minimize and restore it again to fix. Icons randomly disappearing from the dock, requiring a restart of Unity? Yup, pretty consistent there too. Not only this, but the experience felt laggy. On the beefy machine it was running on, I expected the performance to be smooth and responsive but it was quite the opposite.

> Unfortunately, none of these bugs were consistent enough to recreate reliably which meant I just had to deal with it until it because so infuriating that I would have to find a fix.

I decided enough was enough and Unity was not going to work for me. At the login screen, it's possible to select [GNOME](http://www.gnome.org) instead of Unity so I gave that a shot, assuming going back to GNOME would work. As soon as it booted in I was greeted by a monitor that didn't work and a window full of error messages. After Googling around for a while, I found some configuration changes to make in my [xorg.conf](http://en.wikipedia.org/wiki/Xorg.conf) file and was able to actually get it working. I was met with even more errors and problems so I decided it wasn't going to work for me. I decided to switch back into Unity.

When I came back? All of my settings were gone. All of my changes to use a sane Alt-Tab in the [CompizConfig Settings Manager](http://wiki.compiz.org/CCSM), my keyboard shortcuts, everything. I was back to what it was when I first installed. Extremely frustrated, I decided to give the [Mint](http://www.linuxmint.com) side of things a try and give [Cinnamon](http://cinnamon.linuxmint.com) a shot. Again, a few weird problems, but got that running as well. Cinnamon didn't quite fit the bill either. I ran into a display issue or two and found myself actually missing a few things from Unity so I decided I was going to dig in and really give Unity a shot. I didn't want to jump ship to an entirely different flavor of Linux because I had already invested so many years in getting used to the Ubuntu experience.

When I purchased a printer for my computer? Of course Ubuntu had no idea what to do with it. Of course there was a run around necessary to get it working. Even the mouse had problems. My old Logitech MX500, for one reason or another, would spam the logs in [dmesg](http://en.wikipedia.org/wiki/Dmesg) whenever I was using the scroll buttons on it. Sound would skip while listening to music using anything Flash or HTML 5 related like Grooveshark or Pandora. The whole system would lock up occasionally pegging a quad core CPU for no reason at all. Sometimes, it would just crash entirely.

## How I Want to Spend My Time

When I'm at a computer, its because I want to get things done. Gone are the days where I have time to tinker around and spend countless hours Googling for some obscure mail archive to find I need to change "bop" to "boop" in /etc/something/config.ini. The amount of time that I had to spend doing this crap was growing instead of shrinking. This is not a good direction for an operating system to go.

Over the years, I've developed enough acumen to get a lot done in short periods of time. I've found that I work in extremely productive bursts. This means, when I'm ready to get down to business: I'm ready to get down to business. I don't want anything getting in my way. The glitches I had experienced in previous versions of Ubuntu were ones I could fix, get out of the way, and not have to worry about again. They were re-produceable, identifiable, and the fixes worked for me.

With Unity and 12.04, the glitches were random, weird, didn't offer any useful information, and were downright annoying. Some fixes would work for a while then stop working. Some bugs, like the aforementioned blank window, I simply couldn't figure out after a couple hours of Googling so I just got used to them as best I could.

Hours Googling, being frustrated, and being bumped out of the zone due to random glitches was no longer acceptable for me.

## Making the Switch

I knew I had to make a switch. At my most recent job, I was given an iPhone 3G (at a time when the 4 was new) and it was the first Apple product I'd owned. It was an okay device but it was a hand-me-down and I was much more impressed by the 4. By the time the iPhone 4S came around, I was eligible for an upgrade. I decided to take the plunge and it literally changed something inside me. My immediate thought after experiencing the device was: "I want to build things for this."

Exploring many options for iOS development, I looked into building a [Hackintosh](http://en.wikipedia.org/wiki/OSx86) for a while until I realized it wasn't going to be as stable an experience as I wanted. Since I could still get the development done I needed to and had recently built a gaming rig, I couldn't justify the switch. So I just dreamed of eventually having some spare dough around to drop on a Mac, but wasn't terribly serious about buying one.

Fast forward a year or two and it was Christmas time. I wanted to get something nice for myself that I would enjoy. I struggled back and forth again over justifying the cost for dropping into the Mac ecosystem. Back and forth I went until I decided, yet again, I couldn't quite justify the switch. I bought myself a New iPad ensuring I would be able to return it if I didn't like it. Of course, I loved it. My wife gave up her Kindle Fire usage and we shared the iPad. It was incredibly powerful, had a beautiful screen, and was light years beyond any tablet experience in terms of responsiveness, design and construction. I had another "I want to build things for this" moment.

Now the desire for iOS development was getting stronger. The MBP Retina came out and I was absolutely drooling over it. I wanted one so bad, but, I still couldn't justify the cost. "I'm not building anything in iOS, yet. Maybe I'll hate the OS and be stuck with a $2,500 bad decision. Walled garden. Non-customizable." Those were the thoughts that were keeping me from taking the plunge.

## Taking the Plunge

Eventually, I was sick and tired of not being able to spend time developing in the zone due to random glitches and small problems. I didn't want to spend hours or days finding solutions. In short:

> I was tired of spending time on my computer working on my operating system instead of working on my projects.

I carefully considered all my options. We don't have an actual Mac store here, so I didn't have the pleasure of being able to identify, play with, and choose the right Mac for me. I had to go on specs, the advice of others, and my gut instinct.

I wanted the MBP retina, of course. My friend got one and it was an absolutely incredible machine. The design, the responsiveness of the SSD architecture, the retina display; it was beautiful and I was jealous.

Since it was my first foray into the Mac environment, I didn't want to be disappointed. I decided that I would be much happier if I purchased something on the lower end, in case my pre-conceived notions about the OS were correct. I had a choice between the Air, the MBP and the Mini. My local store was constantly out of the upgraded versions and Apple does not ship here.

I decided the base MBP would be the best decision for me. The reason being: I had no idea where I was going to feel a bottleneck on the OS during my development. Would I really be CPU bound? Would not having SSD really slow things down that much? I had no previous experience so I had no idea if those things were worth it. The MBP was upgradeable, so I could fix anything I perceived as a shortcoming in my experience. With the Air I was locked in and I didn't know enough to know whether that was okay with me. The store was constantly out of the upgraded Mac Mini version, so I settled on the last, base 13″ MBP they had in the store.

I was elated bringing the box home. The unboxing was, of course, elegant and easy as my previous Apple products had been. The physicality of the product was awesome. I turned it on, went through the simple configurations, and was up and running pretty quickly. While waiting for the initial setup to complete, I started reading about the various things I could do with my new OS. I started reading about the trackpad and the gestures that were possible. I checked out some things that were "must install" for every user and started to make a list of the OS X apps I had always wanted to try.

## Welcome to OS X

The operating system came up and it was beautiful. The responsiveness, the elegance, and the simplicity were awesome. Being a consistent hater of trackpads over the years, it was one of the first things I played with. I had read reviews of it being incredible before and they were not exaggerating in the slightest. The gestures make sense and are very useful. The trackpad itself worked really well and wasn't constantly triggered by my thumbs accidentally brushing them.

Then I started to dive into the operating system. What I found was absolutely shocking: it was far more customizable than I had ever dreamed. Want to move the dock around? Sure, go ahead. In Ubuntu? Nope. Want to change how the mouse scroll wheel works? There's a program someone wrote for that. Every tiny adjustment I wanted was available either directly in the OS or through the installation of a simple program.

Ubuntu had introduced the ability to launch a program or find something from the dash and I had started to like it, even though it was buggy and extremely slow in a lot of cases. Spotlight? Completely blows it away. It's fast, responsive, and gets me to the program or thing I'm looking for every time.

Every device I hooked up to the machine worked flawlessly. Printer? Plug it in, it finds what you need, and you're good to go. Monitor? Plug it in and it recognizes it correctly and makes it available to start working right away. External hard drive? I plugged it in and it immediately asked me if I wanted to start using it for backups. It's like the OS knew what I wanted and was eager to please every step of the way instead of the struggle I was used to. I didn't have to tell it, nay smash it with a hammer in the face to force it, to get it to work. In other words:

> OS X delivered the experience I wanted Linux to, and more.

## What's My PC Up to Now?

My PC now sits on the floor under the desk. Beyond grabbing some files off of it: it's dormant. I keep it around in case I need to boot up Windows and test something or if I get the itch to start gaming again. But, I am now a 100% Mac convert.

The hardware is great. The OS is a constant pleasure. All my time that I want to spend developing or doing things is actually spent developing or doing things instead of the constantly interrupted, buggy experience I had before. Because it's Unix-based, everything is familiar or easy to learn since I spend most of my time in a terminal.

Instead of finding a brand new and unfamiliar experience, I found the experience I was looking for Linux to be: a great and consistent environment for me to get things done.

Liked this post? You should follow me on Twitter [@randomdrake](https://twitter.com/randomdrake/) or subscribe to my [feed](http://randomdrake.com/feed/).
