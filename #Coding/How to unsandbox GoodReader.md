# How to unsandbox GoodReader

_Captured: 2016-02-28 at 16:48 from [lordscotland.wordpress.com](https://lordscotland.wordpress.com/ios/unsandbox-goodreader/)_

[GoodReader](http://www.goodiware.com/goodreader.html) is a powerful all-in-one app for managing files, annotating PDFs, viewing documents, playing music/videos, and syncing with multiple cloud services. However, because of Apple's [sandbox restrictions](http://developer.apple.com/library/ios/documentation/iphone/conceptual/iphoneosprogrammingguide/TheiOSEnvironment/TheiOSEnvironment.html#//apple_ref/doc/uid/TP40007072-CH9-SW7), GoodReader is incapable of accessing and managing much of the filesystem outside its private, app-specific directory.

On a jailbroken device, this doesn't have to be the case. In the following article, I will explain how to grant GoodReader access to **any part of the filesystem** and the ability to open **arbitrary files**, while keeping all of its configuration files in its sandbox directory.

N.B.: This procedure involves modifying files on your device, including creating symlinks, editing plist files, and changing file permissions. ([This post](http://www.ifans.com/forums/threads/how-to-fix-ibooks-on-5-0-1-untethered.365660/) has a couple of lines describing how to create a symlink using iFile.)

With that, let's get started.

**Step 1**: Decrypt the GoodReader executable. Install [DecryptMe](https://www.myrepospace.com/profile/lordscotland/591111/DecryptMe) and restart GoodReader. If all goes well, you will have a decrypted executable in "My Documents". Move this file to `/var/mobile/Applications` and make it executable (change its permissions to 0755).

**Step 2**: Create a symlink to your unsandboxed GoodReader executable (`/var/mobile/Applications/GoodReader`) called "GoodReader" inside the original app directory (`/var/mobile/Applications/<UUID>/GoodReader.app`).

At this point, we can create as many symlinks to any part of the file system as we would like inside `/var/mobile/Applications/<UUID>/Documents`, and GoodReader will treat them as regular directories or files.

But what if we wanted to make the entire "My Documents" section of GoodReader to point to an arbitrary directory, say, `/var/mobile/Documents`? We could try replacing `/var/mobile/Applications/<UUID>/Documents` with a symlink to `/var/mobile/Documents`, but for whatever reason, this causes GoodReader to no longer accept files from external applications. For example, if we then downloaded a file in Safari, the "Open in GoodReader" option would still show up, but it wouldn't do anything. Weird.

It turns out that when a file is sent to a sandboxed application's Documents directory, iOS expects the directory to be exactly that, a directory. If it isn't, iOS figures that there's something wrong and aborts the operation.

Fortunately, there's a way around that, too: change GoodReader's home directory.

**Step 3**: Save the following BASH script to the file `/var/mobile/Applications/GoodReader.sh`. Make the file executable by setting its permissions to 0755.

`#!/bin/sh  
export HOME="$HOME/Documents"  
export TMPDIR="$HOME/tmp"  
export CFFIXED_USER_HOME="$HOME"  
exec "${0%.*}"  
`

Now, we need to tell SpringBoard to run this code instead of the symlinked GoodReader executable directly.

**Step 4**: Create a symlink to `/var/mobile/Applications/GoodReader.sh` called "GoodReader.sh" inside the original app directory (`/var/mobile/Applications/<UUID>/GoodReader.app`).

Then, let's change the package metadata to run "GoodReader.sh" instead of "GoodReader".

**Step 5**: Change the "CFBundleExecutable" string in the file `/var/mobile/Applications/<UUID>/GoodReader.app/Info.plist` from "GoodReader" to "GoodReader.sh". If possible, convert the plist to binary format.

With the home directory changed to `/var/mobile/Applications/<UUID>/Documents`, we now need to put the correct stuff in that directory. iOS still expects to find the "Documents", "Library", and "tmp" directories in this new home directory.

**Step 6**: Inside `/var/mobile/Applications/<UUID>/Documents`, create a symlink to `../Library` called "Library", and a symlink to `../tmp` called "tmp". Then, create a symlink to _wherever you want "My Documents" in GoodReader to access_, and call that "Documents". To clarify, you should have a `Documents/Library`, a `Documents/tmp`, and a `Documents/Documents` symlink afterwards.

Interestingly, iOS no longer cares that your real Documents directory is not a directory. When you try to send a file to GoodReader now, iOS will faithfully copy it to wherever `Documents/Documents` points and open it in GoodReader!

**Step 6.5**: If you use the special "Downloads" folder in "My Documents", you can change where that points to as well. Simply delete the folder `/var/mobile/Applications/<UUID>/Library/Application Support/com.goodiware.GoodReader.ASRoot/UserDocs` and replace it with a symlink to the directory you want to access.

The final step is to get GoodReader to open any type of file. This has nothing to do with the unsandboxing procedure, actually, but I thought it would be handy to include here. There's only one thing we need to do.

**Step 7**: Returning to the file `/var/mobile/Applications/<UUID>/GoodReader.app/Info.plist`, append a new dictionary to the array "CFBundleDocumentTypes". To this dictionary, add the following key-value pairs:

  * "CFBundleTypeName" = "OTHER"
  * "LSHandlerRank" = "Alternate"
  * "LSItemContentTypes" = Array("public.item")

To clarify, "LSItemContentTypes" should be an array with one string, "public.item". This is the default contentType group to which all files belong.

Feel free to post questions, comments, suggestions, bugs, etc. below.
