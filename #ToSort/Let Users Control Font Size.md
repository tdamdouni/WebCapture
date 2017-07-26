# Let Users Control Font Size

_Captured: 2016-10-23 at 12:32 from [www.nngroup.com](https://www.nngroup.com/articles/let-users-control-font-size/)_

by [Jakob Nielsen](/articles/author/jakob-nielsen/) on August 19, 2002

**Summary:** Tiny text tyrannizes users by dramatically reducing task throughput. IE4 had a great UI that let users easily change font sizes; let's get this design back in the next generation of browsers.

  
  
Sometimes technological progress backfires, and the "better" technology turns
out to be worse for users. The Web is no stranger to this problem, and has
experienced many innovations that would have been best avoided. Examples
include frames, changing the color of browser scrollbars, and scrolling text.

Another example of harmful Web technology comes with the increasing use of [
style sheets](http://www.nngroup.com/articles/effective-use-of-style-sheets/),
which let web designers specify the exact size of text down to the pixel.
Unfortunately, many designers are using this ability, leading to ** reduced
readability of an increasing number of websites**.

##  The State of Font Control

I'm hereby launching a campaign to get Microsoft to ** make user preferences
override ** any fixed font size specification in Web designs.

It may be okay for the browser to initially render the page with the
designer's text size, but users should be able to easily enlarge text, no
matter what the style sheet says. After all, it's my screen, my computer, and
my software, and they should do what I say.

Granted, some web browsers have a geeky feature that lets users specify their
own style sheets. Fine for experts, but 99% of users simply want to make text
bigger if it's too small to read. The Mac-only [ iCab
browser](http://www.icab.de) gives users this simple control; let's make
Internet Explorer equally friendly to users' needs.

So, why is so much website text so hard to read in the first place? Two
theories:

  * Most web designers are young, and so have perfect vision. Tiny text doesn't bother them as much as it bothers people on the other side of 40. Designers also tend to own expensive, high-quality monitors that are easier on the eyes.
  * While creating a website, designers don't actually _ read _ the information on the pages. They simply glance at the text to make sure it looks great. In fact, many designs are approved with "lorem ipsum" standing in the place of real copy. When you don't have to read the words, it doesn't matter that the characters are small.

Because so many sites have made bad decisions regarding font size, users
commonly need to change it. Early IE versions supported this need, offering
users two standard toolbar buttons: one that made text bigger, and the other
that made it smaller. That's the way things should be.

_Mr. Gates, please give us back the good design you shipped in IE4 for the
Mac. _

##  Simplifying Browser Font Control

Unfortunately, recent versions of IE have eliminated IE4's good design,
replacing it with an approach that has two serious usability problems:

  * **The text size button is no longer visible by default**. Only the minuscule percentage of users who customize their toolbars will get this highly useful button. Most users see instead the default toolbar, which is polluted with buttons that have much less utility. Because the feature is hidden, few users realize that their browser can change text size.
  * **Separate buttons no longer exist ** for text-bigger and text-smaller. If users can find it at all, they'll get a single button to control both directions of text change.

For those few experienced users who do prevail and restore the missing button
to their customized toolbar, actually changing the text size in IE6 requires
several steps:

  1. Acquire the button by moving the mouse pointer over it. Since buttons are reasonably big in IE, this step is fairly quick according to [ Fitts's Law](http://www.asktog.com/columns/022DesignedToGiveFitts.html).
  2. Press down the mouse button.
  3. This causes a pull-down menu to appear, with five possible font sizes. Scan this menu, making a mental note of which font size is currently selected.
  4. Mentally compute which new font size you want. This is typically one size bigger (or smaller) than the current selection.
  5. While you continue to press the mouse button, move the pointer down the menu until it points to the desired new font size.
  6. Let go of the mouse button.

Compare this awkward, six-step process with the interaction technique required
by a design that includes separate buttons for "make text larger" and "make
text smaller":

  1. Click the desired button.

Of course, I am cheating a little: You would still have the initial step of
deciding whether you want the text larger or smaller, thus determining which
button you'd click. Still, since the entire change-font-size procedure is
triggered by your annoyance at trying to read unpleasantly sized text, you
already _ know _ that you want bigger (or smaller) text by the time you decide
to change the size. (The average user doesn't have a mental model of a single
"change size" command that is parameterized with the desired direction of
change; the user's model includes two actions: "bigger" and "smaller." How the
code is implemented is irrelevant for the user illusion which should be
designed to match the users' mental model.)

The two-button approach frees users from the cognitive overhead of calculating
how big they want the text to be. _ Just make it bigger. _ Users don't want to
specify exactly _ how big. _ They can easily keep clicking the "bigger" button
if the initial click doesn't make the text big enough.

Usability is enhanced by single action buttons that move along a uni-
dimensional axis in simple steps, as long as each step's result is immediately
clear after each click. That's also why the Back button is so precious to
users, and why it's used much more frequently than history list navigation.

##  Improving Future Browsers

Reverting to IE4's design for the Mac would be a great step forward for font
size usability. Still, we can do better.

Instead of having users manually change the text size every time they come
across a user-hostile design, let's take advantage of the Internet and track
font size preferences: Every time your browser loaded a page from a new
website, it would first check a database for information about your predicted
font size preference:

  * If it's a site you had visited before, a database on your local machine would keep a record of whether you had clicked the text-larger or text-smaller buttons during your previous visits. If so, it would automatically adjust the text accordingly.
  * If this were your first visit to the site, your browser would contact a central database for information about the actions of users similar to you who'd visited the site. It would then apply these users' average adjustment to the first page you see from the site. If you make any additional changes, your local database would note a revised preference and log the modification with the central database.

To expedite response time, your browser might pre-fetch the preference
settings for all websites that the current page linked to before you even
clicked a link.

The central database itself would be a straightforward case of collaborative
filtering, since it would be easy to find other users with the same text-size
preferences. For any given web page, most users would either leave it alone or
request text that's one or two sizes larger or smaller. Because a total of
five options would account for the vast majority of users, font size
preferences would be much easier to model than, say, taste in books or films.

Auto-adjusting font sizes based on collaborative filtering is a simple example
of the benefits that could accrue from more ** network-aware browsers**. It
would also be possible to auto-repair many broken links, auto-remove annoying
ads or pop-ups, and make many other improvements to individual users'
experience based on feedback from prior site visitors.

We must stop thinking of browsers as trivial pieces of free software that aim
at nothing more than rendering web page pictures on the screen. We need user-
supportive environments that facilitate navigation and protect users from the
excesses of bad websites.

##  Readability Guidelines for Websites

We can't wait for Microsoft to ship a good browser, though that has to be the
ultimate solution to the font size problem. For now, websites can increase
readability by following these guidelines:

  * **Do not use absolute font sizes ** in your style sheets. Code font sizes in relative terms, typically using percentages such as 120% for big text and 90% for small text.
  * **Make your default font size reasonably big ** (at least 10 point) so that very few users have to resort to manual overrides.
  * **If your site targets [ senior citizens](http://www.nngroup.com/articles/usability-for-senior-citizens/)**, use bigger default font sizes (at least 12 point).
  * **If possible, avoid text that's embedded within a graphic**, since style sheets and font size buttons don't have any effect on graphics. If you must use pictures of text, make sure the font size is especially large (at least 12 point) and that you use high-contrast colors.
  * **Consider adding a button that loads an alternate style sheet ** with really big font sizes if most of your site's visitors are senior citizens or [ low-vision users](http://www.nngroup.com/topic/accessibility/). Few users know how to find or use the built-in font size feature in current browsers, and adding such a button within your pages will help users easily increase text size. However, because every extra feature takes away from the rest of the page, I don't recommend such a button for mainstream websites.
  * **Maximize the color contrast ** between the text and the background (and do not use busy or watermarked background patterns). Despite the fact that low-contrast text further reduces readability, the Web is plagued by gray text these days.
