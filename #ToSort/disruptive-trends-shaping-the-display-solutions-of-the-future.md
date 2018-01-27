# Disruptive trends shaping the display solutions of the future

_Captured: 2017-10-10 at 19:12 from [community.arm.com](https://community.arm.com/graphics/b/blog/posts/disruptive-trends-shaping-the-display-solutions-of-the-future?utm_source=Social&utm_medium=Organic&utm_campaign=MPG)_

![](https://community.arm.com/cfs-filesystemfile/__key/communityserver-components-secureimagefileviewer/communityserver-blogs-components-weblogfiles-00-00-00-20-66/mobile-phone-image.jpg_2D00_800x400x2.jpg?_=636428137795980439)

Back in 1983, when Motorola released its first commercial mobile phone - 784g of glory known as the [Motorola DynaTAC 8000X](https://en.wikipedia.org/wiki/Motorola_DynaTAC) - the very notion of making a mobile phone call seemed unutterably glamorous and other-worldly.

It seems unthinkable today, but back in '83, we were quite prepared to lug around something the size of a small loaf of bread just for the thrill of being able to speak to people on the move. "We" being the privileged minority, that is, since the 8000X cost £2639 - around a quarter of the average annual salary at the time, making it quite the status symbol, and well out of reach of the average (wo)man.

Fast-forward to 2017, and phones are no longer just about communication. Today's smartphones are multi-tasking devices, used for everything from planning holidays to starting the washing machine from the comfort of your desk. Our mobiles are sat navs, fitness monitors, personal banking tools and, perhaps most commonly, media consumption hubs, allowing us to play games, watch films and view photos.

Of course, the more time you spend looking at your mobile phone, the more important the display becomes - which is why screens are gradually getting bigger, and why manufacturers continue to push boundaries with exciting, new technologies to enhance the user experience… and in ever-more glorious technicolour, too.

## High Dynamic Range (HDR)

One of the industry trends that's been grabbing everyone's attention lately, HDR promises significantly higher-fidelity viewing, preserving texture and highlights, and more closely reflecting the human visual experience.

The world around us has a huge range of luminescence levels - from starlight to direct sunlight. Take a look out of the window and your superlative native viewing devices - that's your eyes - are able to pick out the finest textures, from the brightest whites of the clouds, to the darkest areas of shadow. That's because your eyes can perceive a very wide dynamic range.

Historically, displays have struggled to replicate what the human eye sees: onscreen, shadow tends to become a dark mass, and the texture of light areas - such as cloud - tends to be bleached out.

![HDR statistics](https://community.arm.com/resized-image/__size/300x0/__key/communityserver-blogs-components-weblogfiles/00-00-00-20-66/HDR-display-stats.png)

Naturally, whether you're viewing on a mobile or a widescreen TV, your screen has limitations. Even if the content is filmed in HDR, production processes often have to dramatically reduce the amount of information that's passed along the pipeline, in order to match the technical limitations of the viewing device. And if your screen has a limited dynamic range, it may struggle to accurately display the finer 'shades of brightness' - or darkness - meaning that you miss out on all the details.

That's why HDR is such a game changer.

By allowing you to see more of what was originally recorded, and retaining delicate gradations of tone, HDR makes colours seem richer, details more vivid and textures more authentic, giving you a superlative viewing experience that's breathtakingly life-like.

![HDR diagram](https://community.arm.com/resized-image/__size/1040x0/__key/communityserver-blogs-components-weblogfiles/00-00-00-20-66/1882.HDR-diagram.png)

[YouTube ](https://techcrunch.com/2017/09/08/youtube-launches-hdr-playback-on-select-mobile-devices/)recently updated its mobile app to bring HDR playback to mobile devices, and internet streaming services such as Netflix and Amazon Prime are now enabling HDR-10 content for streaming to any device - from mobiles and tablets to clamshells and digital TVs.

However, whilst excellent news for the consumer, this enhanced viewing experience poses significant technical challenges for the client device: there are numerous HDR formats, each requiring individual support; content creators tend to master content for premium HDR displays, in a range of formats with various characteristics, and that content needs to look good whether it's displayed on a large, state-of-the-art QLED/OLED HDR-capable 4K panel or a smartphone with an inexpensive, SDR full-HD LCD - potentially with SDR UI overlays, such as video playback controls, rendered by the GPU.

A robust HDR solution will, however, be able to tackle these challenges head on: it will work for any HDR content and map to any panel… which is why we've put so much effort into ensuring that our display solution is flexible and versatile enough to preserve the content's artistic intent, whatever device it's displayed on.

## Virtual Reality (VR)

VR already has its own unique set of display requirements, with high resolution at the top of the list: VR headsets sit far closer to the eyes than any other kind of screen, so the perceived quality is harder to maintain, and more pixels, of a higher quality, are needed in the same space for visuals to even begin to look convincing.

The refresh rate required for an immersive VR experience also means that modern display processors need to be able to cope with 4K x 2K displays at 60-120fps. However, to prevent blurring at 60fps, VR devices need low-persistence OLED panels, which are black for most of a frame… and low-persistence mobile LCDs would need 90 or even 120 fps to provide similar latency, since they're unable to progressively illuminate the pixels.

Another reason for VR's high frame-rate requirement is the need for low (<20ms) motion-to-photon latency - the time needed for user movements to be fully reflected on a display screen - which is essential to convince your brain that you're in another place. One way to reduce the overall latency is to increase the refresh rate - that is, the latency between the images - from 60Hz (16.67ms) to 120Hz (8.33ms). This goes a long way to creating an immersive experience, as well as helping to avoid virtual-reality sickness, which can result in symptoms such as nausea, drowsiness and disorientation.

Today's state-of-the-art panels offer resolutions of 2560x1440 (1280x1440 per eye) at 60-120 frames per second (fps) but the industry already has 4320x2160 (2160x2160 per eye) at 60-120fps in its sights. (To give you an idea of how [Mali display processors](https://www.arm.com/products/graphics-and-multimedia/mali-display) shape up to those requirements, they currently support resolutions and frame rates of up to 3840x2160 @60fps, with higher resolutions and frame rates of 4320x2160@90fps or 2880x1440@120fps targeted with our recently previewed display processor, [Mali Cetus](https://community.arm.com/graphics/b/blog/posts/mali-cetus-preview-driving-display).)

![ Virtual reality image](https://community.arm.com/resized-image/__size/1040x0/__key/communityserver-blogs-components-weblogfiles/00-00-00-20-66/Graphics-VR-Headset.jpg)

These unprecedented resolutions and frame rates present huge challenges in meeting the real-time throughput, latency and cost requirements needed to deliver a fully immersive VR experience. Bandwidth power also increases exponentially, often becoming the bottleneck in realizing such performance points in practice. (Smartphone apps processor SoCs are typically thermally limited to under 3W.)

To enable our [Mali multimedia solution ](https://www.arm.com/products/graphics-and-multimedia/mali-technologies)to provide optimal performance and bandwidth power across GPU, video and display, we've enabled novel VR techniques to support rendering of 360° video playback; foveated rendering for gaming; and on-display composition. In addition, the [Arm Frame Buffer Compression](https://developer.arm.com/technologies/graphics-technologies/arm-frame-buffer-compression) (AFBC) format reduces the overall system-level bandwidth - and the latest release adds new header layouts that further optimize performance and power when viewing 4K rotated aka landscape video on your portrait phone display. (I can tell you're impressed…)

## Multi-window Display

Whilst we - or at least, the office-based 'we' - are all quite used to split-screen views on our laptop, for mobile, it's a relatively new phenomenon.

Introduced in [Android N](https://en.wikipedia.org/wiki/Android_Nougat), multi-window displays let you view two apps side by side, so you don't have to interrupt your movie to send a quick text, for example. It also works on browser tabs, allowing you to price check items or cross-reference articles on two different websites at the same time, and windows can be resized on the fly just by dragging them to your preferred dimensions.

Easily launched via the recent apps button, just pressing and holding an app or a web page moves it to the top half of the screen. Pressing and holding another recent app - or hitting the home button to choose from the app tray as usual - selects content for the bottom half of the screen. Hey presto, you're done! It also works beautifully in landscape mode, obligingly flipping the view for seamless multitasking on the hop.

So how is this miracle of multi-windowing achieved? Well, the composition of multiple windows - including freeform, resized windows and Picture-in-Picture - can be better achieved through a hardware display solution, rather than a GPU software-based solution, using Android Hardware Composer HAL driver to limit the GPU's workload.

Premium display solutions are capable of compositing four windows or more, handling both HDR and SDR windows within the same composition scene, and allowing multiple windows to be scaled simultaneously. Add pixel alpha blending for animations, and you've got yourself a superb overall visual experience.

## Screens, Screens, Screens

The number of panels and interfaces that your humble display processor needs to be support just keeps growing. Display solutions must be engineered to support all major industry standards such as MIPI, typically for mobile embedded panels; VESA DP and eDP, for larger panels such as tablets and laptops; HDMI, for large, external screens such as DTV; as well as CEA-861 and ITU-R.

![ Screen block diagram](https://community.arm.com/resized-image/__size/1040x0/__key/communityserver-blogs-components-weblogfiles/00-00-00-20-66/0726.Screens-block-diagram.png)

This fragmented ecosystem requires a huge amount of collaboration with major display PHY, DDIC and display panel vendors to provide complete and optimized display solutions all the way to the glass. Furthermore, the landscape is dynamic, with a constant stream of new and evolving products - not to mention the introduction of new standards every now and then.

The constant quest to reduce cost and power adds another layer of complexity, and whilst the move towards self-refreshing panels has had a significant impact on the overall power consumption of the device, it has also created an additional challenge for silicon vendors, who must ensure accurate synchronization between the chip on the glass and the application processor.

In short, it's complicated - and will ever be so.

But however many complications these display trends bring for SoC providers, silicon vendors and manufacturers they are, ultimately, very good news for the consumer: by pushing the technical boundaries, and constantly revising the parameters of the possible, they are continually enhancing the visual experience… in ways that were unimaginable to proud owners of the DynaTAC 8000X.
