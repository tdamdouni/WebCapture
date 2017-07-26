# JavaScript Style Guide

_Captured: 2016-01-02 at 11:28 from [airbnb.io](http://airbnb.io/projects/javascript/)_

#### **Why does JavaScript need a style guide?**

Let's say you start an e-commerce site.

Your first engineer is Picasso during his blue period. Your codebase quickly becomes filled with Picasso blue period javascript files. He paints you a javascript shopping cart without a problem. He's done it a million times before. But this is his best one. It's his masterpiece. And very blue.

Your second engineer is Salvador Dali. He shows up on his first day with a camera, a single paintbrush, a silly mustache, and starts contributing some crazy surrealist javascript files.

This influences Picasso as they work together and Picasso starts switching things up and begins adding cubism files to the codebase. The codebase is so new that Picasso and Dali can continue adding new files at any time with no harm, because there is no maintenance when it's just two engineers adding new functionality. No one is stepping on each other's toes. There's enough paint for everyone.

Then you hire Monet and he comes in and leaves his impression on everything.

Now you have a blue period shopping cart, impressionist image lazy loading, surrealist photo slide show, and cubism style event tracking in `/app/assets/javascripts`. The javascripts folder becomes a museum.

Let's jump to the future 4 years later. Lots of major functionality has already been built. Picasso has left the company to pursue a company built on a guernica style. Your business focus has shifted a bit and you need someone to extend Picasso's blue period shopping cart to support collaborative shopping (lots of people sharing the same cart in realtime).

Luckily you just hired a rising star in javascript land that likes to spray paint things on the wall, his name is Banksy. So you tell Banksy, "Hey for your first job we need you to modify our shopping cart so it supports collaboration. Timing is really important for the big relaunch, fortunately this should be really easy because we already have Picasso's shopping cart and it's already a masterpiece. Just reuse that."

So Banksy goes in and spray paints over your Picasso shopping cart and makes it collaborative and you have a big successful relaunch.

A month later a bug report comes in about removing items from the shopping cart. Banksy is busy on another project, so you get Monet to go in and fix it.

Monet doesn't know how to use spray paint cans. So his attempts to fix it are sloppy. He breaks the build. He switches back to the brush and just paints over it, but it took a lot longer than it should have because of the time to understand and adopt an unfamiliar style.

When you have over 80 engineers contributing to one codebase, you quickly learn your usual ways of doing things don't work. So we try to turn everyone into Picasso. No matter where you jump in to the codebase, all the files are familiar and look like they were painted by you.

The most important thing, no matter what your preferred javascript style is, is to be consistent when working with a team or a large codebase that will have to be maintained in the future.

The style that works best for our team is our Picasso style since that's how it all started.

We open sourced our style guide so other teams could fork it and turn it into a Monet style guide or a Banksy style guide. Which is lots of fun to [watch](https://github.com/airbnb/javascript#in-the-wild).

As an individual painter/engineer working on side projects and exploring all the wonderful things you can do with javascript, please throw conventions away and ignore everything anyone has ever said.

It's the only way the world will enjoy the next Picasso.
