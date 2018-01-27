# Architecting for CI/CD

_Captured: 2017-10-10 at 20:17 from [dzone.com](https://dzone.com/articles/architecting-for-ci-cd?edition=329552&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-10-10)_

"[Automated Testing: The Glue That Holds DevOps Together"](https://dzone.com/go?i=236222&u=http%3A%2F%2Finfo.saucelabs.com%2FAutomated_Testing_Glue_LP-DZone.html%3Futm_medium%3Dpre-roll_textlink%26utm_content%3Darticle) to learn about the key role automated testing plays in a DevOps workflow, brought to you in partnership with Sauce Labs.

## Fast Management of Environments

Fast-moving teams can't wait to get environments for builds and testing in place, nor can they wait for already overloaded DBAs to manually inject data or schema changes.

This need for speed requires changes to how infrastructure and environments are managed. Cloud-based hosting offerings like Microsoft's Azure or Amazon's Elastic Computing Cloud (EC2) allow teams to offload their build and server management. Services like Sauce Labs also offer physical mobile device farms for support of huge matrices of devices.

### Self-Service for Teams

Fast-moving teams need self-service. Organizations need to move system management and access rights down from centralized administration to individual teams. This means understanding how to wrap concerns such as HIPAA or Sarbanes-Oxley into the power of automation via a delivery pipeline to handle security, artifact storage, configuration, and auditing.

There are affordable, industry standard solutions for these concerns. In addition to the cloud-based solutions mentioned above, on-premises solutions range from commercial products like VMWare to open source containers like Docker.

These tools make it simple to wrap in a CI/CD toolset. Scripts, plugins, adapters, etc. to manage infrastructure are available for every popular solution listed above-it's simple to tie provisioning and deployment into a job on Jenkins or other toolsets.

### Scriptable Databases

Scriptable database changes mean storing schema and data in source control right alongside the appropriate version of the system code. Many toolsets offer this scripting for major databases, regardless whether they're traditional RDBMSs or "NoSQL."

### Scriptable Data

Well-designed applications have APIs exposing major functions: create a user, an account, or a product. Wrapping that in a command-line application is trivial. With this feature in hand, programmers can create test data sets that are imported automatically for any test.

Once the team has achieved the trifecta of fast self-service scriptable environments, scriptable databases, and scriptable data, the continuous deployment system can truly run end-to-end tests atomically.

## Feature Management

Too often organizations ignore the impact of business implementation: What features are selected, how they're conceived, and how they're coded up.

### Smaller Features

Smaller features are generally less complex, making them easier to build as part of a CI/CD pipeline. It's easier to build, integrate, test, and deploy a smaller component with a small set of APIs, database changes, and UI versus a huge footprint of massive schema updates, interwoven service dependencies, and numerous components to be installed for the end user.

### Switchable Features

Smart teams design their systems so wholesale features can be toggled on or off to make the system more testable. This allows bypassing hard-to-test capabilities like CAPTCHA and focus on a larger flow.

Moreover, feature switching can be used for much larger chunks of functionality. You could deploy to your entire production farm, but enable features only on a carefully monitored small number of servers. This allows you to gradually roll out your features to a small population, ensure they're working properly, and gradually turn on those features to more and more users.

## Process

Moving to a pipeline that constantly delivers high-quality, well-tested software is often more a process change than a technical one. Technical roles also have to adapt how they're doing their work in order to successfully move to a CI/CD model.

### Moving to Smaller Branches

Branching strategy is something often as hotly debated as tabs versus spaces or Emacs versus Vim. The branching strategy a team chooses will have a significant impact on the team's ability to work as smoothly as possible in a CI/CD environment.

Small branches allow teams work isolated from others' churn in the codebase. Dependency management across branches is still an issue, but it's lessened by good communication around APIs and automated tests to guard against regressions.

### Tests in Source Alongside Code

Keeping automated tests in sync with the system they cover is critical to automated delivery pipelines. The smoothest approach to handling this is simply keeping automated test code in the same repository as the system code.

Organizing test and system code in a repository is something each project team needs to work out for their own requirements. A common approach is to have unit tests close in layout to the code they're testing, as shown in the following figure. Source code is under `/src/main` with test code under` /src/test.`

![](https://az184419.vo.msecnd.net/sauce-labs/cicdcode.png)

## Code

Finally, let's consider technical impacts in a codebase to ensure good testability in a fast delivery pipeline.

### Leveraging APIs for Testability

Public APIs are a crucial piece of any well-architected system, regardless of whether it's a monolithic system or one composed of numerous service-based components. Those APIs provide a way to dramatically improve automated testing of a system in a delivery pipeline.

Imagine a test that checks if a customer can search for a particular item and place it in a shopping cart. Good automated tests avoid sharing state and data between themselves. This requires data for a test to be randomly or uniquely generated. Pseudo code for setting up prerequisites might look similar to this:

Each pseudo method uses something like the Faker library to randomly generate appropriate data and in turn calls the true system APIs to create real objects with the randomly generated data.

### Managing Code Dependencies

Injecting dependencies on external services is one way teams can stand up systems in lower environments without being reliant on those external systems. As an example, imagine a payroll system with a call to an external security system.

With a properly architected system, a test could simply swap out a call to the "real" security system for a fake call that simply approves a test user as needed. This cuts the dependency to that external system, ensuring tests could run in lower environments, or within unit tests themselves.

## Closing

Moving to a well-tested CI/CD pipeline requires significant effort from organizations. It involves process and policy changes across your entire organization. The payoff can be extraordinary: continual improvement as the organization moves to constantly deliver high-quality, well-tested value to their customers.

This post is a shortened version of a [longer whitepaper](https://saucelabs.com/resources/white-papers/designing-infrastructure-for-continuous-testing-and-ci-cd) available on the Sauce Labs website.

[Learn about the importance of automated testing](https://dzone.com/go?i=236223&u=http%3A%2F%2Finfo.saucelabs.com%2FAutomated_Testing_Glue_LP-DZone.html%3Futm_medium%3Dpost-roll_textlink%26utm_content%3Darticle) as part of a healthy DevOps practice, brought to you in partnership with Sauce Labs.
