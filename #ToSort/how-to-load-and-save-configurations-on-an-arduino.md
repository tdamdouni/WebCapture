# How to Load and Save Configurations on an Arduino

_Captured: 2018-01-16 at 18:36 from [dzone.com](https://dzone.com/articles/how-to-load-and-save-configurations-on-an-arduino?edition=354096&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202018-01-16)_

Earlier, we wrote a rather deep post about a non-volatile (not lost when power is) way to store data [here](https://www.norwegiancreations.com/2017/02/using-eeprom-to-store-data-on-the-arduino/), but in this post, we will focus on the following question:

> How can I save and load configuration data on my Arduino?

And this data should, of course, not be erased when the power is gone!

To solve this, we use an often forgotten little feature on the microcontroller that resides on most Arduino boards (on the Arduino Uno we use here: ATMEGA328P-PU), namely EEPROM.

> **EEPROM** stands for Electrically Erasable Programmable Read-Only Memory. This memory is _non-volatile_, which means that the data doesn't get erased when the board loses power.

## Implementation

We want to have a globally defined configuration layout. We can solve this by defining a struct that holds the data. Here, the configuration is only a lonely integer, but this is, of course, easy and possible to change:

As you can see on line 3, we have written about a "version". This is to detect if the data that resides in the EEPROM is valid configuration data!

If we cannot find valid data in the EEPROM, we need to write and use default configuration settings instead.

We can define the config version, and fill it with default settings like this:

And if we combine all this with some EEPROM magic that loads a configuration struct (if it has the correct CONFIG_VERSION) and saves it back (overwrite) when we want, we have what we need!

Now the program saves a new config every 5 seconds (remember that EEPROM has a max count on write cycles of ~100000).

The output in the serial terminal looks like this when it is booted up with a valid configuration stored in the EEPROM, and then restarted after a minute:

You can, of course, edit and include what you need in the `configuration_type` to make it suit your needs!
