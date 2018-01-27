# Prototyping User Interfaces With Quality

_Captured: 2018-01-04 at 15:03 from [dzone.com](https://dzone.com/articles/prototyping-user-interfaces-with-quality?edition=347159&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=web%20dev%202018-01-04)_

[Get the senior executive's handbook](https://dzone.com/go?i=266423&u=https%3A%2F%2Fwww.appian.com%2Fresources%2Fresource%2Fguide-digital-transformation%2F%3Futm_source%3Ddzone%26utm_medium%3Dcontextual-ads%26utm_campaign%3Ddigital-transformation%26utm_content%3Dtransformers-almanac) of important trends, tips, and strategies to compete and win in the digital economy.

## Introduction

A good user interface prototype is a powerful tool. It can be used to visualize/envision a concept/idea/design, discover design, experiment with different designs, test usability with real users, and lay the conceptual foundation for a product. It can also be used to engage and align stakeholders and achieve sponsorship and support for a project, e.g. funding.

Prototyping, of course, raises questions. What should be prototyped and how? If prototypes are considered throw-away, does quality matter? If so, what kind of quality should we aim for and how might we achieve it? And can prototyping be combined with agile approaches to software development, such as continuously delivering valuable software, emphasizing working software (through practices such as test-driven development) and simplicity (maximizing the amount of work not done)?

This article outlines a process for coding user interface prototypes, which I have found workable and valuable. Starting from understanding the purpose of the prototyping exercise, I build shallow components with default properties running inside a library view. As I code, I iterate on the components, verifying them by looking or listening, and building up a suite of repeatable property settings in the library (I write [other kinds of tests as needed](http://conwy.tech/tests)). I then connect these components together into a navigable, interactive user interface, using routing and/or "glue code" inside containers.

I believe this process can be used to quickly build robust, flexible, working prototypes. These prototypes are valuable because they satisfy a specific purpose. But they also exhibit quality in how they satisfy that purpose: they are readily testable (both via quick and easy manual verification and via automated tests where appropriate) and are modular and decoupled from data sources (allowing them to be either thrown away or integrated into a final, fully functional product).

## Prototyping With a Purpose

One of the first questions I ask on any prototyping assignment is: why are we building this? I find it important to understand the reasons why an organization wants to build something. How do they wish to benefit from it? What need do they wish to satisfy?

Asking questions about the purpose of building a prototype can help to reveal the requirements the prototype will need to satisfy and, thus, what should be prototyped and how it should be prototyped.

Given an understanding of the purpose, there are multiple ways a prototype may be used. I have seen at least four uses of prototypes in real-life projects:

  * **Learning from users.** Observing users interact with a prototype can be a good way for an organization to learn about their users (and themselves). The practice of usability testing encompasses a range of methods for conducting such observations, so as to better understand users and user needs. Data and observations can be collected and synthesized into insights, which can be used to improve the design of an interface. These insights can also contribute themselves to broader areas of design, such as what is known as service design.

  * **Visualizing the solution.** Use of visual imagery to lead groups and individuals is a time-honored technique. A visual image that can be presented to a group of people and manipulated in an iterative cycle can foster open communication and collaboration, help to move the group in a definite direction and achieve agreement and buy-in. It can help to align stakeholders and achieve project sponsorship. A user interface prototype can be a powerful tool for visualizing how a product will look and feel, and where it will fit into people's lives and into a broader design.

  * **Testing for usability and accessibility.** An interface design might look good on paper (or in a wire-framing tool), but may not "survive contact with" a real-life user. Does the interface render properly on common screen sizes? Are the controls easy to operate and manipulate? Are colors of sufficient contrast to be viewable by people with various forms of sight? Can the interface be used with assistive technology, such as screen-readers, braille readers, and various forms of input? These questions may be better answered by building the interface, testing it with real users, and implementing fixes or improvements where necessary. Rigorously testing for usability from the start is often a better project management strategy than waiting until later, when key decisions that affect usability (such as technology or framework choices) may have already been made.

  * **Discovering and comparing technologies.** We need to choose between competing technologies, tools, frameworks, etc. with which to build a future product. For example, two competing web frameworks. Thus, we need to learn more about each alternative, to understand the pros and cons of each. A good way to learn might be to construct a prototype using two or more of the alternatives under consideration. The prototype could be built around a single feature or slice of functionality that the end product will likely offer. Or it could be built around a slice of functionality that each alternative offers so that we learn how that functionality is implemented by each alternative.

## Does Quality Matter if the Code Is "Throw-Away"?

Prototypes are often considered "throw-away." That is, they are built for a specific purpose (e.g. to test a hypothesis, to discover or demonstrate one particular part of a design, etc.). Once a prototype has satisfied its purpose, we throw it away and build a new prototype, to satisfy a new purpose. Dyson remarked that he [built 5,126 prototypes](https://youtu.be/PzCU7fiTXEw?t=17m33s), going through [several prototypes a day, for 4-5 years](https://youtu.be/PzCU7fiTXEw?t=13m32s). He may have had a strong core concept, but he still had to prototype it in many forms, before reaching a final, finished product.

Does this mean that quality doesn't matter when prototyping software? Are developers who build prototypes "off the hook" when it comes to applying quality practices and processes to achieve their outputs? I would argue no, for two main reasons.

First and foremost, each prototype has a purpose to accomplish, and thus, a function to perform. If it didn't have a purpose, why would we waste time building it? Thus, a prototype should be thought of, and built, as, "working software" just as much as any other kind of software, whether a flight simulator or a medical device controller. It simply needs to work well enough to perform the function it is being built to perform, and no more.

For example, a prototype of an online payments system might not perform all the functions of a real payments system. It might not verify a user's credentials, log payments in a central database, or send payments to an automated clearing house. But if the prototype will be shown to stakeholders, to engage them and build their confidence in a concept, it needs to be robust enough to not break during a demo. If it is being built to test a hypothesis, say a user interaction when making a payment, such as filling in an 'Amount' field, it needs to be robust enough to support repeated testing of that interaction.

Secondly, there is a good chance that any code, even code built expressly with a view to being "thrown away," may find its way into a real product. This has, in fact, occurred many times in the history of software. [Thomas Knoll is quoted](https://blokboek.net/en/thomas-knoll-i-never-imagined-that-my-digital-darkroom-would-turn-into-a-product-such-as-photoshop/) as saying: "I never imagined that my digital darkroom would turn into a product such as Photoshop." Yet even the earliest versions of the source code, which have now been released to the public domain, are constructed with a level of quality that inspired [Grady Booch to remark](https://www.pcworld.com/article/2028315/computer-history-museum-shares-original-photoshop-code.html): "this code is so literate, so easy to read, that comments might even have gotten in the way."

Prototype code built in a clean, organized, modular, testable manner can be integrated into a production product. This integration can be done efficiently and the code can be verified to function as expected.

In summary, I would argue that "throw-away" and "quality" should not be seen as competing priorities. Rather, quality needs to take into account what is being built, why, and how it will likely be used in the future. If we properly understand the purpose and value of prototype code, such as its potential to be re-used in production software, then we can determine what kind of quality is appropriate and how we will measure it. A payment screen for demoing might not need to scale to millions of users, but it had better render correctly on-screen when needed, and it had better be ready to be plugged into a real payments back-end if that's a realistic possibility.

## Deciding What to Build

One distinction I have found crucial is between what _might_ be built in a full product vs. what _needs_ to be built for this particular prototype.

Let's say we are prototyping a form that a user will fill out, to register their address. Our purpose is to learn more about how users might want to interact with the form. Specifically, we want to compare a free-range non-validated input with an input that automatically pops up suggestions as the user types.

The first scenario could be prototyped as a simple text-box on a webpage:
    
    
            <label for="address">Address</label> 
    
    
            <input type="text" id="address" />

The second scenario might appear to require a sophisticated auto-suggest input that looks up addresses as the user types them (using an API such as Google Location) and displays them in a pop-up.

But do we really need to go that far, if we just want to test our hypothesis? Why not, instead, give the user a "dummy address" on a piece of paper, for them to enter in, and code a simple suggestion box, which only works with that one dummy address?

Thus, we could implement our prototype with the following code:
    
    
          <label for="address">Address</label> 
    
    
          <input type="text" id="address" />
    
    
          document.forms[0][0].addEventListener('keydown', function (e) {
    
    
            var shouldShow = (e.target.value.toLowerCase().indexOf('1 tes') === 0);
    
    
            dummySuggestionEl.style.display = shouldShow ? 'block' : 'none';

![Screencast of a prototype of an auto-suggest input in plain HTML/Javascript](https://i.imgur.com/GSAIzYv.gif)

By being aware of the purpose of the prototype we're building, and then only building what is needed to satisfy that purpose, we can build what is needed in less time, with better focus and with higher quality.

## Test-First: Library Entry - Component Code - View in Library

Can we apply the test-first or test-driven development (TDD) approach to building prototypes?

I believe we can. We do this by setting up a library to host components (passing in props as needed) and then following an iterative view-code-view cycle, switching between the library and the code.

The cycle looks something like this:

  1. Create a library entry for the non-existing component. Open the library and watch it fail, as the component doesn't yet exist.
  2. Fix the library by actually creating the component, as an empty shell.
  3. Switch back to the library, refresh, observe the empty shell.
  4. Modify the library entry, adding/modifying inputs to the component as needed. Refresh the library and watch the component fail to render as we would expect.
  5. Switch back to the component, add some code to achieve the desired effect.
  6. Repeat step 3.

Observe that, in each iteration, we formulate an expectation (how we expect the component to render), then we write some code to satisfy that expectation, then we verify whether or not it actually satisfies that expectation by viewing it again in the library.

Over the course of multiple iterations, we build up a suite of expectations of components, encoded as library entries, which invoke the component (providing inputs as needed).

![Flowchart of a test-first prototyping workflow](https://i.imgur.com/XlXR6qS.png)

Note 1: The 'library' is simply an environment where we can execute and interact with a running instance of components, quickly and easily refresh them as needed, and thus cycle between code and running instances. This might be a simple HTML web page that renders each web component, one after the other. Or we may use a library-specific or framework-specific tool, such as [Storybook](https://storybook.js.org/) or [Playground](http://www.angularplayground.it/), or a development environment that provides a preview mode, such as Salesforce's [Lightning Experience](https://developer.salesforce.com/lightning).

Note 2: Similar "iterative design" techniques have a history of use in web development, with the emergence of browser plugins, editors, IDEs, build tools, etc., which support auto-refreshing in the browser. They have also been used in graphic design and [generative art](http://generative-gestaltung.de/) communities, with languages/IDEs such as [Processing](http://processing.org/) and [CodePen](https://codepen.io/), which integrate an execution environment with code editing.

Here is an example of a library entry, written with the Storybook framework:
    
    
                <AddressAutosuggest searchText="sugg" suggestions={['suggestion 1', 'suggestion 2']}/>)

Over time, following this process, we build up a suite of "tests" in our container, by listing out each component, passing in the state as properties where needed, and doing all of this in a way that's readily accessible and repeatable (i.e. just refresh the container).

Visual verification can be simply a matter of looking at the rendered result and verifying that it matches our expectations (we may be aided by device emulators, low-vision simulators, etc. to test under various conditions).

Auditory verification may mean switching on a screen-reader and listening to the output, ensuring that it is [perceivable, operable, understandable, and robust](https://www.w3.org/TR/WCAG20/).

## Building Piece-by-Piece: Shallow Components

Many popular user interface frameworks, libraries, and toolkits support building what's known as "shallow components."

A "shallow component" refers to a component which only deals with one piece or one aspect of the user interface ("component"), and which encapsulates little or no internal state or behavior ("shallow").

Its state and behavior are entirely determined by the properties passed into it. It simply maps these properties to elements that can be rendered. In a web application, it would be a set of HTML elements and perhaps some styling and handlers attached to those elements.

(Note: This bears some similarity to the "passive view" pattern, expounded upon by Martin Fowler, and the View layer in MVC, expounded upon in the book _Patterns of Enterprise Application Architecture_. Essentially, the view is just transforming the model it's given, i.e. its properties, into a user interface.)

By breaking a user interface up into components, we can focus on one piece at a time, build only what is needed and test each piece in isolation (see the following section). We can also benefit from re-use: if something appears more than once in an interface, we can simply re-use the component we already built.

Here's an example of an address auto-suggest, to satisfy the library entry given in the previous section, written as a React component:
    
    
              <label htmlFor="address">Address</label>
    
    
              <input type="text" id="address" onChange={e => onEnterAddressText(e.target.value)} />

Note: Components need not be only visual elements. Interfaces need to render non-visually as well, such as the spoken word via a screen-reader. And interfaces need to support interactions and animations. Most user interface frameworks allow these non-visual and non-tangible aspects to be componentized and re-used as well. For example, on one project, I created a 'Wizard' component, whose role was simply to render a set of 'Step' components sequentially, along with a 'Next' button that shows the subsequent step and a 'Back' button to show the prior step. This component isolated a specific set of behavior (moving back and forward one step at a time) and controls along with that behavior (next and back buttons).

## Adding "Dummy Data" Through Properties

Because our shallow user interface components can be controlled by passing in properties, it is easy to pre-configure them with dummy data.

So, for example, we can make our auto-suggest input from above render as a self-sufficient component, by providing `defaultProps`, like so:

Now we can easily define this component anywhere in our prototype:

This makes it easy and convenient to re-use our component, either within the same prototype, a different prototype, or an end product.

## Putting the Pieces Together: Containers, Routing, and "Glue Code"

At some point, we'll need to connect our shallow components together, to make the prototype navigable and interactive.

There are a few different options here. The three main techniques I currently use are:

  * Routing frameworks (e.g. React Router or Angular Router)
  * Container components
  * "Glue code"

A routing framework, such as React Router, allows you to declaratively define the navigation structure of your prototype, using routes and links to routes. For example, a website with pages accessed via a main menu at the top of the page could be prototyped using a router, defining each of the top links as a route.

Container components are another pattern. We define a higher-level component whose responsibility is to manage the interactions between shallow components and/or the context of the components. An example might be a component which supplies the dummy address and dummy suggestion to our `addressAutosuggest` component.

Below is an example of a container component, built in React, that composes an `addressAutosuggest` with a dummy suggestion:
    
    
            if (newValue.toLowerCase().indexOf('test 1') === 0) {
    
    
                  suggestions={this.state.suggestions} />

Finally, "glue code" can be used to compose shallow components together, either dynamically or flexibly. An example might be a wizard component, which takes any number of child components of any kind, and dynamically strings them together into a wizard, with next and back buttons for sequentially navigating between each "step."

An example of the [react-router-wizard](https://github.com/jonathanconway/react-router-wizard) component being used to compose multiple sub-components:

## Summary

The prototyping of user interfaces can be made fast and efficient and produce a quality output. This can be done by understanding the purpose of a prototype, deciding what to prototype and, perhaps more importantly, what _not_ to prototype, then following a test-driven, iterative approach, building the prototype out of re-usable "shallow" components, connected together with containers, routing and/or glue code.

## Other Readings

Some other articles you may find interesting and relevant to this topic:

## Credits

Special thanks to [Elise Chant](http://twitter.com/elisechant) for introducing me to Storybook.

[Read this guide](https://dzone.com/go?i=266422&u=https%3A%2F%2Fwww.appian.com%2Fresources%2Fresource%2Fguide-robotic-process-automation-rpa%2F%3Futm_source%3Ddzone%26utm_medium%3Dcontextual-ads%26utm_campaign%3Drpa%26utm_content%3Dlookbook-guide-rpa) to learn everything you need to know about RPA, and how it can help you manage and automate your processes.
