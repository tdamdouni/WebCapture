# Should You Adopt a Single Code Repository for All Code?

_Captured: 2018-08-08 at 08:11 from [dzone.com](https://dzone.com/articles/should-you-adopt-a-single-code-repository-for-all?edition=388197&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-08-07)_

[Download the blueprint](https://dzone.com/go?i=228233&u=https%3A%2F%2Foffers.automic.com%2Fblueprint-to-continuous-delivery-with-automic-release-automation%3Futm_campaign%3DAMER%252520Online%252520Syndication%252520DZone%252520Platinum%252520Sponsorship%252520Ads%252520JULY-2017%26utm_source%3DDzone%252520Ads%26utm_medium%3DBlueprint%252520to%252520CD) that can take a company of any maturity level all the way up to enterprise-scale continuous delivery using a combination of Automic Release Automation, Automic's 20+ years of business automation experience, and the proven tools and practices the company is already leveraging.

Monorepos (putting all your code in one repository) are a fairly controversial topic in the world of software development for a number of interesting reasons. For many developers, the thought of storing every line of code in a single central repository brings them out in a cold sweat, and they have to go lie down for a while to battle with the idea. Which is understandable when you consider that monolithic source code repositories have a bad reputation.

## **Issues With Monorepos**

As well as confronting potential technical limitations with large-scale monorepos, teams also encounter performance issues for those single source control systems exceeding multiple gigabytes. Consider new or rookie developers too. During the onboarding process, they face a huge codebase to grapple with rather than receive a steady introduction to smaller repositories.

Other issues also emerge with single central repositories such as managing and restricting access control and integrating a monorepo into an existing build process. These are all largely dependent on the size of the project, team, and organization involved though thankfully and can be addressed accordingly.

Organizing your codebase using a single source control system is tricky, but the concept is no more inconceivable than it is to deal with the issues that come with multiple repositories. Enforcing standardization is an issue--especially at scale--and code can become too complex to even read. Work and effort end up being duplicated. And on top of all this, no one is able to understand a platform from end to end when there are so many source repositories involved.

As part of our DevOps as a Service consultancy program, I encourage the companies we work with to adopt a central code library for tools, training material, and other dependencies shared across services. Where possible we cull or combine others--it's a significant move to attempt to drive companies to migrate completely from multi to monorepos.

So, when it comes to repositories, there's a lot of complexity involved in both directions.

## **Different Types of Single Source Code Repositories**

There are essentially two types of monorepos:

  * Large repos containing all the code maintained by a company
  * Project-specific monorepos like Babel, React or Symfony which combine small official interdependent modules in one library

[Awesome-monorepo](https://github.com/korfuri/awesome-monorepo) contains a great collection of monorepo tools that are being used out there in the wild. Mammoth monorepos like those by Google (known as [Bazel](https://bazel.build/)), Facebook ([Buck](https://buckbuild.com/)), and Twitter and Foursquare (who both utilize [Pants](https://www.pantsbuild.org/)) have reaped the benefits of unified versioning and a single source of coding truth. [Babel](https://github.com/babel/babel/blob/master/doc/design/monorepo.md), [Symfony](https://github.com/symfony), and [React](https://github.com/facebook/react/tree/master/packages) are all notable project monorepos which have reduced complexity for the maintainers, while still providing easy-to-change modularity for the end user.

Managing code in a single central system can considerably simplify the development process of modular software projects, like microservice-based infrastructures. Monolithic source code repositories are all about moving fast and achieving project/organizational goals more efficiently. Put simply, monorepos increase developer productivity.

It's important to note at this juncture, that a single source code repository or monorepo in no way implies monolithic software design. This tends to be one of the main reasons many companies don't adopt them, but the two don't have to go hand-in-hand.

As mentioned previously, I've driven all the companies we consult with to begin to adopt some elements of this approach. Implementing a monorepo into an existing process is not easy, but it's not impossible. I begin with a single source testing library that contains all the central tools and resources that are used at the heart of each company's development pipeline. Introducing such a testing library takes us one step closer to achieving an organizational monorepo.

Within the central library, I also enforce a high level of testing coverage--aiming for an optimal 95%. This allows me to kill two birds with one stone. A single central repository ensures testing consistency and helps achieve high test rate levels. From there, it's possible to begin culling other repos slowly and overcome some of the angst involved from the team.

## **Best Practices for Monorepos**

Guidelines for optimizing single source codebases:

  * Organize your monorepo as a single tree with a number of subdirectories that look more or less like the root directory;
  * Get your naming conventions, standards, and policy in order as a disorganized monorepo is horrible to work with;
  * The root of your monorepo should contain very little (a README, and a policy);
  * Subdirectories can serve as team or project namespaces--depending on the size of the organization;
  * Identify each source file by a single strong (a file path that also includes a revision or version control number).

It is best to think of the monorepo as a learning tool. Use it to share information, training material and examples, and much more in a way that you wouldn't be able to in an app repo. Single source code repositories work best for DevOps organizations who have already adopted an open and collaborative working environment and culture. The return on investment in time and effort your team will spend in migrating to a monolithic codebase will materialize multiple times over in improved productivity and better quality code. So, what are you waiting for?

[Download](https://dzone.com/go?i=228234&u=https%3A%2F%2Foffers.automic.com%2Fblueprint-to-continuous-delivery-with-automic-release-automation%3Futm_campaign%3DAMER%252520Online%252520Syndication%252520DZone%252520Platinum%252520Sponsorship%252520Ads%252520JULY-2017%26utm_source%3DDzone%252520Ads%26utm_medium%3DBlueprint%252520to%252520CD) the 'Practical Blueprint to Continuous Delivery' to learn how Automic Release Automation can help you begin or continue your company's digital transformation.
