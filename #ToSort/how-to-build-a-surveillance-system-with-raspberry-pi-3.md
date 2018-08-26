# How to Build a Surveillance System With Raspberry Pi 3

_Captured: 2018-07-03 at 23:14 from [dzone.com](https://dzone.com/articles/how-to-build-a-surveillance-system-with-raspberry)_

Before proceeding to code, you need to install the Node.js on your Raspberry Pi 3. Log in via SSH and update your Raspberry Pi system packages to their latest versions. Here is how to update your system package list:

Next, upgrade all your installed packages to their latest version:

To download and install the latest version of Node.js, use the following command:
    
    
    pi@w3demopi:~ $ curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -

Now, install it by running the following command:

Check the version number and whether the installation was successful with the following command:

Now that `Node.js` has been installed on your Raspberry Pi, you can now start with the coding.

## Coding the Raspberry Pi Camera Module

To use the camera, you need to include a library from npm. You will use the `pi-camera` library to install it and run the command in the terminal, as shown below. Check out the official link for the `pi-camera` npm module at <https://www.npmjs.com/package/pi-camera>:

![](https://www.survivingwithandroid.com/wp-content/uploads/2018/06/word-image-27.png)

Now, create a file with the name CameraModule.js and include the ` pi-camera` module in it:

As per the documentation of the `pi-camera` module, you need to set the configuration of the camera. You have to define two configurations -- one for taking still pictures and one for taking videos:

In both the configurations, the following aspects are defined:

  * A mode that defines whether the camera takes still photographs or a video. Note that the video is created in the h246 format, which is the raw format, and can be played on quite a few popular video players, including the VLC media player.
  * The output, which defines the path where the photo or video will be saved in local storage
  * The height and width, which defines the resolution
  * Timeout (only in case of videos) defines the length of the video that will be recorded.

Define a `cameraInUse` flag and set it to false by default. This flag ensures that the camera doesn't accept any further requests when taking pictures or recording a video. This is to prevent any consequent errors while loading the camera:

Now, define a function that will take a picture when called upon. This function takes callback as an argument and returns a success message when the picture is properly selected.

Note that `module.exports` is used to define the function, which will make this function available when `CameraModule.js` is included ( or imported) in other modules.

Before taking a picture, the code checks the value of the `cameraInUse` lag and starts the camera only if the flag is set to false. Once the camera starts taking photos, the flag is set to true so that no further requests are accepted for the camera until it is done clicking pictures.

Similarly, you will need to define a function that will record the video when called:

## Coding the Raspberry Pi Email Module

The email module is used to send email notifications whenever a trespasser enters the premises, along with evidence in the form of a video or photograph. To accomplish this task, use the npm module `nodemailer`. Download this by running the npm and installing the `nodemailer` command in the terminal as shown below. Check out the the [nodemailer npm module](https://www.npmjs.com/package/nodemailer) here.

![](https://www.survivingwithandroid.com/wp-content/uploads/2018/06/word-image-28.png)

> _Create a file with the name EmailModule.js and include the nodemailer module in it:_

Now, set the transport configuration for the email module by providing the details of the email service provider. The email ID from the email will be sent, along with its username and password:

Next, set the email options for sending the email with the video and photo as attachments:

  * `from :` This is the email address of the sender of the email
  * `to :` This is the email address of the email recipient
  * `subject:` This is the subject line of the email being sent
  * `Html:` This is the content of the email
  * `attachments:` This includes the following elements: 
    * `filename:` Here, you can set the name of the file that is sent as an attachment
    * `path:` This is the local file storage path from where the file will be picked for attachment

Here, the following are defined:

Similarly, you will need to define the email option for sending still photos, as shown in the following block of code:

Now, you will write functions that send the email whenever triggered:

## Coding the Raspberry Pi Sensor Module

Now, it's time to write the code for sensor modules, which will govern the functioning of all the sensors and LEDs. To accomplish this task, you need an npm module called `pigpio` , which gives access to the GPIO of the Raspberry Pi. To install the `pigpio` module, run the sudo npm, and install the `pigpio` command, check out the terminal shown below:

![](https://www.survivingwithandroid.com/wp-content/uploads/2018/06/word-image-29.png)

Check out the official npm link at <https://www.npmjs.com/package/pigpio> for more details about the `pigpio` module.

Create a file with the name `Survillance.js ` and include the `pigpio` module. Also, you will want to include `CameraModule.js` and `EmailModule.js` , which you developed just now. This will give access to the functions of each module for taking pictures, videos, and sending emails:

Make sure that `Survillance.js` , `EmailModule.js` , and `CameraModule.js` are placed in the same directory. Initialize the Raspberry Pi's pins for reading out and sending signals to sensors and LEDs:

The `PIR` sensor's output ( `PIR_out` ) is connected to GPIO 19, so declare GPIO 19 as the input and set the alert event flag to true. The alert event indicates that an alert event will be raised whenever the value at the GPIO changes from low (0) to high (1) or vice versa. You can listen to the alert event and take action accordingly.

The positive terminal of LED ( `red_LED` ) is connected to GPIO 17. The LED will work as an indicator. Whenever a trespasser is detected, the LED will glow. GPIO 17 is set as the `OUTPUT` pin.

The buzzer is connected to the Pi with one of its terminals connected to GPIO 26 and the other connected to the ground. The buzzer is used to raise an alarm when an intruder is detected, so set GPIO 26 as `OUTPUT` .

The infrared sensor's output ( `IR_out` ) is connected to GPIO 5, which is declared as the `INPUT` pin, and the alert event flag is set to true.

The trigger terminal of the ultrasonic sensor is used to generate high frequency ultrasonic waves. The trigger pin is connected to GPIO 16, so declare it as the `OUTPUT` pin.

The echo pin of the ultrasonic sensor is connected to GPIO 21. The echo pin is used to get the output of the ultrasonic sensor, so it is declared as `INPUT` and the alert event flag is set to true.

Make sure you initialize the LED to the low level (0):

First, write the code block to read the data of the `PIR` sensor:

Here, listen to the alert event for the `PIR` sensor. As soon as the `PIR` sensor detects any trespasser in the house, the output goes high from the initial low state, which causes an alert event to fire. The alert function returns a callback with two parameters -- one is level and the other one is tick. The level parameter indicates the state of the GPIO at that moment and tick is the timestamp at which the change in state is observed at the GPIO. So, the alert event is checked, and if the level is high (1), then the `takePicture` function of the camera module is called to click a photo of the trespasser immediately.

Then, the output of the buzzer and LED indicator are set to high and raise the alarm. Once the success callback is received from the camera module's `takePicture` function, the `sendMailPhoto` function of the email module is called. This sends the alert email along with the photo of the trespasser to the owner of the house.

Now, write the code for the ` IR` sensor, which is very similar to the `PIR` sensor code:

An `IR` sensor works in the exact same way as the `PIR` sensor. The only difference is that it records a video instead of taking a still photo.

Lastly, it's time to write the code block for the ultrasonic sensor module:

Making use of the trigger function of the `pigpio`module, a high-pulse is sent to the trigger pin of the ultrasonic sensor for 10 microseconds, which causes the sensor transmitter to emit a burst 8 high-frequency pulse that makes the output at the echo pin high.

The output of the ultrasonic sensor is taken from the `echo`pin on which you are listening for the alert event. As soon as the ultrasonic wave is transmitted, the state of the `echo` pin changes to high and the alert event is fired, which returns a callback with two parameters. The first is the level that is used to check whether the state of echo is high (1) or low (0). The other is tick, which is used to check the timestamp when the state changed.

The state of the `echo` is changed from low to high and this timestamp is saved as `startTick` . When the waves get reflected from obstruction and fall on the receiver, the state of the `echo` pin is changed from high to low. This timestamp is saved as `endTick` . Now, to get the distance of the obstruction from the sensor, you need to record the time taken by the ultrasonic waves to travel to and from the sensor-subtract `startTick` from `endTick` . The tick is the number of microseconds since the system boot. Its value is an unsigned 32-bit quantity. So, to get the correct value after subtraction, you need to use the right shift operator. Once you have the travel time, you can, then, calculate the distance.

Once you have the distance, check whether the distance is less than 10 cm. If it is, raise an alert by lighting the LED, beeping the Buzzer, taking a picture, and, finally, sending the alert through email.

The code part is finally completed. Now, execute the code by running the following command in the terminal:

This is the output for the ` PIR` sensor:

![](https://www.survivingwithandroid.com/wp-content/uploads/2018/06/word-image-30.png)

This is the output of the `IR` sensor:

![](https://www.survivingwithandroid.com/wp-content/uploads/2018/06/word-image-31.png)

This is the output of the ultrasonic sensor:

![](https://www.survivingwithandroid.com/wp-content/uploads/2018/06/word-image-9.jpeg)

The following is a snapshot of the email notification received as an alert:

![](https://www.survivingwithandroid.com/wp-content/uploads/2018/06/word-image-10.jpeg)
