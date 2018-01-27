# How to Crop a Photo With Python

_Captured: 2017-10-08 at 22:28 from [dzone.com](https://dzone.com/articles/how-to-crop-a-photo-with-python?edition=329537&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-10-08)_

[Learn how to build modern digital experience apps](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) with Crafter CMS. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).

If you like taking photos, then you will probably also find yourself cropping your photos from time to time. I will crop photos to get rid of background noise or to just focus more on the subject I was trying to capture. I also like to take high-resolution photos of insects or other small creatures and then crop it down to make it seem like I was even closer to the insect than I really was.

Now, most people will use a photo editing application to crop their image, such as Photoshop Elements. I use these kinds of tools too, but you can also use the Python programming language to do the cropping for you. One good example where you might want to use Python is if you have thousands of scanned images of the same type, then it makes more sense to just write a script to do the cropping for you.

The most popular package for image manipulation in Python is the [Pillow](https://python-pillow.org/) package, a "Friendly fork of the Python Imaging Library (PIL)." You can install Pillow using pip:

`pip install Pillow`

Now that we have Pillow installed, we just need a photo. Here's one of a grasshopper I took:

![Image title](http://www.blog.pythonlibrary.org/wp-content/uploads/2017/09/grasshopper-259x300.jpg)

Let's write some code to try to crop the picture down to just the grasshopper's head:
    
    
    def crop(image_path, coords, saved_location):
    
    
        crop(image, (161, 166, 706, 1050), 'cropped.jpg')

The first thing we do in this code is to import the **Image** sub-module from PIL. Then we create a **crop()** function that takes 3 parameters:

  * image_path - The file path to the file you want to crop.
  * coords - A 4-element tuple that contains the beginning and end coordinates to crop the image to.
  * saved_location - The file path to save the cropped file to.

After we open the initial image, we get an object back that we can call **crop() **on. The crop method takes the coordinates we passed in and crops the image down appropriately and returns a second image object. We then call this second image object's **save()** method and tell it to save it to the specified location.

When you run the code, it will show the cropped image as well as save it:

![Image title](http://www.blog.pythonlibrary.org/wp-content/uploads/2017/10/cropped_pil-224x300.png)

This is pretty close to what I wanted. You can experiment a bit with the x/y coordinates in the code above to try cropping the image in various ways to see how that works.

### Wrapping Up

This code should probably have a check in it that prevents the user from overwriting the original image. Any good photo editor will not overwrite the original photo as that is really annoying and usually a bad thing. But I will leave that to the reader to figure it out.

Anyway, the Pillow project is a really powerful and helpful package for working with images in Python. Give it a try and see what fun things you can accomplish!

Crafter is a [modern CMS platform for building modern websites](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) and content-rich digital experiences. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).
