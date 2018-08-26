# How to Share and Sync Code Between Microservices

_Captured: 2018-03-14 at 15:53 from [dzone.com](https://dzone.com/articles/how-to-share-and-sync-code-between-microservices?edition=368193&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=microservices%202018-03-14)_

A microservice architecture is great for building scalable codebases with less coupling, better separation of concerns, improved resilience, combining different technologies and most of all, better modularity and reusability for the components that build it.

However, modularity and reuse may often result in high-coupling or code duplications. Having different services tied to the same shared-lib undermines why we use services in the first place.

Using new open source technologies [like Bit](https://bitsrc.io), it becomes easier and more effective than ever to share and reuse common code between our microservices. Let's see why and how.

## ![Sharing code between microservices](https://dzone.com/storage/temp/8338136-blog-image-02-1.png)

> _Sharing code between microservices_

Sharing Code Between Microservices

Before explaining how Bit can help solve this problem, let's set the main goals we want to achieve.

  1. Sharing common code between our microservices while keeping our code DRY.

  2. Avoiding coupling through shared-libs which eliminates the advantages of separating development process. 

  3. Enable simple changes and sync to the code we share between our microservices.

Microservices are prawned to code duplications. For example, any service which is used by other services will cause all these other services to duplicate the code needed in order to use that service's API.

Creating an NPM package (with a new repo) for any such piece of code is highly impractical, and will generate a lot of overhead while making it harder to make changes to the code.

## No Shared Libs, No Coupling  
![Image title](https://dzone.com/storage/temp/8339333-10-29-readme-illustration-03.jpg)

[Bit ](https://bitsrc.io)is an open source project which brings a whole new approach to how we share and reuse code in our microservice architecture. Using Bit, you don't have to create a new repository or configure packages to share code instead of duplicating it.

Instead, you can simply define reusable parts of any existing repository and share to the other repositories - as packages or as tracked source code. This way you can make parts of any service reusable from other services without changing a single line of code in your codebase, creating more repos, or coupling your microservices together.

The best part is, Bit also lets you make changes to the code you share with any other service- so you can develop and modify that code from basically any repository.

## Example Workflow

Instead of coupling your micro-services together via common libraries, you can simply isolate and sync any reusable code using the Bit's ability to isolate and track source code among projects. You can even still install this code with NPM in different repos, and still make changes from any end.

Let's use Bit to isolate and share the reusable components `left-pad`, `some-logic` and `hello-world` in the following project's directory structure.

First, let's [install Bit](https://docs.bitsrc.io/docs/installation.html).

Let's [initialize Bit](https://docs.bitsrc.io/docs/initializing-bit.html) for the project.

Let's [add the components](https://docs.bitsrc.io/docs/isolating-and-tracking-components.html) to be tracked by Bit.

Let's add [build](https://docs.bitsrc.io/docs/building-components.html) and [test](https://docs.bitsrc.io/docs/testing-components.html) environments.

Now let's [lock a version](https://docs.bitsrc.io/docs/versioning-tracked-components.html) and isolate the components from the project.

Now let's [share](https://docs.bitsrc.io/docs/organizing-components-in-scopes.html) the components to a remote [Scope](https://bitsrc.io/).

Note that using the `\--eject` flag you can also remove an exported component from your source-code and add it as a package dependency in your project's `package.json` file.

That's it. You can now [install the components](https://docs.bitsrc.io/docs/installing-components-using-package-managers.html) using your favorite package manager, or use `bit import` to [bring their source code](https://docs.bitsrc.io/docs/importing-components.html) into any repository, make changes and sync them across your codebase.

## Conclusion

Microservices provide increased modularity and separation for your development process. Many services will use the same code, so sharing code between them is critical for your development and maintenance efforts.

However, coupling services through shared libs might ruin the point of having multiple different services. Creating different repos to publish every few code lines as a package to NPM isn't practical.

Using new technologies like [Bit ](https://bitsrc.io)we can have the best of both worlds: easily share common code between our microservices, make and sync changes from any end and avoid the coupling created via adding third party shared libraries.

Hope you found this useful!
