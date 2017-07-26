# Continuous Integration: Its History and Benefits

_Captured: 2017-05-25 at 10:20 from [dzone.com](https://dzone.com/articles/continuous-integration-and-its-whereabouts?edition=300092&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-24)_

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

"Continuous Integration," or "CI" for short, is a concept which has been taken as a standard nowadays within our IT services and development. The concept of continuous integration means automating the overall deployment process for an application after a code has been committed. It helps in reducing bugs in the deployment process. Besides this, it also helps in reducing complexity within the code and increases clarity in each module.

The concept was initially brought in by Grady Booch in 1991, although he did not suggest making continuous integration a part of the build process for an entire application. As technologies advanced, with increased complex business procedures and software code, it became important to automate the entire process of building the entire application after every commit made by a developer, to mitigate the process of version controlling for the entire application and to channel cleaner code into the source control. Thus, continuous integration became very important for the "Extreme Programming" process. I will explain extreme programming separately in another blog.

The main concern of continuous integration is to resolve integration problems. In extreme programming, continuous integration was intended to be used in combination with automated unit tests written through the practices of test-driven development. Initially, this was conceived of as running all unit tests in the developer's local environment and verifying that they all passed before committing to the mainline. This helps avoid one developer's work-in-progress breaking another developer's work. In the same vein, the practice of continuous delivery further extends continuous integration by making sure the application checked in on the mainline is always in a state that can be deployed to users and makes the actual deployment process very rapid.

## How Does Continuous Integration Work?

To achieve the required objectives, continuous integration depends upon the following points:

### Maintain a Code Repository

This practice advocates the use of a revision control system for the project's source code. All artifacts required to build the project should be placed in the repository.

### Automate the Build

A single command should have the capability of building the system. Automation of the build should include automating the integration, which often includes deployment into a production-like environment.

### Make the Build Self-Testing

Once the code is built, all tests should run to confirm that it behaves as the developers expect it to behave.

### Keeping the Build Fast

The build needs to complete rapidly so that if there is a problem with integration, it is quickly identified.

### Making It Easy to Get the Latest Deliverables

Making builds readily available to stakeholders and testers can reduce the amount of rework necessary when rebuilding a feature that doesn't meet requirements. Additionally, early testing reduces the chances that defects survive until deployment. Finding errors earlier also, in some cases, reduces the amount of work necessary to resolve them.

### Verifying the Latest Builds

It should be easy to find out if the build breaks and what relevant changes have to be made.

### Automate Deployment

The entire process can be automated by injecting scripts into the continuous integration system. This way, we can automate the entire build just using a single script.

## Benefits of Using Continuous Integration

Continuous integration is intended to produce benefits such as:

  * Integration bugs are detected early and are easy to track down due to small change sets. This saves both time and money over the lifespan of a project.
  * Avoids last-minute chaos at release dates, when everyone tries to check in their slightly incompatible versions.
  * When unit tests fail or a bug emerges, if developers need to revert the codebase to a bug-free state without debugging, only a small number of changes are lost (because integration happens frequently).
  * Constant availability of a "current" build for testing, demo, or release purposes.
  * Frequent code check-in pushes developers to create modular, less complex code.

Besides this, continuous automated testing benefits can include:

  * Enforcing discipline of frequent automated testing.
  * Immediate feedback on system-wide impact of local changes.
  * Metrics generated from automated testing and CI (such as metrics for code coverage, code complexity, and features complete) focus developers on developing functional, quality code.

Continuous Integrations can be carried out using tools like

  * Jenkins,
  * Travis CI,
  * Bamboo.

These CI tools are very easy to use and provide available plugins so that you can integrate it with your version controlling system software and automating your build processes.

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

Opinions expressed by DZone contributors are their own.
