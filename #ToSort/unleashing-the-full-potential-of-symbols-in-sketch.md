# Unleashing The Full Potential Of Symbols In Sketch

_Captured: 2017-04-20 at 15:02 from [www.smashingmagazine.com](https://www.smashingmagazine.com/2017/04/symbols-sketch/?utm_campaign=coschedule&utm_source=twitter&utm_medium=smashingmag)_

Meet the new [Sketch Handbook](https://shop.smashingmagazine.com/products/sketch-handbook?utm_source=magazine&utm_campaign=sketch-handbook&utm_medium=html-ad-content-1), our brand **new Smashing book** that will help you master all the tricky, advanced facets of Sketch. Filled with **practical examples and tutorials in 12 chapters**, the book will help you become more proficient in your work. [Get the book now ->](https://shop.smashingmagazine.com/products/sketch-handbook?utm_source=magazine&utm_campaign=sketch-handbook&utm_medium=html-ad-content-1)

No matter whether you are designing a whole design system or just a couple of screens, symbols in Sketch will help you keep your file organized and will save you a lot of time in the long run. In this article, I'll share with you a few best practices and tricks to help you unleash symbols' full potential.

But first, a bit of a backstory. I started using Sketch a few years ago, as a replacement for my favorite design software back then, [Fireworks](https://www.smashingmagazine.com/category/fireworks/), which had been [discontinued](https://www.smashingmagazine.com/2013/12/present-future-adobe-fireworks/) by Adobe -- [leaving a whole generation of designers](http://blogs.adobe.com/fireworks/2013/05/the-future-of-adobe-fireworks.html) broken-hearted. Since my first days of using Sketch, I was very surprised by how easy and straightforward it is to use. I had, once again, found an application focused on user interface (and icon) design -- and nothing else.

The apparent lack of features in Sketch, compared to the alternatives [full of menus and stacked panels](https://twitter.com/phlntn/status/715367818254921730) that I was used to, was in fact one of its major advantages and helped me to design faster. Among those few features, symbols were the thing that I used very frequently, and still do, practically every day (yes, even on Sundays… you know, a freelancer's life).

What are symbols? In a nutshell, symbols enable you to use and reuse an element across a project, keeping a **master symbol** that **automatically updates** other instances of the symbol when changes are made to it.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/04/system-780w-opt.png)[5](https://www.smashingmagazine.com/2017/04/symbols-sketch/?utm_campaign=coschedule&utm_source=twitter&utm_medium=smashingmag)

> _Symbols are essential to building a design system formed by elements and components that will be used across all of your project. (Source: "[How We're Using Component-Based Design](https://medium.com/@lewisplushumphreys/how-were-using-component-based-design-5f9e3176babb)[6](https://www.smashingmagazine.com/2017/04/symbols-sketch/?utm_campaign=coschedule&utm_source=twitter&utm_medium=smashingmag)") ([View large version](https://www.smashingmagazine.com/wp-content/uploads/2017/04/system-large-opt.png)[7](https://www.smashingmagazine.com/2017/04/symbols-sketch/?utm_campaign=coschedule&utm_source=twitter&utm_medium=smashingmag))_

This concept is not exactly new (nor is it exclusive to Sketch, to be honest). However, if you design interfaces, then you'll find it extremely useful, especially when using components as [part of a design system](https://medium.freecodecamp.com/how-to-construct-a-design-system-864adbf2a117).

In this article, I'll outline how to make use of symbols in Sketch in order to unleash their full potential, going from the most basic situations to some more advanced use cases. I'll also include some tips and tricks that I have learned along the way.

Before digging deeper, and in case you are new to Sketch, let me give you a short introduction to how symbols work.

Symbols can be made from almost any elements in Sketch: text objects, shapes, bitmap images, even other symbols (we'll talk about this later). Inside every symbol (double-click a symbol to enter edit mode), you'll find one main artboard containing the symbol's layers. This artboard also defines the symbol's boundaries.

Usually, symbols are created for those elements in an interface that you expect to reuse later on (such as buttons, list items, tabs, etc.) and that will be spread across different screens, pages and artboards in your designs.

**Note:** For future reference, keep in mind that "copies" of one symbol are called **instances**.

The best thing about using symbols (instead of grouped, independent and disconnected objects) is that if at some point you decide to change some property in a particular symbol (for example, the color, shape, text size, dimensions or whatever else you want), you'll just need to edit the symbol's **master** once, and this change will be automatically replicated to all of the master's instances, wherever they are. I don't know about you, but I find this super-convenient!

Just like in life itself, it's fundamental to keep everything in order. Always design as if someone else will later need to open and work with your design file and understand it without your help! This also applies to the way you name symbols -- naming should meet certain criteria.

One recommendation is to use a slash (`/`) in the symbol's name. Sketch will automatically create a category with the part _before_ the slash, and will name and place the symbol inside it, using the part of the name _following_ the slash. For example, if you have two symbols named "Button/Primary" and "Button/Secondary," here is how they will look like when you try to insert them from the toolbar:

![](https://www.smashingmagazine.com/wp-content/uploads/2017/04/buttons-780w-opt.png)[13](https://www.smashingmagazine.com/2017/04/symbols-sketch/?utm_campaign=coschedule&utm_source=twitter&utm_medium=smashingmag)

> _Naming symbols properly can help you create a neat hierarchy system, which will help you find symbols faster. (_

You can repeat this many times to have several symbols under the same root, grouped by similar logic, making them easier to find. And if your "tree" grows too big, take a moment to reconsider your naming system and see if there's any possible way to optimize it and make it more manageable.

There are many different conventions for how symbols should be named, perhaps one convention for every designer out there. Personally, I prefer not to use names that refer to the visual properties of the elements -- for example, "Red Button" would be a bad choice in my opinion because if the color of the button changes later on for some reason, the name of the symbol will become incorrect. Instead, I try to differentiate the symbol's **function** and **state** (such as "Primary/Disabled").

In any case, just **be consistent** and find something that works for both you and your team, then stick to it; don't switch the naming system according to the case! This also applies to **layers** inside symbols: some designers even [use emojis](http://emojipedia.org/) to mark which of them are meant to be editable (for example, by adding a pencil emoji to the name). To do this, press `Control + Command + Space` to open a dialog [to select emojis](http://www.imore.com/how-to-use-emoji-on-your-mac).

![](https://www.smashingmagazine.com/wp-content/uploads/2017/04/emojis-preview-opt.png)[17](https://www.smashingmagazine.com/2017/04/symbols-sketch/?utm_campaign=coschedule&utm_source=twitter&utm_medium=smashingmag)

> _Adding an emoji to a layer's name is an option when you want to highlight its purpose._

**Note:** Regarding symbols' names, bear in mind that instances will take their names from the master symbol, but you can change them afterwards to whatever you want. This way, instances of the same symbol can have different names from each other.

When you create a symbol, Sketch asks whether you want to send it to the [symbols page](http://www.sketchtips.info/articles/the-power-of-symbols). My advice is to check this box, even if after a while (and a few symbols later) this dedicated page turns into a mess. (Sketch places one symbol next to the other as they are being created, and when you delete a symbol, you'll notice the blank space left in its spot.)

Instead, what I do to sort this out is to create my own symbols page (which is just a regular page, which I would usually name "Symbols") where I can arrange symbol instances in the order I want and, thus, ignore the official symbols page.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/04/page-780w-opt.png)[19](https://www.smashingmagazine.com/2017/04/symbols-sketch/?utm_campaign=coschedule&utm_source=twitter&utm_medium=smashingmag)

> _The symbols page (left) can easily become disorganized, which is why I prefer to have my own separate page (right) where I can organize symbols' instances in the way I think best. ([View large version](https://www.smashingmagazine.com/wp-content/uploads/2017/04/page-large-opt.png)[20](https://www.smashingmagazine.com/2017/04/symbols-sketch/?utm_campaign=coschedule&utm_source=twitter&utm_medium=smashingmag))_

This way, I can create artboards that follow categories (such as lists, buttons, inputs and so on) and place symbols in a way that I find convenient and that makes sense to me. You'll still need to invest some time to update this page from time to time, but once it is created, it will make everything much easier and you'll be able to build a new screen in no time.

**Note:** If you prefer to use the symbols page instead, there's the [Symbol Organizer plugin](https://github.com/sonburn/symbol-organizer), which could help you keep everything arranged.

Replacing an existing symbol with another is easy. Just select the symbol and choose "Replace with" from the contextual menu that appears when you right-click over the symbol instance. Then, select the new symbol that you want to use. Keep in mind that the new symbol will keep the **same size and position** as its predecessor; you can fix this by selecting "Set to original size" from the same contextual menu.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/04/replace-animated.gif)[22](https://www.smashingmagazine.com/2017/04/symbols-sketch/?utm_campaign=coschedule&utm_source=twitter&utm_medium=smashingmag)

> _Replacing symbols_

Once you've made a symbol, you can detach it to recover the elements that form it as a group. To do this, just select "Detach from symbol" in the same contextual menu that I mentioned earlier.

Symbols, like other elements, can also be exported as bitmap images. To do this, you'll need to mark elements as exportable. (Select the symbol instance, and then choose "Make Exportable" at the bottom of the Inspector.)

The problem that I found during this process is that if the symbol has some padding (for example, if the shapes inside are smaller than the symbol's total size), when doing the export, Sketch will **omit the blank space** and will just create an image with the **visible content** only.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/04/slice-780w-opt.png)[23](https://www.smashingmagazine.com/2017/04/symbols-sketch/?utm_campaign=coschedule&utm_source=twitter&utm_medium=smashingmag)

> _Exporting the symbol directly will create an image that contains only the shapes (left). Make use of slices (right) to match the symbol size before exporting. (View large version)_

One way to work this around is by using a [slice](https://www.sketchapp.com/learn/documentation/exporting/slices/). When creating the slice, place it over the instance and make sure it matches the size of the instance's boundaries (width and height); then, select the slice and use the exporting options as needed.

**Side note:** This same trick also applies to other tools, such as [Zeplin](https://zeplin.io/).

In this world full of screens with multiple sizes and aspect ratios, it's important to make sure your design adapts to many different scenarios. This is easier to accomplish if you don't have to design everything from scratch every time, by reusing elements (or symbols, as I'm sure you've already guessed).

![](https://www.smashingmagazine.com/wp-content/uploads/2017/04/general-animated.gif)[29](https://www.smashingmagazine.com/2017/04/symbols-sketch/?utm_campaign=coschedule&utm_source=twitter&utm_medium=smashingmag)

> _A variety of resizing options are available in Sketch. These are very useful when you are looking to adapt your symbols to different dimensions._

This is where the resizing options in symbols come in handy, helping you to use the same element with different widths and heights with no hassle: If you resize just one instance by selecting it, this **won't affect the other instances**. (But remember that resizing options are applied to individual layers inside the master symbol, not to the instance itself. So, even while you can adjust sizes individually from instance to instance, elements inside will always maintain the same behavior.)

**Note:** The options outlined below apply not only to symbols, but to groups as well. Behaviors are not always predictable, so chances are that you'll have to play around and explore a bit before finding what you need, combining one or two different settings in most cases.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/04/stretch-animated.gif)[30](https://www.smashingmagazine.com/2017/04/symbols-sketch/?utm_campaign=coschedule&utm_source=twitter&utm_medium=smashingmag)

> _In this example you can see how the yellow shape will remain one third of the total width of the symbol, no matter what the total width of the symbol is._

When the Stretch option is used, a shape that has specified, let's say, 50% of the symbol's total width will keep this same relationship when the instance is extended vertically or horizontally. This is the default behavior.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/04/pin-to-corner-animated.gif)[31](https://www.smashingmagazine.com/2017/04/symbols-sketch/?utm_campaign=coschedule&utm_source=twitter&utm_medium=smashingmag)

> _The yellow shape has the "Pin to Corner" option applied to it, so it sticks to the closest corner._

"Pin to Corner" will (as the name suggests) pin an element to the nearest corner, and the element will not resize, keeping the same distance to this corner. Keep in mind that if the object is centered (with equal spacing from both sides), it won't know which one is the nearest corner, so it'll stay in the middle.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/04/resize-animated-1.gif)[32](https://www.smashingmagazine.com/2017/04/symbols-sketch/?utm_campaign=coschedule&utm_source=twitter&utm_medium=smashingmag)

> _The yellow shape has the "Resize Object" option applied to it. You can better understand what is happening by also looking at the pink squares, which are for reference only._

When "Resize Object" is used, elements will grow while keeping an equal (or fixed) spacing from the sides.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/04/float-in-place-animated.gif)[33](https://www.smashingmagazine.com/2017/04/symbols-sketch/?utm_campaign=coschedule&utm_source=twitter&utm_medium=smashingmag)

> _With this option, the element won't resize, keeping the relative position to the boundaries of the symbol._

"Float in Place" will make an object stay the same size and will keep its relative position to the boundaries of the symbol.

If you have resized your symbol but aren't satisfied with the result, you can always go back to the beginning by choosing "Set to original size" from the contextual menu.

Keep in mind that symbols have dedicated artboards, and these will define the symbols' boundaries (even when shapes inside overflow on them). You can make the symbol's artboard the same size as of its contents by selecting it and choosing "Resize to fit" from the Inspector.

In the width and height input fields in the Inspector, you can use operators to change values. For instance, you can use `100*2` to set an element's dimensions to 200 pixels. Other operators are `+` (add), `-` (subtract) and `/` (divide).

Besides mathematical operators, in the same input fields you can also use `L` to scale an object from the left (this is the default), `R` to scale it from the right, `T` to scale it from the top (this is the default), `B` to scale it from the bottom, and `C` and `M` to scale it from the center or middle.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/04/stretch-right-animated.gif)[34](https://www.smashingmagazine.com/2017/04/symbols-sketch/?utm_campaign=coschedule&utm_source=twitter&utm_medium=smashingmag)

> _When you resize a rectangle using its upper-right corner as an anchor, the shape will grow out of its left and bottom sides._

For example, if you have a shape that has a width of 200 pixels and want to resize it so that it scales from the right to the left side, you can use something like `300r` in the width input field.

  * "[Sketch 39 Resizing: Cheat Sheet](https://medium.com/sketch-app-sources/sketch-39-resizing-cheat-sheet-feec0450e7e2)" Peter Nowell  
This article is a good reference for understanding the differences in resizing. It also includes some other tips and tricks, so give it a go!

What could be better than one symbol? Perhaps a symbol with another one inside it!

This feature is kind of new in Sketch, and it gives you a lot of possibilities when combining symbols together. You can place one symbol on top of another, select both, and then create a new symbol that contains the two instances. You can repeat this as much as you'd like. Be moderate, though, or else you'll find yourself digging into levels and levels of nested symbols, one inside another. This could make maintenance much harder and could also be a symptom of bigger organizational problems.

Nesting symbols can be especially useful when you need to create **variations** of one symbol. For example, you could follow a process like this:

  1. Pick up one symbol that will serve as a base. (this symbol will remain the same in all cases.)
  2. Overlap it with other symbols (such as icons or badges), which could be there or not, depending on the case.
  3. Finally, create another symbol with the resulting design.

In the image below, you can see that all rows share the same characteristics (they have the same size, text properties and amount of padding on the left), so I created a base symbol that contains only these elements (i.e. elements that will be shared with the other symbols). Using this symbol as a starting point, I then created some overlapping elements that are different, saving the result in each case as a different symbol; so, all of the symbols under "Variations" are actually different symbols.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/04/nested-preview-opt.png)[36](https://www.smashingmagazine.com/2017/04/symbols-sketch/?utm_campaign=coschedule&utm_source=twitter&utm_medium=smashingmag)

> _An example of different symbols created from a common base, with variations in each case._

But you don't -- necessarily -- need to create a new symbol for every state of the row. There may be a simpler way: using overrides.

If you had to create a lot of different symbols just because one part of their content changes, you'd probably go nuts. One of the main purposes of symbols is precisely to have to design as little as possible and to have fewer elements -- and, therefore, more control over them. Enter nested overrides!

![](https://www.smashingmagazine.com/wp-content/uploads/2017/04/overrides-01-animated.gif)[37](https://www.smashingmagazine.com/2017/04/symbols-sketch/?utm_campaign=coschedule&utm_source=twitter&utm_medium=smashingmag)

> _This navigation bar is a symbol that contains the inactive tabs (which are symbols as well). Active tabs are symbols created separately; they override the inactive tabs when necessary._

One practical example of this workflow could be designing a tab bar with different states. In this case, the main symbol with the inactive tabs would act as the base, and then there would be a different symbol for each one of the highlighted tabs. Just choose the one that you want from the "Overrides" options in the Inspector.

**Note:** For this technique to work, keep in mind that the inactive tabs inside the main symbol (the navigation bar) need to be symbols as well. Also, be sure that all symbols (both inactive and active ones) **have the exact same dimensions** (width, height). Otherwise, they won't appear as available options in the "Overrides" dropdown menu.

Let's look at another use case. If you have multiple buttons in a design but with different text labels on them, then the Overrides option will enable you to change the **text value** (not the font family or font size -- you have to modify those inside the symbol itself, when editing the symbol master), without having to create a new symbol each time. This is as easy to do as selecting the instance and changing the text content in the Inspector.

Overrides apply not only to text; you can also use them for bitmap images and even for other symbols, as mentioned before. This way, you can have several instances of a symbol, with a different image in each one of them -- and all of this without having to modify the symbol's master.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/04/placeholder-animated.gif)[38](https://www.smashingmagazine.com/2017/04/symbols-sketch/?utm_campaign=coschedule&utm_source=twitter&utm_medium=smashingmag)

> _Let me show you how overriding images works with something that I usually do when designing._

There are cases when I don't want to have any particular image as part of a symbol's master. So, what I usually do is to create an empty PNG file with **no visible content**, create a shape, and use this image as a **pattern fill** (you can find this option in the "Fill Options" when selecting a shape). Then, when doing the symbol overriding, I just replace this transparent image with the one that I want in each case!

To get the most out of this practice, I also use a layering system with an icon or element that acts as a placeholder underneath the image and that will be visible only if I keep the original transparent bitmap. One benefit of doing this is that I can simulate this empty state that will appear when images are loading in the finished product, something that I consider necessary to design anyway.

One of the reasons why being organized is a good idea is because the way you name and order layers will affect the way they are displayed in the "Overrides" panel. The labels to the left of the input fields in the Inspector will respect the name and order you've previously defined inside the symbol itself, so you'd better pay attention to this order if you want to have a more efficient workflow.

You can replace a nested symbol with another symbol only if the new symbol has the **exact same width and height** as the current element.

When changing the text's value in the Overrides options, you can make an element move as needed when the one to its left is longer (see the following illustration).

![](https://www.smashingmagazine.com/wp-content/uploads/2017/04/input-preview-opt.png)[39](https://www.smashingmagazine.com/2017/04/symbols-sketch/?utm_campaign=coschedule&utm_source=twitter&utm_medium=smashingmag)

> _Top (first field): This shows the original symbol. Bottom (second field): This illustrates how the "Optional" label moves to the right because of the previous label's length (in this case, "Phone Number")._

The secondary text or shape necessarily **needs to be to the right of the text** for this to work. Also, both elements should have **no more than 20 pixels** of distance between them (see the "Further Reading" below).

A symbol can look a bit messy because of the options in the Overrides section. If you don't want an element inside it to be able to be overridden, just **lock or hide this layer** and it won't appear in the list.

Just select "None" from the Overrides section to hide a nested symbol. Of course, it will only be invisible in that particular instance.

There's one way to quickly make a text element disappear in an instance, by using overrides. To do this, just set the text value to a blank space, pressing the space bar and the return key in the Overrides options.

If you have bitmap images inside a symbol, they can be changed by others using the options in the Overrides section. It's also possible to recover the original image (the one that forms part of the editable symbol) by choosing "Remove image override" -- just right-click over the image box next to "Choose Image" in the Inspector.

  * "[Hacking the Button in Sketch](https://medium.com/sketch-app-sources/hacking-the-button-in-sketch-5cbce8526b3f)," [Aleksandr Pasevin](https://medium.com/sketch-app-sources/hacking-the-button-in-sketch-5cbce8526b3f)  
Presents a simple hack to keep an icon to the left of the text (instead of to the right, which is the normal behavior), in just a couple of simple steps.
  * "[Adaptive Text Elements](https://medium.com/@yarontm/adaptive-text-elements-in-sketch-fe5d2a36c3d5)," [Yaron Tamuz](https://twitter.com/YaronTm)  
Explains how to use hidden elements as text separators to avoid their overlapping when the values change.
  * "[This Is, Without a doubt, the Coolest Sketch Technique You'll See All Day](https://medium.com/ux-power-tools/this-is-without-a-doubt-the-coolest-sketch-technique-youll-see-all-day-ddefa65ea959)," [Jon Moore](https://twitter.com/thejmoore)  
Explains how to save time using nested symbols, customizing them to your needs. The article also includes interesting techniques from other designers.
  * "[Creating a Button System With Nested Symbols in Sketch App](https://www.youtube.com/watch?v=_bjqVF7Fvg4)" (video), [Pablo Stanley](https://twitter.com/pablostanley)  
Takes you through the steps that you need to perform to create a button system, using many of the things we've learned so far.

One good thing about Sketch is that when it falls short of a feature, there's usually a plugin to make up for it. And some of them work especially well with symbols, making them even more powerful! Some of these plugins have been mentioned, but in case you missed any of them, here's a list with some additions.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/04/plugins-780w-opt.png)[50](https://www.smashingmagazine.com/2017/04/symbols-sketch/?utm_campaign=coschedule&utm_source=twitter&utm_medium=smashingmag)

> _Sketch Runner lets you quickly insert symbols by navigating a list, and it also shows a preview in the right panel. (View large version)_

Among its many other features, the [Sketch Runner](http://sketchrunner.com/) plugin will help you easily insert symbols in a document using just a combination of keys. The "go to" option is very useful for jumping right to a particular symbol -- very useful if your project has a lot of them and if it's difficult to find symbols using other means.

If you are working with a team, [InVision Craft Library](https://support.invisionapp.com/hc/en-us/articles/208434046-Craft-Introduction-to-the-Library-plugin) will make it easy to create a shared library with assets that everybody can use, allowing you to sync changes when you need to update a symbol, so that you are always sure you're using the symbols's latest version.

[Automate](https://github.com/ashung/automate-sketch) is very powerful and will likely make your work more efficient. Options for managing symbols include ones to remove unused symbols, to select all instances of a symbol, and much more.

[Symbol Instance Renamer](https://github.com/sonburn/symbol-instance-renamer) renames all instances to match the name of their master symbols.

With [Symbol Organizer](https://github.com/sonburn/symbol-organizer), organize your symbols page alphabetically (including the layers list) and into separate groups determined by your symbol names.

[Auto Layout](https://animaapp.github.io/Auto-Layout/) integrates seamlessly in Sketch and enables defining and viewing different iPhone and iPad sizes including portrait and landscape. It also supports more advanced features, such as stacks (a special type of group that defines the layouts of its child layers), and presets for both Android and iOS. Look at their "[Examples" page](https://animaapp.github.io/docs/v1/guide/13-examples.html) for more information.

**Note:** These are only some of the plugins that I think might be most helpful to you, but there are many others. To know more, just visit Sketch's [official plugin page](https://www.sketchapp.com/extensions/plugins/) or the [Sketch App Sources](https://www.sketchappsources.com/plugins.html) website regularly.

Sketch symbols are constantly evolving, so we can expect further improvements that will make them even more valuable and relevant. However, if I had to name just one thing that I would like them to have, that would be the possibility to have shared symbols' libraries, something like [Figma is doing](https://medium.com/figma-design/team-libraries-in-figma-409fa5e20f7). This could be extremely useful, especially for team work, when several designers working on the same project need to pick elements from a primary, always up-to-date document stored in the cloud.

(**Note:** Regarding this feature, I'm aware that Sketch's team is working on it, so hopefully we'll see it soon. The [more open format in version 43](https://twitter.com/NunoMRocha/status/847196484646916097) is probably laying the groundwork for this feature. In any case, I'm looking forward to it, because this could be a game-changer in many designer workflows.)

Truth be told, there are currently some plugins that help you accomplish more or less the same behavior mentioned above, but I always find it more reliable when they are made a part of Sketch's core functionality -- which ensures that the feature will keep working when the software is updated to the next version.

I'm aware that there are many more techniques and tricks. The way one works tends to be kind of personal sometimes, and there's no single right way to do something. Here, I've shared the techniques that I think are reliable, interesting and don't require much hacking. That's why some techniques were left out of this article.

I hope this was a useful read! If it was, then symbols will probably become the backbone of your designs, and you'll use them quite often. Feel free to share your thoughts and other tips and tricks in the comments below. You can also always [reach me on Twitter](http://www.twitter.com/millonestarde) if you need help!

_(mb, al)_
