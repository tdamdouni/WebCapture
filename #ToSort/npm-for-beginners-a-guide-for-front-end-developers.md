# npm for Beginners: A Guide for Front-end Developers

_Captured: 2017-02-17 at 15:36 from [www.impressivewebs.com](https://www.impressivewebs.com/npm-for-beginners-a-guide-for-front-end-developers/)_

Unless you've been under a transpiler-sized rock for the past five years or you're an absolute beginner to front-end coding, then you've probably heard of [npm](https://www.npmjs.com/).

Maybe you've clicked through to the GitHub repo of a tool of some kind, and you noticed the installation instructions had a couple of different possibilities, including something like this:
    
    
    npm install some-tool
    

In addition to that, there's usually something like "download the script and include it at the bottom of your page using `<script>` tags". Many of you probably go for that latter option.

There are tons of developers that have incorporated npm in some way into their workflow. But I'm guessing there are just as many developers and new front-end folks who are confused about what npm is, and why you'd want to use it.

I've been doing some extra reading and research on this subject, and I thought I would walk through most of what I've learned in this tutorial. While I don't consider myself a super-expert in all the subtleties related to npm, I do think this npm tutorial should serve as a good starting point for those who have little or no knowledge of the subject and its benefits for front-end projects.

## What is npm?

In brief, npm (stylized in lowercase, so it's not correct to write it as "NPM") is a package manager for JavaScript. It stands for _Node Package Manager_. The official documentation [explains](https://docs.npmjs.com/getting-started/what-is-npm) that npm is three different things:

  1. The website
  2. The npm registry
  3. The npm client

**The website** is a place where you can browse packages, read the docs, and find general info on npm.

**The registry** is a database that holds the information and the code for the packages.

**The npm client** is a tool installed on a developer's machine that allows you to publish packages, install packages, and update packages.

_Note: A "package" is just another way of saying "JavaScript plugin" or "module". It's a bit of a buzzword, but it's an appropriate term because often packages consist of multiple files._

The rest of this article will go into more detail on the npm registry and using the npm client, but the video below is a good starting point too:

## Installing Node.js and the npm Client

One of the things that's somewhat intimidating to designers and those who don't come from a strong programming background is the fact that npm is used via the command line. But it's really not that big a deal for the purposes of just doing some basic package installing and updating.

To start using npm, you have to do two things:

  1. Install the npm client

Fortunately, when you install Node, the default installation settings will install the client too, so you can do both these steps in one shot. You may have Node installed on your machine already. To find out if this is the case, type the following in the command prompt, which spits out the version number for your Node installation:
    
    
    node --version
    

In my case, when I started writing this article, I was at version 0.10.29, which was released in [June of 2014](https://github.com/nodejs/node/blob/master/doc/changelogs/CHANGELOG_V010.md#0.10.29). Seeing as the latest version is at 7.x, it was clearly time for an upgrade. If you do a clean install, you'll have the option to install either the "recommended for most users" version (currently 6.9.4 LTS) or the version with the latest features (which I assume is similar to a nightly build).

For the purposes of just getting up and running to learn how to use npm for front-end development, I'd say install the recommended version. As mentioned, when you install Node.js, the installer will automatically install the npm client.

As pointed out in the above video, after you install node along with the npm client, it's possible that the npm client will be out of date. To ensure you have the latest npm client, do the following (as weird as this looks):
    
    
    npm install npm --global
    

That command says "use the npm client to install npm". The `\--global` part is a flag that tells the client that you want to install it globally (more on flags later). When that's done, you can check the version number of your npm client:
    
    
    npm --version
    

In my case, after updating my client, I was at version 4.0.5. To confirm that your version is the latest, you can [view the releases on GitHub](https://github.com/npm/npm/releases). The last version with a green "Latest Release" label on it is the one your system will update to if all goes well.

## Using npm to Install Packages

The above instructions need to be followed only once, of course, and then you'll be ready to use npm on your machine for all projects. But it's somewhat annoying to have to do all that when it's simple enough to just download a script or plugin manually or include it using [a CDN link](https://cdnjs.com/). In a way, front-end development feels like [a Rube Goldberg machine](https://en.wikipedia.org/wiki/Rube_Goldberg_machine) - we're jumping through all these hoops to do simple tasks. But, as I'll discuss later in this article, npm has some significant advantages over the traditional way of using scripts. So it's not as bad as it might seem at first glance.

In the meantime, let's look at how you can use npm to add JavaScript modules and other packages to your projects.

As I mentioned at the beginning of this post, even if you've never used npm, you've probably seen it when you look up some kind of tool on GitHub, or on that tool's documentation site. For example, let's say you're interested in trying out [Modaal](http://humaan.com/modaal/), the popular accessibile modal window plugin. In addition to the usual way to install it (download the script, include the CSS manually, etc.) developers have the option to install it via the command line using npm:
    
    
    npm install modaal
    

This option is available for any tool in the npm registry. So this might be where many front-end folks, designers learning to code, and web development beginners might have some trouble. For example, when I first saw one of those npm install commands, my first reaction was twofold:

  1. Where do I run this command (i.e. which directory)?
  2. Specifically what does this do?

To answer that first question, remember that earlier when I installed npm, I used the `\--global` flag. If you're installing something globally on your system, then you don't need to worry about what directory you're in. But in the case of something like Modaal, you want to install it in the directory of the project that's going to use it.

So let's say you have a project called "Photo Gallery", which might be a photo gallery app you're building. That project might live in a directory called `photo-gallery`. Using the command line, [you'll navigate](http://www.digitalcitizen.life/command-prompt-how-use-basic-commands) to the `photo-gallery` folder and exucute the command I showed you above to install the Modaal plugin (or any other package you want to install).

This alone is a nice time-saver. You don't have to download the files yourself, you don't have to figure out if the files need to be combined, you don't have to worry about any missing CSS files - the whole thing gets pulled down from the npm registry using a single command.

Now here's where things get a little sticky for front-end developers.

## What Does `npm install` Do?

From the perspective of a front-end developer or designer who wants to drop a script into a project and start writing code, the way npm installs packages is a little strange and not as plug-and-play as you'd like.

In the case of my fictional `photo-gallery` app, what happens when I use npm to install Modaal? Here's the resulting folder structure:
    
    
    ├── photo-gallery/
    └───── node_modules/
            └───── modaal/
                    ├───── demo/
                    │       ├───── css/
                    │       ├───── img/
                    │       └───── js/
                    ├───── dist/
                    │       ├───── css/
                    │       └───── js/
                    └───── source/
                            ├───── css/
                            └───── js/
                                   └───── lib/
    

In this example I left out the files inside the directories, so this is only the folders. As you can tell, this is a little confusing. You might wonder:

  * Why is everything inside a `node_modules` folder?
  * What's the difference between `dist` and `source`? What is `lib`?
  * Can I just point to the files inside `node_modules`? Or do I have to manually move them up to the root of my project folder? If I have to move them, then why even bother using npm to install the whole thing?

These are legitimate concerns, and these are actually questions I've asked and that I've researched to help me understand why npm works like this. So I'm going to try to explain things as best I can, based on my research, testing, and experimenting.

## dist/, src/, and lib/

First of all, the difference between the `dist/` and `src/` directories, [as explained in this Stack Overflow thread](http://stackoverflow.com/questions/23730882/what-is-the-role-of-src-and-dist-folders), is:

  * `src/` (or `source/`), is the raw code that you would read and/or edit, before any minification, concatenation, or other compilation tasks.
  * `dist/` means "distribution", and is the minified and/or concatenated version of the code that would be deployed to your production sites.

For the most part, these are matters outside the scope of npm in general. This is more about code and project architecture. Modaal has chosen to follow this pattern. Not all packages installed via npm are going to have this structure, but it might be good to be familiar with these concepts if you're just getting started with managing front-end dependencies.

As for the `lib/` folder, "lib" stands for "libraries". That's where Modaal has chosen to put its own dependencies. In this case, the only dependency is jQuery. Again, you might see a slightly different structure in other cases.

If you install Modaal yourself, you'll notice that installing it via npm brings down these folders and a whole bunch of other stuff too, not just the files you plan to include in your project.

## What's With the `node_modules` Folder?

In order to understand why npm throws everything into a directory called `node_modules`, you have to first understand that npm is, first and foremost, a package manager for developers who write JavaScript on the server. That is, Node.js developers.

When a Node.js developer wants to use a package in their project, it's more or less a two-step process. First, they install the package via npm, then they include it in their project with a line like this in their JavaScript:
    
    
    let examplePackage = require('example-package');
    

Using the `require()` function makes their script look inside the `node_modules` folder for that specific package, or module. You could think of this like an include file in PHP, if you're familiar with that. Or, closer to home, like a function reference in client-side JavaScript (which is more or less what this is). The above example will expose the `examplePackage` variable as an API that uses the functionality of the `example-package` module, whatever that is.

And please note that Node.js (i.e. server-side JavaScript) is not my area of expertise. This is my attempt at a basic overview of what is happening, to help you understand why front-end packages installed via node work the way they do. Feel free to correct me if I've misstated anything here.

If you want to read up a little more about npm, folders, and the `node_modules` directory you can do so [in the npm docs](https://docs.npmjs.com/files/folders).

## How Does the `node_modules` Folder Work on the Front-end?

Here's where things get a little complex if you're using npm to install and use stuff exclusively for client-side scripting, or even for CSS. Yes, npm can be used to install basically anything that you use on the front-end, including CSS-only packages. Let's use a popular example.

In the fictional `photo-gallery` project, if I decide I want to include [Normalize.css](https://necolas.github.io/normalize.css/), the ubiquitous CSS reset alternative, I would do this:
    
    
    npm install normalize.css
    

Now I'll have the following additional resources in my app's directory structure:
    
    
    ├── photo-gallery/
    └───── node_modules/
            └───── normalize.css/
                     ├───── CHANGELOG.md
                     ├───── LICENSE.md
                     ├───── normalize.css
                     ├───── package.json
                     └───── README.md
    

These would be in addition to the Modaal resources previously installed, but I've left those out for brevity. As you can see, a folder called `normalize.css` has been created, and inside that folder are five different files. The one I'm most interested in is `normalize.css`.

So how exactly do I use this file? If I leave it where it is, then I'm going to have to do the following with my `<link>` element in my HTML:
    
    
    <link rel="stylesheet" href="node_modules/normalize.css/normalize.css">
    

That's ugly and not great to work with. And that's besides the fact that I commonly put all my CSS files in a `css` folder at the root of my project. Also, I don't care about all that other stuff that's installed; I want only the CSS.

At this point, unless I know any better, the only option is to copy the CSS file from inside `node_modules/normalize.css/` and paste it into my `css` folder. From there, I might have a build process in place that combines and minifies my CSS (more on this later).

Here would be a good place to discuss why using npm is better than just grabbing stuff directly from repos and whatnot. But before I do that, there's something else I've omitted so far that I should explain.

## Installing Packages with Optional Flags

When I installed Modaal and Normalize.css, in both cases I just did a clean `npm install [package]` with no other commands. What I should have done is this:
    
    
    npm install [package-name] --save
    

The difference being the addition of the `\--save` flag. In order for this to be useful, I need to [create a package.json file](https://docs.npmjs.com/getting-started/using-a-package.json) at the root of my project folder. The easiest way to do this is using the following command, which I would execute in the terminal inside my project folder:
    
    
    npm init
    

This command will initialize a package.json file for me, creating it in the root of my project folder, and ask me to add some info to the file. Assuming I had not yet installed any packages, my package.json file should look something like this after I answer all the questions prompted by the `init` command:
    
    
    {
      "name": "photo-gallery",
      "version": "1.0.0",
      "description": "My photo gallery app.",
      "main": "index.js",
      "dependencies": {},
      "devDependencies": {},
      "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
      },
      "author": "Louis Lazaris <my@email.address> (https://www.impressivewebs.com/)",
      "license": "MIT"
    }
    

Now I'll add the two packages, this time installing them along with the `\--save` flag:
    
    
    npm install modaal normalize.css --save
    

As a shortcut, I've installed them both using a single command. Because I added the `\--save` flag, this will update my package.json file. Here's what it looks like now:
    
    
    {
      "name": "photo-gallery",
      "version": "1.0.0",
      "description": "My photo gallery app.",
      "main": "index.js",
      "dependencies": {
        "modaal": "^0.3.1",
        "normalize.css": "^5.0.0"
      },
      "devDependencies": {},
      "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
      },
      "author": "Louis Lazaris <my@email.address> (https://www.impressivewebs.com/)",
      "license": "MIT"
    }
    

Notice the "dependencies" section has been updated to include the two packages I just installed. If I didn't use the `\--save` flag, then the packages would be installed without listing them as dependencies.

Another flag commonly used when installing packages is `\--save-dev`. This adds the package to the "devDependencies" section of package.json. The difference, [as explained in this Stack Overflow thread](http://stackoverflow.com/questions/22891211/what-is-difference-between-save-and-save-dev), is that `\--save` is used for packages that are required for your app to run, while `\--save-dev` is for packages used for development purposes (linting, unit tests, and so forth).

Another thing I should mention here is that all the flags I've used in the examples in this post have abbreviated versions. So:

  * `\--version` can be written as `-v`
  * `\--global` as `-g`
  * `\--save` as `-S`
  * `\--save-dev` as `-D`

Note that the "s" and "d" for "-save" and "-save-dev" are uppercase. There are other flags that use lowercase "s" and "d". You can see [a full list of flag shortcuts here](https://docs.npmjs.com/misc/config#shorthands-and-other-cli-niceties).

## Benefits of npm: Replicating Builds

As I mentioned earlier, there are benefits to using npm to install packages as opposed to just grabbing the files manually.

First of all, when packages are identified as dependencies in my package.json file (i.e. by installing them using the `\--save` flag), this means I can share my project with another developer and that developer will be able to reproduce the full project, with dependencies, using a single command:
    
    
    npm install
    

So if someone has a copy of `photo-gallery`, but doesn't have the dependencies installed, all they have to do is navigate to the `photo-gallery` directory and run the above command. As long as package.json lists the dependencies, they will be installed automatically. This could mean dozens, or maybe even hundreds of packages can be installed with a single command.

As an example, if you used Git to grab a copy of [UglifyJS2](https://github.com/mishoo/UglifyJS2), it wouldn't work unless you first used npm to install the dependencies (in this case, there are [currently 4 listed in its package.json file](https://github.com/mishoo/UglifyJS2/blob/48284844a461e6113bb9911cdcdad7ab8a3d85de/package.json#L31-L35)). The dependencies don't live in the GitHub repo for that project but npm allows you to grab them all using that single command (`npm install`).

You could mimic this behavior locally by deleting the `node_modules` folder in any project and then doing `npm install` in the root of that project. All that's required is that you have the dependencies listed inside package.json, and they'll be pulled in automatically.

## Benefits of npm: Updating Packages

Another benefit of using npm is that it allows you to update any package to a newer version with a single command.

For demonstration purposes, let's say I was using Normalize.css version 4.0.0. If I want to update Normalize.css, I simply have to run:
    
    
    npm update normalize.css --save
    

But hold on! In this case, I didn't get the latest version of Normalize.css (which, as of this writing, is 5.0.0); I got version 4.2.0.

When you update a package with npm, you're not updating to the latest version; you're updating to the latest version that will not have potentially breaking changes. This is recognized by the npm client by means of the version number, which uses [Semantic Versioning](http://semver.org/), or SemVer. A detailed discussion of Semantic Versioning is beyond the scope of this article, but developers are encouraged to use this method of versioning for this reason. [Hugo's article on the subject](https://www.sitepoint.com/semantic-versioning-why-you-should-using/) might be a good place to start if you're not familiar with SemVer.

If I want to view version details on all my project's out-of-date dependencies, I can use [the outdated command](https://docs.npmjs.com/cli/outdated):
    
    
    npm outdated
    

Running that command inside a project directory will output something like this in my terminal:
    
    
    Package        Current  Wanted  Latest  Location
    normalize.css    4.0.0   4.2.0   5.0.0  photo-gallery
    

For full details on what all that means, see [npm-outdated in the npm docs](https://docs.npmjs.com/cli/outdated). But in a nutshell, the "Current" column tells me what version is installed as a dependency; the "Wanted" column tells me what version I'll be able to update to safely (using `npm update`); and the "Latest" column tells me the most up to date version that lives in the npm registry. If I had other out-of-date dependencies, those too would be listed. But in this case, I had only Normalize.css. My Modaal installation was the most up to date version as of this writing.

As a side point here, what if I want to be able to update to the latest version of a package, even if it's a major version update with potentially breaking changes? I do this by changing my package.json file's dependencies to look like this:
    
    
    "dependencies": {
      "modaal": "^0.3.1",
      "normalize.css": "*"
    },
    

Notice instead of a version number for Normalize.css, I've included an asterisk symbol. This tells the npm client that I'm willing to accept major version upgrades, regardless of breaking changes. For Modaal, I've kept it the same, so it won't install a major release if I update later. Now if I run `npm outdated` I get the following:
    
    
    Package        Current  Wanted  Latest  Location
    normalize.css    4.0.0   5.0.0   5.0.0  photo-gallery
    

There's a lot more to discuss when it comes to version numbers and npm, and it's certainly something I'm getting more familiar with. In the meantime there's more info, including a screencast on this subject, [in the npm docs](https://docs.npmjs.com/getting-started/semantic-versioning).

## Benefits of npm: Productivity for Teams

As explained [in the npm docs](https://docs.npmjs.com/getting-started/what-is-npm):

> [npm] makes it possible for your team to draw on expertise outside of your organization by bringing in packages from people who have focused on particular problem areas. But even if you don't reuse code from people outside of your organization, using this kind of module based approach can actually help your team work together better, and can also make it possible to reuse code across projects.

This sort of thing is still possible using manual copy-and-include methods, but that's just not practical for a growing code base and across a team of developers.

So npm will allow you to not only use other people's code available on the npm registry, but it's an easy way to track dependencies and reuse code across different projects.

In short, npm encourages modular code. [Wes Bos explained the benefits of modules nicely](http://wesbos.com/javascript-modules/):

> JavaScript modules allow us to chunk our code into separate files inside our project or to use open source modules that we can install via npm. Writing your code in modules helps with organization, maintenance, testing, and most importantly, dependency management.

Although he was specifically writing about [ES6 Modules](http://caniuse.com/#feat=es6-module), the same basic principle applies: It's easier to deal with code that's separated into pieces, like building blocks. And the npm ecosystem encourages this type of coding.

## Getting Back to the `node_modules` directory

Earlier I discussed the `node_modules` folder and the fact that every package gets installed in that location. It's clear that from a front-end perspective, this isn't the most practical setup. And the folks at npm [have acknowledged as much](http://blog.npmjs.org/post/101775448305/npm-and-front-end-packaging):

> This is a pretty obvious problem. The `node_modules` folder is where npm puts packages by default, to take advantage of the Node.js module loading semantics. Depending what packages you install, packages end up in different places in the tree. This works great for Node, but HTML and CSS, for better or worse, generally expect things to be in one location, like `/static/mypackage`. There are workarounds for this to be sure, but no first-class solution yet.

Ideally, I'd like to have a solution that allows my build process to use the stuff inside `node_modules` to create my production build. This would mean my CSS dependencies get combined and minified inside a `css/` folder inside my project root, while JavaScript dependencies get bundled inside `js/`. Meanwhile, `node_modules` should be completely invisible from a production perspective.

From what I've researched, there are some solutions that you can consider, many of which require an extra tool or two.

## Using Tools like Browserify and webpack

Kyle Robinson Young wrote about this subject [back in 2013](http://dontkry.com/posts/code/using-npm-on-the-client-side.html). He said:

> In order to use node modules on the browser you will need a build tool. This might bother you. If this is a deal breaker then by all means continue wasting your life copying and pasting code and arranging your script tags.

Kyle then goes on to recommend [Browserify](http://browserify.org/) for this purpose. I had seen lots of things about Browserify before but until I started researching this subject I didn't know exactly how it would be beneficial. Remember earlier when I mentioned that the `node_modules` folder makes sense for Node.js development (that is, server-side JavaScript)? Well, the Browserify website describes the tool as follows:

> Browserify lets you require('modules') in the browser by bundling up all of your dependencies.

So the idea is that you get the exact same benefit but you don't have to worry about having to move stuff out of `node_modules` manually. The only problem here is that this doesn't seem to be a good solution for bundling up CSS. Maybe someone with experience using Browserify can chime in and explain their process.

Another potential solution is to try [webpack](https://webpack.github.io/), another module bundler originally designed for bundling JavaScript modules. The [getting started guide](http://webpack.github.io/docs/tutorials/getting-started/) in their documentation has [a section on adding CSS](http://webpack.github.io/docs/tutorials/getting-started/#first-loader) to your app. There it's recommended to use the [css-loader](https://github.com/webpack/css-loader) and [style-loader](https://github.com/webpack/style-loader) webpack plugins to help with this.

## Using Grunt for Simple Bundling

If something like Browserify or webpack is a little too much for you, then you could consider a simple [Grunt](http://gruntjs.com/) task that bundles up your JavaScript and/or CSS modules and dependencies by means of some manual configuration.

For example, you could do something like [what's described in this Stack Overflow thread](http://stackoverflow.com/questions/28749396/referencing-resources-in-node-modules-folder/28901884#28901884), which uses the [grunt-contrib-copy](https://github.com/gruntjs/grunt-contrib-copy) plugin.

This is a pretty common solution, but I don't think there's an easy way to use Grunt to automatically bundle up your CSS files from installed packages, without either copying the packages from the `node_modules` folder or manually finding each one to configure what gets copied, concatenated, and minified for production.

## More on Bundling Modules and Dependencies

Installing and maintaining CSS dependencies via npm might require more work than it's worth, but you'll have to decide based on looking into some of the above technologies.

I might write more about this in a future post, but in the meantime here are some further resources and tools that could help:

  * [modules-webmake](https://github.com/medikoo/modules-webmake) - An alternative to Browserify, some say it's simpler to use.
  * [browserify-css](https://www.npmjs.com/package/browserify-css) - A Browserify transform for bundling, rebasing, inlining, and minifying CSS files.

## The tl;dr Summary…

I covered a lot in this article, but a bullet list of the main ideas might help a little:

  * npm is used to install and manage packages, usually JavaScript modules and sometimes even CSS
  * Creating a package.json file (initialized with `npm init`) in a project's root will allow you to manage your dependencies and keep them up to date
  * The `\--save` flag helps keep package.json updated when you add, remove, or update a dependency
  * Using npm to install and manage dependencies is far superior to the manual download-and-include method
  * A tool like Browserify or webpack can help when dealing with packages strictly for front-end builds
  * Bundling CSS files in packages is challenging

## Final Words from a Non-expert

I've been meaning to research and brush up on my knowledge in these areas for some time, so I thought it would be good to document everything I've learned so other front-end developers can benefit from it too. The extensive post above is what I've come up with.

If you have some experience in dealing with npm and how it relates to front-end development, feel free to comment and let me know if anything I've said needs to be corrected or improved. And more importantly, if you've managed to find a hassle-free solution to bundling front-end dependencies that includes CSS (maybe using Browserify or webpack?) I'd love to hear how you're currently solving that problem.
