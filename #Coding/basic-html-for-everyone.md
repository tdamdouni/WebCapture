# Basic HTML for Everyone

_Captured: 2018-02-02 at 16:53 from [dzone.com](https://dzone.com/articles/basic-html-for-everyone?edition=359105&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=web%20dev%202018-02-01)_

There are so many editors and plugins available that knowing the basics of HTML is no longer required to create a site.

![BuildThis - HTML](https://dzone.com/storage/temp/7974739-html-codes.jpg)

> _BuildThis - HTML_

The problem with this is that if you don't know a few basics, you can easily get into real trouble and have to hire a pricey developer to fix what may be a minor problem. Not only that, but creating changes to your blog such as adding a custom text widget requires a little knowledge.

And if your content layout doesn't look right, HTML knowledge can get you back on track.

Here are some very basic HTML pointers for everyone.

### Word of Warning Before Writing HTML

I want you to get comfortable using these tags, but you should always remember that if you leave out a portion of the tag, you can cause serious problems.

Each tag has an end and a beginning, and leaving one of those out tells the computer that the tag is still open…and all the following code will be included in that tag.

In addition, please type it out. If you copy and paste what I've written, you may get problems when the site interprets your code.

## Links: The <a> Tag

One of the most important things to know is how to make links. The latest update of WordPress is experiencing some issues with some "no follow" plugins, so while you are waiting for a compliant plugin, you'll need to know how to set up a nofollow link for your sponsored and product review posts.

The tag looks like this:
    
    
    <a href="http://www.websiteyouarelinking.com/" target="_blank" rel="nofollow">Website Name</a>

In the "a" is the tag, "href" tells the browser where to take the visitor once she clicks the link. The target "_blank" tells the browser to open that link in a new tab - very important so that visitors don't leave your website.

Next, we have the all-important "nofollow" link that you need to ensure you don't get penalized by Google for compensated posts (if you are writing a post that is not compensated, you can leave out `rel="nofollow"` to give the link a boost on Google). Next comes the title - make it accurate and SEO-friendly. Finally, "</a>" closes this tag.

## Images: The <img> Tag

Sometimes you'll want to create text widgets that include images or linked images.

This is the code:

Pulling in a single image:
    
    
    <img alt="Gluten Free Brownies" src="http://mom-blog.com/wp-content/uploads/2014/04/2014016_brownies.jpg" width="490" height="293" />

Notice that this is a SINGLE tag, but it ends with `/>` to close the tag. In this tag, you'll see `alt`. This is what you fill out after you load your image and is necessary for visitors who are visually impaired (make sure you use it to denote what the photo is, and not what you want your SEO to be). `src` is the link to where your image is actually located. "Width" and "height" are just that - the size of your image in pixels. This is optional, and should match your actual image size, or else the image will appear warped.

Here's how to set up an image with a link:
    
    
    <a href="http://www.websiteyouarelinking.com/" target="_blank" rel="nofollow"><img alt="Gluten Free Brownies" src="http://mom-blog.com/wp-content/uploads/2014/04/2014016_brownies.jpg" width="490" height="293" /></a>

As you can see, you simply replace the text from our <a> tag example ("Website Name") with an image link and voila!

## The Paragraph Tag: <p></p>

Obviously, this tag puts your text or image in it's own paragraph with spacing above the opening <p> and after the closing </p>.

Usually, it will be styled so that there is a certain amount of space above or below it. You can easily adjust that with a bit of style right in the tag.

This is how it's done:
    
    
    <p style="width:200px; padding-right:5px; text-align:center;">Welcome to my blog!</p>

That style tag allows all kinds of sizes and options, but here are some basic ones.

  * "Width" is the actual width of that paragraph. This had created a 200 pixel width paragraph. Make sure your width is NOT bigger than your column or just leave width out to spread text to the size of the column.
  * "Padding" literally puts space around your paragraph. You can add 5 pixels of space just to the right, for example, like it's done here, if you feel your paragraph is too close to the edge on the right side. You can do the same for padding-left, padding-top, and padding-bottom. You also have the options of "padding:5px" to put 5 pixels on each and every side.
  * "Text-align" justifies your text within the paragraph. Options are center, left, right, and justify, which spreads the text out to be even on both sides.

Finally, you can use a paragraph with images and links as well but make sure your image's width fits in your column too. Note that padding is added to that width:

## The Line Break Tag: <br />

This tag gives you a one-line return without a paragraph. It can be used inside a paragraph if you want a series of lines where you have single line breaks that you select yourself (so that you can even out the lines) and still have a paragraph around it, like so:

## Styles

Now that I've shown you some styles, I'm going to quickly list a few more that are useful for creating text widgets:

  * **BOLD:** Place bolded text inside these tags: <strong>**Text goes here**</strong>
  * _ITALICS:_ Place italicized text inside these tags: <em>_Text goes here_</em>
  * _**BOLD+ITALICS:**_ Place text inside:<strong><em>**_Text goes here_**</em></strong>

## Heading Tags

For SEO purposes, you may want to use critical tags with your site's main keywords in text widgets (on your sidebar, footer, etc.) These are heading tags and Google gives more weight to them. For example, your blog's theme will usually have titles and your site's name within these tags.

These tags are:

  * <h1>Text goes here</h1>
  * <h2>Text goes here</h2>
  * <h3>Text goes here</h3>
  * <h4>Text goes here</h4>
  * <h5>Text goes here</h5>
  * <h6>Text goes here</h6>

These tags are in order of size, with <h1> being the largest. Google gives the most weight to text in <h1>, then <h2>, and so on.

Often, <h1> tags are quite large and may have a color. To eliminate that, you can enter something this:

That will give you black text (color: #000;) in a 12 pixel font (font-size: 12px;) and remove bold (font-weight:normal;). If this does not work, your site may have been coded in a more complex manner and you may simply want to select a smaller heading tag.

## Bullets

Bulleted or numbered lists are a great way to show content to your audience. But you might find "weird" or inconsistent spacing when you edit them. This is what they should look like in your text editor:

<ul> means "unordered list" - this will give you bullets (if you want to use a numbered list, simply change all the "ul" tags to "ol"). <li> means list item. There are times you'll hit a return and it will create another <ul> within your list or close your list and start a new one in the middle. It should look like some variation of the above, so if you see extra "<ul>" opening and closing tags, you can delete them.

## Try Writing Your Own

This will help you get started, but please make sure that you back up your site fully first (including themes) so you can restore if necessary.

If you get into trouble with a widget, you can just remove it to figure out where you wrote the wrong code. Finally, feel free to type as normal in your visual editor and compare what you see in the text editor to get a feel for these basics.
