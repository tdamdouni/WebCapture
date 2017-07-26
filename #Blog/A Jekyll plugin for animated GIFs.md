# A Jekyll plugin for animated GIFs

_Captured: 2015-08-20 at 19:08 from [brettterpstra.com](http://brettterpstra.com/2015/08/20/a-jekyll-plugin-for-animated-gifs/?utm_medium=App.net+Broadcast&utm_source=PourOver)_

I put together a Jekyll plugin called [GifTag](https://github.com/ttscoff/JekyllPlugins/tree/master/GifTag) which turns local gif references into a styled placeholder with play/pause and preloading. This allows a page to finish loading before transferring heavy animated gifs, and adds user control as to when they start playing (as well as allowing them to stop).

In use, the syntax is simply:
    
    
    {% gif path_to_gif %}
    

You can pass in either a path to a JPEG or PNG poster image, or the GIF path, as long as both exist. If it's a GIF file, it will search for a JPG or PNG image with a matching path (but different extension). If neither of those are found, it can generate a poster frame for you with the ImageMagick package.

Here's what it outputs:
    
    
    <figure class="animated_gif_frame">
    	<img src="/uploads/2015/08/autobook.jpg" data-source="/uploads/2015/08/autobook.gif" width="800" height="450" />
    </figure>
    

There's some JavaScript and CSS you need to include (along with jQuery, unless you want to rewrite the click handler in something else) in order for it to work on the front end. Easy enough, though. Full details in my [JekyllPlugins project on GitHub](https://github.com/ttscoff/JekyllPlugins/tree/master/GifTag).

![](http://cdn3.brettterpstra.com/uploads/2015/08/matrixish.jpg)
