# An Absolute Beginner's Guide to Using npm

_Captured: 2017-03-01 at 02:59 from [dzone.com](https://dzone.com/articles/an-absolute-beginners-guide-to-using-npm-1?edition=271922&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-28)_

[Start coding today](https://dzone.com/go?i=155124&u=http%3A%2F%2Fplayground.qlik.com%2Fhome) to experience the powerful engine that drives data application's development, brought to you in partnership with [Qlik](https://dzone.com/go?i=155124&u=http%3A%2F%2Fplayground.qlik.com%2Fhome).

Using npm effectively is a cornerstone of modern web development, no matter if it's exclusively with Node.js, as a package manager, a build tool for the front-end, or even as a piece of workflows in other languages and on other platforms.

_Really_ understanding npm as a tool, understanding the core concepts, can be something that's difficult for a beginner - I spent many hours just trying to figure out small details that would seem minor or be taken for granted by others.

As such, I've written up a basic and **detailed** guide for understanding npm, for those who are entirely new to Node.js, npm, and the surrounding ecosystem.

## An Absolute Beginner's Guide to `package.json`

As a general rule, any project that's using Node.js will need to have a `package.json` file. What is a `package.json` file?

At its simplest, a `package.json` file can be described as a manifest of your project that includes the packages and applications it depends on, information about its unique source control, and specific metadata like the project's name, description, and author.

Let's break down the core parts of a typical `package.json` file:

### Specific Metadata: Name, Version, Description, License, and Keywords

Inside a package.json, you'll almost always find metadata specific to the project - no matter if it's a web application, Node.js module, or even just a plain JavaScirpt library. This metadata helps identify the project and acts as a baseline for users and contributors to get information about the project.

Here's an example of how these fields would look in a package.json file:

A `package.json` file is _always_ structured in the [JSON](http://www.json.org/) format, which allows it to be easily read as metadata and parsed by machines.

If needing to format a `package.json` file manually to get your project up and running seems a bit daunting, there's a handy command that will automatically generate a base `package.json` file for you - if you'd like to learn how to use it, take a peek at the `npm init` instructions below!

### Understanding and Managing Your Project's Dependencies: `dependencies` and `devDepenendcies` in Your `package.json`

The other majorly important aspect of a `package.json` is that it contains a collection of any given project's dependencies. These dependencies are the modules that the project relies on to function properly.

Having dependencies in your project's `package.json` allows the project to install the versions of the modules it depends on. By running an install command (see the instructions for `npm install` below) inside of a project, you can install _all_ of the dependencies that are listed in the project's `package.json` \- meaning they don't have to be (and almost never should be) bundled with the project itself.

Second, it allows the separation of dependencies that are needed for production and dependencies that are needed for development. In production, you're likely not going to need a tool to watch your CSS files for changes and refresh the app when they change. But in both production and development, you'll want to have the modules that enable what you're trying to accomplish with your project - things like your web framework, API tools, and code utilities.

What would a project's `package.json` look like with `dependencies` and `devDependencies`? Let's expand on the previous example of a `package.json` to include some.

One key difference between the dependencies and the other common parts of a `package.json` is that they're both objects, with multiple key/value pairs. Every key in both `dependencies` and `devDependencies` is a name of a package, and every value is the version range that's acceptable to install (according to Semantic Versioning - to learn more about Semantic Versioning, also known as semver, check out our [primer on semver](https://nodesource.com/blog/semver-a-primer/)).

## The Essential npm Commands

When using npm, you're most likely going to be using the command line tool for the majority of your interactions. As such, here's a detailed rundown of the commands that you'll encounter and need to use most frequently.

### Using `npm init` to Initialize a Project

The `npm init` command is a step-by-step tool to scaffold out your project. It will prompt you for input for a few aspects of the project in the following order:

  * The project's name.
  * The project's initial version.
  * The project's description.
  * The project's entry point (meaning the project's main file).
  * The project's test command (to trigger testing with something like [Standard](https://github.com/feross/standard)).
  * The project's git repository (where the project source can be found).
  * The project's keywords (basically, tags related to the project).
  * The project's license (this defaults to ISC - most open-source Node.js projects are MIT).

It's worth noting that if you're content with the _suggestion_ that the `npm init` command provides next to the prompt, you can simply hit `Return` or `Enter` to accept the suggestion and move on to the next prompt.

Once you run through the `npm init` steps above, a `package.json` file will be generated and placed in the current directory. If you run it in a directory that's not exclusively for your project, don't worry! Generating a `package.json` doesn't really _do_ anything, other than creating a `package.json` file. You can either move the `package.json` file to a directory that's dedicated to your project, _or_ you can create an entirely new one in such a directory.

#### How to use `npm init`:

### Using `npm init --yes` to _Instantly_ Initialize a Project

If you want to get on to building your project, and don't want to spend the (albeit brief) time answering the prompts that come from `npm init`, you can use the `\--yes` flag on the `npm init` command to automatically populate all options with the default `npm init` values.

> **Note:** You can configure what these default values are with the npm configuration - that's a more advanced topic, and outside the scope of this beginner's guide to npm. 
> 
> That said, if you're interested in setting that up, you can learn how to set these defaults in the eleventh tip of our [npm tricks](https://nodesource.com/blog/eleven-npm-tricks-that-will-knock-your-wombat-socks-off) article.

## Install Modules with `npm install`

Installing modules from npm is one of the most basic things you should learn to do when getting started with npm. As you dive deeper, you'll begin to learn some variations on installing modules, but here's the very core of what you need to know to install a standalone module into the current directory:

In the above command, you'd replace `<module>` with the name of the module you want to install. For example, if you want to install Express (the most used and most well known Node.js web framework), you could run the following command:

The above command will install the `express` module into `/node_modules` in the current directory. Whenever you install a module from npm, it will be installed _into_ the `node_modules` folder.

In addition to triggering an install of a single module, you can actually trigger the installation of _all_ modules that are listed as `dependencies` and `devDependencies` in the `package.json` in the current directory. To do so, you'll simply need to run the command itself:

Once you run this, npm will begin the installation process of all of the current project's dependencies.

As an aside, one thing to note is that there's an alias for `npm install` that you may see in the wild when working with modules from the ecosystem. The alias is `npm i`, where `i` takes the place of `install`.

This seemingly minor alias is a small gotcha for beginners - including myself, several times when I was learning - to the Node.js and npm ecosystems, as there's not a standardized, single way that module creators and maintainers will instruct on how to install their module.

#### Usage:

### Install Modules and Save Them to Your `package.json` as a Dependency

As with `npm init`, the `npm install` command has a flag or two that you'll find useful in your workflow - it'll save you time and effort with regard to your project's `package.json` file.

When you're running `npm install` to install a module, you can add the optional flag `\--save` to the command. This flag will add the module as a dependency of your project to the project's `package.json` as an entry in `dependencies`.

#### Usage:

### Install Modules and Save Them to Your `package.json` as a Developer Dependency

There's a flag that is nearly an exact duplicate, in terms of functionality, of the `\--save` flag when installing a module: `\--save-dev`. There are a few a key differences between the two - instead of saving the module being installed and added to `package.json` as an entry in `dependencies`, it will save it as an entry in the `devDependencies`.

The semantic difference here is that `dependencies` are for use in production - whatever that would entail for your project. On the other hand, `devDependencies` are a collection of the dependencies that are used in _development_ of your application - the modules that you use to build it, but don't need to use when it's _running_. This could include things like testing tools, a local server to speed up your development, and more.

### Install Modules Globally on your System

The final, and most common, flag for `npm install` that you should are the flags to install a module globally on your system.

Global modules can be extremely useful - there are tons tools, utilities, and more for both development and general usage that you can install globally to use.

To install a module from npm globally, you'll simply need to use the `\--global` flag when running the install command to have the module install globally, rather than locally (to the current directory).

> **Note:** One caveat with global modules is that, by default, npm will install them to a system directory, not a local one. With this as the default, you'll need to authenticate as a privileged user on your system to install global modules.
> 
> As a best practice, you should change the default installation location from a system directory to a user directory. If you'd like to learn to do this, take a peek at the seventh tip in our [npm tricks](https://nodesource.com/blog/eleven-npm-tricks-that-will-knock-your-wombat-socks-off) article!

## Want to keep going?

If you want to keep learning about npm and all its facets, I've got a few awesome things for you. A bit ago, we shared a few [npm tricks to knock your wombat socks off](https://nodesource.com/blog/eleven-npm-tricks-that-will-knock-your-wombat-socks-off). Even better, we wrote a follow-up with [even more npm tricks](https://nodesource.com/blog/seven-more-npm-tricks-to-knock-your-wombat-socks-off). This beginner's guide is a great springboard to get off the ground, and both of those will help you start optimizing your work with npm. If you'd like to go even further with npm and start deploying Node.js apps and npm modules into production, you should _definitely_ take a look at [NodeSource Certified Modules](https://certified.nodesource.com/) \- it's an awesome tool that'll compliment your newly acquired npm skills!

[Create data driven applications](https://dzone.com/go?i=155123&u=http%3A%2F%2Fplayground.qlik.com%2Fhome) in Qlik's free and easy to use coding environment, brought to you in partnership with [Qlik](https://dzone.com/go?i=155123&u=http%3A%2F%2Fplayground.qlik.com%2Fhome).
