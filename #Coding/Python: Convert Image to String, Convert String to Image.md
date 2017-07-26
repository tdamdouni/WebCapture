# Python: Convert Image to String, Convert String to Image

_Captured: 2015-11-22 at 13:51 from [www.programcreek.com](http://www.programcreek.com/2013/09/convert-image-to-string-in-python/)_

To store or transfer an image, we often need to convert an image to a string in such a way that the string represents the image. Like other programming languages (e.g. Java), we can also convert an image to a string representation in Python.

Converting in Python is pretty straightforward, and the key part is using the "base64" module which provides standard data encoding an decoding.

**Convert Image to String**

Here is the code for converting an image to a string.
    
    
    import base64
     
    with open("t.png", "rb") as imageFile:
        str = base64.b64encode(imageFile.read())
        print str

Output:

**Convert String to Image**

The following code segment will create an image by using the given string.
