# 35 Questions to Ask While Creating a Deployment Pipeline

_Captured: 2017-04-12 at 20:08 from [dzone.com](https://dzone.com/articles/empowering-developers-to-deploy?edition=290884&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-12)_

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

So, you want to enable your developers to be able to deploy code. It makes sense; we live in a rather microservices-oriented world today. If you do that, then you are going to give your developers some great power. When you give them that power, you have to be careful of that process.

In this post, we are going to ask all the questions one should ask when approaching the methodology of continuous deployment and giving that power.

Note that containerized deployment is a rather new world. Most of those in the world of microservices are not there yet. In these cases, the effort required for your developers to deploy is higher. We have to adopt and create techniques for proper orchestration of our servers. We will cover the challenge in this first post. As you will see, this challenge was not fully resolved by modern orchestration tools such as Kubernetes.

## The Challenge

Deployment is not just taking an app and deploying it. Why not, you ask? Let's see all of the processes and questions that we can (and should!) raise about deployments done by developers.

  1. How do you enforce so that developers can deploy only services they are allowed to?

  2. Do you want your developers to view other deployment processes?

  3. Are you going to purchase a tool or a set of tools, or going to check out open-source solutions, or maybe, do you need to develop an in-house solution? Which deployment tools are available? Will they answer your needs?

  4. How do you integrate with all internal pre-existing services (source control, bug tracker, service deployment tracking, and any other already existing services which are affected by such a new process)?

  5. This deployment tool that we are going to build- note that it's another service and thus should be installed also with a deployment tool. Should this deployment tool be deployed by the deployment tool itself?

  6. Do we need infrastructure alerts? (Those are both alerts tightly related to the deployment tool itself if it's stuck or down.)

  7. Applicative alerts: We want to have alerts on the status of the microservices itself, so do we need any new alerts as part of automating the deployment process?

  8. How do we validate that a microservice has been installed successfully? What if it has started up, but in the wrong version?

  9. Which stronger validations do we want to enforce once we let developers deploy their services (obviously, developers come from different places)?

  10. What if we want to block deployments for a certain region or segment, or for certain teams? How can we achieve that? Who should have access to this block?

  11. Do we want a project per microservice deployment, or do we want a global deployment tool where developers can choose the project they want to deploy from a list?

  12. Are there new conventions and enforcements we might want to enforce? Should RND project names, for example, match RPM name? Or do we rather configuration?

  13. How do we support gradual rollout?

  14. Should we allow deployment to cross the data center or let the developer deploy the data center by data center?

  15. Should developer care if we have multiple data centers? (All he wants is to run his code.)

  16. Should our tool support both legacy platforms and modern ones such as Kubernetes and Swarm or do we solve one problem at a time? Should we have a shared interface?

  17. How do we integrate users management with existing user and group management already existing?

  18. What if a developer post-deployment needs to access (SSH) one of his services and do an operation? Should we enable him or her to do that? Or direct him or her to the production team for such access?

  19. Which additional visibility on services should we enable to the developer?

  20. How do we manage rollback? Now that developers are going to run more deployments, we need to support a quick rollback, possibly one-click rollback. Is it the same process as upgrade- only a different version or is it actually a different rollback? What if rollback fails? Do we provide enough tools for developers to mitigate such problems? Or should we not?

  21. What is the discovery mechanism? Do we let developers deploy to specific services, or only by a general discovery mechanism (such as service name deployment)?

  22. If a developer has a pull request, should he merge it externally to the deployment process or have the deployment pipeline do it for him?

  23. Which info should we show the deployer prior to him making a deployment? Should we show warnings?

  24. If a deployment failed in one of the stages, how do we make sure the target deployment environment gets clean?

  25. If the deployment process involves changes to the database, how will the deployment pipeline support that? Should it support it at all?

  26. How can the deployment process support both standard microservices and other types of jobs such as Hadoop jobs or Spark jobs? Should we mess with jobs at all? Maybe at future phases?

  27. Should the deployment process support the deployment of intrastructure- and production-related changes such as network configuration?

  28. How will the deployment pipeline be integrated with an already-existing system and end-to-end tests?

  29. Would you like to make sure the same deployment pipeline is run on production, QA, CI, local development environment, or going to fall into the trap of having it a production-only tool?

  30. Which insights and analytics do you want to derive from such a deployment pipeline?

  31. Which system tests and end-to-end tests are you going to create for this deployment pipeline and how are you going to run them? (Testing the deployment tool itself.)

  32. How do you create such a pipeline process without introducing yet another layer to manage, could this layer save other deployments layers from happening or would it add an additional one?

  33. Which resiliency mechanisms do you need in this deployment tool? When would you want to retry, for example? Which timeouts do you need in place?

  34. Is the deployment pipeline a microservice? Is it a set of microservices? A monolith, God forbid (or God bless)?

  35. _Many _more. But you get the idea.

## Summary

In this post, we saw that the continuous deployment pipeline is not just the usual _Developer commits > Tests are run > Deploy to CI > QA > Production_, assuming all is successful. There is much more complexity in it, and if you want to do it right, you have the ask the right questions. Now that we have asked some of the main questions, in the next posts, we will try to analyze this subject more and even answer some of the questions.

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

Opinions expressed by DZone contributors are their own.
