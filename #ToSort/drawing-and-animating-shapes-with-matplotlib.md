# Drawing and Animating Shapes with Matplotlib

_Captured: 2017-02-17 at 14:24 from [nickcharlton.net](https://nickcharlton.net/posts/drawing-animating-shapes-matplotlib.html)_

As well a being the best Python package for drawing plots, [Matplotlib](http://matplotlib.org/) also has impressive primitive drawing capablities. In recent weeks, I've been using Matplotlib to provide the visualisations for a set of [robot localisation](http://en.wikipedia.org/wiki/Robotic_mapping) projects, where we can use rectangles, circles and lines to demonstrate landmarks, robots and paths. Combined with [NumPy](http://www.numpy.org/) and [SciPy](http://www.scipy.org/), this provides a quite capable simulation environment.

_Note: You should already know how to work with Matplotlib. If you don't, I suggest either [Matplotlib for Python Developers](http://www.amazon.co.uk/gp/product/1847197906/ref=as_li_ss_tl?ie=UTF8&camp=1634&creative=19450&creativeASIN=1847197906&linkCode=as2&tag=nisbl-21) or the [SciPy Lecture Notes](http://scipy-lectures.github.com/)._

Primative shapes in Matplotlib are known as patches, and are provided by the patches module. Subclasses of patch provide implementations for Rectangles, Arrows, Ellipses (and then Arcs, Circles) and so on. All of this is part of the [Artist](http://matplotlib.org/api/artist_api.html) API, which also provides support for text. In fact, everything drawn using Matplotlib is part of the artists module. It's just a different level of access for drawing shapes compared to plots.

### Drawing

There are multiple ways to write Matplotlib code[^ways]. Whilst I'm using Pyplot in the demonstrations below, the usage is essentially the same. The differences are in how the figure is initialised.

Drawing is a matter of adding the patch to the current figure's axes, which using Pyplot looks something like this:
    
    
    import matplotlib.pyplot as plt
    
    plt.axes()
    
    circle = plt.Circle((0, 0), radius=0.75, fc='y')
    plt.gca().add_patch(circle)
    
    plt.axis('scaled')
    plt.show()
    

`gca()` returns the current Axis instance. Setting the axis to "scaled" ensures that you can see the added shape properly. This should give you something like Figure 2[^colours].

![Figure 2: Circles](https://nickcharlton.net/resources/images/mpl_circles_example.svg)

> _Figure 2: Circles_

### Rectangles
    
    
    rectangle = plt.Rectangle((10, 10), 100, 100, fc='r')
    plt.gca().add_patch(rectangle)
    

`rectangle` is a [Rectangle patch](http://matplotlib.org/api/artist_api.html#matplotlib.patches.Rectangle). It accepts a tuple of the bottom left hand corner, followed by a width and a height.

`kwargs` of either `ec` or `fc` set the edge or face colours respectively. In this case, it gives us a red rectangle without a border. Various others are also supported, as this is just a subclass of `Patch`.

### Circles
    
    
    circle = plt.Circle((0, 0), 0.75, fc='y')
    plt.gca().add_patch(circle)
    

`circle` is a [Circle patch](http://matplotlib.org/api/artist_api.html#matplotlib.patches.Circle). It accepts a tuple of the centre point, and then the radius.

The argument of `fc` gives us a yellow circle, without a border.

### Lines
    
    
    line = plt.Line2D((2, 8), (6, 6), lw=2.5)
    plt.gca().add_line(line)
    

A basic line is a [Line2D](http://matplotlib.org/api/artist_api.html#module-matplotlib.lines) instance. Note that it's an Artist itself and so its not added as a patch. The first tuple gives the `x` positions of the line, the second gives the `y` positions. `lw` specifies the line width. Much like lines that are part of plots in Matplotlib, the line has a lot of configurable styles, such as the following:
    
    
    dotted_line = plt.Line2D((2, 8), (4, 4), lw=5., 
                             ls='-.', marker='.', 
                             markersize=50, 
                             markerfacecolor='r', 
                             markeredgecolor='r', 
                             alpha=0.5)
    plt.gca().add_line(dotted_line)
    

which gives the lower line in Figure 3. `ls` defines the line style and `marker` gives the start and end points.

![Figure 3: Two Lines](https://nickcharlton.net/resources/images/mpl_two_lines.svg)

> _Figure 3: Two Lines_

_Note: If you can't see the lines and only the end markers: There's a [Bug in WebKit](http://code.google.com/p/chromium/issues/detail?id=135321) which stops you seeing straight lines. You probably can't see the plot grid lines, either._

### Polygons

[Polygons](http://matplotlib.org/api/artist_api.html#matplotlib.patches.Polygon) are just a series of points connected by lines -- allowing you to draw complex shapes. The Polygon patch expects an Nx2 array of points.
    
    
    points = [[2, 1], [8, 1], [8, 4]]
    polygon = plt.Polygon(points)
    

Polygons are also a nice way to implement a multi-step line, this can be done by tuning the Polygon constructor somewhat:
    
    
    points = [[2, 4], [2, 8], [4, 6], [6, 8]]
    line = plt.Polygon(points, closed=None, fill=None, edgecolor='r')
    

This gives the red line in Figure 4. `closed` stops Matplotlib drawing a line between the first and last lines. `fill` is the colour that goes inside the shape, setting this to `None` removes it and the `edgecolor` gives the line it's colour.

![Figure 4: Polygons](https://nickcharlton.net/resources/images/mpl_polygons.svg)

> _Figure 4: Polygons_

### Animation

The interest here is to move certain shapes around, and in the case of something like a line (which could, for example, represent a path) update its state. Here, I'm going to get a ball to orbit around a central point at a set distance away from it:
    
    
    import numpy as np
    from matplotlib import pyplot as plt
    from matplotlib import animation
    
    fig = plt.figure()
    fig.set_dpi(100)
    fig.set_size_inches(7, 6.5)
    
    ax = plt.axes(xlim=(0, 10), ylim=(0, 10))
    patch = plt.Circle((5, -5), 0.75, fc='y')
    
    def init():
        patch.center = (5, 5)
        ax.add_patch(patch)
        return patch,
    
    def animate(i):
        x, y = patch.center
        x = 5 + 3 * np.sin(np.radians(i))
        y = 5 + 3 * np.cos(np.radians(i))
        patch.center = (x, y)
        return patch,
    
    anim = animation.FuncAnimation(fig, animate, 
                                   init_func=init, 
                                   frames=360, 
                                   interval=20,
                                   blit=True)
    
    plt.show()
    

To do this, I'm just using the equation for a point on a circle (but with the sine/ cosine flipped from the typical -- this just means it goes around in clockwise), and using the animate function's `i` argument to help compute it. This works because I've got 360 frames.

The `init()` function serves to setup the plot for animating, whilst the `animate` function returns the new position of the object. Setting `blit=True` ensures that only the portions of the image which have changed are updated. This helps hugely with performance. The purpose of returning `patch,` from both `init()` and `animate()` is to tell the animation function which artists are changing. Both of these except a tuple (as you can be animating multiple different artists.) The `Circle` is initially created off screen as we need to initialise it before animating. Without initialising off screen, blitting causes a bit of an artifact.

And so, this (with the addition of the section below) produces the video in Figure 5 below:

Dammit. You can't see this video. It's MP4 (H.264). But, you can [download it and see it that way](). 

> _Figure 5: The Ball Animation as a Video_

[Jake Vanderplas' notes on Matplotlib](http://jakevdp.github.com/blog/2012/08/18/matplotlib-animation-tutorial/) were invaluable in figuring this section out. Notably in blitting[^blitting]. But generally, simple Artist animation is a bit thin on the ground. Hopefully this helps with that somewhat.

### Output

I initially wanted to be able to export in two formats, one as an H.264 video, like the one above and as an animated gif. My initial assumption was that a gif would most likely have less of an overhead than that of a video and it would avoid browser inconsistencies.

To solve the video export, Matplotlib comes with support for exporting video sequences from an animation using the save method on `Animate`. It pipes out support for video to [ffmpeg](http://www.ffmpeg.org/), but video formats are somewhat fickle and so you need to add a few more flags to get it to render correctly.
    
    
    anim.save('animation.mp4', fps=30, 
              extra_args=['-vcodec', 'h264', 
                          '-pix_fmt', 'yuv420p'])
    

This saves an H.264 file to 'animation.mp4' in a format supported by QuickTime[^pfmt]. In [Jake Vanderplas'](http://jakevdp.github.com/blog/2012/08/18/matplotlib-animation-tutorial/) animation tutorial he doesn't specify a pixel format and it works fine. I suspect this might be something to do with ffmpeg defaults. You'll also need to be using Matplotlib version 1.2.0 or greater (I had issues with 1.1.0.)

Sadly, Matplotlib doesn't support producing gifs on it's own, but this was only the first of a few issues. We can convert the image we've just produced using ffmpeg and stitch it back together as a gif using [ImageMagick](http://www.imagemagick.org/script/index.php):
    
    
    ffmpeg -i animation.mp4 -r 10 output%05d.png
    
    convert output*.png output.gif
    

Here, ffmpeg converts the video file from before into a series of PNG files, then we use ImageMagick's `convert` command to push these back together into a gif. On its own, this ended up with a 4MB file. Even the video was only 83KB and so this isn't so great. After attempting to compress the final output gif using ImageMagick (they have a huge article on [Animation Optimisation](http://www.imagemagick.org/Usage/anim_opt/)), I turned to compressing each input file using [ImageOptim](http://imageoptim.com). This ended up giving me a final image size of 8.0MB (and took a good hour.) Worse than I started with.

With this, I concluded that a gif isn't that great of an option. I'd like to see animated SVG support for Matplotlib, but I'd wonder if this required moving to something which was stylised using a Document-Object-Model (DOM). Michael Droettboom touched on this in his "[Matplotlib Lessons Learned" post](http://mdboom.github.com/blog/2013/03/25/matplotlib-lessons-learned/). Even for something much more complex than these contrived examples, using JavaScript to animate the SVG is much better option. But for now, a video is the best way.

And that's about it. One of the advantages of having the Matplotlib provided grid is that the numbers are relatively easy to determine -- for my purposes this means hooking the view to the calculations.

[^colours]: Your colours will probably vary. I use Huy Nguyen's "[Sane colour scheme](http://www.huyng.com/posts/sane-color-scheme-for-matplotlib/)".

[^ways]: I typically use `pyplot`, rather than `pylab` to keep the namespace clean. Pylab provides a merging of the Numpy and Matplotlib namespaces to ease transition from MATLAB. It's not recommended and anyway I'm a programmer -- not MATLAB user -- first.
    
    
    And then I'd use the OOP method for embedding in bigger projects, I've done
    this for use in PyQt, for example. The OOP method is slightly more complex, but
    a better alternative if you need to display multiple, similar plots using 
    different data.
    

[^blitting]: The return value of `animate()` must contain the items which have changed, but also those inside the figure, otherwise you'll see a mess of artifacts working their away across the image.

[^pfmt]: To be more specific, it seems that QuickTime doesn't support the Planar 4:4:4 YUV pixel format which ffmpeg outputs by default. The `-pix-fmt` flag specifies using Planar 4:2:0 YUV which it does support.
    
    
    However, Jake's `save` doesn't have this flag, but it is encoded in 4:2:0. Why?
    I have no idea.
    
