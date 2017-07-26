# Usability Test on Product Hunt for iPhone

_Captured: 2015-11-27 at 11:36 from [medium.com](https://medium.com/@ericjlee/usability-test-on-product-hunt-for-iphone-ba208a440175#.l6qvtbgxt)_

![](https://cdn-images-1.medium.com/freeze/max/30/1*e_iWCkcEe7pNx41Rk13GGw.jpeg?q=20)![](https://cdn-images-1.medium.com/max/1200/1*e_iWCkcEe7pNx41Rk13GGw.jpeg)

#### Redesigning the product discovery experience

Couple months ago, [Ryan Hoover](https://medium.com/u/c2146664c8e4) published [(Still) Building in Public](https://medium.com/@rrhoover/still-building-in-public-942db2218508). The article showcases active attempts by Product Hunt ("PH") to bring together a community in its growth process, making users feel more inclusive and a part of the product. I decided I wanted to contribute to PH's 'building in public' efforts as it expands to a wider range of users and products.

PH is a great product that I use every day to discover new, interesting products in the tech space. Its [website](http://producthunt.com), with the [new update](https://medium.com/@rrhoover/say-hi-to-product-hunt-2-0-3e79e427be32), provides a smooth product discovery experience. However, quick usability tests reveal that its [iPhone app](https://itunes.apple.com/us/app/product-hunt-best-new-products/id904658671) has several pain points that hinder users from fully enjoying PH.

#### Objective

Identify and address pain points to improve the product discovery experience on iPhone app.

#### Design Process

#### User

Prior to conducting usability tests, I developed a provisional persona based on my assumptions to better understand the target users of PH's iPhone app. This process helped me get into the mindset of the users, thinking in terms of their context, needs, and goals.

#### Test Parameters

  * **What**: Product Hunt iOS mobile app (specifically, iPhone 6)

#### Usability Test Scenarios

  * **Search**: Imagine you enjoy using Instagram daily and have tried other photo apps. You now want to find new photo filter apps. Can you show me how you would do that?
  * **Collection**: Imagine you found 5 photo apps you want to try on PH. You want to keep track of them to try later after work. Can you show me how you would do that?
  * **Follow**: Imagine a tech guru you admire is active on PH and posts products or comments 3-4 times a week. You want to keep track of his or her activities. Can you show me how you would do that?
  * **Share**: Imagine you discovered an awesome game app on PH and you want to have your best friend try it. Can you show me how you would do that?

#### Pain Points

After conducting usability tests, I analyzed and synthesized the test results.

First, I listed all the pain points of each user.

Second, I grouped the pain points by their similarity, akin to affinity mapping. Four buckets of pain points emerged. Then, I sorted them in the order of highest frequency. The tasks associated with _Collections_ gave users the most trouble, followed by _Follow/Activity_, _Details_, and _Search_.

Lastly, keeping in mind the needs and goals of the persona, Jack, as well as PH's company mission for a better product discovery experience, I mapped the four pain point buckets by their importance to users and the company. The mapping revealed that _Details_ plays the most pivotal role in shaping users' product discovery experience. Thus, I decided to tackle _Details_ for this case study.

#### Key Insights on _Details_

All users had trouble locating enough _details_ about a product of their choice during usability testing.

> "Because I understand the upvoting process of PH, I'd go with the most upvoted product. But, once I get into the product, **what I'm missing here is the robust description of what it exactly does**. I think this (media) is getting close like the screenshots of what you eventually will get, but I just don't think I'm getting the whole picture yet. **I'm not ready to 'get it'**. I'm not ready to make a commitment." -- User 4

**There are two major problems that prevent users from learning about a product.**

First, users are not successfully getting in-depth product information due to incoherent interface flow and unclear wording.

  * Users are directed to _comments_ section first when they are trying to learn more about a product.
  * Users are confused by and afraid of the green _Get It_ button, unsure of what to expect when they tap the button.

Second, a [zero data or empty state](http://blog.invisionapp.com/why-empty-states-deserve-more-design-time/) leaves users clueless about what a product is about, making them not want to get the product. _(Figure 1)_

  * Unlike the empty state for _comments_, the empty state for _media_ does not provide appropriate feedback to users.

#### Redesign Process

The next step in my design process was ideating and visualizing possible solutions for the pain points.

**Design Stories**

The purpose of design stories is to imagine what users can do with the redesigned app and then break it down into digestible tasks to be done.

**Task Flow**

The proposed flow places the _media_ (description) section as the main content on a product description screen while making the _comments_ section a related action.

> __I put 'Get It' as the end point for the task flow because getting the product indicates that users are truly discovering the product by using it, resulting in more informed opinions, comments, upvotes, shares, and so on.__

**UI Sketches**

I started wireframing by rearranging the current screen elements and then attempted to be more creative with how the content would be presented.

As a next step, high-fidelity screens were produced. Below is a comparison of current app screens against redesigned app screens regarding the product discovery experience.

**Initial Redesign Decisions**

1\. Prominent photo previews instead of maker profiles on the product list _(Figure 2)_

  * Builds upon most users' existing mental model of using App Store.
  * Helps users pick a product through [progressive disclosure](http://www.nngroup.com/articles/progressive-disclosure/). The photos help users get a bit more sense of what each product is about.

2\. Product description screen bypassing the _comments_ section of the current app flow _(Figure 3)_

  * Quick scroll reveals video, text, and photo information on the product, thus reducing current friction to users' product discovery experience.
  * Users can write comments while viewing the product information. This reduces their current cognitive load of having to retain the new product information while writing comments on a separate screen.

3\. Changes in wording and arrangement of actionable elements _(Figure 3)_

  * 'Get It' button is clarified into 'Website' and 'App Store' buttons, which [stay visible at all times](http://www.lukew.com/ff/entry.asp?1945)
  * All the icons have been replaced with text buttons so that users have clear expectations on where each button would lead them to.
  * The menu button has been created on top right corner to reduce visual clutter of icons and options.

**Interactive Prototype**

> _This is the demo of the initial redesign. I used this initial prototype to conduct further user testing and iterate based on the feedback. (Tool: Pixate)_

**Test & Iterate!**

One of the most important aspects of design is getting feedback. Testing the initial prototype with more users helped me refine the design.

#### Key Learnings

The following feedback guided my iteration process:

  1. Users want to see product information right away.
  2. Users still find product descriptions and actionable buttons dense and visually overwhelming.
  3. Users are not sure which interaction to expect -- scroll or swipe or something else?

Thus, the iteration process began. I initially continued iterating at a high-fidelity level on Sketch App.

> _Second Iterations focused on various interaction elements such as scroll and swipe in different sections._

When I iterated at the high-fidelity level, I kept running into designer's block.

> A breakthrough emerged when I decided to zoom out from the current iterations and go back to low-fidelity wireframe sketches.

[IDEO](https://www.ideo.com)'s design thinking course had taught me to be fluid with divergent and convergent ideation and to be divergent longer, considering all the relevant elements, before rushing to converging into a single solution. I realized I was making exactly that mistake.

I returned to sketching low-fidelity wireframes.

I realized I had neglected to hyper-prioritize the elements that should be shown on the product information screen and that doing so would solve the visual clutter problem and immerse users in the product information contents.

To prioritize the features, I conducted a quick card sorting exercise with 6 people to learn about what features are important to users when they try to learn about a product and potentially get it. I provided 8 post-it notes with a feature written on each and asked each participant to arrange them in the order of importance.

  * 4 users were focused on social proof, prioritizing the _number of upvotes_, _comments by others_, and _maker's profile_.
  * 2 users disregarded social proof. They were ready to get the product after browsing the product information and deciding for themselves that they want to try it.

The card sorting results helped me sort features into primary actions to be shown on the main screen and secondary actions to be hidden.

With the card sorting results in mind, I proceeded to high fidelity iterations as shown below.

**Screen Flow of the Prototype**

With the new design, both novice and expert users can immediately learn what a product is about, visually and textually, in an immersive manner. They can also easily access important actionable elements, thus fulfilling the tasks laid out in the aforementioned design stories.

Regarding empty states, one way to improve might be having a specific format for product information. When product hunters or makers submit a product, they must upload at least one photo and few sentences that aid people's understanding of the product. This is to prevent an empty state and make sure everyone can fully enjoy the product discovery experience on PH. An illustration is shown below. _(Figure 4)_

**Interactive Prototype**

#### Next Steps

I'd love to test the redesign with more users and reiterate. There are few things I'd like to explore further.

  1. Collapsing the header when users scroll up but expands back when they scroll down. When collapsed, the header will only display the product name. The purpose is to increase screen real estate for the product information contents.
  2. Clarifying having both the name and profile pic of the maker or hunter in the header. This confuses many novice users.
  3. Exploring users' mental models and reactions on the 'Try It' button as well as the degree of importance they assign on going to a website vs. app store of a product.
