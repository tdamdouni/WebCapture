# Building a Motion Activated Security Camera with the Raspberry Pi Zero

_Captured: 2017-05-25 at 13:28 from [utbrudd.bouvet.no](https://utbrudd.bouvet.no/2017/01/05/building-a-motion-activated-security-camera-with-the-raspberry-pi-zero/)_

![](https://utbrudd.bouvet.no/wp-content/uploads/2017/01/Screen-Shot-2017-01-05-at-12.05.24.png)

Recently my wife and I suspected that some unwanted guests had been visiting our garden. After a discussion we decided that we needed a motion activated camera that could send us emails once it detected movement. We also wanted the ability to view the live video stream from the camera on demand.

As a fully fledged Raspberry Pi geek I knew right away that I wanted to build my own solution. My wife was not so convinced, and starting listing the dozens of unfinished projects I currently have on my backlog. After promising her that I would see this project through to the bitter end I finally got permission to build a proof of concept

This project required no coding, but quite a bit of configuration. It took about 6-7 hours to complete once I had the parts in place. I spent most of this time wrestling with Linux and this blog will hopefully help anyone attempting a similar project.

To reduce the projects overall complexity I decided that the camera would be mounted _inside_ our living room. This meant that the unit could be powered from the mains, and would be protected from the harsh Norwegian weather.

Below is a full list of the parts I used, along with current prices. I already had some of these parts laying around from previous projects, so my total project cost came up to about $40. If you need to purchase _all_ of the below parts then I would suggest shopping around and looking into Pi Zero starter kits to keep your costs low.

Some notes about some of the specific parts:

  * The Combined WiFi Dongle and USB Hub has two USB ports, allowing me to connect a keyboard and optionally a mouse when setting up the Pi Zero for the first time. The Pi Zero has only one mini USB port available, so this dongle is a worthwhile investment for the most Pi Zero projects.
  * I chose the Raspberry Pi NoIR Camera rather than the standard model as the NoIR can work in low light conditions (you'll add need to add infrared lighting for this camera to perform well at night time). _Edit March 2017: It's important to add that here the **standard** Raspberry Pi Camera provides better picture quality, so you'll need to think about your use case before buying._
  * The ZeroView Camera Mount allowed for easy mounting of the camera and Pi Zero on the inside of my terrace window. It is a mount, not a case, and is not suitable for outside usage.
  * If you struggle to pick up the Raspberry Pi Zero you can always use a Raspberry Pi Model 2 or 3. Both have CSI and USB ports and the Model 3 even has built-in WiFi. If you choose to do this you will want to reevaluate using the ZeroView Camera Mount.

Once I had all the pieces in place it took less than 10 minutes to put my prototype together.

![](https://utbrudd.bouvet.no/wp-content/uploads/2017/01/IMG_6378-e1483637522866-1024x768.jpg)

> _Assembled prototype mounted on the ZeroView with the USB Hub / WiFi dongle attached_

![](https://utbrudd.bouvet.no/wp-content/uploads/2017/01/bollocks-e1483637804853-1024x768.jpg)

> _Rear view of the assembled prototype - missing only the power cable_

After assembling the parts I connected a keyboard and monitor to the USB Hub and switched on the Pi Zero. After booting I installed [Raspian Jessie 4.4 from NOOBS](https://www.raspberrypi.org/downloads/raspbian/).

I configured the Pi Zero as follows, with frequent reboots underway…

From the terminal window run the command:

This will open the Raspberry Pi Configuration tool, from which you should do the following:

  * Enable the Camera.
  * Enable the ssh server (you'll need this later on to connect to Pi Zero in headless mode - i.e. without a monitor and keyboard attached).
  * Enable boot to command line without manual login.

At the terminal prompt type enter:

to change your password from the default. This will prevent tech savvy intruders from connecting to your Pi Zero using ssh and the default login and password.

Next you should [set up a static IP address for your Pi Zero](https://www.modmypi.com/blog/how-to-give-your-raspberry-pi-a-static-ip-address-update). This will make it easier for you to connect to your Pi Zero and to expose it outside of your home network via port forwarding. You can validate that your static IP address is working by [connecting to your Pi Zero via ssh](https://www.raspberrypi.org/documentation/remote-access/ssh/).

Now that you are connecting to the web, you can update Raspian Jessie by running:

If you forget to do this then I can promise that you will have problems later on!

Finally, [Validate that your Raspberry Pi Camera is working](https://www.raspberrypi.org/documentation/usage/camera/raspicam/README.md). If you experience any problems, check the ribbon cable between the Pi Zero and camera - it can easily be dislodged.

Once all the above is done you can disconnect the monitor and keyboard and [connect to the Pi Zero via ssh](https://www.raspberrypi.org/documentation/remote-access/ssh/) to complete the rest of the below steps.

My next step was to choose a software solution for my security camera. My requirements were as follows:

  * Streaming video - so that I could check the video feed at will.
  * Motion detection and the ability to trigger events - so that I could send myself an email for each motion event.
  * Small footprint - due to the size of the SD card (8GB).
  * Low memory overhead - due to the capacity of the Pi Zero.
  * Linux compatible (well duh).
  * Compatible with the Raspberry Pi Camera (MMAL).
  * Configurable - allowing one to tweak the software to get the most out of the hardware.

I choose [Motion](https://motion-project.github.io) as it fulfills the above requirements out of the box with no additional coding. I also considered using the marvellous [OpenCV](http://opencv.org), but felt that I would have spent more time having to tweak it to fulfill my needs.

Motion monitors an incoming camera stream and detects 'motion' by finding the pixel values that have changed from frame to frame. If a threshold (i.e. total pixels changed) is exceeded then Motion triggers a «motion detected» event and optionally creates a snapshot of the video stream. Motion includes an inbuilt webserver offering both a video stream and online configuration on the fly.

Important : before installing Motion you _must_ have updated Raspian Jessie by running the '_sudo apt-get update_' and '_sudo apt-get dist-upgrade_' commands.

I found that installing Motion from the deb release file worked best, probably because the Raspberry Pi Camera requires a specific release:

  1. Install Motion using the gdebi tool (allow it to also install the minimal web server):

Don't bother trying to run Motion yet as it won't work until you've updated the configuration file

You can open the configuration file in edit mode by entering:

[Nano](https://www.nano-editor.org/dist/v2.2/nano.html) is a simple Linux text editor allowing you to edit and search text files. Feel free to use an alternative text editor if you wish.

Below is a list of the parameters that I have tweaked for my setup. [Consult the manual](http://htmlpreview.github.io/?https://github.com/Motion-Project/motion/blob/master/motion_guide.html#Configuration_OptionsDetail) for comprehensive documentation of these and other Motion parameters. Note that the rest of these blog will assume that you have set these values as I have specified.

  1. Uncomment the _mmalcam_name vc.ril.camera _parameter.
  2. Uncomment_ target_dir_ and change it's associated value to '/home/pi/Documents/motion'
  3. Ensure that _ffmpeg_output_movies_ is set to 'off'
  4. Set _stream_localhost_ to 'off'
  5. Set _webcontrol_localhost_ to 'off'
  6. Set _width_ to '640' and _height_ to '480'
  7. Set _locate_motion_mode_ to 'preview'
  8. Set _locate_motion_style_ to 'redbox'
  9. Set _event_gap_ to '10'
  10. Set _output_pictures_ to 'center'
  11. Set _quality_ to '80'
  12. Set _text_changes_ to 'on'

Feel free to play around with the configuration parameters to get a feel for what they do. Be careful to keep a record of the parameters you have changed, in case you mess up and need to start again. Remember that you always have a clean copy of the config file at _/etc/motion/motion.conf_.

Now you are finally ready to run Motion for the first time! Use the following command to run Motion with your configuration file:

While Motion starts up, key an eye out for any error messages that pop up. Problems can occur if your camera isn't correctly connected or if Motion lacks permissions to create image files.

Note that Motion occasionally fails to start up due to previous Motion processes that have failed to shut down properly and are running in the background. If you suspect this, try running the following:

_pid_ refers to the Process ID that you get from the ps aux command.

Once Motion is up and running you'll want to check out the video stream. To do this, you'll need the IP address of the Pi Zero along with the port specified by the _stream_port_ parameter from the Motion config file. Go to the address:

and you should see your video stream in the browser.

You can also access Motion's HTML control panel by changing the port to that specified by the _webcontrol_port _as specified in the Motion config file. Here you can change configuration options on the fly, stop and start Motion and even take snapshots.

Now you can test the motion detection. Movement in front of the camera should result in a still image being saved to the directory you specified for the _target_dir. _If this is working then your motion activated security camera is almost ready for use!

Our next job is to ensure that alert emails get sent from our Pi Zero. As with all things Linux there are many different ways to do this, but I found the following to work without issue.

**Installing a Mail Client**

For this solution you'll need a throwaway Gmail account, as you are going to specify your Gmail password in a configuration file.

Start by installing the tools you'll be using to send emails:

Next, run:

and ensure that file contains the following configuration parameters, making sure that your Gmail account credentials are in place:

1234567 
root=postmastermailhub=smtp.gmail.com:587hostname=raspberrypiAuthUser=yourgmailusername@gmail.comAuthPass=yourgmailpasswordFromLineOverride=YESUseSTARTTLS=YES

Finally send a test email with an attachment from the _target_dir _directory:

If this mail arrives you are good to go to the next step.

**Configuring Motion to send Email**

Here you'll need to make a small change to your Motion configuration file.

You'll be updating the _on_picture_save_ parameter. Uncomment it and change it's value as follows (updating the recipientEmailAddress to the email at which you want to receive alerts):

What happens here is that Motion will call this command each time a new image snapshot is saved to the _target_dir _directory. The %f variable contains the full path to the file.

Save the configuration file, restart Motion and voila! You should now be receiving email notifications each time Motion detects a motion event.

**Ensuring Motion startups up on Reboot**

The easiest way to ensure Motion starts up on reboot is to add it to the [rc.local ](https://www.raspberrypi.org/documentation/linux/usage/rc-local.md)file. This is a simple as adding the following command - assuming that you have specified the configuration file as outlined in this blogpost:

**Removing old files**

Over time there is a danger that your SD card will fill up with old images. Therefore I strongly recommend that you create an [automated cronjob](https://www.raspberrypi.org/documentation/linux/usage/cron.md) to periodically remove all images from the output directory specified in the Motions configuration (the value to the key _target_dir_)_._

So does my camera do the job it was meant to do? Definitely! Here are some examples of the alerts that I have been sent by the camera.

![](https://utbrudd.bouvet.no/wp-content/uploads/2017/01/Screen-Shot-2017-01-05-at-12.11.05.png)

> _Examples of the camera successfully detecting humans in my garden (click to zoom)_

In addition the streaming video works perfectly, making it easy to check the video stream each time I get alerts. By setting port forwarding in my home router I have exposed the live stream to the web and can now view it from my iPhone.

The Camera is meant to run 24/7, and was recently up for 4 weeks without a single problem while myself and my family where on holiday in England. In addition to receiving alerts via email, we used the streaming video on a daily basis to see how the weather was in Oslo (and to check that my brother in law was watering the flowers as agreed).

There are many use cases for this kind of project. It can be used for wildlife watching, pet monitoring or even to tell you when your kids come home from school!

**Minor Issues**

I have two minor problems with the solution, which are both easily resolved:

  1. The Pi NoIR camera works well in low light, but really needs an IR light source to perform at night. I haven't got around to picking one up yet, but they are easy to get hold of online.
  2. The camera is mounted inside the house looking outwards.There is a small gap between the lens of the camera and the glass, which allows for reflections to appear when it is dark outside and the living room light is on. This can be resolved by placing some cardboard or tape around the edges of the ZeroView camera mount, which would stop the light pollution hitting the glass right in front of the camera.
![](https://utbrudd.bouvet.no/wp-content/uploads/2017/01/Screen-Shot-2017-01-05-at-13.01.51.png)

> _Example of light pollution affecting the pictures from the Camera_

![](https://utbrudd.bouvet.no/wp-content/uploads/2017/01/IMG_6383-e1483636837240-1024x1024.jpg)

> _Here you can make out the gap between the ZeroView/Camera and the glass window_

**Other Issues**

A more difficult issue to resolve was that of _false positives_. The Motion software algorithm for detecting movement is based on the amount of pixels changing from frame to frame. In practice this meant that I received alerts when the neighbours cat paid us a visit, or on partly overcast days when the shadows in the garden quickly moved and changed. Rain running down the window was also an issue.

![](https://utbrudd.bouvet.no/wp-content/uploads/2017/01/Screen-Shot-2017-01-05-at-12.15.26.png)

> _Example of false positive due to moving shadows_

On some days I received 50 alert emails due to these false positives, which tended to undermine the usefulness of the camera. Motion allows you to tweak the amount of pixels needed to trigger an alert, but then you run the risk of making the camera less effective.

Over all I was very happy with the result. The camera worked as designed and satisfied our original requirements.

The false positives issue was the only real problem. I therefore decided to find a solution to this!

In my next blog post I show [how I solved the problem of false positives by using Image Analysis and Amazon Web Services](https://utbrudd.bouvet.no/2017/01/10/smarten-up-your-pi-zero-web-camera-with-image-analysis-and-amazon-web-services-part-1/).

Until then, thanks for reading! If you have put together a similar project, or have any questions about this blog, or find any errors in the code then feel free to tweet me [@markawest](https://twitter.com/markawest) or post a comment below.
