# Analyzing Codebases: Part I

_Captured: 2017-03-26 at 19:32 from [dzone.com](https://dzone.com/articles/methods-for-assessing-existing-codebases-part-1?edition=286925&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-26)_

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

In [Taking Over a Project: Part I](https://dzone.com/articles/taking-over-a-project-part-1-1), we discussed the necessary tasks to be executed while assessing and taking over existing projects -- namely, producing an easy-to-maintain project and capturing the important aspects of a project through valuable communication with previous project owners.

In "Analyzing Codebases Part I", we are going to learn how to use Git version control together with a few more powerful tools which can actually provide invaluable information, possibly more than the previous project owners. We'll take code metrics from Kubernetes open source, which would serve as an existing test case project for code complexity, and find hotspots in it.

In _Cyclomatic Complexity and Lines of Code: Empirical Evidence of a Stable Linear Relationship_, by Graylin Jay, Joanne E. Hale, Randy K. Smith, David Hale, Nicholas A. Kraft, and Charles Ward, academic research shows the relationship between simple code measurements such as LOC and more complex code complexity metrics such as Cyclomatic Complexity (CC). Researchers have carried out a large empirical study of the relationship between LOC and CC for a sample population that crossed languages, methodologies, and programming paradigms. The research shows that the linearity of the relationship between these two measurements has been severely underestimated. This means LOC is an extremely simple metric, which is an excellent measurement to detect code complexity.

We are going to utilize forensic psychology techniques that were adapted to software development as presented by Adam Tornhill in his great work and his book, _Your Code as a Crime Scene: Use Forensic Techniques to Arrest Defects, Bottlenecks, and Bad Design in Your Programs_. Specifically, in the second post, we'll focus on tools setup and very basic complexity metric measurements that will allow us a better analysis of our code.

![](https://lh6.googleusercontent.com/a44hcCZeYCKB6IYM2My7i4Bk1kWHX_XObEkePGB8kmmhte3GK2zuopUymHMbZOKbG4NTzxBFnKMPDguyczwMU6UEx7JUr2VmGjUoN_oAcITrPZ3Njf3cCsJyJ_xccgudrlu2UeBMDXs9Zqg5Fw)

> _Points scored_

_Figure 1. LOC and CC Linear Relationship based on empirical evidence collected by papers such as, "Cyclomatic Complexity and Lines of Code: Empirical Evidence of a Stable Linear Relationship."_

## Analysis Plan

  1. **Clone** Kubernetes, Code Maat, and its scripts; clone CLOC.

  2. **Run** LOC complexity metrics.

  3. **Run** Code frequency complexity metrics.

  4. **Integrate **LOC and code frequency metrics for global complexity.

  5. **Run **module coupling metrics.

  6. **Identify **hotspots.

  7. Plot **clustering and coupling**.

## The Analysis

I don't like installing stuff and cluttering my development laptop. Therefore, I'm going to utilize a docker whenever possible to keep my laptop clean for the experiments.

Let's start by cloning Code Maat and compiling it into a standalone JAR:
    
    
    $ docker run -it --rm -v "$PWD":/Users/tomerb/tmp/blogspot/code-maat -w  /Users/tomerb/tmp/blogspot/code-maat clojure lein uberjar

We are using Docker's clojure container in order to compile a Code-Maat JAR, and in order to avoid installing clojure and its build tool (lein).

Let's run a Code-Maat generated JAR:

We have successfully compiled clojure without having clojure directly installed. Yay!

Now let's clone Kubernetes sources:

Formatted logs for Kubernetes Git log:
    
    
    $ maat -l k8s-git.log -c git2 -a summary

Let's view the header for this file:

Let's get a brief summary of the Git traffic on Kubernetes since January 1, 2016:
    
    
    $ maat -l k8s-git.log -c git2 -a summary

Since January 1, 2016, there are 698 authors (some of them could be automatic robots such as merge robots) on the Kubernetes project, with 111K commits. That's what we call a project with some development going on!

Distribution of changes across entities:

Kubelet is the module with the highest developer activity -- 330 changes. It's not that surprising to find that as Kubelet is indeed one of core components of Kubernetes; however, it may raise some questions about its stability.

> "The relative number of commits is a surprisingly good predictor of defects and design issues."

Looking at the source code for Kubelet.go, we find that the last update time was 16 minutes earlier!

It's 2,185 LOC. That's quite a lot!

Digging deeper inside its source code, we see this:

So, it has some dependencies even if conceptual ones are in the docker! This is not the perfect sign. I would expect some dependency injection at least! Anyway, this is a rather big file, and it's the kubelet that's one of the core components; obviously, a lot is going on there.

Let's look at the recent changes to Kubelet.go from 17 hours ago:

A rename from release_1_5 to clientset.

Note: According to the docs, Kubernetes used to keep multiple releases in the main repo, and now that they use `client-go` to do the versioning they no longer need to explicitly write the revision, so this change is a refactor and cleanup.

In the same, way we see that:

## Summary

In this post, we have reused a few tools with very basic analysis from _Your Code as a Crime Scene: Use Forensic Techniques to Arrest Defects, Bottlenecks, and Bad Design in Your Programs_. We can now begin sniffing a huge codebase with 1.8M LOC and get to places where we suspect most traffic is going, which leads us to a better investment of our time. We should concentrate on these modules. We immediately see that Kubelet gets lots of traction, so even without knowing the internals of Kubernetes we could guess this as the main module and one we should focus on. These techniques can, of course, be applied to any project.

In the next post, we are going to dive deeper into code analysis and get a better understanding of where the hotspots are.

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

Opinions expressed by DZone contributors are their own.
