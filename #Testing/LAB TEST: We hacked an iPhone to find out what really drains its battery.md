# LAB TEST: We hacked an iPhone to find out what really drains its battery

_Captured: 2015-10-26 at 23:52 from [blog.gotenna.com](http://blog.gotenna.com/post/131775543810/lab-test-we-hacked-an-iphone-to-find-out-what)_

By Jorge Perdomo & Raph Abrams

At goTenna, we worry about battery usage not only for our app, but for our hardware as well. This week, [several](http://www.theverge.com/2015/10/22/9600466/facebook-acknowledges-ios-battery-drain) [news](http://techcrunch.com/2015/10/15/facebook-working-on-fix-for-ios-app-battery-drain-issue/) [outlets](http://fortune.com/2015/10/15/facebook-battery-killing-iphone-bug/) suggested Facebook's app is the worst-offender when it comes to draining iPhone batteries, and we wanted to figure out whether that was true. And we also thought it'd be interesting to do a little hands-on research into exactly what goes on inside your iPhone that affects its battery life to help us (and others) understand what you can do to get some more juice out of your phone. Here's what we found.

## Testing methodology

All tests were performed on an iPhone 5, which has a 1,440 mAh battery. We conducted all the tests with the iPhone in Airplane Mode. We did this to remove large variables related to poor or inconsistent signal strength (more on that in the Airplane Mode section of our results below).

First, we disassembled the iPhone and tapped directly into the battery lines of the device:

![image](http://41.media.tumblr.com/735fc73e49cf7d4991dcd9818a3be763/tumblr_inline_nwp46prBMW1tu1tea_1280.jpg)

> _Then we put the iPhone back together, running the wires out through a drill-hole. The wires were then hooked up to a current probe and multimeter:_

![image](http://40.media.tumblr.com/c0e5d10706187dc9be03dee3338e128d/tumblr_inline_nwp4b71H9S1tu1tea_1280.jpg)

## Results

**Bluetooth**

The difference between Bluetooth on-and-paired versus totally off was so small our instruments couldn't even read it. With the advent of [Bluetooth Low-Energy](http://gizmodo.com/5725982/what-is-bluetooth-low-energy-ble) (Bluetooth 4.0) -- which is what goTenna uses -- people really don't have to worry about Bluetooth-related battery drain. (Totally different story, of course, with Classic Bluetooth, which is what you use stream to external speakers and similar devices. In those cases, more power is required.)

**Screen brightness**

The difference between a maximum-brightness setting and the lowest setting is huge. On our test iPhone, the difference was 84mA to 220mA -- a 3X increase in power consumption! Put another way, that's the difference between 17 hours of battery life and 6.5 hours!

We then took it a step further and turned off the screen entirely. This brought us down to 21mA, or about a 68-hour lifetime (again, remember, on Airplane Mode).

**Futzing with your screen (a.k.a. doing stuff)**

This was undoubtedly the largest draw on the battery, but also the hardest to quantify as it's difficult to control for this test. We ran it as similarly as possible on apps like Facebook, Instagram, Uber, Google Maps, Twitter, and our own.

We found that average basic manipulation of the screen "costs" you about 200mA, so it easily can more than double your operating current at any one time. Actions like turning on your camera or flashlight makes things worse, with a top-out observed at 700-800mA, which is a rate that can easily kill your battery life in under 2 hours.

**Location v. No location**

Using a location-based app like Google Maps, Uber, or even goTenna's mapping functions requires roughly 75mA in power above baseline. This isn't zero, of course, but it isn't a huge dent in an iPhone 5's 1,440 mAh battery (or in an iPhone 6's 1,810 mAh battery for that matter). To help put this into context, if you were able to run something at precisely the 75mA rate, it would take 19.2 hours to drain an iPhone 5's battery.

**Airplane Mode**

In our lab tests, with nothing else running, on Airplane Mode, and with the screen off, your iPhone consumes almost no power -- indeed, many times as little as single digit milliamps which can last forever on a 1440mAh battery (and of course, on an iPhone 6's even bigger 1,810 mAh battery).

However, if your phone is searching for a signal, like when you're off-grid or underground in the subway, it jumps up to 80mA every 5 seconds, as it struggles to find a tower -- and sometimes goes all the way up to 250mA! The lesson here? Keep your iPhone on Airplane Mode when you think you're not likely to have reliable service -- it makes a huge difference! (And consider [buying some of these](http://www.gotenna.com/products/buy-gotenna) for when you're off-grid.)

## Conclusion

In conclusion, most of your iPhone's battery life is really under your control. The less time you have your screen on, the less bright your screen is, the less your phone is trying to connect to wifi or a tower, and -- shocker! -- the less you mess with it, the likelier you'll be able to count long-lasting battery juice. Of course, we all have implicit understandings of this, but we thought it'd be interesting to put some numbers behind it.

Also, in defense of Facebook, we can confirm their app is not tracking location non-stop, as some reports have suggested. Our tests today definitely aren't the end-all-be-all, but we do feel we've isolated the fingerprints of apps that do use location (as goTenna does), and Facebook's power draw doesn't have that Worst-Ever-Battery-Killer effect you may have read about recently.

In fact, among our sampling, Facebook's power draw is rather average. In our tests, Uber and Google Maps drained a lot more power. Here's some raw data on apps' average current consumption while on standby with the screen on at full brightness on an iPhone 5:

  * Uber = 320mA (uses location)  

  * Google Maps = 302mA (uses location)  

  * goTenna = 290mA (uses location)  

  * Facebook = 217mA  

  * Twitter = 217mA  

  * Snapchat = 210mA  

  * Instagram = 210mA (camera usage takes you to 600-700mA!)  


Do some tests of your own and let us know what you learn:

  * You can do exactly what we did, and try different apps (or even the same ones) as well as some other variables.
  * Use the lab results we shared here to make some educated guesses. Divide the current draw from the full capacity of the battery to get the hours your phone will last doing what it's doing.  

  * You can also use iOS's built-in [battery monitoring feature](http://mashable.com/2014/09/17/ios-8-battery-usage/#cIgrosqg7Sql) -- iOS 8 and above -- to see what drains your own iPhone's battery. You'll get some cool details like how much an app consumes when you're actively using it v. how much it uses in the background, but this tool won't give you any power-saving tips unrelated to app usage.
