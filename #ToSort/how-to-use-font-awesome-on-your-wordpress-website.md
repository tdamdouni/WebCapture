# How to Use Font Awesome On Your WordPress Website

_Captured: 2017-04-23 at 10:58 from [www.elegantthemes.com](https://www.elegantthemes.com/blog/tips-tricks/font-awesome-wordpress)_

![How to Use Font Awesome On Your WordPress Website](https://cdn.elegantthemes.com/blog/wp-content/uploads/2016/10/font-awesome.jpg)

Interested in a fun way to make your WordPress site's design even more appealing? Font icons let you spice up your posts, pages, or menus by including eye-catching icons. And when it comes to font icons, Font Awesome is definitely one of the biggest names out there.

If you want to add Font Awesome's huge collection of icons to your WordPress site, keep reading to learn a little more about them and two quick and easy ways to add these icons to WordPress.

## What Are Font Awesome Icons and Why Are They Beneficial?

If you're a Divi user, you're probably already familiar with font icons from the [Elegant Icon Font](https://www.elegantthemes.com/blog/resources/elegant-icon-font) that's included in Divi.

Font Awesome operates on the same principle-it's a font built with icons. Not a set of images. Why is this distinction so important? Because icon fonts like Font Awesome and Elegant Icon Font are:

  * **Vectors** - that means they look great no matter what size they're displayed at.
  * **Customizable** - you can manipulate them like any other font. Change colors, add animation, and more!
  * **Cross-browser compatible** - icon fonts should work on pretty much any browser.

Font Awesome currently offers a massive 634 different icons that you can add anywhere on your WordPress site. It's also compatible with both Divi and any other WordPress theme you're using.

## How to Add Font Awesome Icons to WordPress Manually

It's easy to manually add Font Awesome to WordPress, but if you don't want to deal with any code (even if it's simple!), you can skip to the next section for a simple plugin solution.

There are two parts to implementing Font Awesome manually. First, you need to include the Font Awesome stylesheet in your theme's header section. Then, you need to find the actual name of the icon you want to include and include it with another short code snippet. Here's how to do both of those things:

### Adding Font Awesome to Your Theme's Header Section

The first step is adding Font Awesome to your theme's header.php. This is the specific bit of code you need to add, though I'll provide a slightly different version for non-Divi themes:

`<``link` `rel``=``"stylesheet"` `href``=``"https://maxcdn.bootstrapcdn.com/font-awesome/4.6.3/css/font-awesome.min.css"` `/>`

This code brings in the Font Awesome stylesheet from Bootstrap CDN. You can also get a stylesheet [directly from Font Awesome](http://fontawesome.io/get-started/), but it doesn't make any real difference.

If you're using Divi, you can add this code by going to _Divi -> Theme Options -> Integration_. Scroll down a bit and find the _Add code to the < head > of your blog_ box. Paste the code there. It should look like this:

![font-awesome-wordpress-manually1](https://cdn.elegantthemes.com/blog/wp-content/uploads/2016/10/font-awesome-wordpress-manually1.png)

Make sure to click _Save Changes_ and then you're all finished for this part.

If you're using another theme, you'll want to use a slightly different bit of code:

Instead of the header.php, you'll want to add it to your child theme's functions.php by going to _Appearance -> Editor_:

![font-awesome-wordpress-manually2](https://cdn.elegantthemes.com/blog/wp-content/uploads/2016/10/font-awesome-wordpress-manually2.png)

Definitely make sure you're [using a child theme](https://www.elegantthemes.com/blog/resources/wordpress-child-theme-tutorial) so that your additions don't get accidently overwritten by a theme update.

### Inserting Font Awesome Icons

Once you've added the code to your theme, you're ready to start using Font Awesome icons wherever you want.

To find a full list of icons, [go to the Font Awesome website](http://fontawesome.io/icons/) and search for any icon you want. For example, if you want a "download" icon, just search for download and pick one from the list by clicking on it:

![Insert Font Awesome](https://cdn.elegantthemes.com/blog/wp-content/uploads/2016/10/font-awesome-wordpress-insert-1.png)

After you click on your desired icon, you'll see a screen showing that icon in various sizes. Around the middle of the screen, you should see a little code block:

![font-awesome-wordpress-insert-2](https://cdn.elegantthemes.com/blog/wp-content/uploads/2016/10/font-awesome-wordpress-insert-2.png)

You need to copy all the code for whichever icon you choose. Then, you can insert that code anywhere in WordPress, no matter if you're using the Divi Builder or the WordPress Editor. Just make sure you insert it in the _Text_ tab of whichever editor you're using. You can go back to the visual tab after you're finished adding icons.

Here's what that looks like using a normal text module in Divi:

![font-awesome-wordpress-insert-3](https://cdn.elegantthemes.com/blog/wp-content/uploads/2016/10/font-awesome-wordpress-insert-3.png)

Here's what that looks like on the frontend:

![font-awesome-wordpress-insert-4](https://cdn.elegantthemes.com/blog/wp-content/uploads/2016/10/font-awesome-wordpress-insert-4.png)

It's the same idea with the normal WordPress Editor. Just add the icon code in the _Text_ part of the editor:

![font-awesome-wordpress-insert-5](https://cdn.elegantthemes.com/blog/wp-content/uploads/2016/10/font-awesome-wordpress-insert-5.png)

And then you should see this when you publish the post:

![font-awesome-wordpress-insert-6](https://cdn.elegantthemes.com/blog/wp-content/uploads/2016/10/font-awesome-wordpress-insert-6.png)

### Making Font Awesome Icons Bigger

As you can see in the above examples, the icons are pretty small by default. If you need them to be bigger, all you need to do is add a tiny bit of code to the icon. For example, to make the icon twice as big, you just need to add "fa-2x" to the icon class.

That means that this:

`<``i` `class``=``"fa fa-download"` `aria-hidden``=``"true"``></``i``>`

Becomes this:

`<``i` `class``=``"fa fa-download fa-2x"` `aria-hidden``=``"true"``></``i``>`

So, when I change my earlier example to that code, my icon shows up like this instead:

![font-awesome-wordpress-insert-7](https://cdn.elegantthemes.com/blog/wp-content/uploads/2016/10/font-awesome-wordpress-insert-7.png)

Here's a list of code bits you can add to manipulate the size:

  * fa-lg - increase size by 33%
  * fa-2x - double the size
  * fa-3x - triple the size
  * fa-4x - …
  * fa-5x - …you get the point!

You can also do other cool things like use Font Awesome icons as bullet points, add animation, and more. The official Font Awesome site has a [great guide](http://fontawesome.io/examples/) on how you can manipulate font icons in different ways.

## How to Add Font Awesome Icons to WordPress With a Plugin

If you don't like the manual way, you can also get Font Awesome up and running by installing a plugin. There are a variety of plugins which offer this functionality, but one of the more popular and regularly updated options is called **Better Font Awesome Icons**.

You can try one of the other options, but I think this one is a good choice because it:

  * Is updated fairly regularly. This is important because several popular Font Awesome plugins haven't been updated in years.
  * Automatically fetches the latest set of Font Awesome icons.
  * Lets you add icons via shortcode or the same code I used in the manual example.

To get started, [install and activate the plugin](https://wordpress.org/plugins/better-font-awesome/) like you would any other.

The plugin will add a new _Better Font Awesome_ link under the _Settings_ menu in your dashboard. You don't really need to configure anything - it mainly just gives you instructions on how to use the plugin:

![better-font-awesome-1](https://cdn.elegantthemes.com/blog/wp-content/uploads/2016/10/better-font-awesome-1.png)

### Adding Icons

To add the actual icons to posts, you can either use the same method I showed you in the manual section, or you can use shortcodes. The advantage of using shortcodes is that you don't need need to switch to the "Text" tab of your editor.

The shortcode format you need to use is:

Where NAME is the name on the Font Awesome website:

![better-font-awesome-2](https://cdn.elegantthemes.com/blog/wp-content/uploads/2016/10/better-font-awesome-2.png)

You can add this shortcode in Divi modules or the regular WordPress text editor. Here's an example where I include an icon via a shortcode in a text module while using the Divi Visual Builder:

![better-font-awesome-3](https://cdn.elegantthemes.com/blog/wp-content/uploads/2016/10/better-font-awesome-3.png)

The Visual Builder renders that like this:

![better-font-awesome-4](https://cdn.elegantthemes.com/blog/wp-content/uploads/2016/10/better-font-awesome-4.png)

You can use the exact same shortcodes in the regular WordPress editor, too.

If you want to change the size of your icons via shortcode, just add a class tag with the exact size you want like this:

All the same size options from the manual examples will work with the shortcodes.

## Wrapping Up

There you go! Two different ways to add Font Awesome icons to your WordPress site. I prefer the manual method, because it's not really much more work and then you don't have to worry about a plugin potentially breaking down the road.

But if you don't want to fuss with your theme's code, the Better Font Awesome Icons plugin is a great option!

**Now it's your turn. What's your favorite way to use Font Awesome icons?**

_Article thumbnail image by tulpahn / shutterstock.com_
