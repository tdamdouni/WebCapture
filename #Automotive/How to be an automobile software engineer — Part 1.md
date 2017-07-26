# How to be an automobile software engineer — Part 1

_Captured: 2015-12-09 at 18:29 from [medium.com](https://medium.com/@viktorschepik/how-to-be-an-automobile-software-engineer-part-1-7729a780d89b#.7cjgbpsxk)_

#### Understanding software in a car

Many software developers who get into an automotive job feel really lost regarding the kind of software they find there. It is so different compared to other kinds of software like web, desktop and even mobile applications that automotive rookies think they have entered a maze like Thomas in the movie "Maze Runner". Watch the first 50 seconds or so to get an impression of the shock when you step into automotive software development.

What they find are terms and tools they have never heard about. When I got into a job interview in the automotive industry I asked which IDE they were using and the interviewer was a little bit irritated about my question. I was used to Visual Studio and expected naively something similar for developing embedded software. Little did I know what was in store for me! A plethora of small and large (in the sense of complexity) tools were waiting to overrun me.

Tools are not the only challenge about working in automotive software development. Newbies are challenged by finding entry-level documentation or even tutorials for automotive software libraries or architectures. The term "Tutorial" sounds odd in this industry since it is a very closed community. And you can't even call the automobile industry a community because everybody is frightened of being outperformed by a competitor if they share anything about how they develop software in their company. In order to learn about some tools and frameworks you can join amazingly expensive courses but your company must be willing to pay a lot of money for it and you will have to wait for several weeks until you get the knowledge you need now. It's a great pity that it is so hard to get into the automobile way of thinking of how to build embedded software and that's where I want to tie on.

Since I have been switching back and forth between the worlds of web/desktop application development and embedded software development, I have seen the problems of novices coming from web/desktop application development. The same is true for graduates starting their career at an automotive company.

In this post and in the following posts I would like to give you a grasp about how an automotive embedded software application works as well as an indepth insight into the exotic embedded software architecture.

#### **Which topics will be considered?**

  * How does the embedded software augment what happens with the car?
  * How does the embedded software control a car?
  * What are typical CPU constraints?
  * How does the embedded software application process continuous data from sensors?
  * How is the software structured and how do the individual pieces collaborate to control the car?

I will answer these questions through a concrete example and want to guide you by developing the software architecture of an embedded software application. The example will be a fully electronic steering system. This steering system isn't real but architecturally similar to the steering system that you would most probably find in your own car. I will concentrate on the architecture and therefore will over-simplify the actual steering functionality.

You can watch an interesting example of an electronic steering system developed by a team I have been part of.

This example steering system is partially controlled by software. Partially means that it supports the driver but the driver has the ultimate control of steering the car.

#### Developing a car steering system in a sandbox

Let's assume we want to develop a fully electronic steering system in which the steering wheel is not directly connected to the wheels. Instead a sensor measures the steering wheel angle and sends it to our software. The automotive term for this would be Steer-by-Wire. You won't believe it but Nissan has already brought a car with Steer-by-Wire to the market: <http://www.caranddriver.com/features/electric-feel-nissan-digitizes-steering-but-the-wheel-remains-feature>

The software runs on a tiny CPU or to be exact a microcontroller which has a network connection to the sensor.

![](https://cdn-images-1.medium.com/max/800/1*qzItaLZDJrNqe3gLftftcg.png)

When the driver turns the steering wheel the software gets to know about this through a steering wheel sensor which sends continuously the current angle of the steering wheel. E.g. when the driver turns the wheel 90° to the right in 1 second the sensor signal will proceed as in the following diagram.

![](https://cdn-images-1.medium.com/max/800/1*1cU8VmOQlCM_Hjh-bzrs9g.png)

On the other end the software controls an electrical motor that moves the steering rack from left to right and vice versa changing the angle of the front wheels of the car. This way the software is able to steer the car to the left and right side. The connection from the microcontroller running the software to the electrical motor is established through an electrical control unit (ECU) containing the microcontroller, and a power stage that controls the power supply of the motor. This way the software is able to control the electrical current that a motor needs to move the steering rack.

![](https://cdn-images-1.medium.com/max/800/1*uS-eMa6j_ZEPDKHz9JR4HA.png)

Assuming the software is finished and working correctly the position of the steering rack would follow the movement of the steering wheel almost instantly.

![](https://cdn-images-1.medium.com/max/800/1*jBCnEUJCCyPHH2u0IkZOIg.png)

It gets clear that processing this data is not event driven like applications with graphical user interfaces or even batch-driven. Instead the input values must be processed continuously and in a timely manner. When the software needs too much time to process the sensor data, the steering rack and the front wheels of the car will follow with a delay that the driver will recognize. Most probably the driver will loose control over the car in an extreme situation e.g. if he wants to avoid an obstruction at the street and the car movement does not immediately react to his steering attempts. This scenario of course burdens hard timing requirements onto the software especially with regards to the very limited CPU performance of a typical ECU in the car.

The next parts of this series will elude the software architecture that solves these problems and will hopefully help aspiring software engineers to get a clear understanding of the principles behind embedded software architecture.

I am looking forward to answer your questions.

**[How to be an automobile software engineer -- Part 2**  
medium.com](https://medium.com/p/240369393ef5)
