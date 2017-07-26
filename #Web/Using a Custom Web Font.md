# Using a Custom Web Font

_Captured: 2015-12-09 at 12:18 from [independentpublisher.me](http://independentpublisher.me/2013/using-a-custom-web-font/)_

If you want to use a custom font-that is a font that is not included with any of the common operating systems (Windows, Mac OS, Linux)-you'll need to download the font, upload it to your web server, and then create a few CSS rules that point to the new font. Once you've created the CSS rules that point to the new font on your web server, you can being using the font on your site.

Let's say you come across a website that's using the 'Source Sans Pro' font and you want to use that font for the blockquotes on your WordPress theme. The first thing you'll need to do is download the Source Sans Pro font.

_Keep in mind that not all fonts are available for download. Some fonts, like those included with [TypeKit](http://typekit.com), require paying a subscription. A great place to download custom fonts for free is [Font Squirrel](http://www.fontsquirrel.com/). You can also get free fonts at [Google Fonts](http://www.google.com/fonts), but Google makes it slightly more difficult to download them and prefers instead that you load the fonts remotely from Google's servers (this article does not explain that method)._

## Downloading the Custom Font

Let's start by finding the Source Sans Pro font. A quick search on Google for "Source Sans Pro font" turns up [the font at Font Squirrel](http://www.fontsquirrel.com/fonts/source-sans-pro) with a big "Download TTF" button at the top.

Downloading the font will give us a zip file that contains a bunch of different files ending in `.otf`:

![Source Sans Pro font files](http://independentpublisher.me/wordpress/wp-content/uploads/2013/11/Screen-Shot-2013-11-30-at-10.22.11-AM.png)

> _Source Sans Pro font files_

Each of those files contains the Source Sans Pro font in a different style. For example, if you're using the Source Sans Pro font and you make the text bold, you'll need the web browser to load the `SourceSansPro-Bold.otf` file.

There are several different styles included with the Source Sans Pro font and you'll need to create a separate `@font-face` declaration for each style that you want to use. But before we talk about declaring the fonts, we need to install them.

## Installing the Custom Font

To install the font, we need to upload the font files to our web server. The best place to put these is inside a [Child Theme](http://codex.wordpress.org/Child_Themes).

A Child Theme allows us to make modifications to the parent theme without actually modifying the parent theme itself. This makes it easy to upgrade the parent theme and to see exactly what changes we made.

A child theme is simply a blank theme that imports a parent theme. We can then override styles and functions in the parent theme by making changes to our child theme.

If you're already using a Child Theme, you can skip the next section.

### Installing and Activating a Child Theme

If you're not already using a Child Theme with Independent Publisher, you can download the starter [Independent Publisher Child Theme](https://github.com/raamdev/independent-publisher-child-theme), upload it to the WordPress Themes directory on your server (`wp-content/themes/`), and then activate it from your WordPress Dashboard (`Dashboard -> Appearance -> Themes`).

_**Note:** If you downloaded the (parent) Independent Publisher theme from GitHub, you'll need to make sure the theme directory name is `independent-publisher` and not `independent-publisher-master`, otherwise the child theme won't be able to find the parent theme. After downloading and uploading the Independent Publisher Child Theme, you should have two directories in your `wp-content/themes/` directory: `independent-publisher` (the parent theme) and `independent-publisher-child `(the child theme, which we'll be modifying in this tutorial._

### Uploading the Custom Font

Before we can start using the custom font, we need to upload the font files to the server.

When we unzipped the `source-sans-pro.zip` file, it gave us a directory called `source-sans-pro` with a bunch of font files inside. I recommend uploading that entire directory to your Child Theme directory (you should end up with `wp-content/themes/independent-publisher-child/source-sans-pro/`).

### Creating a new @font-face Rule

Now comes the fun part. To start using the custom font on our website, we need to create new CSS3 `@font-face` rules, one for each font style that we want to use.

Add the following to the `style.css` file inside your Child Theme:
    
    
    @font-face {
    	font-family: SourceSansPro;
    	src: url('source-sans-pro/SourceSansPro-Regular.otf');
    }
    @font-face {
    	font-family: SourceSansPro;
    	src: url('source-sans-pro/SourceSansPro-Bold.otf');
    	font-weight: bold;
    }
    @font-face {
    	font-family: SourceSansPro;
    	src: url('source-sans-pro/SourceSansPro-Italic.otf');
    	font-style: italic;
    }
    @font-face {
    	font-family: SourceSansPro;
    	src: url('source-sans-pro/SourceSansPro-BoldItalic.otf');
    	font-weight: bold;
    	font-style: italic;
    }
    @font-face {
    	font-family: SourceSansPro;
    	src: url('source-sans-pro/SourceSansPro-Light.otf');
    	font-weight: 300;
    }
    @font-face {
    	font-family: SourceSansPro;
    	src: url('source-sans-pro/SourceSansPro-LightItalic.otf');
    	font-style: italic;
    	font-weight: 300;
    }

Now we're ready to start using the new font face!

## Changing the Blockquote Font

Let's say that we want to change the quotes font. Right now, quotes in the Independent Publisher theme look like this:

![](http://independentpublisher.me/wordpress/wp-content/uploads/2013/11/Screen-Shot-2013-11-30-at-11.40.19-AM.png)

If we want to start using the Source Sans Pro font for quotes, we'll need to override the parent theme CSS style definition for the `<blockquote>` tag. We can do that by adding the following CSS to the Child Theme's `style.css` file:
    
    
    blockquote { 
    	font-family: SourceSansPro, sans-serif; 
    	font-style: italic;
    	font-weight: 300;
    }
    

_**Note: **You'll notice how I added `sans-serif` to the end of the font list. That's called a "font stack" and it's important because if someone loads your website and they have a problem downloading or loading the SourceSansPro font, the web browser will simply load the next font in that list (in this case, `sans-serif`, which is a default font available on all computers)._

If you save the `style.css` file and then view a quote, you'll see how the font has changed:

![](http://independentpublisher.me/wordpress/wp-content/uploads/2013/11/Screen-Shot-2013-11-30-at-11.40.07-AM.png)

### How Does This Work?

If you look back at the `@font-face` declaration that included the styles `font-style: italic;` and `font-weight: 300;` you'll see that it loaded the font file `source-sans-pro/SourceSansPro-LightItalic.otf`. That's the version of the Source Sans Pro font that will get loaded when wherever we use that combination of styles.

## Warnings and Further Reading

There are lots of things to be aware of with regards to using custom fonts and the `@font-face` rule. One thing in particular is that not all web browsers support all font types (or even the `@font-face` rule, for that matter).

In this example we used the Open Type Face (`.otf`) font, but there are many other formats (`.ttf`, `.eot`, `.woof`, `.svg`) and not all web browsers support all formats.

The following links will help you determine browser support:

For more on the `@font-face` rule, check out [this article on Six Revisions](http://sixrevisions.com/css/font-face-guide/).
