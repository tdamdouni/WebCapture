# TypeScript code generation with YAKINDU Statechart Tools

_Captured: 2017-08-30 at 17:05 from [blogs.itemis.com](https://blogs.itemis.com/en/typescript-code-generation-with-yakindu-statechart-tools?utm_source=hs_email&utm_medium=email&utm_content=55794650&_hsenc=p2ANqtz--4a2Bl3JQFA95yHZhwpJSQTQGciq_qgo2vVgTKBSJuFAkL9Lap_AzglDy6_gXcbzCTp5vDXxAOkMx9x5tXCiTSDD9awA&_hsmi=55794432)_

To handle the complexity of modern web applications, model-driven development comes to your rescue. This blog post will show you how to model your web application's behavior with state machines and transform the latter into TypeScript code directly.

The generated code can easily be integrated with modern web development frameworks, like Angular or Ionic.

![yakindu-ts-angular-ionic.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Statechart%20Tools/yakindu-ts-angular-ionic.png?t=1504082489107&width=2172&height=1272&name=yakindu-ts-angular-ionic.png)

## Single-page web applications

TypeScript is a free and open-source programming language developed and maintained by Microsoft. It is a strict syntactical superset of JavaScript and adds optional typing to the language. TypeScript is designed for development of large web applications and compiles to JavaScript. As it is a superset of JavaScript, existing JavaScript programs are also valid TypeScript programs - that means you don't need to go through a big rewrite to migrate them. TypeScript brings a lot of features you already know from other higher-level programming languages like Java. Some examples:

  * Type annotations and compile-time type checking
  * Type inference 
  * Interfaces
  * Enumerated types
  * Mixins
  * Generics
  * NameSpaces
  * Classes
  * Modules
  * And much more

Some modern web frameworks like Angular 2+ or Ionic 2+ are based on TypeScript. These frameworks make use of the advantages of TypeScript when building scalable single-page web applications.

Since more logic is moved to the frontend, single-page web applications easily become complex. This is especially true for the interaction logic. This logic often ends op to be cluttered across the different parts of the application like event handlers, observables, etc.. In order to organize this better developers often end up in writing TypeScript classes that more or less implement state machines. At this point it is possible to go beyond typical implementation approaches and allow developers to model an application's behavior graphically as a state machine and to transform it directly into TypeScript code using tools like [YAKINDU Statechart Tools](https://www.itemis.com/en/yakindu/state-machine/).

## Web-based car infotainment app

In this example, we will have a look at an application with a simple HMI (Human Machine Interface) that represents an infotainment system for cars.

This application consists of two screens:

  * **welcome screen**: shows a welcome animation
  * **main Screen**: consists of severals components (speedometer, light widgets, infotainment…).

The infotainment component represents a container for further components like _infotainment menu_, _weather_, _music player_ and _phone_.

On the right-hand side of the image below you can see the menu with three items. If you click on an item, the corresponding feature will be displayed.

![human-machine-interface-car-infotainment.gif](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Statechart%20Tools/human-machine-interface-car-infotainment.gif?t=1504082489107&width=2172&name=human-machine-interface-car-infotainment.gif)

The demonstrated behavior is modelled with YAKINDU Statechart Tools as follows:

![hmi-yakindu-statechart-tools.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Statechart%20Tools/hmi-yakindu-statechart-tools.png?t=1504082489107&width=2172&height=1209&name=hmi-yakindu-statechart-tools.png)

![yakindu-statechart-tools-menu-service.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Statechart%20Tools/yakindu-statechart-tools-menu-service.png?t=1504082489107&width=936&height=909&name=yakindu-statechart-tools-menu-service.png)

In the definition section we define a _menuState_ variable of type string. The _menuState_ is used to decide which state is to be entered.

Then we define an _inevent onMenuChanged_ to respond to user interactions.

Finally, we define four _operation callbacks_ which display the corresponding feature.

## Generating TypeScript artifacts

To configure the code generation process, YAKINDU Statechart Tools uses a textual generator model called _SGen_. It describes what should be generated where, and with which options. The generator model can be created either by using the provided _YAKINDU Statechart Generator Model_ wizard or by creating a text file with the extension _.sgen_.

![yakindu-statechart-tools-generator-model.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Statechart%20Tools/yakindu-statechart-tools-generator-model.png?t=1504082489107&width=2172&name=yakindu-statechart-tools-generator-model.png)

Using the _Outlet_ feature, we specify that our target project is _ycar_app_.

The generated artifact should be placed into the _src/app/gen/statemachine_ directory within the _ycar_app_ project.

The generated state machine has some dependencies. They are generated into the library target folder _src/app/gen/stateutils_**.**

Using the _GeneratorFeatures_, we specify that our statechart should be created as an Angular service (useAngular = true) with an event-driven behavior (useEventQueue = true).

## Integrating the generated menu service state machine into Angular

In context of Angular, the generated _MenuService_ state machine was created as an Angular service. The state machine needs to be added as a provider to _YMainScreenModule_.

![yakindu-statechart-tools-main-screen-module.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Statechart%20Tools/yakindu-statechart-tools-main-screen-module.png?t=1504082489107&width=2172&name=yakindu-statechart-tools-main-screen-module.png)

Next we have to customize the _YMainScreenComponent_ to inject the service and write some glue code for setting the _in_ events and the operation callbacks. We do that in the component lifecycle hook _ngAfterViewInit:_

![yakindu-statechart-tools-main-screen-component.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Statechart%20Tools/yakindu-statechart-tools-main-screen-component.png?t=1504082489107&width=1920&name=yakindu-statechart-tools-main-screen-component.png)

From line 34 to 47 we define an operation callback object of type _IOperationCallback_. The members of this object are callback functions that are called from _menuService_.

In line 48 the _menuOperationCallback_ object is passed as an argument to the _setdefaultScopeOperationCallback_ function.

The _mainScreenService.menuChanged_ observable is subscribed. Depending on the value of _menuState_, _menuService.menuState_ will be set.

## Try it yourself!

The demonstrated example is available in full in the [example wizard of YAKINDU Statechart Tools](https://www.itemis.com/en/yakindu/state-machine/documentation/examples/). However, since the TypeScript generator is still in its beta testing phase, it does not come bundled with the YAKINDU Statechart Tools out of the box yet. Instead you have to install it manually. To do so, please go to _Help -> Install New Software_ and select _YAKINDU Typescript Generator_ from our update site, as shown in the screenshot below.

![yakindu-statechart-tools-typescript-generator.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Statechart%20Tools/yakindu-statechart-tools-typescript-generator.png?t=1504082489107&width=2163&height=930&name=yakindu-statechart-tools-typescript-generator.png)

Once you have installed the generator, you can import the project _Web-based YCar App_ from our example wizard, which you can invoke using _File -> New -> Example… -> YAKINDU Statechart Examples_.

Try it out and have some fun!

## Conclusion

Web applications are becoming increasingly complex. To make the complexity manageable, it pays out to implement parts of an application in a model-driven way.

In this blog post I have described how to configure the generation process for our modelled state machine. I have shown how simple it is to integrate a generated TypeScript artifact, here: the state machine, to an existing Angular application. The only thing we still have to do, is to customize the Angular module and their component that uses the generated Angular service.

What's coming next? Okay, it's really cool to generate TypeScript code from a state machine, but what would you say if you could use existing TypeScript artifacts directly in a statechart, similar to our [deep C integration](https://www.itemis.com/en/yakindu/state-machine/documentation/user-guide/#cdom_deep-c-integration) - one of the main features of YAKINDU Statechart Tools? Yes, we are already working on that, and the development is well advanced. Stay tuned for more information about this!

![yakindu-labs-logo.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Statechart%20Tools/yakindu-labs-logo.png?t=1504082489107&width=948&name=yakindu-labs-logo.png)

Researching, prototyping and putting our ideas into code, aside from the day-to-day business, is an [essential part of the itemis company culture](https://blogs.itemis.com/en/4-1-wins-a-somewhat-different-working-time-model). YAKINDU Labs is a collection of such projects which are currently in beta phase and therefore not yet released with any YAKINDU product bundles. As we love early feedback we regularly blog about what's going on behind the scenes. So try it, and get in touch with us!
