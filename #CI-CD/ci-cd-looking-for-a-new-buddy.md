# CI + CD: Looking for a New Buddy?

_Captured: 2018-01-26 at 18:26 from [dzone.com](https://dzone.com/articles/ci-cd-looking-for-a-new-buddy?edition=355142&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-01-26)_

**Best practices for [getting to continuous deployment](https://dzone.com/go?i=268427&u=https%3A%2F%2Finfo.rainforestqa.com%2Febook-getting-to-continuous-deployment%3Futm_campaign%3Dgetting-to-continuous-deployment%26utm_medium%3Ddisplay%26utm_source%3Ddzone) faster and with dramatic results in reduced outage minutes, development costs, and QA testing cycles. Brought to you by [Rainforest QA](https://dzone.com/go?i=268427&u=https%3A%2F%2Fwww.rainforestqa.com%3Futm_campaign%3Dhome-page%26utm_medium%3Ddisplay%26utm_source%3Ddzone).**

So first off, congratulations to our ex-neighbors (before we [moved to Bangkok](https://everyworldheritage.site/) and all) for becoming _another_ Vancouver company acquired by Apple!

**[The BuddyBuild team is now part of Apple!**](https://www.buddybuild.com/blog/buddybuild-is-now-part-of-apple)

> We're excited to share that the BuddyBuild team has joined the Xcode engineering group at Apple to build amazing developer tools for the entire iOS community.
> 
> We've always been proud to be a Canadian company, so we're also pleased that we will be staying right here in Vancouver -- a hotbed of developer and engineering talent.
> 
> The buddybuild service will remain available to existing customers to build, test, and ship iOS apps to testers through buddybuild.com…

SWEET! Big win all around, right? Right?

> As of today, we are no longer accepting new customers. Existing Free Starter plans and Android app development will be discontinued on March 1, 2018…

… oh. So if you're a little indie and/or you have an Android version, _not so much then._

Well, while we can hope that this promises that our developer memberships may be including some level of CI service in the nearish future, it's just about a guaranteed certainty that the Android side is about to become just as much a dimly remembered history as [that of TestFlight](http://www.alexcurylo.com/2014/02/21/testflight-r-i-p/). Looks like just about the same scenario in fact, the only difference this time is: they announced Apple's acquisition first!

So, let's take a look around at what options there are for the indie developer who feels the pain of those free + Android plans going away, shall we?

Here is one particular instance of that discussion being conducted online, as an issue for [GitHawk](http://githawk.com/):

> We will almost certainly lose support for this project. Time to find a new CI. Any suggestions?  
I'm reading [this article](https://medium.com/xcblog/olympics-of-top-5-cloud-ios-continuous-integration-servers-fcaa6c79468d) which offers:
> 
> I read about [Buildkite](https://buildkite.com/) and [AppCenter](https://appcenter.ms/) on Hacker News.
> 
> I'm also considering open source, self-hosted solutions so that something like this doesn't happen again:

Read through the whole discussion there: other options that showed up were

No strong consensus there, although Bitrise and Circle have positive buzz and Travis doesn't, that's what stands out.

Circle has an article here: [Migrating from BuddyBuild to CircleCI](https://circleci.com/blog/migrating-from-buddybuild-to-circleci/).

If you enjoy managing everything with FastLane, looks like that's the service for you. Those of us who want the magic to just work, we'll keep looking a bit.

Here's another fellow who went through the evaluation process and came up with a surprising answer:

> In the end, I chose to go with [GitLab CI](https://about.gitlab.com/features/gitlab-ci-cd/). GitLab CI works very similarly to BuildKite: it merely coordinates a set of agents ("runners" in GitLab parlance), who are responsible for the actual building of the project. I'm already running a GitLab server to host my Git repositories, so using it for CI didn't require any new installation or setup for my existing repositories…
> 
> … As I said above, GitLab CI is almost certainly not the right solution for your case. It's the right solution for me, because a) it's cheap, b) I was already running a GitLab server, and c) none of the other alternatives fit my needs quite as well.

OK, if you're using GitLab, self-hosted or not, that looks like the really obvious choice! Here's [how to set up GitLab CI for iOS in three relatively simple steps](https://medium.com/static-object/how-to-set-up-gitlab-ci-for-ios-in-a-few-relatively-simple-steps-56a0d88d0272).

While GitLab is a fascinating option, we expect that Github is where indie projects are likeliest to live … ours, anyways. And, as you [may remember](http://www.alexcurylo.com/2017/05/22/new-bestie-microsoft/), we were kinda impressed with Microsoft's plans for [Visual Studio App Center](https://appcenter.ms/), and haven't had any reason to go back on that since. And in what is possibly not a complete coincidence, they recently posted [Build Any App with Visual Studio App Center](https://blogs.msdn.microsoft.com/vsappcenter/hi-were-visual-studio-app-center-build/):

> At Microsoft, we strive to deliver the best developer tools on the planet in order to help make all developers more productive. With [Visual Studio App Center](https://appcenter.ms/), you can easily automate your DevOps lifecycle to continuously build, test, release, and monitor your apps on every platform, so you have more time to focus on your users and their experience.
> 
> The App Center Build service is completely free for your first 240 build minutes per month (up to 30 minutes per build) and supports iOS, macOS, Windows, and, of course, Android apps.
> 
> App Center supports apps written in Obj-C, Swift, Java, React Native, and Xamarin, and integrates with existing tools such as GitHub, Visual Studio Team Services, and Bitbucket. Once you've selected your repository, setting up build automation for any branch of your desktop and mobile apps takes just a few clicks. Additionally, App Center Build includes other cloud services, so you can run UI tests to retain the highest quality standards and distribute your apps to testers…

That's the one we're going to try next, personally; find out for ourselves just how usable in practice App Center is, because it sure _looks_ like the best multiplatform development support out there, and one that we can trust has just about as low a probability as possible of being acquired or discontinued … which seems to occur with depressing regularity to these tools of ours, doesn't it now?

And as a parting note, here's some more informed commentary and interesting speculation for WWDC 2018. Cloud Xcode Server would certainly be nice!:

**Discover how to [optimize your DevOps workflows](https://dzone.com/go?i=268430&u=https%3A%2F%2Finfo.rainforestqa.com%2Febook-getting-to-continuous-deployment%3Futm_campaign%3Dgetting-to-continuous-deployment%26utm_medium%3Ddisplay%26utm_source%3Ddzone) with our on-demand QA solution, brought to you in partnership with [Rainforest QA](https://dzone.com/go?i=268430&u=https%3A%2F%2Fwww.rainforestqa.com%3Futm_campaign%3Dhome-page%26utm_medium%3Ddisplay%26utm_source%3Ddzone). **
