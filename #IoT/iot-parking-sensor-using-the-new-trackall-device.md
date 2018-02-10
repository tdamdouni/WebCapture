# IoT Parking Sensor Using the New TrackALL Device

_Captured: 2018-02-09 at 09:41 from [www.hackster.io](https://www.hackster.io/mc-Things/iot-parking-sensor-using-the-new-trackall-device-5a15ad?utm_source=Hackster.io+newsletter&utm_campaign=ca1b82efe4-EMAIL_CAMPAIGN_2017_07_26&utm_medium=email&utm_term=0_6ff81e3e5b-ca1b82efe4-141949901&mc_cid=ca1b82efe4&mc_eid=1c68da4188)_

![IoT Parking Sensor Using the New TrackALL Device](https://hackster.imgix.net/uploads/attachments/415480/2018-01-17-trackall-time-of-flight-02_G04hCVJwyg.jpg?auto=compress%2Cformat&w=900&h=675&fit=min)

In this example we'll use the distance (LIDAR) sensor on the new [TrackALL (On kickstarter now!)](https://www.kickstarter.com/projects/mcthings/trackall-a-wireless-battery-powered-asset-tracker?ref=dy0u4c) to setup a wireless IoT parking sensor and displaying the information onto a [Tago.io](http://tago.io/) dashboard. This can be done using Sigfox and/or mcAir!

Not only could you set this up as a personal parking sensor in your garage, office, etc. but imagine a smart building/city solution where you could put in a wireless system that can last for years while sending the data to a cloud service/application of your choice!

With the advent and soon to be released mcCloud feature, the mcThings platform now provides the ability to connect to devices remotely, from anywhere in the world and within range of an mcGateway, so that you can easily debug and make programming changes to the application on your mcThings device. New mcOS (device firmware) is also updated OTA through mcCloud and the mcGateway.

After writing a programming script within mcStudio and uploading that to your mcCloud security domain, you can then deploy applications to your devices easily from anywhere. Information incoming from your devices travels either to Sigfox to the cloud or to an mcGateway over mcAir (a LPLAN) and are forwarded, through integrations that you setup within your security domain, to any type of application that can receive webhooks (HTTPS). You can even send the same information to multiple different applications like Microsoft Azure, Ubidots, AWS, Losant, etc. Check out this visual:

![](https://hackster.imgix.net/uploads/attachments/414770/connectivity_zZHReKDoCc.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

> _How the new mcThings platform works_

You can use either Sigfox or mcAir to send the data to the internet and onto the application of your choice to view/capture/etc. the data. Sigfox, where available, provides fantastic range and is perfect for sending location (and other data) from Sigfox enabled devices. If you are not within Sigfox coverage, you can send information from the device to the cloud within range of an mcGateway (theTrackALL device has an mcAir range of up to 1.2km!) . You can also log data to the device and send it to the cloud when the device comes back into range of an mcGateway. And finally, you can also use both networks in tandem (store data on the device while sending exception reports out using Sigfox) if you wish. Check out more info in our [Kickstarter campaign!](https://www.kickstarter.com/projects/mcthings/trackall-a-wireless-battery-powered-asset-tracker?ref=dy0u4c)

installing a TrackALL is really easy as it has flanges for screws and you could also use many other methods (like double-sided tape, velcro, etc)

;

;

![](https://hackster.imgix.net/uploads/attachments/415039/20180120_153222_resized_Kz14SOansO.jpg?auto=compress%2Cformat&w=680&h=510&fit=max)

Tago is a very friendly and easy to use IoT cloud application - You have lots of options to display your data like graphs, displays, maps, etc. One thing that we really like is the ability to display data as media! Tago allows you to show images or videos based on the data incoming and the parameters you set .

In the below dashboard, we setup TrackALL devices, programmed them to measure distances, and forward that data to Tago. Within the dashboard, we setup media widgets which change images based on the distance measured allowing us to display how many parking spaces are left!

;

;

![](https://hackster.imgix.net/uploads/attachments/414799/open_HWKM1QhRt2.PNG?auto=compress%2Cformat&w=680&h=510&fit=max)

Its easy to change your dashboard to suit your needs:

![](https://hackster.imgix.net/uploads/attachments/414802/almostfull_VSRdPwsq5s.PNG?auto=compress%2Cformat&w=680&h=510&fit=max)

You can also do some fun stuff too!

![](https://hackster.imgix.net/uploads/attachments/414807/ezgif_com-video-to-gif_\(5\)_EJRpdxlVCj.gif?auto=compress%2Cformat&w=680&h=510&fit=max)

The TrackALL device is currently on Kickstarter,[ check it out!](https://www.kickstarter.com/projects/mcthings/trackall-a-wireless-battery-powered-asset-tracker?ref=2wfs2k) And join our hub here on Hackster to stay up to date with many more examples and projects to come using the mcThings platform.

Thanks for reading!
