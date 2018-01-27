# Become 10,000 Times More Productive With Intentional Programming

_Captured: 2017-10-17 at 15:20 from [dzone.com](https://dzone.com/articles/become-10000-times-more-productive-with-intentiona?edition=332507&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=agile%202017-10-17)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

Intentional programming is not a new invention. In fact, it was invented a couple of decades ago by Microsoft's Charles Simonyi around Y2K. It is based on the idea that the developer has an "intention to solve some specific problem, and the computer creates a solution for that problem." Read the Wikipedia article about the idea [here](https://en.wikipedia.org/wiki/Intentional_programming). The idea is based on the concept that most problems have a generic solution, which, if abstracted, allows the computer to create code to solve the problem by itself, on your behalf. Hence, the computer becomes the system developer, and you simply feed it your intentions.

A primary example of such an idea is CRUD apps. CRUD, of course, implies Create, Read, Update, and Delete -- and it is estimated that approximately 80% of all apps you could possibly create need to solve this problem in some way. Hence, if you can create a generalized solution for CRUD, which could be reused in all possible CRUD scenarios, you could simply declare which fields you want to gather, and the computer could generate your app on your behalf.

I have developed such a solution. It's called [Camphora Five](https://github.com/polterguy/camphora-five). Arguably, it allows any human being to create software using the paradigm of "anti-programming." Instead of allowing the user to create the code that becomes the system, they simply declare the fields and their types, and the computer does the rest. Below is a screenshot of such an app.

![An address book application created with intentional programming](https://dzone.com/storage/temp/6710478-address-book-example.png)

> _An address book application created with intentional programming_

You can try the app yourself [here](https://home.gaiasoul.com/address-book).

The above web application was actually created in 36 seconds. If you want to see me creating it, you can view the video on [this link](https://gaiasoul.com/2017/09/26/become-10000-times-more-productive-as-a-software-developer/). If you multiply 36 seconds by 10,000, you get an end result of exactly 100 hours. Thus, we can guess that the average system developer would need roughly 100 hours to create something similar by coding the solution himself -- hence, the 10,000 times more productive claim.

## Features of the Address Book Example

The app features never-ending scrolling to feed the grid with more items. You can sort both ascending and descending. You can search and filter for items, both generically and on specific columns. You can edit, create, view, and delete items. In addition, it allows you to declare the most common types of columns, such as checkbox columns, single line textbox columns, multiline text area columns, radio button columns, and select dropdown lists. The latter allows you to select a value from a pre-defined static collection of values.

Arguably, these are 95% of all possible features you could possibly expect from most CRUD-based apps. As an additional bonus, it also features hashtagging and Markdown on multiline text area columns, allowing you to apply some basic formatting and categorization to your items if they contain a multiline text area column, and even create columns containing images and/or HTML if you wish.

It also stores its records in a MySQL database. And it allows for import and export to and from Excel files (CSV) -- though it follows the CSV RFC, so you must make sure you import/export your items to and from Excel/numbers using the CSV RFC standard. Use double quotes to wrap multiline values and values containing commas to apply the CSV RFC.

If you believe that the above is an example of a "generalized solution" for CRUD, and you believe that to create something similar in C# or Java, for example, would require 100 hours of work - then this implies that you become 10,000 times more productive, whenever you want to create any type of CRUD app. The cost for your employer to create such an app, would hence be reduced by 99.99%. And a solution which you'd normally have to charge $100,000 for, could, now, be implemented for $10.

**Effectively resulting in, if give me a cup of coffee, I'll create a $100,000 web app for you!**

Now, if somebody could just help me figure out how to cure the world's developers of the "not invented here syndrome," I think we might actually create some change here!

### Getting Started

To test out Camphora Five for yourselves, [first, install Phosphorus Five](https://github.com/polterguy/phosphorusfive/releases). Then visit the "Bazar" and choose to install "Camphora Five." Also notice that _it's still in BETA_, and there are some quirks in it.

And of course, everything is Free Software and Open Source!

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

Opinions expressed by DZone contributors are their own.
