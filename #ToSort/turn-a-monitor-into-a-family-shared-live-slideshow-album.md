# Turn a Monitor Into a Family-Shared Live Slideshow Album

_Captured: 2017-05-13 at 14:51 from [www.hackster.io](https://www.hackster.io/naran-inc/turn-a-monitor-into-a-family-shared-live-slideshow-album-63ca4f?ref=channel&ref_id=425_published___&offset=2)_

![Turn a Monitor Into a Family-Shared Live Slideshow Album](https://hackster.imgix.net/uploads/attachments/294988/thumbnail_iq2GSI9aj4.jpg?auto=compress%2Cformat&w=900&h=675&fit=min)

'Keeping contact with your family can be difficult when you live far from them. Even an increasing number of communication means doesn't make it easier to take the time to message, email or Skype your family. We offer you today a fun and easy way for your family and your elders' to keep track of everyone's everyday life.

**OBJECTIVE**: Turn an old monitor into a smart screen that will automatically display all your daily pictures.

**FOR** **WHOM: **This project is perfect for families who live far from each other, especially big families with members spread in different cities. It's the perfect way for your parents/grandparents or even the whole family (you can do the same for several monitors) to keep track of the best moments your daily life in a very simple way, without them having to turn on a computer or any other tech device.

![](https://hackster.imgix.net/uploads/attachments/294991/FUVRXPSJ1QP37R5.MEDIUM.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

  * Raspberry Pi 2 or 3 // ~$25-$35
  * 16GB SD Card // ~$9
  * A monitor with HDMI connectivity
  * HDMI cable

**Note**: This project is based on Kiosk app for Prota OS, which is not yet available for all users. The beta will be released next week, and we'd like to grant a free access to any person who would like to join the beta testing program.

Please contact us to [address ](http://eepurl.com/cHy8gX)to enroll or get further information on the program. (FYI, the official launch will be around early of May!)

### Step 2: SET UP YOUR PROTA PI SMART HUB

You first need to build the smart hub that will control the automation of your ring bell and connect all devices together. Prota OS for Raspberry Pi is our free smart hub OS which is very easy to install. In no time you will turn your Raspberry Pi into a smart home automation hub!

![](https://hackster.imgix.net/uploads/attachments/294992/F7U284BIZYGB9XA.MEDIUM.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

You can download [Prota OS here.](https://prota.info/prota/pi/) Then burn it on the SD card. We made an [easy guide ](http://docs.prota.info/101-prota-pi/)you can follow to set up your Prota Pi.

Alternatively, you can check [this tutorial.](https://www.instructables.com/id/Build-Your-Own-Smart-Hub-Prota-OS-for-Raspberry-Pi/)

### Step 3: DOWNLOAD AND SET UP ALL NECESSARY APPS

Once you're Prota Pi is set up:

  * Go to App Libraries
  * Download Kiosk app
  * Download Email app
  * Download IFTTT app 

IFTTT app will allow you to connect your Prota with an IFTTT account. On IFTTT, you can easily set up an automation that will automatically display the photos you take, as soon as you take them (as long as you have an internet connection on your smartphone).

Email app will connect an email address to your Prota Pi, to allow the rest of your family to send other images to the monitor. To avoid a constant spam of emails, you should create an email address dedicated to this slideshow. All family members will know that sending emails to that specific address will directly duplicate the images on the screen. That incredibly simplifies the process of sharing with your loved ones, with an almost instant repercussion on the monitor!

  * Open Email app
  * Click on + and add your credentials
  * If you have an error message displaying about authorized access (happens for instance with Gmail), you need to grant access as explained in this [guide.](http://docs.prota.info/guides/apps/email/)

Kiosk app is the app that will display the photos on your monitor. For now, you don't need to set anything.

### Step 4: WRITE DOWN THE AUTOMATION

Smart home is all about setting up automation workflows. Let's create simple ones that will automate the display of your photos.

![](https://hackster.imgix.net/uploads/attachments/294993/F63BMSUJ1QP3DFY.MEDIUM.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

Automation of images sent by email

  * Open Stories app.
  * Click on + Click on When.
  * Set up the sensor-story as "When [EMAIL] receives a message." If you click on "Conditions," you can filter which emails will trigger this automation workflow based on the address of the sender or the subject line.
  * Set up the action-story as "... [KIOSK SCREEN] add a new media slide" and set the instructions as follow ⇒ for value select "file," set temporary on "true" and set the time range it should stay up until it is replaced by a following image (we will set for instance 60 seconds).

Follow the screenshots below. Alternatively, you can click on that [link ](http://stories.market/stories-market/imp/?ident=1e4455368b3f4b40&desc=)to import the same storyline to your Stories app.

![](https://hackster.imgix.net/uploads/attachments/294995/FTP7PABJ1QP3DV4.SMALL.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

![](https://hackster.imgix.net/uploads/attachments/294994/FHSX9FBJ1QP3DXX.SMALL.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

![](https://hackster.imgix.net/uploads/attachments/294996/FOZOPAIJ1QP3DYX.SMALL.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

![](https://hackster.imgix.net/uploads/attachments/294997/FBHH8KSJ1QP3E0D.SMALL.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

![](https://hackster.imgix.net/uploads/attachments/294999/FRSDL55J1QP3E18.SMALL.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

Automation of images directly appearing after you take them

  * Click on +
  * Click on When
  * Set up the sensor-story as "When [IFTTT] runs a Prota applet."
  * Set up the action-story as "... [KIOSK SCREEN] add a new slide" and set the instructions as follow ⇒ set the value as Result1, the type as Image, set Temporary as True and the duration as 60 seconds.

Follow the screenshot below or this [link.](http://stories.market/stories-market/imp/?ident=f78a258a4efe49e4&desc=)

![](https://hackster.imgix.net/uploads/attachments/294998/FO7SUYDJ1QP37R8.MEDIUM.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

IFTTT applet You now need to create the IFTTT applet that will send the pictures taken on your smartphone to your Prota.

Go to [IFTTT.com](http://ifttt.com/) and create an account. You also need to download the IFTTT app on your smartphone and sign in.

  * Search for 'Prota' and connect your Prota Space account to IFTTT (you need to use a device which has access granted).
  * Start creating a new applet.
  * For the IF part, select either Android Photos or iOS Photos (depending on your smartphone) and select "`Any new photo` " (or another option that would fit better your expectations).
  * For the THEN part, select Prota and use the option "`Execute the Storyline` ". Select the storyline you wrote earlier (starting with When IFTTT run a Prota applet") and set the Parameter1 as "`PublicPhotoURL` ".
![](https://hackster.imgix.net/uploads/attachments/295000/FBB3PEMJ1QP37RC.MEDIUM.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

Alternatively, use those pre-made applet:

![](https://hackster.imgix.net/uploads/attachments/295001/FF88O8UJ1QP37S0.MEDIUM.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

You can now plug-in your monitor with the HDMI port of your Prota Pi and start taking pictures. All pictures will directly be displayed on the screen.

You can now keep updated all your family members with snapshots of your daily life, a perfect way to share your travel adventures with your family members. You can also send news or any other information the same way, and while only one device can be directly paired via IFTTT, you can enroll any other family member into this project through the email automation.

Kiosk app is still in development but already allows you to display any pre-defined text (for instance to warn you of a special event), videos or any website you want. A lot more features are about to be released so make sure to subscribe to our beta tester program.

We hope you enjoyed this project. Don't forget to support us by "favoriting" it and following us on both Hackster and [Twitter.](https://twitter.com/thenaran_)

If you have any question, please use our [forum!](http://support.prota.info/hc/en-us)
