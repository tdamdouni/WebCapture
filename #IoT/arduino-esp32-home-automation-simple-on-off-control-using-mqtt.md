# Arduino: ESP32 Home automation (Simple On/Off control using MQTT)

_Captured: 2017-12-11 at 00:30 from [icircuit.net](http://icircuit.net/arduino-esp32-home-automation-simple-off-control-using-mqtt/2272)_

We have built a home automation system using NodeMCU [here](http://icircuit.net/ihome-internet-based-load-controlling-using-nodemcu/758). In this post we will try to replicate same system using ESP32. We will connect couple of LEDs to ESP32 and control those LEDs from a WebApp (The WebApp is integrated into this blog, scroll down to see!!).

![](http://icircuit.net/wp-content/uploads/2017/12/esp32_mqtt_led_on_off-1.jpeg)

## Environment requirements:

  * ESP32
  * Arduino libraries : PubSubClient,ArduinoJson (if you haven't already installed it , you can install it from Sketch->Include library->Manage Libraries)
  * [mqtt broker](http://icircuit.net/getting-started-with-mqtt-using-nodemcu/745) , if you don't have one you can use [eclipse Paho](https://iot.eclipse.org/getting-started#sandboxes) broker for experimentation (host: iot.eclipse.org , port : 1883, it is a free and open broker)
  * couple of LEDs and breadboard to see the output

## Solution Approach :

MQTT will be used to transport messages between ESP32 and client application. All the messages are JSON encoded.We already know how to connect ESP32 to Access point and MQTT broker from this [post](http://icircuit.net/arduino-getting-started-mqtt-using-esp32/2138). You can check this [post](https://techtutorialsx.com/2017/04/26/esp32-parsing-json/) by Nuno Santos to know more about parsing JSON messages using ArduinoJson library.

![ESP32 MQTT LED Control](http://icircuit.net/wp-content/uploads/2017/12/esp32_mqtt_home_automation.png)

> _ESP32 MQTT LED Control_

ESP32 will listen on the following channel for messages

_**/ic/ha/to/esp32/gpio/**_

Expected JSON message is format is as follows

`1`
`{``"switches"``:[{``"status"``:``false``,``"id"``:1,``"lable"``:``"GPIO 4"``},{``"status"``:``false``,``"id"``:2,``"lable"``:``"GPIO 5"``},{``"status"``:``false``,``"id"``:3,``"lable"``:``"GPIO 16"``},{``"status"``:``true``,``"id"``:4,``"lable"``:``"GPIO 17"``}]}`

we have an array called "switches", each item in this array is a switch with three fields. status indicates whether IO is high(true) or low(false). id is used to map each switch to GPIOs of the ESP32. We need to manipulate the status filed of respective switches to control it for example to make GPIO 4 HIGH and remaining all GPIOs low, we need to send following message on the MQTT channel

`1`
`{``"switches"``:[{``"status"``:``true``,``"id"``:1,``"lable"``:``"GPIO 4"``},{``"status"``:``false``,``"id"``:2,``"lable"``:``"GPIO 5"``},{``"status"``:``false``,``"id"``:3,``"lable"``:``"GPIO 16"``},{``"status"``:``false``,``"id"``:4,``"lable"``:``"GPIO 17"``}]}`

PubSub client default max message length is 128, since our message much bigger than that, we need to increase it to 1024. You can find the setting in PubSubClinet.h file (~\Documents\Arduino\libraries\pubsubclient\src). Remember to change it back to 128 once you are done with the testing (otherwise other arduino boards with lesser RAM may not work properly)

![Increasing MAX PACKET size of PUBSUB client](http://icircuit.net/wp-content/uploads/2017/12/pubsub_client_max_packet_size.png)

> _Increasing MAX PACKET size of PUBSUB client_

## Code:

First we will connect to given access point (change the ssid, password to connect to your network). By default ESP32 will connect to eclipse open mqtt broker. if you have MQTT broker change the mqtt_server,mqtt_port (if the broker is protected by user name and password you need to mention them in MQTT_USER, MQTT_PASSWORD). Once ESP is connected to network it will try to initiate connection with broker and subscribe to the channel "_/ic/ha/to/esp32/gpio/_". In main loop we have nothing much to do , we simply call loop method of pubsub client.

When a new message is received pubsub will call you callback method with channel name and message. we need to parse the received JSON and switch the GPIO accordingly.

#include <WiFi.h>

#include <PubSubClient.h>

#include <ArduinoJson.h>

// Update these with values suitable for your network.

const char* ssid = "SSID";

const char* password = "PASSWORD";

const char* mqtt_server = "iot.eclipse.org";

#define mqtt_port 1883

#define MQTT_USER "username"

#define MQTT_PASSWORD "password"

#define MQTT_SERIAL_PUBLISH_CH "/ic/ha/from/esp32/gpio/"

#define MQTT_SERIAL_RECEIVER_CH "/ic/ha/to/esp32/gpio/"

#define ID_MAP_LENGTH 5

WiFiClient wifiClient;

/*id - GPIO

* 1 - 4

* 2 - 5

* 3 - 16

* 4 - 17

*/

int iomap[ID_MAP_LENGTH]={0,4,5,16,17};

PubSubClient client(wifiClient);

void setup_wifi() {

delay(10);

// We start by connecting to a WiFi network

Serial.println();

Serial.print("Connecting to ");

Serial.println(ssid);

WiFi.begin(ssid, password);

while (WiFi.status() != WL_CONNECTED) {

delay(500);

Serial.print(".");

}

randomSeed(micros());

Serial.println("");

Serial.println("WiFi connected");

Serial.println("IP address: ");

Serial.println(WiFi.localIP());

}

void reconnect() {

// Loop until we're reconnected

while (!client.connected()) {

Serial.print("Attempting MQTT connection...");

// Create a random client ID

String clientId = "ESP32Client-";

clientId += String(random(0xffff), HEX);

// Attempt to connect

if (client.connect(clientId.c_str(),MQTT_USER,MQTT_PASSWORD)) {

Serial.println("connected");

//Once connected, publish an announcement...

client.publish("/icircuit/presence/ESP32/", "hello world");

// ... and resubscribe

client.subscribe(MQTT_SERIAL_RECEIVER_CH);

} else {

Serial.print("failed, rc=");

Serial.print(client.state());

Serial.println(" try again in 5 seconds");

// Wait 5 seconds before retrying

delay(5000);

}

}

}

void callback(char* topic, byte *payload, unsigned int length) {

//print recevied messages on the serial console

Serial.println("\-------new message from broker-----");

Serial.print("channel:");

Serial.println(topic);

Serial.print("data:"); 

Serial.write(payload, length);

Serial.println();

StaticJsonBuffer<500> jsonBuffer;

JsonObject& message = jsonBuffer.parseObject((char *)payload);

if (!message.success()) {

Serial.println("JSON parse failed"); 

return;

}

// loop through each switch and swith IO sate

JsonArray& switches=message["switches"];

int i=0,id,io_status;

for(i=0;i<switches.size();i++){

id=switches[i]["id"];

io_status=switches[i]["status"];

digitalWrite(iomap[id],io_status);

}

}

void setup() {

Serial.begin(115200);

Serial.setTimeout(500);// Set time out for 

int i=0;

for(i=0;i<ID_MAP_LENGTH;i++){

pinMode(iomap[i],OUTPUT);

}

setup_wifi();

client.setServer(mqtt_server, mqtt_port);

client.setCallback(callback);

reconnect();

}

void loop() {

client.loop();

}

## How To Test:

Connect LEDs to GPIO4,5,16,17 with a 4k7 resistor

![ESP32 MQTT LED On/Off](http://icircuit.net/wp-content/uploads/2017/12/esp32_mqtt_led_on_off-1.png)

> _ESP32 MQTT LED On/Off_

Copy the above code to Arduino IDE and Upload the code to ESP32 and open serial console. Console will show connected message if it is connected to MQTT broker (if it prints any error code, check you network, MQTT settings in the code)

![](http://icircuit.net/wp-content/uploads/2017/12/esp32_mqtt_led_on_off.png)

Now ESP32 is ready to receive messages from MQTT broker, click on "Connect" below (if you are using a different MQTT broker provide those details in the respective fields), you will see four buttons (if the button is in blue means OFF,green means ON). Click the button to control the LEDs.

---------------------------------------
