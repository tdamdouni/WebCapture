# Introducing Bit: Writing Code in the Age of Code Components

_Captured: 2017-04-30 at 11:53 from [blog.bitsrc.io](https://blog.bitsrc.io/introducing-bit-writing-code-in-the-age-of-code-components-fd8512a9aa90?source=userActivityShare-c79006fee040-1493545984)_

![](https://cdn-images-1.medium.com/freeze/max/30/1*UyTPSBv7x3_yzRh4jM_dsA.jpeg?q=20)![](https://cdn-images-1.medium.com/max/800/1*UyTPSBv7x3_yzRh4jM_dsA.jpeg)

I believe code should be written once and then evolve over time. Atomic pieces of code should be composed with other atomic components as lego bricks to form any kind of functionality.

Making code reusable means keeping it well encapsulated, polymorphic and composable. Yet, as software development is being scaled, creating, finding and reusing these atomic components is getting harder. Small pieces of code are being rewritten or duplicated every day instead of being reused.

To validate this, we analyzed GitHub's top JavaScript repositories to see how many times a single functionality such as "isString" had been re-implemented. We found that this functionality had ~100 different implementations which were duplicated over 1,000 times in only 10,000 repositories. I plan to write a separate post dedicated to this research.

We also found that even for great organizations, the problem is getting worse with over 30% of their codebase duplicated or reinvented.

The question is, why is it so hard to make a few lines of code reusable and accessible to everyone. What makes us prefer the alternative of copying and pasting or reimplementing code instead of using methods for reusability.

### Code components as "lego bricks" in real life

The age of code components has already begun. Great web frameworks such as React, Angular or Vue are making component isolation, encapsulation and composability easier then ever before. Components are the building blocks for anyone working with these frameworks.

The Node community is also headed in this direction. Authors such as Addy Osmani [described](https://addyosmani.com/first/) great outlines for component reusability. Others such as [Sindre Sorhus](https://www.npmjs.com/~sindresorhus) are willing to invest great time and effort designing and publishing over a thousand micro-packages. Frameworks such as Express and others are making some of our code reusable by design.

> "Looking into the future, I don't think micro packages are the best way to use code components as "lego bricks" to compose software applications. I believe modularity should breed creation and not add more complexity than productivity."

In my experience, I find it very hard to maintain a large collection of small components using packages and artifacts. Looking into the future, I don't think micro packages are the best way to use code components as "lego bricks" to compose software applications. I believe modularity should breed creation and not add more complexity than productivity. Micro-packages fail to achieve this for three reasons:

  * **Publish overhead**: to create a new package for every small component you would have to create a VCS repository, create the package boilerplate (build, testing and so on) and somehow make this process practical for a large set of components.
  * **Maintenance**: modifying a package takes time and forces you to go through multiple steps such as cloning, linking, debugging, committing, republishing and so on. Build and install times quickly increase and dependency hell always feels near.
  * **Discoverability**: People often use different terms to describe the same functionality. It's hard if not impossible to organize and search multiple repositories and packages to find the components you need, and there is no single source of truth to search and trust. We also have no solid measures and criteria to determine the quality of a micro-package (edge cases, testing, etc.) prior to using it.

Facing these problems, some people try to use static utility or para-utility libraries to group together bunches of components. In my view, this isn't much of a solution either. Using such utility libraries reminds me of using a CD-ROM instead of cloud-based storage: these libraries are static, cumbersome to handle and contain lots of stuff we don't need.

### Making code reuse as easy as copy pasting

> "Bit adds a "virtual layer" that makes the reuse of atomic components as easy as copying and pasting, while preserving the same kind of predictability."

To allow the use of code components as "lego bricks" in real life we created Bit: [an open source virtual repository for code components](https://github.com/teambit/bit). Bit adds a virtual layer that makes the reuse of atomic components as easy as copying and pasting, while preserving the same sort of predictability.

The purpose of Bit is to enable developers to easily create, maintain and reuse components from any context (any software project you're working on) without paying the price of using a package.

Bit solves the problems described above by applying a few concepts:

#### Scopes

A Bit Scope is a distributed and virtual container of components on top of a source-code repository (and outside of it). It allows us to keep and maintain components in a single place, while still being able to independently find, use and modify individual components.

When depending on a component, Bit caches it on the closest Scope. This makes our software independent, fast and predictable. Component updates are designed to be event-driven. This makes sure components will never mutate, unless you explicitly stated differently or applied a trusted method for automatic updates (such as test-based updates, moderation and more).

#### Component environment

To make components quick and easy to publish from any context, Bit provides a configurable, isolated and reusable component environment. This allows us to create new components without duplicating or recreating a boilerplate (build, test, docs, etc.),

Defining build and test environments can be easily done using configurations and conventions. These environments are defined by other reusable Bit components implementing predefined environment interfaces. This allows Bit to build and test the component for maintenance, analysis and/or integration purposes.

#### Virtual API

Instead of installing components the same way package managers do, Bit generates a virtual "package" or module with a chosen set of components.

Using this approach has many benefits. For example, it makes it easy to modify components by enabling to build components in runtime during development. It also allows to add custom layers of syntactic sugar and provides better control over your components.

In the future, this architecture will enable us to support further languages by being less subjected to language-specific constraints.

#### Component discoverability

Bit indexes each component by functionality and makes them all accessible using an integrated search engine. This search uses expressive linguistic models to make your components more discoverable, even when you forgot their exact names.

Source-code sensitivity enables Bit to parse and use different elements of your source code as documentation and quality measurements. This means Bit provides you with the information and confidence to choose the right components.

For now, Bit enables us to use the [component unit testing](https://bitsrc.io/bit/promise/global/promisify) as part of the component documentation. It helps to determine and monitor the different use cases a component handles and its current state.

#### Distribution

Whatsapp groups enable us to share content and communicate like we could never do on Facebook or Twitter. Bit's distributed nature applies the same to code.

Bit Scopes are easy and "cheap" to create and can be inter-connected to one another to form a network. Scopes can be encapsulated by teams, ideas and more. This allows us to share components in small groups and only expose chosen components to the rest of the network.

Distribution is also important for flexibility and freedom, making sure software development stays free, open and decoupled from commercial interests.

#### Centralized hub

Bit is distributed by nature. However, every distribution can highly benefit from centralization, as long as it's not compromising flexibility and freedom. To allow ourselves and others to easily find, curate and collaborate on components and Scopes, we built a centralized community hub called [bitsrc.io](https://www.bitsrc.io/?utm_source=Medium&utm_medium=Medium&utm_campaign=Medium001).

> ״In the future, people should be able to find code components shared across the web or by colleagues and compose them in their codebase to build anything.״

Anyone can connect and host virtual component repositories (Scopes) on the Bit community hub without having to setup a remote Scope manually. it also allows people to easily share and find components and Scopes created by the community and others around the world.

Our hub will be free for open source for now and forever.

### Future thoughts

By putting component source-code first and being sensitive to it, some exciting future features are made possible. These features include automatic dependency definition, source code indexing, component quality measurement, semi-automatic semantic versioning and many more. One step at a time, these features will allow us to turn code components into the building blocks we want them to be in real life.

Bit is also language agnostic by design. Future roadmap includes adding more drivers to support more languages and allow the composition of components written in different languages together.

Feel free to try Bit and bitsrc.io out for yourselves.
