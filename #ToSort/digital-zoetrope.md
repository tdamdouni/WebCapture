# Digital Zoetrope

_Captured: 2017-11-10 at 18:43 from [www.corteil.co.uk](http://www.corteil.co.uk/Blog/making/digital-zoetrope/)_

![](http://www.corteil.co.uk/Blog/wp-content/uploads/2015/08/IMG_20150423_203936.jpg)

You may have seen on my posts on Twitter about my project "Digital Zoetrope". It is going to be a true zoetrope, with 12 Adafruit OLED displays connected to a single Raspberry Pi via SPI. The first hurdle is that the Raspberry Pi has only two CS lines, after talking with my friends at Makespace, Cambridge's maker/hack space. I decided that the displays would be daisy chained together with custom daughter PCBs controlling the CS line and isolating any other data lines as required, they will also buffer the signals. The PCBs will act as shift register, passing the signals on to the next screen. I also have plans for creating a Raspberry Pi video camera for recording short films to download to the zoetrope. I hope to have the above, all ready for the UK Makerfaire in Newcastle and a pro-type running at the Raspberry Pi birthday bash. I would also like to thank Pimoroni for their support in the making of this project.

Video showing 3 displays running

### Progress so far

I have been working on this project since the start of the year, first thing I did was select the display I would be using, the reason, I selected the Adafruit OLED is the bright image, and also that there was code written for the Arduino by Adafruit, first job was converting the Adafruit C code into python, I needed a library for controlling the display over SPI, I found and followed a "how too" on the Raspberry Pi Spy blog site, and installed the py-spidev library. I wrote a number of test programs and was able to write directly to the screen memory and was able to update the screen in less than 0.03 of a second, result. Due to a limitation with the SPI library write function, I had to break each frame into 8 blocks. Next job was writing a single frame from a video to the display, for this purpose I installed the python library SimpleCV, with the library, I was able to convert a MP4 formatted video to single frames, and read the RGB value of each pixel. The next step was to convert the RGB value to the 565 colour space and load the pixels into blocks and then each block of pixels into a single list for each frame. The frames are stored in another list. At the end of this I was finally able to display images on the display! You can find the code on my Github account.

### Connection details to Adafruit OLED display

![breadboard](http://www.corteil.co.uk/Blog/wp-content/uploads/2015/08/breadboard.jpg)

Connections OLED to Raspberry Pi

Follow the drawing for connecting the display, the same connection will work for all models of the Raspberry Pi

### Code

you can download the code from my github account by entering the following command on your Raspberry Pi's command line.

> _git clone https://github.com/Corteil/Zoetrope.git_

then change the working directory

> _cd ./Zoetrope_

and then run the code

> _sudo python displayTest-2.py_

you will need to place the video you wish to display in the same directory as the program and change the follow line to reflect the name of your file. Edit the file with your editor of choice.

> _video = VirtualCamera("Pirate.mp4″, "video") # Load an existing video into a virtual camera_

### Next Steps

Next on the list is bread boarding the logic for the daughter PCBs and getting a couple of displays running. Designing and getting the PCBs made. Plus design the frame.

![IMG_20150328_120507](http://www.corteil.co.uk/Blog/wp-content/uploads/2015/08/IMG_20150328_120507-1024x768.jpg)

> _breadboard with the logic ICs_

![IMG_20150417_201809](http://www.corteil.co.uk/Blog/wp-content/uploads/2015/08/IMG_20150417_201809-1024x768.jpg)

> _PCB for display selection_

![IMG_20150420_221117](http://www.corteil.co.uk/Blog/wp-content/uploads/2015/08/IMG_20150420_221117-1024x768.jpg)

and a PCB with the surface mounted components installed

![IMG_20150421_115001](http://www.corteil.co.uk/Blog/wp-content/uploads/2015/08/IMG_20150421_115001-1024x768.jpg)

laser cut frames for holding the screens

![IMG_20150403_103616](http://www.corteil.co.uk/Blog/wp-content/uploads/2015/08/IMG_20150403_103616-1024x768.jpg)

base showing encoder

Frame advance sensor working

### Links

http://www.raspberrypi-spy.co.uk/2014/08/enabling-the-spi-interface-on-the-raspberry-pi/  
https://github.com/doceme/py-spidev

### Video

The video I'm using for testing the displays is Cuthbert, The Pirate Who Never Listened from [Neil Grunshaw](http://vimeo.com/grunshaw)
