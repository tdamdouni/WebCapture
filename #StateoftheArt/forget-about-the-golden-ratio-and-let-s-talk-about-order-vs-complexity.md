# Forget about the Golden Ratio and let's talk about Order vs Complexity

_Captured: 2017-01-25 at 13:31 from [blog.prototypr.io](https://blog.prototypr.io/forget-about-the-golden-ratio-and-lets-talk-about-order-vs-complexity-23e1edc6a96b?source=userActivityShare-c79006fee040-1485347467)_

![](https://cdn-images-1.medium.com/freeze/max/30/1*D5tZOuiOQHmsmwr46BPJRw.png?q=20)![](https://cdn-images-1.medium.com/max/800/1*D5tZOuiOQHmsmwr46BPJRw.png)

> _Aesthetic Measure, George David Birkhoff_

If you have some visual arts background, you might have seen quite a lot of buzz about the Golden Ratio. This famous mathematical relationship has been observed in Nature for a long time and some of our societies got quite thrilled about using it in their projects. As with anything else that excites people, some will use it [consistently](https://www.behance.net/gallery/12471003/Mies-van-der-Rohes-Farnsworth-House); others, only [for the hype](https://www.quora.com/Apple-company/Does-the-Apple-logo-really-adhere-to-the-golden-ratio); and others, [for having fun](https://www.facebook.com/fibonaccinobrasil/?fref=ts). And as expected, it will also cause lots of [polemics](https://www.fastcodesign.com/3044877/the-golden-ratio-designs-biggest-myth).

If you don't remember exactly what it is about, check out this amazing video before reading the rest of the article:

![](https://i.embed.ly/1/display/resize?url=https%3A%2F%2Fi.vimeocdn.com%2Fvideo%2F50741686_1280.jpg&key=4fce0568f2ce49e8b54624ef71a8a5bd&width=40)

> _Nature by Numbers -- a video that shows some of the patterns in Nature._

This is dangerously interesting and is the kind of thing that might captivate us to dive deep into math & nature. _But what if I told you that the number φ (phi) might not hold any virtue in itself and the phenomenon that really amuses our perception is just the realization of a strong underlying order in a complex system?_

### Aesthetic Measure

Some time ago, an American mathematician in his later years proposed another theory behind measuring "beauty" and wrote a book heavily backed by mathematics called Aesthetic Measure. The guy behind this fascinating book was [George Birkhoff](https://en.wikipedia.org/wiki/George_David_Birkhoff).

To warm our brains up for the mathematics to come, let's try an interactive example I built based on one of Birkhoff analysis. He compared a set of Chinese vases and started analyzing the vase attributes, such as height, maximum width, minimum width and so on. Each vase configuration would have a different "beauty score" or, as he called it, "aesthetic measure".

(First, click on the 'Result' tab and move your cursor along the x and y-axis. If you have issues running the example, try the live version [clicking here](http://tiagoferreira.me/projetos/threejs/aesthetics/vase/vase.html).)

When you're changing the vase dimensions, try to think of what makes you feel one setting nicer than the other. What relationships do you see between the different attributes -- neck, body, and base?

### Here comes the math

Birkhoff defines a typical aesthetic experience as a compound of three successive phases: (1) the act of attention, that increases proportionally to the observed object's **complexity** **(C)**; (2) the feeling of value or aesthetic **measure** **(M)**; and (3) the realization that the object is characterized by a certain harmony or **order** **(O)**. The relationship of the three phases could then be modeled by the following mathematical formula:

To decrease the amount of abstraction, we can analyze this formula by just thinking of numerical values: a given object with an _order_ of 4 and a _complexity_ of 2, will have an _aesthetic measure_ of **2** (4/2 = 2). If we invert the values for order and complexity, it gives us an aesthetic measure of **0.5**. In other words, **_the Aesthetic Measure of an object is directly proportional to its order and inversely proportional to its complexity._**

After understanding the formula, the first instinct might be to remove all the complexity, once:

![](https://cdn-images-1.medium.com/max/800/1*dfslkM3bEmwLQrYAhh38Ew.png)

> _If we have zero complexity, keeping the order constant, the aesthetic measure goes To Infinity and Beyond_

But remember that the complexity is also responsible for increasing the observer's attention. So, zero complexity would mean that the object won't drive any attention.

### Mathematical!

Before you start comparing rectangles to symphonies, Birkhoff clarifies that the comparisons can only be made between objects of the same "class", such as the vases we just saw. Even two paintings will have so many different levels of order and complexity that it would be impossible to compare both.

To return to the Golden Ratio, let's analyze another interactive example. This one is a representation of a phyllotaxis growth (the leaf arrangement on a stem). The example starts with the φ (1.618) value as default but you can change to different values. Again, what are the configurations that look pleasant to the eyes: Only the 1.618 option or any one that displays a nice and ordered setting?

(Again, click on the Result tab to see the example -- if you want the live version, click here: [Processing - Phyllotaxis](http://tiagoferreira.me/projetos/phyllotaxis/).)

The appearance of the Fibonacci-based sequences in Nature still amazes me and the number φ holds some rich properties (that unfortunately were out of the scope of this post). But after reading Birkhoff and Max Bense (see footnote), I started looking through other prisms and began to find some other equally gorgeous ratios and rules that could be applied to all sort of different aesthetic experiences (for example, have you ever seen the reasoning and math behind the A series of paper sizes? Check it out here: <http://pumas.jpl.nasa.gov/files/10_06_03_1.pdf>).

I believe the beauty behind the _sectio aurea_ does not come from the number or the ratios it allows, but in fact, from the strong order it provides in nature. And as I just mentioned, there are quite a lot of other (mathematical) ways to create order. Using math to support a project can bring a great analytical perspective and unlock a completely new set of fascinating results.
