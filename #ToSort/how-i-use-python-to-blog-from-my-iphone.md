# How I Use Python to Blog From My iPhone

_Captured: 2018-07-07 at 21:03 from [dzone.com](https://dzone.com/articles/how-i-use-python-to-blog-from-my-iphone-1?edition=385212&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-07-07)_

Deploying code to production can be filled with uncertainty. Reduce the risks, and deploy earlier and more often. [Download this free guide](https://dzone.com/go?i=278435&u=https%3A%2F%2Ftry.rollbar.com%2Flow-risk-continuous-delivery-guide%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\)) to learn more. Brought to you in partnership with [Rollbar.](https://dzone.com/go?i=278435&u=https%3A%2F%2Frollbar.com%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\))

![Using Python to blog from an iPhone](https://dzone.com/storage/temp/9670886-python-blog-iphone.jpg)

> _Using Python to blog from an iPhone_

Over the last 12 years, I have been blogging almost uninterruptedly about different subjects (mostly on tech stuff), on different platforms and using a variety of devices and applications. First on desktop and laptop computers, and more recently from iPhone and iPad. This year I went on to try something new and decided to create this blog based on Pelican, a static site generator made with Python. And I got the whole process working on my iPhone, which has become, arguably, my main personal computer. So, how do I publish new content to this blog from my iPhone?

## 1\. I Write Each Article in Markdown

Markdown is a simple syntax that can be easily translated to HTML (and a bunch of other formats), but only requires a simple text editor and allows us to focus on the content. On my Mac, I tend to use either Ulysses, or BBEdit, or VIM, whatever comes to hand. On iPhone, currently, I use Ulysses, Drafts or Working Copy. I may start with Drafts or Ulysses, then copy to Working Copy and go on from there…

Pelican only requires that the header contains some standard metadata. Some of it is optional, but I try to always include the same set of fields. Here's an example of the header I would use for this article:

Then I just leave a white line and write the rest of the article below.

## 2\. Sync With the Cloud, I Mean, Commit to GitHub

The source code for this website is hosted as an open source repository on GitHub. It's a good way to share the experience with others while keeping track of any changes and having them synced between devices on demand.

I may start on my iPhone and commit the changes to GitHub using Working Copy. Then, if I want, I may clone the repo or fetch the changes from my iPad or Mac, do some further editing and commit again to GitHub.

## 3\. Build the Website With Pelican

Usually, you will use Shell to type a command like `pelican content/ -s publishconf.py` or `make html`. While on a desktop operating system it is an easy task, on mobile it is less than ideal. So, I created my own building script that I can use in Pythonista to generate all the HTML and image thumbnail files. Actually, I compiled a few scripts that do the whole process - as I want it to be done - just by tapping a few buttons.

If I need to grab the most current version from GitHub, I run the following code in StaSh:

Note that I don't need to manually open the Pythonista app, then open StaSh in Python 2.7 mode (required here for this `git` command to work properly), then type the path to this script… No. I created a simple workflow that automates all those steps and added an icon to the home screen. I just tap the icon and it downloads all the source files. Then I do the same with another button that calls my `make_html.py` script. One tap and it starts building the site in Pythonista with Pelican:
    
    
    print ‘\nReading the publish settings file.\n’
    
    
    abspath = os.path.abspath(__file__)
    
    
    dname = os.path.dirname(abspath)
    
    
    os.chdir(os.path.expanduser(‘~/Documents/pelican-stuff/The-No-Title-Tech-Blo/src’))
    
    
    settings_filepath = os.path.expanduser(dname+’/The-No-Title-Tech-Blo/src/publishconf.py’)

## 4\. Optimize Images

OK, if you follow my writings, you may already know I have been exploring ways to automate my image optimization workflow. On my Mac, I like to export my images to PNG or JPEG (the image format will depend on the type of content), in the best suitable size. When possible, I try to offer images in 2x resolution for _Retina_ displays. Then I use ImageOptim and JPEGmini to shrink the files.

On iOS, I often use the Workflow app, when I have a picture on my photo library, to resize it and save it as a smaller JPEG. Or to combine 2, 3, or 4 iPhone screenshots into a single image, using just a few taps.

But if I already have all the source images in their folders, after I build the site I do a final optimization step. It's still kind of experimental, but I have another home screen button that runs my [Optimize Images](https://no-title.victordomingos.com/projects/optimize-images/) Python application on the Pelican output folder. That way I can squeeze out a few more bytes from the thumbnails generated during the build process.

## 5\. Upload Using FTP

Yeah, our old and beloved friend, FTP, an old solution that is still simple and efficient enough to keep deserving some usage in the present. The way I do it is by running a Python script that opens an FTP connection to my web server and uploads everything from the output folder:
    
    
    print(‘\n\nOpening an FTP connection for the upload...\n’)
    
    
    opts = {“force”: True, “delete_unmatched”: True, “verbose”: 3}
    
    
    s = UploadSynchronizer(local, remote, opts)
    
    
    print(‘\n\nUpload complete!’)

On iOS, of course, it requires a single tap on a home screen icon. It takes a while to upload, depending on the connection speed, so it may be a good idea to do something else while it is working. When it finishes, I usually open Safari and do a final check to see if there were no typos or a broken link.

## 6\. On iOS 12 (Currently in Beta) You Can Do it "Hands-Free" With Siri

On the upcoming iOS 12 operating system, Apple is adding a new feature called Siri Shortcuts, that seems to be an evolution from URL schemes and the Workflow app (in fact, Apple has acquired the company that created Workflow). On the current beta, we still don't have the new Shortcuts app, but we do have access to some Siri suggestions of available shortcuts we can set. The trick is to use the Workflow app to create a new workflow for each task (like running a specific Python script in Pythonista), then you run it, and then you should be able to find that workflow action in Siri's suggestions, in Settings. You set a voice command and that's it.

I created four Siri shortcuts for those same four actions for which I had created home screen icons (I could probably reduce this to just one or two steps, but I prefer to go through each stage at a time, in order to see any eventual warnings or error messages):

  1. Get the latest version from GitHub.

  2. Build the website.

  3. Optimize images.

  4. Upload the website.

![Using Siri Shortcuts on iOS 12 to deploy a static website from an iPhone](https://dzone.com/storage/temp/9670879-ios12-beta-siri-shortcuts.jpg)

> _Using Siri Shortcuts on iOS 12 to deploy a static website from an iPhone_

So, after I finish writing and preparing images, all it takes is 4 taps on the screen or 4 voice commands to Siri. The iPhone does the rest of the magic, automatically. Here is a small video of the whole build and deployment process being done directly from an iPhone 7:

Deploying code to production can be filled with uncertainty. Reduce the risks, and deploy earlier and more often. [Download this free guide](https://dzone.com/go?i=278436&u=https%3A%2F%2Ftry.rollbar.com%2Flow-risk-continuous-delivery-guide%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\)) to learn more. Brought to you in partnership with [Rollbar.](https://dzone.com/go?i=278436&u=https%3A%2F%2Frollbar.com%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\))
