# IoT and Vert.x: Building a Simple MQTT Server

_Captured: 2017-08-08 at 17:53 from [dzone.com](https://dzone.com/articles/iot-and-vertx-building-a-simple-mqtt-server?edition=313400&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-07)_

Almost a year ago, Dreamix adopted [Vert.x](http://vertx.io/) in its technology stack as a need for a framework with reactive capabilities. Its good documentation and strong community are excellent additions to the various features which the framework provides.

The term IoT (Internet of Things) is very popular these days, since everyone talks how all sorts of devices from TVs, refrigerators, air conditioners, etc. will be connected to the Internet. The implementation of IoT standards indicates that the field has grown tremendously, and every developer with an interest in this ecosystem should be aware of them.

This blog will cover the implementation of an MQTT server with Vert.x and the corresponding communication with an Android MQTT client.

"MQTT is a machine-to-machine (M2M)/"Internet of Things" connectivity protocol. It was designed as an extremely lightweight publish/subscribe messaging transport. It is useful for connections with remote locations where a small code footprint is required and/or network bandwidth is at a premium."

## **Prerequisites**

  1. Download the [MQTT Dash (IoT, Smart Home)](https://play.google.com/store/apps/details?id=net.routix.mqttdash) Android application. This will serve as our client.

## **Hands on the Project**

We are going to implement simple home automation project and more specifically remote switching of your home lights. But first little theory.

As the quote above states, the MQTT is as simple publish/subscribe protocol one of the de-facto IoT standards. The protocol is developed by Andy Stanford-Clark and Arlen Nipper in 1999 for the purposes of oil pipeline monitoring through the desert.

The main communication unit is called Broker and is responsible for dispatching all messaging between the sender and the receiver. In the context of our project we are going to implement exactly an MQTT broker which will dispatch messages from our Android client to a LightsController class which will simulate the switching of the lights.

Our Android client will publish a message to the broker with included special string in it's message. This string is called **Topic**. Based on the topic, the broker will know how to reroute the message to a previously subscribed receiver to the same topic.

Let's build our MQTT broker.

The broker implements publish/subscribe handlers, which are the backbone of MQTT communication. Also, the implementation provides an unsubscription mechanism, which, for the purpose of the demo, just prints a message in the console.

The topic that the broker must handle is called "lights". Based on the topic, the broker will know how to dispatch the message. In our case, it gives the message sent from our client to the LightsController class.

MQTT QoS (Quality of Service) ensures that the messaging between the sender and receiver will be guaranteed according to the specific QoS levels. There are three QoS levels:

  * **At most once **(0): This is the minimum level, or the so called "fire and forget". The receiver is not obliged to return a response to the sender and the sender is not obliged to resend the message.
  * **At least once **(1): This ensures that the message will be delivered at least once to the receiver. The receiver must return a message to the sender. However, the message can be delivered more than once, so duplicate messages should be considered.
  * **Exactly once **(2): The safest and slowest level. It ensures that the message will be delivered only once.

In our case, we are using QoS level 1. When the LightsController finishes with its task, a response to the client will be sent.

Let's look at the LightsController implementation.

This simple expects the message to contain a special value, based on which the controller will "turnOn" or "turnOff" the lights.

Run the application. "MQTT server is listening on port 1883" should appear in the console.

## **Android Client Configuration**

Open the MQTT Dash Android application. The following screen should appear:

![MQTT Dash ](https://dreamix.eu/blog/wp-content/uploads/2017/08/MQTT-Dash-170x300.png)

Click on the "+" sign in the upper right corner. Enter a preferred name of your dashboard in the "name" field (in my case, it will be Demo) and also enter the IP address of the running MQTT Broker application. Click on the upper right floppy disk icon in order to save the configuration. The following screen should appear:

![MQTT Dash Demo ](https://dreamix.eu/blog/wp-content/uploads/2017/08/MQTT-Dash-Demo-170x300.png)

Click on your newly created dashboard and check the console of the MQTT Broker application. "MQTT client [<client-id>] request to connect" should appear in the console.

Let's improve our dashboard and add a switch button to it.

Click on the "+" sign and choose "Switch/button". The following screen should appear:

![MQTT Dash readme ](https://dreamix.eu/blog/wp-content/uploads/2017/08/MQTT-Dash-readme-170x300.png)

Insert the following configuration on the screen and click the floppy disk icon in order to save:

  * Name - Home Lights
  * Topic(sub) - lights
  * Other settings - QoS(1)

The following screen should appear:

![MQTT light ](https://dreamix.eu/blog/wp-content/uploads/2017/08/MQTT-Light-171x300.png)

Click on the checkbox and, again, check the console of the broker application.

"Subscription for lights with QoS AT_LEAST_ONCE"

"Lights are on!"

If you click again on the checkbox, you will see another message which indicates that the "Lights are off!"

## **Conclusion**

The MQTT protocol is a very powerful tool and should be kept in mind when developing IoT projects. If you want to get deeper into the Vert.x implementation of this protocol, check out <http://vertx.io/docs/#mqtt-server>.

The code from this basic project can be reused and improved without any concerns.
