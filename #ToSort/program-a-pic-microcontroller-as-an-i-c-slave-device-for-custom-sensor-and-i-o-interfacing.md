# Program a PIC Microcontroller as an I2C Slave Device for Custom Sensor and I/O Interfacing

_Captured: 2017-12-18 at 20:02 from [www.allaboutcircuits.com](https://www.allaboutcircuits.com/projects/program-a-pic-chip-as-an-i2c-slave-device-for-custom-sensor-and-i-o-interfa/)_

No I2C interface with that sensor? No problem. Program a PIC chip as an I2C slave device for custom sensor and I/O interfacing. Here, we use three DHT22 sensors on a single I2C interface.

The Inter-Integrated Circuit (I2C) bus is a common and convenient technique to interface devices to embedded controllers. This popular serial interface protocol allows a microcontroller board, such as an Arduino UNO, to communicate with a peripheral device, such as a sensor, using two communication wires, clock and data (SCL and SDA), and two power supply wires (Vcc and GND). Each I2C peripheral device is addressable, allowing multiple devices to be attached to the same I2C connections and that is a major reason for its popularity.

But, what do you do when the peripheral device you want to use does not use an I2C communication protocol? One solution is to roll your own I2C interface. This project presents a relatively easy and inexpensive way to do just that.

Specifically, we will use an economical PIC12F1840 IC as a slave I2C device that will interface to an Arduino UNO as well as most any microcontroller board using a single master / multiple slaves, I2C scheme.

![The project circuits on breadboards.](https://www.allaboutcircuits.com/uploads/articles/IMG_1082r.jpg)

> _The project circuit on breadboards._

To illustrate the technique in a manner that has some utility, the PIC chip will interface with three DHT22 (aka AM2302) humidity and temperature sensors. The final result is an easy method to deploy all three sensors using a single I2C bus. The technique can be expanded to include other custom sensor applications as well as custom I/O expansions and combinations of the two.

### The Hardware

The circuit consists of the PIC I2C interface and, separately, the three DHT sensors. The PIC I2C interface contains the 12F1840 IC, a few support components, a header/jumper (JP1) to connect the board to the master and three additional headers/jumpers to attach the three sensor boards. The four connections on J1 for the Arduino UNO are +5v, GND, SDA and SCL which are all available on the Arduino board headers. The 12F1840 includes 6 I/O pins. Two of these pins, RA1 and RA2, form the SDA and SCL lines for I2C communications. I have included 10K, I2C pull-up resistors (R1 and R2) on these lines and they work fine, but you may want to adjust the values to your application.

Additionally, those resistors may need to be eliminated completely if you already have pull-up resistors on the I2C lines on your system. Three I/O pins, RA0, RA4 and RA5, connect to the data lines on DHT22 sensors #1, #2 and #3, respectively. The remaining pin (RA3) is unused and left unconnected. With additional expansion circuitry, this pin could function as a general purpose input or to enable a hardware reset (MCLR).

![Figure 1. Schematic for the PIC I2C Board.](https://www.allaboutcircuits.com/uploads/articles/PIC2DHTr1.jpg)

> _Figure 1. Schematic for the PIC I2C Board._

PIC I2C Board parts list.

Part Description

U1
PIC 12F1840/P

C1
0.1uf capacitor

R1,R2
10K resistor

J1,DHT1-3
4-pin header/jumper

Cables
3 X 4-pin

Each of the sensors is mounted on a separate board with the intention that they will be placed at some distance from each other and connected to the I2C board via 4-pin cables. Since only 3 of the 4 pins on the DHT22 are usable, you could substitute 3 pin cables and connectors (making the appropriate connections) if desired.

![The DHT22 or AM2302 Humidity and Temperature Sensor. Pins: 1-Vdd, 2-Data, 3 n/c, 4-GND.](https://www.allaboutcircuits.com/uploads/articles/IMG_1099r.jpg)

> _The DHT22 or AM2302 humidity and temperature sensor: Pins: 1-Vdd, 2-Data, 3 n/c, 4-GND._

The sensor boards are also relatively simple, containing only the DHT22 sensor, a pull-up resistor on the data line, and a bypass capacitor across the power lines.

![Figure 2. Schematic for a single DHT22 sensor. One board is required for each of the 3 sensors.](https://www.allaboutcircuits.com/uploads/articles/DHTBB.jpg)

> _Figure 2. Schematic for a single DHT22 sensor. One board is required for each of the 3 sensors._

Sensor Boards parts list 

Part Description

DHT22
DHT22 sensor

C1
0.01 uf capacitor

R1
4.7K resistor

J1
4-pin header/jumper

The project, as presented, is designed for use with 5v, but I also tested it with 3.3v and it works fine, as that voltage is within the operating range of both the PIC IC and the DHT22.

### Implementing a Custom I2C Sensor

The PIC 12F1840 is an example of Microchip's enhanced 8-bit mid-range architecture. It is an 8-pin microcontroller that includes a large number of peripheral device functions. Chief among these peripheral device functions, for the present project, is the Master Synchronous Serial Port or MSSP. This feature allows us to implement an I2C interface such that the chip will function as a slave I2C device. Perhaps best of all, the software "heavy lifting" has already been done for us in an application note (AN734C). The code in that application note forms the basis of our I2C engine. It is interrupt-driven and will allow the chip to essentially function as a 32-byte memory array allowing two-way reading and writing between master and slave devices. The attached program includes code from the application note modified only slightly for use with the 12F1840.

The master I2C device (in this example, an Arduino UNO) will issue commands to the slave I2C device by writing to a select location in the memory array. The PIC, as slave I2C device, will execute the commands (i.e., reading the DHT22 sensors) and report back status and sensor information through the memory array. The master then reads the memory array to retrieve the sensor readings.

### Memory Map

We will refer to the 32-byte memory array as Array[0] through Array[31]. Array[0] serves as the location where the master (the Arduino) will issue a command, and where the slave (PIC) will report status that will be read by the master. In this regard, the PIC will return one of three values as described in the table. These values will indicate a power-up status, a successful execution of a valid command, and reception of a bad or unknown command.

ARRAY[0] STATUS - Value set by the PIC to report status. Status Values 

0x00
Power up value. Also, the value set on software PIC reset

0x01
Last command was executed successfully

0xF1
Bad (unknown) command was requested

The Arduino will write to Array[0] with one of four possible command values as described below. These will instruct the PIC to either read one of the DHT sensors or to reset.

ARRAY[0] COMMAND - Value set by the Arduino to issue a command. Command Values 

0x02
Read DHT sensor #1

0x03
Read DHT sensor #2

0x04
Read DHT sensor #3

0x10
Execute a software reset of the PIC

When a sensor read command has been issued, by writing either 0x02, 0x03 or 0x04 to Array[0] and the PIC has returned a successful execution status, by writing 0x01 to Array[0], the sensor data will be available to the Arduino by reading the memory array.

The DHT22 returns 5 bytes to indicate the humidity (relative humidity or RH) and temperature (degrees Celsius) as follows: RH integral, RH decimal, Temperature integral, Temperature decimal, and a checksum which is the value of the sum of all four bytes AND 255. These 5 bytes will be written into different memory locations by the PIC following the read sensor commands. Array[16]-Array[31] locations are unused free memory available for custom use.

ARRAY memory locations - Values set by the PIC for reading by the Arduino. Sensor Data Information Map 

Array[1]-Array[5]
DHT sensor #1: RH integral, RH decimal, Temp integral, Temp decimal, checksum

Array[6]-Array[10]
DHT sensor #1: RH integral, RH decimal, Temp integral, Temp decimal, checksum

Array[11]-Array[15]
DHT sensor #1: RH integral, RH decimal, Temp integral, Temp decimal, checksum

Array[16]-Array[32]
Available for use

The final command available is 0x10 and will cause a software reset of the PIC 12F1840. Normally, this command does not need to be used, but it could be useful in the case of an unexpected situation.

### Reading the DHT22 Temperature and Humidity Sensor

The job of reading the DHT22 sensors and storing them in the memory array also falls to the PIC chip. The low-price, availability and relative reliability of the DHT22 have made it ubiquitous. The serial protocol that the chip uses, however, requires very precise timing. These timing requirements can be problematic for systems using relatively slow I/O or with systems (e.g., System on Chip [SOC] ICs) whose multiple high-priority functions can make the required dedicated timing requirements troublesome. In that regard, it makes good sense to "off load" the job to a dedicated IC.

Communication with the sensor is through a specific "one-wire" serial protocol that should not be confused with the Dallas/Maxim semiconductor one-wire protocol - the two are completely different. Three connections are involved (Vcc, GND and Data). The data pin is where all the manipulations take place and a careful reading of the datasheet will provide the details.

Briefly, the following steps describe the interaction, from the PIC side, required to read the sensor and the included MPASM program has been liberally commented to facilitate following the program flow.

1\. Set the data line to output, set it low and wait for 18 microseconds.

2\. Take the data line high for 30 microseconds.

3\. Set the data line to input and monitor its status. The DHT22 should set it low for 80 microseconds and then high for 80 microseconds.

4\. Steps 1-3 are the preamble to the data stream. Next, the DHT22 will set the data line low for 50 microseconds which signals the start of a data bit.

5\. Here is where it gets a bit tricky. Following the start bit time, the DHT22 will bring the data line high for either ~27 microseconds or for 70 microseconds. The former signals the data bit is '0' and the latter signals that the data bit is '1'.

6\. Following the data bit (in step 5 above), the DHT22 will go into another 50 microsecond start bit period followed by another data bit (either a '0' or '1' as described in 5 above) and this sequence is repeated for 40 bits, constituting the 5 bytes of sensor data (RH integral, RH decimal, Temperature integral, Temperature decimal, and checksum).

You can see that the protocol requires precise timing and that the time to read the sensor is variable in that it depends upon the number of '0' and '1' bits in the reading. One strategy is to measure each of the intervals and subsequently decide if the data bit fits into a '0' or '1' interval. I chose a different strategy, described below, which is less demanding and very reliable.

![Figure 3. Strategy to distinguish a ‘0’ from a ‘1’ bit in the serial stream.](https://www.allaboutcircuits.com/uploads/articles/Read_Strategy1.jpg)

> _Figure 3. Strategy to distinguish a '0' from a '1' bit in the serial stream._

After the preamble, we wait for the end of the start bit time and then delay for about 43 microseconds and then read the data line. If the data line is low, then the bit was a '0' and we will be in the next start bit time. In this case, we record the bit as a '0' and wait for the start bit time to end before reading the next bit. If the data line is high, the bit is a '1' and we are still in the bit time. In this case, we record the bit as a '1' and then wait for the next start bit time to begin and then wait for the start bit time to end before reading the next bit.

When the PIC has finished reading the requested DHT22 sensor, the data are available for reading through the I2C interface. In this case, Array[0] will be read as 0x01 indicating the successful completion of the last command.

### Getting the Sensor Data with an Arduino UNO

Accessing the memory locations to request and read sensor data through the I2C interface is in the usual fashion. Readers who have programmed the Arduino for I2C functions will recognize the steps and the included sketch has been commented to facilitate the program flow.

First, you need the statement,

to use the I2C library.

Next, you need the I2C address of the PIC. This is set in the PIC MPASM code by the program line:
    
    
    #define I2C_ADDRESS        0x32                       ; Slave address

That address should be right-shifted one bit to form the address that the Arduino is going to use. Those familiar with the I2C 7-bit addressing scheme will recognize this, often inconvenient, step. Right shifting 0x32 gives us 0x19 and that will be the I2C address that the Arduino uses. Of course, you can set this address in the MPASM code to whatever available I2C address that you have.

To start the ball rolling, use the statement Wire.begin(); // join bus as master - usually in the setup().

The steps to issue a command to read sensor #2, as an example, are as follows (the variable "address" has been set to 0x19):
    
    
    Wire.beginTransmission(address);
    
    Wire.write(0); // buffer index pointer
    
    Wire.write(3); // command byte (3=read DHT22 #2)
    
    
    
    delay(50);     // wait for it to be done - 50 msec to start

The delay in this last line waits for the sensor reading to complete and is probably longer than it needs to be but it is best to be conservative. You can try decreasing the delay if needed by your application.

At this point, the data from DHT sensor #2 should be in Array[6]-Array[11]. To retrieve the data, use the following:

First, read the status byte at Array[0]
    
    
    Wire.beginTransmission(address);
    
    Wire.write(0); // buffer index pointer
    
    
    
    Wire.requestFrom(address, 1);
    
    // update the status byte
    
    

Check that the status byte (now in DHT[0]) equals 0x01, indicating a successful completion of the command. Next, get the 5 bytes of DHT data (from Array[6]-Array[11]) with the following statements:
    
    
    Wire.beginTransmission(address);
    
    Wire.write(6); // buffer index pointer (point to data for DHT #2)
    
    
    
    Wire.requestFrom(address, 5);

After we put those data into a program array DHT[6]=-DHT[10], we convert the data to RH and Temperature and, finally, we check that the CRC is good:
    
    
    
    
    
    
    
    RHz2+=DHT[7];
    
    
    
    
    
    TempCz2=DHT[8]&0x7f;
    
    
    
    TempCz2+=DHT[9];
    
    
    
    
    
    
    
      TempCz2*=-1;
    
    
    
    TempFz2=TempCz2 * 9 / 5 +32;  
    
    // checksum
    
    if ((DHT[6]+DHT[7]+DHT[8]+DHT[9] & 255) != DHT[10])
    
     {
    
     Serial.print(" *** BAD CRC! ***  "); 
    
     }    
    
    else{
    
    
    
     }

The other two DHT22 sensors are read in the same manner, using the appropriate command codes.

The included Arduino example sketch simply reads all three sensors every 5 seconds and displays the data on the serial monitor.

![Screen output from the Arduino test sketch.](https://www.allaboutcircuits.com/uploads/articles/SS1.jpg)

> _Screen output from the Arduino test sketch._

### Getting Up and Running

The software necessary to use the circuits is included here and consists of: The 12F1840 MPASM source code, 12F1840 HEX code file, and Arduino test sketch. You will need to program the PIC 12F1840 chip. If you have used PIC chips before, this should not represent a difficult step. If you are unfamiliar with the PIC chips, then this may seem like a challenging task. There are, however, many inexpensive programmers available including several DIY designs that have received a good deal of support. The MPASM assembler is available for free from Microchip.

Additionally, by starting out with a smaller PIC chip, like the 12F1840, the task is less daunting than it might seem. You can assemble the included MPASM source code for programming as is, or make changes such as the I2C address. Alternatively, most programmers will allow you to use the straight HEX code file to program the chip with the source code as included.

### Closing Thoughts

This project is intended to provide a useful addition to a larger embedded controller project. Specifically, it is well suited to one where you need to monitor humidity and temperature in multiple zones. It is also intended as a starting point for utilizing the I2C bus in custom applications. While the 12F1840 is very inexpensive and appropriate for this project, expansions can be implemented using larger PIC chips that contain the required MSSP function but also contain more GPIO. It is, therefore, quite feasible to implement inexpensive I2C-based combinations of sensor interfaces and I/O expansion.
