# Applied Rails: Customizable Text

_Captured: 2017-05-12 at 00:36 from [dzone.com](https://dzone.com/articles/applied-rails-customizable-text?oid=twitter&utm_content=bufferd6aca&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

The other day, I was assigned the task of making a Rails application in which the user could add a set of "Terms and Conditions" in the Offer screen. These documents are typically standard, but the business guys wanted the user to be able to customize the individual clauses. It sounded oxymoronic at first, but, after remembering Scott Meyers' words, "pretty this ain't, but sometimes a programmer's just gotta do what a programmer's gotta do," I set out in earnest to figure out what could be done.

From our business analyst, I got the typical standard clauses for these types of documents. To illustrate, here is an example -- "Offer shall be valid for 45 days." My first thought was that I should identify the parts that vary and take them as input data from the user.

In many cases, the thing that varied was a number. Taking the data in the HTML form for these variables and displaying them as inserts in constant text made sense. For the example I quoted above, I would take an input field of a type number with name the "validity" and insert it as follows:

`Offer shall be valid for <%= @offer.validity %> days.`

There were only a few clauses initially. But then, their number started increasing. Also, they were being specified with more variable parts than just one, and sometimes with non-numeric parts too.

Further, in one meeting I was told that the user may enter a totally new clause that is not part of the standard set. There was no question of identifying the part of the sentence that varies. The sentence itself would be new.

I considered different ways of providing the feature, but they all seemed like overkill. Finally, I narrowed it down to a text box. I provided the user with a set of standard clauses above the box, with a note that users should copy-and-paste the clauses into the text box.

![](https://1.bp.blogspot.com/-zhFkJthShgE/WLkY0DX48xI/AAAAAAAAChc/xBKRkerihtYXE7zCIP-F74-vzF6QNPAjQCPcB/s640/customizable-text-screenshot.png)

This would not only allow them to change the variable parts but also add new sentences. The text in the text box was saved in a MySQL database, in a column type, "text." In order to display the clauses separately, I just had to split them onto a new line and print.

Our business analyst accepted this solution. Problem solved with a simple text box.
