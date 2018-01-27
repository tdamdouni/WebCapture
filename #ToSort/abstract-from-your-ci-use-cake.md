# Abstract From Your CI. Use Cake!

_Captured: 2017-10-24 at 20:25 from [dzone.com](https://dzone.com/articles/abstract-from-your-ci-use-cake?edition=334723&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-10-24)_

The Nexus Suite is uniquely architected for a DevOps native world and creates value early in the development pipeline, provides precise contextual controls at every phase, and accelerates DevOps innovation with automation you can trust. [Read how in this ebook](https://dzone.com/go?i=222229&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).

Here at [Coolblue](https://www.coolblue.nl), we can choose our tools from a range of technologies. A while ago, our team started moving from Microsoft MSTest to xUnit.

Although the code change was fairly simple, the build pipeline was tied with the MSTest framework, ignoring the xUnit tests. Between the requests to the deployment team to alter the team's deployment pipelines, [Nathan](https://nathanjohnstone.wordpress.com/) challenged us to use Cake.

## What Is Cake?

![](https://camo.githubusercontent.com/37601742f9e68206e3ba9b4bd5da255b69d0b929/68747470733a2f2f63646e2d696d6167652e6d79726563697065732e636f6d2f73697465732f64656661756c742f66696c65732f7265642d76656c7665742d63616b652d636f636f6e75742d637265616d2d6368656573652d66726f7374696e672d63726f702d736c2e6a7067)

> _Image source_

_._

Although I'm a cake monster, "Cake (C# Make) is a cross-platform build automation system with a C# DSL to do things like compiling code, copy files/folders, running unit tests, compress files and build NuGet packages _(source)_."

Great, this is the tool that was missing, allowing us to abstract from our CI server, speeding our development (and in the end, that is Agile)!

## The Roller-Coaster

Cake allows us to build our project in many different ways with a syntax that is our bread and butter (C#). The platform is open-source, meaning that we can fix any bug, or [contribute](https://cakebuild.net/docs/contributing/contribution-guidelines) with a module to increase the ecosystem.

During my spare time, I started playing around with Cake in a [pet project](https://github.com/joaoasrosa/pullrequests-viewer). The pet project is built using .NET Core 2.0, and the ultimate goal was to build the project in [AppVeyor](https://www.appveyor.com/) and [TravisCI](https://travis-ci.org/). The build steps were:

  1. Ensure the non-solution folders exists (for example, artifacts folder).
  2. Clean the solution.
  3. Restore the NuGet packages.
  4. Build the solution.
  5. Run the tests.

As a bonus, it should be able to:

  1. Package and push a NuGet package.
  2. Create and push a Docker container.

Cake offers support to all these steps, either out-of-the-box feature or as a module offered by the community.

The development was simplified since the operations to build & test my project was the same that the build server would execute. It avoids the old developer excuse "it works on my machine," _**since**_ the developer machine has the same software that the build server (during the development I face this problem with AppVeyor. The solution was published [here](https://anotherlookontech.wordpress.com/2017/08/10/build-a-net-core-2-0-application-in-appveyor/)).

## A Plethora of Opportunities

![](https://camo.githubusercontent.com/a65d613e7adede566d60cc8e0d87b90323ceec16/68747470733a2f2f6d656469612e6d616b65616d656d652e6f72672f637265617465642f4f50504f5254554e49544945532d4f50504f5254554e49544945532d455645525957484552452d316b657575732e6a7067)

This approach decreased the time to configure two different CI servers since it supports the executing of the scripts in Windows, Linux, and MacOS.

However, the opportunities are endless. In an enterprise environment, the software is a complex web of services and other moving parts; a team needs to be able to add a feature, testing & shipping it quickly; at the same time assuring the business that is working as expected, and more important, it doesn't introduce any regression bugs.

Using Cake, we can setup the script to deploy the necessary components on our development machines, running the tests to assure that everything works before we push our changes. This level of automation and abstraction also enables the developers to focus on delivering value (coding a new feature), rather than spending time configuring and deploying (manually) all the components to run the tests. Raise your hand who was in this situation. Yeah, every developer.

## The Final Result

After a few hours around the script, both AppVeyor and TravisCI can execute it, predictably, as I do in my development environment. You can view a sample of the build logs [here](https://ci.appveyor.com/project/joaoasrosa/pullrequests-viewer) and [here](https://travis-ci.org/joaoasrosa/pullrequests-viewer).

Within our team, we start to move towards this direction. All the new projects are bootstrapped with a basic Cake script (Clean, Restore, Build, Test and Create NuGet package), but the team iteratively adapts it to our development needs. In the end, a development team should be proud of the software delivered, because it improves the business, but also the team was able to use the time is an effective way.

## And for Other Languages/Frameworks?

The same concept exists in other languages/frameworks. As a short list, we have:

Be aware that this is a _short list_. Out there exists other build platforms that allow you to abstract from your CI server.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. See how the Nexus platform infuses precise open source component intelligence into the DevOps pipeline early, everywhere, and at scale. [Read how in this ebook](https://dzone.com/go?i=222230&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).
