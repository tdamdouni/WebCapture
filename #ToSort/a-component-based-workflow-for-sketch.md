# A Component-based Workflow for Sketch

_Captured: 2017-04-20 at 13:22 from [medium.com](https://medium.com/goabstract/a-component-based-workflow-for-sketch-6d3556b18d4c)_

![](https://cdn-images-1.medium.com/max/2000/1*HKjFVnwFH9elMseRWPv_BA.png)

## The way we design is changing, and so are our tools.

_This article was originally posted on the __[Abstract blog_](https://www.abstractapp.com/blog/)_._

Give people a tool, and they'll find different ways to put it to use. No two designers work the same way, but I'm predicting that will change over the next couple of years. Modern digital design grew out of hacking photo editors to draw user interfaces, losing track of work inside systems designed not to lose work, and an endless cycle of recreating existing screens when things get lost in translation…

Over the past decade, designers began to re-evaluate their approach and gravitated toward a component-based workflow. Photoshop introduced Smart Objects (being able to "place" other Photoshop files in a PSD). This new feature allowed designers to share a centralized version of a component, without worrying about having duplicates of that component across their files. Sadly, this never really turned into a workflow across design teams -- it was more of an exception than a rule.

When Sketch introduced symbols, the value of components became more clear. Despite being constrained to a single file, symbols make components extremely easy: create a component, and then reuse it infinitely throughout the file across artboards and pages. Initially static, symbols soon became a more robust feature with responsive resizing and the ability to overwrite values. I'm convinced symbols will have more powerful customization options in the future.

The real breakthrough came when Sketch enabled nesting symbols inside of other symbols. Even as a single designer, there is tremendous value in properly defining, naming, and structuring symbols. Coincidentally, this is how developers structure components as well: starting at the bottom where they define things at a micro level, all the way up to entire screens on a macro level.

One of _Abstract_'s strengths is providing a way for designers to version and manage their work. Abstract tracks changes made to any component within a Sketch file, allowing you and your team to compare different versions at the component level. This means that the more symbols in a Sketch file, the less likely you (or any of your colleagues) are to run into any conflicts. With Abstract, editing an icon that's used on every single layer shouldn't cause any conflicts with others who are working on the same file. And if a conflict happens to arise, Abstract handles this situation gracefully.

As an example, here's how I structure the Sketch files we use for designing Abstract. Many of my favorite design teams use similar workflows, and it seems to scale well no matter how big/small the team.

Every project starts off with defining a color palette. Brand colors, text colors, UI colors, colors for different types of actions… From that point on, it's generally not a good idea to use a color that isn't part of the palette, unless there's a really, really good reason (which means it should probably go into the palette anyway).

Second on the list is typography. Make a list of font sizes needed in the project. The shorter the list, the easier it'll be to maintain. As with the colors, there generally isn't any need to deviate from this list.

Adding some modifiers to the text styles takes this list one step further (color, font weight, text transformations…), but this also either makes the list hard to scan by adding all the different permutations, or will force constant customization to items on the list. (This is an area where I feel Sketch can and will improve over time. A simple alignment overwrite shouldn't break the connection with the defined text style.)

### Components

Here's where things get really exciting. Embedding symbols inside of other symbols, creates levels and levels of components easy to maintain and keep up-to-date.

![](https://cdn-images-1.medium.com/max/800/1*DdMZh80rxSN8SQG2QFZxqg.png)

#### LEVEL 1: Foundation

Level 1 symbols don't include any other symbols. They're the lowest level in our stack of components.

  * **Iconography**: Dark, light, and tinted variants of our icon set, with slicing set up in a way developers can easily open the Sketch file and grab the assets they need
  * **Avatars**: A set of 8 avatars we use throughout the app. They're imperfect photos from a diverse set of people.
![](https://cdn-images-1.medium.com/max/800/1*ddw_YKDIHDb623T8oGq-jA.png)

#### LEVEL 2: Lower-level blocks

Level 2 symbols combine primitives and level 1 symbols.

  * **Form elements**: Buttons, inputs, checkboxes, radio controls…
  * **Cells**: People, comments, commits, files, pages, artboards…
  * **Subnavigation**: Headers with optional actions or icons
  * **Banners**: Combines text, icons and buttons
![](https://cdn-images-1.medium.com/max/800/1*aksom80FKIHpju4DM5xnnw.png)

#### LEVEL 3: Mid-level blocks

Level 3 symbols combine symbols from level 2 and level 1. These are more advanced symbols, which usually end up being used in the actual design.

  * **Sidebars**: Lists of cells, might serve as navigation
  * **Main content areas**: Everything from a grid of projects to a commit detail including actions, title, description, previews and comments
  * **App headers**: Wayfinders, helping people know where they are inside the app, mix of text labels and icons
  * **Modals**: Actions, action confirmations, full flows…

I'll typically group Level 3 symbols on a page so I can quickly compare them for consistency.

![](https://cdn-images-1.medium.com/max/800/1*lWySOkj9JGbKrBWIRgfygg.png)

#### LEVEL 4: Compositions

Having such an expansive collection of components, the artboards holding the actual designs usually don't contain more than a handful of symbols. The first page in my Sketch file holds all the key screens of our app, while other pages are dedicated to flows including all the possible edge cases.

### So how will design change?

Design and engineering workflows are slowly creeping towards each other. On the design end, drawing tools like Sketch build new and more powerful functionality with each update which, when combined with Abstract, creates a solid, predictable, and reliable workflow. On the engineering side, there are new developments building better components for a variety of platforms. Both sides are standardizing similar processes, and this excites me.

Standardization, combined with extensive new tools, and a shared vocabulary, elevates the design process to the level our engineering counterparts have been operating on for decades. Throw Abstract in the mix, and suddenly everyone on a team has access to a rich history of why things are the way they are, the decisions that led to the current state of the work, and a way to instantly start contributing in a meaningful way.

Building high-quality products is a team effort, and all of us here at Abstract are excited to play a critical role in evolving this process.

_Abstract is currently in Private Alpha. We are working toward a Public Beta in late Q2. Feedback from our testers has been incredibly helpful as we've been refining the flows and improving the overall experience. More than ever, we believe now is the time for designers to have the proper infrastructure to highlight the value of design. New batches of invites go out each week. Thank you for your support and encouragement. We look forward to doing amazing things together._

_If you haven't signed up for the Private Alpha waitlist, __[you can do so here_](https://www.abstractapp.com/)_. And if you're interested in helping us redesign the design process, we are looking for amazing people with a variety of experiences, perspectives, and skills. __[Check out our open positions and apply now!_](https://www.abstractapp.com/careers/)
