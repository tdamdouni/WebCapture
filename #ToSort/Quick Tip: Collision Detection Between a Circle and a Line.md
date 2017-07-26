# Quick Tip: Collision Detection Between a Circle and a Line

_Captured: 2016-08-09 at 22:40 from [code.tutsplus.com](http://code.tutsplus.com/tutorials/quick-tip-collision-detection-between-a-circle-and-a-line--active-10546)_

by [Kah Shiu Chong](http://tutsplus.com/authors/kah-shiu-chong)5 Jan 2012

Difficulty:BeginnerLength:QuickLanguages:English

[Games](/categories/games)[Flash](/categories/flash)

__

__

  * __
  * __
  * __
  * __

This post is part of a series called [Collision Detection and Reaction](http://code.tutsplus.com/series/collision-detection-and-reaction--active-10878).

[Quick Tip: Collision Detection Between Circles](/tutorials/quick-tip-collision-detection-between-circles--active-10523)

[Quick Tip: Collision Detection Between a Circle and a Line Segment](/tutorials/quick-tip-collision-detection-between-a-circle-and-a-line-segment--active-10632)

In [my previous Quick Tip](http://active.tutsplus.com/tutorials/games/quick-tip-collision-detection-between-circles/), we looked at the idea of collision detection in general, and specifically at detecting collisions between a pair of circles. In this Quick Tip, we'll look at detecting a collision between a circle and a line.

* * *

This is the result that we will work on. Click the Restart button to reposition all circles at the top of the stage and watch them fall down.

Note that the circles collide with the line even outside of the segment that is drawn. My next Quick Tip will show how to fix this.

* * *

##  Step 1: The General Idea

To check whether any circle has collided with a line, we have to check the _perpendicular length_ from the line to circle. Observe the diagram below.

![Perpendicular distance to circle](https://cdn.tutsplus.com/active/uploads/legacy/tuts/393_qtCollisionDetection123/assets/perp_length.png)

It is clear from the diagram above that cases 3 and 4 should detect a collision between the circle and the line. So we conclude that if the perpendicular length (marked in red) is equal or less than circle's radius, a collision happened due to the circle touching or overlapping the line. Question is, how do we calculate this perpendicular length? Well, Vectors can help to simplify our problem.

* * *

##  Step 2: Line Normal

In order to draw a line on stage, we need two coordinates (c1 and c2). The line drawn from c1 to c2 will form a vector pointing to c2 (Note the direction of the arrow).

Next, we need to find the line's _normal_. The line's normal is another line that makes 90° with the original line, and intersects with it at a point. Despite the line's normal being yet another line, the normal's vector form can be further identified as the _left_ or _right_ normal relative to the line's vector. The left normal is the line vector itself, rotated -90°. The right normal is the same but rotated 90°. Remember, the y-axis in Flash's coordinate space is inverted compared to the y-axis on a typical graph - so positive rotation is clockwise and negative rotation is counter-clockwise.

![Normals of a line.](https://cdn.tutsplus.com/active/uploads/legacy/tuts/393_qtCollisionDetection123/assets/normals.png)

* * *

##  Step 3: Projection on Left Normal

The left normal is used in our attempt to calculate the perpendicular length between the circle and the line. Details can be found in the diagram below. _A_ refers to a vector pointing from _c1_ to the circle. The perpendicular length actually refers to vector A's _projection_ on the left normal. We derive this projection by using trigonometry: it is `|A| Cosine (theta)`, where `|A|` refers to the magnitude of the vector _A_.

![Projection on normal.](https://cdn.tutsplus.com/active/uploads/legacy/tuts/393_qtCollisionDetection123/assets/projection.png)

The simplest approach is to make use of [vector operations](http://active.tutsplus.com/tutorials/actionscript/euclidean-vectors-in-flash/), specifically the dot product. Starting from [the equation of the dot product](http://en.wikipedia.org/wiki/Dot_product), we rearrange the terms so that we arrive at the second expression shown below. Note that the right side of the second equation is the projection that we wanted to calculate!

![Alternative to term.](https://cdn.tutsplus.com/active/uploads/legacy/tuts/393_qtCollisionDetection123/assets/dotProduct.png)

Also note the left and right side of the equation will ultimately produce the same result, although different in their approaches. So instead of using the right side of the equation, we can opt for the left side of equation. To easily arrive at the end result, it is favourable to use the left because variables can be easily resolved. If we insist on using the right of equation, we'd have to push ActionScript through rigourous Mathematical work in calculating the angle theta. We conclude with the diagram below.

![Projection on normal using vector.](https://cdn.tutsplus.com/active/uploads/legacy/tuts/393_qtCollisionDetection123/assets/projection2.png)

_(*Additional note: If the circle falls below line vector, the perpendicular length calculated from the formula in above diagram will produce a negative value.)_

* * *

##  Step 4: Implementing Circle-Line Collision Detection

Now that we have understood the approach mathematically, let's proceed to implement it in ActionScript. In this first section, note the line's vector is being rotated -90° to form the left normal.

    
    
    
    //declaring coordinates
    x1 = 50; y1 = 100; 
    x2 = 250; y2 = 150;
    
    //drawing line
    graphics.lineStyle(3); 
    graphics.moveTo(x1, y1); graphics.lineTo(x2, y2)
    
    //forming line vectors
    line = new Vector2D(x2 - x1, y2 - y1);
    leftNormal = line.rotate(Math.PI * -0.5);

In this second section, I have highlighted the calculations mentioned and the condition to check for collision between circle and line.

    
    
    
    private function refresh(e:Event):void {
    	for (var i:int = 0; i < circles.length; i++) {
    	
    		//calculating line's perpendicular distance to ball
    		var c1_circle:Vector2D = new Vector2D(circles[i].x - x1, circles[i].y - y1);
    		var c1_circle_onNormal:Number = c1_circle.projectionOn(leftNormal);
    		
    		circles[i].y += 2;
    		
    		//if collision happened, undo movement
    		if (Math.abs(c1_circle_onNormal) <= circles[i].radius){
    			circles[i].y -= 2;
    		}
    	}
    }

For those who'd like to investigate further, the following are excerpts of methods used in `Vector.as`

    
    
    
    /**
    * Method to obtain the projection of current vector on a given axis
    * @param axis An axis where vector is projected on
    * @return The projection length of current vector on given axis
    */
    public function projectionOn(axis:Vector2D):Number
    {
    	return this.dotProduct(axis.normalise())
    }
    
    
    
    /**
    * Method to perform dot product with another vector
    * @param vector2 A vector to perform dot product with current vector
    * @return A scalar number of dot product
    */
    public function dotProduct(vector2:Vector2D):Number
    {
    	var componentX:Number = this._vecX * vector2.x;
    	var componentY:Number = this._vecY * vector2.y;
    	return componentX+componentY;
    }
    
    
    
    /**
    * Method to obtain vector unit of current vector
    * @return A copy of normalised vector
    */
    public function normalise():Vector2D
    {
    	return new Vector2D(this._vecX/this.getMagnitude(), this._vecY/this.getMagnitude())
    }
    
    
    
    /**
    * Method to obtain current magnitude of vector
    * @return Magnitude of type Number
    */
    public function getMagnitude():Number
    {
    	return Math.sqrt(_vecX * _vecX + _vecY * _vecY);
    }

* * *

##  Step 5: The Result

Press the Restart button to reposition all circles at the top of stage. Note that the collision is between the _whole_ line (including the section not drawn) and the circles. In order to limit collision to line segment only, stay tuned for the next Quick Tip.

