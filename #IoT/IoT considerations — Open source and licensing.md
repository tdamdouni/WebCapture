# IoT considerations — Open source and licensing

_Captured: 2016-03-25 at 01:01 from [medium.com](https://medium.com/lattice-research/iot-considerations-open-source-and-licensing-44208c7469cb)_

![](https://cdn-images-1.medium.com/max/2000/1*28Q_PDRN1sm3qID-Q-0GRQ.png)

If you wanted to build a custom-designed car in your own garage, you probably wouldn't set out by designing a gearbox, engine and suspension components. So why should you do the same for your IoT project?

There are plenty of open source libraries and frameworks available already, so a better place to start would be to see if some of those fit your needs. I'm not just talking end to end frameworks or cloud services -- although [there](https://www.cesanta.com/) [are](http://derbyjs.com/) [plenty](https://www.meteor.com/) [of](https://strongloop.com/node-js/loopback-framework/) [those](http://www.kaaproject.org/) [out](http://www.ibm.com/cloud-computing/bluemix/) [there](http://thinger.io).

Rather, I mean that if you wanted to build some code from scratch, you can bootstrap the process by using some excellent open source libraries to speed up development and to prevent re-inventing the wheel.

I'm going to take a look at some of these from a javascript-centric viewpoint (we love node.js, Angular, Phonegap, Electron at Lattice Research) -- but the principles hold true for pretty much any language, and they are relevant to most software development, not just IoT projects.

But -- and there's an important but -- not all open source is equal. If you are trying to build a commercial product, you may not want to disclose your entire source code. In this case, non-permissive type open source licenses may not suit and MIT style "permissive licenses" are less onerous.

[If you missed the previous IoT articles, the overview with links to all the other content is [here](https://medium.com/@desflynn/236e379dd821).]

### Open source options

Open source has slowly been changing the face of software development.

Once upon a time, integrating some external code into your own project meant trawling the web for a suitable snippet and copying the code in (if the license permitted). Some large libraries were often available for many languages which extended the abilities of the language beyond the built-in libraries. But -- these were often large, bloated and complex to use.

Nowadays, things have changed and a library usually exists for whatever you'd like to do.

Just this week -- a bit of a kerfuffle caused code deployments depending on external libraries in node.js projects to [break horribly](https://t.co/91aQnBj6IV). The code in question? A library for left padding strings easily -- no more than 11 lines of code. Hundreds of thousands of projects depended on this code -- which shows how prevelant open source libraries are.

That is an aberration, but it is an insight into the modern software development mindset - just grab some open source code to save time. Of course, the correct action here would be to just [write it yourself](https://twitter.com/conoro/status/712536680335609856) day one (it takes well under 160 characters!)

But there is value in re-using OSS code -- what if the library you need would take a few days, weeks or months to write, but someone else has done it already, is maintaining it, and hundreds or thousands of users have tested it already? Well -- then it makes more sense -- with the proviso that you should probably keep a backup local copy of the library forever if you depend on it.

### Package managers

So how did one small library cause so many projects to have build problems? The answer lies in "package managers".

If you've used Linux -- you are probably familiar with these already. Aptitude (apt-get), Yum, IPKG, and others are examples of easy ways to install some software with a single command or click. The publisher of the software has uploaded it to a central location and pre-written any scripts to install the code, deploy any dependencies and get it running fast -- and it works great. It's much more efficient, easy to use and repeatable than on windows.

Similar tools exist for many modern programming languages and frameworks. For example -- Ruby is well known for the Ruby Gems package manager, Python has Pip/PyPM, Node.js has NPM, etc etc.

These take the pain out of deploying open source (and other) libraries in your project. As my day-to-day routines revolve primarily around node.js, I'll describe the process from that viewpoint -- my descriptions from here on may not be exactly correct for other languages -- but by and large the concepts hold true.

You set out and search the web for something you need and find a project which fits the bill on a site like github, npmjs, or somewhere else. These are usually (but not always) published in a way which they can be used in the language-specific package manager.

In node.js, these published libraries are called modules. You can run a short command to install a single module into the current folder (or globally). For example, the following commands in the console / terminal would download and install a module:

> npm install some_module #Available to the project in this folder only

> npm install some_module -g #Globally available

…or you can add it to your project's configuration files as a dependency. This lets large swathes of libraries be installed in one go using a single command.

Next -- you include a reference to the library in your own code. In node.js / javascript parlance:

> var some_module = require('some_module')

Finally -- you can use the resulting object to access the features of the library as found in the library's documentation.

### Pros and Cons

Pros: Oh my God, it's so easy. It's fast. It lets you move rapidly. It lets you do things which you wouldn't bother with if you had to write from scratch. Libraries are often well maintained with frequent updates. If the library source is on github or another git repository, you can post an issue if you run into bugs. If you want to add new functionality to the library, you can do it and post a pull request to github. You can post on stackoverflow with the reasonable expectation that someone else has run into the same issue you have. You can help others solve their problem if you know how to do it. There is a community around the code. You can read the code in order to understand how it does what it does.

Cons: Oh my God, it's too easy. It lets you move too fast without having to understand the underlying code. The underlying code could be terrible. It could have awful security problems. It could be slow. The library could be far too complex for your skill level. It could turn your project into a horrible hodgepodge. It could add bloat. It adds external dependencies. Dependency hell. Etc etc.

So -- there are plenty of pros and cons. But if you understand them before starting, the benefits vastly out weigh the negatives.

### Example of how to use open source effictively

I just checked the dependencies on one of our projects (just one part of our "stack"), and there are 99 external open source dependencies in that one project alone -- and those libraries may have dependencies of their own in turn. I think from memory, there are over a million lines of library code supporting this one (admittedly, fairly sizable) project. And that does not include a single line of the actual project code.

However -- I got 99 problems but OSS ain't one. I understand what each of the libraries does pretty well, and although I couldn't ever hope to read each and every single line of code, we've chosen libraries which are widely used, well supported, by and large mature, and all with published sources. For anything security critical, we've made sure not to rely entirely on an external library to provide it.

We've used open source as a springboard for delivering complex solutions which would have taken far longer otherwise.

### Types of libraries

You need to think it through carefully before committing to adding open source libraries to your project, but as long as you do it brings big benefits. There are six types of libraries present for the example project I gave above.

#### Code helpers

Libraries like [async](https://github.com/caolan/async), [bluebird](https://github.com/petkaantonov/bluebird), [underscore](https://github.com/jashkenas/underscore) and [lodash](https://github.com/lodash/lodash) (all javascript) make it easier to do things like asynchronous code flow, manipulating strings or arrays etc. These are like extensions of regular javascript which make it easier to write your code. Sometimes they fill in a gap which the underlying language does not cover. These types of libraries are used in nearly everything by most programmers.

#### Frameworks

Libraries like [express](https://github.com/expressjs/express), [koa](https://github.com/koajs/koa) and [hapi](https://github.com/hapijs/hapi) (all node.js), [angular](https://angularjs.org/) or [ember](http://emberjs.com/) (both JS) are opinionated frameworks that make you structure your project in a specific way. By doing so, they help make it easier to do common things like web-scale projects, client side UIs, and to integrate other "helper" or middleware libraries written specifically for them. Whole projects are based on top of these frameworks.

#### Widely used, common libraries

These type of general libraries are widely used -- for example for connecting to databases, caching (redis etc), cloud storage, monitoring services like Loggly or New Relic, etc.

#### Niche libraries

There are many libraries which are smaller and widely used, and others which may only have a handful of users. But if you have the right use case, there is a library for most things. Do you need to generate UUIDs in a specific format, tail a specific database's log file for events, turn XML into JSON or vice versa, communicate on a serial port, control a robot, generate your own certificates for use within your code, monitor disk space, monitor CPU usage, extract zip files etc etc? You can generally find what you're looking for. These are the libraries that are really useful to have in your toolbox.

#### Workflow helpers

These are not directly included in your final code, but provide ways to change your workflow and can improve how you work with your project. Examples -- task runners, test suites, reporting and code coverage -- there are open source libraries a-plenty for this too.

#### Environment

If your code is ultimately running in a container or on a linux platform, don't forget there are plenty of open source libraries present there too. An example is a specific open-source library which we compile from source to run on some hardware for interacting with a third party device via a known API.

### A warning on dependency

So -- there are open source libraries for mostly anything -- and they can help you do whatever you need fast.

However - what happens if the deployment of you project relies on grabbing the the latest versions of dependencies / libraries from the web during deployment? Just like the leftPad brouhaha -- you could be left unable to deploy or trying to find a workaround.

The suggested solution -- Keep local copy! Make sure you have a copy of all your dependencies (and their dependencies) locally. Better yet -- mirror your package manager's "repository" (location where it stores the source code) or use a tool to cache the libraries you need.

### **Licensing**

One final thing to consider is the terms of the libraries you choose to use.

If you are developing a commercial project and you're trying to build some proprietary IP, then beware -- as open source is not all equal.

Most libraries published online come with a license attached. Different open source licenses hold the developer to different standards.

MIT/BSD/Apache type licenses are free to use/modify, all that is required to comply with the license is attribution that the original code was used if you are distributing the source code or binaries.

However other "non-permissive" licenses -- particularly GPL -- are more onerous. They may require you to release your modified source code to anyone who gets a copy of the binaries. If your business plan revolves around giving your code away and making money from the services or consulting associated, then this may be fine -- but could be a roadblock if you are doing something commercial.

How can you be sure you are not breaking licenses? Before you start working with a library, make sure to check its' license. In our case, you can be reasonably sure that node.js code is permissive -- MIT licensed or similar -- but this is not always the case.

For node.js (and other languages with a package manager environment), some third party tools exist which can scan your libraries folder to determine the licenses of each library, allowing you to 1. gather the license messages for publishing in the case of permissive licenses or 2. Take action if non-permissive licenses were used when they should not have been.

To end on a thoughtful note, those third party license finder libraries are usually open source themselves, and could scan themselves to determine their license. How meta.

### Summary

Using open source libraries can amplify your efforts. Be sure to think through how to use them before you start, keep a copy of all dependencies safe (in case the cloud blows away) and make sure you know where you stand on licensing.

In an IoT context, there is so much to do that the use of open source somewhere in your project seems inevitable -- just make sure put a little consideration into Open source and licensing before you start your next project.

_PS -- If you write something cool and it's not part of your private core IP in a business context, consider releasing it into the wild! Publish it online with an open source license. Without contributors open source would not exist._

Des Flynn is CTO of Lattice Research, who help companies to design, build, deploy, operate and service innovative and cost-effective IoT control systems to meet their customer's needs. More information at [www.lattice.ie](http://www.lattice.ie/)
