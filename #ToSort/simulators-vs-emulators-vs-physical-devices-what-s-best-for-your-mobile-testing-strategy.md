# Simulators vs. Emulators vs. Physical Devices: What's Best for Your Mobile Testing Strategy?

_Captured: 2017-12-28 at 19:55 from [dzone.com](https://dzone.com/articles/simulators-vs-emulators-vs-physical-devices-whats?edition=347133&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=mobile%202017-12-28)_

### Devices, simulators, and emulators all bring different options for mobile testing. Read on to see which one is best for your testing strategy.

[Download](https://dzone.com/go?i=242231&u=http%3A%2F%2Finfo.saucelabs.com%2FFY17Q3-AST-Mobile-Testing-Reference-Guide_LP-Dzone.html) this comprehensive Mobile Testing Reference Guide to help prioritize which mobile devices and OSs to test against, brought to you in partnership with Sauce Labs.

When it comes to mobile application testing (or even mobile infrastructure testing for that matter), there are three main approaches that you can take to test infrastructure: Simulators, emulators and physical (or "real") devices. Each has its strengths and weaknesses, which determine when one approach is better than another.

Let's take a look at the differences between simulators, emulators and physical devices, and the types of use cases that apply to each.

## Simulators for Mobile Testing

Simulators are often confused with emulators, but there is a big difference between the two. An emulator is a (usually) virtual representation of a physical device that is designed to behave nearly identically to the real device. Simulators, on the other hand, might be best described as unsanctioned emulators.

Developers sometimes create simulators when no emulator is available for a particular mobile device. The simulator loosely mimics the physical device's behavior, but does not run a true copy of the mobile operating system. As such, a simulator might not run mobile apps in exactly the same way as a physical device would. In fact, some simulators only mimic a mobile OS, and will not run apps at all. As such, simulators are sometimes better than nothing when it comes to mobile app testing, but it is far better to use an emulator or a physical device if one is available.

## Emulators and Mobile Testing

As previously noted, emulators are usually virtualized mobile devices. A good emulator runs exactly the same OS as the physical device that it is emulating, and is therefore a really good option for mobile device testing.

The disadvantage to using an emulator is that emulators have limitations that stem from not running the mobile OS on a physical device. Mobile devices include hardware components such as Bluetooth receivers, GPS receivers, cameras, infrared ports, and accelerometers that may not be present on the PC that is running the emulator. Some emulators will let you work around these limitations by providing static values. For example, you might be able to manually tell the emulator to act as if the device is located in Miami, Florida (for the purpose of testing GPS-enabled apps), or that the device is being held in landscape orientation. Some emulators even go so far as to allow you to simulate a 4G LTE connection, or simulate a weak cell signal.

My own personal experience in working with emulators is that emulators tend to work really well, so long as you can find an emulator for the mobile OS that you want to test. On occasion, I have had problems with the computer's video resolution not matching up to the emulated mobile device's native resolution, but this problem seems to be getting better and has not happened to me recently.

## Mobile Testing Using Physical Devices

In most cases, testing on physical devices gives you the most accurate test results because, simply put, you are testing on the actual device on which your software will run. Physical devices eliminate the chances of erratic test results due to unforeseen differences between a real software environment and an emulated one. For this reason, testing on physical devices is a good idea when you need test results to be as accurate as possible.

That said, it is important to keep two factors in mind regarding physical devices. First, there is no guarantee that physical devices will perfectly model production environments in all cases. Even though there is no emulation or simulation at play, other variables still exist within the equation. They include not only runtime variables that may be configured differently on end-users' devices than they are on the physical devices you test on, but also the possibility of hardware modifications or malfunctions, which can make your test environment less than a mirror image of your production environment.

Second, you have to weigh the costs of physical device testing against the benefits. One of these costs is monetary; with the latest iPhone costing a thousand dollars, for example, acquiring a mobile device collection can get expensive. This is especially true when you consider that you will need one of each type of mobile device that your app is designed to run on. Your real-device testing infrastructure could easily end up costing you hundreds of thousands of dollars to acquire, if you set it up yourself.

Even if monetary cost is not an issue, there are times when testing on physical devices is too costly from a time standpoint because the configuration is too complicated. Let me give you an example. A couple of months ago, I was doing some mobile testing and had a variety of mobile devices at my disposal. The problem that I ran into, however, was that there wasn't a practical way of connecting the mobile devices to my lab environment. My lab consisted of about a dozen different virtual machines, all within the 192.168.0.x address space. Even though it is possible to manually configure some mobile devices to use a static IP address of your choosing, doing so just wouldn't work in this situation.

The problem was that the building's Wi-Fi network used a completely different address range. Had I configured the devices with a 192.168.0.x address, the mobile device would not have been able to find my lab environment, because there was no route defined between the wireless access point and my lab environment. While it would have conceivably been possible to create a route, or to use a different address space in the lab, doing so would have undermined all of the effort that went into keeping the lab isolated from the production environment.

Because there was no easy way to connect a physical mobile device to my lab environment, I was forced to use an emulator for testing. In this particular case, the emulator ended up being a far better option, even though physical devices were available.

In general, it is best to limit physical device testing to situations where highly accurate test results are worth the time and money required. In many cases, physical device tests make the most sense for software that is on the verge of being released into production, and has already been vetted by emulator and simulator testing to find most of the problems.

## Conclusion

Physical devices are often the best platform for testing mobile applications. Even so, there are situations in which using physical devices just isn't practical. In these cases, simulators and emulators may provide a testing environment that is more flexible, and that costs less than using physical devices.

Analysts agree that a mix of emulators/simulators and real devices are necessary to optimize your mobile app testing - learn more in this [white paper](https://dzone.com/go?i=242232&u=http%3A%2F%2Finfo.saucelabs.com%2FFY17-ADV-EmuSimRealDevices-WP-LP-DZone.html), brought to you in partnership with Sauce Labs.
