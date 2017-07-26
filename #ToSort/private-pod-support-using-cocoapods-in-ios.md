# Private Pod Support Using CocoaPods in iOS

_Captured: 2017-03-28 at 20:49 from [dzone.com](https://dzone.com/articles/private-pod-support-using-cocoapods-in-ios-1?edition=286932&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-28)_

Discover [how to focus on operators for Reactive Programming](https://dzone.com/go?i=190139&u=https%3A%2F%2Fblog.wakanda.io%2Freactive-programming-operators%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how they are essential to react to data in your application. Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190139&u=https%3A%2F%2Fwww.wakanda.io%2F).

You might have read our recent blog on [SDUI framework](http://www.azilen.com/blog/server-driven-user-interface-sdui-framework-ios-applications/) that introduced the concept of UI presentation made easier by eliminating the need for frequent updates to an application by the end user. It is built and deployed with just "one code base logic" and is applicable for each of the UI releases while eliminating the need for frequent updates of the Apps.

The framework can be of used in other iOS projects; hence it requires a lot of effort in manually installing and building it. Therefore, to overcome this challenge the team explored various options and found a more centralized solution, 'CocoaPods' \- a dependency manager tool that provides a standard format for managing the external libraries. It has over 27 thousand libraries and is used in over 1.6 million apps and can help scale any project elegantly. It focuses on the source-based distribution of third party code and automatic integration into Xcode projects.

## Getting Started

The dependencies for projects are specified in a single text file called a Podfile. CocoaPods will resolve the dependencies between libraries, fetch the resulting source code, and then link it together in the XCode workspace to build your project.

![Image title](https://dzone.com/storage/temp/4752781-step-by-step-guide-to-add-private-pod-support-in-i.jpg)

### Follow the Below Steps to Add Private Pod in Your Ios Project:

By default, CocoaPods uses a public specification repository (<https://github.com/CocoaPods/Specs>). If you want to make your pod private then you have to create a private repository with the same structure and upload your pod specification file to the private repository.

## Installation

**1.** CocoaPods is built with Ruby and it will be installable with the default Ruby available on Mac OS. Using the default Ruby install will require you to use "sudo" when installing gems.

**2.** Follow the below command to install Cocopods in your system:
    
    
    $ sudo gem install cocoapods

### Create a pod specification file (.podspec file).Create and Use Cocoapods in Your Ios Project

  * The specification file contains detailed information about the repository. When you execute pod install or pod update commands, CocoaPods will look into the specification file and clone the repository.

### Follow the Below Steps:

**1.Create a specification for your pod using the following command:**

`$podspec create <your_pod_name>`

**Example:** pod spec create AppUtils

**2.Edit the AppUtils.podspec**

  * Name - name of the pod.
  * Version - the current version for the specification. Your repo must contain a tag for the version number. i.e. 1.0,1.2 etc.
  * Summary - a short summary of project.
  * Description - detailed description of the project.
  * Homepage - homepage of the project.
  * License - license for the project, i.e - MIT,BSD.
  * Author - author of the repo.
  * Platform - OS and version used in the repo, i.e. iOS 9.0.
  * Source - source URL of the repo.
  * source_files - files to be included in the pod.
  * exclude_files - files not to be included in the pod.
  * Dependency - any third party dependency for the pod project.

**3.Now verify the pod spec file by using the following command:**

$ pod spec lint AppUtils.podspec

![Image title](https://dzone.com/storage/temp/4752809-verify-pod-spec-file-by-using.jpg)

> _Solve any error or warning that may occur while validating_

  * **.podspec file**

**4.Now upload the specification file to your specification repository.**

CocoaPod is using a public specification repository for the public pod. If you want to create a private pod then you have to create your own private specification repo that will store.podspec files.

![Image title](https://dzone.com/storage/temp/4752810-structure-of-repo.jpg)

Each version has its own specification file. Your specification repository can have more than one specification.

![Image title](https://dzone.com/storage/temp/4752812-specification-repository.jpg)

> _5.Specifying a private pod in Podfile._

If you are using a private pod then you have to tell CocoaPod, where the specification repository is located by specifying the source at top of the Podfile:
    
    
    Source “<path of your privatespecification git repo> "
    pod 'AppUtils', '~> 1.0'

If you don't want to create a private specification repository then create the same specification structure in your project and specify the repository URL as the source in the Podfile.

![Image title](https://dzone.com/storage/temp/4752813-2.jpg)

### Benefits

CocoaPods are widely used for third party dependency integration. Below are few benefits of using CocoaPod over manually managing Dependencies in your project.

  * Managing dependencies in your code is simplified by downloading all of them when you run the pod install/update command.
  * Manually added dependency may not be easy for another coder to locate it. Pods ensure that one can easily go through the pod scheme or a Podfile to understand all the dependencies used in the project.
  * The task of replacing a library with a new version is simplified with CocoaPods automatically by using only one command instead of manually deleting old files and adding new ones.

## Conclusion

Private pods make managing your project much simpler. It saves a lot of effort and time when dealing with dependencies in your project. Also, we can use this pod privately for internal access.

[Learn how divergent branches can appear in your repository](https://dzone.com/go?i=190140&u=https%3A%2F%2Fblog.wakanda.io%2Fanimated-git-4-understand-divergent-branches-appear-fetching-remote-repository%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how to better understand why they are called "branches". Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190140&u=https%3A%2F%2Fwww.wakanda.io%2F).
