# Publishing from Ulysses to Pelican

_Captured: 2017-01-11 at 20:18 from [www.movingelectrons.net](http://www.movingelectrons.net/blog/2017/01/08/ulysses-to-pelican.html)_

It's been a while since moving from [Squarespace](https://www.squarespace.com) to using [Pelican](http://blog.getpelican.com) as a **static site generator** for this website. Squarespace is beautifully designed, very resilient and _for the most part_ dependable (they experienced several DDOS attacks in the past). But it's not flexible when it comes to deeply customizing your site or when writing content.

Site generators like **Pelican** are extremely malleable. Since they process markdown files and images stored in certain pre-defined folders, the user only needs a text editor and an internet connected device to write and post.

Up until now, I've been using a combination of Apps for writing posts depending on which platform I'm working on: On windows and Mac, I use [Sublime Text](http://www.sublimetext.com/) and on iOS I use [Editorial](https://itunes.apple.com/us/app/editorial/id673907758?mt=8&at=11lqkH). Each of them is arguably the best text editor on their respective platform. Editorial may be lagging behind as it hasn't been updated in a long time, but nevertheless continues to work fine on iOS 10.

After posts were written, I would use [Dropbox](https://db.tt/TTohr0yOWI) as a glue between devices and [Hazel](https://www.noodlesoft.com/) to move files around between folders in order to generate the site. It's a pretty straight forward process, with some caveats: visualizing posts with images on the iPad was a pain because of where the site's content files are located in my computer (i.e. not in Dropbox) and the way markdown links work. There was a lot of massaging involved deleting temporary files and shuffling images around. Also, in order to work offline with [Editorial](https://itunes.apple.com/us/app/editorial/id673907758?mt=8&at=11lqkH) syncing through Dropbox, I had to remember opening Editorial and syncing the files beforehand.

## Enter Ulysses

I read a lot about **Ulysses** before writing this post. People are using it to writing blog posts, novels, do research and even writing [technical books](https://ulyssesapp.com/blog/2016/11/eline-explains-5/). I have yet to find a bad review. But what is so special about it?. Well, for starters **everything is in one library**, that's the main feature that sets it apart from similar Apps. All documents (known as _Sheets_) and _attachments_ are in one place, which allows to have a consistent look and previewing documents everywhere. There is an [iOS version](https://itunes.apple.com/us/app/ulysses/id950335311?mt=8&uo=4&at=11lqkH) and a [Mac OS version](https://itunes.apple.com/us/app/ulysses/id623795237?mt=12&uo=4&at=11lqkH), and syncing is beautifully done through iCloud. It's probably the best iCloud syncing implementation I have seen on any platform. Text, images and attachments were available in all platforms almost instantly in my tests. There is also support for [Dropbox](https://db.tt/TTohr0yOWI), but not all features are available when syncing that way (at least for now).

There is no Windows application, which is a big disadvantage for those of us who are forced to live in that environment during office hours. However, Ulysses allows to sync with _External Folders_ and Dropbox folders can easily be added to the library on both the Mac App and the iOS App. **The library, including synced external folders, can be used offline**.

![Ulysses for Mac - Preferences Pane.](http://www.movingelectrons.net/images/Ulysses_Pelican-Mac_prefs.png)

> _Ulysses for Mac - Preferences Pane._

As seen above, Ulysses allows direct publishing to Medium and Wordpress, but there is no official support for other blogging platforms. That's when the flexibility of Pelican and other [static site generators](https://www.staticgen.com/) comes into play. With some additional tools, posts can be sent to the Pelican in an _almost_ seamless process.

## General Setup

Here is the general layout of the process[1](http://www.movingelectrons.net/blog/2017/01/08/ulysses-to-pelican.html):

![From Ulysses to Pelican - General Process.](http://www.movingelectrons.net/images/UlyssestoPelican-General.jpg)

> _From Ulysses to Pelican - General Process._

As it can be seen, the heavy lifting will be done by a _Python 3.5 Script_. Posts can be written on either Ulysses for Mac or Ulysses for iOS, everything will be synced through iCloud. Images can be imported into the library from multiple sources, as always, and they will be automatically copied and placed in Pelican's content folders at the end of the process, ready to be used when generating the website. Alternatively, images from outside Ulysses library can be manually put in Pelican's content folders. As long as they are adequately referenced in the post/sheet, they will be used when generating the website.

Here is what is needed on each platform:

**On the Mac**

  * [Ulysses for Mac](https://geo.itunes.apple.com/us/app/ulysses/id623795237?mt=12&at=11lqkH). 
  * [Python 3.5](https://www.continuum.io/downloads/%E3%80%82).
  * [Python script](https://gist.github.com/Moving-Electrons/8d471055bb91929974733700aadbf78b) (more on this below).
  * _Bash script_ for executing the Python script. The Python script can be run directly without this script. However, I'm using it to facilitate execution, do some testing and save some lines when running the Python script from the command line.

The _Bash Script_ is just one line in the following format:

`<Path to Python Interpreter> <path to Python script> "$1"`

So, it would be something like this:

`/anaconda/envs/Anaconda3/bin/python3.5 /Scripts/Python/pelican_injection.py "$1"`

Remember to make the file executable like so:

`chmod 700 pelican_injection.py`

**On iOS**

  * [Ulysses for iOS](https://itunes.apple.com/us/app/ulysses/id950335311?mt=8&at=11lqkH).
  * [Workflow iOS App](https://itunes.apple.com/us/app/workflow-powerful-automation/id915249334?mt=8&at=11lqkH). This is one of my favorites apps on the platform. It allows to customize your device and automate repetitive tasks in an elegant way. it's tremendously effective in filling the gaps that separate iOS as a mobile platform from a full feature desktop OS.
  * [Workflow](https://workflow.is/workflows/8820a220d4dd48d4a1a80d599c5372c2) for Workflow App (I wish there was a better way to referencing the App and its actions). 

## Python Script

This part needs a bit more explanation as some configuration is required for the whole process to work as intended. Don't worry, it's very easy to setup.

The [script](https://gist.github.com/Moving-Electrons/8d471055bb91929974733700aadbf78b) is written in _Python 3.5_ (although it runs fine on _Python 2.7_). Here is a general overview of what the script does. It's the glue that bonds all together: Ulysses sheet, custom HTML and Pelican contents folder.

![From Ulysses to Pelican - Python Script](http://www.movingelectrons.net/images/UlyssestoPelican-Script.jpg)

> _From Ulysses to Pelican - Python Script_

It should be run passing an argument that must be either a _Zip file_ or a _Markdown file_, which are two of the three file extensions Ulysses can export to when exporting sheets to Markdown format (the Zip file includes all the images referenced in the sheet in addition to the Markdown file). The third is a [TextBundle](http://textbundle.org/) format, but the script is not compatible with it (yet).

If a Zip file is passed, the script extracts the images and copies them into the _Images content folder_ in Pelican. Then, it takes the Markdown file, renames it based on the _Slug_ (which is contained in the header of every post), inserts Pelican's _image output folder_ on every Markdown image link and performs what I call _HTML Code Injection_.

Markdown files can include raw HTML code which is then passed to the rendered HTML page. _HTML Code Injection_ is just a method I use to abbreviate the code that should be included in the final rendered page. For example, the Python script includes a function called _before_after_ which inserts the necessary HTML code in the Markdown file to show the before-and-after image comparison I use on some review posts, like [this one](http://www.movingelectrons.net/blog/2016/07/10/voigtlander-15mm-review.html#twentyBox-2). In order to accomplish that, I just include the following line in the Ulysses sheet at the place where I want the image comparison to be inserted:

`<beforeafter> before_filename|after_filename </beforeafter>`

For this particular case, the `before_filename` and `after_filename` image files should be manually copied to Pelican's image content folder in order to be rendered (i.e. They are not included in Ulysses library).

Keep in mind **there is no need to use this feature**, it's just an additional capability I've included for my particular case. I use this methodology to include the code that is later rendered as [Quarks Rating](http://www.movingelectrons.net/blog/2016/07/10/voigtlander-15mm-review.html) and [360 rotation](http://www.movingelectrons.net/blog/2016/12/11/sennheiser-pxc-550-review.html).

One thing **you do need to do is configuring the script _Constants_ holding the paths to Pelican content folders** (_POSTS_FOLDER_ and _IMAGES_FOLDER_) as well as the **path to the output image folder** relative to the site (in the case below _"/images/"_). For that, just edit the following section at the top of the script according to the way your Pelican folders are arranged on your system:
    
    
    # Constant Definition
    # -------------------
    
    # Path to be prepended to image links in markdown file, like so: ![](IMAGE_LINK<image_filename>).
    IMAGE_LNK = '/images/'
    
    # Pelican Content Folders:
    POSTS_FOLDER = 'Insert Path to Pelican markdown content folders.'
    IMAGES_FOLDER = 'Insert Path to Pelican image content folders.'
    FILES_FOLDER = 'Insert Path to Pelican files content folders. Not used in this version of the script.'
    # -------------------
    

That's it!. That's all you need to do. The script is free to use and modify as needed.

**Note** \- There is no need to rename the file when exporting from Ulysses. The script takes the _Slug_ field in the header and renames it accordingly. - Be aware that the script will **replace** any file in the output folder that shares the same name/slug as the one being converted. - Sheet attachments are not transferred to Pelican since they are not exported by Ulysses in the zip file.

## Workflow App

The [Workflow App](https://itunes.apple.com/us/app/workflow-powerful-automation/id915249334?mt=8&at=11lqkH) and associated [Workflow](https://workflow.is/workflows/8820a220d4dd48d4a1a80d599c5372c2) are instrumental for the process to work seamlessly on the iOS platform. As seen in the diagram above, the workflow sends the exported sheet from Ulysses to the Python script in the remote machine where Pelican is run. This is done **over an SSH connection** (through Workflow's _Run Script Over SSH_ action), so it's fast, reliable and secure.

![From Ulysses to Pelican - Workflow.](http://www.movingelectrons.net/images/UlyssestoPelican-Workflow.png)

> _From Ulysses to Pelican - Workflow._

Since Ulysses can send either a zip file or a text file when exporting from iOS, the Workflow automatically detects the file extension and reacts accordingly. When the workflow is imported, it'll ask for the necessary info to set everything up: _folder path_ for the script on the remote machine and _login credentials_. Everything will be stored locally.

## Ulysses for Mac

The Mac OS version of Ulysses is an extremely polished product. You can tell [The Solumen](https://www.ulyssesapp.com/team/) are a detail-oriented team. Simplicity and elegance are probably the two terms that would describe the App more accurately. It's very responsive _for the most part_ (it was a bit slow with long Sheets but that was remedied in the last update).

![Ulysses for Mac - Main Window.](http://www.movingelectrons.net/images/Ulysses_Pelican-Mac_App.png)

> _Ulysses for Mac - Main Window._

Both the Mac OS and the iOS versions are continuously updated. Not because of bugs needing to be squashed, but because the team constantly adds features and refines the product. It's truly a pleasure to use an App ecosystem in which so much thought has been put into.

When working on Ulysses for Mac, the process of exporting to Pelican is very straight forward: **just export the Ulysses Sheet in _Text_ and then _Markdown_ format to your disk**. If the Sheet has images, they will be exported alongside the Markdown file, in the same folder (note: they _will not_ be compressed into a Zip file like on the iOS version). Since the script can only take either Markdown (.md) files or compressed files (.zip) you can **either compressed the files and pass the resulting Zip file as an argument to the shell script or manually copy the image files to the appropriate Content folder on Pelican and run the Markdown file through the Shell script**. So, for the first option, the following should be typed on the _Command Line_ (obviously, change the path and the filenames below per your particular case):

`/path-to-script/pelican_injection.sh ulyssesExport.zip`

That's the manual way of doing it. There is an even more streamlined way to go through this process: through an [Alfred](https://geo.itunes.apple.com/us/app/alfred/id405843582?mt=12&at=11lqkH) Workflow on the Mac.

![Alfred Workflow for automating the Ulysses export process.](http://www.movingelectrons.net/images/UlyssestoPelican-AlfredWkflw.png)

> _Alfred Workflow for automating the Ulysses export process._

Using this Alfred Workflow, I just **export the files to disk from Ulysses, select them on the Finder, type _Alt CMD \_ and select _Send to Pelican_ from the Menu.** Done!, everything should now be on Pelican's Content folders adequately formatted and ready for the site to be generated.

## Ulysses for iOS

The iOS version of Ulysses has become one of my favorite apps on the platform. It simply invites you to continuing writing. It's elegantly designed, very responsive, with great iCloud synchronization. As mentioned before, it's possibly the best third party iCloud implementation as of today.

![Ulysses for iOS on iPad Pro.](http://www.movingelectrons.net/images/UlyssestoPelican-Ulysses_iOS.png)

> _Ulysses for iOS on iPad Pro._

Everything on the App feels native and well thought out. All features on the Mac version have been brought to iOS without compromising the user interface: attachments, tags/keywords, external folders, etc. Images can be imported from the Photos App or from the other Apps or cloud services, such as Dropbox.

Exporting sheets works as expected and very similar to the way it has been implemented on the Mac. The procedure to export to Pelican is as follows:

  * Tap on the _Share_ icon and select the format. In this case Text and then Markdown.
  * Tap on the three dots (_…_) and then _Open in Another App_.
  * On the new window, select _Run Workflow_ and once the list of workflows is shown, just select _Remote Pelican Injection_.

That's it!. It's that easy.

## Putting It All Together

I tried to make the process as easy and streamlined as possible on both platforms, MacOS and iOS. Looking at the paragraphs above, it may seem a bit complicated, but trust me, it's not. As an example, here is a video for exporting _this whole post_ from Ulysses for iOS into Pelican. When it's done, all images and Markdown file are adequately formatted and organized within Pelican content folders. **it only takes 17 seconds**.

Note: Disregard the error at the end of the video, the Workflow was run with a dummy IP for demo purposes.

[Exporting from Ulysses for iOS to Pelican Site Generator](https://vimeo.com/198487836) from [Moving Electrons](https://vimeo.com/user23511847) on [Vimeo](https://vimeo.com).
