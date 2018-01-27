# Your Computer’s Hard Drive Can Be Used to Listen to What You’re Saying

_Captured: 2017-10-17 at 13:41 from [blog.hackster.io](https://blog.hackster.io/your-computers-hard-drive-can-be-used-to-listen-to-what-you-re-saying-808b83f19f80)_

We talk a lot about [security vulnerabilities](https://www.hackster.io/security) around here, and for good reason: it's an important part of our modern technological world. It seems like every day we come across some new and ingenious way that hackers have found to breach your privacy. These revelations come to us in one of two ways: when white hat hackers demonstrate them so the holes can be fixed, or when black hat hackers use them for unethical purposes. The hope, for most of us, is that the white hats find these new techniques before the black hats.

![](https://cdn-images-1.medium.com/freeze/max/60/1*0ZqqpUgNgBPEXqdotijaVQ.png?q=20)![](https://cdn-images-1.medium.com/max/1600/1*0ZqqpUgNgBPEXqdotijaVQ.png)

> _Turning hard disk drives into accidental microphones. (📷: Alfredo Ortega)_

As our devices become increasingly more connected, and gain an ever-growing number of sensors (like cameras and microphones), one of the major concerns the average person has is regarding spying. This is why many people choose to cover their laptops' cameras. But, [as Alfredo Ortega points out](https://github.com/ortegaalfredo/kscope/blob/master/doc/HDD-microphones.pdf), even something as innocuous as your computer's hard disk can be used to record sound.

The technique works by measuring the vibrations of the hard drive's magnetic disks. Ortega says (translated) "It turns out that when the physical platters of the hard drive vibrate, the hardware must wait until the vibration stops reading information from it. We can measure this delay accurately even though users are not privileged. What can cause the hard drive vibration? Movement and sound. Therefore, we can measure movement and sound."

As he shows in a teaser video for a [talk he's giving on the subject](https://www.ekoparty.org/charla.php?id=790), those vibrations can be translated into [discernable audio](https://www.hackster.io/voice). What's even more worrying is that the vibration-detection in most operating systems is available to all users regardless of privileges, because it's a base-level operation. So, a black hat hacker could potentially use any computer's guest account (or any account they can access) to install software to record audio in the room.
