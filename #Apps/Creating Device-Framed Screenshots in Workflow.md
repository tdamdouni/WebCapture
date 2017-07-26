# Creating Device-Framed Screenshots in Workflow

_Captured: 2016-01-05 at 22:13 from [www.jordanmerrick.com](https://www.jordanmerrick.com/posts/screenshot-builder-workflow)_

I spent some time over the holidays catching up on a selection of previous [Club MacStories](https://www.macstories.net/club/) newsletters and came across a reader question in the _Workflow Corner_ section of Issue 10:

> Is there any way to build a workflow that would put the latest screenshot into an iPhone or iPad frame?

Federico Viticci response was that there isn't a fully autonomous way of placing a screenshot inside an iOS device frame, suggesting instead to use an app like [Pixelmator](https://itunes.apple.com/gb/app/pixelmator/id924695435?mt=8&at=10l64N) and Apple's [official product marketing images](https://developer.apple.com/app-store/marketing/guidelines/).

Federico isn't wrong - there isn't really any way to automate the placement of a screenshot inside an existing image of something like an iPhone or iPad using something like Workflow. However, if we come at this from a different angle, it actually is possible to achieve the desired result with Workflow.

Instead of looking to insert a screenshot inside device image, a screenshot can be "wrapped" by slicing a device image beforehand. Then, with some creative use of the "Combine Images" action and a few variables later, it's possible to wrap a screenshot in a way that results in a perfect image of an iOS device containing a screenshot.

![An example using this workflow](https://www.jordanmerrick.com/assets/images/screenshot-builder-example.jpg)

> _An example using this workflow_

I've created this [Screenshot Builder workflow](https://workflow.directory/workflows/screenshot-builder) and the necessary image assets that you can use to frame a screenshot with the iOS device of your choice. This is achieved by slicing the device image into four distinct segments (top, bottom, left and right sides), as the following screenshot (with some added padding) will show:

![See how the device has been split into four distinct pieces](https://www.jordanmerrick.com/assets/images/screenshot-builder-split.jpg)

> _See how the device has been split into four distinct pieces_

I spent some time slicing the images available from Apple so that the workflow can provide support for:

  * iPhone 6s
  * iPhone 6s Plus
  * iPad Pro
  * iPad Air
  * iPad mini
  * iPod touch
  * Apple Watch

Each iOS device has an option (and assets) to use either Silver or Space Gray colours (with the exception of the iPod touch, which offers Blue and Silver options) and will automatically detect if a screenshot should be in portrait or landscape.

### Using this Workflow

This workflow requires the pre-made image assets I've created be saved to Dropbox so it can use them when creating these device screenshots. To do this, use this [Dropbox link](https://www.dropbox.com/sh/gz6wag6qnlj1liw/AAAs8jxO9NjiD692Ccvwhj5Ha?dl=0
) and add the folder (`screenshot-builder`) to your Dropbox account (click _Download_, then _Save to my Dropbox_). You'll need to update the Dropbox action in the workflow if you move this from the root of your Dropbox folder.

Once the above has been done, simply run the workflow and select the device, its colour and the screenshot that you'd like to create.

### Examples

![Apple Watch with CARROT Weather](https://www.jordanmerrick.com/assets/images/screenshot-builder-example-watch.jpg)

> _Apple Watch with CARROT Weather_

Apple Watch with [CARROT Weather](https://itunes.apple.com/gb/app/carrot-weather-talking-forecast/id961390574?mt=8&at=10l64N)

![iPhone 6s Plus with Overcast](https://www.jordanmerrick.com/assets/images/screenshot-builder-example-iphone-6s-plus.jpg)

> _iPhone 6s Plus with Overcast_

iPhone 6s Plus with [Overcast](https://itunes.apple.com/gb/app/overcast-podcast-player/id888422857?mt=8&at=10l64N)

![iPhone 6s Plus with Alto's Adventure](https://www.jordanmerrick.com/assets/images/screenshot-builder-example-iphone-6s-plus-landscape.jpg)

> _iPhone 6s Plus with Alto's Adventure_

iPhone 6s Plus with [Alto's Adventure](https://itunes.apple.com/gb/app/altos-adventure/id950812012?mt=8&at=10l64N)
