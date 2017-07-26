# Working Effectively with Git from iOS

_Captured: 2016-11-21 at 00:43 from [codenugget.co](http://codenugget.co/2016/11/20/working-with-git-from-ios.html)_

'Tis the season… for iOS automation, I guess.

Almost exactly one year ago [I blogged about my workflow](http://codenugget.co/2015/11/18/mobile-blogging-with-pythonista-jekyll-and-github.html) for publishing new posts from my iOS devices with the help of [Ole Zorn's](https://twitter.com/olemoritz) iOS app [Pythonista](http://omz-software.com/pythonista/). For someone like me, who does not use Python on a regular base, it was a pretty ambitious attempt, because it used the [pygithub3 module](https://github.com/PyGithub/PyGithub) for pushing new content and some custom UI for user interactions from the iOS share sheet.

![Pythonista and Working Copy running in Split View Mode on iPad](https://raw.githubusercontent.com/b00giZm/b00gizm.github.io/master/uploads/workingcoppy-ipad.jpg)

Back then, I neglected all existing Git clients for iOS, because I couldn't think of them being anywhere near as useful as the one running on my Mac. But there's one particular called [Working Copy](https://workingcopyapp.com/) by [Anders Borum](https://twitter.com/palmin) that's really close. Due to its closed nature, iOS data exchange between apps is still somewhat cumbersome, but gladly, Anders knows all the tricks of the trade: Working Copy registers itself as iOS [Document Provider](https://developer.apple.com/library/content/documentation/General/Conceptual/ExtensibilityPG/FileProvider.html), has a built-in [WebDAV server](https://en.wikipedia.org/wiki/WebDAV), and offers [a pretty extensive URL schema](https://workingcopyapp.com/url-schemes.html). Yes, you can really integrate your Git work flow with iOS editors like [Coda](https://panic.com/coda-ios/) or [Textastic](https://www.textasticapp.com/).

Sadly, there's no such integration yet with Pythonista, but you can get really far with just using Working Copy's URL scheme.

Here's the idea: I really wanted to keep all my Pythonista scripts at [Github](https://github.com/), because… well, that's where code belongs, I guess. Plus, being able to easily clone them on my Macs for further development, is a huge win for me.

So, I came up with two small Python scripts which do exactly that: Pushing new code to, and replacing old code by pulling changes from a Github repository:

import editor

import sys

def main():

print(sys.argv)

if len(sys.argv) <= 1:

print("No changes detected.")

quit()

editor.open_file(sys.argv[1])

text_length = len(editor.get_text())

editor.replace_text(0, text_length, sys.argv[2])

if __name__ == '__main__':

main()

[^gist]

They're really simple, as you can see. Depending on an `argv` parameter, the `update_repo` script builds URLs for either writing or reading file changes, and launches the Working Copy app. For writing, Working Copy will present a view where you can enter your commit message and choose to either save (`git add`), commit, or commit and push. For `reading`, it will pull changes from the remote repository, applies them locally and returns file's new contents via `x-success` parameter back to Pythonista, where `update_script` is called to update the script file.

![Working Copy and Pythonista on iPad](https://raw.githubusercontent.com/b00giZm/b00gizm.github.io/master/uploads/workingcopy-ipad.gif)

![Working Copy and Pythonista on iPhone](https://raw.githubusercontent.com/b00giZm/b00gizm.github.io/master/uploads/workingcopy-iphone.gif)

There are obvious limitations like the fact that you cannot easily update all your scripts at once, and that "local" changes are vicouisly overwritten, but at least it's something ;)

If you believe Apple CEO Tim Cook, [the iPad _is_ the future of computing](http://www.telegraph.co.uk/technology/2016/01/21/apples-tim-cook-declares-the-end-of-the-pc-and-hints-at-new-medi/). It might be for him, but for someone like me it still seems quite far away, though I'd love giving up my MacBook Pro for an iPad Pro, if I only was able to get my work done on it. 2016 wasn't the year for that, but small improvements like these make me a little more confident that we'll get there some day.
