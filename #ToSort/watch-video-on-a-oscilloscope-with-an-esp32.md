# Watch Video on a Oscilloscope with an ESP32

_Captured: 2018-04-07 at 10:00 from [hackaday.com](https://hackaday.com/2017/12/23/watch-video-on-a-oscilloscope-with-an-esp32/)_

![](https://hackadaycom.files.wordpress.com/2017/12/camera-on-osci-e1513899776500.jpg?w=800)

[bitluni] got a brand new scope, and he couldn't be happier. No, really -- check the video below; he's really happy. And to celebrate, [he turned his scope into a vector display using an ESP32](http://bitluni.net/oscilloscope-as-display/).

Using a scope in X-Y mode is nothing new, of course. The technique is used to display everything from [Lissajous patterns from an SDR](https://hackaday.com/2015/11/22/gnu-radio-drives-oscilloscope/) to [bouncing balls from an analog computer](https://hackaday.com/2017/01/28/op-amps-combine-into-virtual-ball-in-a-box/). Taken on as more of an exercise to learn how to use his new tool than a practical project, [bitluni]'s project starts by using two DACs on an ESP32 to create simple Lissajous patterns to learn about the scope's controls. Next he built some code to display 3D point clouds, but learned that the native DAC code wasn't up to the job. A little hacking improved the speed 27-fold, which was enough for great 3D images and live video from an I²S camera module. The latter was accomplished by grabbing frames from the camera and rendering them pixel by pixel, CRT style. The results are pretty clean, and there's a lot to be learned about both using scopes as X-Y displays and tweaking the ESP32 for maximum performance.

Need more background on the ESP32? Start by checking out [these ESP32 tutorials](https://hackaday.com/2017/03/01/esp32-tutorials/).
