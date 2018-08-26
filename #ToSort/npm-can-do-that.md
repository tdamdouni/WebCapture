# NPM Can Do That?

_Captured: 2018-08-11 at 09:29 from [dzone.com](https://dzone.com/articles/npm-can-do-that?edition=387207&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-08-10)_

Deploying code to production can be filled with uncertainty. Reduce the risks, and deploy earlier and more often. [Download this free guide](https://dzone.com/go?i=278435&u=https%3A%2F%2Ftry.rollbar.com%2Flow-risk-continuous-delivery-guide%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\)) to learn more. Brought to you in partnership with [Rollbar.](https://dzone.com/go?i=278435&u=https%3A%2F%2Frollbar.com%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\))

![npm-can-do-that](https://briandesousa1.files.wordpress.com/2018/07/npm-can-do-that.png?w=267&h=164)

I have been using the NPM package manager for a few years and watched it rise, almost fall (to Yarn) and evolve into a fast, full-featured package manager and much more. Along the way there are a few simple tricks that have saved me a bunch of time.

## Viewing Available NPM Scripts

Picture this… you finally find some time to work on that little app or side project. It's been days or weeks since you last looked at the code. You open up Visual Studio Code, hit CTRL-` to open the integrated terminal and type _npm…_? Darn, you can't remember the command to build/run/debug/do something to your app. Time to crack open the package.json and see how it all works. Buzz kill. Wait, what about…

This command outputs a nicely formatted list of npm scripts that are available:

## Check for Outdated NPM Packages

Let's continue with the theme of opening up a side project that you haven't worked on for a while. We all know that NPM packages and JavaScript in general are evolving at light-speed. Here's a quick way of checking out how current your NPM packages are:

By default, this command presents the top-level NPM dependencies in your package.json (i.e. depth=0) in a nicely formatted table with information about the version you are currently using and the latest available version.

![npm_outdated](https://briandesousa1.files.wordpress.com/2018/07/npm_outdated.png)

> _Bonus tip: Add the -long option to see the package type:_

![npm_outdated_long](https://briandesousa1.files.wordpress.com/2018/07/npm_outdated_long.png)

## View All Available Versions of a Package

It has only been three hours since I upgraded my project's dependencies but thanks to `npm outdated` I can now see that most of my packages are already out of date. Hmm… how many versions of @angular/cli have been released since I stepped away for coffee?

But seriously, occasionally I need or want to see the released versions of a particular package available in the NPM public registry. Luckily I don't need to open a browser and navigate to the NPM registry website.

This command outputs a list of all the available versions of the package:

![npm_view.PNG](https://briandesousa1.files.wordpress.com/2018/07/npm_view.png)

> _Bonus Tip: If you have grep, you can use it to quickly filter out specific versions:_

![npm_view_grep.PNG](https://briandesousa1.files.wordpress.com/2018/07/npm_view_grep.png)

## Viewing an NPM Package's Code Repository

If I am working with an NPM package and I get stuck and need to look up documentation on how to use it, I would normally open a browser and search for the package. In most cases, I would land on the README file in the top-level directory of the package's code repository. What if there was a quick way to launch a package's source code repository in the browser from the command-line? Oh wait, there is:

This command will launch the launch the repository URL in your default browser (ex. <https://github.com/reactivex/rxjs>). Most packages published to NPM provide a repository URL in their package.json file.

## Don't Assume NPM Packages Are Installed Globally

The ability to quickly write short scripts in package.json to perform frequently used tasks from the command-line is fantastic. You should try not to assume that packages are installed globally when writing your scripts but you also certainly don't want to have to write long-form scripts like the one below to reference locally installed package binaries:

Luckily, NPM adds the _node_modules/.bin/ _folder to the path by default which means you can reference package binaries as if they are installed globally like this:

Install nodemon as a devDependency, reference the nodemon binary in your script, run the script, and away you go. This script will work for the next developer right out of the box (or clone?) without needing to globally install nodemon.

--

Those are just a few tips to consider when using NPM. There are plenty of other clever tricks that can help speed up your development process. This is especially true when you are using NPM within a tool like Visual Studio Code or via Node Version Manager (NVM).

What lesser-known NPM tricks do you use on a regular basis?

Deploying code to production can be filled with uncertainty. Reduce the risks, and deploy earlier and more often. [Download this free guide](https://dzone.com/go?i=278436&u=https%3A%2F%2Ftry.rollbar.com%2Flow-risk-continuous-delivery-guide%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\)) to learn more. Brought to you in partnership with [Rollbar.](https://dzone.com/go?i=278436&u=https%3A%2F%2Frollbar.com%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\))
