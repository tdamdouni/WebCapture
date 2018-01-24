# Review: IoT Data Logging Services with MQTT

_Captured: 2017-10-31 at 17:08 from [hackaday.com](https://hackaday.com/2017/10/31/review-iot-data-logging-services-with-mqtt/)_

![](https://hackadaycom.files.wordpress.com/2017/10/fremium-iot-data-logging.jpg?w=800)

For the last few months, I had been using Sparkfun's Phant server as a data logger for a small science project. Unfortunately, they've had some [serious technical issues](http://data.sparkfun.com) and have discontinued the service. Phant was good while it lasted: it was easy to use, free, and allowed me to download the data in a CSV format. It shared data with [analog.io](https://hackaday.io/project/4648-analogio-a-full-stack-iot-platform), which at the time was a good solution for data visualization.

While I could continue using Phant since it is an open-source project and Sparkfun kindly [releases the source code for the server on Github](http://github.com/sparkfun/phant), I thought it might be better to do some research, see what's out there. I decided to write a minimal implementation for each platform as an interesting way to get a feel for each. To that end, I connected a DHT11 temperature/humidity sensor to a NodeMCU board to act as a simple data source.

### What Makes IoT Data Logging Services Useful?

To start, I had three main requirements. First of all, the service would be primarily used for data logging , so a proper export feature is a must.

Second, it needs to support MQTT well, and be properly documented so that I can implement it on a wide variety of hardware. An Arduino library is useful, but not sufficient. We've previously covered [the basics of MQTT](https://hackaday.com/2016/05/09/minimal-mqtt-building-a-broker/) if you need a quick refresh.

Finally, it had to be available at a reasonable cost. It did not have to be free of charge, as there are plenty of ways to make a reasonably priced service pay for itself in effort saved or actual income.

After that, there are a lot of things that were optional. A slick dashboard with live graphs is a great way to quickly share data and get people interested. Support for MQTT QoS level 2 (each datapoint is sent exactly once using a 4 way handshake) would be nice as some of the networks I'll be using will not exactly be reliable and this means better quality data. Finally, if I can host it on my own VPS so that I can rent a server in the countries where I am collecting data, that would really improve reliability in my area.

After considering the above I found five options that seemed to fit the bill: Adafruit.io, Cayenne, Thingspeak, Thingsboard, and Ubidots. I also considered Blynk, but they don't seem to have documentation available yet to use MQTT with their service. This is a shame because otherwise it looks pretty slick and has a neat smartphone app.

In each case I'll explain the pros and cons from my standpoint, and provide an implementation example in Lua using a generic MQTT library (from NodeMCU). Most platforms also provide custom libraries or ready-made solutions for Arduino, Raspberry Pi, and others, however I wanted to investigate at a slightly lower level how each service works. As an added benefit, the code will run directly on NodeMCU firmware that supports MQTT.

One criteria not in consideration is security - these data loggers are collecting non-critical scientific data. They're on an encrypted Wi-Fi network, and do not accept commands from the Internet.

### Adafruit IO

I've always been impressed with Adafruit's documentation, and [Adafruit IO](http://io.adafruit.com) was no exception. The MQTT communication protocol was well-defined, it was clear how to set things up without any aspect ever feeling 'dumbed-down', and there were links to further reading.

Setting up a device in Adafruit IO starts with creating a feed in the user interface, which is easy on the eyes and well thought out:

![](https://hackadaycom.files.wordpress.com/2017/10/adafruit-io-dashboard.png)

Once you've created a feed, you'll be able to add it to a dashboard if you wish. The collection of widgets is somewhat sparse compared to some other platforms, but all the necessary ones are there and they can be resized as you need:

![](https://hackadaycom.files.wordpress.com/2017/10/adafruit-io-dashboard-graphs.png)

To add data to a feed, you need to set your MQTT client to connect to io.adafruit.com, using your Adafruit account name as your username, and your AIO key (to the left in yellow when you log in) as your password. Note that if your device is not using SSL, these credentials can be intercepted, and that Adafruit IO supports SSL. If your device supports SSL, it's a good idea to use it.

Once connected, the MQTT topic to publish to is simply your-username/feeds/feed-name. Even though JSON data format is supported, one caveat is that you can really only record one value at a time per feed. You can add latitude, longitude, and elevation to a single feed, but could not add temperature and humidity. By contrast, some platforms let you add more or less arbitrary amounts of variables inside a single feed, which I often find useful for things like weather stations. Nothing stops you from tying multiple feeds to a single dashboard, so I don't see this as a major flaw. The only shortcoming I've been able to find is that Adafruit IO only supports MQTT QoS levels 0 and 1, with no support for 2.

Adafruit IO has convenient data management as well. You can manually add and delete values, a feature missing on some of the other platforms. Downloading the data from a feed is trivial, there's a button for it when you are viewing a feed.

One truly excellent feature I would like to point out is that there's an error console. Not only that, but the dashboard flags it red when there's something new for you to see there. This feature combined with the excellent documentation made Adafruit IO the best platform to learn with -- none of the complexity is hidden, but it's documented and there are tools for debugging. Our sample code to try out this platform is below:

1234567891011121314
`ClientID = 'put anything here'``username = 'your username here'``AIOkey = 'your key here'``m = mqtt.Client(ClientID, 120, username, AIOkey)``m:connect("io.adafruit.com", 1883, 0, function(client) print("connected") m:publish(username.."/feeds/temperature", temp, 0, 1) m:close() end)``function postThingSpeak(level)``m:connect("io.adafruit.com", 1883, 0, function(client) print("connected") m:publish(username.."/feeds/humidity", humi, 0, 1) m:close() end)``end``tmr.alarm(1, 5000, tmr.ALARM_SINGLE, function() postThingSpeak(0) end)`

### **Cayenne**

The interface in [Cayenne](https://mydevices.com/) is organized by device. Each device has channels that contain your data. When sending data to a channel, the device can indicate what type of data (e.g. humidity) is being sent to assist in processing. There are quite a few [supported data types](http://mydevices.com/cayenne/docs/bring-your-own-thing-api/#cayenne-mqtt-api-supported-data-types).

![](https://hackadaycom.files.wordpress.com/2017/10/cayenne-dashboard.png)

You can create different 'projects' that take data from channels on different devices and add them to a common dashboard. Each channel can be displayed as a graph of preset or custom time intervals. The graphs are clean, but are a bit on the small side for larger data sets, and have an odd smoothing effect that created curved lines that didn't represent the data. I don't like this feature at all as it makes it harder to see what's really going on. What I would liked to have seen was an ability to turn off the trend line entirely or at least the smoothing feature.

On the graph view is a 'Download Chart Data' button that downloads the data as a CSV file.

![](https://hackadaycom.files.wordpress.com/2017/10/cayenne-graph-and-export.png)

Overall Cayenne checked all the boxes, but how easy is it to code for? As it turns out, it has one of the more unusual MQTT setups of the services I investigated. It requires a client ID, a username, and a password specified to connect, and the client ID and username specified again in the MQTT topic:

1234567891011
`ClientID = 'your client ID here'``username = 'your username here'``password = 'your password here'``channel = 'your device channel'``m = mqtt.Client(ClientID, 120, username, password)``m:connect("mqtt.mydevices.com", 1883, 0, function(client) print("connected") m:publish("v1/"..username.."/things/"..ClientID.."/data/"..channel, "temp,c="..temp, 2, 1) m:close() end)`

The channels added to each device are named in the web interface, and are simply identified with a number. For example your first channel would be `v1//things/<ClientID>/data/0`.

In the end, this worked fine and it even supported MQTT QoS level 2.

### **Thingspeak**

First off, [Thingspeak](https://thingspeak.com/) has integration with MATLAB. Being able to store, visualize, and analyze data in the same place seems like an excellent feature. I prefer to do hypothesis testing in Python but MATLAB is an excellent choice and all common statistical tests are available.

In Thingspeak, data is sorted into channels. Channels contain fields, and fields contain your data.

![](https://hackadaycom.files.wordpress.com/2017/10/thingspeak1.png)

![](https://hackadaycom.files.wordpress.com/2017/10/thingspeak-graphs.png)

The graphs on Thingspeak are tidy and clearly show the data points. However, I couldn't find a way to resize the graphs in the interface, which ought to be possible because they seem to be generated as SVG graphics.

One very interesting feature is the ability to generate an iframe from the graphs and include them on another website. I gave this a quick try, it worked like a charm. It would have been a neat add-on to this [radiation detector](https://hackaday.com/2017/10/08/connecting-a-50-geiger-counter/).

The MQTT implementation at Thingspeak is dead simple, requiring only the channel ID and API key:

1234567
`ChannelID='your channel ID'``apikey = 'your API key'``m = mqtt.Client(ClientID, 120)``m:connect("mqtt.thingspeak.com", 1883, 0, function(client) print("connected") m:publish("channels/"..ChannelID.."/publish/"..apikey, "field1="..temp.."&amp;field2="..humi, 0, 0) m:close() end)`

Unfortunately, Thingspeak only supports QoS level 0, which means data can be duplicated or missed on shaky Internet connections. I'm not sure how much this matters in practice, but given their focus on data analysis it would be nice not to have to deal with missing data points.

### **Thingsboard**

Up to this point, we've only investigated externally hosted services. If you need something that you can host yourself, [Thingsboard](https://thingsboard.io/) is worth checking out. Their setup is a little different from anything we've seen so far. Much of it is access control for different users, rule setup for raising alarms/actions, and exciting things that are beyond the scope of this article.

![](https://hackadaycom.files.wordpress.com/2017/10/dashboard.png?w=1600&h=530)

For our purposes in Thingsboard, devices contain telemetry data. Then widgets on dashboards are connected to the telemetry contained in devices. The dashboard creation workflow is convoluted compared to some other platforms, but they have by far the widest selection and coolest looking dashboard widgets I've seen, and each of them can be set to display full screen.

![](https://hackadaycom.files.wordpress.com/2017/10/widgets.png)

However, data export is somewhat inconvenient at first - there's no download button but it can be done [programatically via Curl](https://thingsboard.io/docs/user-guide/telemetry/#timeseries-data-values-api). This way data export and backup can be automated (e.g. with cron), which suits me fine.

The MQTT implementation here is very straightforward and supports QoS level 2. An access token associated with a device is used on connect, and then any telemetry sent will belong to that device. A very important consideration is that you must not send integer or float data as a string - it will work on real-time displays such as gauges, but any graphs will fail to pull historical data correctly. In other words, do not send `{"temperature":"57"}`, be sure to send `{"temperature":57}`. Code example below:

1234567891011121314151617181920212223242526272829
`ClientID = 'put anything here'``token = 'your token here'``m = mqtt.Client(ClientID, 120, token)``function postThingsboard(level)``status, temp, humi, temp_dec, humi_dec = dht.read(pin)``print(string.format("DHT Temperature:%d.%03d;Humidity:%d.%03d\r\n",``math.floor(temp),``temp_dec,``math.floor(humi),``humi_dec``))``print('{"temp":'..temp..',"humidity":'..humi..'}')``m:connect("demo.thingsboard.io", 1883, 0, function(client) print("connected") m:publish("v1/devices/me/telemetry", '{"temp":'..temp..',"humidity":'..humi..'}', 2, 1) m:close() end)``end``tmr.alarm(1, 10000, tmr.ALARM_AUTO, function() postThingsboard(0) end)`

### **Ubidots**

Unlike the other platforms reviewed here, [Ubidots](https://ubidots.com/) does not offer a free account tier. That being said, new accounts start off with enough credits to operate a device for 5 months, and USD $5 will purchase enough credit for a device to run for 2 months.

In Ubidots, data is sent to variables, and variables exist within devices. You can create a dashboard by adding widgets and selecting a data variable. User interface is where Ubidots really shines; it has by far the best dashboard creation process and overall it's immediately clear how to do everything you might need to do… with one exception.

![](https://hackadaycom.files.wordpress.com/2017/10/ubidots-dashboard-creation.png)

The option to export all data from a variable is accessed by entering the variable, then clicking on 'variable settings', where the only two options are 'Export to CSV' and 'Delete Values' - neither of which are settings. Exporting all data from a device on the other hand is intuitively labeled, and where you would expect it to be, which I've indicated with a big red arrow:

![](https://hackadaycom.files.wordpress.com/2017/10/ubidots-device1.png?w=1600&h=578)

As for the MQTT implementation, it's a bit clunky in my opinion. You connect with your token as your username, and the way data is associated with a particular device is via the MQTT topic. The data keys in the JSON dictionary then have to exactly match the variable names set up in the user interface (which must be unique).

This strikes me as less easy to manage than some of the other platforms, where you specify a device-specific token, and you can use non-unique variable names. Perhaps I'm missing something, but if I'm logging the temperature of 30 different pipes I would personally find it easier to manage unique keys than unique variable names. It does support MQTT QoS level 2 though, which is nice:

123456789
`clientID = 'anything can go here'``Token = 'your token'``Device = 'your device name'``m = mqtt.Client(clientID, 120,Token)``m:connect("things.ubidots.com", 1883, 2, function(client) print("connected") m:publish("/v1.6/devices/"..Device, '{"Temperature":"'..temp..'","Humidity":"'..humi..'"}', 2, 1) m:close() end)`

### **Summary**

All of these platforms provide data capture, display, and export. They differ a little in their MQTT implementation, but not by very much. For datalogging purposes they're all sufficient. After trying each of them, a few things stuck with me.

Adafruit IO was hands down the best platform to learn with. They had excellent documentation, data management, and an error console for debugging. The free account is enough to get started, and the paid account is reasonably priced and powerful enough to get a lot done. If I had to suggest a service to someone wanted to learn how to add IoT data logging to their projects, I would recommend Adafruit IO without hesitation.

Thingspeak integrated data analytics into their platform. I haven't dug deeply into it, but the idea of having data acquisition, storage, analysis, and decision making in the same place and automated seems brilliant. Can it perform automated hypothesis testing and control systems based on rejection/failure to reject the null hypothesis? I'm not a MATLAB user, but on the surface it looks like it could. Just don't tell any direct response marketing teams about that.

Ubidots has a slick user interface and is easy to understand. If I had to introduce IoT to children or managers without going into many technical details, this is what I would use. That's not intended to be a snide remark, it's just ideal for both groups for different reasons.

Finally, Thingsboard. I had no idea something this mature existed in the IoT space. The possibilities are staggering for both personal and commercial projects since it's open-source and can be self hosted. To top it off, it has beautiful dashboard widgets that I can actually show clients. My reaction when I saw it was to immediately pick up the phone and start making calls. I don't know what I'll be doing yet, but it's going to be fun, and I'll try to share it here one day.
