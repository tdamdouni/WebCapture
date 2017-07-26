# Installing Node.js Tutorial: MacOS

_Captured: 2017-02-03 at 13:57 from [dzone.com](https://dzone.com/articles/installing-nodejs-tutorial-macos)_

Just like any programming language, platform, or library, getting up and running with Node.js takes some initial setup before you can start hacking away. With Node.js, the only initial setup required is, quite simply, getting the binary installed.

In this brief tutorial, we'll take a quick look at how to get Node.js on MacOS. Once we've completed the entirety of the tutorial, you'll be ready to take the next step with Node.js.

This guide covers installing Node.js on the following versions of OS X and MacOS: OS X 10.10 (Yosemite), OS X 10.11 (El Capitan), and MacOS 10.11. These are the versions that are consistently tested and supported by the Node.js build process at the time of writing.

## Step 0: The Quick Guide (TL;DR) to Get Node.js Installed on MacOS

Here's the abbreviated guide, highlighting the major steps:

  1. Go to the [Node.js Downloads page](https://nodejs.org/en/download/)
  2. Download Node.js for MacOS by clicking the "Macintosh Installer" option
  3. Run the downloaded Node.js `.pkg` Installer
  4. Run the installer, including accepting the license, selecting the destination, and authenticating for the install.
  5. You're finished! To ensure Node.js has been installed, run `node -v` in your terminal - you should get something like `v6.9.4`

## Step 1: Download the Node.js `.pkg` Installer

As our first step, we need to actually _get_ the official installer for Node.js on MacOS. To do so, we can head over to the [Node.js Downloads page](https://nodejs.org/en/download/) to download the installer.

You can get the MacOS installer by clicking the `Macintosh Installer` option - this will download the `.pkg` installer for Node.js. Make sure you save it somewhere that you'll be able to access it!

## Step 2: Run the Node.js Installer

Now that you've got the installer downloaded, you'll need to run it. The installer is a pretty typical interface - it won't take long to get through it (under a minute), even though there are a few parts to it. You can get through it by following the guide below:

  * Introduction 
    * Select `Continue`
  * License 
    * Select `Continue`
    * Select `Agree`
  * Installation Type 
    * Select `Install`
    * Authenticate with your Mac to allow the Installation
    * Select `Install Software`
  * Summary 
    * Select `Close`

## Step 3: Verify That Node.js Was Properly Installed

To verify that Node.js was installed correctly on your Mac, you can run the following command in your terminal:

If Node.js was properly installed, you'll see something close to (but probably not _exactly_) this:

## Step 4: Update Your npm Version

As one last step for good measure, we'll update your version of npm.

Node.js always ships with a specific version of npm - Node.js doesn't (and shouldn't!) automatically update npm. The npm releases aren't synced with Node.js releases. Because of this, there's almost _always_ a newer version of npm than the one that is installed by default with a given version of Node.

To easily update your version of `npm`, you can run the following command:

## Step 6: Start Building With Node.js!

Now you've got Node.js on your Mac. It's time to start exploring!

Thankfully, we've got your back. We've got a ton of articles on getting started with Node.js! If you're interested in exploring ES6, you should check out our article on [some of the most exciting ES6 features in Node.js](https://nodesource.com/blog/six-of-the-most-exciting-es6-features-in-node-js-v6-lts). Looking for ways to standardize your JavaScript code across your team? In that case, you should check out our guide to [using ESLint to build code standards in Node.js applications](https://nodesource.com/blog/streamline-javascript-development-with-eslint). Maybe you'd just like to start deploying your applications? In that case, check out our guide on [deploying Node.js apps with systemd](https://nodesource.com/blog/running-your-node-js-app-with-systemd-part-1)!

That said, if you want to keep in touch with Node.js and the surrounding ecosystem, you should go follow [@NodeSource](http://twitter.com/nodesource) on Twitter! We'll keep you updated with important news from the Node.js project, and share the best Node.js tutorials, guides, and tools that the community has to offer!
