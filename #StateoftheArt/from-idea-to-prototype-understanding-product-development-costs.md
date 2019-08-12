# From Idea to Prototype — Understanding Product Development Costs

_Captured: 2018-09-14 at 07:07 from [blog.hackster.io](https://blog.hackster.io/from-idea-to-prototype-understanding-product-development-costs-eedae378dd3f?mc_cid=0f60694da5&mc_eid=1c68da4188)_

Developing a new electronic hardware product is of course no trivial task. It requires significant engineering across a variety of disciplines to develop a commercially viable product.

Development costs are the first big obstacle that you are likely to run into, especially if you don't have the experience to do much of the development yourself.

![](https://cdn-images-1.medium.com/freeze/max/60/0*Znj7jUgpNeKLw6vF.jpg?q=20)![](https://cdn-images-1.medium.com/max/1600/0*Znj7jUgpNeKLw6vF.jpg)

_This article was originally published on PredictableDesigns.com. Download their free cheat sheet _**_[15 Steps to Develop Your New Electronic Hardware Product_**](http://predictabledesigns.com/15-steps-develop-your-new-electronic-hardware-product/?utm_source=Hackster)**_._**

In this article, I'm going to run line by line through all the costs that make up your total development cost, so you can understand all the different expenses needed to get a product developed.

I'm also going to give you some ball park estimates on each of these costs but keep in mind most costs vary significantly between different products.

Also be aware that all of the price estimates shown assume you are not doing any of the development work yourself.

The low-end price estimates assume you are outsourcing to freelance engineers, and the high-end price estimates assume you are using a full product design firm. In general, I assume development will be done in the U.S, Canada, or Europe.

**NOTE: **This is a long, very detailed article so here's a **[free PDF version**](https://predictabledesigns.com/pdf-idea-to-prototype-understanding-product-development-costs/?utm_source=Hackster) of it for easy reading and future reference (includes printer friendly version).

The prices will typically be considerably lower if you choose to use **[cheaper freelance developers**](https://predictabledesigns.com/how-to-hire-low-cost-product-developers-but-get-high-value-results/?utm_source=Hackster) in countries like India, Russia, China, Brazil, etc.

The more work you can learn and do yourself the more money you will save. But the additional cost of this strategy is your time, a longer path to market, and potentially a lower quality product. Nothing is ever free!

First, we're going to look at the design of the electronics, then the software development, followed by any mechanical or enclosure development. Lastly, we will look at the package design.

### Electronics Development

#### Preliminary Design

The first step when developing the electronics for a new product is to create a **[preliminary product design**](https://predictabledesigns.com/why-you-should-predesign-your-product/?utm_source=Hackster) which includes a system level block diagram, selection of all critical components, and a preliminary Bill of Materials (BOM).

Creating a preliminary design and BOM allows you to calculate early estimates on the cost to manufacture your product.

Also, by starting with a preliminary design you can more accurately estimate the complexity and cost for all of the other development steps.

**Cost for Preliminary Design: **$1,000 to $5,000

Now it's time to design the schematic circuit diagram, which will take the information from the preliminary design and then fill in all the little details. A schematic diagram is like a blueprint for the electronics for the product. It's a conceptual drawing that shows how everything connects together.

This is where you get into all the little details like the pin numbers, or what pins have to connect up to the value of each resistor and capacitor. All those little details have to now be taken care of as part of the schematic diagram.

Once you have a completed schematic diagram then you can automatically generate a bill of materials via the PCB design software.

Unlike the preliminary BOM, this will be a complete BOM that lists every single electronic component including low-cost passives (resistors and capacitors). However, this will not be the final BOM for your entire product, just for the electronics.

**Cost for Schematic Design:** $2,000 to $8,000

#### Printed Circuit Board (PCB) Layout

The next step is going to be designing the printed circuit board layout.

The **[PCB layout**](https://predictabledesigns.com/tutorial-how-to-design-your-own-custom-microcontroller-board-video-part1/?utm_source=Hackster) will be done in the same software as you used in the schematic design because that way the software can perform the necessary verification to confirm that your PCB layout actually matches the schematics circuit diagram.

Verification is not something you can do manually. This same software also verifies that your PCB layout follows all of the design rules for your particular process.

As far as cost, the schematic design and a PCB layout design are going to be pretty close, but it obviously depends on the product. For instance, you might need a really complex layout if you are using custom wireless radio circuits. In that case, most of the additional complexity is in the PCB layout, not necessarily the schematic diagram.

**Cost for PCB Layout: **$2,000 to $9,500

The cost to prototype a custom PCB is made up of four parts: the empty PCB, soldering of all components, the cost of the components, and the shipping cost.

In most cases you should only order 3-5 boards at a time when [prototyping](https://predictabledesigns.com/how-to-prototype-hardware-product/). During the later stages of prototyping, after you know your product is mostly functional, the number of prototypes can be increased if you need a larger number of test units or product samples.

Keep in mind that any product design will take multiple prototype iterations in order to get it ready for mass manufacturing. You should plan for a minimum of 3 PCB prototype iterations, but 5 or more is also common. It really depends on the complexity of your product.

Using a domestic PCB shop for your prototyping will save you time and money on shipping. But there are also some good Chinese PCB shops that will give you quality prototypes for a considerably lower price. However, when you go offshore you will spend more time and money on shipping which can be considerable.

If money is your primary concern then probably go with an Asian PCB prototype shop, but if speed to market is your main concern then go domestic.

One of the best ways to **[reduce your prototype cost**](https://predictabledesigns.com/tips-for-hardware-startups-to-save-money-and-reduce-risk/?utm_source=Hackster) (and many other development costs) is to always get independent design reviews before you prototype.

Finding problems after you prototype is a lot more expensive and time consuming than finding them as part of a design review. No matter who designed your product -- you, an experienced development firm, or a contracted freelancer, it is wise to get a design review.

**Cost for PCB Prototypes: **$2,500 to $7,500

#### Hardware/Software Integration

Hardware/software integration is where you power up the PCB and make sure the firmware (software embedded in your product) is working and communicating with the mobile app if your product has one.

This is sort of like early product testing, but it's really about integrating all the pieces of your product together properly. The hardware, the firmware and the mobile app need to all work together.

**Cost for Hardware/Software Integration: **$3,000 to $9,500

#### Testing/Debug

This is the stage where you need to fully test the product and determine fixes for any problems that are found. Obviously, the integration step includes some testing, but this separate item is more for debugging any problems that are found.

Don't expect your first version of a product to be perfect. It's almost guaranteed you're going to have some type of problem and you're going to have to debug it.

Debugging tends to be a step that's difficult to forecast. It is hard to know how long debugging will take, and how much it's going to cost, since you don't know about these problems ahead of time. Otherwise, you would have already fixed them.

You're always dealing with unknowns in the debug stage. Whereas, the cost for more predictable steps like schematic design or PCB design are usually easier to accurately estimate.

**Cost for Testing/Debug: **$3,000 to $9,500

#### Documentation

It's critical that the development of your product is fully documented. You don't want to receive a design without any type of documentation. This documentation is necessary as your company grows, and you bring on your own engineers, or you switch firms or developers.

It's always critical to have proper documentation on the product design so other people can pick up and continue with the design or try to fix any problems.

Most development firms will include documentation, but I have found that freelancers typically won't. Make sure to specify upfront that you want written documentation on all the details of the product.

**Cost for Documentation: **$1,500 to $5,000

### Software Development

The software development can be primarily broken down into three categories: firmware, mobile applications, and PC software.

#### Firmware Software

Firmware is the software running on the processor embedded inside a product (usually a microcontroller but for more advanced products it will be a microprocessor). **[Firmware**](https://predictabledesigns.com/introduction-to-programming-stm32-arm-cortex-m-32-bit-microcontrollers/?utm_source=Hackster) is low level software that interfaces closely with the hardware.

Many times, a firmware programmer will be an electrical engineer because a deep understanding of the hardware is necessary.

**Cost for Firmware Software: **$7,500 to $50,000 (sorry, but there is a huge variation in this cost depending on the software complexity).

#### Mobiles Apps / PC Software

Mobile apps and PC software, on the other hand, utilize higher-level programming that doesn't require an understanding of hardware. This programming is typically handled by software programmers (software engineers, computer scientists, etc.) and not electrical engineers.

Most products that require a **[mobile app**](https://www.newgenapps.com/blog/bid/219838/10-steps-to-create-a-successful-mobile-application) will need two separate versions: one for Android and one for Apple iOS. This almost doubles your mobile app development cost so you may consider offering only one version for your early market testing.

The exact cost of all the software development of course depends on the product. For many products, the software will be more expensive to develop than the hardware.

There are obviously exceptions to this, but for most of the products I've seen, the software development ends up costing more than the electronics design.

This is especially true if you require a mobile app that is really fancy with lots of graphics and a complex user interface. This type of app can be very expensive to develop and commonly requires a lot of communication with the developer.

**Cost for Mobile App : **$7,500 to $50,000

### Industrial Design / Enclosure Development

Now we're going to look at the mechanical aspects for a hardware product. For most products this is going to be the enclosure that holds the electronics.

There are exceptions, like products with motors and lots of different moving parts, but for most products the majority of the mechanical development is for the enclosure.

#### 3D Model Design

It all begins with a 3D model. Although, sometimes a simple clay model is useful to create first. The primary work of designing the enclosure is designing the 3D model and then getting that model ready for manufacturing.

A 3D model for prototyping can be considerably different than a 3D model that's compatible with mass manufacturing. This is because the manufactured version of a plastic enclosure will be made using injection molding technology, instead of 3D printing.

You can 3D print just about any shaped product. On the other hand, **[injection molding**](https://predictabledesigns.com/introduction-to-injection-molding/?utm_source=Hackster) is very restrictive on what shapes you can produce.

Typically, you'll design a 3D model for the prototype stage. Once you have perfected the enclosure using 3D printing technology, you need to go back and make the final tweaks necessary to get it **[ready for injection molding**](https://www.3dhubs.com/knowledge-base/how-design-parts-injection-molding).

**Cost for 3D Model : **$3,500 to $15,000

#### Photorealistic 3D Model

The next step is creating a photo realistic 3D model. If you want to use the 3D model for marketing purposes or to attract investors, you can make the model look more photo-realistic which is an additional step.

The person designing the 3D model should be an industrial designer or mechanical engineer that will focus on making sure they're developing an enclosure that can be mass manufactured. They'll be dealing with manufacturing related issues and designing the enclosure so it works and looks like you want.

The photo-realistic 3D model is more artistic in nature so you may need to find a non-engineer to turn your 3D model into something more realistic looking that can be used in presentations.

**Cost for Photorealistic 3D Model : **$500 to $1,500

#### Enclosure prototyping

Next you have the prototyping cost for the enclosure itself, which is typically the cost of 3D printing. Just like with the electronics, do not expect the first prototype to be the final version.

You'll find with the enclosure, like everything in hardware development, there are lots of little details that you won't necessarily think of upfront. It's going to take multiple versions to reach perfection. Even something as simple as getting two pieces of plastic to snap together properly can be a challenge.

Obviously, you can do a lot in a 3D modeling program, but you will also need to get the plastic in your hands to test it out. Always expect on producing more than just one **[prototype**](https://blog.dragoninnovation.com/2018/07/02/prototype-to-product-the-quick-and-dirty/).

If you anticipate that you will need a high number of prototype iterations then you may want to consider purchasing your own 3D printer. Having your own 3D printer is also beneficial if speed to market is important for your product.

Being able to almost instantly iterate your prototype is a huge advantage that will significantly reduce your development time. The downside is that the prototype quality may not be as good compared to using a professional prototype shop.

**Cost for Enclosure Prototypes : **$2,500 to $7,500

#### Package Development

Finally, you have the **[package design**](https://predictabledesigns.com/how-to-package-your-new-hardware-product/?utm_source=Hackster). If you're going to sell your product in retail stores this becomes even more critical. On the other hand, if you're going to sell your product primarily online, then the package isn't quite as important.

For retail, the package has to sell your product. It needs to look really nice, explain the product, stand out on the shelf, and all that good stuff. This is in contrast to selling through your website, where the package primarily serves to protect the product during shipping.

The two most common package types are plastic clamshells for smaller products, and retail boxes for larger products or products with lots of different pieces. You will need to hire a graphic artist to design the artwork for your package.

You will also need to make a 3D model for any custom shaped plastic required for your packaging. This can usually be done by the same person that created the 3D model for your product's enclosure.

Any custom plastic pieces will need to be custom molded. Be sure to plan for this additional plastic production which will require its own 3D model, injection molds, prototyping, 3D prototyping and such.

Don't forget, you may also need to write and design an instruction manual for your product. I typically find that the founder is the best person to write the first draft of a manual. You can always get someone involved later to edit and fine tune it.

**Cost for Package Development : **$1,500 to $4,500

#### Project Management

The last cost I'll address is for project management.

To develop a commercial product there are lots of pieces that must all come together. Multiple engineers are almost always required including electronic engineers, firmware programmers, app programmers, industrial designers, mechanical engineers, manufacturing engineers, etc.

Project management is necessary to ensure that all of the various parts of development eventually merge together to form the final product. All of those engineers must be properly managed.

If you hire a firm to fully develop your product then they will likely handle the project management (and bill you appropriately for it).

Whereas with freelancers you must hire multiple engineers for different parts of product development. You're going to have to be the one responsible for managing all those engineers, and making sure that all the different pieces of the product integrate and come together to form the final product.

If you're comfortable with project management and have the necessary technical skills, then I definitely advise that do all this yourself which will save you significant money.

If you don't have the technical skills, or aren't comfortable managing a complex project, then that's going to make working with freelancers a bit more challenging for you. In that case, a development firm is probably going to be your best bet, but then the costs are going to be higher.

**Cost for Project Management : **$3,500 to $10,500

### Conclusion

We've taken a deep dive into all the various development costs required to get your product to market. These costs can vary significantly from product to product, but the estimated ranges I've provided will at least give you an idea of what to expect.

Development costs are one of the primary obstacles you will need to overcome to get your product to market. In order to have a chance at success you absolutely must have realistic expectations on the cost to develop your product.

Knowledge is power, and that is especially true when bringing a new physical product to market. Having unrealistic expectations is one of the biggest reasons hardware entrepreneurs fail, so be sure you know the costs that lie ahead.
