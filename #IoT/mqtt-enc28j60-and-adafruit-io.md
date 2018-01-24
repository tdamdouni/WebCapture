# MQTT – enc28j60 and Adafruit IO

_Captured: 2017-12-04 at 13:36 from [www.lucadentella.it](http://www.lucadentella.it/en/2016/11/19/mqtt-enc28j60-e-adafruit-io/)_

[Adafruit IO](https://io.adafruit.com/) is the new cloud platform (at the moment still in _beta_) by Adafruit, designed to allow simple data connections using standard APIs and web-based _dashboards_.

This new platform exposes [MQTT APIs](https://learn.adafruit.com/adafruit-io/mqtt-api), you can therefore apply what you learned in my [previous posts](http://www.lucadentella.it/en/category/mqtt/) to create a complete project that takes advantage of all its features.

#### The project

Goal of the project is to connect the Arduino to a _dashboard_ hosted on Adafruit IO:

  * Arduino reads the room temperature (thanks to the DHT11 sensor already used in a [previous tutorial](http://www.lucadentella.it/en/2016/11/02/mqtt-enc28j60-e-arduino-22/)) and sends its value every t seconds to Adafruit IO
  * Arduino is also able, using an external _relay_ module, to turn on/off an heater
  * The _dashboard_ on Adafruit IO displays the temperature values on a chart and has a toggle button to turn the heater connected to the Arduino on and off
![mqtt-io1](http://www.lucadentella.it/blog/wp-content/uploads/2016/11/mqtt-io1.jpg)

#### Adafruit IO

Let's see how to create the _dashboard_ using Adafruit IO.

First, you need to subscribe to the _open beta _program using the button on the official website [https://io.adafruit.com](https://io.adafruit.com/):

![io-01](http://www.lucadentella.it/blog/wp-content/uploads/2016/11/io-01.jpg)

After having logged in with your Adafruit account (or having created a new account) you'll be redirected to the default _dashboard_.

Click on **My dashboards**:

![io-02](http://www.lucadentella.it/blog/wp-content/uploads/2016/11/io-02.jpg)

> _next click on Create dashboard:_

![io-03](http://www.lucadentella.it/blog/wp-content/uploads/2016/11/io-03.jpg)

> _give a name to the new dashboard, then click on Create dashboard:_

![io-04](http://www.lucadentella.it/blog/wp-content/uploads/2016/11/io-04.jpg)

you'll see a completely empty _dashboard_. To add new elements (charts, buttons…) click on **Create a new block**:

![io-05](http://www.lucadentella.it/blog/wp-content/uploads/2016/11/io-05.jpg)

choose **line chart** among the available elements and click on **Create**:

![io-06](http://www.lucadentella.it/blog/wp-content/uploads/2016/11/io-06.jpg)

you have to link the chart to a _feed _(= topic, in the MQTT language). Create a new _feed_ named **temperature**:

![io-07](http://www.lucadentella.it/blog/wp-content/uploads/2016/11/io-07.jpg)

> _once created, you can link it to the chart (choose), then click on next step:_

![io-08](http://www.lucadentella.it/blog/wp-content/uploads/2016/11/io-08.jpg)

you can change some chart settings (for example type **°C** as y-axis label), then complete the wizard with **create block**:

![io-10](http://www.lucadentella.it/blog/wp-content/uploads/2016/11/io-10.jpg)

You'll see a new block in your _dashboard _that represents the chart, empty for the moment. Using the _drag'n'drop_ you can move the block in the page or resize it.

Now add the toggle button, again using **Create a new block**:

![io-20](http://www.lucadentella.it/blog/wp-content/uploads/2016/11/io-20.jpg)

> _create a new feed named control:_

![io-21](http://www.lucadentella.it/blog/wp-content/uploads/2016/11/io-21.jpg)

and link it to the button:

![io-22](http://www.lucadentella.it/blog/wp-content/uploads/2016/11/io-22.jpg)

> _give a label to the button and to the two possible values, then create the new block:_

![io-23](http://www.lucadentella.it/blog/wp-content/uploads/2016/11/io-23.jpg)

> _Your dashboard is now complete!_

#### Feeds, topics and MQTT APIs

As explained above, each element of your _dashboard _can be linked to one or more _feeds_, that are data flows. For example you linked to the chart a _feed_ named **temperature**, while the button is linked to another one named **control**.

If you use the MQTT APIs, each _feed_ corresponds to a **topic** named as it follows:
    
    
    <username>/f/<feedname>

where **username** is the name of your Adafruit account.

Hence, my two _feeds_ correspond to the following two topics:

  * lucadentella/f/temperature
  * lucadentella/f/control

To connect to the Adafruit's MQTT _broker_ (address **io.adafruit.com**) you need to specify a username and a password.

The username is the name of your Adafruit account (**lucadentella** for me), while the password is your **Adafruit IO key**, that can be retrieved using a button in the _dashboard_:

![io-31](http://www.lucadentella.it/blog/wp-content/uploads/2016/11/io-31.jpg)

![io-32](http://www.lucadentella.it/blog/wp-content/uploads/2016/11/io-32.jpg)

You can test your dashboard using the **mosquitto_sub** command to subscribe to the topic linked to the toggle button. Every time you click on the button, the _dashboard_ sends to that topic a message with the actual status of the button (ON or OFF):
    
    
    mosquitto_sub.exe -h io.adafruit.com -u <username> -P <AIOkey> -t <username>/f/control

![io-33](http://www.lucadentella.it/blog/wp-content/uploads/2016/11/io-33.jpg)

#### Arduino

The _sketch _for Arduino is available in my [Github repository](https://github.com/lucadentella/enc28j60_tutorial/tree/master/_21_AdafruitIO).

First, some constants are defined: the parameters for the Adafruit IO service (username, password, topics…) and the PINs the DHT11 sensor and the relay are connected to:
    
    
    #define CLIENT_ID       "ArduinoMQTT"
    #define USERNAME        "adafruit_username"
    #define PASSWORD        "adafruit_io_key"
    #define PUB_TOPIC       "username/f/temperature"
    #define SUB_TOPIC       "username/f/control"
    #define PUBLISH_DELAY   5000
    #define DHTPIN          3
    #define DHTTYPE         DHT11
    #define RELAY_PIN       6

In the** setup()**, the MQTT client is configured. Unlike the previous example, this time I also define the **callback function** that is called every time the client receives a new message from a topic that was subscribed:
    
    
    // setup mqtt client
    mqttClient.setClient(ethClient);
    mqttClient.setServer("io.adafruit.com", 1883);
    mqttClient.setCallback(mqttCallback);

Indeed, when the _sketch_ connects to the _broker _it subscribes the topic linked to the button in the _dashboard_ to be notified when a user clicks on it:
    
    
    void mqttConnect() {
     
      while(!mqttClient.connected()) {
     
        if(mqttClient.connect(CLIENT_ID, USERNAME, PASSWORD)) {
     
          Serial.println(F("MQTT client connected"));
          mqttClient.subscribe(SUB_TOPIC);
          Serial.println(F("Topic subscribed"));
        } else {
          Serial.println(F("Unable to connect, retry in 5 seconds"));
          delay(5000);
        }
      }
    }

The _callback_ function checks if the message received is ON or OFF and changes the relay status accordingly:
    
    
    void mqttCallback(char* topic, byte* payload, unsigned int length) {
     
      if(strncmp((const char*)payload, "ON", 2) == 0) {
        Serial.println("ON message received, turning relay ON");
        digitalWrite(RELAY_PIN, HIGH);
      } else {
        Serial.println("OFF message received, turning relay OFF");
        digitalWrite(RELAY_PIN, LOW);
      }
    }

The following video shows the project in action:
