# Watermarking Images With Workflow

_Captured: 2016-07-24 at 20:16 from [www.jordanmerrick.com](https://www.jordanmerrick.com/posts/watermarking-images-with-workflow)_

# [Watermarking Images With Workflow](https://www.jordanmerrick.com/posts/watermarking-images-with-workflow)

[20 July, 2016](https://www.jordanmerrick.com/posts/watermarking-images-with-workflow)

Although [Workflow](https://itunes.apple.com/us/app/workflow-powerful-automation/id915249334?mt=8&at=10l64N) doesn't currently have a built-in action specifically for watermarking, there are a couple of ways to accomplish this with just a little preparation.

### Using the Edit Image action

Workflow has a capable image editor built-in already, powered by [Aviary](https://aviary.com/), which is invoked using the _Edit Image_ action. There's a text tool within Aviary that provides control over the placement and style of text in an image. The only drawback is that the text cannot be automatically specifiedâit has to be entered each time. 

A workaround is to include a _Text_ action with the text to use, then have Workflow copy it to the clipboard before the rest of the workflow Is run, as shown in this [example workflow](https://workflow.is/workflows/25ec6146c64b48cda4cfcf5514bfb659). All you then need to do is paste it into the editor's text input field. 

![](https://www.jordanmerrick.com/media/watermark-edit-image-process.gif)

This method works great if you just need to occasionally watermark an image. If you want to fully automate the process and/or work with multiple images, there is a better solution.

### Using the Overlay Image action

It's possible to create a workflow that can automate the entire process of adding a watermark to images using the _Overlay Image_ action, a more recent addition to Workflow's collection1. This particular action is very customizable, providing options for the dimensions, location and angle of the overlaid image2.

Although Workflow cannot generate an image file from text, we can just create one in advance and use it within the workflow. I created a watermark in [Pixelmator](https://itunes.apple.com/us/app/pixelmator/id924695435?mt=8&at=10l64N) and saved it as a transparent PNG (delete the background layer before exporting). I recommend making the canvas size (and text) suitably large, around 2000-3000px wide, so that it can be used in images of all different sizes (Workflow will resize the image down accordingly).

![](https://www.jordanmerrick.com/media/watermark-pixelmator.jpeg)

With a watermark already created, it's simply a matter of overlaying the watermark onto the target image. At this point, we could use the Overlay Image action's option of **Show Image Editor** and manually drag and resize the watermark, but we can do better than this. Instead, Workflow can get the height of the target image, then set the size of the watermark to a proportional height.

In this [example workflow](https://workflow.is/workflows/8887f92cd04b4c0f812eb2dcac69866c), I've specified that the watermark be placed on the lower-left, at a height of 10% of the target image. The width is automatically scaled, and the opacity is set to 90%. The watermark is stored in the `/Workflow` directory on iCloud Drive, as `workflow.png`.

![](https://www.jordanmerrick.com/media/watermark-overlay-image.jpeg)

The entire process is fully autonomous and works with multiple images. You could take this workflow even further and include options for selecting whether a black or white text overlay should be used, as well as varying the angle and location of the text (if you prefer a full-size diagonally-placed watermark, for example). 

* * *

  1. This action was added to Workflow 1.4.4. ↩
  2. It basically made my [Screenshot Builder](https://www.jordanmerrick.com/posts/screenshot-builder-workflow) workflow obsolete. ↩

Â© 2012-2016 [Jordan Merrick](mailto:jordan@jordanmerrick.com)

  * [RSS](http://feed.jordanmerrick.com)
  * [Twitter Feed](https://twitter.com/jordanmerrick_))
