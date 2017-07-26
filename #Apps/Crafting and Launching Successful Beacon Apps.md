# Crafting and Launching Successful Beacon Apps

_Captured: 2015-11-19 at 20:47 from [www.vektordigital.com](http://www.vektordigital.com/2015/11/16/crafting-and-launching-successful-beacon-apps/)_

We were early to hop on the "beacon train" in 2013, and after two years, we still believe there's a bright future for proximity based user experiences. During that time, we've been lucky enough to work on 10 smartphone applications that use beacons and bluetooth low energy. Over the course of these projects, we've learned powerful lessons about what makes separates successful and unsuccessful beacon apps. The goal of this article is to share the patterns, concepts, and best practices our team utilizes whenever tackling a new beacon project. Hopefully you'll find it helpful as well.

### 1\. Set Stakeholder Expectations

Beacons provide a whole new way for businesses to provide proximity based user experiences. With that said, there are limitations to what experiences beacons can support. Unfortunately, these limitations often go unmentioned when people get their first exposure to beacons. Here are some of the common misconceptions our team sees when meeting with stakeholders.

**Common Misconceptions**

  * **All content lives in the beacon.** In reality, beacons broadcast a small advertising packet with a serial number. In most cases, beacons simply don't have the storage for more than a few lines of text, let alone images, or video. It's easy to see how stakeholders get confused here. As a user, beacon content magically pops up on a smartphone when near a beacon. But the reality is users see see location specific text, images, and video because their smartphone is detecting the beacon's serial number and then pulling the content from a server, or locally from the phone.
  * **Battery life is forever. **Using any of the sensors on a smartphone causes battery life drain. GPS does, the accelerometer does, and the bluetooth antennae used for beacon detection does as well. If your app requires constant beacon scanning or long running bluetooth usage, your users will see battery drain. Fortunately, the right development team can optimize your app's bluetooth interactions so that your users won't delete your app.
  * **Infinite range. **Beacon range is dependent on the batteries that power them. Many beacons run on AA batteries or coin cells, which, in most cases, don't reach more than 50-120 feet. Smartphones and tablets broadcasting as beacons tend to reach further distances, but rarely more than 150-200-ft.
  * **Pinpoint accuracy. **At their core, beacons are a proximity, not a 3D positional tool. It's better to think of beacons as being, immediate, near or far to a smartphone, as opposed to a super-accurate indoor GPS. It's true, beacon signal strength can be roughly correlated with distance when in close proximity to a beacon. But beyond 10 to 20-ft, this correlation breaks down because signal strength drops off exponentially as a smartphone moves away from a beacon. Often, a user's smartphone will have a hard time telling the difference between a beacon that is 20-ft away versus one that is 35-ft away.
  * **No app required.** For the most part, users need to have a mobile app on their smartphone to detect beacons. If you are going to deploy custom beacons at a business, this means that they'll likely need to create an app that is specially configured to detect beacons. With the launch of Eddystone this has changed for Android, but for iPhone, users can only detect Eddystone beacons using an app that is running the Eddystone SDK. For many projects, this means that you'll still need an app.

### 2\. Validate If You Need Beacons

Beacons do not make experiences - they make some experiences smarter and faster. Carefully consider your business requirements. Do they call for proximity based user experiences? If yes, still note that there are a suite of alternative technologies like geofences, wifi, and NFC tags. If no, maybe it's best to walk pass on proximity entirely.

![Alternatives.001](http://www.vektordigital.com/wp-content/uploads/2015/11/Alternatives.001-1-1024x768.jpg)

> _Not every project needs location based user experiences. But if yours does, know that a beacon based solution isn't the only option._

Let's explore an example of an outdoor basketball app that checks in a user when they arrive to the basketball court. The idea is to keep track of which players attend each game. To capture these check ins, you could deploy beacons around the court, and then check in the user when their phone detects a beacon. Or, more practically, you could use a geofence, relying on your user's smartphone GPS to determine if they've reached the field. In this case, beacons could work, but bring infrastructure overhead that just is not needed.

Now let's explore another example. Imagine a brick and motor retailer creating an app that tells the user which department they're currently in. In this scenario, a potential solution is wifi RSSI fingerprinting. With an appropriate number of wifi hubs throughout the store, it's reasonable to estimate which department the user is in. Considering this retailer's requirements, beacons might not be worth the cost.

And sometimes, projects don't need contextual based experiences at all. Should your B2B accounting application be powered by beacons? Maybe not. Before incorporating beacon technology into your app, you need to take a hard look at ROI. How much will it cost to incorporate beacon scanning into your app? What is the cost to deploy the beacons? And finally, what is the long term cost associated with maintaining beacons.

### 3\. Know Your Operating Systems

As of late 2015, mobile apps are the main method for users to interact with beacons. And as an app owner, you have to understand the differences that your developers and users will experience if they're on Android, iOS or Windows. Each operating system provides pros and cons, technical limitations, and unique approaches to beacons. In some cases, these differences force app owners to deploy on one platform, but not another. Fortunately, as each year passes, Android, iOS and Windows are providing mature native frameworks for beacons. The end result is more app owners launching beacon technology one more than one platform.

**Android**

  * You can perform all the scanning and all the background monitoring you want. The trade off here is you will impact your user's battery life with long running bluetooth operations.
  * An app isn't required with Eddystone beacons.
  * More than 67% of Android devices support BLE, and this percentage increases every month. (source: developer.android.com/about/dashboards/index.html)
  * Individual models are better at BLE than others.
  * Eddystone, Altbeacon are software frameworks for building beacon interactions into an app.

**iOS**

  * Users can get lock screen notifications even when an app is terminated (the user shut it off, but didn't delete it).
  * Apple provides a nifty lock screen icon for apps that are currently detecting a relevant beacon. This only works for apps that are already downloaded onto the user's phone.
  * Greater than 84% of devices support BLE.
  * Core Bluetooth is required for complex background functionality.
  * iBeacon and Core Bluetooth are the software frameworks that developers use to build beacon interactions.
  * Eddystone works on iOS too, but is not built into Apple's existing frameworks. Users need an app with the Eddystone SDK to detect Eddystone beacons. Google Chrome for iOS is likely the widest-distributed iOS app running the Eddystone SDK.

**Windows**

  * Available on Windows 8.1 with open source WinBeacon
  * Available natively with Windows 10
  * Windows-based beacon frameworks allows monitoring and ranging (natively called watching and scanning)
  * Developers will rely on WinBeacon for apps running Windows 8.1 or higher. And for Windows 10 or higher apps, they'll likely use Window's native beacon functionality.
![Operating Systems.001](http://www.vektordigital.com/wp-content/uploads/2015/11/Operating-Systems.001-1-1024x768.jpg)

> _Here are some of the software frameworks your developers will be using when building beacon apps._

### 4\. Understand Beacon Background Modes

Some proximity based experiences rely on smartphones constantly scanning for beacons, even if the user isn't actively using the app. But as we've explored, beacon background detection is limited by the user's operating system, battery life, distance. Let's distinguish some of the functionality that can and can't be done when scanning for beacons in the background.

**What you can do.**

  * Determine proximity (immediate, close, far) from beacons.
  * Send operating system appropriate lock screen messages.
![Notifications.002](http://www.vektordigital.com/wp-content/uploads/2015/11/Notifications.002-1-1024x550.jpg)

> _Here are some of the types of lock screen notifications your app can implement._

**What you can't.**

  * Avoid impacting battery life. The more your app is running in the background, the more it will negatively impact your users' batteries.
  * Show content outside lock screen notification norms. Examples of violations include launching an application into the foreground without the user allowing, showing a full screen pop-up.
![Notifications.001](http://www.vektordigital.com/wp-content/uploads/2015/11/Notifications.001-1-1024x550.jpg)

> _Sorry folks, you can't show this big beautiful coupon on your lock screen. You could, however, show this screen after the user opened your lock screen notifications._

### 5\. Convey Value During Onboarding

Despite Apple, Google and Windows formally adopting beacon functionality into their operating systems, beacons have yet to reach mass adoption. Some retailers, stadiums and consumer facing loss prevention solutions have embraced beacons, but the average user still only has a small number of beacon-enabled applications on their smartphone. As an app owner, it's your job to convince the user during onboarding to allow beacon permissions, and more importantly, embrace your value proposition. During onboarding, explain the benefits of your beacon feature, without digging into technical details of how beacons work. If you save your user time or money, they'll buy in.

![Onboarding.001](http://www.vektordigital.com/wp-content/uploads/2015/11/Onboarding.001-1-1024x550.jpg)

> _Tile does a great job of explaining their value proposition during their onboarding flow._

![Onboarding.002](http://www.vektordigital.com/wp-content/uploads/2015/11/Onboarding.002-1-1024x550.jpg)

_And here's an example of a long-form onboarding for Facebook's Place Tip feature. Notice how the focus is on value and explaining to the user exactly what they are sharing with Facebook and other users._

### 6\. Handle Bluetooth Off States

Not everyone has bluetooth "On" all the time. Let these users know they're missing out. Many apps present users a request to turn on bluetooth during onboarding, but most fail to reengage the user after the initial ask. This is a shame. If you're truly providing value to your users using beacons, it's worth showing unintrusive empty states and messaging to get them to turn bluetooth back on. iOS provides handy one-click shortcuts to the user's settings menu, so it's easy to implement.

![Bluetooth Permissions.001](http://www.vektordigital.com/wp-content/uploads/2015/11/Bluetooth-Permissions.001-1-1024x550.jpg)

> _Not everyone has their bluetooth on when they download your app. Tell them why it's needed and ask to them to turn it back on._

### 7\. Provide Privacy Settings

Get up and walk around your office. As you pass your coworkers' computers, take a look at their front facing cameras. What percentage of them have a piece of tape covering the camera? In many offices, this number is high, and growing. And next time you download an app that asks for your location, what do you do? Do you always tap, "No", or do you occasionally tap "Yes" if it's an app you trust?

Users value privacy more than ever before. Beacon applications require user bluetooth access, and in most cases, background location. These aren't requests to be taken lightly in a world of valued privacy.

![Settings.001](http://www.vektordigital.com/wp-content/uploads/2015/11/Settings.001-1-1024x550.jpg)

> _Users value privacy. How can you respect your users' privacy while meeting your business goals?_

As app owners, how do we navigate this? A favorite quote of mine comes from the CEO of Estimote, Jakub Krzych. He was giving a presentation at the San Francisco Beacon Meetup when he shared this straightforward advice - "Just optimize for user, and the rest will work itself out." I completely agree - if your value proposition is strong enough, your users will trust that they're entering a fair trade by sharing their bluetooth and location access. And to show your users that your app is trustworthy, be completely transparent on what your users are sharing and how to change it.

![Settings2.001](http://www.vektordigital.com/wp-content/uploads/2015/11/Settings2.001-1-1024x550.jpg)

_Provide your users with transparent explanations of what your app is accessing, and give users quick access to update these privacy settings. This isn't bad business, this is trusting the user to make an informed decision about your value proposition. _

**Ask yourself - Are you optimizing for the user?**

  * Be transparent about why you want their location
  * Explain what you are collecting and how it benefits them
  * Give them an option to opt-out, or change privacy settings

### 8\. Ensure User Interface Matches Beacon Accuracy

Beacon accuracy isn't perfect. Your user interface shouldn't suggest it is.

Let's use the example of an app that shows the name, breed and emergency contact info for dogs tagged with a beacon. Now imagine that you're using this app at a dog park with 20 dogs tagged with beacons. If three are within 50-ft of your phone, your user interface could show all three of these dogs and how far away they are. But remember, smartphones have a hard time accurately detecting the distance of beacons further than 15 to 20-ft away.

A poor user interface would list all three dogs and list their distance in feet. For example, dog #1 is 12-ft away, dog #2 is 30-ft away and dog #3 is 40-ft away. Since the smartphone can't reliably determine distance to this level of accuracy, it's misleading to the user to provide such explicit measurements through the user interface. Additionally, if dog #3 is now 25-ft away, your smartphone still might think that dog #2 is closer, despite it actually being 35-ft way. The user will see the readings in the app, and not have it match with what they see in real life.

The better user interface for this app would show all three dogs on the screen, but would use less precise terms of measurement. Dog #1's avatar could be shown larger than dog #2 and #3. And as dog #3 runs closer to the user, it's avatar would gradually grow while #2 stays the same size. At a glance, your user knows which dog is relatively closer than the others, but won't be confused if there are beacon inaccuracies or interference.

### 9\. Use Beacon Cloud Management

If you don't have a maintenance plan, your app won't be useful for long. Beacons get stolen, die from battery drain, get moved, and need firmware updates. Prominent beacon manufacturers provide cloud management systems that will allow your operations team to know when a specific beacon's firmware is out of date, where it was last located, and if its battery needs to be replaced.

![Dashboards.001](http://www.vektordigital.com/wp-content/uploads/2015/11/Dashboards.001-1-1024x550.jpg)

![Dashboards.002](http://www.vektordigital.com/wp-content/uploads/2015/11/Dashboards.002-1-1024x550.jpg)

> _Your beacon application needs a cloud management system to succeed. How else will you track beacon locations, battery life, firmware and more?_

### 10\. Deploy with Interference in Mind

Beacons signals aren't transmitted uniformly and get scattered or dampened by their surroundings. During a smart office installation the Vektor Digital team performed in 2014, we learned this lesson well. The project required us to deploy beacons throughout an office with the goal of presenting a welcome lock screen notification to users when they reached the office entrance, and then context specific images and videos when entering different rooms and spaces.

We started by installing beacons under counters, in rafters and over doorways in the key spaces we were targeting. We quickly found out, however, that some beacon signals would read strong, while others would read weak, despite being the same distance from our smartphones. This was due to the fact that beacon antennas project bluetooth signals in non-uniform manner. The result is the same beacon would read as 10 to 20-ft away when it was turned one way, and then read 20 to 40-ft away when rotated 180 degrees. Similarly, some rooms contained office furniture and were relatively empty. But others had open ventilation systems made of metal. In these open ventilation rooms, our beacon signals would scatter and bounce, making a beacon seem stronger than it's next-door counterparts.

To provide a consistent experience for this office's app users, we spent a considerable amount of time on site, physically adjusting beacons, fine-tuning our software's rate of beacon scanning, and tweaking the thresholds in which our software determined if a beacons was close, near or far. As an app owner, your team will experience unique challenges, no matter the space you deploy beacons. Ensure that your software adjusts for this space, and ensure that your operations team is prepared to make adjustments to beacon locations.

### 11\. Measure

Analytics let your team measure if features are providing the ROI your team set before launch. Smart app owners can do this by measuring the following:

  * **Beacons scanned** - the serial numbers of the beacons that your users detected, in the background or foreground during use. These metrics provide feedback on the path your users take through your spaces, if your beacon placement is appropriate and which beacons are getting the most attention by users.
  * **Dwell time** - the amount of time a user spent within a defined threshold of a beacon. If dwell times are a few seconds or lower, it's a sign that users are moving through your beacon-equipped zones too quickly to engage with your content.
  * **Content viewed and duration**- the screens or content consumed by a user during their beacon visit. This can help measure if your users are engaging with the content your app is providing and how long they are engaging with this content.
  * **Notification opens vs. sent** - In many apps, a local notification is sent to the user's smartphone when entering or exiting an area equipped with beacons. It's important to measure both when a user was sent a notification, and when the user actually opened the app upon receiving the notification.

### Conclusion

Crafting and launching successful beacon apps isn't easy. It requires the right mix of value proposition, implementation, and attention to detail. The world of beacons is fast changing - leave a message in the comments if you have feedback or updates you'd like to see made to this article.
