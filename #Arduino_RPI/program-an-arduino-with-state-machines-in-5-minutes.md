# Program an Arduino with State Machines in 5 Minutes

_Captured: 2018-10-23 at 12:51 from [blogs.itemis.com](https://blogs.itemis.com/en/program-an-arduino-with-statemachines-in-5-minutes?hs_fb_ad_id=6080348829744&utm_campaign=YAKINDU+Statechart+Tools&hs_fb_campaign_id=6064207344544&source=fb&hs_fb_adset_id=6080348830144&hs_parent_creative_id=6064800275144&utm_source=facebook&hs_fb_account_id=466432463486493&utm_medium=paid)_

Did you ever program an Arduino? Have you ever been worried about complex control flows written in pure C? Maybe you have already heard of statecharts and state machines? In this blog post, I will show you how to program an Arduino in just 5 minutes in a model-driven way with the help of [YAKINDU Statechart Tools](https://www.itemis.com/en/yakindu/statechart-tools/) (SCT).

![YAKINDU Statecharts for Arduino](https://blogs.itemis.com/hs-fs/hubfs/Social_Media/Diverse/Statechart-Platine-Arduino.jpg?t=1540293311980&width=1920&name=Statechart-Platine-Arduino.jpg)

> _YAKINDU Statecharts for Arduino_

There have been several attempts to program an Arduino with YAKINDU SCT as described by [Marco Scholtyssek](http://scholtyssek.org/blog/2013/10/21/yakindu-statechart-tools-arduino-integration/) or [Rene Beckmann](https://blogs.itemis.com/en/developing-software-for-arduino-with-yakindu-statechart-tools). However, when I tried to teach how to program an Arduino with YAKINDU SCT within the [Automotive Software Engineering Summer School 2016](https://internationalresearchdortmund.wikispaces.com/SummerSchool2016) at the University of Applied Sciences and Arts in Dortmund I found out that it's hard to understand and implement without appropriate tooling. So I sat down and implemented Arduino support for YAKINDU SCT to generate lots of the glue code that is needed to run state machines on the Arduino.

[YAKINDU Statechart Tools for Arduino](https://github.com/wendehals/arduino_sct_tools) is based on Eclipse, YAKINDU Statechart Tools, and the Eclipse C/C++ Development Tooling (CDT). It sets up an initial project containing an empty statechart that you just need to fill with your own ideas. The only part that you still need to program on your own is the connection between the statechart and the hardware, i.e. initializing the hardware and updating the state of the hardware depending on the state of the statechart and vice-versa.

Now, let's have a look at the tooling. In the screenshot depicted below you'll find the well known Arduino "Hello World" example - a blinking LED - programmed as a statechart. I created an Arduino SCT project with the help of a wizard. It opened an empty statechart with an empty interface declaration. I will use this statechart to model a blinking LED and generate the state machine running on an Arduino Uno board.

![YAKINDU Statechart Tools for Arduino: Blink state machine example](https://blogs.itemis.com/hs-fs/hubfs/blog-files/SCTforArduino_Blink.png?t=1540293311980&width=3072&name=SCTforArduino_Blink.png)

> _YAKINDU Statechart Tools for Arduino: Blink state machine example_

The LED has two states, on and off. Therefore, I declare a boolean variable `on` representing on and off with its values `true` and `false` in the interface. Within the statechart, I create the two states `On` and `Off`. Once deployed to the Arduino, the program's execution starts by entering the statechart through the black dot - the `Entry` state - depicted in the statechart. After entering the statechart, it immediately changes its state through the first transition - it's the arrow from the `Entry` state to the `On` state. When entering the `On` state, the boolean variable `on` is set to `true`. After 500 milliseconds, the state changes to `Off` and the variable `on` is set to `false`. Again, after another 500 milliseconds, it switches back to `On`. This goes on and on and on .... until you pull the plug.

Once I finish the modelling I might want to simulate my model with YAKINDU SCT to find out if it works as expected. You will find more details about modelling and simulation in the [YAKINDU SCT documentation](https://www.itemis.com/en/yakindu/statechart-tools/documentation/user-guide/). Based on this statechart, I generate a state machine in C++ code that executes the statechart on my Arduino. All that I still need to do is connecting the statechart with the hardware. I do this by editing the `init()` and `runCycle()` methods of the `BlinkConnector` class:

  * In the `init()` method I set up the LED built into the Arduino Uno board. This method is called once when starting the program's execution - analog to the `setup()` function in a common Arduino sketch.
  * The `runCycle()` method is the analogon for the `loop()` function of an Arduino sketch. It is called regularly, once in every cycle of the statechart's execution. Here, I set the LED's pin accordingly to the statechart's boolean variable `on`.

Now, I compile the code and upload it to my Arduino board. There it is, a blinking LED in five minutes!

![YAKINDU Statechart Tools for Arduino: Generated C++ code](https://blogs.itemis.com/hs-fs/hubfs/blog-files/SCTforArduino_Blink_generatedCode.png?t=1540293311980&width=3072&name=SCTforArduino_Blink_generatedCode.png)

> _YAKINDU Statechart Tools for Arduino: Generated C++ code_

Ok, you're right, this example may be implemented in plain C and uploaded to the Arduino in less than five minutes. It's that simple. But could you imagine the effort of developing a state machine in plain C with the complexity of a pedestrian crossing light shown in the picture below? And even this example is still a simple one. By the way, you will find this example as well as the Blink example in the YAKINDU SCT for Arduino environment.

![YAKINDU Statechart Tools for Arduino: State machine describes pedestrian crossing example](https://blogs.itemis.com/hs-fs/hubfs/blog-files/SCTforArduino_PedestrianCrossing.png?t=1540293311980&width=3072&name=SCTforArduino_PedestrianCrossing.png)

> _YAKINDU Statechart Tools for Arduino: State machine describes pedestrian crossing example_

On my [GitHub pages](https://wendehals.github.io/arduino_sct_tools/) you will find a complete walkthrough starting from installation, through setup, modelling, simulation, code generation, and code deployment. It is also integrated into the online help of YAKINDU Statechart Tools for Arduino.

Currently, YAKINDU SCT for Arduino only supports the ATmega 168/328 microprocessors used for example on the widely adopted and well known Arduino Uno boards. Additionally, it uses Timer 1 of the microprocessor by default. If some library that you need is also depending on Timer 1, you're in trouble. There are still various other limitations as well. So, in the near future I plan to extend the YAKINDU SCT for Arduino tooling to support more timer implementations and other microprocessors.

Stay tuned!
