# Developing Inspirato’s Search Tool

_Captured: 2015-10-30 at 12:11 from [medium.com](https://medium.com/bpxl-craft/developing-a-new-way-to-search-cf1a46d382df#.pbwfq772n)_

During the discovery process for the project, the Inspirato team kept emphasizing how their members were booking vacation mostly over the phone using broad statements about the type of vacation experience they were looking for. It became clear that we needed to offer something more than your standard search paradigm.

Natural Language Search (NLS) was proposed to offer something very different from traditional search and yet very similar to the way Inspirato members were thinking about and booking their vacations.

Designed and developed by Black Pixel for Inspirato, Natural Language Search allows users to interactively create sentences about the kind of travel experience they are looking for.

In a world where the typical search is a text field associated with a bunch of checkboxes, NLS stands out. You can formulate a search as you would naturally talk. It just makes sense. It just works. By tapping and scrolling you can create rich natural sentences.

> _Example of NLS sentences_

This post will take you behind the scenes for a deeper look at the way NLS works.

#### Some History

When you see a finished application it is sometimes difficult to imagine the amount of work that went into the implementation of certain features. Some may seem daunting, others dead simple. The truth is that no nice, polished feature is ever the result of just a few hours of work. Most polished features, even if they look simple, are often the end result of hours of hard work and many iterations. NLS is one such feature. It was not created in a few days. In fact it took the better part of three months to come to the level of polish you see today.

Of course we had a visual prototype working within a few days, but as the most experienced software engineers know, there is a wide gap between a working visual prototype and a fully functioning, fully refined feature.

The visual design started on the iPad knowing that we would need to implement NLS on the iPhone at a later stage. At the time the iPhone 6 and iPhone 6 Plus had not been introduced yet.

#### What's an NLS Sentence?

Before we look at the data model and visual implementation, let's start with a short explanation of NLS sentences.

When users interact with NLS they are usually awed by the nice visual interaction and animation. It feels natural and users typically find it delightful. The search sentence sounds so natural they don't think about it. Let's have a closer look at how the search sentence is built up.

It always starts the same way with, "I want to …" This group is then followed by an action verb and options for a location and a time. Changing the action verb impacts what should come next, such as the prepositions:

  * Vacation on the beach anytime.
  * Vacation in a city anytime.
  * Vacation anywhere (no preposition) anytime.
  * Jaunt to the mountains.
  * Daydream in the countryside.

Changing the action also affects the possible content of the sentence:

  * The list of locations for a "Jaunt" is changing every week based on current "Jaunt" offerings.
  * When you daydream, you don't specify a time.
  * When the selected location is a geographic region, the sentence also displays the associated destinations for that region.

The list of locations shown to the user offers a variety of choices:

  * Anywhere, which gives access to all destinations.
  * A region (the Bahamas, the South), which gives access to specific destinations.
  * A vacation style (city, mountains, beach).
  * A typed location, which is a standard text search.

The way these words relate to actual residences or destinations can be rather complex.

The sentence itself allows you to look for residences to plan your next vacation so it has to translate into a list of residences or destinations.

#### Diving into the NLS Architecture

**Model and Controllers and Views**

> _The overall NLS architecture showing the main components and their relationships. Some elements are omitted for the sake of clarity._

The NLS architecture relies on two major components:

  * The Sentence Controller, which is responsible for ensuring the sentence is always syntactically and grammatically correct no matter what words are selected.
  * The Sentence View Controller, which is responsible for the display and layout of the sentence, as well as handling all user interactions.

The delegation relation that exists between both ensures that all changes made to the Sentence Controller (like when a user selects a previous search sentence in the history) are properly reflected visually.

**The Sentence Controller**

At the heart of sentence management is the sentence controller. This controller:

  * Manages the prepositions of each collection of words to ensure a consistent grammatical sentence.
  * Enforces the rules about sentence creation such as "daydream does not allow time selection."
  * Updates the list of words (action, location, sub location, and time) based on the currently selected words.
  * Updates the sentence model with the current word selection.
  * Initializes the current selection based on a given sentence or initial state.
  * Communicates changes made to the sentence back to the view.

The list of available residences and destinations, which is regularly retrieved from the Inspirato server, determines which locations can be shown to the user.

The sentence can be changed in several ways:

  * A user can edit the sentence visually.
  * A user can pick a previous sentence from history of past searches.
  * A user can receive a push notification with a specific sentence, such as for new "Jaunt" offerings.
  * A residence or destination may be removed from the Inspirato offering temporarily or permanently.

All of these cases have to be handled gracefully by the sentence controller to ensure the sentence is always correct and all residences or destinations shown are current.

**Core Data**

Core Data is used to model all the instances making up this model. All location words (region, vacation style, destinations, residences) are related to actual destinations or residences the user can see. The relationship model of core data makes retrieving this information very easy.

One complexity of the model is figuring out which words to display. For example, when the user selects the action "Jaunt," we need to show destinations that match several criteria:

  1. The destinations shown need to contain residences that are "Jaunt" residences,
  2. But should not show residences that are temporarily off the market (for maintenance, for example),
  3. And should correspond to the selected location word.

This sometimes results in rather complex fetch requests made of up to three levels of subquery.

**The Sentence View Controller**

Without the sentence view controller there would be no NLS as we know it. All the work done to layout the NLS sentence and manage user interactions goes through the sentence view controller.

Whenever a list expands or collapses it communicates its state to the sentence view controller, which can:

  * Relay the information to the sentence controller (to change the sentence).
  * Layout the views dynamically.

#### A Deeper Look at the Visual Design Implementation

From the beginning, Inspirato was going to be both an iPad and iPhone application. All decisions made while designing NLS for the iPad were done so knowing that the iPhone would come next.

**The Root of NLS Design: The iPad**

There are several moving pieces in the iPad visuals. Let's start with the default NLS sentence which greets the user the first time she uses the application. When she taps on the "anywhere" word to choose a new destination the following happens simultaneously:

  1. The list of locations expands vertically with all destinations moving into place.
  2. The list of locations expands horizontally so as to accommodate all destinations using a single line layout for each.
  3. The horizontal expansion of the list pushes the rest of the sentence to the side or another line.

The overall animation is very smooth with everything moving into place nicely and naturally. This is best illustrated with a video.

> _NLS on the iPad in slow motion showing the details of the animations_

**The Sentence Layout**

Laying out the sentence's words is the easiest part. The sentence is composed of up to 11 different views from the opening statement to the period at the end.

The views are not laid out individually; they are grouped logically to ensure a pleasant and natural layout. For example, the location word can display a region, in which case a disclosure indicator will be displayed. These two views (disclosure indicator and destination) are grouped together and laid out as one. Similarly, the period is attached to whatever word precedes it so it doesn't end up alone on a line.

The algorithm to layout the views is relatively straightforward once you know the width of all the views you want to layout. The algorithm takes the array of widths to layout along with the total available width and distributes the views on different lines. The constraints of the different views are then updated to position the views horizontally and vertically.

**The Lists of Words**

The lists of words are central to the sentence creation process. Using these lists, the user can select different words to make up the complete search sentence.

Each list uses a _UITableView_ which will:

  * Change its width according to the current selection, or, when a list is expanded, accommodate the widest entry in that list. Each row in the list has the same row height.
  * Change its height dynamically from a single row height to the full height of the iPad screen when the list expands to reveal its words.
  * Animate its cells to their final position during an expansion or a collapse by applying a 2D transform to each cell.

In order to make this work smoothly on the iPad we use several tricks:

  * We pre-compute the maximum width of all cells in their non-selected state using a template cell set up with autolayout. This ensures a very fast computation of the table view width when it expands to reveal its content.
  * A width constraint is set on the table view and updated to dynamically change its width. The sentence view controller can read this updated width for the layout computation.

The principles are easy enough to understand. The devil is really in the details:

  * The sequence of animations is important and often non-commutative, especially with auto layout: performing update A before update B does not yield the same results as proceeding the other way around.
  * The timing of animations is tricky: you need to always end up in a consistent state at the end of each animation, both for the list and the sentence.

Let's look at the details of what happens during the expansion of a list.

**Revealing a List's Content**

The video above shows a slow motion video of a list expansion. It was created by slowing down the animations in code. The picture below describes the various steps of this animation from start to finish.

To synchronize those steps we make use of the dispatch_group_enter dispatch_group_leave dispatch_group_notify methods. This ensures that we get properly notified once all animations have completed without imposing an a priori time limit. During this completion phase we perform several tasks such as re-enabling scrolling for the table view and telling our delegate that the expansion is completed.

Getting there was not straightforward. Far from it. It took a lot of experimentation, a lot of broken animations, and a lot of very intensive, relentless, ruthless testing. Working with a great QA team helped tremendously. NLS would not have reached the level it is at right now without this extremely tight and constant back-and-forth between engineering and QA. And quite honestly sometimes I got scared of submitting changes knowing that QA would break the whole thing apart without mercy. But this is what it takes to make great software.

**What About the iPhone?**

Implementing NLS for the iPhone was relatively straightforward with minimal changes to the original algorithm and design.

> _Example of NLS layout on the iPhone_

> _Explicit layout and expansion on the iPhone_

If you look closely at the iPhone design you will notice:

  * Each of the 11 views used to represent the sentence lives on a different line. This was achieved by telling the layout algorithm that each view had the width at the iPhone screen (minus some margins). Without any changes, the algorithm positioned each view on different lines.
  * Each list has rows of varying height.

So in essence the design went from a "varying width/fixed table row height" on the iPad to a "fixed width/variable table row height" on the iPhone.

On iPhone, instead of pre-computing the width of all cells, we pre-computed their height for the non-selected state using the same template cell and autolayout. This ensured we could very easily provide each row height upon the list expansion.

Apart from these changes the rest of the code remains almost identical for the sentence layout and the list animation.

#### Pushing the Limits

The design team at Black Pixel loves to push the limits of what can be done to delight our users with great experiences. When I first saw the design for NLS, I immediately noticed its appeal. I could visualize the animations and interactions. I was loving it. And as a developer, I was terrified because I knew it was very different from any interactions I had ever seen. I had just joined Black Pixel and, quite frankly, I did not know whether I would be up to the challenge. And then I was asked to work on it … and the adventure started. The fear is _mostly_ gone.

The NLS feature you see today is the result of an intense and continuous collaboration with both the design and QA teams. I am grateful to both teams for pushing my limits and allowing me to grow and perfect my craft. Being part of this project and having the opportunity to work as part of Black Pixel's great integrated multidisciplinary team has been a real privilege.

If you want to see the app in action you can [download the Inspirato app](https://itunes.apple.com/us/app/inspirato/id970207197?mt=8) from the App Store.
