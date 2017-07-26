# 3D Force Touch: beyond peek & pop

_Captured: 2015-10-21 at 22:44 from [medium.com](https://medium.com/produkt-blog/3d-force-touch-beyond-peek-pop-c448edc2b1f5#.6bgcy0zh9)_

A few days ago I bought an iPhone 6S. I was super impressed with its new **3D touch** and I could not wait to start experimenting.

Peek & pop is a great feature to include in an app. The downside: we don't have much control over it. We can only add a preview and a few actions -- iOS manages the rest.

Since I discovered _3D Touch_, I have been thinking about new ways of interacting with the content. Peek & pop is a great interaction; but what I really want is to create my own controls.

We need to take into account that, because _3D touch _is only available in iPhone 6S and 6S Plus, no action should be completed **just** by using this feature. The user should be able to achieve any action without using _3D touch_ (just like peek & pop does), and _3D touch _should only provide an extra level of interaction.

#### Accessing force property

https://gist.github.com/victorBaro/523f1041e80e184b328b#file-forcegesturerecognizer-swift

The new force property can be found in UITouch class. To get the user _touch_ we should override _touches_ methods (touchesBegan, touchesMoved, touchesEnded), either subclassing (e.g. UIView, UIButton; see example 1) or creating a gesture recognizer (see below; used in examples 2 and 3).

The force value goes from 0.0 to 6.667. For further details, I extremely recommend [Exploring Apple's 3D Touch post](https://medium.com/@rknla/exploring-apple-s-3d-touch-f5980ef45af5).

#### Example 1: Force Button

https://gist.github.com/victorBaro/b0600eb98ee6415d0497#file-forcebutton-swift

**Force Button** is a subclass of UIButton that modifies its shadow based on the input force (as seen in the top video).

The above function modifies the button shadow based on input force. You can find another example on how to modify the button scale while its being pressed [here](https://github.com/Produkt/3dForceTouchExamples).

This button uses _3D touch_ only for visual purposes, it does not add any extra feature. It might be nice to add an extra event (e.g. _UIControlEvents.ForceMaxInside) _to add a taget action once the user has pressed the button to its maximum force.

#### Example 2: Zooming

https://gist.github.com/victorBaro/07c28e0a5c2cb31f4caf#file-imagepressed-swift

We are all used to pinch to zoom in and out, it feels natural. However, sometimes it is tricky to use 2 fingers while holding the device with 1 hand. Google maps app tries to solve this issue by using a _doble-tap-longPress-drag_ gesture (which feels weird if you are not use to it).

Using ForceGestureRecognizer (see code above), it is really easy to zoom in and out while dragging your finger. If you have an iPhone 6S give it a go, it feels great.

To achieve this effect, I simply apply a CATransform3D scale to the imageView layer. By doing this, the image scales from its center. To move the image under my finger (zooming to an specific area) I need to update the anchorPoint based on the finger's location.

#### Example 3: Controlling animations

The last interaction I am proposing for the 3D_ touch_ is to **control an animation**. To be honest, I haven't found any interesting use for this interaction (other than being great for fine-tunning), but I would like to mention it (someone might find it useful).

Here is a quick video of an animation being controlled with _3D touch._
