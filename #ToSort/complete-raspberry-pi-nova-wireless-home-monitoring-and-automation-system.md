# Complete Raspberry Pi / Nova Wireless Home Monitoring and Automation System ...

_Captured: 2017-11-23 at 21:40 from [www.instructables.com](http://www.instructables.com/id/Complete-Raspberry-Pi-Nova-Wireless-Home-Monitorin/)_

![](https://cdn.instructables.com/FSV/04RQ/J9OWBW08/FSV04RQJ9OWBW08.MEDIUM.jpg)

![](https://cdn.instructables.com/FTG/LDB0/JA8J9J59/FTGLDB0JA8J9J59.MEDIUM.jpg)

The Raspberry Pi is an awesome little device ..I will show how you can have a complete stand alone wireless Security / Home Automation System on One device ..We will be installing  
OpenHab [ http://openhab.org](http://openhab.org)  
Node Red modules http: node Red.org  
ParticlePi program [ http://particle.io](http://particle.io)  
Tying them all together seamlessly and adding Particles as wireless sensor inputs and controls  
We will make our own PCBs and solder them up   
We will make   
Wireless Sensor shields  
Wireless Relay shields   
Screw shields (For the ParticlePi)   
We will wire them up program them and showcase the final product.

Another Note : Comment ( // ) out the Alarm activation and reporting until you leave the house ..Re-Flash uncommented program when you leave.. When the monitoring swings back around it will shut off when there is no motion ..Or use Alarm Switch as demonstrated

## Step 1: The Raspberry Pi 0

![](https://cdn.instructables.com/F4U/9TJW/J9SVXR47/F4U9TJWJ9SVXR47.MEDIUM.jpg)

![](https://cdn.instructables.com/FWE/YEYK/J9SVXR59/FWEYEYKJ9SVXR59.SMALL.jpg)

![](https://cdn.instructables.com/FAG/O8NP/J9SVXR74/FAGO8NPJ9SVXR74.SMALL.jpg)

![](https://cdn.instructables.com/FHI/H7YT/JA8J9J35/FHIH7YTJA8J9J35.SMALL.jpg)

![](https://cdn.instructables.com/FNS/0R74/JA36M1CF/FNS0R74JA36M1CF.SMALL.jpg)

![](https://cdn.instructables.com/FYC/YM62/JA36M1AM/FYCYM62JA36M1AM.SMALL.jpg)

This is a beautiful little computer ..I'll solder on the headers and then add the ParticlePishield

## Step 2: Hologram Nova Wireless IOT

![](https://cdn.instructables.com/F63/JO3P/J9SW4GZ0/F63JO3PJ9SW4GZ0.MEDIUM.jpg)

![](https://cdn.instructables.com/FB2/D7SH/J9SW4H0D/FB2D7SHJ9SW4H0D.MEDIUM.jpg)

![](https://cdn.instructables.com/FVJ/NLR6/JA8J9JB9/FVJNLR6JA8J9JB9.SMALL.jpg)

![](https://cdn.instructables.com/FSK/FEF3/JA36JNXB/FSKFEF3JA36JNXB.SMALL.jpg)

![](https://cdn.instructables.com/FCX/LCZ9/JA36JNXA/FCXLCZ9JA36JNXA.SMALL.jpg)

![](https://cdn.instructables.com/FKO/0KUB/JA36LZPB/FKO0KUBJA36LZPB.SMALL.jpg)

The link to the Hologram site is here

<https://hologram.io>

The Hologram Nova is a new connectivity platform for the IOT world and the Raspberry Pi ..It is configured by Linux but it is a great learning platform. I am going to use it as an alarm transmitter for Temperatures, Motion , Smoke Alarms and any important notifications.

Instructions on how to get your Hologram Nova talking to your Raspberry Pi are here.

Here is my setup for sending Messages to the Hologram IDE and Having it emailed to myself..The above pictures are of my emails

All you really need is to install the Node Red Particle node and a node called Exec configure as shown and you will get emailed notifications when your particle publish is sent

## Step 3: The Particle Photon 

![](https://cdn.instructables.com/FYK/5L0S/J9SVXRRA/FYK5L0SJ9SVXRRA.MEDIUM.jpg)

![](https://cdn.instructables.com/F2P/VWJ7/J9SVXRSQ/F2PVWJ7J9SVXRSQ.MEDIUM.jpg)

This is a pretty nifty device for connecting all your homes devices ..For $19 US they are a really good deal ..I generally hate using jumper wires and breadboards for anything so I developed boards for just about everything including the Particle..

it can be Purchased here

## Step 4: Particle PI Program & Screw Shield

![](https://cdn.instructables.com/F78/0Y6Q/J9SVZ1LB/F780Y6QJ9SVZ1LB.MEDIUM.jpg)

![](https://cdn.instructables.com/FNK/65J6/JA1TYHBS/FNK65J6JA1TYHBS.MEDIUM.jpg)

The Particle Pi shield I developed a long time ago it includes labeling for the Raspberry pi as well as the particlePi pinouts that the program uses ..It works pretty good and enables me to us screw terminals as opposed to little insert-able pins which bug me when they come out //

the Link for installing the Particle Pi program is here

It is a full install to do from opening up your raspberry to installing the raspian program to full particle pi install

what the Particle pi allows me to do is to use it like a particle and remote program it with io's and specialized sensors..

## Step 5: The Relay Board

![](https://cdn.instructables.com/F44/MUKE/J9OWBX9C/F44MUKEJ9OWBX9C.MEDIUM.jpg)

![](https://cdn.instructables.com/FG0/BB6Q/J9OWBWLS/FG0BB6QJ9OWBWLS.SMALL.jpg)

![](https://cdn.instructables.com/F7P/WS0T/J9YJ7EGL/F7PWS0TJ9YJ7EGL.MEDIUM.jpg)

![](https://cdn.instructables.com/FPH/616S/J9OWBWDP/FPH616SJ9OWBWDP.SMALL.jpg)

![](https://cdn.instructables.com/FBK/ENUX/J9OWBX28/FBKENUXJ9OWBX28.SMALL.jpg)

The 12 volt relay board can be used as a garage door opener, you can turn your hot tub on and off by integrating a relay into it ..Diagram above ..You can also turn heating on and off as well, and larger loads.

You really don't even need to Program it you can use the Particle App and just use the tinker to turn stuff off and on.. But we are getting more complicated than that..

## Step 6: The Motion Sensors

![](https://cdn.instructables.com/F0G/ALNO/J9SVYZSE/F0GALNOJ9SVYZSE.MEDIUM.jpg)

![](https://cdn.instructables.com/F38/GMLM/J9SVZ08N/F38GMLMJ9SVZ08N.SMALL.jpg)

![](https://cdn.instructables.com/FB2/A3TP/J9SVZ0A1/FB2A3TPJ9SVZ0A1.SMALL.jpg)

![](https://cdn.instructables.com/F4V/DA2S/JA36RWRV/F4VDA2SJA36RWRV.SMALL.jpg)

These sensors are available off of amazon and come in many configurations and are wired with a 4 wire #18 guage security wire ..as we need +12VDC and 3.3VDC a ground and a return alarm circuit. Please see picture 1 the Return Wire is wired to the common of the Switch circuit so the input yellow gets either 3.3 volts(NC state no motion and 0 Ground state Motion Detected ) Driving the input to ground is necessary to make the input to definitely change state quickly ...the Ground is common to both the 12 and 3.3 circuit so its ok to jumper it over to the switch ..If the grounds were not common(different power supplying 12VDC then it wouldn't be a good idea..as you could get a difference of potential(BAD)..or it wouldn't be a dependable state change..

## Step 7: Temperature Sensors

![](https://cdn.instructables.com/FBI/DZNR/J9OWBWO9/FBIDZNRJ9OWBWO9.MEDIUM.jpg)

![](https://cdn.instructables.com/FRI/L372/J9OWBVZY/FRIL372J9OWBVZY.MEDIUM.jpg)

I am partial to the DS18B temperature sensor ..They are dependable and last a very long time and come prewired in a kit so installing them in the real world is a lot easier..Special note if you don't use the supplied shield you need to use a 10K resistor between the +3.3 and the yellow data wire ..The same goes for the DHT22 a 10K resistor is required (if you don't they may melt)

## Step 8: The Security Board

![](https://cdn.instructables.com/F1H/4C15/J9OWBX63/F1H4C15J9OWBX63.MEDIUM.jpg)

![](https://cdn.instructables.com/FC3/YLAE/J9OWBWZ8/FC3YLAEJ9OWBWZ8.MEDIUM.jpg)

![](https://cdn.instructables.com/F1B/D01Q/JA36M170/F1BD01QJA36M170.SMALL.jpg)

For the Main Control Board that sits in the Control Cabinet. I have included a gerber File for the enthusiast that doesn't want to go through the hassle of doing a total design work up.  
I have 3 relays designed into the Board.

1-can be used for an alarm Bell

1-can be used for turning on and off the solenoid

1-can be used for turning heating or Air conditioning on and off.

The Raspberry Pi Zero can be soldered into place in the spots provided to get power from the Board or you can use a header .. It utilizes a 18-24 volt AC input and has a 12 Volt and 5 volt power supply for your devices..

A particle Photon or electron can be used.. The Electron has more io points but is Cellular and can cost more in Data but is more dependable as it has a battery input for redundancy.

## Step 9: Install the OpenHab Programand the Openable App

![](https://cdn.instructables.com/FXG/DV8F/J9OWBWNS/FXGDV8FJ9OWBWNS.MEDIUM.jpg)

![](https://cdn.instructables.com/FB2/2PF6/J9OWBWOU/FB22PF6J9OWBWOU.SMALL.jpg)

![](https://cdn.instructables.com/FQG/O43D/J9SVXSIS/FQGO43DJ9SVXSIS.MEDIUM.jpg)

![](https://cdn.instructables.com/F73/ZE60/J9SVXSE2/F73ZE60J9SVXSE2.SMALL.jpg)

![](https://cdn.instructables.com/FEY/23UL/J9SVXSV5/FEY23ULJ9SVXSV5.SMALL.jpg)

![](https://cdn.instructables.com/FNL/5CXY/J9SVXSXG/FNL5CXYJ9SVXSXG.SMALL.jpg)

The Following Links will get you started as well  
[http://www.makeuseof.com/tag/getting-started-openh...](http://www.makeuseof.com/tag/getting-started-openhab-home-automation-raspberry-pi/)  
[http://www.makeuseof.com/tag/openhab-beginners-gui...](http://www.makeuseof.com/tag/openhab-beginners-guide-part-2-zwave-mqtt-rules-charting/)  
Http://homeautomationforgeeks.com

Installing the Openhab program on the Raspberry Pi is SUPER EASY follow these steps

Go to

Right Click on the Download Button on the Run Time 1.8.3 (Copy Link)

ssh into your Raspberry Pi from another computer or just open the command prompt you can get a good program called Putty here its for SSH'ing into devices like the Pi

type in

sudo mkdir /opt/openhab

"press enter"

then

cd /opt/openhab

"press enter"

once your in the file location type in

"press enter"then

type in

ls

you will see the file ..copy that file name(easier than typing it in)

sudo unzip (paste in file name) press enter

then type in

sudo rm -r (paste in file name again)

then type in

ls

You will see all the files there

then type in

sudo mkdir addons_repo

then go to that file

cd addons_repo

then type in

sudo wget [https://bintray.com/openhab/mvn/download_file?file...](https://bintray.com/openhab/mvn/download_file?file_path=org%2Fopenhab%2Fdistro%2Fopenhab%2F1.10.0%2Fopenhab-1.10.0-addons.zip) (this will take a while)

ls  
you will see the file ..copy that file name(easier than typing it in)

sudo unzip (paste in file name)

press enter then type in

sudo rm -r (paste in file name again)

then type in

ls

you will see all the addons in this file you don't install them in the addons folder because the program takes 20 minutes to start if you do ..

ok now you need to copy a couple of things over to the addons file, to do this type in

sudo cp org.openhab.persistence.mqtt-1.10.0.jar /opt/openhab/addons

you need these addons copy past and enter each time

sudo cp org.openhab.action.mqtt-1.10.0.jar /opt/openhab/addons

sudo cp org.openhab.binding.mqtt-1.10.0.jar /opt/openhab/addons

sudo cp org.openhab.persistence.rrd4j-1.10.0.jar /opt/openhab/addons

Ok now that the program is installed (ish)

now comes the fun part

there are tutorials and help in doing some programming but I will paste in what I have to get you started

type

cd ..

include the two dots that takes you back one level

if you typed in cd just type in

cd /opt/openhab

that'll get you back

now type in

cd configurations

then type in ls to see all the files your going to play with

now type in

sudo nano openhab_default.cfg

that gets you into the default configurations folder

type "Ctrl" w (control Button) that's basically "where is".. its a big file

type in mqtt in the upper filed

do it once scroll down.. **You have to use arrow keys to navigate here** 10 lines ish then again "Ctrl"w then up arrow

you will see MQTT Transport

there are a few things to change here

make the changes as below

# Define your MQTT broker connections here for use in the MQTT Binding or MQTT

# # URL to the MQTT broker, e.g. tcp://localhost:1883 or ssl://localhost:8883 ((((mqtt:mymosquitto.url=tcp://localhost:1883))))) This is what you change it to without brackets

then (Ctrl) o that's a save as .. then change the file name to openhab.cfg "enter" then your done (Ctrl)x "enter"

now type in

cd items

that takes you to the items folder then paste in the following

sudo nano default.items

"enter"

then look at the attached notepads ..there is an items file copy paste the whole thing in there

"Ctrl"o  
to save ..then type

"Ctrl"x

to exit

type

cd .. (go back one space)

cd sitemaps

sudo nano default.sitemap

paste in all the files in the sitemaps folder from sitemaps notepads

"Ctrl"o  
to save ..then type "Ctrl"x to exit

**T****here are some dependencies to install like MQTT the instructions to install it are here as well as a full instruction set on installing openhab ..**

**you need to install it before you start the program ..**

once you have done everything I posted and followed the instructions in the [ http://homeautomationforgeeks.com ](http://homeautomationforgeeks.com) site ..Please do what I posted then go back and follow that they say in the site as well ..There are some addons you need to copy over to the addons folder as well as some other small things like starting automatically and shortcuts etc..

type

cd /opt/openhab

then sudo ./start.sh

then go to your browser and type in the ip address of the pi:8080 the program should show you some stuff if you don't have the Node Red set up yet and the particles you wont see much happening but it'll look nice..

## Step 10: Node Red Program & Special Notes

![](https://cdn.instructables.com/FY2/B7V0/J9SVXTU2/FY2B7V0J9SVXTU2.MEDIUM.jpg)

![](https://cdn.instructables.com/FWE/7JTG/J9SVXTZU/FWE7JTGJ9SVXTZU.MEDIUM.jpg)

![](https://cdn.instructables.com/FQX/O6N1/JA2TMKV2/FQXO6N1JA2TMKV2.SMALL.jpg)

![](https://cdn.instructables.com/FNY/F08P/JA2TMKVA/FNYF08PJA2TMKVA.SMALL.jpg)

![](https://cdn.instructables.com/F2Y/BXJB/JA2TMKVF/F2YBXJBJA2TMKVF.SMALL.jpg)

## Step 11: DIY Water Leak Sensor Board

![](https://cdn.instructables.com/FGM/LNAA/J9SVZ3XB/FGMLNAAJ9SVZ3XB.MEDIUM.jpg)

![](https://cdn.instructables.com/F7Z/QA5H/J9SVZ3R5/F7ZQA5HJ9SVZ3R5.MEDIUM.jpg)

![](https://cdn.instructables.com/FVV/6XY3/J9SVZ3PZ/FVV6XY3J9SVZ3PZ.SMALL.jpg)

![](https://cdn.instructables.com/FRS/AB75/J9SVZ3TV/FRSAB75J9SVZ3TV.SMALL.jpg)

![](https://cdn.instructables.com/FQD/OFVG/J9OWBWLT/FQDOFVGJ9OWBWLT.SMALL.jpg)

![](https://cdn.instructables.com/FJI/710Z/J9OWBWIQ/FJI710ZJ9OWBWIQ.SMALL.jpg)

## Step 12: Particle Security Program

![](https://cdn.instructables.com/FDR/6M7W/J9SVXSMH/FDR6M7WJ9SVXSMH.MEDIUM.jpg)

![](https://cdn.instructables.com/FOK/5CVI/J9SVXSGM/FOK5CVIJ9SVXSGM.SMALL.jpg)

![](https://cdn.instructables.com/F6W/4GCN/J9SVXSL0/F6W4GCNJ9SVXSL0.SMALL.jpg)

below is the link to a clean security program I will paste in the code with descriptions as well for learning purposes

// This #include statement was automatically added by the Particle IDE.

#include <Adafruit_DHT.h>

#include <onewire.h>

#include "DS18.h"//Note this is added when you search the library for onewire..(add to sketch)

#define DHTTYPE DHT11 // Sensor type DHT11/21/22/AM2301/AM2302

#define DHTPIN D0 // Digital pin for communications

DHT dht(DHTPIN, DHTTYPE);

DS18 sensor(D1);

DS18 sensor1(D2);

DS18 sensor2(D3);

int n; // counter

int RelayPin1 = D6; //Relay 1(Underside Heat On)

int RelayPin2 = D5; //Relay 2(Alarm Bell)

int RelayPin3 = D7; //Relay 3(Heat On)

int digitalin2 = A2; //Office Motion

int digitalin4 = A3; //Living Motion

int digitalin3 = A4; //Kitchen Motion

int digitalin1 = A1; //Bed Motion

int digitalin5 = A0; //Office Thermostat

int Smoke = A1; //Smoke Detector

int sensorValue = 0;

void setup() {

Serial.begin(9600);

dht.begin();

digitalWrite(RelayPin1,LOW);

digitalWrite(RelayPin2,LOW);

digitalWrite(RelayPin3,LOW);

pinMode(RelayPin1, OUTPUT); //Alarm relay

pinMode(RelayPin2, OUTPUT); //Heating relay

pinMode(RelayPin3, OUTPUT); //Water Shut off relay

pinMode(digitalin1, INPUT);

pinMode(digitalin2, INPUT);

pinMode(digitalin3, INPUT);

pinMode(digitalin4, INPUT);

pinMode(digitalin5, INPUT);

pinMode(Smoke, INPUT);

Particle.function("Heating", HeatOn);

Particle.function("Heating1", HeatOn1);

Particle.function("Alarm", AlarmOn);

}

void loop() {

char message[56];

//**************DHT Sensor************************

float h = dht.getHumidity();

float t = dht.getTempCelcius();

float f = dht.getTempFarenheit();

if (isnan(h) || isnan(t) || isnan(f)) {

Serial.println("Failed to read from DHT sensor!");

Particle.publish("Failed to read from DHT sensor!","0",PRIVATE);

return;

}

float hi = dht.getHeatIndex();

float dp = dht.getDewPoint();

float k = dht.getTempKelvin();

Serial.print(h);

Serial.print(t);

sensorValue =(t);

sprintf(message, "%d",sensorValue);

Particle.publish("Bath_Temp", message, PRIVATE);

sensorValue =(h);

sprintf(message, "%d",sensorValue);

Particle.publish("Bath_Hum", message, PRIVATE); delay(100000);

//********************Security PIR input section*******************************88

sensorValue = digitalRead(digitalin1);//Bed Motion

if (sensorValue == LOW) { Particle.publish("OffMot","0",PRIVATE);

digitalWrite(RelayPin1,HIGH);//*****Uncomment to turn Alarm System On)****

}

else if (sensorValue == HIGH) {

Particle.publish("OffMot","1",PRIVATE); //Particle publish sensed by node red sent on to Openhab as MQTT

}

sensorValue = digitalRead(digitalin2); //Kitchen Motion

if (sensorValue == LOW) {

Particle.publish("BedMot","0",PRIVATE);

digitalWrite(RelayPin1,HIGH);//*****Uncomment to turn Alarm System On)****

}

else if (sensorValue == HIGH) {

Particle.publish("BedMot","1",PRIVATE);

}

sensorValue = digitalRead(digitalin4); //Living Motion

if (sensorValue == LOW) {

Particle.publish("LivingMot","0",PRIVATE);

digitalWrite(RelayPin1,HIGH);//*****Uncomment to turn Alarm System On)****

}

else if (sensorValue == HIGH) {

Particle.publish("LivingMot","1",PRIVATE);

}

sensorValue = digitalRead(digitalin3); //Office Motion

if (sensorValue == LOW) {

Particle.publish("KitMot","0",PRIVATE);

digitalWrite(RelayPin1,HIGH);//*****Uncomment to turn Alarm System On)****

}

else if (sensorValue == HIGH) { Particle.publish("KitMot","1",PRIVATE);

}

sensorValue = digitalRead(Smoke); //Smoke Detector

if (sensorValue == LOW) {

digitalWrite(RelayPin1,HIGH);//(*****Uncommented to turn Alarm On in Case of Fire)****

Particle.publish("Smoke","1",PRIVATE);

}

else if (sensorValue == HIGH) {

Particle.publish("Smoke","0",PRIVATE);

}

sensorValue = digitalRead(digitalin5); //Thermostat

if (sensorValue == HIGH) {

digitalWrite(RelayPin1,HIGH);

Particle.publish("Thermostat","1",PRIVATE);

}

else if (sensorValue == LOW) {

Particle.publish("Thermostat","0",PRIVATE);

}

sensorValue = digitalRead(D6); //Relay 1(Under Heat)

if (sensorValue == HIGH) {

Particle.publish("Alarm_On","1");

}

else if (sensorValue == LOW) { //do nothing

}

sensorValue = digitalRead(D5); //Relay 2(Alarm)

if (sensorValue == HIGH) {

Particle.publish("Underside_Heating_On","1");

}

else if (sensorValue == LOW) {

Particle.publish("Underside_Heating_Off","0");

sensorValue = digitalRead(D7); //Relay 3(BaseBoardHeat)

if (sensorValue == HIGH) {

Particle.publish("BaseHeat_On","1");

}

else if (sensorValue == LOW) {

Particle.publish("BaseHeat_Off","1");

}

}

if (sensor.read()) { // Do something cool with the temperature

Serial.printf("Temperature %.2f C %.2f F ", sensor.celsius(), sensor.fahrenheit());

Particle.publish("Bed_Temp", String(sensor.celsius()), PRIVATE);

}

if (sensor1.read()) {

Serial.printf("Temperature %.2f C %.2f F ", sensor.celsius(), sensor.fahrenheit());

Particle.publish("Living_Temp", String(sensor.celsius()), PRIVATE);

}

else {

if (sensor.searchDone()) {

}

}

delay(100000);

}

int HeatOn(String command) { //(((This is your Function commands from Openhab switches to Node-red to here))))

if(command =="1") {

digitalWrite(D7,HIGH);

Particle.publish("Base_Heat_On","1",PRIVATE);

}

if(command =="0") {

digitalWrite(D7,LOW);

Particle.publish("Base_Heat_Off","0",PRIVATE);

}

return 1 ;

}

int HeatOn1(String command) { //(((This is your Function commands from Openhab switches to Node-red to here))))

if(command =="1") {

digitalWrite(D6,HIGH); Particle.publish("Under_Heat_On","1",PRIVATE);

}

if(command =="0") {

digitalWrite(D6,LOW);

Particle.publish("Under_Heat_OFF","0",PRIVATE);

}

return 1 ;

}

int AlarmOn(String command) { //(((This is your Function commands from Openhab switches to Node-red to here))))

if(command =="1") {

digitalWrite(D5,HIGH);

Particle.publish("Alarm_On","1",PRIVATE);

}

if(command =="0") {

digitalWrite(D5,LOW);

Particle.publish("Alarm_OFF","0",PRIVATE);

}

return 1 ;

## Step 13: Particle Relay Program

![](https://cdn.instructables.com/FDR/87BU/JA36JPIZ/FDR87BUJA36JPIZ.MEDIUM.jpg)

The Particle Relay Shield is here ..It is really simple and can either be used with the Openhab App and program or as a stand alone device for Just using the Tinker app ..

///Note is in Libraries just do a search "DS18.h" is included in the library  
#include

#include "DS18.h"

DS18 sensor(D0);

int Relay1(D1); i

nt sensorValue = 0;

void setup() {

Serial.begin(9600);

pinMode(Relay1, OUTPUT);

Particle.function("Relay1", Activate); }

void loop() {

char message[120];

sensorValue = digitalRead(Relay1); //Relay 1

if (sensorValue == HIGH) {

Particle.publish("Relay1","1");

} else if (sensorValue == LOW) {

Particle.publish("Relay1","0");

if (sensor.read()) {

Serial.printf("Temperature %.2f C %.2f F ", sensor.celsius(), sensor.fahrenheit()); Particle.publish("Temperature", String(sensor.celsius()), PRIVATE);//You can adjust ("Temperature") to say what you want

}

else

{

if (sensor.searchDone()) {

Serial.println("No more addresses.");

delay(2500); }

}

}

}

}

int Activate(String command) {

if(command =="1") { digitalWrite(D1,HIGH);

Particle.publish("D1_HIGH", "1",PRIVATE);

delay(20000);

digitalWrite(D1,LOW);

Particle.publish("D3_Reset", "0",PRIVATE);

}

return 1 ;

}

## Step 14: Adding a Security Camera and an Audible Alarm System

![](https://cdn.instructables.com/FD3/1F59/JA7HZQM9/FD31F59JA7HZQM9.MEDIUM.jpg)

![](https://cdn.instructables.com/F18/ZVN5/JA7HZQRZ/F18ZVN5JA7HZQRZ.MEDIUM.jpg)

![](https://cdn.instructables.com/FWQ/H9AH/JA7HZR64/FWQH9AHJA7HZR64.SMALL.jpg)

![](https://cdn.instructables.com/FDC/ZVD7/JA8J9IOZ/FDCZVD7JA8J9IOZ.SMALL.jpg)

![](https://cdn.instructables.com/FWJ/3F4H/JA8J9IMC/FWJ3F4HJA8J9IMC.SMALL.jpg)

## Step 15: Fritzing Files and Program to Make Your Own PCBs 

## Step 16: In Operation 
