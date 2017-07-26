# MallocNanoZone=1 Makes for Hard Debugging

_Captured: 2015-10-08 at 22:22 from [shapeof.com](http://shapeof.com/archives/2015/10/mallocnanozone.html)_

While debugging a problem in [Acorn](http://flyingmeat.com/acorn/) yesterday, I came across a little oddity in Xcode that I thought was worth writing up for the greater good of my fellow Mac OS X developers. (Hey everyone- how's it going? iOS might get all the attention, but at least we can charge livable prices for our apps, amiright?).

Yesterday, Acorn had a bug where pasting a bitmap into an image would occasionally cause the bitmap show up as an empty layer. I could never get it to reproduce on my machine of course. I knew it was real though, I even had video evidence of it in action. It would just would not happen for me.

Then all of a sudden it did happen. And of course, I didn't have a debugger attached from Xcode so I couldn't break and see what the heck was going on. So I launched Acorn from Xcode, and tried to reproduce it. No luck.

Then it happened again, and I found a pretty reliable way to reproduce it. But again I wasn't running from Xcode and when I launched it from Xcode I couldn't reproduce it.

This shouldn't be happening. Why would the debugger "fix" this problem? Well, that's easy enough to test- I'll just turn off the debugger when running from Xcode. But then the bug didn't happen.

OK, so I was going down the wrong trail. It's not the debugger causing it. What else could be causing problems? Environment variables I turned on for debugging maybe? I checked the Run scheme to see if I had anything turned on there- and I did (Core Image flags), but turning those off wouldn't cause the bug to occur.

Maybe Xcode was setting an environment variable for me that I wasn't aware of? This was easily tested- I just added a couple of lines to Acorn to print the env vars, and compared the output from when I ran from Xcode vs. the Finder. One entry jumped out at me immediately- MallocNanoZone was set to 1 when run from Xcode, and it wasn't around when run from the Finder.

So I set MallocNanoZone to 0 in Acorn's Run scheme, launched Acorn from Xcode, and the bug reproduce right away. I had found what was masking the bug, and it was pretty easy to find the actual bug in Acorn after that.

So what does the MallocNanoZone env variable do? It's a flag that changes the memory allocator for your app, and for the frameworks your app uses. I don't know the specifics of this allocator vs whatever the normal one is, but I do know how it hid this bug from me in Acorn. When MallocNanoZone was set, the allocator worked in such a way that when I used CFRelease with a CGImageRef, and then used CGImageGetWidth with that same (bad) reference, it would return the correct answer (CGImageCreateCopyWithColorSpace() may have been involved as well). When MallocNanoZone was off the normal allocator was used and CGImageGetWidth would return a bad answer (as it should!). This bad answer caused Acorn to put the bitmap in the wrong spot and then the layer showed up empty.

Why does Xcode set MallocNanoZone=1? My understanding is that the Finder used to do this, so Xcode set the variable to behave the same as the Finder. However, I checked 10.8-10.11 and couldn't find any evidence of this.

TL;DR: If you're working on an OS X app, open up the run scheme and make sure to set MallocNanoZone=0 in your environment variables. If you don't, then you're using a different allocator than your users are, and behavior of your app might be different.

The fixes will be in Acorn 5.1.1 and 4.5.7, available now on the [latest builds](http://flyingmeat.com/download/latest/) page.
