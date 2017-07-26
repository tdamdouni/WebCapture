# Be More Productive When Working on iPad or iPhone – Thanks to Automation

_Captured: 2016-04-20 at 00:31 from [ulyssesapp.com](http://ulyssesapp.com/blog/2016/04/introduction-x-callback-support/)_

## A Brief Introduction to Ulysses X-Callback-Support

![Ulysses Ideas](http://ulyssesapp.com/blog/wp-content/uploads/2016/04/Scenery-iPhone-6-6s-Plus-424-19.04.16-15-32.png)

Do you often find yourself doing the same things on your iPad or iPhone over and over again? Automation apps let you run such routines automatically, with the help of so-called x-callback-urls. Ulysses now also supports x-callback, allowing you to speed up your iOS workflows.

An x-callback-url triggers a particular action within an app and follows a certain app specific scheme. Here is a simple example for a Ulysses x-callback-url:
    
    
    ulysses://x-callback-url/open-favorites
    

Can you guess what it does? On iPad or iPhone, this URL opens your Ulysses Favorites. If you're reading this on an iOS device, give it a try and tap the following link - but don't forget to get back here, ok? <ulysses://x-callback-url/open-favorites>

For taking advantage of x-callback-urls, you will need automation apps. The following are - for good reason, I think - very popular:

  * **[Launch Center Pro ($4.99)](http://geni.us/9gi)** lets you collect specific app actions for fast access. As an example, the launch center action "Message Max" would automatically open the Messages app, select Max as a recipient and prompt you for text input. 
  * **[Workflow ($2.99) ](http://geni.us/3ukS)** allows you to automate complex series of steps involving the use of different apps. If you want, you can add a button to your homescreen to run your workflow with just one tap. An example is "Cross-Post", a workflow for sharing a photo with a caption on Twitter, Facebook and Instagram at once.

Other apps worth mentioning are [Drafts ($9.99)](http://geni.us/3UUA) and [Editorial ($9.99)](http://geni.us/2OY9), which specialize in the automation of text processing.

## Ulysses Actions

Here is a list of all actions in Ulysses that can be triggered via an appropriate x-callback-url:

  * `new-sheet` to create a new sheet
  * `insert` to add text to an existing sheet
  * `attach` to create a note attachment for an existing sheet
  * `new-group` to create a new group
  * `open` to open a particular sheet or group
  * `open-group` to open a group with a particular name
  * `open-all` to open the All section of your library
  * `open-recent` to open Last 7 Days
  * `open-favorites` to open your Ulysses Favorites

For every available action you can determine certain parameters in the x-callback-url.

As an example, you can specify the group to which you want to add a new sheet, or the sheet to which you want to add a note attachment. For every sheet or group, Ulysses provides a unique identifier. Go to the library or the sheet list, respectively, swipe left on a sheet or group. Select "More", then "Share…". Now you can copy the identifier, and insert it into the x-callback-url.

For a comprehensive list of parameters available for each action, check out the [Ulysses x-callback specification](http://ulyssesapp.com/kb/x-callback-url/).

## Put into Practice: Jotting Down Sudden Inspiration with Launch Center Pro and Ulysses 

Time to give it a try! Let's assume you are a writer with an open mind for sudden inspiration, no matter where you are. Whether it is an awkward conversation on the bus or a news item read in a cafe - if you could use it for your writing, you jot it down. For collecting these snippets, you have created a subgroup "Ideas" in the group "My Personal Writing" of your Ulysses library.

Without any automation, your workflow for adding a new piece to your collection includes the following steps:

  * Open Ulysses.
  * Open the "Ideas" group. Depending on where you left Ulysses after using it for the last time, this involves a number of steps. As an example: On iPhone, you may have to end editing a sheet, then navigate to the sheet list, from there to the library and then to the "Ideas" group.
  * Create a new sheet in the "Ideas" group.

Only then you can start typing. An x-callback-url for automating these steps would look as follows:
    
    
    ulysses://x-callback-url/new-sheet?group=Ideas
    

The parameter `group` allows to specify a group by its name. If you're having more than one group of that name, the new sheet is created in the first matching group. An alternative would be to use the parameter `groupId` instead, with the group's identifier.

Now you can add the URL as an action to your Launch Center, following these steps:

  * Open Launch Center Pro.
  * Tap the little pencil top right to edit your launch actions.
  * Tap the Plus button to create a new action.
  * Name the action and insert the x-callback-url.
  * If you want, you can add an icon for that action. I imported Ulysses' app icon as a photo. You can of course do the same, here's [the icon for you to download]().
  * Tap Done. The action is now part of your Launch Center.

![L1](http://ulyssesapp.com/blog/wp-content/uploads/2016/04/L1-169x300.jpg)

![L2](http://ulyssesapp.com/blog/wp-content/uploads/2016/04/L2-169x300.jpg)

![L3](http://ulyssesapp.com/blog/wp-content/uploads/2016/04/L3-169x300.jpg)

![L4](http://ulyssesapp.com/blog/wp-content/uploads/2016/04/L4-169x300.jpg)

![L5](http://ulyssesapp.com/blog/wp-content/uploads/2016/04/L5-169x300.jpg)

![L6](http://ulyssesapp.com/blog/wp-content/uploads/2016/04/L6-169x300.jpg)

![L7](http://ulyssesapp.com/blog/wp-content/uploads/2016/04/L7-169x300.jpg)

![L8](http://ulyssesapp.com/blog/wp-content/uploads/2016/04/L8-169x300.jpg)

(Side note: All instructions in this post refer to iPhone. You can do the same things on iPad, too, albeit the app interfaces may look slightly different.)

So, whenever you would like to jot down a sudden inspiration in the future, you would just do this:

  * Open Launch Center Pro.
  * Tap the "Ulysses Ideas" action.

## Jotting Down Sudden Inspiration with Workflow and Ulysses

With Workflow, you can get to a similar result. Setting up is a little more complicated, because the app is designed to also handle workflows of a more complex kind.

Here are the steps involved:

  * Open Workflow.
  * Tap the Plus button top right to add a new workflow.
  * Tap "Actions" bottom left to select the actions that belong to the workflow.
  * From the list of actions, select "URL" and swipe right to add it to your workflow.
  * Insert the x-callback-url in the designated field.
  * Go back to Actions, select "Open URLs" and also add it to your workflow via swiping right.
  * Now tap the gear to name the new workflow and give it a proper icon. I opted for a pencil glyph on an orange background, since there was no butterfly available.
  * Finally, you can add your brand-new "Ulysses Ideas" workflow to your homescreen. For this, the Workflow app will forward you to a website. Then, just follow the designated steps.
  * "Ulysses Ideas" now appears as an icon on your homescreen. 

![w1](http://ulyssesapp.com/blog/wp-content/uploads/2016/04/w1-169x300.jpg)

![w2](http://ulyssesapp.com/blog/wp-content/uploads/2016/04/w2-169x300.jpg)

![w3](http://ulyssesapp.com/blog/wp-content/uploads/2016/04/w3-169x300.jpg)

![w5](http://ulyssesapp.com/blog/wp-content/uploads/2016/04/w5-169x300.jpg)

![w6](http://ulyssesapp.com/blog/wp-content/uploads/2016/04/w6-169x300.jpg)

![w7](http://ulyssesapp.com/blog/wp-content/uploads/2016/04/w7-169x300.jpg)

![w9](http://ulyssesapp.com/blog/wp-content/uploads/2016/04/w9-169x300.jpg)

![w10](http://ulyssesapp.com/blog/wp-content/uploads/2016/04/w10-169x300.jpg)

![w11](http://ulyssesapp.com/blog/wp-content/uploads/2016/04/w11-169x300.jpg)

Workflow also allows for sharing your creations. So, if you are interested in "Ulysses Ideas", but too busy to build it yourself, please don't hesitate to [grab it here](https://workflow.is/workflows/f74956a177264a34bc2339de0436ba7a).

When running the workflow for the very first time, you'll have to confirm it. After that, it will take you exactly one tap to open Ulysses, navigate to the Ideas group and add a new sheet.

## Coming Soon: Inspiring User Creations 

This was a simple example for an automated workflow based on a Ulysses x-callback-url. There's more what you can do with Ulysses thanks to x-callback-support and automation apps. We will be back soon, presenting some inspiring workflows created by the Ulysses community.
