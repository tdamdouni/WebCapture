# Git Workflows on iOS with Working Copy

_Captured: 2015-10-25 at 13:13 from [jblevins.org](http://jblevins.org/log/working-copy)_

![Showing Differences](http://jblevins.org/log/working-copy-diff.png)

> _Showing Differences_

[Working Copy](http://workingcopyapp.com/), by Anders Borum, is a comprehensive Git client for iPhone and iPad with support for iOS 8 share extensions and the iCloud document picker. It is currently [free in the App Store](https://itunes.apple.com/us/app/working-copy/id896694807?mt=8&at=11l5Vs&ct=log) with a $9.99 in-app purchase to unlock push support. This app is fundamentally new and different in ways that are hard to convey through simple lists of features, so I will elaborate by means of an example.

![Cloning a Repository](http://jblevins.org/log/working-copy-clone.png)

> _Cloning a Repository_

As it happens, this very post is a prime example of the power of Working Copy and inter-app communication on iOS 8. As I once described in "[Managing Websites with Git](http://jblevins.org/log/managing-websites-with-git)", I publish posts to this site by committing changes to a local working copy of the Git repository and then pushing the changes to a bare repository on my web server.[1](http://jblevins.org/log/working-copy) Although I write in Markdown, when the changes are received the server automatically converts the source files to HTML.

![Save in Working Copy](http://jblevins.org/log/working-copy-save.png)

> _Save in Working Copy_

Since Working Copy is a full Git client with support for the document picker, I first wrote this post on my iPhone in [Editorial](https://itunes.apple.com/us/app/editorial/id673907758?mt=8&at=11l5Vs&ct=log), then saved it directly to Working Copy using the iOS 8 share extension (first screenshot above), and finally committed and pushed the changes to the remote repository from Working Copy. Similarly, I took the screenshots on my iPhone and saved the images to Working Copy (which also has very good support for images) directly from the Photos app (second screenshot above). Another good option for editing files is to use [Textastic for iPad](https://itunes.apple.com/us/app/textastic-code-editor-for/id383577124?mt=8&at=11l5Vs&ct=log) or [iPhone ](https://itunes.apple.com/us/app/textastic-code-editor-for/id550156166?mt=8&at=11l5Vs&ct=log) and the document picker.
