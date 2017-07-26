# Editorial App Workflow Upload Image to WordPress Media Library Version 2.2

_Captured: 2015-09-26 at 17:03 from [www.jackenhack.com](http://www.jackenhack.com/editorial-app-workflow-upload-image-wordpress-media-library/)_

![Editorial iOS app icon](http://www.jackenhack.com/wp-content/uploads/2014/04/editorial-app-icon-150x150.jpg)

> _Editorial iOS app icon_

I've tried a lot of blogging apps for the iPad, but none of them handles images the way I want. Images gets the weird name iOS has assigned to them which is not good for [SEO](http://en.wikipedia.org/wiki/Search_engine_optimization). When I upload images to WordPress, I want them to end up in the WordPress Media Library and have all the theme defined sizes created automatically. Just like when you upload from the web interface in WordPress. There's an added problem when you want your site to support images displayed on a Retina or high DPI device, showing the picture in high resolution using a plugin like [WP Retina x2](https://wordpress.org/plugins/wp-retina-2x/). My favourite text editor on iOS is [Editorial](http://www.jackenhack.com/go/editorial-app/) app, So I made this Workflow so I can do the naming, resizing and uploading of the images directly inside the app from my iPad or iPhone 6 Plus. You can select which of the theme defined image sizes you want to display and also set the image alignment. This workflow works excellent with the [WP Retina x2](https://wordpress.org/plugins/wp-retina-2x/) plugin, which is the one I use on my site. When everything is done, you have an [MultiMarkdown](http://fletcherpenney.net/multimarkdown/) referred image link at the cursor position in the text editor, and the image link and information like width, height and alt-text is added to the end of the document. This makes a very convenient way of blogging on the iPad.

## Features

  * uploads images directly to WordPress Media Library which creates the different image sizes defined in WordPress theme
  * Able to name the image and give it an alt-text
  * Choice of uploading original size or to reduce the image size
  * Choose left, center or right alignment for the image
  * Creates a short referenced MultiMarkdown link at the cursor position and adds the image info at the end of the document automatically
  * Adds the images pixel dimensions for HMTL5 compliance

## Download The Workflow

Begin by downloading the [workflow](http://www.jackenhack.com/go/editorial-app-upload-image-wordpress-media-library-v2/) by following the link and press install on your iOS device.

## Prerequisites

This workflow use the wordpress_xmlrpc module, so that **needs to be installed in Editorial before you can use the workflow!** But I've [written a guide about how to install the module/library here](http://www.jackenhack.com/editorial-app-import-modules-with-pipista/). You could also add the wordpress_xmlrpc library via iTunes, but I haven't tried it. If you forget to install the library, the workflow will warn you and also link you to instructions on how to install it. It's a one time installation. I'm thinking of making this automatic, but I haven't had time to look into it yet.

## Before you begin

You need to edit the Workflow and add the URL of your site, your WordPress username and password. It's easily found in the beginning of the workflow.

## How to use

Put the cursor where you want your image to appear and start the Workflow. After starting, you get the standard iOS image select dialog to choose an image from your iOS image gallery. So select the picture you want to use.

![imageselect](http://www.jackenhack.com/wp-content/uploads/2014/12/image-select-347x400.jpg)

After selecting the image you get a dialog where you can upload either the full resolution image, or resize it to your liking before uploading.

![Image resize dialog](http://www.jackenhack.com/wp-content/uploads/2014/12/image-resize-dialog-300x400.jpg)

> _Image resize dialog_

Enter a filename for the image. Use something descriptive, but avoid spaces and substitute them with "-". If you forget and use spaces, they will be replaced by "-" automatically. You don't need to add .jpg at the end of the name if you don't want to, it's also handled automatically.

![filename dialog](http://www.jackenhack.com/wp-content/uploads/2014/12/filename-dialog-300x400.jpg)

> _filename dialog_

Enter an image title if you like. If you don't need an image title, just press OK.

![Image title dialog](http://www.jackenhack.com/wp-content/uploads/2015/01/image-title-dialog-400x232.png)

> _Image title dialog_

Next up is a dialog box where you can select one of the predefined image sizes you have configured in your WordPress theme, or go with a full resolution image.

![Select image size dialog](http://www.jackenhack.com/wp-content/uploads/2015/01/select-image-size-349x400.png)

> _Select image size dialog_

Enter an alt text for the image. **You need to do this**, because it's used as the marker name in the [MultiMarkdown](http://fletcherpenney.net/multimarkdown/) link. And you should always enter an alt description for images anyway. Both for visually impaired and for Google, because Google Image use that text to get a hint of what the image is depicting.

![image alt text dialog](http://www.jackenhack.com/wp-content/uploads/2015/01/image-alt-dialog-400x200.png)

> _image alt text dialog_

When everything is done, you should now have a referenced link inserted and the image link information added at the end of the document.

![Finished link screenshot](http://www.jackenhack.com/wp-content/uploads/2015/01/finished-link-400x270.jpg)

> _Finished link screenshot_

When it's time to export to HTML, you need to use the [MultiMarkdown](http://fletcherpenney.net/multimarkdown/) function. Just make a simple export workflow like this one.

![Multimarkdown export script](http://www.jackenhack.com/wp-content/uploads/2015/01/editorial-multimarkdown-export-400x150.jpg)

> _Multimarkdown export script_

Happy blogging!

[ How To import modules with Pipista into Editorial iOS app](http://www.jackenhack.com/editorial-app-import-modules-with-pipista/)
