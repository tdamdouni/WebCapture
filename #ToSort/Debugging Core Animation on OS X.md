# Debugging Core Animation on OS X

_Captured: 2015-12-03 at 19:36 from [jwilling.com](http://jwilling.com/blog/debugging-core-animation-on-osx/)_

Have you ever looked longingly at the Core Animation template in Instruments and wished it worked for OS X apps? Sadly that hasn't happened yet, but workarounds exist. In this post, we'll be exploring ways to debug Core Animation on the Mac so you can make your app as optimized as possible.

Since we don't have access to the Core Animation template, we're going to have to resort to two different tools for debugging and profiling.

## Profiling FPS

In order to see what FPS our application is achieving, we need to use the Quartz Debug application. Unfortunately, it's not bundled by default with Xcode. It requires a separate download. At the time of writing, it's available [in Apple's developer downloads](https://developer.apple.com/downloads/?name=graphics%20tools%20for%20xcode) as part of the _Graphics Tools_ package.

![](http://jwilling.com/assets/images/posts/debugging-core-animation-on-osx/quartz-debug.png)

The tool is relatively straightforward. You run Quartz Debug, then launch your application. Start an action that requires the application to perform a drawing update (such as scrolling), and watch the FPS & CPU meter on Quartz Debug. Sadly, this is about all of the utility this tool provides. Other debugging tools can be located in _Window > Quartz Debug Settings_, but unfortunately they are limited in practice. However, it's still valuable to know the framerate of your application, as it's handy to determine if your app needs more optimization.

## Debugging Core Animation

This is one of the areas that's been lacking severely on OS X. What most people don't know is that there's an entirely hidden way to perform Core Animation debugging in a very similar fashion to iOS.

![](http://jwilling.com/assets/images/posts/debugging-core-animation-on-osx/debug-example.png)

Does this coloring look familiar? If you've utilized Instrument's Core Animation template for iOS, you might recognize the coloring of opaque views. So how do we get this on the Mac?

Before 10.9, it was possible to utilize undocumented Core Animation environmental variables to enable various Core Animation debugging modes. Unfortunately this does not work in 10.9. Why? Layers in 10.9 are actually rendered out-of-process, meaning it effectively broke the debugging capability that previously existed. But thanks to another undocumented magic environmental variable (h/t [Matt Sarnoff](https://twitter.com/autorelease)), we can achieve the old behavior. Here's the flag:

> `CA_LAYER_SURFACE=1`

There isn't any information anywhere about this flag, so utilize it with care. From what I have best been able to determine, it forces the application to render layer trees in-process. This will not cause any harm to your system, but it is something that can potentially impact your performance measurements. As a result, it should not be enabled unless debugging is taking place.

If you're unfamiliar with how to add environmental variables, you can do so in Xcode in _Product > Scheme > Edit Scheme_. Select the _Run_ target, click on the _Arguments_ tab, and enter the environmental variable in the list near the bottom. It'll look like this:

![](http://jwilling.com/assets/images/posts/debugging-core-animation-on-osx/env-variables.png)

Now that we've enabled in-process rendering, we can start using other environmental variables to force Core Animation to enable various debugging modes. Let's take a look at some of the most useful ones. More can be found [here](http://iphonedevwiki.net/index.php/QuartzCore.framework).

### Color Opaque

Variable: `CA_COLOR_OPAQUE`

One of the most significant hits to performance can occur as a result of blending. Transparent layers force the GPU to composite layers all the way up the tree until it reaches an opaque layer. This blending can potentially be expensive. Often it is unnecessary, and can be avoided with just a few changes.

Here's an example. This is a layer that is non-opaque. Notice that it's highlighted in red.

![](http://jwilling.com/assets/images/posts/debugging-core-animation-on-osx/opaque1.png)

> _By setting it to opaque, it becomes green._

![](http://jwilling.com/assets/images/posts/debugging-core-animation-on-osx/opaque2.png)

In most applications, it's not possible to remove all blending. After all, sometimes it's useful to have blending. However, by removing as much blending as possible, rendering time can be reduced.

Tips:

>   * If the background is a solid color, simply set a background color on the layer that matches that of the layer behind it. This allows your layer to be opaque, but still have the same effect.
>   * The amount of blending occurring is signified by the shade of overlaied red. A light red color indicates little blending. If removing blending isn't possible, try to make the red color as light as possible.

### Color Offscreen

Variable: `CA_COLOR_OFFSCREEN`

In certain situations, Core Animation is forced to render layers twice: once off-screen and one on-screen. This is simply known as off-screen rendering.

This type of rendering can be triggered by numerous different situations. Here are some of them:

  * `CALayer` with rasterization enabled (`shouldRasterize` = `YES`)
  * `CALayer` with a shadow
  * `CALayer` with a corner radius
  * `CALayer` with a mask

Here's an example. The black square has a shadow applied to it.
    
    
    CALayer *layer = [CALayer layer];
    layer.shadowRadius = 5;
    layer.shadowOpacity = 1;
    

With the environmental variable enabled, it looks like this:

![](http://jwilling.com/assets/images/posts/debugging-core-animation-on-osx/offscreen1.png)

In order to remove this offscreen rendering pass, we can set a value on the `[shadowPath`](https://developer.apple.com/library/ios/documentation/GraphicsImaging/Reference/CALayer_class/#//apple_ref/occ/instp/CALayer/shadowPath) property of our layer. Although the intricacies of `shadowPath` our outside of the scope of this article, it essentially bypasses a complete traversal of the layer's sublayers when attempting to figure out the path that the shadow should be cast from. By skipping out on dynamic shadows and providing this ourself, we can usually increase performance quite dramatically. Let's see what setting a shadow path does:
    
    
    CGMutablePathRef path = CGPathCreateMutable();
    CGPathAddRect(path, NULL, layer.bounds);
    
    layer.shadowPath = path;
    
    CGPathRelease(path);
    

![](http://jwilling.com/assets/images/posts/debugging-core-animation-on-osx/offscreen2.png)

Much better. On a side note, it seems like if the content view of the window is layer-backed, it is rendered off-screen. I'm not exactly sure why.

Tips:

  * A common case for setting a border radius on a layer is to get a circle avatar effect. This is rather expensive to do through layers due to off-screen rendering. A good alternative is to pre-render the images clipped to a circle in a drawing context. That circle image can then safely be used as the content for the avatar layer, without it needing any corner radius. Although this has an up-front performance cost, we can avoid the cost per-frame, which is a worthy tradeoff.
  * In certain situations, layers can be rasterized (`shouldRasterize` = `YES`) in order to minimize off-screen rendering. Sometimes this can be relatively beneficial. If the layer's content does not ever change, it is worth the initial cost to rasterize the layer, as layer rendering will be easy. However, if the content of the layer changes frequently, it will be even more costly than if it was disabled.

### Color Copied Images

Variable: `CA_COLOR_COPY`

If you have an application that is image-intensive, minimizing Core Animation image copies is extremely important. Before we discuss how to fix the issue, let's talk about why it occurs.

Before images can be displayed by Core Animation, they must first be decompressed. Most images are stored on disk in a compressed format, so they must first be decompressed in order to be usable. This is done automatically by Core Animation when it is time to render. This decompression is not a fast process.

Additionally, even when an image is decompressed it might not be in the right format. Core Animation has a very specific byte-alignment for images, and if the image does not match this, it will be copied _on the main thread at render time_. As expected, this is very slow. In an application that requires fast image loading due to scrolling, this can be a huge bottleneck.

We can detect some of this through the use of the environmental variable shown above. If an image is copied, it might be displayed in blue. Something like this:

![](http://jwilling.com/assets/images/posts/debugging-core-animation-on-osx/copy1.png)

By using proper byte-alignment when decompressing, it should display without any tint:

![](http://jwilling.com/assets/images/posts/debugging-core-animation-on-osx/copy2.png)

Note that this instrument does not seem to always work as expected. Although it's an easy way to check at a glance if there are any issues with image decompression or copying, it's not completely accurate. The most accurate way to detect if copying is occurring is to use Instruments with a time profiler. You'll want to be looking for `CA::Render::copy_image` in your stack trace.

So how can we get proper byte-alignment for our images so Core Animation doesn't need to do a copy? We need to forcibly decompress the images using Core Animation's pixel format by redrawing it in a new context. Here's an example category on `NSImage` that can accomplish this. It's recommended to generate this image on a background thread in order to avoid the very problem that we're trying to prevent.
    
    
    @implementationNSImage(JNWDecompression)
    
    static CGContextRef JNWCreateOpaqueGraphicsContext(CGSize size) {
        size_t width = size.width;
        size_t height = size.height;
        size_t bitsPerComponent = 8;
        size_t bytesPerRow = 4 * width;
    
        CGColorSpaceRef colorSpace = NSScreen.mainScreen.colorSpace.CGColorSpace;
        if (colorSpace == nil) {
            colorSpace = (CGColorSpaceRef)CFAutorelease(CGColorSpaceCreateDeviceRGB());
        }
    
        CGBitmapInfo bitmapInfo = (CGBitmapInfo)kCGImageAlphaNoneSkipLast;
        CGContextRef ctx = CGBitmapContextCreate(NULL, width, height, bitsPerComponent, bytesPerRow, colorSpace, bitmapInfo);
    
        return ctx;
    }
    
    - (NSImage *)jnw_decompressedImage {
        CGImageRef CGImage = [self CGImageForProposedRect:nil context:nil hints:nil];
    
        CGRect rect = (CGRect){
            .size.width = CGImageGetWidth(CGImage),
            .size.height = CGImageGetHeight(CGImage)
        };
    
        if (rect.size.width == 0 || rect.size.height == 0) {
            return nil;
        }
    
        CGContextRef context = JNWCreateOpaqueGraphicsContext(rect.size);
    
        CGContextDrawImage(context, rect, CGImage);
    
        CGImageRef nativeCGImage = CGBitmapContextCreateImage(context);
        NSImage *image = [[NSImage alloc] initWithCGImage:nativeCGImage size:self.size];
    
        CGImageRelease(nativeCGImage);
        CGContextRelease(context);
    
        return image;
    }
    
    @end
    

## CA Instrument

To help make instrumentation easier, I've put together a small app.

![](http://jwilling.com/assets/images/posts/debugging-core-animation-on-osx/ca-instrument.png)

Here's how to use it:

  * Select an app to instrument from the drop-down list in the titlebar. You can either select an app manually, or you an select an app that is already running.
  * Enable the various instruments that you'd like to utilize. It's usually best to only use one at a time.
  * Click instrument. The app will be (re)launched with the correct environmental flags enabled.

The app can be downloaded [here](http://jwilling.com/apps).
