# Don't Install Development Tools!

_Captured: 2018-06-02 at 22:06 from [dzone.com](https://dzone.com/articles/dont-install-development-tools?edition=380205&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-06-02)_

The need for DevOps innovation has never been greater. Get the results from over 100 business value assessments in this whitepaper, [Digital Darwinism: Driving Digital Transformation](https://dzone.com/go?i=291429&u=https%3A%2F%2Fpages.cloudbees.com%2Fl%2F272242%2F2018-04-19%2F8t38t%3Futm_source%3Ddzone%26utm_medium%3Dbumper-text%26utm_campaign%3Ddzone-sponsored-link%2520), to see the positive impact of DevOps first hand.

## …Use Jenkins X, DevPods and Kubernetes!

I wrote [previously](https://dzone.com/articles/dont-install-kubernetes) about how you can be lazy and avoid installing Kubernetes (by letting cloud providers do it). In this installment, I want to tell you how to not install (or at least not to install many) development tools on your workstation. The tools I have installed that I will talk about are [Jenkins X binary (jx](https://jenkins-x.io/getting-started/install/)[)](https://jenkins-x.io/getting-started/install/) and [Visual Studio Code](https://code.visualstudio.com/).

Around the time of that blog I was expressing frustration when talking with [James Strachan](https://twitter.com/jstrachan) about all the work required to keep my local machine (a Mac) up to date with dev tools, and how tired I was of seeing the beachball on OS X when doing this:

![](https://www.cloudbees.com/sites/default/files/kubernetes-cloudbees-osx.png)

> _(stare at it for a while...)_

This is a drag on time (and thus money). There are lots of costs involved with development, and I talked about the [machine cost for development](https://dzone.com/articles/dont-install-kubernetes) (how using something like GKE can be much cheaper than buying a new machine) but there is also the cost of a developer's time. Thankfully, there are ways to apply the same smarts here to save time as well as money. And time is money, or money is time?

Given all the work done in automating the detection and installation of required tools, environments, and libraries that goes on when you run 'jx import' in [Jenkins X](https://jenkins-x.io/), it makes sense to also make those available for development time, and the concept of "DevPods" was born.

_The [pod part of the name](https://kubernetes.io/docs/concepts/workloads/pods/pod/) comes from the Kubernetes concept of pods (but you don't have to know about Kubernetes or pods to use Jenkins X. There is a lot to Kubernetes but Jenkins X aims to provide a developer experience that doesn't require you to understand it)._

Why not use Jenkins X from code editing all the way to production, before you even commit the code or open a pull request? All the tools are there, all the environments are there, ready to use (as they are used at CI time!).

This rounds out the picture: Jenkins X aims to deal with the whole lifecycle for you: from ideas/issues, change requests, testing, CI/CD, security and compliance verification, rollout and monitoring. So it totally makes sense to include the actual dev time tools.

If you have an existing project, you can create a DevPod by running (with the jx command):

This will **detect** what type of project is (using build packs) and create a DevPod for you with all the tools pre-installed and ready to go.

Obviously, at this point, you want to be able to make changes to your app and try it out. Either run unit tests in the DevPod, or perhaps see some dev version of the app running in your browser (if it is a web app). Web-based code editors have been a holy grail for some time, but never have quite taken off in the mainstream of developers (despite there being excellent ones out there, most developers prefer to develop on their desktop). Ironically, the current crop of popular editors are based around [Electron](https://github.com/electron/electron) which is actually a web technology stack, but it runs locally (Visual Studio Code is my personal favorite at the moment), in fact Visual Studio Code has a Jenkins X extension (but you don't have to use it):

![](https://www.cloudbees.com/sites/default/files/kubernetes-cloudbees-jenkinsx.png)

> _To get your changes up to the DevPod, in a fresh shell run (and leave it running):_

This will watch for any changes locally (say you want to edit files locally on your desktop) and sync them to the DevPod.

Finally, you can have the DevPod automatically deploy an "edit" version of the app on every single change you make in your editor:

The first command will create or reuse an existing DevPod and open a shell to it, then the **watch **command will pick up any changes, and deploy them to your "edit" app. You can keep this open in your browser, make a change, and just refresh it. You don't need to run any dev tools locally, or any manual commands in the DevPod to do this, it takes care of that.

You can have many DevPods running (jx get devpods), and you could stop them at the end of the day (jx delete devpod), start them at the beginning, if you like (or as I say: keep them running in the hours between coffee and beer). A pod uses resources on your cluster, and as the Jenkins X project fleshes out its support for dev tools (via things like VS Code extensions) you can expect even these few steps to be automated away in the near future, so many of the above instructions will not be needed!

## End-to-End Experience

So bringing it all together, let me show a very wide (you may need to zoom out) screenshot of this workflow:

![](https://www.cloudbees.com/sites/default/files/kubernetes-cloudbees-workflow.png)

> _From Left to Right:_

  * I have my editor (if you look closely, you can see the Jenkins X extension showing the state of apps, pipelines and the environments it is deployed to).
  * In the middle I have jx sync running, pushing changes up to the cloud from the editor, and also the "watch" script running in the DevPod. This means every change I make in my editor, a temporary version of the app (and its dependencies are deployed).
  * On the right is my browser open to the "edit" version of the app. Jenkins X automatically creates an edit environment for live changes, so if I make a change to my source on the left, the code is synced, build/tested and updated so I can see the change on the right (but I didn't build anything locally, it all happens in the DevPod on Jenkins X).

On Visual Studio code: The Jenkins X extension for visual studio code can automate the creation of DevPods and syncing for you. Expect richer support soon for this editor and others.

### Explaining Things With Pictures

To give a big picture of how this hangs together:

![](https://www.cloudbees.com/sites/default/files/kubernetes-cloudbees-workflow-visualization.png)

In my example, GitHub is still involved, but I don't push any changes back to it until I am happy with the state of my "edit app" and changes. I run the editor on my local workstation and jx takes care of the rest. This gives a tight feedback loop for changes. Of course, you can use any editor you like, and build and test changes locally (there is no requirement to use DevPods to make use of Jenkins X).

Jenkins X comes with some ready to go environments: development, staging, and production (you can add more if you like). These are implemented as Kubernetes namespaces to avoid the wrong app things talking to the wrong place. The development environment is where the dev tools live: and this is also where the DevPods can live! This makes sense as all the tools are available, and saves the hassle of you having slightly different versions of tools on your local workstation than what you are using in your pipeline.

DevPods are an interesting idea, and at the very least, a cool name! There will be many more improvements/enhancements in this area, so keep an eye out for them. They are a work in progress, so do check the documentation page for better ways to use them.

Some more reading:

  * Docs on [DevPods](https://jenkins-x.io/developing/devpods/) on jenkins-x.io
  * The [Visual Studio Code](https://github.com/jenkins-x/vscode-jx-tools) extension for Jenkins X (what a different world: an open source editor by Microsoft!) 
    * Expect extensions for other editors soon as well
    * This extension can watch for pipeline activity on Jenkins X, help out with DevPods and more
  * James Strachan's great [intro to Jenkins X talk](https://jenkins-x.io/demos/devoxx-uk-2018/) at Devoxx-UK also includes a DevPod demo

Interested in Kubernetes but unsure where to start? Check out this whitepaper, **[A Roundup of Managed Kubernetes Platforms**](https://dzone.com/go?i=291430&u=https%3A%2F%2Fpages.cloudbees.com%2Fl%2F272242%2F2018-03-07%2F7wybk%2520) from Codeship by Cloudbees, for an overview and comparison of Kubernetes platforms.
