# Communicating with a Raspberry Pi from an Arduino using Node-RED

_Captured: 2017-11-09 at 23:09 from [ktinkerer.co.uk](http://ktinkerer.co.uk/communicating-arduino-raspberry-pi-using-node-red/)_

I wanted to add some sensors to a Raspberry Pi but I was quickly running out of GPIO pins, luckily I had some spare Arduinos so decided to experiment with plugged one into the Pi.

I loaded [this sketch](https://gist.github.com/ktinkerer/a48556dc0ff3b7b06e7d9a323f53aede) onto the Arduino to read temperature and humidity using the DHT22. More information on how to do this can be found on [my previous post about using DHT sensors with an Arduino](http://ktinkerer.co.uk/testing-dht22-and-dht11-temperature-and-humidity-sensors-on-the-arduino/). Once this is working connect the Arduino via USB to the Raspberry Pi.

To get the readings in Node-RED install [Node-RED serialport](https://flows.nodered.org/node/node-red-node-serialport) (follow the instructions in the link), restart Node-RED and select the serial port node (make sure your Arduino is plugged in to the pi using a USB cable). To set it up you need to put in the serial port you are using. My settings looked like the following image.

![](https://i0.wp.com/ktinkerer.co.uk/wp-content/uploads/2017/10/Node-RED-192.168.0.4-Google-Chrome_001-1.jpg?w=1009)

You may need to parse the values coming from your Arduino, maybe to separate out different values. To do this I added a function with this code:  
`  
var readings = {};  
var values = msg.payload.split(",");  
for (var i = 0; i < values.length; i++) { var items = values[i].split(":"); readings[items[0].trim()] = parseFloat(items[1]); } msg.readings = readings; return msg; `

This will parse readings in the format 'Reading1: value1, Reading2: value2' and add them to the msg object as msg.readings.Reading1 etc.  
I added MQTT outputs so that I could access the readings through MQTT clients. An example of the flow I used is on [Github](https://gist.github.com/ktinkerer/7e1d66da3b9e5e96857a9e413cb6120d)
