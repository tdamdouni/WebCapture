# RaspiReader: build your own fingerprint reader

_Captured: 2017-10-04 at 15:18 from [www.raspberrypi.org](https://www.raspberrypi.org/blog/raspireader-fingerprint-scanner/)_

Three researchers from Michigan State University have developed a low-cost, open-source fingerprint reader which can detect fake prints. They call it [RaspiReader](https://arxiv.org/pdf/1708.07887.pdf), and they've built it using a Raspberry Pi 3 and two Camera Modules. Joshua and his colleagues have just uploaded all the info you need to build your own version -- let's go!

![GIF of fingerprint match points being aligned on fingerprint, not real output of RaspiReader software](https://www.raspberrypi.org/app/uploads/2017/09/fingerprint2.gif)

> _Sadly not the real output of the RaspiReader_

## Falsified fingerprints

We've probably all seen a movie in which a burglar crosses a room full of laser tripwires and then enters the safe full of loot by tricking the fingerprint-secured lock with a fake print. Turns out, the second part is not that unrealistic: you can fake fingerprints using a range of materials, such as glue or latex.

![Examples of live and fake fingerprints collected by the RaspiReader team](https://www.raspberrypi.org/app/uploads/2017/09/RaspiReader3-768x375.png)

> _The RaspiReader team collected live and fake fingerprints to test the device_

If the spoof print layer capping the spoofer's finger is thin enough, it can even fool readers that detect blood flow, pulse, or temperature. This is becoming a significant security risk, not least for anyone who unlocks their smartphone using a fingerprint.

## The RaspiReader

This is where Anil K. Jain comes in: Professor Jain leads a [biometrics research group](http://biometrics.cse.msu.edu/). Under his guidance, Joshua J. Engelsma and Kai Cao set out to develop a fingerprint reader with improved spoof-print detection. Ultimately, they aim to help the development of more secure commercial technologies. With their project, the team has also created an amazing resource for anyone who wants to build their own fingerprint reader.

So that replicating their device would be easy, they wanted to make it using inexpensive, readily available components, which is why they turned to Raspberry Pi technology.

![RaspiReader fingerprint scanner by PRIP lab](https://www.raspberrypi.org/app/uploads/2017/09/RaspiReader1.png)

> _The Raspireader and its output_

Inside the RaspiReader's 3D-printed housing, LEDs shine light through an acrylic prism, on top of which the user rests their finger. The prism refracts the light so that the two Camera Modules can take images from different angles. The Pi receives these images via a [Multi Camera Adapter Module](http://www.arducam.com/multi-camera-adapter-module-raspberry-pi/) feeding into the CSI port. Collecting two images means the researchers' spoof detection algorithm has more information to work with.

![Comparison of live and spoof fingerprints](https://www.raspberrypi.org/app/uploads/2017/09/RaspiReader2.png)

> _Real on the left, fake on the right_

## RaspiReader software

The Camera Adaptor uses the `[RPi.GPIO](https://pypi.python.org/pypi/RPi.GPIO)` Python package. The RaspiReader performs image processing, and its spoof detection takes image colour and 3D friction ridge patterns into account. The detection algorithm extracts [colour local binary patterns](https://en.wikipedia.org/wiki/Local_binary_patterns) … please don't ask me to explain! You can have a look at the [researchers' manuscript](https://arxiv.org/pdf/1708.07887.pdf) if you want to get stuck into the fine details of their project.

## Build your own fingerprint reader

I've had my eyes glued to my inbox waiting for Josh to send me links to instructions and files for this build, and here they are (thanks, Josh)! Check out the video tutorial, which walks you through how to assemble the RaspiReader:

You can find a parts list with links to suppliers in the video description -- the whole build costs around $160. All the STL files for the housing and the Python scripts you need to run on the Pi are available on [Josh's GitHub](https://github.com/engelsjo/RaspiReader).

## Enhance your home security

The RaspiReader is a great resource for researchers, and it would also be a terrific project to build at home! Is there a more impressive way to protect a treasured possession, or secure access to your computer, than with a DIY fingerprint scanner?

![](https://img.buzzfeed.com/buzzfeed-static/static/2015-06/19/6/enhanced/webdr09/anigif_enhanced-25675-1434709288-9.gif)

Check out this [James-Bond-themed](https://www.raspberrypi.org/blog/be-james-bond/) blog post for Raspberry Pi [resources](https://www.raspberrypi.org/resources/) to help you build a high-security lair. If you want even more inspiration, watch this video about a [laser-secured cookie jar](https://www.raspberrypi.org/blog/laser-cookies/) which [Estefannie](https://www.youtube.com/channel/UCXX7AV8HDBCZXbKRHJYYODg) made for us. And be sure to share your successful fingerprint scanner builds with us [via social media](https://www.raspberrypi.org/blog/connecting-raspberry-pi-social/)!
