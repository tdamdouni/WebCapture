# MQTT, Adafruit IO & You!

_Captured: 2018-01-07 at 20:25 from [learn.adafruit.com](https://learn.adafruit.com/mqtt-adafruit-io-and-you?view=all)_

![adafruit_io_1946-04.jpg](https://cdn-learn.adafruit.com/assets/assets/000/028/180/large1024/adafruit_io_1946-04.jpg?1445539648)

So you have a "Thing" that you want to connect to the the "Internet of". How do you do that technical 'connection' part?

![adafruit_io_howtocomm.png](https://cdn-learn.adafruit.com/assets/assets/000/029/740/large1024/adafruit_io_howtocomm.png?1452825020)

> _If its a toaster, you could plug it into Ethernet and then run a cable to your router._

![adafruit_io_ethernet.png](https://cdn-learn.adafruit.com/assets/assets/000/029/739/large1024/adafruit_io_ethernet.png?1452824915)

But many things are wireless, so no Ethernet. Instead, they might use wireless protocols like **WiFi** (just about everything that stays in a home or business),** Bluetooth classic** (older, pre-BLE devices),** Bluetooth LE** (wireless lightbulbs, any things that connect to your cellphone),** ZigBee, 802.15.4** (mesh networks, sensor nets),** Cellular **(e.g. vending machines, geotracking for cars, Kindles) etc..

![adafruit_io_tower.png](https://cdn-learn.adafruit.com/assets/assets/000/029/735/large1024/adafruit_io_tower.png?1452824451)

The upshot is - while _some _devices are wired, there's a ton that are wireless. And honestly, wireless is pretty fun! **BUT** wireless means portable power, such as a battery, which means power requirements are important to think about. If we want to connect this device to the Internet, it has to connect fast, send data, and disconnect fast. And if it's using a low-power data connection protocol like Bluetooth LE, it has to be extra-careful that it doesn't have too much overhead. For cellular, where you really pay-by-the-byte, that's also important!

Chances are you're familiar with HTTP - its used for every website. HTTP is stateless, so you have to have a connection per data transfer - one connection every time you want to write data, one connection for reading. HTTP is great for huge amounts of data such as used for websites, and it _can_ be used for IoT connections. But it's not lightweight and its not terribly fast.

Another problem with HTTP is that it's pull only - your toaster can only _send data_ to the server whenever it wants (e.g. "Toast is done!"). If it wants to pull data from the server, it has to constantly connect and ask ("Any updates to the Toast darkness level?" "What about now?" "Anything now?") which is really data and time consuming. Pull updates are either slow (check only every few minutes) or data/power intensive (check constantly)

![adafruit_io_polling.png](https://cdn-learn.adafruit.com/assets/assets/000/029/736/large1024/adafruit_io_polling.png?1452824526)

![adafruit_io_mqtt.png](https://cdn-learn.adafruit.com/assets/assets/000/029/737/large1024/adafruit_io_mqtt.png?1452824585)

Thus we have no 'build up and tear down' overhead, and we can stream data in and out of multiple 'topics' quickly and easily. MQTT can run on top of any kind of network, whether it be a mesh network, TCP/IP, Bluetooth, etc. Since we'll be connecting to adafruit.io, the MQTT style we'll be discussing runs on top of a TCP/IP connection.

Cellular and WiFi and Ethernet all connect pretty easily to TCP/IP so that makes it easy to connect directly to adafruit.io

If you are using Bluetooth, XBee, Bluetooth LE, or another non-Internet-connected protocol & device, you will need a gateway! [For example, the Adafruit Bluefruit Connect app has a BLE adafruit.io gateway for passing data back and forth.](https://learn.adafruit.com/../../../../datalogging-hat-with-flora-ble/)

OK so we're using MQTT for speed and ease. Let's say you have this toaster at home (it has a WiFi chip, and is on your home network). And you have a geotracker in your car (a cellular+gps connection).

There's 2 ways you could have the two 'talk' to each other

  1. Have one of the devices run as a 'server' with an IP address, so that the other sensor can connect to it at any time
  2. Have a third 'server' somewhere, both toaster and car connect to that computer server and the computer sends messages back and forth.

Option #1 is in a sense, the 'least expensive' because no extra computer is needed. However, it's crazy difficult to pull off because the toaster or car have to be constantly waiting for a connection. And the other device needs to know the IP address of the listener. And then, what happens if a third device is involved?

Thus, we go with option #2 - the server that handles the messages? That's the **MQTT Broker** \- and that's what adafruit.io is, essentially. A neutral party that your Things can connect to to send and receive messages.

![adafruit_io_complexmqtt.png](https://cdn-learn.adafruit.com/assets/assets/000/029/738/large1024/adafruit_io_complexmqtt.png?1452824754)

![adafruit_io_accountname.png](https://cdn-learn.adafruit.com/assets/assets/000/028/190/large1024/adafruit_io_accountname.png?1445552840)

![adafruit_io_yourkey.png](https://cdn-learn.adafruit.com/assets/assets/000/028/192/large1024/adafruit_io_yourkey.png?1445553105)

> _(The key above is just me bashing on the keyboard, don't use that number. Use only the key that is created for your account!)_

![adafruit_io_photogaugecreate.png](https://cdn-learn.adafruit.com/assets/assets/000/028/194/large1024/adafruit_io_photogaugecreate.png?1445553614)

> _Use a thin type gauge with min value 0 and max value 1024 (this could store a 10 bit value)_

![adafruit_io_photogauge2.png](https://cdn-learn.adafruit.com/assets/assets/000/028/195/large1024/adafruit_io_photogauge2.png?1445553656)

> _the block is now added to the dashboard_

![adafruit_io_photogauge.png](https://cdn-learn.adafruit.com/assets/assets/000/028/196/large1024/adafruit_io_photogauge.png?1445553952)

> _Next up, make another block, this time an on-off toggle switch. Tie it to the onoff feed_

![adafruit_io_onoffbutton.png](https://cdn-learn.adafruit.com/assets/assets/000/028/197/large1024/adafruit_io_onoffbutton.png?1445554054)

> _Use the defaults for the 'on' and 'off' texts_

![adafruit_io_createonoff.png](https://cdn-learn.adafruit.com/assets/assets/000/028/198/large1024/adafruit_io_createonoff.png?1445554066)

> _OK now you have two blocks! You are ready to rock._

![adafruit_io_readydash.png](https://cdn-learn.adafruit.com/assets/assets/000/028/199/large1024/adafruit_io_readydash.png?1445554083)

> _Continue on to the next step!_

![adafruit_io_2821-08.jpg](https://cdn-learn.adafruit.com/assets/assets/000/029/628/large1024/adafruit_io_2821-08.jpg?1452396511)

![adafruit_io_received.png](https://cdn-learn.adafruit.com/assets/assets/000/028/209/large1024/adafruit_io_received.png?1445563239)

![adafruit_io_complexmqtt.png](https://cdn-learn.adafruit.com/assets/assets/000/029/741/large1024/adafruit_io_complexmqtt.png?1452825107)

> _In this diagram you can see there's two of each_
