# Choosing the correct resistor for your LED

_Captured: 2017-10-24 at 19:12 from [forum.digikey.com](https://forum.digikey.com/t/choosing-the-correct-resistor-for-your-led/183)_

Choosing the correct resistor value is imperative to insure your LED receives proper voltage and current. To ensure you have the correct resistor you will need to know three values from your circuit.

Vs - Supply Voltage - This is the power supply that you are using to power your circuit.  
Vf - Forward voltage for your LED. This is the voltage required to turn on your LED.  
If - Forward Current for your LED. This is the current required by your LED for operation.

With these numbers you can calculate the resistance ® required with the following equation.  
R = (Vs - Vf) / If

For my example I am going to use LED part [67-2250-ND10](https://www.digikey.com/short/3wv0mw). This LED has a forward voltage of 3.2V and a forward current of 20mA. I will be powering my circuit with a 9V battery.

R=(9V-3.2V)/.020A  
R= 290ohms

Next you will want to make sure you calculate the wattage required for your resistor to ensure that your resistor can handle the load.Using Ohm's law you can verify the voltage that is being dropped across your resistor.  
Resistance x Current = Voltage in my example would be 290ohm x .020A = 5.8V  
To calculate power you would then take Volts x Amps = Watts. In our example this would be 5.8V x .020A = .116W  
So the required resistor for my example circuit would be 290ohms and 1/8th watt.

To help simplify the process Digi-Key has an [LED Series Resistor Calculator62](http://www.digikey.com/en/resources/conversion-calculators/conversion-calculator-led-series-resistor) that will calculate you required resistance and power ratings for your LED circuit. Digi-Key also has a separate [Ohm's Law Calculator14](http://www.digikey.com/en/resources/conversion-calculators/conversion-calculator-ohms) for the customer convenience.
