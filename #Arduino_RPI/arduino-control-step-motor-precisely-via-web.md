# Arduino - Control Step Motor Precisely via Web

_Captured: 2019-01-11 at 20:50 from [www.hackster.io](https://www.hackster.io/iot_lover/arduino-control-step-motor-precisely-via-web-e35e47?utm_source=Hackster.io+newsletter&utm_campaign=8d8d00bfad-EMAIL_CAMPAIGN_2017_07_26_COPY_01&utm_medium=email&utm_term=0_6ff81e3e5b-8d8d00bfad-141949901&mc_cid=8d8d00bfad&mc_eid=1c68da4188)_

When user access webpage of PHPoC [WiFi] Shield from a web browser on smartphone or PC, a WebSocket connection will be created between Arduino and web browser. The WebSocket connection allows for the real-time exchange data between web browser and Arduino without reloading webpage.

When user rotates the plate on webpage, the rotated angle will be send to Arduino. Arduino convert angle to the equivalent number of steps, and then move step motor to the equivalent position.

**_Angle to the Number of Step Calculation_**

Assumption:

  * Angle per step: ANGLE_PER_STEP. This value is got from motor specification.
  * Angle per mirco-step: ANGLE_PER_MICRO_STEP = ANGLE_PER_STEP / MICRO_STEP_MODE

**=> the number of micro-step = angle / ANGLE_PER_MICRO_STEP**

The motor I used: ANGLE_PER_STEP = 1.8

The mocro-stepping mode I used in this code : MICRO_STEP_MODE = 32

  * Stack PHPoC Shield or PHPoC WiFi Shield on Arduino
  * Stack Stepper Motor Controller PES-2604 on PHPoC Shield or PHPoC WiFi Shield
  * Connect stepper motor to terminal block of Stepper Motor Controller PES-2605
  * Bipolar stepper motor
![](https://hackster.imgix.net/uploads/attachments/714073/2605_wiring_bipolar_step_motor.PNG?auto=compress%2Cformat&w=740&h=555&fit=max)

  * Unipolar stepper motor: there are two ways to connect a unipolar stepper motor to terminal block of PES-2605. User can choose one of them.
![](https://hackster.imgix.net/uploads/attachments/714074/2605_wiring_unipolar_step_motor.PNG?auto=compress%2Cformat&w=740&h=555&fit=max)

![](https://hackster.imgix.net/uploads/attachments/714075/image_760.jpg?auto=compress%2Cformat&w=740&h=555&fit=max)

**_Arduino Code_**

See code section

**_Web User Interface - remote_rotate.php_**

remote_rotate.php is a file that contains web user interface. It needs to be stored on PHPoC [WiFi] Shield. In order to upload the file to PHPoC [WiFi] Shield, please do the following steps:

**_The image used in web user interface_**

step_plate.png

![](https://hackster.imgix.net/uploads/attachments/714077/image_752.png?auto=compress%2Cformat&w=740&h=555&fit=max)

The image also needs to be uploaded to PHPoC [WiFi] Shield

  * Compile and upload code to Arduino
  * Upload web user interface to PHPoC [WiFi] shield
  * Open Serial monitor and copy IP address of PHPoC Shield
  * Access web user interface via web browser: http://**_ip_address_of_shield_**/remote_rotate.php
  * Control step motor via web
![](https://hackster.imgix.net/uploads/attachments/714078/image_753.png?auto=compress%2Cformat&w=740&h=555&fit=max)

![Arduino web step hardware nyxyk1dlcv](https://hackster.imgix.net/uploads/attachments/714081/arduino_web_step_hardware_NyXyk1dlCv.jpg)
