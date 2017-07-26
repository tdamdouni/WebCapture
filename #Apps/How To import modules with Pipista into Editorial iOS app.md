# How To import modules with Pipista into Editorial iOS app

_Captured: 2015-09-26 at 17:04 from [www.jackenhack.com](http://www.jackenhack.com/editorial-app-import-modules-with-pipista/)_

![1377461573.jpg](http://www.jackenhack.com/wp-content/uploads/2013/08/1377461573-150x128.jpg)

## Importing pipista modules in Editorial

Lets face it, the [Editorial](http://omz-software.com/editorial/) App is a fantastic text/Markdown editor. It's incredibly powerful with scripting abilities. But one of the most amazing tool for a power user is the ability to write Python scripts that can do almost anything. There are a lot of modules included with Editorial, but how do you add a library if it's not included? There is a script for Editorials sister application [Pythonista](http://www.jackenhack.com/go/pythonista-python-ios/), that makes it easy to add modules, and you can use that for importing libraries to Editorial as well. The script is called [Pipista](https://gist.github.com/pudquick/4317095).

## How to import a python module in Editorial

I needed to import the python-wordpress-xmlrpc library for [uploading images to the WordPress Media Library on my blog directly from Editorial](http://www.jackenhack.com/editorial-app-workflow-upload-image-wordpress-media-library/) so the images ends up in the media section in WordPress. I didn't want to use FTP or SFTP. So here is how to import (and use) that module.

First you need [Pipista](https://gist.github.com/pudquick/4317095). I'm using version 2 unstable because it unzips the file automatically, so everything is done for you. It also puts the modules in a separate directory so it doesn't clutter up your filesystem.

  1. First we need to get the pipista script into Editorial. So go to the [pipista GitHub page](https://gist.github.com/pudquick/4317095) and download the script as a text file. (You can just select the text and paste it into a text file.)
  2. Name the file pipista.py
  3. Upload the pipista.py file to Editorial with iTunes  
![Import pipista to Editorial app image](http://www.jackenhack.com/wp-content/uploads/2014/06/itunes_pipista_editorial_import.jpg)

> _Go to the Console and write the following lines. Enter each line separately and end with return._

  4. import pipista  
pipista.pypi_install('python-wordpress-xmlrpc')

You should now have the module installed and ready to go.

## Using the new module in your scripts

Because the directory with the modules aren't in the system path, you need to add that at the top of your script before trying to import a module. Just write

sys.path += [os.path.join(os.getcwd(), '../../../Documents/pypi-modules')]

And now you can import you're newly installed modules.

from wordpress_xmlrpc import Client, WordPressPost  
from wordpress_xmlrpc.compat import xmlrpc_client  
from wordpress_xmlrpc.methods import media, posts

And there you go!

## Compatible Modules

Not all modules will be compatible, especially those that needs to compile C or other languages, so you need to experiment and check the [Editorial](http://omz-forums.appspot.com/editorial) or [Pythonista forums.](http://omz-forums.appspot.com/pythonista)

**Happy hacking!**
