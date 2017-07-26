# Live Stream to YouTube With a Raspberry Pi

_Captured: 2017-05-25 at 13:49 from [www.makeuseof.com](http://www.makeuseof.com/tag/live-stream-youtube-raspberry-pi/)_

By adding a camera module (or USB webcam) to your Raspberry Pi, you essentially get a portable, lightweight and easy-to-hold-or-mount internet-connected camera.

So, it makes sense that you might want to stream footage with it. But how do you get started with this? Which Pi model should you use? Is one camera module solution better than another? And how the heck do you get the footage onto YouTube?

As with most things Raspberry Pi, it's remarkably straightforward.

## What You Will Need

To live stream whatever is in front of your Raspberry Pi to YouTube, you'll need the following:

  * A Raspberry Pi (Model B+ or later).
  * Raspberry Pi Camera Module (original or NoIR revision, either is fine) or a USB webcam. These instructions assume a Raspberry Pi Camera Module is in use.
  * Wireless dongle if using pre-Raspberry Pi 3 model.
  * Portable battery supply (optional).
![muo-diy-picamera-device](http://cdn.makeuseof.com/wp-content/uploads/2015/08/muo-diy-picamera-device.jpg?x73577)

For the operating system, the standard [Raspbian Jessie](http://www.makeuseof.com/tag/5-ways-new-raspbian-jessie-makes-raspberry-pi-even-easier-use/) will be fine, preferably with the [Pixel desktop](http://www.makeuseof.com/tag/upgrade-raspberry-pis-raspbian-os-pixel-desktop-environment/). But you might prefer Ubuntu or Arch Linux, or any of the [other Raspberry Pi distros](http://www.makeuseof.com/tag/not-just-raspbian-10-linux-distros-pi-can-run/) currently available.

You'll also need a YouTube channel, for streaming your footage to. This isn't as difficult to set up as you might think, and unlike other solutions, it's free.

## Set Up Your YouTube Channel

You probably already have a YouTube account. If you use Google Mail, there is an account ready for you to activate. We need a special URL from here that we can use to direct the footage captured by the Raspberry Pi's camera to YouTube, thus streaming it.

This is called an **RMTP address** and is basically a specific media URL.

![youtube streaming live](http://cdn.makeuseof.com/wp-content/uploads/2016/12/muo-diy-rapsberrypi-youtube-streaming-live.png?x73577)

To find this, head to YouTube, sign in, and look for the **Upload** button. This is what you would normally use in YouTube to add a video. On this occasion, however, we're going to ignore this and click **Get started** button under Live Streaming.

![youtube streaming key](http://cdn.makeuseof.com/wp-content/uploads/2016/12/muo-diy-rapsberrypi-youtube-streaming-key.png?x73577)

In the subsequent screen, fill in the details you want for the live feed. This will be information about the subject of the feed, and a title, which you should add under **Basic Info**. In the next tab, **Stream Options**, look for Encoder Setup and copy the **Server URL** and **Stream name/key** (you'll need to click **Reveal** to see this). Note that the Stream key needs to be kept private -- anyone with this information can stream to your YouTube channel!

## Prepare the Raspberry Pi for Live YouTube Streaming

Now, it's time to set up your Raspberry Pi for streaming.

Begin by running an upgrade. This ensures you're running the most recent version of Raspbian, with all of the necessary system and software updates, including raspivid.

![diy picamera enable](http://cdn.makeuseof.com/wp-content/uploads/2015/08/muo-diy-picamera-enable.png?x73577)

Next, connect your camera and boot up. If you don't have a monitor attached, use VNC to establish a [remote desktop connection to the Pi](http://www.makeuseof.com/tag/run-remote-desktop-raspberry-pi-vnc/), and test the camera. Our previous guide to [setting up the Raspberry Pi Camera Module](http://www.makeuseof.com/tag/raspberry-pi-camera-module/) should help here. If you don't have time for that, open a terminal window and enter:
    
    
    sudo raspi-config

Use the arrow keys to select **Enable Camera**, tap **Enter,** then select **Yes.** You'll be prompted to reboot. When your Pi restarts, enter:
    
    
    raspistill –o image.jpg

You'll find the resulting snap in the Home directory. Once you know that your camera is working with your Raspberry Pi, you can proceed.

## Set Up Streaming With avconv

To stream the feed from your Pi's camera, you'll need to install **avconv**. This is part of the **libav-tools** package, so you can should be able to install it with:
    
    
    sudo apt-get install libav-tools

Unfortunately, it doesn't always work that way.

With **avconv** installed, you're ready to create the feed for YouTube. You'll need the stream name/key that you noted down earlier for this.

(If you're doing this via SSH, it will be easier to simply copy the stream name/key from the YouTube browser window into your remote Raspberry Pi command line.)

The command, however, is long. Really long.
    
    
    raspivid -o - -t 0 -vf -hf -fps 30 -b 6000000 | avconv -re -ar 44100 -ac 2 -acodec pcm_s16le -f s16le -ac 2 -i /dev/zero -f h264 -i - -vcodec copy -acodec aac -ab 128k -g 50 -strict experimental -f flv rtmp://a.rtmp.youtube.com/live2/[your-secret-key-here]

As you can see, it has a lot of elements to it. Now, if you want to go ahead and just run it, then copy the code, paste it into your terminal window, and hit enter. Remember to change **[your-secret-key-here]** for the Stream key you made a note of earlier.

If everything has worked as intended, you'll end up with something like this:

![youtube streaming output](http://cdn.makeuseof.com/wp-content/uploads/2016/12/muo-diy-rapsberrypi-youtube-streaming-output.png?x73577)

> _When this happens, switch back to the YouTube browser tab. You'll see something like this:_

![youtube streaming health](http://cdn.makeuseof.com/wp-content/uploads/2016/12/muo-diy-rapsberrypi-youtube-streaming-health.png?x73577)

> _And a few moments later, the footage will start streaming:_

![youtube streaming stream](http://cdn.makeuseof.com/wp-content/uploads/2016/12/muo-diy-rapsberrypi-youtube-streaming-stream.png?x73577)

### Problems? Try ffmpeg

In some cases, **avconv** won't push your Pi's stream to YouTube. If this happens to you, then you should consider using **ffmpeg**, the precursor to **avconv**, which was available for older versions of Raspbian.

Although deprecated from Debian, **ffmpeg** can be downloaded and compiled manually, [using these instructions](https://www.assetbank.co.uk/support/documentation/install/ffmpeg-debian-squeeze/ffmpeg-debian-jessie/). Be aware that this can take a while, so make sure you've got hot drinks and snacks to hand. Or a book to read.

## What the Stream Command Means

That long command above can be quite confusing to the untrained eye, but features a collection of separate parameters. Let's look at the most important.

**-fps** -- This is the frames per second rate. For the best results it should be over 24, which is the speed movies traditionally ran at in order to create the illusion of movement. If performance is an issue, however, you may prefer to reduce this to improve steaming.

**-w -h** -- These can be used to specify width and height. If you omit them, raspivid will use the full 1920 x 1080 high definition resolution (1080p).

**-b** -- Output bitrate limit. YouTube's recommendation is 400-600kbps. A lower figure will reduce upload bandwidth, in exchange for a lower quality video.

**-acodec** -- This one is particularly important for streaming to YouTube. The service doesn't allow video without an audio track (or audio without a video track) so we use this to create a fake audio track for the stream. As the Raspberry Pi doesn't ship with a built in mic, and the best audio results are gained from adding a sound card HAT, this is the easy solution.

**-f** -- This is the output format, in this case flv, the preferred format for YouTube live streams.

## You're Streaming: What Next?

With the Pi streaming video from the camera, everything should be working fine. But there is a chance that things can overheat, which will slow down the stream. This is particularly likely on older devices, prior to the Raspberry Pi 2, especially if you've set a high resolution for streaming.

As such, you're likely to get better results from the Raspberry Pi 2, and almost perfect results with the [Raspberry Pi 3](http://www.makeuseof.com/tag/raspberry-pi-3-faster-better-wi-fi-bluetooth/).

**Have you tried streaming live on YouTube with your Raspberry Pi? Perhaps you have some other camera-based projects for your Pi you'd like to share? Let us know below.**
