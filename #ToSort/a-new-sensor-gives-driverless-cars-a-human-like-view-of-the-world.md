# A New Sensor Gives Driverless Cars a Human-Like View of the World

_Captured: 2017-12-22 at 05:34 from [www.technologyreview.com](https://www.technologyreview.com/s/609718/a-new-sensor-gives-driverless-cars-a-human-like-view-of-the-world/?utm_content=64796588&utm_medium=social&utm_source=twitter)_

![](https://cdn.technologyreview.com/i/images/aeye2.png?sw=1180&cx=0&cy=32&cw=1176&ch=893)

When you stare through the windshield of your car, you don't see the world the same way a dash cam does. What you see is being warped by the inner workings of your brain, prioritizing detail at the center of the scene while keeping attention on the peripheries to spot danger. Luis Dussan thinks that autonomous cars should have that ability, too.

His startup, AEye, has built a new kind of hybrid sensor that seeks to make that possible. The device contains a solid-state lidar, a low-light camera, and chips to run embedded artificial-intelligence algorithms that can reprogram on the fly how the hardware is being used. That allows the system to prioritize where it's looking in order to give vehicles a more refined view of the world.

Dussan, AEye's founder and CEO, has worked in electronics and optics labs at Lockheed Martin, Northrop Grumman, and NASA's Jet Propulsion Laboratory; he put a PhD in computational physics on hold to launch the startup. He initially planned to build AI to help vehicles drive themselves, but he soon found that sensors on the market couldn't provide the data he wanted to use. "We realized we had to build our own hardware," he explains. "So we did."

Most autonomous cars use lidar sensors, which bounce laser beams off nearby objects, to create accurate 3-D maps of their surroundings. The best versions that are commercially available, made by market leader Velodyne, are mechanical, rapidly sweeping as many as 128 stacked laser beams in a full 360 degrees around a vehicle.

But even though they're good, there are a couple of problems with those mechanical devices. First, they're expensive (see "[Lidar Just Got Way Better--But It's Still Too Expensive for Your Car](https://www.technologyreview.com/s/609526/lidar-just-got-way-better-but-its-still-too-expensive-for-your-car/)"). Second, they don't offer much flexibility, because the lasers point out at predetermined angles. That means a car might capture a very detailed view of the sky as it crests a hill, say, or look too far off into the distance during low-speed city driving--and there's no way to change it.

![](https://cdn.technologyreview.com/i/images/aeye1.png?sw=1080&cx=0&cy=0&cw=1798&ch=953)

> _ AEye _

The leading alternative, solid-state lidar, uses electronics to quickly steer a laser beam back and forth to achieve the same effect as mechanical devices. Many companies have seized on the technology because they can be made cheaply. But the resulting sensors, which are on offer for as little as $100, scan a regular, unvarying rectangular grid and don't offer the standard of data required for driving at highway speeds (see "[Low-Quality Lidar Will Keep Self-Driving Cars in the Slow Lane](https://www.technologyreview.com/s/608348/low-quality-lidar-will-keep-self-driving-cars-in-the-slow-lane/)").

AEye wants to use solid-state devices a little differently, programming them to spit out laser beams in focused areas instead of a regular grid. The firm isn't revealing detailed specifications on how accurately it can steer the beam yet, but it does say it should be able to see as far as 300 meters with an angular resolution as small as 0.1 degrees. That's as good as market-leading mechanical devices.

AEye's setup doesn't scan a whole scene in such high levels of detail all the time, though: it will scan certain areas at lower resolution, and other areas at higher resolution, depending on the priority of the car's control software.

Still, the fact that it can be reprogrammed at will makes that a useful feature. "You can trade resolution, scene revisit rate, and range at any point in time," Dussan says. "The same sensor can adapt." On the freeway its view could be focused primarily on the lane ahead, like a human eye, gathering fewer data points in the periphery of the image. On city streets, it could cover the entire field of view equally, but randomly shift where the points are acquired to minimize the chances of missing an obstacle.

The device can also use data from its camera in some neat ways. First, it can add color to raw lidar images. That's a bit different from the way most autonomous cars process lidar, sending it to a central computer to be fused with data from other sensors. Such rapid processing is useful for quickly spotting things where color is important--like brake lights.

![](https://cdn.technologyreview.com/i/images/aeye2.png?sw=1080&cx=0&cy=0&cw=1794&ch=942)

> _ AEye _

The key innovation, though, is how the camera can be used to direct what the lidar focuses on. With high-speed image recognition algorithms running on its chips, says Dussan, the lidar can steer its gaze to pay special attention to cars, pedestrians, or whatever else the onboard AI is told to consider important.

Ingmar Posner, an associate professor of information engineering at the University of Oxford and founder of the university's [autonomous-driving spinoff, Oxbotica](https://www.technologyreview.com/s/601910/oxboticas-new-autonomous-vehicle-software-learns-as-it-goes/), says that kind of adaptive imaging "is good for higher-level interpretation of the world." He suggests, though, that autonomous-car firms would probably not choose to use this kind of imaging by itself. Instead, they may choose to use a suite of regular sensors to complement a device like AEye's for safety reasons.

[Manage your newsletter preferences](https://www.technologyreview.com/newsletters/preferences/)

Either way, there's one point that there is no getting around: AEye's device only has a 70° field of view, which means that a car would need five or six of the sensors dotted around it for a full 360 degrees. And that raises a killer question: how much will it cost? Dussan won't commit to a number, but he makes it clear that this is supposed to be a high-end option--not competing with hundred-dollar solid state devices, but challenging high-resolution devices like those made by Velodyne. For a full set of sensors around the car, he says, "if you compare true apples-to-apples, we're going to be the lowest-cost system around."

Some people appear to be convinced by the idea already. AEye says it's currently working with "one of the largest vehicle manufacturer OEMs on the planet" to test the sensors in robotic taxis.
