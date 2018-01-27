# Contributing to OpenFaaS without writing any code… (yet)

_Captured: 2017-11-17 at 21:57 from [hackernoon.com](https://hackernoon.com/contributing-to-openfaas-without-writing-any-code-yet-846dd014514f)_

I am a web developer by trade. My primary coding languages are Javascript and C#.

![](https://cdn-images-1.medium.com/freeze/max/60/1*QCJbAYR1kOoPuTGny-6q1g.png?q=20)![](https://cdn-images-1.medium.com/max/1600/1*QCJbAYR1kOoPuTGny-6q1g.png)

I found the OpenFaaS project as a potential solution to the problem of a microservice architecture with all these servers being deployed for minimal functionality. The project is very open and welcoming to new contributors (see my other post "[My First Pull Request to OpenFaaS -- a major open-source project!"](https://hackernoon.com/my-first-pull-request-to-openfaas-a-major-open-source-project-d0c823790691)). I wanted to contribute, to give back to the project, and be a part of this great team. The [contributing guide](https://github.com/openfaas/faas/blob/master/CONTRIBUTING.md) is very detailed and offers suggestions on how to get started.

![](https://cdn-images-1.medium.com/freeze/max/60/1*Iok1KfylaD6P7ZLx_x4WvQ.png?q=20)![](https://cdn-images-1.medium.com/max/1600/1*Iok1KfylaD6P7ZLx_x4WvQ.png)

> _A variety of languages are included in the project_

[OpenFaas](https://github.com/openfaas) is primarily written in Go with a mix of other languages mostly for the sample functions.

I am not a Go developer. I understand the basics. I went through the [Learn Go By Example](https://gobyexample.com/) and have been able to write some small command line tools that I use, but nothing on the level of OpenFaaS.

So, what can a web developer who primarily works in Javascript do to contribute to this project? How do I become part of this amazing team without being an expert in the primary language it's written in?

Of course, I could help out with the UI piece of the project since I'm familiar with that type of development, but I want to get into the core of this! I want to give back and learn in the process!

### Some of the other ways to contribute

  * **Testing Others' Pull Requests**
  * **Offering Suggestions/Use Cases**
  * **Answering Questions On Issues**
  * **Documentation**
  * **Community and Social Media**

You don't need to be an expert on the language the code is written in to know if it works the way it should. Some of the code changes are complex, but the result may be a new feature (like authorization), or a fixing a bug that has been reported. You don't need to know how the code works to test that the feature works as expected, or that the bug is no longer present.

Added bonus, after going through the testing, look at the diff to see what was changed that made it work. You'll have a better understanding of how the code works.

OpenFaaS has a very active community on their Slack workspace. All it takes to get in is to send a simple email to [alex@openfaas.com](mailto:alex@openfaas.com) with a little introduction about yourself. From there, let everyone know what you're doing, or planning to do with the project. If some functionality doesn't exist yet, or doesn't work the way you need it to, someone can help work it out.

You don't need to write the code to do it, although the team encourages and offers a lot of help if you do want to try it yourself.

At the time of writing, there are 4 open issues with the tag "[question](https://github.com/openfaas/faas/issues?q=is%3Aissue+is%3Aopen+label%3Aquestion)". Some of these are questions on how to accomplish something with OpenFaaS. If you've used the project, you may know something, or been through a similar situation as the person asking the question.

Share your experience and help someone get the most out of OpenFaaS. This will help everyone on the team and the user community.

Speaking of helping out the community, updating the documentation is a very valuable task! It's generally the first thing someone looks at when they hear about the project. It's important that it stays up-to-date and accurate, and doesn't require any code!

It's also possible to contribute without even going into the Github repo, by writing a blog post about what you're doing with OpenFaaS, sharing a Tweet about it (@openfaas), or any other social media outlet.

Start a local Meetup about OpenFaaS, or make a presentation at an existing Cloud, Docker, or Serverless meetup that you already attend. Even mention it to your team at work, perhaps there's a problem that could be solved using serverless functions.

Anything that makes OpenFaaS more visible is also contributing and helps the project grow. There's a great [community file](https://github.com/openfaas/faas/blob/master/community.md) that showcases all the blogs, presentations, events, and repos that involve OpenFaaS as well. Once you publish something, make a PR to join the list!

These are all great ways to quickly become part of the growing team of contributors. Also, it will help get you comfortable with everyone on the project, and more familiar with how it all works. If you were interested, you could start looking into some of the issues marked with the "[skill/beginner](https://github.com/openfaas/faas/issues?q=is%3Aopen+is%3Aissue+label%3Askill%2Fbeginner)" label and get your hands in the code.

For more suggestions, check out the [contributing guide](https://github.com/openfaas/faas/blob/master/CONTRIBUTING.md) or join the Slack community by sending an email to [alex@openfaas.com](mailto:alex@openfaas.com).

My little success story starts with a (relatively) simple issue to add the ability to push a Docker image up to Docker Hub when the automated (Travis CI) build completes successfully. This was not a difficult task, and it didn't require writing any _real _code. However, what it did do is get me talking with the team and opened the gates for more contributions.

Since then, my first contribution has been replicated to another project within the OpenFaaS organization, [faas-netes](https://github.com/openfaas/faas-netes) (the Kubernetes backend for OpenFaaS). I also wrote a little Go code to be able to turn off the verbose logging and optionally enable it for debugging, as well as writing 2 blogs about my experiences and sharing with my colleagues at work. I'm becoming much more comfortable with the project and code base so that I can soon begin to dive into the core of the project!
