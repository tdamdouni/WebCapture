# Infrared Bird Box - Part 2

_Captured: 2017-05-04 at 20:07 from [www.raspberrypi.org](https://www.raspberrypi.org/learning/infrared-bird-box/worksheet2/)_

In this project, you will use a Raspberry Pi and a Pi NoIR camera to allow you to observe nesting birds without disturbing them. This advanced worksheet covers how to stream the video you produce to the internet.

## YouTube Setup

  1. Go to [YouTube](https://www.youtube.com/), and sign in.
  2. On the left-hand side of the screen you should see a menu with the **My Channel** option available:

![channel](https://www.raspberrypi.org/learning/infrared-bird-box/images/channel.png)

  3. In the middle of the screen you should see the **Video Manager** option:

![video manager](https://www.raspberrypi.org/learning/infrared-bird-box/images/video-manager.png)

  4. In the menu on the left you should see a **LIVE STREAMING** option, and within that a **Stream now BETA** option:

![live stream](https://www.raspberrypi.org/learning/infrared-bird-box/images/live-stream.png)

  5. Scroll down to the bottom of the page, and you should see the **ENCODER SETUP** option:

![encoder setup](https://www.raspberrypi.org/learning/infrared-bird-box/images/encoder-setup.png)

  6. Within the the **ENCODER SETUP** there is a **Server URL** and a **Stream name/key**. The key will appear to be just a line of asterisks, until you click on the **Reveal** button. You need to keep the key secret, though, so make sure you don't share it online.

## Compile FFmpeg

Firstly, you need to install some software called [FFmpeg](http://www.ffmpeg.org/), which will continually stream the video data from the Camera Module to the web. Instructions are below.

**NOTE**: This step is going to take about two hours, since you have to [compile](http://en.wikipedia.org/wiki/Compiler) the program from its source code. The Raspbian FFmpeg package that can be installed using `apt-get` doesn't have the required `h264` video encoder support. You can just set the process going and do something else during this time; you'll also only need to do it once.

The part that takes two hours is the `make` command at the end of the list below. The `./configure` part takes a while too; just be patient. Enter the following commands to download, compile, and install FFmpeg:
    
    
    cd /usr/src
    sudo mkdir ffmpeg
    sudo chown pi:users ffmpeg
    git clone git://source.ffmpeg.org/ffmpeg.git ffmpeg
    cd ffmpeg
    ./configure
    make && sudo make install

You can now do something else until you see the command prompt reappear.

## Streaming with FFmpeg

Open a terminal window and then, with this single command, you can start streaming to YouTube. You'll need to remove the `<key goes here>` part of the command and replace it with your key copied from YouTube:
    
    
    raspivid -o - -t 0 -w 1280 -h 720 -fps 25 -b 4000000 -g 50 | ffmpeg -re -ar 44100 -ac 2 -acodec pcm_s16le -f s16le -ac 2 -i /dev/zero -f h264 -i - -vcodec copy -acodec aac -ab 128k -g 50 -strict experimental -f flv rtmp://a.rtmp.youtube.com/live2/<key goes here>

It's never a good idea to copy and paste commands from the internet into a terminal window without understanding what you're typing, so let's break it down a little. The first half of the command has the following options:

  * `raspivid -o -` tells the Raspberry Pi to start capturing video.
  * `-t 0` is an option to keep recording forever.
  * `-w 1280 -h 720` sets the video's width and height in pixels.
  * `-fps 25` set the frame rate to 25 frames per second.
  * `-b 4000000` sets the bit rate (the speed of data transfer) to 4Mbps.
  * `-g 50` sets the key frame rate. So a complete picture will be recorded every 50 frames, while the ones in between will be compressed.

The second half of the command is for streaming. The `|` symbol takes the data from `raspivid` and passes it to `ffmpeg`.

  * The `-re` flag tells FFmpeg to use the same frame rate as captured by the camera.
  * `-ar 44100 -ac 2 -acodec pcm_s16le -f s16le -ac 2 -i /dev/zero`, `-acodec aac -ab 128k` and `-strict experimental` creates a silent audio stream, as YouTube needs audio to accompany its videos.
  * `-f h264` and `-f flv` are the codecs FFmpeg is receiving from the PiCamera and the output it's sending to YouTube.
  * The very last option is just your personal streaming details for YouTube.

## Viewing your stream

Once you have run the command, you can hop back over to YouTube and, after a minute or two, you should see your video being streamed for anyone to watch.

Remember: be careful about what content you place on the internet, especially in a public channel.

## Remote control

The last thing you should consider is being able to access the Raspberry Pi remotely from another computer, without having to have a keyboard, mouse, and monitor connected to it. Having these attached would be pretty inconvenient if the Pi is located somewhere outside, like up a tree.

The easiest way to remotely access the Pi is to use VNC.

## VNC setup on the Raspberry Pi

  1. First, you'll need to get the RealVNC server for your Raspberry Pi. You can download the **deb** package [here](https://github.com/RealVNC/raspi-preview/releases/download/5.3.1.18206/VNC-Server-5.3.1-raspi-alpha1.deb).

    * To install the package, open a terminal (**Ctrl + Alt + T**) and type the following command in the directory the deb package was downloaded to:
    
        sudo dpkg -i VNC-Server-5.3.1-raspi-alpha1.deb

  2. You'll need a license key for the server, but don't worry: these are completely free. On the [RealVNC website](https://www.realvnc.com/purchase/activate/), you can fill in your details and obtain your free license key.
  3. Next, you need to apply the license key. This is again done in a terminal window with the following command:
    
        sudo vnclicense -add <your-license-key-here->

  4. It's a good idea to find the IP address of your Pi. Be warned, though: this can change when it disconnects and reconnects to your network, although most networks will let the Raspberry Pi retain the same IP address for quite some time. To find your IP address, you can hover your mouse over the network icon in the top-left of the screen, or alternatively use the following command in the terminal:
    
        hostname -I

  5. The next command will start your VNC server each time the Raspberry Pi is started. Again, it needs to be typed into a terminal window:
    
        sudo systemctl enable vncserver-x11-serviced.service

  6. On your Windows, MacOS, or Linux computer, you can now take control of your Raspberry Pi. You'll need a VNC viewer, and 

## What next?

  * Wait for some birds to move in
  * Tell the world about your bird box
  * Post the Ustream channel URL on social media or email it to your friends and family
