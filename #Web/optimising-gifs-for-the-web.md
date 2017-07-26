# Optimising GIFs for the Web

_Captured: 2017-02-19 at 05:29 from [bitsofco.de](https://bitsofco.de/optimising-gifs/)_

Like a lot of people, I like GIFs. I like to use them in my articles to illustrate functionality. For example, this GIF from my article on "[Recreating the iTunes Library"](https://bitsofco.de/challenge-itunes-library/) -

However, a problem with this is that GIFs are _heavy_, the one above is a whopping 11.4 MB 😱 (NB: not exactly the image above, I couldn't _actually_ load that on a page). Recently, I've found that some of my articles that are GIF-heavy tend to get incredibly slow. The reason for this is that each frame in a GIF is stored as a GIF image, which uses a lossless compression algorithm. This means that, during compression, no information is lost in the image at all, which of course results in a larger file size.

To solve the performance problem of GIFs on the web, there are a couple of things we can do.

## Use HTML5 Video

Surprisingly, the lossless compression algorithm used on GIFs is so unoptimised that video formats such as MP4 or WebM will provide a smaller file size than GIF images. Because of this, one solution to the GIF performance problem is to not use GIFs at all, and to replace them with autoplaying, looping, HTML5 Video.

By applying certain attributes to the `<video>` element, we can simulate the behaviour of a GIF, but with a much smaller file size. The attributes we need are -

  * `autoplay`: Immediately start playing the video without the user needing to press "play"
  * `loop`: Loop the video infinitely
  * `muted`: Although there is no audio track on the GIF, stating this attribute is needed for iOS Safari to autoplay the video
  * `playsinline` : For iOS Safari, to make sure that the video is not moved to fullscreen mode
  * `poster`: Specifies an image to be displayed while the video is downloading

To replace the GIF from the introduction to this article, we can use the following video element -
    
    
    <video autoplay loop muted playsinline poster="original.jpg">  
        <source type="video/webm" src="original.webm">
        <img src="original.gif">
    </video>  
    

This will give us a video that's much smaller in size, at only 1MB 😱😱!

![](https://bitsofco.de/content/images/2017/01/lossy-compressed.gif)

To convert a GIF to WebM, we can use [CloudConvert](https://cloudconvert.com/gif-to-webm). Or, if you use [Cloudinary](https://cloudinary.com), you can just change the file extension from .gif to .webm to get the video format.

## Lossy Optimisation

In some cases, because HTML5 Video doesn't work everywhere, we can't get around having to use an actual GIF. For example, when this blog post is delivered as an HTML email, an actual GIF has to be used. So, there are some optimisations we can make to the GIF itself to make it more performant.

As I mentioned, GIF compression algorithm is lossless. However, there are options for _lossy_ compressions as well. Although this may sound like we will get visibly lower quality GIFs, lossy compression done well should not noticeably degrade the quality of the image.

There are a number of tools we can use for lossy GIF compression. One popular tool for optimising GIFs is [gifsicle](https://github.com/kohler/gifsicle) and [giflossy](https://github.com/pornel/giflossy). Gifsicle is a CLI for manipulating GIF image files, and giflossy is a fork of gifsicle which offers a lossy compression option (`\--lossy`).

To use giflossy to apply a lossy compression to a GIF image, we can use the following command -
    
    
    gifsicle -O3 --lossy=80 -o compressed.gif original.gif  
    

The `-03` option tells gifsicle to attempt several methods for optimisation to find the most suitable. The `\--lossy=80` option specifies how much to apply lossy compression. Depending on your needs, you can adjust this number. The `-o compressed.gif` option specifies what the output GIF should be called. Finally, we define the path to the original GIF.

Using this on the GIF example from before, we go from a 11.4MB GIF to a 6MB GIF, a 47% reduction in the size!

With these two methods combined, we can make use of GIFs in a way that doesn't degrade performance so drastically.
