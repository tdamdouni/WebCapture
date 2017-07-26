# Camera.app Pauses Audio Playback

_Captured: 2016-03-22 at 19:31 from [oleb.net](http://oleb.net/blog/2016/03/ios-camera-app-pauses-audio-playback/)_

I tweeted this yesterday:

> Launching the camera app still halts music playback on iOS 9.3. I'm starting to think Apple doesn't see this as a bug (but why?).

The replies I got varied wildly between [agreement that this is extremely annoying](https://twitter.com/mjtsai/status/712120360129454081) to various explanation attempts or confusion because it doesn't happen all the time on every device. So let's try to take this apart.

**It only happens on the iPhone 6s (Plus).** On older devices without Live Photo support, audio playback pauses only when you switch to video recording, not sooner. This leads me to believe the behavior has something to do with Live Photos, although I can't be sure. Presumably, the new iPhone SE and 9.7-inch iPad Pro will also be affected.

**The mode the camera app is in doesn't matter.** Audio playback is paused not only in video recording mode, but also in all photo taking modes - regardless whether Live Photo recording is active or not.

**The camera app can't record audio while music is playing.** It doesn't have to be this way, however. The iPhone is capable of recording and playing back audio at the same time, and the [audio session API](https://developer.apple.com/library/ios/documentation/Audio/Conceptual/AudioSessionProgrammingGuide/AudioSessionCategoriesandModes/AudioSessionCategoriesandModes.html#//apple_ref/doc/uid/TP40007875-CH10-SW1) supports a mode where the recording app does not interrupt the audio coming from other apps.

**Taking photos or videos while listening to music is not [an edge case](https://twitter.com/zbowling/status/712175714322100225).** It's unclear to me whether the current behavior is a deliberate choice by the engineers who wrote the camera app or if nobody really thought about this, but I think it's a bad default.

I can imagine many situations where I would want music playback to continue while I'm recording a video or taking a photo (Live Photo or not). I almost always listen to podcasts or music when I walk around the city, and this is also a great opportunity for taking pictures. And it's not even limited to using headphones. Say you're at a party where people are taking turns at playing songs on the room's stereo wirelessly from their smartphones. You wouldn't want your iPhone to stop music playback just because you want to [take a video of your dancing friends](https://twitter.com/PossiblyAlan/status/712067084776243200).

**It's not because the volume buttons [double as the shutter button](https://twitter.com/Bonney/status/712226497377869825).** This feature has existed for years and it didn't stop the camera app from behaving better before the iPhone 6s came out. It just means you can't adjust the volume while the camera app is open, which is fine.

**The camera app could definitely behave better when Live Photo recording is inactive.** When I tried to figure out why the camera app behaved they way it does, my latest guess was that it tries to be overly smart, buffering video and audio all the time even when the Live Photo mode is not active. If it did, you could activate the Live Photo mode and instantly hit the shutter button and still get a "complete" Live Photo that included the moments before the mode was even activated. But it turns out the camera app doesn't do that, so it's irrelevant.

**Apple indeed sees this as a bug.** Many thanks to Elliott Harris, who works on the camera team at Apple and replied to me on Twitter:

Fingers crossed for iOS 10.
