# Using PWM with the Kitronik Motor Driver Board

_Captured: 2017-12-25 at 15:11 from [www.kitronik.co.uk](https://www.kitronik.co.uk/blog/using-pwm-kitronik-motor-driver-board)_

Way back when we first released our [Motor Driver Board](https://www.kitronik.co.uk/5620-motor-driver-board-for-the-bbc-microbit-v2.html) the [microbit](https://www.kitronik.co.uk/microbit.html) Block Editor only allowed digital write on the pins we used for controlling motors. This meant that motors had to be full on or off. Thanks to an update in the [MakeCode editor](https://pxt.microbit.org/) you can now use PWM to control the motors and therefore the speed of your buggy.

![PWM robot-buggy-introduction-main-870](https://www.kitronik.co.uk/wp/wp-content/uploads/2017/04/robot-buggy-introduction-main-870.jpg)

## What is PWM?

PWM or Pulse Width Modulation is a way of varying power into a pulsing signal. This lets us control how much power is sent to the motors by controlling the pulse.

When we talk about duty cycle we mean the portion of 'on' time compared to the total time; a low duty cycle corresponds to low power because the power is off for most of the time. Duty cycle is expressed in percent, 100% being fully on.

![experiment-4-pulse-graph-870](https://www.kitronik.co.uk/wp/wp-content/uploads/2016/04/experiment-4-pulse-graph-870-.jpg)

## Writing The Code:

In this example, we're going to use two microbits. One, the handset, is going to be used to send various commands to the other, the motor controller. We're going to simply send a different value from the handset based upon if button A, B, or both are pressed. We'll add an on shake command to bring the unit back to a stop. Using the [MakeCode editor](https://pxt.microbit.org/) create this code or download it from the bottom of this guide.

![handset_code_870](https://www.kitronik.co.uk/wp/wp-content/uploads/2017/05/handset_code_870.jpg)

On the motor controller, we're going to see which number is received and apply a different frequency to make the motors go faster or slower. We'll achieve this by using while/do loops.

If the received number is 0 we'll set all pins to 0. If the received number is 1 we'll set pin 0 and pin 8 to 300 (analogue) and leave P16 and P12 at 0. By increasing the values of pin 0 and pin 8 (up to 1023) we increase the speed, so we'll add options for received number 2 and 3 as you can see below.

As you can see from the code we are using two different types of block to send power to the motors, the digital write and analog write. Behind the analog write block is a PWM pulse and behind the digital write is an on/off command, or full power/no power command.

Using the MakeCode editor create this code or download it from the bottom of this guide.

![controller_code](https://www.kitronik.co.uk/wp/wp-content/uploads/2017/05/controller_code.jpg)

## In Action:

As you can see from this quick video the buggy goes through three different speed cycles as we change the options on the handset.

>

## New Blocks:

To make it even easier for you, we've created a package that lets you add our Motor Driver blocks to the MakeCode editor.

Click Add Package and paste https://github.com/KitronikLtd/pxt-kitronik-motor-driver into the box and hit search.

![add-package-870](https://www.kitronik.co.uk/wp/wp-content/uploads/2017/05/add-package-870.jpg)

> _You can now add the blocks to your project as normal._

![kitronik-motor-driver-blocks-870](https://www.kitronik.co.uk/wp/wp-content/uploads/2017/05/kitronik-motor-driver-blocks-870.jpg)

Note: We used this for our[ line following buggy](https://www.kitronik.co.uk/5604-line-following-buggy-for-the-bbc-microbit.html) in the video above but we did swap the wires around on the motor to set the buggy in line with "forward" in the block as can be seen below. Note: The blocks go from a speed of 0 to 100, not 1023 as with an analogue pin write.

![buggy-rewired-870](https://www.kitronik.co.uk/wp/wp-content/uploads/2017/05/buggy-rewired-870.jpg)

> _Download the handset code here and the motor controller code here._

(C)Kitronik Ltd - You may print this page & link to it, but must not copy the page or part thereof without Kitronik's prior written consent.

![Resources](https://www.kitronik.co.uk/img/banners/resources.png)

> _<- Previous Post Next Post ->_
