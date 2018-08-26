# How to Build Your Own Weather Station Using a Raspberry Pi

_Captured: 2018-07-13 at 19:22 from [dzone.com](https://dzone.com/articles/how-to-build-your-own-weather-station-using-a-rasp?edition=386201&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-07-13)_

![](https://s3-eu-west-1.amazonaws.com/wia-flarum-bucket/2018-07-02/1530519961-733576-weather-station-1.png)

In this tutorial, we will go over how to create a weather station using a Raspberry Pi and send events to Wia.

This is an updated version of our old tutorial. There have been several changes to the Wia dashboard and code since our last tutorial.

## What You Will Need

  * Raspberry Pi 2 or Model 3 B+
  * Raspberry Pi Sense HAT
  * Node.js and NPM must both be installed on the Raspberry Pi.

If you do not have it already installed, [learn how to install node.js here](https://community.wia.io/d/4-how-to-install-node-js-on-any-raspberry-pi).

## Setting up the Raspberry Pi

First, you have to set up the Raspberry Pi. [Our tutorial will walk you through it!](https://developers.wia.io/docs/raspberry-pi) Be sure to follow each step carefully. When you're ready, run `ssh pi@('RASPBERRY-PI-IP-ADDRESS')`. This will allow you to begin working in the Raspberry Pi terminal through your computer.

## Setting up the Wia Node.js SDK

First, we need to create a folder on the Raspberry Pi to store our files. Create a new folder called `wia-wether-device`.

Next, initialize the package by creating a packackge.json file using the command line `npm init`. Hit `enter` for each of the prompts. Right now, they are not important.

Once you are through that, you can install the Wia SDK onto the Raspberry Pi. Install the Wia SDK by using the command line `npm install --save wia`.

## Using the Sense HAT with Node.js

Next, we must install nodeimu so that we can use the sensors. Use the command `npm install --save nodeimu`.

Now, your package.json file should look like this:

![](https://s3-eu-west-1.amazonaws.com/wia-flarum-bucket/2018-07-02/1530524205-205083-screen-shot-2018-07-02-at-103618-am.png)

## Create Your Weather Device

Go to the [Wia Dashboard](https://dashboard.wia.io/) and select `Create a New Space.` Then, select `Devices`. You will add a device and give it a name. Now, in the `Configuration` tab of your device, you will find `device_secret_key,` which should begin with `d_sk`. Make note of this. It will be important later on.

## The Code

Create a file called `index.js`. Then, copy the code from the example below and paste it into the `index.js` file.

Replace the `device_secret_key` with your device's secret key:
    
    
    var wia = require('wia')('device-secret-key');
    
    
     setTimeout(function() { tic = new Date(); IMU.getValue(callback); } , 250 - (toc - tic));
    
    
    wia.stream.on('connect', function() {

To test your program, run `node index.js`  
Now, you should see events appearing in the `Events` tab for your device in the Wia Dashboard.

## The App

Next, we will make a few widgets through Wia to present the data that the weather station collects. Log in to the Wia dashboard, and navigate to your device. Select the `widgets` tab and create a new widget. Name it `Humidity`. For the `event` box, type humidity exactly as it appears in the node.js code that you copy and pasted before. Select `done` and you will see the latest update! Follow these steps for temperature and pressure to finish your Weather Station project.

![](https://s3-eu-west-1.amazonaws.com/wia-flarum-bucket/2018-07-02/1530524302-521378-screen-shot-2018-07-02-at-103805-am.png)

## Web Page

Next, we will create a webpage and host it on GitHub so that we can check the weather from our weather station at any time!

If you don't have a GitHub account already, [you can make one here](https://github.com/).

Once you are set up with GitHub, create a new repository and name it your-username.github.io. Check the box to initialize with a README.

Now, navigate to your new repository and create a new file. It **must** be named `index.html`. Copy and paste the following block of code:

So far, our webpage is pretty blank. Navigate back to your Wia Dashboard. In the overview for your device, you can see your widgets. In the upper right-hand corner of the widget, there should be a box with an arrow. Click the box. A screen like this should pop up.

![](https://s3-eu-west-1.amazonaws.com/wia-flarum-bucket/2018-07-02/1530524388-230043-screen-shot-2018-07-02-at-103927-am.png)

Change the settings so that `Anyone can view this widget and embed it in any website`. You should also see the `Embed` code, which will start with <iframe> and end with </iframe>. Copy the entire code and paste it below the <h1>Wia Weather Station</h1> line and above the </body> line. Your full code should look something like this:

You will need to do this again for each widget. Click commit changes. Now, visit your site at <https://github.com/username/username.github.io>.

Now, you should see the weather from your Raspberry Pi appear on your own webpage!

![](https://s3-eu-west-1.amazonaws.com/wia-flarum-bucket/2018-07-02/1530524430-891880-screen-shot-2018-07-02-at-104013-am.png)

> _Topics: node js , raspberry pi , javascrip , weather , weather station , developer , tutorial_
