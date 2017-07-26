# Meet the future of design. Hint: it’s on your phone.

_Captured: 2015-10-10 at 10:20 from [medium.com](https://medium.com/@pixiteapps/meet-the-future-of-design-hint-it-s-on-your-phone-55e1ba30e04e)_

#### The story of Pixite's vector design app called Assembly

![](https://d262ilb51hltx0.cloudfront.net/freeze/max/30/1*jJJb7hBC522s-MSUe-XdIw.jpeg?q=20)![](https://d262ilb51hltx0.cloudfront.net/max/2000/1*jJJb7hBC522s-MSUe-XdIw.jpeg)

> _Design overlaid on photo. Made with Assembly and Pixite Source._

Project brief title: "High End Overlay App"  
Goal: Create an app that allows users to make art while supporting and promoting graphic artists while having widespread appeal to both the mobile editing community and the general public.

Starting development on the High End Overlay App would eventually lead us to publish [Assembly](https://itunes.apple.com/us/app/assembly-graphic-design-for/id1024210402?mt=8), our vector design app. At the time of the brief, [Over](http://madewithover.com/) and other apps were overlaying simple black and white designs on photos and doing well. So we thought, why not let our users overlay colorful, more sophisticated designs that were created by professional graphic artists? It seemed like a win-win situation -- the app would let graphic artists get their work out to iPhone users, and the app users could place nice looking graphics on their photos like stickers.

We wanted a variety of overlay styles and ended up spending a small fortune getting the first round of overlays created. We decided to take a few of the designs and get initial feedback from our most trusted mobile artists that we work with. Below is the actual set of overlays we sent out.

### Initial feedback

#### (June 15)

Getting feedback from users is always tricky. People are likely to say nice things, but usually, it's the negative comments like the ones below that are the most important.

_"I personally don't see many styles that resonate with me. Most of the images have too much of a button/badge/icon feel."_

_"I'm still happier just making stuff I know I've done all the work on."_

_"…an app for just overlays and masking is not so necessary."_

The response was more negative than what we expected. People felt the overlays were too finished and had difficulty adding them to photos. The overlays were so overpowering, they became the focus of the artwork.

We were back to square one. However, one piece of feedback got us heading in the right direction.

**_"An app that gives you the ability to make your own shapes and graphics is really what I think is missing."_**

### Breakthrough

#### (June 18)

Earlier in the April as an exercise in market research, we invited some talented graphic designers to our office to see what their workflows were in Adobe Illustrator. Many of them created basic shapes, then combined, subtracted, and manipulated the shapes to form their final designs.

As we sat in that Monday morning meeting, it dawned on us that we had the pieces to our next app right in front of us.

The overlay designs that most appealed to us and our mobile artists consisted of basic geometric shapes. Adding finished designs to photos is challenging but adding basic geometric shapes isn't. These shapes can be combined to create more elaborate designs. Given enough basic shapes and the right tools, our artists could make their own overlays, and even icons and logos if they wanted. This is how we stumbled upon the building block approach to graphic design.

### Beginning work on Assembly

#### Official start (June 23)

We realized the best way to test the new building block concept was to try it on the iPhone. We immediately started work on the new app. "Assembly" was a name we had thrown around before. With the building block theme in mind, the name was perfect.

Instead of rasterized shapes, it made sense to build Assembly using vector shapes so that the artwork would scale to any size and keep the memory footprint as small as possible. Within a week we had wireframes and a basic working prototype in Xcode.

### Exploration

#### (July 1)

The first prototype had a handful of shapes, less than ten colors, and options to turn on/off outlines and shadows. It would place different shapes on the screen and auto-generate designs.

We thought auto-generation would play a big part in the app until we realized that the designs, even with a lot of tweaking to the algorithm, weren't compelling. We also realized that what people wanted was more control over their artwork, not less. We needed to explore further.

We added a way to choose shapes and position the shapes on the artboard in the following iteration. That opened up a lot of possibilities and we started exploring the different things we can make with Assembly. We also started looking at Dribbble and other design resources to see what designers in the wild were making.

> _A few of the designs made in the prototype by the development team._

### Vision Statement and Features

#### (July 20)

Now that we understood what was possible, we needed to figure out exactly what we wanted Assembly to do. We formed a vision statement for the app that would guide us to the final product.

**_"Building blocks for playful creations. Entry level vector design app. Legos for overlays, specifically for our artist community."_**

The exploration also helped us organize and form the features and shape packs we needed for Assembly 1.0.

### Road to beta -- coding, testing, repeat

#### (August 11)

By August after multiple iterations and internal testing, we had the first beta version that we wanted to send to a small group of our best artists. Most of the main features including grid snapping, styles, undo/redo, exporting and saving were in place. At the same time, we started contracting graphic designers for the final shapes that would go into Assembly.

> _Beta 0.1 screenshots_

The feedback from the group was astounding. We could sense the excitement in each of the responses that came back.

"Can the app do this?"

"I want this feature."

"Can I get more shapes?"

Even more impressive was the work that the artists were sharing. Below are just few of the ones that people submitted the first 48-hours into beta testing.

### Onboarding

#### (August 18)

We realized early on that Assembly was going to be a powerful tool and the onboarding would be crucial.

We decided three things will help the user achieve success -- the inline help, tutorials, and overview. We tackled the tutorials first since the UI wasn't ready for the short videos that would end up in the inline help and overview. We created 15 tutorials in total that were grouped into three skill levels. Each tutorial focused on a key skill(s) but also produced artwork that the users can be proud of.

Inline help was a tricky problem. In previous apps, we popped up just-in-time help tips, but dialing in the experience so that users get the right help at the right time was difficult. We tried a new approach with Assembly by putting together a set of short videos for each section of the app. When the user opened the section for the first time, they immediately saw the videos.

After user testing, we found people just closed out the help without scrolling through the videos. So instead, we tried a bright orange banner at the top of the section. After more user testing, we saw people actively looked for help but completely missed the banner. **People are so conditioned in seeing ad banners that they immediately ignore them -- banner-blindness.**

And after more testing we finally found something that worked, which is a small help tip button with icon and text that animates into the workspace and doesn't go away until it's tapped. Most people ignored the button while in the section for the first time, but tapped on it when they got stuck.

Finally, the overview. Although they're standard in the industry, we've kept away from them because like ad banners, many people have "overview-blindness" and tend to skip them. However, our testers who have at least seen what Assembly can do were more engaged and created more interesting things.

Figuring out the onboarding process turned out to be the biggest challenge we faced in development.

### Final Polish and App Submission

#### (September 1)

By September, the app was looking pretty good. Our initial deadline for submission was September 3, just 10 weeks after kicking off the project. But we weren't 100% happy with where the app was, so we decided to delay the submission to address those issues.

One issue was the lack of multi-selection and grouping. People can move, change colors, resize, or copy just one shape but not a group of shapes. That really limited what you could make with the app. The challenge of adding multi-select and grouping was more on the UI/UX. We already had a lot of buttons on the screen so we didn't want to add another. We came up with a clever solution using hold-down-and-drag gesture (hold-down-and-tap also works).

Another issue that annoyed the development team was project files going missing when the app was uninstalled. We knew that if people were going to take Assembly seriously as a graphic design tool, we had to ensure project files were backed up automatically. So we decided to integrate iCloud syncing though we knew implementing it the right way wouldn't be easy.

These two issues and a handful of others delayed the submission two weeks until September 17, but **we were still able to develop the entire app in less than three months.**

> _All the shapes available in the app including in-app purchases._
