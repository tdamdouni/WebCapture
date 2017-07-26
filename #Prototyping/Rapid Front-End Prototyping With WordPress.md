# Rapid Front-End Prototyping With WordPress

_Captured: 2015-06-27 at 00:09 from [www.smashingmagazine.com](http://www.smashingmagazine.com/2015/06/26/rapid-front-end-prototyping-with-wordpress/?utm_medium=App.net+Broadcast&utm_source=PourOver)_

Prototyping is one of the best things that can happen within a project, yet it is extremely underutilized. **Prototyping makes a project better suited to users**, elevates user experience, increases the quality of your final code, and keeps clients happy.

The problem is that developers often see prototyping as a waste of time, since high-quality prototypes take considerable effort to make. I want to show you that by using WordPress, highly interactive prototypes with great visuals are not at all that difficult to make.

![Rapid Front-end Prototyping With WordPress](http://media.mediatemple.netdna-cdn.com/wp-content/uploads/2015/06/01-featured-opt-small.jpg)[1](http://www.smashingmagazine.com/2015/06/26/rapid-front-end-prototyping-with-wordpress/)  


> _(Image credit: Jeff Sheldon via Unsplash) (View large version)_

First, we'll look at some basic prototyping concepts, then set up a test server from scratch. We'll continue by converting an HTML template to a WordPress theme and learning how to use its items to create what we need. We'll also learn how to add front-end and server-side functionality to our prototype.

While all this seems complex, beginners should be able to follow along easily, including the "create your own server" section, which is a cinch!

### About Prototyping

> "[A] prototype is an early sample, model, or release of a product built to test a concept or process or to act as a thing to be replicated or learned from."

This sentence neatly sums up the pros and cons of a prototype. The advantage of creating a prototype is that it lets you **test an idea and learn from the process**. It allows you to make a reasonable assumption about the feasability of your project before you put in hundreds of hours of work.

One of the downsides is that prototypes are made so that we may learn from them. Often, designers and coders look on this as wasted time. Why make a protoype when we could be working on the real thing? Who is going to pay us for the time we spend prototyping?

To be honest, these are tricky questions. For smaller projects, no one will pay you for it, but your project will be better for it; this, in turn, leads to bigger and better projects. In most cases, the time you spend prototyping is regained while building the product anyway!

It also appears that designers like to prototype a lot more than developers. The root of the issue here is speed. A designer could prototype a design a lot faster than a developer, since the latter needs to build a quick framework, implement a design and do a lot of fiddly things which take time.

### Fidelity And Functionality

We can approach prototypes by looking at two key features: fidelity and functionality. _Fidelity_ refers to how detailed the prototype is visually, while _functionality_ refers to the level of interaction possible within the system. Let's look at how levels of fidelity and functionality in prototypes pair up.

#### Low-Functionality, Low-Fidelity

These prototypes are easy to make. They could be simple drawings, or [Balsamiq mock-ups](https://balsamiq.com/products/mockups/). There is minimal interaction -- or none at all -- and visually the prototype has very little to do with the final product.

![A Balsamiq mock-up of Facebook](http://media.mediatemple.netdna-cdn.com/wp-content/uploads/2015/06/02-balsamiq-facebook-opt-small.png)[6](http://www.smashingmagazine.com/2015/06/26/rapid-front-end-prototyping-with-wordpress/)  


> _A Balsamiq mock-up of Facebook. (Image credit: Frontify)(View large version)_

#### Low-Functionality, High-Fidelity

Increasing the fidelity while keeping functionality low is also quite common. A good example would be a Photoshop design file which could contain final design elements. Again, there is next to no interaction here but plenty of visual detail, enough to put it close to the final product in terms of design.

![A high-quality PSD mock-up of notifications](http://media.mediatemple.netdna-cdn.com/wp-content/uploads/2015/06/03-notifications-psd-opt-small.jpg)[9](http://www.smashingmagazine.com/2015/06/26/rapid-front-end-prototyping-with-wordpress/)  


> _A high-quality PSD mock-up of notifications. (Image credit: Pixeden)(View large version)_

#### High-Functionality, Low-Fidelity

These prototypes are a bit more difficult but you can still make them without too much effort. Before you create the login/forgot password form for a large website, you might want to test if everything works by just dropping in a form and business logic strictly in HTML and PHP -- no CSS, JavaScript or consideration of the context of the form.

![Twitter without any CSS](http://media.mediatemple.netdna-cdn.com/wp-content/uploads/2015/06/04-twitter-opt-small.png)[12](http://www.smashingmagazine.com/2015/06/26/rapid-front-end-prototyping-with-wordpress/)  


> _Twitter without any CSS. (View large version)_

Using front-end frameworks like [Bootstrap](http://getbootstrap.com/) or [Foundation](http://foundation.zurb.com/) can can increase your fidelity somewhat, but you'd need to write a good amount of CSS to make it your own.

![A medium fidelity mock-up](http://media.mediatemple.netdna-cdn.com/wp-content/uploads/2015/06/05-bootstrap-opt-small.png)[16](http://www.smashingmagazine.com/2015/06/26/rapid-front-end-prototyping-with-wordpress/)  


> _A medium fidelity mock-up. (Image credit: Bootstrap)(View large version)_

I would still consider these low-fidelity mock-ups because each front-end framework looks generic by default. That's fine for testing the principle, but it doesn't increase fidelity to a point where more sensitive clients would be able to visualize what the final product will be like.

#### High-Functionality, High-Fidelity

Prototypes like this are rarely seen because creating them can take more time than is worth it. Why create something so similar to the website-to-be when you could be working on the actual site?

High-functionality, high-fidelity prototypes contain a high degree of interactivity while also being a much closer facsimile of the final product. Users can follow links, submit forms and do many other things that help them see what the end result will be like.

The real trick is managing the time spent on making such prototypes -- which is where WordPress comes in.

### Which One To Use

There is, of course, no simple answer to this question. A high-fidelity, high-functionality prototype is closest to the real thing, but it takes time to make; for simpler projects, it may not be worth the time.

Low-fidelity, low-functionality prototypes are simplistic and cannot be interacted with, but for small projects and close-knit teams, perhaps they're all that is needed.

Several factors need to be considered:

  * How well your team works together
  * How large your project is
  * How visually and technically oriented your client is
  * How well you understand the product you are building
  * How many people will be involved other than programmers and designers

In my experience, the **most important factors are the client and the project's complexity**. Even if I understand the project well, I would like a high-fidelity, high-functionality prototype just in case. One of the fundamental mistakes you can make in projects is thinking you know them well.

For complex, large-scale projects you should always create prototypes with a high degree of freedom. The more systems and subsystems you need to build, the more intertwined they become and the more places things can go wrong.

The client can be an even bigger factor. Often, clients do not know what they want. They may not be design- or code-oriented, which means they will equate a low-fidelity prototype with bad design and missing features -- even if you tell them what the prototype is for. As a result, a clearer visual aid is sometimes called for to enhance communication.

Since I will be talking about high-fidelity and high-functionality prototypes from now on, I will be calling them high-quality prototypes. This is not at all a reflection on other prototypes; a low-fideltiy, low-functionality prototype can also be created with high quality.

### Considerations For High-Quality Prototypes

There are a number of considerations when making high-quality prototypes. What platform they should be built on, what functions need to be added (or not added), how intricate should we make the design, and so on.

#### The Platform

The platform chosen should be one which allows you to work fast and quickly add features as well. Bootstrap, Foundation and other frameworks are great, but they offer very little functionality, since they are purely front-end. Using them can still be a good idea, but not on their own.

On the other side of the spectrum, we have PHP frameworks like Laravel, which is excellent for creating high-quality modular code. This is out of the question, though, since we have to write too much business logic ourselves just to get a site up and running.

WordPress strikes a good balance here because it is essentially a bag of useful functions combined with a reasonably flexible way to template pages quickly. I want to stress that **you should use a platform you feel comfortable with**. If you're amazing at using Laravel, by all means go with it.

#### The Design

You can create a simple design framework for yourself, but that also takes quite some time. This is the place to use front-end frameworks to lighten your workload.

What I recommend is getting a good pre-made HTML admin template. Many of these templates use Bootstrap or Foundation anyway, and put a bunch of elements at your fingertips. In addition, they've already styled the elements of their frameworks into something less generic, which is just what we need. With a little work they can be converted to WordPress themes and will facilitate extremely quick prototyping.

I don't use bespoke WordPress themes because they are for presenting content, not creating application architecture. You won't be able to create a menu or a form anywhere easily, and your code will likely be a mess by the end.

#### Depth Of Functionality

Depth of functionality is all about interactivity. Since you have control over a CMS you can, in theory, make things work properly -- login forms could genuinely log you in. You probably don't want to spend your time coding in all the functionality. That isn't really the point here.

For example, is the login form really important? Everyone knows how logging in works. Perhaps the form can be allowed to be blank, and the login button logs you in immediately as a test user.

If you are building a finance management app, however, you may want to spend some time making sure that the "Add transaction" form works as expected. Real data can be listed and submitted adding a great deal of depth to your prototype.

### Prototyping With WordPress

I think WordPress is a great choice for prototyping because of the **flexibility of templating and the number of functions** you have at your disposal. Logging in and out, adding metadata, querying items -- a lot of base functionality is already there.

I like to choose a pre-made HTML admin theme that looks close to what we'll be doing in the final iteration of the design. You can find a large number of premium admin themes on [Themeforest](http://themeforest.net) but you can also grab some good free ones via a quick Google search. For my examples I will be using a free admin theme called [AdminLTE](http://shapebootstrap.net/item/adminlte-dashboard-and-control-panel/).

When choosing an admin theme try to gauge what features you will need. Concentrate on the **rapid** aspect of prototyping, not making sure that your prototype looks like the final design.

### A Complete Example

When I started this article, I wanted to provide a complete example of how I use WordPress to prototype. I ended up recording a video of the process and writing about it in a bit more detail. The video below will walk you through my process of creating a prototype of the Twitter front page.

Following the video I'll go into even more detail, giving you some instruction about setting up test servers, using the WordPress menu system to populate menus, and much more. I recommend watching the video first, and then looking at the details below, as they will be a lot clearer.
