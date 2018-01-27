# Create an Electro-Theremin

_Captured: 2017-11-27 at 19:05 from [tinkercademy.com](https://tinkercademy.com/tutorials/electro-theremin/)_

Get down to the funky sounds of electric 'analog' music

# **Materials**

  * 1 x BBC micro:bit
  * 1 x Micro USB cable
  * 1 x Buzzer
  * 2 x F-F Jumper Wires

  * 1 x Potentiometer
![](https://i2.wp.com/tinkercademy.com/wp-content/uploads/2017/10/WP_20171031_17_04_42_Pro-2.jpg?w=1080&ssl=1)

# **Step 1**

  * Plug in your Buzzer to Pin0, making sure the positive lead is connected to the yellow signal pin and the negative lead is connected to the black ground pin on the breakout board.
  * Plug in the potentiometer to Pin1, match the colours of the wires to the ones on the breakout board!

# Step 2

  * In Makecode, we'll be tracking the value of the potentiometer using a variable. Variables are like buckets that can hold changing values.
  * Make a new variable called _reading_ (or anything you like, really) in the **Variable **drawer.
  * We want to constantly set our _reading_ variable to the analog value of the potentiometer instead of the digital.
  * Reading the analog value allows us to access a whole range of signals from the potentiometer, instead of just a digital 1 or 0. Find this block in the **Pins** drawer.

# **Step 3**

  * Check your minimum and maximum values for your potentiometer by showing the number of the _reading_ variable.
  * Turning the knob ounter-clockwise all the way gives you the minimum, and clockwise all the way gives you maximum.
  * Notice how the values jump? That's because the micro:bit takes some time to scroll a large number across the screen, and by the time you read a new value, the potentiometer would be way ahead! 

# Step 4

  * Now we're going to use those values you just read from your potentiometer to map out your notes!
  * Our music blocks may not have as wide a range as your potentiometer. In this instance, we want to make sure the highest potentiometer value still corresponds to the highest note we can play.
  * Check out the value of the lowest and highest notes in the micro:bit piano keys. 
  * Using the map block from the **Pins** drawer to key in all the values. 

# **Step 5**

  * You may have noticed we made another variable called _note_ in the previous step, make sure you set the _note_ variable to the mapped values. 
  * Ring the tone using the _note_ variable. 
  * Upload it all into your micro:bit and you are ready to make some noise!
  *     *       * Now you've learned how to play around with the potentiometer, you can try using it to control LEDs, servos, and other components! And if you get your hands on another analog sensor, you'll know just how to use it!
