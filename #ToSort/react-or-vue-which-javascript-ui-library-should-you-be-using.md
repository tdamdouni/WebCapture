# React or Vue: Which JavaScript UI Library Should You Be Using?

_Captured: 2017-06-18 at 21:36 from [dzone.com](https://dzone.com/articles/react-or-vue-which-javascript-ui-library-should-yo?edition=305103&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-17)_

[Try RAD Studio for FREE!](https://dzone.com/go?i=219227&u=https%3A%2F%2Fwww.embarcadero.com%2Fproducts%2Frad-studio%3Futm_source%3DDzone%26utm_medium%3DOnlineDisplay%26utm_campaign%3DRadStudioDzone%26utm_content%3DPostRollText) It's the fastest way to develop cross-platform Native Apps with flexible Cloud services and broad IoT connectivity. [Start Your Trial Today!](https://dzone.com/go?i=219227&u=https%3A%2F%2Fwww.embarcadero.com%2Fproducts%2Frad-studio%3Futm_source%3DDzone%26utm_medium%3DOnlineDisplay%26utm_campaign%3DRadStudioDzone%26utm_content%3DPostRollText)

In 2016 React cemented its position as king of the JavaScript web frameworks. This year saw the rapid growth of both its web and native mobile libraries, and a comfortable lead over its main rival Angular.

But 2016 was an equally impressive year for Vue. The release of its version 2 made a huge impression on the JavaScript community, attested to by the 25,000 extra Github stars it gained that year.

The scope of both React and Vue is undeniably similar: both are lightweight component-based libraries for building user interfaces that focus on the view layer only. Both can be used in a simple project, or be scaled up to a sophisticated app using cutting edge tooling.

As a result, a lot of web developers are wondering which one they should be using. Is one clearly superior over the other? Do they have specific pros and cons to be aware of? Or are they basically the same?

> _Note: this article was originally posted [here on Medium](https://medium.com/js-dojo/react-or-vue-which-javascript-ui-library-should-you-be-using-543a383608d?jsdojo_id=dz_rov) on 2016/12/22_

## Two Frameworks, Two Advocates

In this article, I want to answer those questions with a thorough and fair comparison. The only problem is: I'm an unashamed Vue fanboy and totally biased. I've used Vue heavily in my projects and even released an online course, the Ultimate Vue.js Developers course.

To even out my biased position I've brought in my friend Alexis Mangin who is both a great JavaScript developer and a big React fan. He's similarly immersed in React, using it frequently in both web and mobile projects.

Alexis asked me one day: "why are you so into Vue, and not React?" Since I didn't know React that well, I couldn't give a good answer. So I put the idea to him that we sit down one day with our laptops and show each other what our chosen library had to offer.

![1-0_PABYfDH4JN8GDzg2rgvA.jpeg](https://cdn.filestackcontent.com/UTjqfbJRJiVuzT4ZMOXt)

> _Anthony (left) and Alexis (right) comparing React and Vue at Bull and Bear Cafe in Chiang Mai, Thailand_

After a lot of discussion and learning from both sides, the following six points are our key findings.

## If You Like Building Apps With Templates (or Want the Option To), Go With Vue

Putting your markup in an HTML file is the default option for a Vue app. Similar to Angular, mustache braces are used for data-binding expressions, while directives (special HTML attributes) are used for adding functionality to the template. The following demonstrates a simple Vue app. It prints a message and has a button that dynamically reverses the message:
    
    
          this.message = this.message.split('').reverse().join('');

In contrast, React apps shun templates and require the developer to create their DOM in JavaScript, typically aided with JSX. Below is the same simple app implemented with React:
    
    
          message: this.state.message.split('').reverse().join('') 
    
    
            <p>{this.state.message}</p>
    
    
            <button onClick={() => this.reverseMessage()}>

Templates are easier to understand for newer developers who've come from the standard web development paradigm. But even some experienced developers prefer them, as templates can better separate layout from functionality and give the option of using pre-processors like Pug.

But templates come at the cost of having to learn all the extended HTML syntax, while render functions only require knowledge of standard HTML and JavaScript. Render functions also benefit from easier debugging and testing.

On this point, though, you can't go wrong with Vue, as it's introduced the option of using either templates or render functions in version 2.

## If You Like Simplicity and Things That "Just Work", Go With Vue

A simple Vue project can be run directly from a browser with no need of transpilation. This allows Vue to be easily dropped into a project the way jQuery is.

While this is also technically possible with React, typical React code leans more heavily on JSX and on ES6 features like classes and non-mutating array methods. But Vue's simplicity runs more deeply in its design. Let's compare how the two libraries handle application data (i.e. "state").

State in React is immutable so you can't directly change it. You need to use the `setState` API method:

Diff'ing the current and previous state is how React knows when and what to re-render in the DOM, hence the need for immutable state.

In contrast, data is just mutated in Vue. The same data property can be altered far less verbosely in Vue:
    
    
    this.message = this.message.split('').reverse().join('');

Before you conclude that Vue's rendering system must lack the efficiency of React's, let's examine how state in Vue is managed under the hood: when you add a new object to the state, Vue will walk through all of its properties and convert them to getter and setters. Vue's reactivity system now keeps track of the state and will automatically re-render the DOM when it is mutated.

Impressively, altering state in Vue is not only more succinct, but its re-rendering system is actually faster and more efficient than React's.

Vue's reactivity system does have caveats, though. For example, it cannot detect property addition or deletion and certain array changes. These cases can be worked around with a React-like `set` method from the Vue API.

## If You Need Your Application to Be as Small and Fast as Possible, Go With Vue

Both React and Vue will build a virtual DOM and synchronize the real DOM when the app's state changes. Both have their own means of optimizing this process. Vue core developers have offered a benchmark test that shows Vue's rendering system to be faster than React's. In this test, a list of 10,000 items is rendered 100 times. The comparison is tabled below.

![1-xy2KzzZrqP0mdLUbIdC-xA.png](https://cdn.filestackcontent.com/INno9MqSreYatysmrCy6)

> _Benchmarks as published on vuejs.org_

From a pragmatic standpoint, this kind of benchmark is only relevant in edge cases. Most apps will not need to do this kind of operation routinely so it should generally not be considered an important point of comparison.

Page size, though, is relevant to all projects, and again Vue has the upper hand. Minified, the current release of the Vue library is only 25.6KB.

To get a similar set of functionality in React you need React DOM (37.4KB) and the React with Addons library (11.4KB), which totals 48.8KB, almost double the size of Vue. To be fair, you will get a larger API with React, but you don't get twice as much functionality.

## If You Plan to Build a Large Scale App, Go With React

A comparison of a simple app implemented in both Vue and React, like the one at the beginning of this article, may initially bias a developer to favor Vue. This is because template-based apps are easier to understand at first look, and quicker to get up and running with.

But these initial benefits introduce technical debt that can slow development of apps reaching a larger scale. Templates are prone to unnoticed runtime errors, are hard to test, and are not easy to restructure or decompose.

In contrast, JavaScript-made templates can be organized into components with nicely decomposed and DRY code that is more reusable and testable.

Vue also has a component system and render functions. But React's rendering system is more configurable and has features like shallow rendering that, combined with React's testing utilities, allow for far more testable and maintainable code.

Meanwhile, React's immutable application data may not be as succinct, but it shines in a larger application when transparency and testability become critical.

## If You Want a Library That Is Adaptable for Both Web and Native Apps, Go With React

React Native is a library for building native mobile applications with JavaScript. It's the same as React.js, only instead of using web components, it uses native components. If you've learned React.js, you'll very easily be able to pick up React Native, and vice versa.

The significance is that a developer can build an app on either the web or native mobile without requiring a different set of knowledge and tools. Learning React gives you a huge bang for you buck if you intend to develop for both web and mobile.

Alibaba's Weex is another cross-platform UI project. Currently, it considers Vue an "inspiration" and uses a lot of the same syntax, with plans to fully integrate Vue. However, the timeline and specifics of this integration are still unclear.

Since Vue has HTML templates as a core part of its design and does not have custom rendering as a current feature, it's hard to see that a native counterpart for Vue.js in its current form will be as tight as what React.js and React Native are.

## If You Want the Biggest Ecosystem, Go With React

There's no question that React is currently the more popular library with ~2.5M NPM downloads a month as opposed to Vue's ~225K per month.

![1-YTD_ZbHE77GWKzYJVGh_Fw.png](https://cdn.filestackcontent.com/goFRY5xhTPy2NOkk7vm5)

Popularity is not merely a shallow benefit. It means there are more articles, tutorials, and Stack Overflow answers for help. It means there are more tools and add-ons to leverage in a project and save developers from building everything themselves.

Both libraries are open source, but React was born from Facebook and benefits from that patronage. Developers and companies committing to React can be assured of continued maintenance.

In contrast, Vue was created by a single developer, Evan You, and You is currently the only full-time maintainer of Vue. Vue has some corporate sponsorship but not on the scale of Facebook or Google.

To the credit of the Vue team, its small size and independence have not materialized as a disadvantage. Vue has a regular release cycle and even more impressively, Vue has only 54 open issues on Github compared to 3456 closed issues, while React has a far larger 530 open issues compared to 3447 closed.

## If You're Already Happy With One or the Other, There's No Need to Switch

To recap, our findings, Vue's strengths are:

  * Flexible options for template or render functions.
  * Simplicity in syntax and project setup.
  * Faster rendering and smaller size.

React's strengths:

  * Better at scale, sturdier, and more testable.
  * Web and native apps.
  * A bigger ecosystem with more support and tools available.

However, both React and Vue are exceptional UI libraries and have more similarities than differences. Most of their best features are shared:

  * Fast rendering with virtual DOM.
  * Lightweight.
  * Reactive components.
  * Server-side rendering.
  * Easy integration with router, bundler, and state management.
  * Great support and community.

If you think we've missed something we'd love to hear in the comments. Happy developing!

I'm a JavaScript developer and online course instructor. I run a blog, Vue.js Developers, and am the author of the Ultimate Vue.js Developers course.

Alexis helped me write this article with his exceptional knowledge of web development. You should follow him on [Medium](https://medium.com/@alexmngn) as he writes his own great tutorials on React.

> _Get the latest Vue.js articles, tutorials and cool projects in your inbox with the [Vue.js Developers Newsletter](http://vuejsdevelopers.com/newsletter/?jsdojo_id=dz_rov)_

Get Your Apps to Customers 5X Faster with [RAD Studio](https://dzone.com/go?i=219226&u=https%3A%2F%2Fwww.embarcadero.com%2Fproducts%2Frad-studio%3Futm_source%3DDzone%26utm_medium%3DOnlineDisplay%26utm_campaign%3DRadStudioDzone%26utm_content%3DPreRollText). Brought to you in partnership with [Embarcadero](https://dzone.com/go?i=219226&u=https%3A%2F%2Fwww.embarcadero.com%2Fproducts%2Frad-studio%3Futm_source%3DDzone%26utm_medium%3DOnlineDisplay%26utm_campaign%3DRadStudioDzone%26utm_content%3DPreRollText).
