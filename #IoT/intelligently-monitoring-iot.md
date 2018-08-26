# Intelligently Monitoring IoT

_Captured: 2018-07-03 at 23:16 from [dzone.com](https://dzone.com/articles/intelligently-monitoring-iot)_

![](https://www.nastel.com/wp-content/uploads/intelligent-monitoring.jpg)

I was recently talking with a company that manages environmental and AV systems for large buildings. They use the most advanced technology, which, in this case, is IoT.

They setup control systems to control light, HVAC, window shades, door locks, AV displays, speakers, and more. In a large building, this can be tens of thousands of actuators and sensors, controlled locally by wall mounted control panels, as well as centrally for each apartment, office, floor, and centrally by maintenance.

Each user has customized settings for their environment and some globally mandated settings. Everything can be managed through macros to allow for multiple things to happen during an event. For example, if the sun is shining, light and heat sensors can decide which blinds, fans, and A/C units come into play. While at night, when there is no one around (sensors can see this), different configurations can come into play.

Modern luxury buildings rely on this level of configuration and intelligence. And, it helps keep the costs down, the rents up, and everything secure.

The companies that manage all this technology will be monitoring everything continually. They will do this offsite, managing many hundreds of buildings from a central global location.

But, sometimes things do not go as planned, and when things fail to work within agreed levels they need to be able to understand the issue quickly and remediate any issue. Ideally, they should be able to do as much of this as remotely as possible.

One problem that this particular monitoring company has had recently was a real head scratcher, one that was proving very expensive to resolve. For some reason, several dozen devices would go off-line at the same time, and the only thing they eventually could do was send out an engineer. The engineer would end up replacing all the failing devices and the hub that controlled them, resolving the issue. Needless to say, this was a really time consuming and expensive fix.

After this had happened several times at several buildings, they were able to identify the issue. It turns out that most of the industrial class of IOT devices do an automated reboot every 28 day, and, as part of the reboot process, they would check the local hub for any firmware updates.

These firmware updates were loaded over the internet to an SD card on the hubs. But, someone had chosen to save a few dollars by using lower quality SD cards than were normally provided. The MTBF of these cards was significantly lower than the top end ones that were specified. And, every month, a couple would randomly fail. When the IOT devices would reboot and check for any updated firmware, they would receive an error from the target device, and so they would reboot and try again.

Since they were in the process of rebooting, they didn't log an error event. No one knew what was happening. The cumulative effect of these outages ran into many millions of dollars of additional expense.

Luckily, a smart troubleshooter decided to recreate a test environment using a series of defective replaced devices and was able to find the root cause of this particular series of events.

All the inferior SD cards were replaced and this particular event wasn't seen again.

But, it brought up the more strategic business need for a monitoring solution that would allow all of the activities prior to a failure to be investigated.

This is exactly the kind of scenario that Nastel AutoPilot Insight can help with. Nastel AutoPilot Insight allows you to track complete transactions and drill into the detail in real time. Seeing what happened just before a failure is one of the easier scenarios for it to solve.

With millions of events taking place across thousands of applications, platforms, infrastructures, middleware, and IOT devices, every complex business application can make dramatic performance and availability improvements using Nastel Autopilot Insight.

### Like This Article? Read More From DZone
