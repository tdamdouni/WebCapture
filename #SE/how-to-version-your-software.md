# How to Version Your Software

_Captured: 2018-09-15 at 09:36 from [dzone.com](https://dzone.com/articles/how-to-version-your-software?edition=397192&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-09-14)_

Find vulnerabilities in your open source libraries in seconds. [Get your 30 day free trial today!](https://dzone.com/go?i=306522&u=https%3A%2F%2Fapp.sourceclear.io%2Fsignup%3Futm_source%3Ddzone%26utm_medium%3Dtextroll%26utm_campaign%3Dsca%26utm_content%3Dfree-trial)

I often receive questions about software versioning. Although it seems something trivial and simple, when people start thinking about it, several questions pop up: "How can we uniquely identify our software? Which versioning scheme should we use for our software? Which version of the software is delivered to our test or production system?" With this post I hope to give some answers to these questions and provide some of the choices you have.

## Why?

Why do we need a version anyway? Well, you need some way to uniquely identify the software you have delivered. You have, of course, the elaborate release notes containing all the features and bug fixes of your release/version, but it is easier to talk about a release when you give it a name or number. When you add extra information to it, it is also possible to give information about the state of your software. Think about Alpha, Beta, Release Candidate releases. Adding this information tells something about how mature the release is. Besides that, when one of your users is reporting a bug, it is necessary for the development team to know the version of the software the bug is being reported. This is even more important when you have multiple versions of your software running.

## Different Types of Versioning

There are numerous variations to think of how you can version your software. Which variation you choose is not so important as long as you keep the following aspects in mind:

  * The version identifier must be unique, never re-use the same identifier;
  * Choose an identifier which has some logical sequence in it, e.g. alphabetical, numbers, ... This way, your users will automatically know that version 2 came after version 1 for example.

There are quite a lot of different types of versioning schemes. I will discuss some of the options you have, taken from my experience and what I have encountered during my career. Eventually, it is up to you which one you decide to choose.

### Semantic Versioning

One of the most used versioning schemes is the [semantic versioning](https://semver.org/). Taken from the semver website, the versioning scheme works as follows:

Given a version number MAJOR.MINOR.PATCH, increment the:

  * MAJOR version when you make incompatible API changes,
  * MINOR version when you add functionality in a backwards-compatible manner, and
  * PATCH version when you make backwards-compatible bug fixes.

Additional labels for pre-release and build metadata are available as extensions to the MAJOR.MINOR.PATCH format.

When you are developing libraries, this is the versioning scheme to use. Also, a lot of software vendors use this versioning scheme, like Atlassian (JIRA), GitLab, and more. When you create a Spring project on [start.spring.io](https://start.spring.io), your starting version number will also be 0.0.1-SNAPSHOT. It is a very clear way of showing your users what the possible impact is when using a new version. Following additional labels can be used: alpha (a), beta (b), release candidate (rc), release (r), etc.

### MAJOR.MINOR Versioning Scheme

Sometimes, the semantic versioning scheme can be to elaborate to use. In that case, you can choose a shorter form and use a MAJOR.MINOR versioning scheme (e.g. 1.2). Whether you increment the MAJOR or the MINOR number is up to you and subject to personal judgement, but in general it is not so difficult to decide which one to increment. You can choose for an incremental numbering, but you can also choose to use the year of first release date as the MAJOR number like JetBrains is doing with IntelliJ (e.g. 2018.1). Choose this versioning scheme when you want to keep it simple, but still want to be able to give some information about the impact of the release to your users.

### Name Versioning Scheme

Another variant is to use names for your releases. Something like Android is doing with their releases, although they also have a MAJOR.MINOR version (e.g. version Nougat which corresponds with version 7.0). The versioning name corresponds to the aspects we previously mentioned for versioning schemes. Since it is alphabetical, it gives information about the sequence of the releases. You can be creative on the topic you choose: e.g. choose names of planets or stars when you develop software for a space project, use the NATO alphabet for air traffic systems, and so on.

### Basic Versioning Scheme

When all of the above still sounds too complex, you can choose for using a single incrementing digit (e.g. version 1, version 2, ...). When developing custom made software, this versioning scheme can be very useful, simple and clear for the users.

## Internal Versioning Scheme

Up till now, we have talked about the external versioning scheme to use. This is the versioning scheme which is visible for your users and which will be used when communicating about releases between you and your users. For internal use, this external version does not contain enough information. Your development team (software developers, testers, analysts, ...) need to know which software is running on which machine (test, acceptance, production) corresponding to your Version Control System (VCS). Up to the moment you have released the software to production, the same external version is used and therefore there is a need to distinguish between builds which have the same external version. So, when you are using Git, the only thing you need is the Git commit hash to uniquely identify a release for internal purposes. When using a CI server, it is also interesting to know what the build number from the CI server is.

To summarize, we need at least the following information:

  * A unique number/name to identify the external version (it is not necessary to know it when starting with development, it must be know the latest when you start building your official release for your users);
  * A unique identifier which corresponds to your VCS (at least e.g. the Git commit hash, but it is also useful to add the branch name);
  * The build number of your CI server.

Several other information can be added like the machine the build was created on, the build date and time, and so on.

Ensure that you don't have to add all of this information manually. This information must be added automatically during your build process. The external version is something you will change manually, but all of the other information must be added automatically. The easiest way is to add this information in a plain text file and add it to your release. For ease of access, ensure that anyone who wants to view the version information, can easily retrieve it. You can make an "About" dialog in your application or provide an URL where the information can be retrieved. When using Spring Boot and Maven, you can make use of the Git Commit Id Plugin which provides the above functionality out-of-the-box. In a [previous blog](https://mydeveloperplanet.com/2018/02/22/maven-git-commit-id-plugin/), I explained how you can incorporate this plugin into your build and how you can use it with, e.g. [Spring Actuator](https://mydeveloperplanet.com/2018/04/18/spring-boot-actuator-in-spring-boot-2-0/). When you are using another build tool, the above can also be added by using shell scripting, so there is no excuse for not adding the information to your build. The steps to take are:

  * Create a shell script which writes the necessary information to a text file;
  * Invoke the shell script during your build and make it part of your deliverables;
  * Provide a URL in order to retrieve the version information.

## Conclusion

Decide for your software application which external versioning scheme to use. It doesn't really matter which one you choose, as long as it is comprehensible for your users. Ensure from the beginning of your development that the internal version information is automatically generated during your build, this will prevent any unclarities and will save you a lot of time.

Software composition Analysis for DevSecOps. [Start finding vulnerabilities](https://dzone.com/go?i=306523&u=https%3A%2F%2Fapp.sourceclear.io%2Fsignup%3Futm_source%3Ddzone%26utm_medium%3Dtextroll%26utm_campaign%3Dsca%26utm_term%3Ddevsecops%26utm_content%3Dfree-trial) in your open source components today.
