# How to Get Windows 10 IoT Core on the Raspberry Pi

_Captured: 2019-04-28 at 22:50 from [www.digikey.com](https://www.digikey.com/en/maker/blogs/2019/how-to-get-windows-10-iot-core-on-the-raspberry-pi?utm_source=twitter&utm_medium=social&utm_campaign=windows10iotonrpi)_

### ![How to Get Windows 10 IoT Core on the Raspberry Pi](https://www.digikey.com/-/media/MakerIO/Images/blogs/2019/How%20to%20Get%20Windows%2010%20IoT%20Core%20on%20the%20Raspberry%20Pi/Featured-image.jpg?la=en&ts=651d9512-3919-440f-9e9b-aacba0769479)

When it comes to IoT projects on the Raspberry Pi, many may think of Raspbian and other Linux-based distros. However, Microsoft has released a simple version of Windows 10, called Windows 10 IoT Core. It contains many .net framework elements that can make creating Windows-based IoT projects a breeze!

### BOM:

### Step 1: Get Windows 10

Unlike other systems, Windows 10 IoT requires a Windows 10 installation for access, programming, and downloading, so no matter how much you may love your Windows 7 system, you will have to bite the bullet and get Windows 10. Fortunately, Windows 10 can be purchased cheaply from websites like Software Geeks, and it can be installed alongside a previous Windows installation. That means you won't have to wipe and format your drive!

### Step 2: Get Windows 10 IoT Core (and the Windows 10 Core IoT Dashboard)

Microsoft tries to make the installation of Windows 10 IoT simple with the use of the IoT Core Dashboard. This dashboard allows you to create a customized Windows 10 IoT system by targeting specified CPUs, but whether or not this actually makes things simpler depends on the user. We'll use the Dashboard in this How-To, mainly because the Dashboard can flash a microSD card without the need for ISO to USB packages.

You can download Windows 10 IoT Core [here](https://docs.microsoft.com/en-us/windows/iot-core/downloads).

You can download the Windows 10 IoT Core Dashboard [here](https://docs.microsoft.com/en-us/windows/iot-core/downloads).

### Step 3: Create your Raspberry Pi Image

Insert a microSD card into a card reader and ensure that Windows recognizes the inserted card. Open the Windows 10 IoT dashboard and click the button titled "Set up a new device." Since the dashboard can target many different systems, make sure that Raspberry 2 & 3 is selected as the device type. In the build version, choose the latest build and choose the microSD card that you inserted as the drive target in the drive selection.

Before you can download the image to the SD card, you will also need to set the admin password. Once all of this is done, accept the software license terms and click "Download and Install."

![How to Get Windows 10 IoT Core on the Raspberry Pi](https://www.digikey.com/-/media/MakerIO/Images/blogs/2019/How%20to%20Get%20Windows%2010%20IoT%20Core%20on%20the%20Raspberry%20Pi/1_Create.jpg?ts=df69d9cb-5983-4a8f-8c9b-86d315a7510b&la=en-US)

### Step 4: Get Visual Studio 2017

As the OS downloads, you will need to get a copy of Visual Studio 2017. This package allows you to create programs in VB.net, C#, and C++ using the .net framework. Make sure to choose the community edition, as the other versions are not free.

You can get Visual Studio 2017 [here](https://visualstudio.microsoft.com/downloads/).

### Step 5: Launch Visual Studio 2017

The next step requires us to create a universal application. To do this, After Launching Visual Studio 2017 click File > New Project and then Visual Basic > Windows Universal > Blank App. If this is the first time you have done this, the system may require you to download some new libraries before continuing.
