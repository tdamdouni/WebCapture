# GitLab vs. GitHub for Open Source Projects

_Captured: 2018-02-03 at 20:35 from [dzone.com](https://dzone.com/articles/gitlab-vs-github-for-open-source-projects?edition=358115&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-02-03)_

**Best practices for [getting to continuous deployment](https://dzone.com/go?i=268427&u=https%3A%2F%2Finfo.rainforestqa.com%2Febook-getting-to-continuous-deployment%3Futm_campaign%3Dgetting-to-continuous-deployment%26utm_medium%3Ddisplay%26utm_source%3Ddzone) faster and with dramatic results in reduced outage minutes, development costs, and QA testing cycles. Brought to you by [Rainforest QA](https://dzone.com/go?i=268427&u=https%3A%2F%2Fwww.rainforestqa.com%3Futm_campaign%3Dhome-page%26utm_medium%3Ddisplay%26utm_source%3Ddzone).**

GitHub is the standard nowadays, not only as a source code repository, but also as a place of collaboration for open-source projects; a lot of the interaction between project members and the wider community is made through GitHub Issues or Pull Requests.

![](https://cdn-images-1.medium.com/max/800/1*OLsrVuctE2DO924KoSkNLA.png)

As such, GitHub is often referred to as "the Facebook of open-source development," and rightly so. GitHub has made the act of forking a project as easy as clicking on a button, arguably lowering the entry barrier for people looking to fix bugs on projects they use, making it trivial to also share this fix back upstream.

But, ironically, GitHub itself isn't open-source.

Because of that, we decided to give GitLab a try when we bootstrapped Qaclana, and here is a list of things we've learned during this last months.

## GitLab Is a Great Place to Start a Project

GitLab is a complete solution and the hosting of Git repositories is only part of the story, making it easy to get started. Deciding which CI tool or issue tracker to use can be postponed, so that you can just focus on your core project.

![](https://cdn-images-1.medium.com/max/800/1*xrxm3wzgIzyOaDqCs4LXDg.png)

> _Qaclana's pipeline as seen on GitLab._

The integration with their own CI tool makes it easy to visualize the builds and pipelines. The killer feature, though, is `gitlab-runner`: just install it on your machine and enable this local runner on GitLab's CI/CD UI and, suddenly, you have your own build executor. This is helpful to speed up builds and to analyze build failures. To have something similar for projects hosted on GitHub, tools like Travis or CircleCI would have to be used.

![](https://cdn-images-1.medium.com/max/800/1*iJ856FpXsTEktrxYWQIe3w.png)

> _Qaclana Kanban Board on GitLab._

GitLab's Issue feature is very similar to GitHub's, but its Boards view is a huge improvement, making it easy to move cards among columns. This can be done on GitHub using external tools like waffle.io, but having "one UI to rule them all" is a major win.

Those are two of the major differences for Qaclana, but we do see other features that might be interesting to people in other projects. For instance, the ability to start Kubernetes clusters a la CodeFresh for testing or staging environments look very interesting.

Another noteworthy and interesting feature is the Container Registry. We are using it only for pushing intermediate images for the build pipeline, but it could be interesting to have it to host the actual images for a project that won't, or can't, use Docker Hub.

## Final Words

During this last few months, we've seen features being implemented in GitHub which were first available in GitLab and vice-versa. Technically, they are very similar and close to each other, with major differences mainly in the philosophy: while GitHub focuses on high availability and performance of its basic core features, delegating tangential or complex features to external tools like Travis or Waffle, GitLab tries to incorporate all features on a single, well-tested and well-integrated package.

All in all, these last few months using GitLab felt like using a mature Git repository on-par with GitHub regarding its core features, plus a well-curated set of plugins, all being part of the same single, consistent UI.

The only missing "feature" on GitLab is the vibrant community that is present on GitHub. But perhaps that could change soon?

**Discover how to [optimize your DevOps workflows](https://dzone.com/go?i=268430&u=https%3A%2F%2Finfo.rainforestqa.com%2Febook-getting-to-continuous-deployment%3Futm_campaign%3Dgetting-to-continuous-deployment%26utm_medium%3Ddisplay%26utm_source%3Ddzone) with our on-demand QA solution, brought to you in partnership with [Rainforest QA](https://dzone.com/go?i=268430&u=https%3A%2F%2Fwww.rainforestqa.com%3Futm_campaign%3Dhome-page%26utm_medium%3Ddisplay%26utm_source%3Ddzone). **
