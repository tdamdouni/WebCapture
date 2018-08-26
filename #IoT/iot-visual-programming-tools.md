# IoT Visual Programming Tools

_Captured: 2018-08-14 at 14:10 from [dzone.com](https://dzone.com/articles/iot-and-the-iot-visual-programming-tools?edition=385369&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202018-08-14)_

We all constantly hear talks about the impact that IoT is having and will have in different areas of our lives and in the production systems. But, what is IoT? Simply speaking, it is a world of connected objects that talk to each other to exchange information. Going a little deeper into the IoT ecosystem, we can identify several elements that usually build an IoT system. There are not only smart objects, but there are also gateways, sensors, and IoT cloud platforms that enable us to create dashboards and analyze the data. The interesting aspects of the Internet of Things are the possibility to explore this world by ourselves.

Lately, we are noticing the birth of several IoT development boards that have different features. Starting with Arduino and Raspberry to ESP8266, Particle, NXP, and, lately, Android Things, all these development boards help us to take the first steps towards an IoT ecosystem. Moreover, the explosion of the prototyping kits that brings together IoT boards, sensors, motors, LEDs, and so on makes it easier for amateurs and hobbyists to develop IoT projects.

## Visual Programming Tools Overview

Tutorials and articles enables everyone to build their first project. There is one aspect that is still a problem -- the programming language. All these prototyping boards have its own programming language, like C, Python, or Java. If you want to develop your IoT system, you must know at least one of these programming languages. Fortunately, during these years, several visual programming languages have been developed to help people start programming without knowing the programming language. These IoT visual programming tools have a different approach when it comes time to program. We are used to writing several lines of code, using variables, conditional statements, loops, objects, and so on. Well, an IoT visual programming tool has a graphical user interface where the user, using a drag-and-drop approach, moves some code blocks that execute a simple piece of logic. For example, there is a block for loop, another for reading data from pins and so on. To make it simple, [Wikipedia](https://en.wikipedia.org/wiki/Visual_programming_language) defines a visual programming language as:

"Combining these blocks, a user can build its own IoT app without knowing much about programming languages. Combining the simplicity of IoT development kits with the power of the IoT visual programming tools, you can dive into the Internet of things ecosystem without having much experience about devices, resistors, programming languages, and so on."

This article provides a list of IoT visual programming tools -- in no particular order -- that can be used to develop your IoT app. Let us begin!

## Node-RED

![Nodered](https://www.survivingwithandroid.com/wp-content/uploads/2018/08/node-red-icon-2.png)

> _Source:https://nodered.org/about/resources/media_

[Node-RED](https://nodered.org/) is a flow-based programming tool, developed initially by IBM, and now it belongs to JSFoundation. It was built on the NodeJS framework. It is based on the concept of Node that is a black box element that performs a specific task. The data flow works through the nodes according to the node connections. Every node has a data input and data output and is a widely-used visual programming tool. Using this visual approach, Node-RED connects device hardware and cloud services that can invoke external APIs to complete tasks. The interesting aspect of this visual programming tool is that the editor runs in a browser and the flow and nodes are saved using JSON, making it easy to share data and schemas. It is an open-source platform and its code can be found in [GitHub](https://github.com/node-red). Node-RED supports several IoT prototyping boards, like Arduino, Raspberry Pi, and Android. It also supports these IoT cloud platforms: IBM Bluemix, Microsoft Azure, Amazon Web service, and SenseTecnic FRED.

### Visuino

![Visuino](https://www.survivingwithandroid.com/wp-content/uploads/2018/08/visuino_logo.png)

> _Source: https://www.visuino.com/_

Visuino is another visual programming tool. It is made for hardware developers that do not have much knowledge of software development. It uses blocks to program Arduino boards and is based on the drag-and-drop paradigm that is used to control sensors and peripherals. Moreover, it has a built-in panel to visualize data coming from sensors. It is made for Arduino boards, and it can be used with Arduino compatible boards with ESP32 and ESP8266. It requires a subscription fee to receive updates after a trial period. Currently, it supports only Windows OS. However, they are working to support OS X, too.

### Wia

![Wia IoT platform](https://www.survivingwithandroid.com/wp-content/uploads/2018/08/wia_logo.png)

> _source: https://www.wia.io/_

[Wia](https://www.wia.io/) is a cloud platform that simplifies the IoT app development connecting IoT devices together and with external services. Using Flow Studio, it is possible to connect IoT development boards, IoT devices, and sensors and external services. It is a bit different from others because it uses complex blocks that perform complex operations like managing a sensor. It supports several IoT development boards like Arduino MKR1000, MKR1200, Espressif, Raspberry Pi, Particle and so on. Moreover, it supports several external services like AWS, Twitter, Twilio and so on. Wia has a set of API we can use to interact with and exchange data. It is open source and we can download the source code from [Github](https://github.com/wiaio).

### Embrio

![Embrio IoT](https://www.survivingwithandroid.com/wp-content/uploads/2018/08/embrio-logo.png)

> _Source: http://www.embrio.io/_

[Embrio](http://www.embrio.io/) is another interesting visual tool to develop IoT apps. It is made for Arduino and supports different OS as Windows, OS X, and Linux. Embrio is a drag-and-drop tool that uses a different approach to program Arduino visually. It uses the Agent concepts. An Agent is more or less a process that has a job to complete. Agents can run at the same time, and they can activate or kill other Agents. The connections between Agents define the IoT app data flow and the app logic. The Embrio app can be compiled into an Arduino code and runs on an Arduino platform.

### Visualino

[Visualino](http://www.visualino.net/index.html) is a visual programming environment that supports several Arduino boards. It supports Windows OS, OS X and Linux. Currently, there is not much documentation about this project. It generates Arduino native code that can run directly on an Arduino compatible board. It is an open-source project. You can find more information here at [GitHub](https://github.com/vrruiz/visualino/).

### XOD

![XOD](https://www.survivingwithandroid.com/wp-content/uploads/2018/08/xod-logo.png)

> _Source: https://xod.io/_

[XOS](https://xod.io/) is a visual programming tool for microcontrollers. It is based on the Node concept that can represent a sensor, motors, or some functional piece of code, such as comparison operations, text operation, and so on. Each node has an input and an output, connecting all the nodes so that we can define the IoT app logic. XOD generates native code that you can upload on Arduino compatible boards and run on it. It supports mainly Arduino. It is an open-source project, and the interesting aspect is that it is extensible -- that is it is possible to create new nodes to support new components.

### Wyliodrin

[Wyliodrin](https://www.wyliodrin.com/) is a complete platform that includes a visual programming tool that supports several prototyping boards. It helps the user from the beginning to the deployment phase. It supports several programming languages that can be used instead of the visual programming IDE. The visual IDE is built on Google Blocky. It is based on the concepts of blocks, which are piece of code that performs a task. Combining blocks and defining its order, we can define the IoT app business logic. Blocks can perform simple tasks like sum two variables or more complex tasks as turning on or off a LED, set the pin status, or stream data from an URL. It is a browser-based environment. It supports several prototyping boards, such as Raspberry Pi, Intel Galileo, Intel Edison, and so on.

### Ardublock

[Ardublock](http://blog.ardublock.com/) is a graphical programming language for Arduino. The interesting aspect of this visual tool is the capability to be integrated with Arduino IDE. It uses the block concept at the base of the programming. Using these blocks, we can, for example, set the status of a pin or read its value. Using Ardublock, the interaction with Arduino pins get very simple; it is just a matter of drag-and-drop some blocks and connect them in the right way. At the end, it is possible to generate a native Arduino code that can be executed on the Arduino board.

### Modkit

[Modkit](http://www.modkit.com/vex) is a graphical tool where there is a representation of the Arduino board where we can work on selecting its pins. Using blocks it is possible to interact with Arduino pins without knowing much about programming languages for IoT. It is very easy to use and it supports common operation and logic blocks. Moreover, it has another version called Modkit VEX that you can use to program a robot.

### Zenodys

![Zenodys IoT platform](https://www.survivingwithandroid.com/wp-content/uploads/2018/08/zenodys_logo.jpg)

> _Source: https://www.zenodys.com/_

[Zenodys](https://www.zenodys.com/) helps developers to build IoT apps easily. Using Zenodys platform, it is possible to collect data from any sensors and visualize the values acquired easily without programming. Using Workflow builder makes it possible to build complex backend solutions using visual programming tools. Finally, the UI builder helps the developer to build IoT dashboard to visualize data and information. It is a complete platform that provides several services that can be connected together using its tools and builders. There are several scenarios where Zenodys can be used -- predictive maintenance, real-time monitoring systems, product line automation, and so on.

### ReactiveBlocks

"Reactive Blocks is a visual model-driven development environment supporting formal model analysis, automated code generation, hierarchical modelling, and an extensive library of ready-to-use components for the Java platform. By combining re-usable blocks, a developer can create complex applications graphically." (Source: http://www.bitreactive.com/reactive-blocks/)

There are other IoT visual programming tools, such as Grasp.io and DGLux5.

## Conclusion

At the end of this article, you gained an overview of the most important IoT visual programming tools that you can use to develop IoT apps. These tools help developers to build complex IoT solutions without writing tons of code lines. This can be an easy solution for people that are more focused on the hardware part of the IoT and want to develop and prototyping an IoT app easily without spending too much time. Moreover, these IoT visual programming tools support several prototyping boards, ranging from Arduino to Raspberry Pi.

Topics:

iot ,node-red ,wia ,visual programming ,tools ,visuino ,embrio ,nodejs ,ide
