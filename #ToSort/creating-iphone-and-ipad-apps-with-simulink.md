# Creating iPhone and iPad Apps with Simulink

_Captured: 2017-03-04 at 00:04 from [blogs.mathworks.com](http://blogs.mathworks.com/simulink/2016/11/08/creating-iphone-and-ipad-apps-with-simulink/?s_eid=PSM_gen)_

The other day, a user told me: _That would be cool if we could program apps for smartphones using Simulink_.

Guess what my answer was: _Of course you can!_

**Simulink Support Packages for Apple iOS and Android**

Yes, you heard it right. If you have a Simulink license, you can download the [Simulink Support Package for Apple iOS](https://www.mathworks.com/hardware-support/ios-device-simulink.html), or if your prefer the [Simulink® Support Package for Android™](https://www.mathworks.com/hardware-support/android-programming-simulink.html).

![Simulink Apple iOS library](http://blogs.mathworks.com/images/simulink/2016Q4/iosgettingstartedexample_02.png)

Since he works mostly in the Apple ecosystem and I don't, I asked my colleague Mariano Lizarraga Fernandez to be guest blogger this week and describes his first experience trying to build an app for his iPhone.

**Getting Started**

Before you get started, make sure you have the following:

  * An Apple computer running OS X Yosemite or El Capitan with MATLAB and Simulink installed.
  * Xcode 7.x.
  * A free Apple Developer Account.
  * The [Simulink Support Package for Apple iOS](https://www.mathworks.com/hardware-support/ios-device-simulink.html).
  * An iOS device running iOS 8.x or 9.x.

Make sure that when you install the Support Package you completely follow the setup instructions **including obtaining a certificate for signing the application**. You need to make sure, in your Xcode preferences, that your certificate is valid and that the identifier matches that of your application. In the following picture, **CBDemo** is the name of the Simulink model:

![Xcode Configuration](http://blogs.mathworks.com/images/simulink/2016Q4/XcodeConfig.png)

For your first model, as suggested in the [Getting Started documentation page](https://www.mathworks.com/help/supportpkg/appleios/examples/getting-started-with-apple-ios-devices.html), an easy test is to acquire the camera video, and display it on the screen. You can directly access this demo by executing iosGettingStartedExample in MATLAB.

Before running this model, open the model's Configuration Parameters, and in the Hardware Implementation section make sure the Hardware Board is configured for Apple iOS Devices and that your iOS Device is shown in the Target Hardware Resources:

![Model Configuration for iPad target](http://blogs.mathworks.com/images/simulink/2016Q4/iosConfigParams.png)

> _Now to the Fun Part ..._

To give you an idea of what kind of app it is possible to create, we decided to start with an example from the [Computer Vision system Toolbox](https://www.mathworks.com/products/computer-vision/): [Traffic Warning Sign Recognition](http://www.mathworks.com/help/releases/R2016a/vision/examples/traffic-warning-sign-recognition.html)

The model as-shipped loads a video from your filesystem and performs identification of stop and yield traffic signs. To adapt it for the iOS target, we only need to replace source and sink. Instead of just replacing the blocks, we decided to use [Variants Subsystems](http://www.mathworks.com/help/simulink/examples/variant-subsystems.html) to switch between a simulation-only version, and a deployable version.

For the source, we use the [iOS camera source](https://www.mathworks.com/help/supportpkg/appleios/ref/camera.html) block. Since this source only produces 8-bit unsigned integers, we need to modify: (1) How the [From Multimedia File](https://www.mathworks.com/help/dsp/ref/frommultimediafile.html) block produces the output so it too results in 8-bit unsigned integers; and (2) Convert the 8-bit frame to single precsision floating point one using the [im2single](https://www.mathworks.com/help/images/ref/im2single.html) function.

![Video source for Simulink Apple iOS library](http://blogs.mathworks.com/images/simulink/2016Q4/iosSources.png)

Similarly, for the sink variant, since the [iOS Video Display](https://www.mathworks.com/help/supportpkg/appleios/ref/videodisplay.html) block only accepts 8-bit unsigned integers, we convert the processed image from single precision floating point to 8-bit unsigned integers using the [im2uint8](https://www.mathworks.com/help/images/ref/im2uint8.html) function

![Video Sink for Simulink Apple iOS library](http://blogs.mathworks.com/images/simulink/2016Q4/sinkVariant.png)

> _Here is what this looks like in action on an iPad mini:_

<https://youtu.be/AMLdghppCn4>

**Now it's your turn**

What kind of app will you create for your iPhone or iPad? Noise cancelling headphone? Driving assistant for blind people?

If you create a cool app, submit it to [MATLAB Central File Exchange](http://www.mathworks.com/matlabcentral/fileexchange) and let us know in a comment below.
