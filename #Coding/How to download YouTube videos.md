# How to download YouTube videos

_Captured: 2015-12-11 at 16:07 from [www.chainsawonatireswing.com](http://www.chainsawonatireswing.com/2015/03/08/how-to-download-youtube-videos/)_

I teach a lot of classes & give a lot of talks, & long ago I learned a painful lesson: never rely on the Internet to be available. Murphy's Law & all that. So if I have a video to show, I try to get an offline copy just in case. Since YouTube has everything in the world on it, this usually means grabbing a copy of the video from the ubiquitous service.

The most reliable method I've found is a wonderful command line tool called `[youtube-dl`](http://rg3.github.io/youtube-dl/). Its `man` page describes itself thusly:

> youtube-dl is a small command-line program to download videos from YouTube.com and a few more sites. It requires the Python interpreter, version 2.6, 2.7, or 3.2+, and it is not platform specific. It should work on your Unix box, on Windows or on Mac OS X. It is released to the public domain, which means you can modify it, redistribute it or use it however you like.

(By the way, note the sort of tongue in cheek "and a few more sites". It actually works on a _lot_ of other sites. Not all, but quite a few.)

To install it on your Mac[1](http://www.chainsawonatireswing.com/2015/03/08/how-to-download-youtube-videos/), use Home Brew via your terminal[2](http://www.chainsawonatireswing.com/2015/03/08/how-to-download-youtube-videos/):
    
    
    brew install youtube-dl

Now that it's on your machine, let's test it. I've been playing the new zombie apocalypse combined with parkour jumper game [Dying Light](https://en.wikipedia.org/wiki/Dying_Light) lately, & that first night mission is incredibly tense & scary. Let's download the video so you can see for yourself![3](http://www.chainsawonatireswing.com/2015/03/08/how-to-download-youtube-videos/)
    
    
    $ cd ~/Downloads
    $ youtube-dl https://www.youtube.com/watch?v=QG8j3SqOxJw
    [youtube] QG8j3SqOxJw: Downloading webpage
    [youtube] QG8j3SqOxJw: Extracting video information
    [youtube] QG8j3SqOxJw: Downloading DASH manifest
    [download] Destination: Dying Light - First Night Mission-QG8j3SqOxJw.mp4
    [download] 100% of 77.89MiB in 00:20

A short wait later, you'll find an MP4 file named "Dying Light - First Night Mission-QG8j3SqOxJw.mp4" in your Downloads folder. Note that `youtube-dl` figured out the largest resolution available for the video & then downloaded the MP4 version of that file (& named the file with the YouTube ID as well). If you want a smaller resolution, or a different format, start reading the very complete `man` page or the [online documentation](https://github.com/rg3/youtube-dl/blob/master/README.md).

Now, that's cool, but what if you're like me, & you're thinking that you'd like to be able to perform a workflow like this:

  1. See a video on YouTube's website.
  2. Download said video using `youtube-dl` without having to manually type or cut & paste. 

[Keyboard Maestro](http://www.keyboardmaestro.com) to the rescue (insert picture of superperson with a large KM on their chest)!

I use Safari, but this could be applied to any web browser. Set up a trigger (in my case, I open a palette of commands in Safari & press `Y`) & use the following actions:

  * Type the ⌘L keystroke  
Select the address bar.
  * Type the ⌘C keystroke  
Copy the URL of the current webpage.
  * Activate iTerm  
[iTerm 2](http://iterm2.com) is my terminal app of choice, & it's always running.
  * Type the ⌘T keystroke  
Open a new tab in iTerm.
  * Insert Test by Pasting: `cd ~/Downloads && youtube-dl "%CurrentClipboard%" && exit %Return%`  
The cool part: `cd` to my `Downloads` directory; if that happens successfully (the `&&`), then run `youtube-dl` using the URL copied earlier; if that happens successfully (again with the `&&`), then exit the shell, closing the tab we opened earlier. The `%Return%` is there to execute the command.
  * Delete Past Clipboard 0  
No need to keep that URL.

You could always extend this, so that, for instance, after the video downloads it immediately loads & plays, or that you go back to Safari after the download finished, but I'll leave that up to you. For now, happy downloading!

  1. If you're using Linux, you should be able to find `youtube-dl` in your software repository of choice. If you're Windows, you can download an executable from the website. [↩](http://www.chainsawonatireswing.com/2015/03/08/how-to-download-youtube-videos/)

  2. If you don't update your Home Brew installation very often, you'd better get in the habit. It seems like `youtube-dl` updates a few times a week. [↩](http://www.chainsawonatireswing.com/2015/03/08/how-to-download-youtube-videos/)

  3. **Warning**: This video contains scary zombie monster situations & some bad language, but nothing like the bad language you would have heard coming out of my mouth when I was playing it for myself! [↩](http://www.chainsawonatireswing.com/2015/03/08/how-to-download-youtube-videos/)
