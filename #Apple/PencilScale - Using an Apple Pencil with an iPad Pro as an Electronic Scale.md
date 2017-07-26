# PencilScale - Using an Apple Pencil with an iPad Pro as an Electronic Scale

_Captured: 2015-11-25 at 12:42 from [flexmonkey.blogspot.de](http://flexmonkey.blogspot.de/2015/11/pencilscale-using-apple-pencil-with.html?m=1)_

Following all the interest created by my [Plum-O-Meter](http://flexmonkey.blogspot.co.uk/2015/10/the-plum-o-meter-weighing-plums-using.html), I couldn't resist trying a similar experiment with my newly arrived Apple Pencil, so here's [PencilScale](https://github.com/FlexMonkey/PencilScale), an iPad Pro application that uses the Pencil as an electronic scale.  
PencilScale requires some additional special hardware that I've had to create myself using the advanced manufacturing facilities in my kitchen. The custom harness is in two parts: a base unit and a platform that sits on top of the Pencil. Luckily, Apple actually supplied the necessary raw materials in their packaging:

![](http://1.bp.blogspot.com/-cHD8NAGe7LE/Vk82a2DxUyI/AAAAAAAAGSY/eP7vCnwR_W0/s320/unnamed.jpg)

Both parts consist of seven segments, after folding, the vertical segments are 3cm high and the horizontal segments are 5cm square (amazingly, one the Pencil packaging sides is exactly 27cm by 10cm as if Apple had this in mind!).  
After some highly technical fabrication, my harness pieces look like a work of art:

![](http://3.bp.blogspot.com/-6Cc38jUV2YA/Vk83I2UbM4I/AAAAAAAAGSg/jhXONpIvZkQ/s320/unnamed-2.jpg)

Once the hardware was complete, I moved onto the software. To jazz up the user interface, I used my old [Nixie Tube](http://flexmonkey.blogspot.co.uk/2015/08/a-swift-nixie-tube-display-component.html) project and the rest of the app is pretty simple stuff. When the touch begins, I make sure it originates from the Pencil by looking at the touch's _type_ property...

override func touchesBegan(touches: Set<UITouch>, withEvent event: UIEvent?)

guard let touch = touches.first where touch.type == UITouchType.Stylus else

zeroButton.enabled = true

update(weight: touch.force, touchLocation: touch.locationInView(view))

The _update()_ method simply subtract's the touch's force from a base weight (which is set as the current touch force when the 'zero' button is pressed) and multiplies it by 140 which gives the weight in grams (very roughly):

func update(weight weight: CGFloat, touchLocation: CGPoint?)

var weight: CGFloat = 0

nixieDigitDisplay.setValue(string: "\--------")

nixieDigitDisplay.setValue(string: String(format: "%.1f", max(0, (weight - baseWeight) * 140)))

...and amazingly, that is pretty much all there is to it!  
Interestingly, the maximum possible force of the Pencil with the iPad Pro is 4.16666 which indicates to me that its precision is much higher than 3D Touch on the iPhone 6s, however as you can see from the video, the accuracy seems a little hit and miss, maybe with more experimentation I can get better results.  
The source code, as always, is available at [my GitHub repository here](https://github.com/FlexMonkey/PencilScale). Enjoy!
