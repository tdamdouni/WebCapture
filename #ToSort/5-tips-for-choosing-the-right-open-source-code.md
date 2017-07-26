# 5 Tips For Choosing The Right Open Source Code

_Captured: 2017-06-08 at 21:23 from [readwrite.com](https://readwrite.com/2017/06/07/5-things-you-should-look-at-when-using-code-from-the-web/)_

![](https://readwrite.com/wp-content/uploads/RW_API.png)

[Studies](https://static.googleusercontent.com/media/research.google.com/en//pubs/archive/43835.pdf) conducted by Google show that for many developers finding code online consumes a large portion of the day. Finding a simple function, a library, a useful package, a reusbale component or a useful "how to" blog tutorial isn't always simple. Knowing if you can trust and use the code you found can be even more tricky.

Finding the right code usually means turning to the gods of Google or other search engines, throwing in a query and crossing fingers for a quick win. Simple functional queries such as "Javascript has own property" will probably lead to different forums and blog posts, while higher level descriptions ("React component x") will often land you in GitHub or NPM.

![Screen Shot 2017-06-06 at 10.36.49 AM](https://15809-presscdn-0-93-pagely.netdna-ssl.com/wp-content/uploads/Screen-Shot-2017-06-06-at-10.36.49-AM.png)

However, even after finding the right code - [trusting and using](https://medium.com/@Rich_Harris/small-modules-it-s-not-quite-that-simple-3ca532d65de4) it is a whole different problem. To help understand which code you can actually use, I gathered 5 parameters which can be helpful to consider. Making the right decision should factor these parameters (among others), as well as the nature of the task itself. Here are the 5 keys you can consider for choosing the right code.

### 1\. Is the code readable?

Readable code means much more than only good comments and documentation. It means the code itself should be readable to you. Different parameters for readability can be good naming conventions for identifiers, good spacing, clear readable logic, well-understood scopes and more. The bottom line is, the code should be readable **to you**. When you choose a piece of code, even one that works, but you don't fully understand how it works - you're basically bringing in a maintenance time-bomb into your code base.

Debugging, modifying, updating and maintaining code you can't read is something you should strongly avoid. The best way to avoid it will be never letting it in the first place when possible.

### 2\. Is the code actively maintained?

![mirai04](https://15809-presscdn-0-93-pagely.netdna-ssl.com/wp-content/uploads/mirai04-300x155.jpg)

We want the code we pick to be "alive". Meaning, we want to know bugs, issues and updates are being handled and this code will be actively maintained by the developers who wrote it. A nice example for an activity indicator can be GitHub's open issues, pull requests and [Pulse indicator](https://github.com/teambit/bit/pulse). Package managers provide information relevant for maintenance such as the number of dependencies and dependent projects, but still, struggle to present a trustworthy metric in this field.

Still, if a big popular project is dependent on another package, we can assume problems have a high likelihood of being fixed (however, we all remember [left-pad](https://www.theregister.co.uk/2016/03/23/npm_left_pad_chaos/)). However, when copying code from stack overflow (which is [a problem](https://stackoverflow.com/questions/4226284/how-to-convince-a-colleague-that-code-duplication-is-bad) on its own) you have no way of knowing you can trust this code will be maintained other than updating it yourself whenever needed (and wherever you've duplicated it).

Small core functionalities simply don't change as much. In this spirit, [reusable components imported from Bit](https://bitsrc.io) rely on a simple [incremental versioning](https://bitsrc.io/tomlandau/simple-js/global/is-mobile) which increments the component's version by 1 every time its author changed something. Keeping your components in a "latest updated" version means, given good tests, your code can be actively maintained by its maintainer while still updating even small functions or components in your code without breaking anything.

### 3\. Is the code well tested?

Choosing code that works is probably our first priority. Tests are a great way of knowing if the code I use actually does what it's supposed to do. The tests description also present different use cases and edge cases which help us know how this code will behave in different situations. Using tested components makes for [more maintainable software](https://addyosmani.com/first/) as a whole, saving time and trouble when trying to change stuff before rolling to production.

Snippets copied from around the web usually don't come with tests. Rarely, if at all, functions copied from forums or blog posts will include unit tests. Packages and libraries might very well be tested, the problem lies in being able to quickly figure it out. When exploring a library on GitHub, different badges or files in the repository can indicate how well and how much of this code is tested. We'll still have to use indicators provided by [external tools](https://circleci.com/?utm_source=Google%20&utm_medium=SEM%20&utm_campaign=ASearch%20Activation%20non%20Branded&utm_term=v1&utm_content=TravisCI&gclid=CIO1w5qNqdQCFQgyaQod_1oIWA) to figure out if the tests passed or not. While looking for a package, there isn't really a reliable way of knowing which package is tested and whether the tests usefully passed. This is a big issue when it comes to packages discoverability. Reusable

When looking for a package, there isn't really a reliable way of knowing which package is tested and whether the tests usefully passed. This is a big issue when it comes to packages discoverability. Reusable [Bit components](https://github.com/teambit/bit) can be tested if such tests are added by the developer. The Bit Scope runs the test so that the green indicators and the tests description can be shown online before [choosing a component from the Bit community hub](https://bitsrc.io/bit/utils#array) (or via the CLI when used on your local machine in a [distributed manner](https://teambit.github.io/bit/bit-on-the-server.html)).

### 4\. Is the code being used by others?

![nokia-mwc2017-lounge-2](https://15809-presscdn-0-93-pagely.netdna-ssl.com/wp-content/uploads/nokia-mwc2017-lounge-2.jpg)

Popularity is something we evolutionary trust. Public opinion is good for making decisions which help our survival. If we see everyone eating a certain fruit off a tree, we know it probably won't kill us. If we see everyone running from the bushes, a hungry tiger might soon follow. To some extent, the same goes for choosing code in 2017.

Around Programming forums, we can use different indications such as a "V" marking the correct answers, the number of upvoted and vocal user vocal opinions. These are excellent and reassuring features for increasing the probability the code works fine. When it comes to GitHub, we can rely on stars, collaborators and other social metrics to get a trust-worthiness feeling. When looking for packages, a good indicator would be the number of downloads for this package.

Bit components found on the Bit community hub present the number of downloads, collaborators (on the scope level), simple "likes" and more (as shown in [this React Scope of components](https://bitsrc.io/materialui/react-material-ui#styles)). Either way, keep in mind social metrics are a good indication - but bot an absolute truth regarding the quality of the code. People are often wrong, and public opinion can change quicker than we think.

### 5\. Is the code well documented?

Documentation makes code much easier to understand, use and modify. It's also a great indication for the thought and carefulness the developer who wrote the code put into it. The documentation for code found on Stack Overflow or different blog posts can consist of both the comments in the code itself as well as the actual answer or blog it was found in. When a forum answer includes a useful elaboration on the code it includes, this might very well be a documentation worth adding even when copy-pasting the code itself (again, please don't copy paste code).

For GitHub repositories and packages, things are a bit trickier. Usually, the readme and docs files presented on GitHub or NPM will provide a general indication as to the quality of documentation. Documentation for Bit components is parsed from within the code itself and so it shows the actual description for the atomic component, and can also include usage examples and a specified signature including arguments and returns for different functions and behavior for React components and others. Either way, choosing documented code is a good decision whenever possible.

For GitHub repositories and packages, things are a bit trickier. Usually, the readme and docs files presented on GitHub or NPM will provide a general indication as to the quality of documentation. Documentation for Bit components is parsed from within the code itself and so it shows the actual description for the atomic component, and can also include usage examples and a specified signature including arguments and returns for different functions and behavior for React components and others. Either way, choosing documented code is a good decision whenever possible.

![pros cons connected world iot](https://15809-presscdn-0-93-pagely.netdna-ssl.com/wp-content/uploads/pros-cons-connected-world-iot.jpg)

At the end of the day, the human memory is limited and there is really not much point in reinventing the wheel every time. However, when finding and using a piece of open source code the above indicators can help make sure your application remains secure, maintainable, working and in good health.

Different use cases mean giving different weight to the different parameters. When choosing a package, it will be hard to know how tested, readable, documented and actively maintained it is. When copying code from on online forum, we may be prioritizing popularity over tests, maintenance and so on. Bit components combine information relevant for importing and reusing components and atomic functionalities such as description, examples, downloads, dependencies, tests description, test results and more. By carefully considering these different parameters we can make an informed decision and cross the maze of finding and choosing the right code for the job.
