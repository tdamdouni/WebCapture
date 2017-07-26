# Things Everyone Forgets Before Committing Code

_Captured: 2017-05-10 at 00:38 from [dzone.com](https://dzone.com/articles/things-everyone-forgets-before-committing-code?edition=298034&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-09)_

Reduce testing time & get feedback faster through automation. Read the [Benefits of Parallel Testing](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile), brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

Committing code involves, in a dramatic sense, two universes colliding. Firstly, you have the universe of your own work and metaphorical workbench. You've worked for some amount of time on your code, hopefully in a state of flow. And secondly, you have the universe of the team's communal work product. And so when you commit, you force these universes together by foisting your recent work on the team.

In bygone years, this created far more heartburn for the average team than it does today. Barbaric as it may seem, I can actually remember a time when some professional software developers didn't use source control. A "commit" thus involved literally overwriting a file on a shared drive, obliterating all traces of the previous version (sometimes, you might create a backup copy of the folder). Here, your universe actually kind of ate the team's communal universe.

### More Frequent Commits, Fewer Problems

But, even in the earliest days of my career, the lack of source control represented a sloppy process. I remember installing the practice in situations that lacked it. But even with source control in place, people tended to go off and code in their own world for weeks or even months during feature development. Only when release time neared did they start to have what the industry affectionately calls "merge parties," wherein the team would spend days or weeks sorting out all of the instances where their changes trampled one another's.

In the interceding years, the industry has learned the wisdom of continuous integration (CI). CI builds on the premise, "if it hurts, do it more," by encouraging frequent, lower stakes commits. These days, most teams commit on the order of hours, rather than weeks or months. This significantly lowers the onerousness of universes colliding.

But it doesn't eliminate the problem altogether, even in teams that live the CI dream. No matter how frequently you do it and how sophisticated the workflows around modern source control, you still have the basic problem of putting your stuff into the team's universe. And this comes with the metaphorical risk of leaving your tools laying around where someone can trip over them.

So today, let's take a look at some of the most common things everyone forgets before committing code. And, for the purposes of the post, I'll remain source control agnostic, with the parlance "commit" meaning generally to sync your files with the team's files.

### Adding or Removing Files

I'm sure any developer reading can appreciate this one. You work for a while, commit your code, and get a build failure (or an email from an annoyed teammate). Before you even process the message, you realize the problem. You added a file to the codebase but forgot to add it to source control. Oops.

Ways to prevent or mitigate this situation do exist. Many IDEs and editors will allow source control plugins that automatically add appropriate files to source control, for instance. But regardless of your tooling or process, you have an obligation. Whenever you add or remove files, you need to make sure source control knows about it.

### Compiling the Code

I sort of hate that I even have to type this in 2017, but the issue still exists. Sometimes, developers forget to compile code before committing. When you do this, you play a dangerous game wherein you assume a lack of mistakes on your part and don't check. I rarely see people just bang away at the keyboard without ever compiling and then commit, however. More commonly, you see this when someone wants to make a quick little change right before committing that they "know" won't cause a problem.

If you have an automated build, it will quickly slap you for this. Your team may then shame you and force you to bring donuts the next day. But better to avoid all of this and run a local build just before a commit.

### Making Sure Not to Break Other People's Stuff

You can generalize the compiling issue to this one, making that a special case of "don't break your teammates." In other words, you can interrupt their progress in more ways than by dumping non-compiling code on them.

For instance, imagine that you need to make some changes to a frequently called method. As interim, placeholder code, you remove its implementation and throw a not implemented exception. Then you forget that you did this and commit changes you were making elsewhere. Your code may compile, but now anyone running the software will have to deal with all sorts of exceptions.

So before committing, make sure you haven't done anything that will ruin someone's afternoon.

### Updating Comments to Reflect Reality

Personally, I'm not big on commenting code, specifically because of the problem I'm about to discuss. Comments, particularly ones explaining the "how" of the code, age poorly.

If you go into a heavily commented method and start changing its behavior, you will likely make some of those comments obsolete. Perhaps you're fixing a bug or the requirements have changed. Whatever the case may be, you don't want to leave obsolete comments in there. They will just confuse you and anyone else maintaining the code later.

Even deleting the comments represents an outcome preferable to that. But if someone took the time to add them, you should probably take the time to fix them.

### Removing Temporary Code

We'd all like to think that we don't do this, particularly among so-called clean code advocates. Who needs temporary code when you have sophisticated debuggers and, more importantly, simple code covered by unit tests? Theoretically, this holds true always. In practice, it still holds true _most of the time_. But most means not all.

So, when you do have the occasion to put in some temporary code that you added for debugging purposes, don't leave it there. At best, this adds useless clutter and, at worst, it negatively affects production behavior. Make sure to clean up after yourself.

### Running the Unit Tests

Does your team have a unit test suite? If so, I imagine that you, as a human being, have committed once or twice without actually running all of the things. If it makes you feel any better, I've done this in my life, when in a hurry. You absolutely, positively _know_ that your changes won't affect anything. Except then, of course, they do.

Whether or not you have a build that runs the tests and fails on failure, school yourself away from ignoring the tests before a commit. Doing so is sloppy, and it will just wind up creating more work for you later. I personally never contend with this issue anymore because I install continuous test runners, thus taking the onus off of myself to do it.

### Running Static Analysis

This may not apply to all situations, but, in my opinion, it should. Some teams routinely run static analyzers, and some even bake static analysis rules into the build.

When your team has standards along these lines, especially with automated enforcement, you may as well check in non-compiling code. In either case, you'll generate a build failure. But even without enforcement, [if you have a standard](http://blog.ndepend.com/company-coding-standards-right-wrong/), ensure your code compiles by running the analyzer before committing.

### Automate as Much as You Can

I'll close with a parting call to unburden the team as much as possible. Here, I've laid out a list of things to check for before committing. But in a world where you commit frequently, you don't want to sit there going through a literal checklist every time. We automate things for a living -- we shouldn't have to put up with that.

So, automate as much of this checklist as you can. And try to operationalize the rest. The more you can put on auto-pilot, the more you can focus on your code and the less you'll have to worry about leaving your metaphorical tools all over the room for people to trip over.

The Agile Zone is brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile). Discover how to optimize your DevOps workflows with our [cloud-based automated testing infrastructure](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).
