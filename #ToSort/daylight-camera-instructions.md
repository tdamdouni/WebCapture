# Daylight Camera Instructions

_Captured: 2018-06-14 at 20:58 from [mynaturewatch.net](https://mynaturewatch.net/daylight-camera-instructions)_

![instructions-5046.jpg](https://static1.squarespace.com/static/5a54dbf8692ebedda68569ff/5aba1b1c03ce64c09d48174b/5aba1b33f950b783c303a946/1525353407642/instructions-5046.jpg?format=750w)

Making My Naturewatch Camera is a 6 step process.

  1. **Download the Software. **The camera software needs to be installed on the SD card from the Internet. The Raspberry Pi Zero will read the software from the SD card to become a My Naturewatch Camera.
  2. **Assemble the Electronics.** Here you will attach the camera to the Pi Zero. It's a little fiddly, but with patience you'll manage.
  3. **Name Your Camera.** You can give your camera its own name and password.
  4. **Test Your Camera**. Now you can power up the camera and see if it works.
  5. **Make the Camera Housing.** Assuming you have a working camera, it's time to make a weather-resistant housing from household materials.
  6. **Assemble the Camera. ** Finally, you're ready to fix the camera inside the housing and try it out!

The whole process should only take 60 - 90 minutes.

_Copy the camera software to an SD Card (up to 1 hour). This software contains the operating system for the Pi Zero and an application that controls the camera. This bundled software is often referred to as a 'disk image'._

_Downloading the software and installing it on the SD card can take a while, depending on things like the speed of your internet and the computer you're using. You can skip to Step 7 and continue working through the 'Assembly' and 'Housing' sections while you wait for actions in steps 1-6 to complete if you like._

1\. Download the disk image (2.3 GB) from here (up to 1hour):  
<http://interaction.gold.ac.uk/naturewatch-cam-v0p2p5.zip>

2\. Download an application called '[Etcher](https://etcher.io/)' this will copy the disk image to the micro SD card safely and easily.

3\. Unzip the disk image, making sure you have around 10GB of free space on your computer.

4\. Insert the Micro SD Card into your computer - using a micro SD Adaptor (your laptop may have a built-in SD Card Reader), or an External Micro SD Reader

5\. Using 'Etcher' software - select the unzipped disk image as 'Image' and the Micro SD Card as 'Drive', then press 'Flash'. This step can take up to 30 minutes.  
_(Helpful Tip: the time can be shortened by deselecting "Validate write on success" in the Etchers settings menu, found by clicking the cog on the top right of the app)_

![Untitled1.gif](https://static1.squarespace.com/static/5a54dbf8692ebedda68569ff/t/5b082b53352f5359eeda4d4f/1528450612491/Untitled1.gif?format=750w)

_The camera connector is very fragile, so take care on this step! _

7\. To attach the Camera Module to the Pi Zero: Unclip the black locking strip away on the white camera connector on on the Pi Zero - it should move outwards by 1mm and feel loose. Now insert the Camera Module ribbon under the black strip and into the white connector - the metal side of the camera ribbon should face toward the green board. Secure the ribbon by re-clipping the black strip towards the white connector.

_If the connector breaks, you can hold still use hot glue to hold the cable in place - but its best to be gentle and patient to avoid breakage._

![NW_instructions-5235.jpg](https://static1.squarespace.com/static/5a54dbf8692ebedda68569ff/5a87360553450aa2712e158f/5b082bd76d2a7369214f12ae/1528450612493/NW_instructions-5235.jpg?format=500w)

![NW_instructions-5245.jpg](https://static1.squarespace.com/static/5a54dbf8692ebedda68569ff/5a87360553450aa2712e158f/5b082c216d2a7369214f228e/1528450612496/NW_instructions-5245.jpg?format=500w)

8\. Super Glue a metal bolt or nut to the darkly coloured square chip on the Pi Zero. This helps with heat dissipation.

![NW_instructions-5252.jpg](https://static1.squarespace.com/static/5a54dbf8692ebedda68569ff/5a87376f53450aa2712e7be3/5b082ca1f950b791c0592657/1528450612498/NW_instructions-5252.jpg?format=500w)

![NW_instructions-5254.jpg](https://static1.squarespace.com/static/5a54dbf8692ebedda68569ff/5a87376f53450aa2712e7be3/5b082ccaf950b791c0592fa0/1528450612501/NW_instructions-5254.jpg?format=500w)

![NW_instructions-5255.jpg](https://static1.squarespace.com/static/5a54dbf8692ebedda68569ff/5a87376f53450aa2712e7be3/5b082cfc8a922d9de988c49d/1528450612503/NW_instructions-5255.jpg?format=500w)

_The ribbon cable can easily detach from the PI Zero. We recommend mounting both to a piece of card to protect the connection._

9\. Fold a 160 x 40mm piece of card in half. Stick the Camera to one side and the Pi Zero to the other, with the Camera ribbon hanging over the top of the cardboard.

**** Skip the naming procedure below if you are a Microsoft Windows user and proceed directly to step 13 ****

We have identified a bug with renaming the camera using Windows computers and are working on fixing the issue.

_Once Steps 1 - 5 are complete you can name your camera and make sure it works._

![intructions-screenshot1 \(boot\).png](https://static1.squarespace.com/static/5a54dbf8692ebedda68569ff/t/5b0809ea03ce647cacc9f6f7/1527258906311/intructions-screenshot1+%28boot%29.png?format=750w)

![intructions-screenshot2 \(find_config\).png](https://static1.squarespace.com/static/5a54dbf8692ebedda68569ff/t/5b080ab2f950b75f00f55171/1527258906313/intructions-screenshot2+%28find_config%29.png?format=750w)

11\. In 'boot', open '**naturewatch-configuration.txt**'. _Tip: You may need to eject the Micro SD Card and reinsert it again before you can view the contents_

![intructions-screenshot3tions \(config_file 2\).png](https://static1.squarespace.com/static/5a54dbf8692ebedda68569ff/t/5b080cc1575d1f998b7af943/1527258906315/intructions-screenshot3tions+%28config_file+2%29.png?format=750w)

12\. The Name and Password of your Camera can be edited by rewriting the appropriate lines which are defaulted as '**naturewatch-robin**' and '**badgersandfoxes'** respectively, or can be left as default

![NW_instructions-5221.jpg](https://static1.squarespace.com/static/5a54dbf8692ebedda68569ff/t/5b082e2e8a922d9de988fe40/1528450612505/NW_instructions-5221.jpg?format=750w)

13\. Insert the 'Micro SD Card' into the silver socket on the Pi Zero - the metal side of the SD Card should face toward the green board.

![NW_instructions-5247.jpg](https://static1.squarespace.com/static/5a54dbf8692ebedda68569ff/t/5b082e8470a6adc429bcb149/1528450612507/NW_instructions-5247.jpg?format=750w)

14\. Power the assembled Unit by connecting the USB Power Bank to the Pi Zero. The LED on the Pi Zero will illuminate when successfully powered. The small end of the USB cable plugs into the 'PWR' port on the end of the Pi Zero closest to the camera. The large end of USB cable plugs into the USB battery (or any USB power source).

15\. Allow 30 seconds for the Pi Zero to boot up. The green light on the Pi Zero will flicker to indicate processing. Once the system has started, a red LED on the Camera ribbon cable will light.

16\. On a Smartphone, tablet or computer connect to the Pi Zero's Wifi network using the name and password you chose when you named your camera.

17\. Open any internet browser and visit the following webpage to access the Camera Interface, which should bring up a live-feed alongside a 'Start recording' 'Sensitivity' and 'View Photos' button.

_Find more information about the web interface in 'Using My Naturewatch Camera"._

_My Naturewatch Camera should be protected from the elements by some sort of housing. The possibilities are endless, from ziplock bags to more elaborate constructions. We show you one possibility here, but feel free to improvise! _

![NW_instructions-5257.jpg](https://static1.squarespace.com/static/5a54dbf8692ebedda68569ff/t/5b082f92562fa7e0d724d83a/1528450612509/NW_instructions-5257.jpg?format=750w)

_The camera works best if the lens is not behind the housing material, no matter how clear that may seem. We drill a hole in our housing and use a cover to protect the lens._

18\. Pierce a hole in the side of a tall Food Storage Box, at a height that accommodates the Camera lens. The hole should be about 10mm in diameter, and can be made roughly with scissors, or accurately with a drill.

![Naturewatch_instructions-5260.jpg](https://static1.squarespace.com/static/5a54dbf8692ebedda68569ff/t/5a8737f5ec212d59c9dad5fc/1525353407663/Naturewatch_instructions-5260.jpg?format=750w)

19\. Cut around a Plastic 2Bottle with scissors to form a lens cover. Position the bottle opening around the Camera Hole of the Food Storage Box and attach with Sugru, Blu Tack or a hot glue gun.

![Naturewatch_instructions-5268.jpg](https://static1.squarespace.com/static/5a54dbf8692ebedda68569ff/t/5a87382c24a69413ba8c3775/1525353407671/Naturewatch_instructions-5268.jpg?format=750w)

20\. Tape the Cardboard camera mount inside the Tupperware, with the lens positioned to look through the hole you drilled, and place the attached Battery Pack inside. Tip: a pouch of silica gel will help any absorb moisture in the container.

![Naturewatch_instructions-5274.jpg](https://static1.squarespace.com/static/5a54dbf8692ebedda68569ff/5a8738ab8165f5d758b2b9a8/5a8738ab24a69413ba8c5c07/1525353407678/Naturewatch_instructions-5274.jpg?format=500w)

![Naturewatch_instructions-5278.jpg](https://static1.squarespace.com/static/5a54dbf8692ebedda68569ff/5a8738ab8165f5d758b2b9a8/5a8738abe2c4835a336c72a2/1525353407674/Naturewatch_instructions-5278.jpg?format=500w)

21\. Seal the lid - you now have a weatherproof myNaturewatch Camera!

_Tip: Unplug the battery when you're not using the camera to save power_

The Naturewatch Camera uses specially designed machine vision to understand when something is moving in front of the lens and then captures those images - you can view the captured images by pressing the 'Browse Photos' button when connected to the Naturewatch Cameras' Wifi.

You do not have to remain connected to the Cameras' Wifi for it to function and continue recording.

The battery pack of the Naturewatch Camera will have to be periodically charged for it to continue working.

For best results, try to frame the image of the Camera so that the action you expect to capture will be 0.5 - 1 metre away.

Share your images! Post your pictures to [Instagram](https://www.instagram.com/mynaturewatch/), [Facebook](https://www.facebook.com/mynaturewatch) and [Twitter](https://twitter.com/mynaturewatch) with the tags #mynaturewatch and #springwatch. See more on our [gallery page](https://mynaturewatch.net/gallery-1/).

![Mobile_00.jpg](https://static1.squarespace.com/static/5a54dbf8692ebedda68569ff/5a58cedc9140b7a08463f5e4/5a58cfae53450a9c6317b348/1527082863476/Mobile_00.jpg?format=1500w)
