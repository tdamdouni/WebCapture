# Will trigonometry help an Arduino measure water depth?

_Captured: 2018-01-08 at 17:17 from [publiclab.org](https://publiclab.org/notes/show/15445)_

![](https://publiclab.org/system/images/photos/000/023/055/large/springhouse_20171213-2111.JPG)

A prototype of the [tilting-arm water level measurer](https://publiclab.org/notes/cfastie/12-09-2017/will-an-arduino-measure-water-depth?) was able to measure the height of objects in my office with an error of several millimeters. That system depended on a brute force calibration which involved relating the raw output of an accelerometer to a range of measurements (e.g., heights of the end of the tilting arm above the floor). A more elegant approach is to use trigonometry to derive a dimension of a triangle from the angle measured by the accelerometer. This approach is much easier to transfer to a new location like the spring house where I want to measure water depth.

![MMA8451_20171229-2325.JPG](https://publiclab.org/system/images/photos/000/023/059/medium/MMA8451_20171229-2325.JPG)

_Figure 1. The updated prototype. An [Arduino Nano (right) on a logging shield](https://publiclab.org/tag/nano-data-logger) reads data from an MMA8451 3-axis accelerometer (center). A green LED (above the MMA8451) blinks when the Nano is reading tilt data. Every five seconds the Nano takes the average of 50 readings from the accelerometer and computes the distance of the tilting arm's end above the floor. The result is displayed in real time on the LCD (left)._

An advantage of the earlier method is that it did not require knowing the tilt angle of the arm--the raw accelerometer output was regressed directly against height. Trigonometry requires an angle, so the accelerometer output had to be converted to an angle. The raw accelerometer output is related to angle, but it is a non-linear relationship.

![nonLinearAcceler.PNG](https://publiclab.org/system/images/photos/000/023/056/large/nonLinearAcceler.PNG)

> _Figure 2. For some reason, the tilt data produced by an accelerometer have a nonlinear relationship to tilt angle. Probably for the same reason, the relationship is trigonometric. Source_

It's not too hard to learn that the curve in Figure 2 is a sine wave. To convert accelerometer output (12 bit) to an angle the formula is:
    
    
    angle = arcsine(output/4096)  (note: this is somewhat simplified)  
    

.

![ArcsinFunc.PNG](https://publiclab.org/system/images/photos/000/023/057/large/ArcsinFunc.PNG)

_Figure 3. To confirm that the arcsine function was working, I measured the angle of the tilting arm (using trigonometry) when its end was resting at different heights above the ground. Then I applied the arcsine function to the accelerometer readings for each of those tilt angles. There is good agreement between the two curves when the right correction factor (+12) is used._

So now I can convert accelerometer output to tilt angle, and more importantly, so can the Arduino. When the Arduino knows the angle, it can use trigonometry to find dimensions of right triangles. Every different tilt angle creates a new triangle in which the arm is the hypotenuse and the other two sides are vertical or horizontal. The length of the hypotenuse (arm) is known, as is the height of the arm's pivot point. So the Arduino can compute the length of each triangle's adjacent side and derive the height of the arm's end above the floor (Figure 4).

![MMAtrig.jpg](https://publiclab.org/system/images/photos/000/023/058/medium/MMAtrig.jpg)

_Figure 4. The Arduino can derive the height of the arm above the floor because it is told two of the other three dimensions and given a good hint about the angle. It computes the angle and then the adjacent side and then the height._

The MMA8451 accelerometer I used is a 3-axis accelerometer and these calculations were done using only the Y-axis output. All three axes can be used to get a more robust estimate of tilt angle, but the math is messier. I could not parse the method in [this document from the manufacturer](https://www.nxp.com/docs/en/application-note/AN3461.pdf) (e.g., equation 55), but I could grasp the [simplified version in this post](http://www.hobbytronics.co.uk/accelerometer-info). I implemented the simplified version and it worked well for part of the range of tilt angles but not for the rest. I gave up and went back to using only the Y-axis data which seems to yield sufficiently accurate and precise results for the entire range of angles I need (25° to 85°).

The two minute video below shows the device in action computing the height above the floor and displaying the measurement in real time.

The data logging shield is not needed in this implementation, and the cost of the required components (Nano, MMA8451, and LCD) is about $8.00 on eBay. The low cost makes this an excellent candidate for a STEM project or if you wanted a really inconvenient ruler.

### People who did this (0)

None yet. [Be the first to post one!](https://publiclab.org/post?tags=replication:15445,arduino,nano-data-logger,accelerometer,mma8451)

**This is marked this as an activity for others to try.**   
[Try it now](https://publiclab.org/post?tags=activity:15445,arduino,nano-data-logger,accelerometer,mma8451) [Click here](javascript:void\(\)) to add some more details.
