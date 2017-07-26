# Package Management: Stop Using Version Ranges

_Captured: 2017-06-11 at 02:06 from [dzone.com](https://dzone.com/articles/package-management-stop-using-version-ranges?edition=304168&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-10)_

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

## The Problem

### Packages and Managers

Packages are collections of software: data files, binaries, executables, source archives, etc. These are published, resolved, downloaded, and installed with package managers.

Unfortunately, in 2017, almost every package manager has the ability, the default, or even the common practice of creating nondeterminism in the form of version ranges.

![Image title](https://dzone.com/storage/temp/5520655-screen-shot-2017-06-06-at-114350-am.png)

> _This problem is illustrated in this conversation between two developers:_

Bob: It looks like the tests fail.  
Alice: Really? I ran them yesterday and they work fine for me.  
Bob: Yeah. Here's the error…  
Alice: Try X, Y, and Z.  
Bob: Still doesn't work.  
Alice: Okay, well try…..  
(hours later)  
Bob: I think it's octo-json-parser.  
Alice: What version do you have?  
Bob: Oh, I have 2.0.0.  
Alice: Oh, that was just released this morning.

Floating software dependencies do all of the following:

  1. Produce different builds.
  2. Affect test results.
  3. Change which bugs are present.

They inhibit building and using older versions of the project, complicate bug reports, and make CI results unreliable. A version number or commit hash is no longer sufficient information to describe the state--the rest of the universe must be considered as well.

### In the Wild

This practice is discouragingly common. Consider some of the most popular Javascript (NPM) packages. Express has 83 edges in its transitive dependency graph, 50 of which have floating (not-fixed) versions. Grunt has 89 floating of 93. Gulp has 621 of 633. React has 17 of 17.

Even relatively stable Java-land is not immune to poor software dependency decisions. For years, [aws-java-sdk-core](http://central.maven.org/maven2/com/amazonaws/aws-java-sdk-core/1.9.40/aws-java-sdk-core-1.9.40.pom) depended on joda-time [2.2,). aws-java-sdk-core version 1.9.40 will evidently be compatible with whatever version of joda-time is released in 2040. It will depend on the latest version of joda-time until the end of time.

## The Fallacy of Harmless Upgrades

Having established that 1.8.0 - Infinity is a bad version range, perhaps we can be more discriminating and only take the latest 1.8.x version. We'll use 1.8.0, 1.8.1, 1.8.2, etc.

This notion is so common that some package managers dedicate syntax to this practice.

![Image title](https://dzone.com/storage/temp/5520656-screen-shot-2017-06-06-at-114400-am.png)

> _If everyone follows semantic versioning, it's safe, right? Wrong._

The hypothetical story of the trailing comma bug:

  1. Version 1.8.0 of octo-json-parser provides a function `parseJson()`, which is documented to parse JSON for valid input and produce an error for invalid input.
  2. A bug is reported where `parseJson()` considers trailing commas to be okay, like `["abc",123,]`. This is a bug, since the behavior differs from the documented API.
  3. The bug is corrected, so trailing commas produce an error.
  4. Since the documented API of octo-json-parser has not changed, semantic versioning classifies this as a patch release. And so the maintainers release version 1.8.1.

Wonderful. Bugs getting patched, clients getting 1.8.x updates…the machine of software humming along.

But wait--a client of octo-json-parser has been validating user input with `parseJson()` and persisting the input to a database. The data is retrieved on demand and reparsed and processed with octo-json-parser. Upgrading to version 1.8.1 suddenly corrupts (makes unreadable) their months of stored data. The 1.8.0 -> 1.8.1 upgrade has failed.

Certainly some changes are safer than others, but there's no such thing as a 100% innocuous change. Any dissenting opinion lacks imagination (and experience).

### The Fallacy of Security

Some justify `"~1.8.0"` because it includes important security updates automatically. The reality is that no clever versioning scheme fixes security. In the event of a vulnerability, the exposure must be assessed, the fixed version must be deployed, and penetration and damage must be analyzed. Using version ranges for security is like bringing a Band-Aid onto an airplane in case there is a mechanical problem.

### A Note About External VCS

Some package managers (e.g., npm and Go) can depend on other VCS repos. These can have similar problems. If using Git, never depend on HEAD or a branch. Always use a tag or commit hash.

## Solutions

Package management in 2017 shouldn't be so messy. Changes should be limited to a very well-defined scope, which is almost always a version-controlled repository. A reliable build must be hermetic. It shouldn't depend on some bits moving around half a world away. Violating this principle will leave your builds as a thing of wax, molded by the current bit of weather.

There are several ways to overcome version ranges.

### Don't Allow Version Range

Some forward-thinking package managers don't allow version ranges at all, e.g., [Nix](https://nixos.org/nix/) and [Guix](https://www.gnu.org/software/guix/). In fact, these two take reproducible versioning to another level by using the package hash as the version.

### Don't Use Version Ranges

Even if version ranges are allowed, you don't need to use them. Naturally, this only works if your transitive dependencies play by the same rules. For Java, this is a workable strategy. For Ruby, perhaps not.

Some poorly made build tools can be non-deterministic even using fixed ranges, e.g., [npm](https://docs.npmjs.com/how-npm-works/npm3-nondet).

### Use Version Control Sources

Copy the sources for dependencies into your repo, e.g., Go [vendoring](https://github.com/golang/go/wiki/PackageManagementTools#go15vendorexperiment). This requires you to incorporate your dependencies' build processes into your own, including the same build tools, header files, etc. Doing so can quickly get complicated. For example, on the JVM alone, projects could be using Ant, Maven, Gradle, SBT, Make, scalac, groovyc, jythonc, Clojure, etc.

### Use Version Control Outputs

Copy the binaries for dependencies into your repo. However, this bloats the size of your repo. While DCVS is awesome, hauling around 100GB of bygone binaries in the history is not. You may need [Git LFS](https://git-lfs.github.com/) or another strategy for dealing with large repos.

### Copy Repos

This is an operational solution to the problem. Create a copy

of

artifact repos--either plan copy or something more sophisticated like [Artifactory](https://www.jfrog.com/artifactory/)--in a way that allows you to control when updates are made available. The downside is that this solution takes place outside version control.

### Use Version Lock File

Bundlr has [Gemfile.lock](https://bundler.io/v1.3/rationale.html); npm has [shrinkwrap](https://docs.npmjs.com/cli/shrinkwrap); Go has [Glock](https://github.com/robfig/glock). These solutions generate complete version info for transitive dependencies, which is put under version control. They make updates more complicated than a simple one-line change, and complete version info now involves hundreds of lines. But it's better than non-determinism.

## Conclusion

Upgrade your dependencies. Security updates are important. Functional fixes are important. Performance improvements are important. But always upgrade intelligently and deliberately, under version control.

The important thing is to ensure that builds, deployments, tests, and versions are as reliable and reproducible as possible. If your package management solution hinders that, you should fix it. Just as you wouldn't begin a Python script with `from __future__ import *`, don't use version ranges in software dependencies. Software is hard enough--don't make it any flakier than it already is.

(FYI, there actually is one valid reason for using version ranges: to document/enforce compatibility. This is the intent in package managers like apt and yum. Unfortunately, these package managers choose to resolve the versions in a non-deterministic way. This could be made to work in a deterministic way (e.g., require the lower point of the version range to exist and resolve to the lowest version of the intersection), but I'm not aware of any systems that do that.)

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).
