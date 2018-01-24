# Minimal MQTT: Building a Broker

_Captured: 2017-10-31 at 18:22 from [hackaday.com](https://hackaday.com/2016/05/09/minimal-mqtt-building-a-broker/)_

![](https://hackadaycom.files.wordpress.com/2016/04/mqtt.jpg?w=800)

In this short series, we're going to get you set up with a completely DIY home automation system using MQTT. Why? Because it's just about the easiest thing under the sun, and it's something that many of you out there will be able to do with material on-hand: a Raspberry Pi as a server and an ESP8266 node as a sensor client. Expanding out to something more complicated is left as an exercise to the motivated reader, or can be simply left to mission creep.

We'll do this in four baby steps. Each one should take you only fifteen minutes and is completely self-contained. There's a bunch more that you can learn and explore, but we're going to get you a taste of the power with the absolute minimal hassle.

In this installment, we're going to build a broker on a Raspberry Pi, which is the hub of your MQTT network. Next time, we'll get an ESP8266 up and running and start logging some data. After that, we'll do some back-end scripting in Python to make the data speak, and in the last installment, we'll explore some of the useful frills and fancy bits. Let's get started!

## Overview

[MQTT](http://mqtt.org/) is a pub-sub, store-and-forward, IoT-enabled, machine-to-machine connectivity protocol juggernaut. As you can see, it's fully buzzword-compliant. That doesn't necessarily mean that it's super complicated, though. You can read up on MQTT until [you're blue in the face](http://www.hivemq.com/mqtt-essentials/). Here's the bare minimum you need to know to be comfortable.

![](https://hackadaycom.files.wordpress.com/2016/04/mqtt-dot4.png)

The network has clients (called "clients") and servers (called "brokers"). Clients, whether it's your temperature sensor node or the graphing application that's going to use the data, use the broker as a central hub. Data are arranged in "topics", which use a directory-like structure. So the temperature node in my bedroom is called "home/bedroom/temp". When I add a light sensor to my bedroom node, I'll set up a topic called "home/bedroom/light" and so on.

When a client gets some new data, it "publishes" it to the topic -- sends the data to the server. The server then forwards the data along to all of the other clients that have "subscribed" to the topic. In my example, the bedroom node publishes to "home/bedroom/temp" and then a databasing program which is a subscriber to "home/bedroom/temp" automatically receives it. And so does any other client that's subscribed to the topic.  
Often a given physical device will subscribe to some topics and publish to others. My heating controller will want to act on the temperature sensors, and display its status on an LED in the bedroom, for instance. There's naturally more to say, but let's get our broker up and running first and explore the details later.

## Build a Broker

OK, "build" is a little bit overstated. We're just going to download `mosquitto`, which is the most widely-used broker. If you've got a Raspberry Pi (or other spare computer) lying around, you've got an MQTT broker-in-waiting. Unfortunately, Raspbian comes with an old version of mosquitto by default, so we'll have to do a tiny bit more typing to get the most recent version. Here's how I set up a fully-featured MQTT broker on a brand-new Raspberry Pi (Jessie Lite):

1234567
`curl -O http:``//repo.mosquitto.org/debian/mosquitto-repo.gpg.key``sudo apt-key add mosquitto-repo.gpg.key``rm mosquitto-repo.gpg.key``cd /etc/apt/sources.list.d/``sudo curl -O http:``//repo.mosquitto.org/debian/mosquitto-jessie.list``sudo apt-get update``sudo apt-get install mosquitto mosquitto-clients`

Et voila. Later, when we need to access the broker from the outside world, we'll need to know the Raspberry Pi's IP address, but that's it. You're up and running. If you're using an older version of Raspbian, substitute "wheezy" for "jessie" in the fifth line. If you're using anything other than a Raspberry Pi, you can probably find what you need, including Windows binaries, [here](http://mosquitto.org/download/). (I haven't tested Windows or Mac.)

## Playing Around

Now that our broker is set, let's do some quick experiments to get a taste of how MQTT works in practice. The astute among you noticed that I also installed `mosquitto-clients`. Let's try them out.

Open up a window and type `mosquitto_sub -h localhost -t "test/topic"`. Congratulations, you've just subscribed a client to the "test/topic" topic. `-h localhost` connects you to an MQTT server on the local machine, rather than on the broader Internet. If we weren't setting up our own server, I'd have you point to [the MQTT test servers](http://test.mosquitto.org/). As it is, I'll just let you know that they're out there when you need them.

OK, let's publish our first data. Open up another window and type `mosquitto_pub -h localhost -t "test/topic" -m "hello!"` Same server, same topic, but now we're sending a message. You should see the message pop up instantly in the subscribed window.

Try opening up multiple subscriber windows, subscribed to the same topic. You'll see that they all get the message. Try sending messages to topics that don't exist yet. What happens?

One last stupid MQTT trick before we get to the important stuff. MQTT can use two different [types of wildcards](http://mosquitto.org/man/mqtt-7.html) in the topic names. So my network has "home/bedroom/temp" and "home/cellar/temp" topics. I can read all the temperatures by subscribing to "home/+/temp" and get all the values from my bedroom node from "home/bedroom/#". ("+" matches one hierarchical level, while "#" stands for everything deeper in the tree.) Once you start using wildcards, you'll want to know which topic is reporting, so try subscribing in verbose mode `mosquitto_sub -h localhost -v -t "test/#"` and send yourself some test messages to different topics.

## Quality of Service

Here is MQTT's killer feature for a low-power home automation sensor network: it's a "store and forward" protocol with a couple levels of quality of service (QOS) guarantees. If your node has already registered with the broker and it's offline when a new message comes in, the broker can take care of delivering that message to the node as soon as it reconnects. This means that your nodes can spend most of their lives in a deep sleep, conserving battery power, and when they do finally connect, they haven't missed anything.

Three things are needed for the QOS feature: the subscribing clients need to be previously registered by ID with the server, and they need to disable the (default) clean-slate behavior otherwise all stored messages are erased when you log back in. _Both_ the subscriber and the publisher need to be using quality-of-service level one or two so that the server knows it's a stored message. (QOS level one usually suffices, but feel free to [read up](http://www.hivemq.com/blog/mqtt-essentials-part-6-mqtt-quality-of-service-levels).)

Here's an example:

12345
`subscriber:  ``mosquitto_sub -h localhost -v -t ``"test/#"` `-c -q 1 -i ``"james bond"``publisher:``mosquitto_pub -h localhost -t ``"test/topic"` `-m ``"wowie"` `-q 1``mosquitto_pub -h localhost -t ``"test/topic"` `-m ``"zowie"`

To demonstrate what QOS does, run the subscriber's command in one window and send the other two messages to it. You'll get them both. Now stop the subscriber with ctrl-c and resend both messages. Now, when you subscribe again, you'll only get "wowie" because it was the message sent with QOS enabled.

One gotcha with IDs is that you'll only get whatever has happened _between_ IDed logins. You have to be previously registered with the server so that it saves messages for you. You can't just walk in, give it a new ID, and say "what have I missed?" because it doesn't know you yet.

Also note that the subscriber must do three things to enable receiving messages with QOS. The ID and QOS levels are obvious. The one I always forget is to disable clean-slate logins with the `-c` flag. Don't forget.

## Retained Messages

If you don't need to get the full history of messages since your node was last online, consider the "retain" flag. When messages are sent as retained, the last such message gets automatically transmitted to any client that subscribes to the topic. Retained messages are great for things like status reports. Any time that you want to log in and see just the last value without having to wait for an update, you'll wish you had retain set. And note that retained messages and QOS aren't exclusive -- just be careful because you'll get one message (the most recent one) delivered twice.

## More??

This was just a taste of the power of having your own MQTT server running. Next, we'll connect some small devices to the network, and then we'll build up some back-end processing. If you've gotten this far and just can't wait, try playing around with `mosquitto_sub -h test.mosquitto.org -t "hackaday/new_articles" -c -q 1 -i "your_name_here"`. The stream is published with `QOS=1` and retains the last message. Feel free to play around and show us what you build in the comments.
