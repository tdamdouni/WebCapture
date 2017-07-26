# How to be an automobile software engineer — Part 2

_Captured: 2015-12-09 at 18:30 from [medium.com](https://medium.com/@viktorschepik/how-to-be-an-automobile-software-engineer-part-2-240369393ef5#.aj9qa0h85)_

#### What drives automobile software architecture

This is a follow-up to Part 1. Make sure to have a look at it if you want to know how quirky the automobile industry is.

**[How to be an automobile software engineer -- Part 1**  
medium.com](https://medium.com/p/7729a780d89b)

In Part 1 of this series we started the endeavour to build a Steer-By-Wire system of a car, at least in our heads. I showed you a sketch of such a system where you can see the essential parts and connections of it.

![](https://d262ilb51hltx0.cloudfront.net/max/800/1*qzItaLZDJrNqe3gLftftcg.png)

> _Simple Steer-By-Wire System_

#### The Rhythm of the System

So how do we connect the parts of our system? We connect the steering wheel sensor which is a position sensor via the FlexRay bus with the ECU. This is possible because the sensor itself is quite intelligent and is able to communicate on a FlexRay bus contrary to a simple temperature sensor that just outputs a voltage according to the measured temperature.

Today's cars own two kind of network technologies: CAN and FlexRay. FlexRay could be regarded as a successor to CAN. Its main advantage is that we can determine exactly when a certain signal is transmitted therefore making the protocol deterministic. The systems of a car like the brake controller, the steering system and some other intelligent sensors communicate via such a network with each other.

Typical FlexRay communication partitions the bus time into slots where certain signals or values must be sent by a certain sender. Measuring physical values, sending the data, processing it and controlling devices follow the rhythm of the communication bus. The diagram shows recurring FlexRay communication slots which are used to send data around the bus.

![](https://d262ilb51hltx0.cloudfront.net/max/800/1*6gXy8odRpL0QBwfPR1kk-g.png)

> _FlexRay Periodic Communication_

That means that the steering wheel sensor must send its current value when the corresponding slot is next and must not send its value in-between. The above diagram exaggerates dramatically the possible changes of the steering wheel position since a typical period time for sending the value is 10 milliseconds. And a human driver won't be able to turn the wheel by 5° in 10 milliseconds. But for illustration purposes let's stick to the above example.

Our microcontroller contains a FlexRay controller that receives the values sent periodically by the steering wheel sensor / position sensor. As you all probably have figured out the software running on the CPU must also take periodically the FlexRay values and process them. Processing in this particular case means determining the desired position of the steering rack (see diagram „Simple Steer-By-Wire System" at the top) corresponding to the steering wheel position. From this desired rack position the desired motor angle position can be calculated by a mathematical formula that takes the different gear translations into account.

![](https://d262ilb51hltx0.cloudfront.net/max/800/1*TA6cIaQbIarmkjIeQUeN2Q.png)

> _Processing chain when driver does nothing_

As you guys might have noticed there is an unfamiliar block present in the figure above called PWM. That's the PWM output that controls the electrical current of the power stage that in turn regulates the power supply of the motor. But what is PWM?

PWM stands for Pulse Width Modulation and is well established technique to control the power supplied to electrical devices. In short you control the power in percentage of the maximum power, so 0% means no power and 100% means full power that the power stage can provide to the motor. As always you can find details in Wikipedia:

What happens when the driver turns the wheel? The software running on the CPU gets the new steering wheel position at some point of time and derives the PWM value that is necessary to move the motor. The motor in turn moves the steering rack. In the example below the driver turns the wheel by 5° (1). The sensor measures the position and puts the position value onto the FlexRay bus (2). Our FlexRay controller receives the value (3), the software calculates the necessary PWM value (4) and puts it into the PWM module of the microcontroller (5). The PWM module controls the electrical current which in turn regulates the power the motor gets from the power stage (6). This power moves the motor (7) and the motor moves the steering rack (8).

![](https://d262ilb51hltx0.cloudfront.net/max/800/1*ynpRKzqJhmLEzLlVQX4jFg.png)

> _Processing chain when driver turns the steering wheel_

As you all are already aware of it that a lot of different physical calculations and units come into play in the previous example. E.g. somehow the PWM value in % must be derived from the steering wheel position in degrees. In reality the current position of the motor must be considered too because only then it is clear in which direction and with which speed the motor must be moved. But unfortunately that's a topic related to control engineering and not within the scope of this article.

I am a software developer by passion and an architect by profession, and therefore I am more interested in the software architecture that supports such a system. It gets clear that the software architecture has to follow the rhythm of the system and it could have been simpler if there was only one rhythm. But unfortunately there are several different rhythms that are interconnected. E.g. the rhythm for controlling the motor must be much faster than that of the bus communication in order to get a nice steering feeling and avoid jitter.

#### Rhythmic Software Architecture

Thus the environment of the software demands rhythmic processing of signals. Rhythmic means that the software has to run in cycles. Have you ever seen a software architecture that supports it? In case you didn't don't be scared. We dive straight in.

Let's have a look at how we could partition our software that runs on the CPU in the above picture („Processing chain when driver turns the steering wheel"). If you think in responsibilities of software components you are obviously going to realize that we have 3 of them: one to receive the FlexRay signal, one to calculate PWM value from the FlexRay signal and one to control the PWM output. The next picture stacks these components onto the microcontroller and, voila, a layered software architecture emerges.

![](https://d262ilb51hltx0.cloudfront.net/max/800/1*cTWbAaWl5Di1rpngCR-Lhg.png)

> _Layered architecture_

„Com" stands for Communication and it reads the FlexRay signal from the FlexRay controller inside the microcontroller. It is also involved in checking if the transmission of the signal was correct (e.g. by using checksums) and makes the signal available to the rest of the software as the steering wheel position. The Steering component takes this value and calculates the necessary PWM value through a clever algorithm that took years to develop. No joke, developing such an algorithm may take a lot of time because in the end it's all about the driver experience. And that means a lot of evaluations of the algorithm in a real car in many different driving situations. Coming back to the layered architecture the PWM component is left over. The PWM component takes the calculated PWM value and controls the PWM output of the microcontroller.

Let's get back to our timing concepts. The data flow has to occur every time the FlexRay signal arrives and if this FlexRay signal is sent every 10 milliseconds we get this picture:

![](https://d262ilb51hltx0.cloudfront.net/max/800/1*kpMLEJKNJqAe1_b9EMBRLw.png)

> _Simple timing view_

The arrival of the FlexRay signal triggers the execution of the 3 dependent functions or components. At the end the PWM output is set. And this happens repeatedly every 10 milliseconds. This is the rhythm of the software.

When we obtain the signal values of the output of the software we get a diagram like this:

![](https://d262ilb51hltx0.cloudfront.net/max/800/1*xYo1tf9sJlVvvFPBdcAgUg.png)

> _Stepped output_

The PWM is calculated and output every 10 milliseconds and hence we have reached our first milestone. We are now able to steer our car!

As you all might have guessed the steps in the output will result in non-smooth movement of the electrical motor. Better would be something like this:

![](https://d262ilb51hltx0.cloudfront.net/max/800/1*wNYGEF5JzCjT8fnG3j-Hiw.png)

> _Smooth Output_

That would be a bad experience for the driver when the front wheels judder during the turning of the steering wheel. The software architecture must be enhanced. That is subject to the next parts in this series and I hope you will be excited to continue reading. I also really hope that you all guys get to grip automobile software architecture. As you have seen software architecture is driven by the environment or context of the system.

I am looking forward to answer your questions and comments.
