# Lessons Learned From Using IoT Devices in the Real World

_Captured: 2017-03-16 at 21:26 from [dzone.com](https://dzone.com/articles/lessons-learned-from-using-iot-devices-in-the-real?edition=283884&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-16)_

As a consultant, I've spent a decent amount of time working on a full stack development project in the realm of IoT. Over the years, our teams have run into a lot of avoidable issues. Here are some lessons I learned from using IoT devices in the industry.

I define IoT as "connecting a device to a larger system with the goal of that device providing information to the system that is then leveraged in some way." This can range from something like a FitBit to a Tesla to a smart fridge -- all of which connect and report information to a cloud or back end, making them "Internet of things" devices.

## Lesson 1: Start Small

Although starting small should be done in all development, I found this to be even more important once devices are involved. As a developer, changing something after the fact no longer means "just a code adjustment" -- it also means changing a device's configuration, or even its embedded system. So how do you start small?

First, get your device connect with a simple mock service. Mocks are easier to control and set up than complete systems.

Second, add security to the service. Once that is done, write tests, error handling, and documentation for the base code. This ensures a few things: Your foundational code is ensured to be solid and properly tested (so you won't need to go back later and change it); security will be in place early, allowing for confidence in trusting the device; and you'll have a framework set up to use the development patterns you've laid out.

With the project I worked on, we did not start small everywhere, like we should have. This led to a lack of testing, error handling, and documentation all around.

In addition, trying to "go too fast" led us to take shortcuts like putting passwords in URLs that devices used to connect to the system. Of course, this all had to be changed later to make the system production-ready and led to more work. And not only more work in the code, but also on the devices themselves. These are examples of things you want to do right -- starting small, from the beginning.

## Lesson 2: Define What You Can

Another major issue I ran into on this project was a lack of clear requirements. Without knowing how a device should respond to a particular situation, it is difficult to build an integrated system. Focus on getting requirements around who holds ownership for what (in this case, "what section of the system" holds ownership).

For example, who is the owner of a device's configuration or who is responsible if a bad message comes through? Also, consider what type of messaging requirements exist (zero loss, in order, no duplicates) and the impact of that on the larger system.

Consider the situation where a user's account balance is at {{the_content}}. What happens if they try to use their card? If it is a debit card, it would get denied, but what if it is something like a train pass? How should the farebox react if it's lost its data connection to the system for a moment? Knowing that up front will help to build a more efficient IoT system. Without defining requirements the system won't know how to react and the development and testing teams won't know what to expect.

## Lesson 3: Check Capabilities

When integrating devices as IoT, it is important to check capabilities of the frameworks being used, as well as capabilities of the devices themselves. How stable of an Internet connection is reasonably expected of the device? What type of storage does it have? What built-in components can be used from the software framework chosen? Answering these questions will help avoid scrambling to fix issues down the line.

One area my project could have dug into deeper was our frameworks. We re-wrote functionality in libraries that our frameworks provided us with from the start. Rather than using the ones built, we duplicated functionality simply because we did not check.

After moving the system into production, we realized our messaging framework (as well as the storage on our devices) was limited. The messaging framework could not handle the message sizes being sent to it, and messages were getting rejected. We had to scramble to figure out a quick solution when this could have been avoided had everyone on the project known about the limitations of the frameworks and devices we'd selected.

## Lesson 4: Trust Your Device

The lesson I find to be most crucial from my experience with IoT is the importance of trusting the device. What happens when the overall system thinks one thing and the device tells it another? Trust the device.

Why bother connecting a device to a system to gather and send information if the system isn't going to trust and use that information? That being said, trusting the device showcases the need for security.

In order to fully trust what a device is sending to the cloud, the communication between the two must be secure. Otherwise, the system cannot know that the information being sent is not garbage -- or worse, compromised.

Consider FitBit. Why bother buying a FitBit if you did not want it to tell you how many steps you took? You buy a FitBit to tell you how active you have been and you trust it by default. This is also how the system should work. Tesla gathers information when the driver runs it in autopilot mode. Then, that information is used by Tesla to make autopilot better. If Tesla did not trust the information being sent to its cloud system, then the autopilot would never improve.
