# The Plum-O-Meter: Weighing Plums Using 3D Touch in Swift

_Captured: 2015-10-28 at 08:42 from [flexmonkey.blogspot.co.uk](http://flexmonkey.blogspot.co.uk/2015/10/the-plum-o-meter-weighing-plums-using.html?m=1)_

Here at FlexMonkey Towers, the ever beautiful Mrs FlexMonkey and I love to spend our Sunday mornings luxuriating in bed drinking Mimosas, listening to [The Archers](http://www.bbc.co.uk/programmes/b006qpgr) omnibus and eating some lovely plums. Being a generous sort of chap, whenever I pull a pair of plums from the freshly delivered [Fortnum & Mason's](https://www.fortnumandmason.com/) hamper, I always try to ensure she has the larger of the two. However, this isn't always easy, especially after the third of fourth breakfast cocktail.  
[3D Touch](http://flexmonkey.blogspot.co.uk/2015/10/3d-touch-in-swift-retrospective.html) to the rescue! My latest app, the [Plum-O-Meter](https://github.com/FlexMonkey/Plum-O-Meter), has been specifically designed to solve this problem. Simply place two delicious plums on the iPhone's screen and the heavier of the two is highlighted in yellow so you can hand it to your beloved without fear of being thought of as a greedy-guts.

###  Lay your plums on me

_Plum-O-Meter_ is pretty simple stuff: when its view controller's touchesBegan is called, it adds a new CircleWithLabel to its view's layer for each touch. CircleWithLabel is a CAShapeLayer which draws a circle and has an additional CATextLayer. This new layer is added to a dictionary with the touch as the key. The force of the touch is used to control the new layer's radius and is displayed in the label:

var circles = [UITouch: CircleWithLabel]()

override func touchesBegan(touches: Set<UITouch>, withEvent event: UIEvent?)

for touch in touches

circle.drawAtPoint(touch.locationInView(view),

force: touch.force / touch.maximumPossibleForce)

circles[touch] = circle

view.layer.addSublayer(circle)

highlightHeaviest()

When the touches move, that dictionary is used to update the relevant CircleWithLabel for the touch and update its radius and label:

override func touchesMoved(touches: Set<UITouch>, withEvent event: UIEvent?)

for touch in touches where circles[touch] != nil

circle.drawAtPoint(touch.locationInView(view),

force: touch.force / touch.maximumPossibleForce)

highlightHeaviest()

Both of these methods call highlightHeaviest(). This method loops over every touch/layer item in the circles dictionary and sets the isMax property on each based on a version of the dictionary sorted by touch force:

func highlightHeaviest()

return circles.sort({

(a: (UITouch, CircleWithLabel), b: (UITouch, CircleWithLabel)) -> Bool in

return a.0.force > b.0.force

circles.forEach

$0.1.isMax = $0.0 == getMaxTouch()

isMax sets the layer's fill colour to yellow if true.  
When a plum is removed from the screen, its CircleWithLabel layer is removed and the relevant entry removed from the circles dictionary. Because the heaviest needs to be recqlucated, highlightHeaviest is also invoked:

override func touchesEnded(touches: Set<UITouch>, withEvent event: UIEvent?)

for touch in touches where circles[touch] != nil

circles.removeValueForKey(touch)

highlightHeaviest()

###  In Conclusion

The value displayed is actually the normalised force as a percentage. It's interesting to see that it changes depending on other forces acting upon the screen which to me indicates that the 6s isn't going to replace your high precision electronic scales. What this demo does show is that the 6s can handle multiple touch points each with a decent value for their relative forces.  
I did originally build this app for grapes, but they're too light to activate the 3D Touch.  
Of course, for such an important piece of software, I've made the [source code available at my GitHub repository here](https://github.com/FlexMonkey/Plum-O-Meter). Enjoy!
