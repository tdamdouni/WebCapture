# What Is Quality?

_Captured: 2016-03-27 at 18:39 from [medium.com](https://medium.com/@sam_hatoum/quality-is-love-a6069647175b)_

#### Quality, like love, is one of the greatest things in life, and just as ephemeral and hard to define. But just as we express our love to a person through "acts of love," we can express quality through functions we apply to our product.

![](https://cdn-images-1.medium.com/max/800/1*g0pJlGLs-wWXxqO98Jlpmw.png)

In my previous post, I spoke about [The Forgotten First Principle of Software Delivery](https://medium.com/@sam_hatoum/the-forgotten-first-principle-of-software-delivery-b1540ad6000e): **Quality**. I promised to explain more about how to measure and define Quality, but to do so, we need to also consider Value, because there is an intrinsic relationship between Quality and Value. Allow me to explain.

### Quality Is Love

#### Just like love, quality is not a thing unto itself.

When you love someone or something, you invest your time and energy to express that love. You care about their wellbeing and their growth. When applied throughout a child's life, the love manifests itself in the child being balanced and secure. For a car to be admired as a "classic" 70 years after it leaves the factory, it needs to have had love applied throughout its life, from the designer to the owner.

Quality is exactly the same. When due care and attention is applied throughout, the quality of the resulting outcomes can be both measured in tangible ways, and felt in emotional ways.

> High quality comes from due care and attention.

#### Quality Only Exists In The Presence Of Value

Quality is not a thing by itself, as in it cannot be applied to nothing. Again, just like love. At the risk of getting a little too philosophical, even if you have an enormous capacity to love, that love is not actualized until it is applied to someone or something.

#### Applying Quality To Value

Let's look at how this works in product development. Consider the following coarse-grained stages of value creation:

![](https://cdn-images-1.medium.com/max/800/1*zdvXXIr4dRNy5GT5O9DYBA.png)

> _A modified version of the Design Squiggle_

Value creation always begins as an idea that you realize through an iterative series of steps. At every single stage in this process, you are assuming that your idea and its implementation are valuable. This is **assumed value**. When a consumer receives value from your realized idea, then and only then, is your idea truly valuable. This is when _assumed value_ becomes **real value.**

### Quality Functions

The way in which _assumed value_ is transformed into _real value_ is through **quality functions**. I briefly introduced the idea of _quality functions_ in my previous post and said that "_quality functions_ are the methods and practices that are essential for the continued delivery of value." Perhaps a simpler way of thinking about them is that:

> Quality Functions are acts of love, care and attention that you apply throughout a product's life.

They are the means by which you adapt the idea and its implementation to increase quality.

#### Putting Quality Functions Into Practice

I like to use extreme examples when trying to prove a concept or theory. Consider these two extremes:

Extreme 1:

  1. **Idea  
**You get the idea when you're drunk.
  2. **Research & Refine  
**You check with your mum that the idea is good and she says, "yes dear".
  3. **Specify  
**You write the idea on the back of a napkin and spill tea on it.
  4. **Build & Test**  
You write the code to realize it without running the code at all and your test is a simple check that there were no compilation errors.
  5. **Deploy**  
You copy the code manually to the server in your closet.
  6. **Monitor**  
You ensure the server power is on as you enter and leave the house

Will the _assumed value_ be transformed into _real value_? Will the _real value_ be of high quality? Extremely unlikely!

Extreme 2:

  1. **Idea**  
[You have been training yourself to have better ideas](https://blog.bufferapp.com/how-to-produce-more-great-ideas-according-to-science) regarding a specific problem you want to solve. You go over it in your head and try to prove yourself wrong to make sure the idea makes sense. You trash the first set of ideas and think of a few more until you have an idea you're happy with. You socialize the idea with people outside of your circles to see if they think it's valuable and you rinse and repeat this process.
  2. **Research & Refine**  
You iterate on this process a few times. You apply [design thinking](http://dschool.stanford.edu/use-our-methods/) and modify the idea based on the feedback you get. You [research the market and the opportunity](http://xolv.io/product-market-fit-consulting/?utm_source=medium&utm_medium=sh-blog&utm_campaign=quality-articles) and figure out how you will reach customers. You go back and modify the idea according to your findings. You iterate on this and go back to step 1 a few times until you finally have empirical proof that shows your idea is in demand and ready to be realized.
  3. **Specify**  
You use a combination of UX wireframes and [BDD style stories](http://dannorth.net/whats-in-a-story/) to define the idea with the team that is going to build and test it. You sit with the team and work with them throughout the development stage. You change the original idea some more based on the feedback from the team.
  4. **Build & Test  
**The team writes clean code that respects the [separation of concerns principle](http://aspiringcraftsman.com/2008/01/03/art-of-separation-of-concerns/), amongst other engineering best practices. They practice [pair](http://www.extremeprogramming.org/rules/pair.html) & [mob programming](http://mobprogramming.org/) and embrace a testing culture. They use an [automated testing approach](https://github.com/xolvio/automated-testing-best-practices/) and are dedicated to creating tight feedback loops that allows them to iterate quickly.
  5. **Deploy**  
The team creates automated deployment to clustered cloud servers that autoscale on-demand, and you ensure you can trust the deployment through smoke tests. You use services like [LaunchDarkly](https://medium.com/u/b6a5df04b7aa) to diligently roll out your features. If any of the deployments fail, the code or the automation is changed until the deployment is successful and the smoke tests pass.
  6. **Monitor**  
You regularly monitor the health of the app and receive automated notifications. You also monitor the usability metrics, customer feedback and web/app usage metrics. When you see the usage dropping you go back to step 1 and repeat the entire process to ensure your customers are receiving value.

Will the _assumed value_ be transformed into _real value_? Will the _real value_ be of high quality?

I know which extreme I would put my money on!

When the end result is of high quality, it is because _quality functions_ were applied throughout every single stage of delivery. The _quality functions_ are the mechanism that transforms the **assumed value **into** real value.** This implies that:

> Value cannot exist without quality

And I mentioned above, quality cannot exist by itself, so the inverse is also true:

> Quality cannot exist without value

In other words, Quality and Value have a Yin-Yang relationship.

### Q()

Now as a programmer by trade, I like to think of _quality functions_ as I see them in code, which looks like this:
    
    
    **Q() {  
    ** researchAndRefine()  
     specify()   
     buildAndTest()  
     deploy()  
     monitor()  
    **}**

The above simply says that **Q()** is all of the _quality functions_ that you apply in your delivery process.

And since _quality functions_ are what transforms _assumed value_ into _real value_, we can pass the _assumed value_ into the _quality functions_:
    
    
    **V**_r_** = Q(V**_a_**)**

In other words, _real value is _the product of all the _quality functions _applied to_ assumed value._

### Quality Belongs Everywhere, And To Everyone

#### When you look at quality like this, doesn't it seem completely absurd that in most companies, the "job" of quality is given to one person or department, right at the end of a process?

Have a look at Parasoft's research where they asked 780 IT professionals to answer a series of questions about their team's development process. When they asked the different teams "who owns quality?", these were the results:

![](https://cdn-images-1.medium.com/max/800/1*t05wgCtIk4qnjloBSH5cDg.png)

> _[source](https://alm.parasoft.com/nonfunctional-requirements-report)_

You can clearly see that the responsibility of quality falls on the testing team in all of the development methodologies, and the testing team typically operates at the tail end of the process. The truth is, most of the opportunities to influence the quality of the real value have already passed by then.

There are hundreds, even thousands of _quality functions_ that you can be applied to the product development process. Every single person that touches the _assumed value_ is responsible for applying _quality functions_ to it.

**This is why, quality needs to be a holistic concern across the whole lifecycle**, and this is why I think we need a whole new category of product that unites _quality functions_ to really make a dent in the software quality problem.

#### Join our mission

I promise you, we're working on this problem. It has been haunting me my entire career and it's time to do something about it.

If this theme and my comments resonate with you, please let me know by clicking that heart icon and recommending the article to expand the reach of this message.

And if, like me, you feel passionately about the need for prioritizing quality in software development, please connect with me by following me [here on Medium](https://medium.com/@sam_hatoum/), and [here on Twitter](https://twitter.com/sam_hatoum) and at the [Xolv.io site and blog](http://xolv.io/blog/?utm_source=medium&utm_medium=sh-blog&utm_campaign=quality-articles) where I will update you on our progress. You can [contact me here](http://xolv.io/contact-us/?utm_source=medium&utm_medium=sh-blog&utm_campaign=quality-articles).

You can also help me by telling me your story, your opinions, or any other resources you think are pertinent to this cause. How does your team transform _assumed value_ into _real value_? What _quality functions _do you apply?

I cherish any and all feedback, and I look forward to teaming up with you.

Sam.
