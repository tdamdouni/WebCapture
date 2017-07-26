# Building Basecamp 3: Mobile Prototypes

_Captured: 2015-11-19 at 20:40 from [signalvnoise.com](https://signalvnoise.com/posts/3978-building-basecamp-3-mobile-prototypes)_

## Interactive prototyping was essential to designing Basecamp 3 for [iOS](https://itunes.apple.com/us/app/basecamp-3/id1015603248?ls=1&mt=8) and [Android](https://play.google.com/store/apps/details?id=com.basecamp.bc3). In this article we'll look at how we chose a prototyping tool and take a peek at a few of our prototypes.

At Basecamp design happens through iteration. We don't make highly-polished comps but instead work right in Basecamp's code making hundreds (even thousands!) of tiny revisions until the design is just right. We can then see and click the work-in-progress design just like our customers will the finished product. We've done it this way for years�--our [workflow](https://signalvnoise.com/posts/1061-why-we-skip-photoshop) and development stack are highly optimized for it.

When designing Basecamp's mobile apps it was a completely different story. Even for the simplest of changes the difference between refreshing a web browser and building an app to a device (or simulator) is orders of magnitude slower. It's worse when you consider that making even seemingly minor visual changes to iOS or Android designs in native code can take much more time than you might expect. Over the course of a day that time adds up. All told, we had to find a better way.

![Basecamp 3 mobile wizard](https://s3.amazonaws.com/37assets/svn/2073-bc3-mobile-hero.jpg)

> _Basecamp 3 mobile wizard_

## Solution: interactive prototypes

We knew right off that static Photoshop mock-ups weren't going to cut it. We wanted to see and touch our designs on real devices. It was tempting to simply make prototypes in HTML, CSS and JavaScript--tools we're very familiar with--but it turns out they're a poor fit for the kinds of designs we wanted to try. Simple things that are essentially free in native code can be difficult or quirky in web browsers. For example, full-screen transitions or fixed navigation bars.

So we set out to find a prototyping tool that met these requirements:

  1. **Fast**. Above all a suitable tool had to be faster and easier than putting something together in native code or even HTML/CSS. It was equally important that the round-trip was short between making changes, previewing them, and making further tweaks.
  2. **Real devices**. We wanted to see and touch designs on real devices, desktop emulation alone wouldn't cut it.
  3. **Shareable**. Prototypes would serve two purposes: Quickly sharing work-in-progress designs for critique and sharing the final, high-fidelity reference designs with our programmers. 
  4. **Cross-platform**. We're all developing on Macs but it was important that any tool worth considering would be suitable for prototyping both iOS and Android app designs.

We looked at a ton of tools and put several through their paces including [Quartz Composer w/Origami](http://facebook.github.io/origami/), [Form](http://www.relativewave.com/form/), [Pixate](http://pixate.com), and [Briefs](http://giveabrief.com) before settling on [Framer](http://framerjs.com).

_N.B., We evaluated these tools nearly one year ago at the beginning of Basecamp 3's mobile development so some of the reasons we choose Framer over the others may no longer be true. In fact, Quartz Composer was my favorite tool to use--the springy-band UI is unique and super-fun--but it lacked on-device preview at the time, a deal-breaker for us that has [since been corrected](https://medium.com/facebook-design/introducing-origami-live-and-origami-2-0-a68116294e65). What I hope you'll find interesting in this article is how Framer met our requirements and what we learned about those requirements after we had been using it regularly_

## Why we picked Framer

The excellent Framer Studio for Mac is a one stop tool for developing, previewing, and sharing prototypes. It consists of two panes: code and preview. Make a code change on the left, try it on the right in real-time. No refreshing or rebuilding.

![Basecamp 3 in Framer Studio](https://s3.amazonaws.com/37assets/svn/2074-framer-studio-bc3.jpg)

> _Basecamp 3 in Framer Studio_

Framer's previewer also includes a nice selection of device frames to wrap your prototypes in including various models, sizes and colors of iPhones, iPads, Apple Watches, and Android devices. _It's so easy to fire-up Framer and drop a screenshot into a prototype that it's even become my go-to tool for making device artwork. _

Framer prototypes are written in CoffeeScript, a language in which I was already familiar that compiles into JavaScript. As much as I loved using Quartz Composer it wasn't intuitive and I had to learn a lot to become proficient. Framer's UI, on the other hand, is code. It felt more like writing web apps. Integrated access to the excellent [documentation on its framework](http://framerjs.com/docs/) made getting started easy. I'd expect most web designers who are comfortable with HTML, CSS, and JavaScript could be productive with Framer in a matter of hours.

When it's time to share a prototype, Framer pushes your prototype to the cloud and provides a private link you can share with anyone--all with a single click. They'll be able to interact with it in their web browser or on their device just by opening the URL. And if they have a copy of Framer Studio on their Mac, they can open your prototype and edit it themselves. It was dead simple to drop a URL in Campfire when we needed feedback.

## What surprised us

Sharing was one of the key requirements in choosing a prototyping tool but it's also the area where our expectations were the mostly incorrect.

The first surprise was that sharing a URL, while handy, didn't provide enough context. In almost every case our prototypes would focus on one particular feature or flow so not every element was interactive and there was no obvious way to communicate to someone what they could tap, or in what order. It turned out the simplest workaround was to record and upload an animated GIF demonstrating the flow. That alone was good enough almost all the time and the actual Framer prototype was only reviewed when someone really needed to see the interaction at full size and high frame rate. [LICEcap](http://www.cockos.com/licecap/) was an excellent tool for quickly capturing screen recordings as GIFs.

It turns out the second scenario: sharing and iterating on prototypes with our native programmers was largely imagined, too. Though we designers may have agonized over the specific timing of every animation, it wasn't necessary for the programmers to install Framer Studio to get it right and I don't think any of them ever did.

Similarly we found that seeing prototypes on actual devices didn't matter as much as we thought it would, at least not at this stage in the design. Instead we used [Skala Preview](https://bjango.com/mac/skalapreview/) in conjunction with Photoshop to get our designs right at the screen design stage. By the time they were animated in Framer, size and proportion were already right.

## A few examples

This first animations shows an early concept in which a menu button would persistently float over all screens giving you quick access to new content via notifications. Click to try the interactive prototype.

![Early prototype animated](https://s3.amazonaws.com/37assets/svn/2075-floating-menu.gif)

> _[Early prototype animated](http://share.framerjs.com/c9wtm76uecyu/)_

Here's a idea for writing comments in a full-screen composer.

![Comments prototype animated](https://s3.amazonaws.com/37assets/svn/2077-composing-comments.gif)

> _[Comments prototype animated](http://share.framerjs.com/j4br0if3iva8/)_

Finally, this is the prototype that lead to the final home screen design in the app today. Again, click to try the Framer prototype.

![Nearly final prototype animated](https://s3.amazonaws.com/37assets/svn/2076-home-6d.gif)

> _[Nearly final prototype animated](http://share.framerjs.com/3ankz26roc6r/)_

In a future post we'll look closer at this design and how we got here. Until then I'd love to hear more about how you're using interactive prototypes in your mobile designs.
