# A 4-bit Calculator made in cardboard and marble

_Captured: 2017-11-15 at 13:35 from [lapinozz.github.io](http://lapinozz.github.io/learning/2016/11/19/calculator-with-caordboard-and-marbles.html)_

## LOGIC

![image](http://lapinozz.github.io/assets/image/LOGIC/logic_name_full.png)

# What is it?

LOGIC is a fully functional 4-bit calculator made entirely out of cardboard, hot glue and marbles. I built it with my little sisters for a science activity, it can add numbers from 0 to 15 for a maximum computable number of 30. We made it from scratch and at the time I didn't see any of the various kind of calculator that have been made using Lego, wood and other, so it's a completely new model!

# Why?

Mostly for fun! For some time now I wanted to build an adder but I wasn't sure how I wanted to do it yet. I was thinking of maybe make it using a water system or with only cardboard. Then my sisters had a science activity where they had to present a science project and I was helping them to choose a subject. I randomly found a video about [a calculator made with dominoes](https://www.youtube.com/watch?v=OpLU__bhu2w) and I thought, why not make one with marbles?

# What was learned?

My little sisters already knew how to count in binary, through the project they also learned about, binary addition, binary/decimal conversion, logic gates, basic logic circuits, and more.

I also learned how simple it can be to build logic circuits using simple material lying around. As in all my projects, I always try do with what I already have.

# What does it look like?

![image](http://lapinozz.github.io/assets/image/LOGIC/LOGIC-low.jpg)

> _Woah, How do you use it?_

You place your input numbers as binary in the inputs, a marble is a one, no marble is a zero. The bit on the right is the least significant bit. You have to reset some part of the calculator before each calculation too. Then you remove the little bit of cardboard that kept the marbles from running down and they will slide along the paths, moving and changing the paths as they go, to finally arrive at the outputs at the bottom, giving you the result, as binary again.

![image](http://lapinozz.github.io/assets/image/LOGIC/LOGIC-IO-low.jpg)

> _Here's an example of input if you wanted to add 7 plus 5._

![image](http://lapinozz.github.io/assets/image/LOGIC/LOGIC-7-plus-5-low.jpg)

## How does it work?

When we were reflecting on how to make the logic gates we needed, we always started by stating what the gate is doing in common term. The first gate we did was the AND gate.

# AND gate

So what do a AND gate does? Basically:

If there is no marble in: no marble out  
If there is one marble in: no marble out  
If there is two marble in: one marble out

So we needed a system that let one marble pass if there is two else it there is none out.  
Here's what we came up with.

One marble: no output

![image](http://lapinozz.github.io/assets/image/LOGIC/AND-1.gif)

> _Two marbles: one output_

![image](http://lapinozz.github.io/assets/image/LOGIC/AND-2.gif)

The XOR was a bit more complicated because the inputs had to be at the exact same time.

So how do we model an XOR? Simple!

If you have one marble than it pass  
If you have two marbles then they should cancel out

We imagined that it would be quite simple to have them cancel out. Put a path only large enough for one marble and when they arrive they collide and keep each other falling in the path. The problem is that they have to be in perfect synchronization and even when it's the case they bounce and usually they get out anyways.

We still managed to make one but it was so unreliable that we decided to move on and to just let it be as a prototype as we might not need it at the end.

![image](http://lapinozz.github.io/assets/image/LOGIC/XOR.gif)

AND and XOR gates we would have needed 16 AND gates, 16 XOR gates and 4 OR gates which would have made it just way too big and we didn't have to make all those.

![half adder circuit](http://lapinozz.github.io/assets/image/LOGIC/Half-Adder-Circuit.gif)

> _That's where thinking the gates in common terms comes handy, for a Half-Adder it would be:_

If there is one marble: make it fall in the first output  
If there is two marbles: make one of them fall in the second output

It actually wasn't too hard to make one. The first marble flip a little piece of cardboard, so if there is a second marble it fills fall in a hole. That second marble lands on another flip which block the first one.

For one marble you can see it fall in the 1 path

![image](http://lapinozz.github.io/assets/image/LOGIC/Half-Adder-1-cropped.gif)

> _For two marble you can see it fall in the 2 path_

![image](http://lapinozz.github.io/assets/image/LOGIC/Half-Adder-2-cropped.gif)

> _The one begin the sum and the two begin the carry._

# Full Adder

A Full-Adder is normally made of two Half-Adder and one OR gate. We were really surprised to see that we could make one by modifying only slightly our Half-Adder. In common term the Full-Adder is the same as a Half-Adder apart that if there is a third marble, then it should fall in the 1 path.

![image](http://lapinozz.github.io/assets/image/LOGIC/two-half-adder.png)

If there is one marble: make it fall in the first output  
If there is two marbles: make one of them fall in the second output  
If there is three marbles: make one the fall in the first output and another in the second

It was really easy to add the third case to our Half-Adder model, literally only one little piece of cardboard needed to be added. The reason our Full-Adder looks so different is because we edited it to allow for more time between the first and second marble thus lowering the synchronicity requirement.

![image](http://lapinozz.github.io/assets/image/LOGIC/Full-Adder-IO-low.jpg)

> _So for one marble it falls in path 1_

![image](http://lapinozz.github.io/assets/image/LOGIC/Full-Adder-1-cropped.gif)

> _For two marble one of them fall in path 2_

![image](http://lapinozz.github.io/assets/image/LOGIC/Full-Adder-2-cropped.gif)

> _And finally for three marble one of them fall in path 1 and another in path 2_

![image](http://lapinozz.github.io/assets/image/LOGIC/Full-Adder-3-cropped.gif)

> _Putting it all together_

Now that we can make Full-Adder we can finish our calculator. We just had to connect them so that the carry out go to the carry in of the next.

![image](http://lapinozz.github.io/assets/image/LOGIC/Full-Adder-circuit.jpg)

Even if each Half-Adder and Full-Adder we made were working properly, once all glued together the calculator had problem working. Marbles would go too fast or too slow, they would bounce off and that sorts of things. This is not to say that it can't work, the calculator work but you have to try multiple time before everything go the way it supposed to be. The logic itself is flawless, it's just that cardboard turn out to not always be the most practical and require a lot of adjustment, we just couldn't finish all the adjustment on time.

# Done!

We built two more Full-Adder and the rest are just path so that the marbles go to the correct inputs and outputs!

![image](http://lapinozz.github.io/assets/image/LOGIC/LOGIC-gates-low.jpg)

After finishing this project I searched if others had made similar constructions and was amazed by the diversity and the creativity. One thing I noticed was that in most mechanism using balls, you entered the number by setting the flips and you had to have a lot of ball running down, in our model you set the input numbers using directly the marbles position and count. This is closer to how it works in computer and it seems to me that it would be easier to incorporate in bigger project. I'm already thinking of how I could make a minimalist marble computer or a Turing machine.

Thank you for reading I hope you did enjoy.  
As always comments are welcome and appreciated!
