# Develop Your First Google Chrome Extension Using HTML and jQuery

_Captured: 2018-07-09 at 07:42 from [dzone.com](https://dzone.com/articles/develop-your-first-google-chrome-extension-using-h-1?edition=385213&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-07-08)_

Deploying code to production can be filled with uncertainty. Reduce the risks, and deploy earlier and more often. [Download this free guide](https://dzone.com/go?i=278435&u=https%3A%2F%2Ftry.rollbar.com%2Flow-risk-continuous-delivery-guide%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\)) to learn more. Brought to you in partnership with [Rollbar.](https://dzone.com/go?i=278435&u=https%3A%2F%2Frollbar.com%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\))

Chrome extensions are small programs (using HTML, JavaScript, jQuery), written basically to add additional functionality to the Chrome browser. You can download and find all Google Chrome Extensions in the Chrome Web Store (formerly the Google Chrome Extensions Gallery). As per Wikipedia, by February 2010 over 2,200 extensions had been published by developers.

If you check the Chrome web store, you will find a lot of Chrome extensions. You can check this out using this [link](https://chrome.google.com/webstore/category/extensions).

These Chrome extensions have a small UI which is mainly an HTML page and we can make it interactive by using JavaScript and jQuery.

There are 3 main parts in a Chrome extension. These are:

  1. _manifest.json._
  2. A JavaScript file.
  3. An HTML file.

Let's see what is _manifest.json_.

### manifest.json

Every Chrome app has a JSON file which is called _manifest.json_. This file contains the information related to the app in JSON format.

Here is a simple manifest file.

Basically, it contains metadata like name, description, what icon is used in the app, icon size, the HTML page being used, permissions, browser action, version, etc.

![Image title](https://dzone.com/storage/temp/9662986-im1.jpg)

### Browser Action

Browser action is used to show the Chrome app in the Google Chrome toolbar. It contains several properties like tooltip, badges, popup, etc.

![Image title](https://dzone.com/storage/temp/9662989-ext2.jpg)

### Permissions

While creating a Chrome extension, you may need to use some third-party libraries, the Chrome API, etc. So to include these in the project, we need permissions data. We can mention our permissions in _mainfest.json_. Here is an example showing the permissions in our _mainfest.json _file.

Now let's try to create a Chrome app using Visual Studio 2015. For a Chrome template in Visual Studio, you can download it from [this link ](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.GoogleChromeExtensionProjectTemplate)and install it.

After installing the Chrome Extension Project Template, restart Visual Studio.

Once you restart your VS, you will find the following template under C# projects.

![Image title](https://dzone.com/storage/temp/9663000-ext3.jpg)

Now select the Google Chrome extension and work on it.

![Image title](https://dzone.com/storage/temp/9663005-ext5.jpg)

Now go to the_ mainfest.json_ and add the following:

Here, I used a 128*128 image, labeled as `myimg`.

Now, in _Popup.html_, write the following HTML code.
    
    
          <script src="jquery-3.2.1.min.js"></script>
    
    
          <script src="popup.js"></script>
    
    
    <input type="text" id="txt_name" />

Now go to the _popup.js_ and write the following logic to show the alert.

Now all the tasks related to creating the app are done, so we will see how we can add the extension to the browser.

Here are the steps to do so:

  * Open the project in the File Explorer.
  * Copy the project in the desktop.
  * Now go to Chrome settings, then Extension.
![Image title](https://www.codeproject.com/KB/applications/1185723/41.JPG)

Now click on the Load Unpack extension button and find your extension project on the desktop.

![Image title](https://www.codeproject.com/KB/applications/1185723/01.JPG)

After loading, it will appear in the top right corner of your browser, and you can access it by clicking it. You can play with it by typing your name.

![Image title](https://www.codeproject.com/KB/applications/1185723/ee.JPG)

Now click on the small icon which will appear on the top right side of the Chrome browser. It will start the app and will work as per your logic.

![Image title](https://www.codeproject.com/KB/applications/1185723/56.JPG)

So in this way, we can just start creating a small Chrome app. For Chrome, there are lots of apps in the Chrome store. If you want to visit the chrome store, please click this [link](http://chrome.google.com/webstore/category/extensions).

![Image title](https://dzone.com/storage/temp/9663016-ext8.jpg)

Deploying code to production can be filled with uncertainty. Reduce the risks, and deploy earlier and more often. [Download this free guide](https://dzone.com/go?i=278436&u=https%3A%2F%2Ftry.rollbar.com%2Flow-risk-continuous-delivery-guide%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\)) to learn more. Brought to you in partnership with [Rollbar.](https://dzone.com/go?i=278436&u=https%3A%2F%2Frollbar.com%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\))
