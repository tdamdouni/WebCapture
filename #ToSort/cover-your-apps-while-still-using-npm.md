# Cover Your Apps While Still Using npm

_Captured: 2018-01-15 at 20:51 from [dzone.com](https://dzone.com/articles/cover-your-apps-while-still-using-npm?edition=352124&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-15)_

[Get deep insight into Node.js applications](https://dzone.com/go?i=200144&u=http%3A%2F%2Fpages.nodesource.com%2Fnsolid-free-trial-dzwd.html%3Futm_campaign%3DDZONE%26utm_source%3Dbumper%26utm_content%3Dbtext) with real-time metrics, CPU profiling, and heap snapshots with N|Solid from NodeSource. [Learn more](https://dzone.com/go?i=200144&u=http%3A%2F%2Fpages.nodesource.com%2Fnsolid-free-trial-dzwd.html%3Futm_campaign%3DDZONE%26utm_source%3Dbumper%26utm_content%3Dbtext).

Every once in a while, the JavaScript and Node.js ecosystem experiences something that is deeply disturbing to many developers: an outage of the npm registry.

Whenever this happens, we hear outcries that npm is the single point of failure for the entire ecosystem and that the entire ecosystem is doomed because of this.

In reality, the way that both the npm CLI and npm registry (and Yarn's equivalents, for that matter) were built is extremely tolerant to enabling you to make reliable systems. The CLI is highly configurable and allows you to be registry agnostic-as long as the CLI gets the payload it expects from the registry it's pointed at, it will install the module it's instructed to install. Similarly, the npm registry is flexible and open - anyone can replicate the npm registry at any point, and there is a suite of options for registries across the globe.

We gravitate toward the default, though. It's easy to get going with Node.js and npm and get lodash by just downloading Node.js and typing `npm install lodash`, so much so that we're _conditioned_ by the ecosystem to do this. There's zero barrier to entry there, which is one of the most enabling parts of the ecosystem.

![](http://images.contentful.com/hspc7zpa5cvq/2QNiCvfMZakO6EAuUEiOo8/a88b50a4e0e28351e4e7d66e87e06151/lodash.png)

> Default install instructions, provided by lodash: Just `npm install` it!

The default can be an issue, though, when you're deploying JavaScript and Node.js applications that are critical - be it the platform that powers your business to the weekend project app that automates your home.

If you don't take proper precautions to set up fail-safes for the modules and code that you rely on, you're setting yourself up for a hard time when the next outage occurs. There are two relatively simple changes you can make - both reactively and proactively - that can ensure you don't get caught without the code you depend on.

## Independent Registries and Mirror Registries

Obviously, most people install from the default registry, `registry.npmjs.com`. This is only made clear by the sheer number of people expressing dismay whenever an outage occurs. Most people either don't see a need (until they are impacted in dramatic fashion) or don't know that you _can_ change your default registry.

I've put together a list of registries that are _currently_ up and running. I tested all of them and was successfully able to install `express@4.16.2` from each.

![](http://images.contentful.com/hspc7zpa5cvq/1Xtoh15kuwSiS8qi4OIWQo/1daa754ccb34b735bad9098b6f83fd3e/carbon.png)

> Setting my npm CLI's registry to the Yarn registry and installing `express@4.16.2`.

There are a few severely outdated articles on the Internet outlining some of the public-facing mirrors of the npm registry, but most seem to have shut down since the articles were published.

  * [Certified Modules Registry (NCM)](https://nodesource.com/products/certified-modules/technical-details): Certified Modules, or NCM, is a product specifically tailored to be highly reliable and fault tolerant - effectively, the registry for the Enterprise. Modules aren't ever removed or deleted, period. It has a built-in module quality score that, if the score falls below a certain point - usually due to non-OSS licenses or active security vulnerabilities anywhere in the dependency tree - will be automagically prevented from installing unless explicitly whitelisted.
  * [npmjs.cf](https://npmjs.cf/): This is an npm registry mirror that lives on the CloudFlare CDN, with 96 edge locations across six of the seven continents. This mirror is single-handedly maintained by [Terin Stock](https://twitter.com/terinjokes), and is a reliable free drop-in replacement for the default npm registry that's available for anyone to use.
  * [cnpm](https://cnpmjs.org/): CNPM is the most used public mirror of the npm registry in China, which is one of the [biggest markets](https://nodesource.com/node-by-numbers) outside of North America for Node.js. While it may not be the best choice in North America, there is definitely merit to using it if you're in the eastern hemisphere.
  * [Yarn Registry](https://registry.yarnpkg.com/): Although the Yarn registry is the default for Yarn (an alternative package manager from Facebook's OSS team), it's fully compatible with the npm CLI tool as an alternative registry. The Yarn team doesn't have an official description of the registry anywhere on their site, so the link is _directly_ to the URL you'd use as your registry replacement.

## Local Caching and Private Registries

In the event of a registry outage, the value of caching and private registries becomes evident. Until an outage, it's a little bit less obvious, but if you need to be able to access your modules and dependencies reliably, going down the path of setting up local caching and/or a private registry is worthwhile and highly suggested.

> The npm registry and all of it's components are doing great _right now_. No need to worry. Really.

One interesting thing to note is that setting up tooling for local caching and private registries are usually entirely independent of your registry choice - so, choosing an alternative registry from the list above doesn't impact your ability to begin using the features that local caching and private registries offer.

  * [JFrog Artifactory](https://jfrog.com/artifactory/): JFrog Artifactory is a full-blown registry that can hold basically any type of module or contained code. This includes everything from npm modules to Docker images. It's a pretty powerful tool and includes the ability to both cache the modules you depend on _and_ publish private modules for internal use (a.k.a. inner-source). This is probably one of the best options for a medium-to-large company looking for a true solution for a large group of developers.
  * [npmE](https://www.npmjs.com/enterprise): npmE is an on-prem version of the npm platform that enables private publishing and caching within your company. It also has a few integrations like GitHub, TravisCI, and Greenkeeper that enable developers to work in the places they're already familiar.
  * [Verdaccio](https://github.com/verdaccio/verdaccio) and [Sinopia 2](https://github.com/fl4re/sinopia): These two are userland private registries, with Verdaccio being a more up-to-date fork of Sinopia. They both can do effectively the same thing, but, at this point, Verdaccio seems like the more reliable choice. They both allow local caches of the modules you rely on for your production apps and local publishing of modules. These two are a good option if you're looking to spin up something for a smaller team and want to have the option to publish modules privately.
  * [local-npm](https://github.com/local-npm/local-npm): local-npm is another userland private registry that provides a pretty intense feature set that is effectively a local mirror that only saves the modules you're already using throughout your dependency trees - no need to replicate the entire npm registry. If you're looking to just have your modules _when you need them_, this is a really good option.
  * [Gemfury](https://gemfury.com/help/npm-registry/): GemFury is one of the very few hosted SaaS private registries. Their entire model seems to be centered around hosting modules of any kind, not just npm modules - similar to jFrog, but with seemingly less supported formats. That said, they do offer private publishing and can cache.
  * [Git repository](https://docs.npmjs.com/files/package.json#repository): If you've published a module to GitHub, GitLab, or any git repository and just want to rely on that for your Node.js app that's totally possible. It's **strongly** recommended you don't do this for modules and apps you'll be open-sourcing or making publicly available, but it _is_ a possibility.

## One Last Thing...

At NodeSource, addressing issues around Node.js, security, and stability of the platform is our number one goal. To explicitly help address the needs of businesses that are relying on Node.js and JavaScript, we've built both of our products- [Certified Modules](https://nodesource.com/products/certified-modules/technical-details), an added layer of assurance around the module ecosystem and [N|Solid](https://nodesource.com/products/certified-modules/technical-details), a drop-in replacement for the Node.js runtime-to help ensure you've got your apps covered no matter what.

Node.js application metrics sent directly to any statsd-compliant system. [Get N|Solid](https://dzone.com/go?i=222222&u=http%3A%2F%2Fpages.nodesource.com%2Fnsolid-free-trial-statsd-dz.html%3Futm_campaign%3DDZONE%26utm_source%3Dbumper%26utm_content%3Dbtext)
