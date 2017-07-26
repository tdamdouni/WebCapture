# Unlimited Backgrounding on iOS

_Captured: 2015-10-20 at 00:44 from [yifan.lu](http://yifan.lu/2013/12/17/unlimited-backgrounding-on-ios/)_

Since iOS4, developers have the ability to perform background tasks with some limitations. Background tasks must fit one of the five different categories for background supported apps. Music and streaming apps can be backgrounded as long as they play music. Newsstand apps can wake once a day to download updates. Location aware apps can wake up once in a while to update their position. VOIP apps can have one socket (I found out the hard way that the one socket does not include listener sockets) connected in the background. General apps can request up to 10 minutes to finish some task. While this is enough for most backgrounding purposes, sometimes we need backgrounding for more advanced tasks. Specifically, I wanted to write a [HTTP proxy server](https://github.com/yifanlu/Polipo-iOS) that runs on the device (in the future, this proxy server will work as an ad-blocking proxy) in the background. I will show you the steps of making this work. Please note that Apple will certainly reject any app that abuses their backgrounding policy so doing so would only be useful for personal and enterprise uses.

So how are we going to abuse the iOS background policy? We are going to declare our app as a background music player but not play any music. Sounds simple right? Well, in hindsight it is, but there's some subtle tricks I had to discover to get it all working. Let's go through this step by step…

First make sure your app has, in "Capabilities", Background Modes turned on and "Audio and AirPlay" enabled. Also make sure you're linking with "AVFoundation.framework."

In our demo app, we will have one button that says "Enable Background" that, when tapped, will keep our app running even if the user switches apps. We also have a NSThread will will keep logging to show that it is running even in the background.

First create your silent music file. I had success with a one-second MP3 file of silence. The audio file does not have to be silent, but why scare the user with a random audio file? Add this to the "Supporting Files" category.

Add a property to the View Controller that will hold the silent audio player.

> @property (nonatomic, strong) AVPlayer *player;

Now, you should set up the audio session. I chose to do this in viewDidLoad of my view controller of the single view in the demo app.

> NSError *sessionError = nil;  
[[AVAudioSession sharedInstance] setCategory:AVAudioSessionCategoryPlayback withOptions:AVAudioSessionCategoryOptionMixWithOthers error:&sessionError];

The category AVAudioSessionCategoryPlayback is one of the few categories that allow for backgrounding. The option AVAudioSessionCategoryOptionMixWithOthers will make sure your silent audio won't stop any currently playing background audio and also make sure that when the user plays music in the future, it won't kick off your background task. A good developer will also check the return values and sessionError, but I'm not a good developer.

> AVPlayerItem *item = [AVPlayerItem playerItemWithURL:[[NSBundle mainBundle] URLForResource:@"silence" withExtension:@"mp3″]];  
[self setPlayer:[[AVPlayer alloc] initWithPlayerItem:item]];

Now create the actual player item for your silent audio file. If you are embedding your audio file a different way, feel free to adapt this to do so. No trickery here.

> [[self player] setActionAtItemEnd:AVPlayerActionAtItemEndNone];

Here's the trick; this makes sure that the audio player is kept active after playing your sound file. The alternative is to keep looping a silent track, but why waste more CPU cycles (and battery)?

Now, whenever you wish to keep the app in the background, just call

> [[self player] play];

And your app will keep working even after the user switches the app. In my case, the HTTP proxy server was still working after I left the iPad in sleep mode overnight (with the charger connected of course).

Here is the sample code: [Limitless Background (1466)](http://yifan.lu/download/49)
