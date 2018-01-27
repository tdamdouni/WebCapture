# Dartmouth to Display Three New Wearable Technologies at ACM UIST 2017

_Captured: 2017-10-25 at 22:43 from [blog.hackster.io](https://blog.hackster.io/dartmouth-to-display-three-new-wearable-technologies-at-acm-uist-2017-6e79ae6dc6f0)_

The Association of Computing Machinery's annual User Interface Software and Technology (UIST) symposium is upon us, and we're sure to see a lot of exciting new tech on display. Among those we're looking forward to are [three new wearable tech prototypes](https://www.eurekalert.org/pub_releases/2017-10/dc-dtd101917.php) being demonstrated by researchers from Dartmouth College. All three come from the school's human-computer interface lab, and all are designed to improve the way we interact with our wearables.

#### Pyro: Thermal Thumb-Tip Gesture Recognition

A common hurdle for UI (user interface) and UX (user experience) [design for wearables](https://www.hackster.io/wearables) is how to provide input to the device. Like any other input method, it would need to be intuitive, accurate, and efficient. But, wearables present a unique challenge when it comes to subtlety--a requirement not found in many other devices.

![](https://cdn-images-1.medium.com/freeze/max/60/1*XqromCRRZJ_pbNKNdL5a8Q.png?q=20)![](https://cdn-images-1.medium.com/max/1600/1*XqromCRRZJ_pbNKNdL5a8Q.png)

> _A PIR sensor detects fine finger gestures accurately._

Unlike a keyboard, a wearable input device needs to be unobtrusive (both to the user and to the people around the user). The entire purpose of a wearable is to provide a quick and effortless interaction. A traditional [analog wristwatch](https://www.hackster.io/clocks) accomplishes this by always displaying the time, and the wearer simply needs to give the watch a quick glance to know that time.

> _Up to six gestures can be repeatably understood._

[Pyro seeks to provide a similar experience](http://www.cs.dartmouth.edu/~xingdong/papers/Pyro.pdf), but for input. It works by using a passive infrared sensor to measure the heat from your fingers. That heat signature changes in a discernible way as you move your fingers to make gestures. All the user needs to do is move their index fingertip against their thumb in a particular pattern to interact with a device they don't even need to be looking at.

As the researchers point out in their paper on Pyro, the device can sense up to six unique gestures (like a square or triangle shape). During testing, ten participants were shown to have an accuracy of 93.9% for these gestures. While six gestures may not seem like a lot, consider how few buttons an everyday digital wristwatch has, and how much can be done with just those.

#### Frictio: Passive Smart Ring Force Feedback

As big a challenge as subtle input is, unobtrusive output is even more illusive. Most wearable devices rely on either [LCD or OLED displays](https://www.hackster.io/displays), or just simple LEDs. But, once again, the key to good wearable design is that it not be obvious when input or output is happening.

A glowing display is pretty obvious, particularly when it stands out in a setting like a movie theater. Even outside of that specific scenario, social conventions in many cases dictate that it is rude to check your device during something like a business meeting, or when you're on a date. It's imperative that a wearable be able to provide some sort of output that only the wearer notices.

> _Feedback is provided by how hard the ring is to rotate._

[That's where Frictio comes in](http://www.cs.dartmouth.edu/~xingdong/papers/Frictio.pdf). It's a ring that has a rotating outside band that's friction can be dynamically adjusted to provide feedback to the user. It might rotate completely freely when no notifications are present, but then become harder to rotate as more notifications pile up.

> _A gear motor and brakes are used to make the ring more difficult to rotate._

Imagine you're on a date, and you feel your phone ringing in your pocket. It'd be rude to check it, but how do you know it's not important or an emergency? Now imagine the caller could give that call a priority level, and you'd only need to rotate your ring to know how important it is. Frictio achieves this by integrating brakes on a gear motor into the band of the ring.

#### RetroShape: Pixelated Smartwatch Tactile Feedback

Of course, not everything needs spy levels of covert input and output. Sometimes, the goal is just to provide a richer experience. Many people already wear smartwatches that are anything but subtle. For these people, the experience is the key.

> _Objects displayed in pixels on the display are reproduced with taxels on the watch back._

To increase the variety of feedback from a smartwatch, [RetroShape uses a 4x4 grid](http://www.cs.dartmouth.edu/~xingdong/papers/Retroshape.pdf) of 16 moving pins on the back of the watch (against your wrist). These pins, called taxels (tactile pixels), can be set to mirror the pixels on the watch's display. So, something like a ball bouncing on the screen might give the user a corresponding touch on their wrist.

> _Testing with prototypes proves the concept._

This has potential for both providing tactile feedback that complements what's on the screen, and for providing the wearer [with notifications](https://www.hackster.io/notifications) that don't require the screen to turned on. Just like with Frictio, it could give the user a variety of uniquely identifiable notifications that can be felt, instead of being seen or heard.
