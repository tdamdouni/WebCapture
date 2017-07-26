# Migrating from Desktop to Cloud-Native Web Applications

_Captured: 2017-04-26 at 00:05 from [community.oracle.com](https://community.oracle.com/docs/DOC-1001176?utm_content=buffer0034e&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

** Leverage modern web technologies for the migration and creation of rich desktop applications that can run in the cloud.**

A highly integrated application provides a one-stop shopping experience for users. At the same time, developers can build new features leveraging the surrounding application infrastructure and benefit from the resulting productivity. When migrating to the cloud, a question arises: how can you provide a smooth migration path from a desktop application to a web application that has a similar user experience as the desktop application?

JavaFX, which is provided by the Java runtime, can be used as the foundation for hybrid desktop applications. These applications can be built with the latest web and desktop frameworks united. This article explores an architecture that combines the best of both worlds--web and desktop--as a migration path and an option for building next-generation desktop applications.

## The Desktop Experience

Rich desktop applications provide a single point of entry for all the use cases. Many users are accustomed to the statefulness of desktop applications, which offers context information for the task at hand and allows them to switch between different tasks easily. To offer a responsive experience, remote calls to back-end systems can be avoided, because these applications cache most data. This in turn enables high productivity for users.

As an example, a sales agent might use an application in the following way: While working on a case, a customer calls to inquire about a different case. Of course, the agent suspends her current activity in order to access the customer's data. After providing all necessary information on a specific case, the customer suddenly might want to update his address information. Only if the application provides easy navigation to these related tasks does it support the agent to help the customer quickly, thus providing a good experience.

When multiple applications need to be used for different use cases, more friction is introduced. Waiting on the phone for an agent is generally not regarded as a good experience, and neither is being switched between different departments.

Figure 1 shows a typical desktop application designed as an integrated tool that has flexible entry points for the use cases and entry points for activities related to the current task.

![f1.png](https://community.oracle.com/servlet/JiveServlet/downloadImage/102-1001176-6-185528/1538-900/f1.png)

> _Figure 1. Typical desktop application_

As shown on the left, multiple entry points for the use cases are provided. These reflect different kinds of triggers that lead to customer interaction. On the right, below the form area, are entry points for related activities to the task at hand.

This kind of application provides less-obvious benefits as well:

  * An agent does not need to sign in multiple times.
  * Because a single application is used, the user experience is consistent across all use cases.
  * Additional context information can be provided even for just remotely related use cases, for example, a running order for payment can be shown as a warning when a new order is created.

## The Modern Web

Standard request-oriented web applications do not offer the same rich experience as desktop applications do. Instead, they offer something else: true device independence, because they are capable of running on almost all devices that have a web browser. It is easy to see that this means nearly every connected device today.

Since the introduction of Ajax and DHTML, web applications have become more like their desktop counterparts: They respond quickly because the server provides only fragments instead of a full page that needs to be transmitted and rendered on the client. Because different back-end systems can be used in the same client application, they offer more options for integration.

Nowadays web components and frameworks such as AngularJS and Oracle JavaScript Extension Toolkit (Oracle JET) provide rich options for developing web applications while using back-end applications only for retrieving data. Presentation is handled completely by the client.

This concept aligns well with the design of desktop applications created with Swing or JavaFX when using the Common Object Request Broker Architecture (CORBA) or other remote facilities for back-end access.

When targeting cloud platforms as a runtime environment for an application, using web technologies is a natural fit: Cloud applications need to be stateless in order to support global scale and easy implementation of resilience patterns.

Thanks to modern browsers and client-side web application technologies, the challenge of running applications in the cloud without losing the benefits of rich desktop applications seems to be solved. However, one question still remains: how can you migrate to cloud-based web applications with as smooth a transition as possible?

## The Big Bang Theory

It is a common belief that large big-bang migration projects tend to expand beyond time and resource budgets. The reason for this is that a big-bang approach prevents risk distribution across small incremental changes and delays feedback. During the migration phase, either no new features can be introduced or they have to be developed for the old and new system in parallel, adding to the cost and risk. The new system lacks any kind of feedback from real users and the production environment, preventing continuous improvement and adjustment based on to metrics.

Therefore, a smooth migration from a legacy system to a new system should be sought by any means. If a fundamental change of the architecture and runtime environment is part of the new system, users often face the issue of working with separate systems because integration might be challenging.

In order to reduce friction and pressure from the development of a complete replacement, integration of the old and new system should be considered instead, even if this results in additional effort. A successful hybrid must support the web-based future and the Swing- or JavaFX-based current parts of the application at the same time. Simply showing a web page inside the desktop application is insufficient. To provide the required level of integration, interaction between the elements of the desktop-based user interface and the web-based user interface must be supported in both directions.

One way to achieve this is by using the `WebView` provided by JavaFX.

## Introducing the JavaFX `WebView`

The JavaFX `WebView` is implemented using a WebKit-based embedded browser. WebKit provides good support for CSS, JavaScript execution, and HTML5 features. Among HTML5, the following features are supported:

  * Canvas
  * Media playback
  * Form controls
  * Editable content
  * Scalable vector graphics (SVG)

As a JavaFX component, the `WebView` is usable inside Swing applications as well. This makes it suitable as a building block for a migration strategy.

The `WebView` API provides various means to configure the browser and to influence the exposed behavior. To implement an embedded web browser, two classes are required: `WebView`, which is the container representing the UI in the JavaFX scene graph, and `WebEngine`, which provides access to the features of the embedded browser.

Usage of `WebView` is straightforward, as shown in Listing 1.

**Listing 1. Instantiating a WebView and loading the JavaOne web page.**

As mentioned earlier, it is possible to influence the behavior of the browser. Listing 2 shows how to override the default look of the web page by adding custom CSS.

**Listing 2. Overriding the default CSS styling using a user stylesheet in the embedded browser.**

Inside the `WebView`, it is further possible to execute JavaScript triggered from the Java part of the application. Exposing Java methods to the JavaScript in the `WebView`, making them callable, is possible as well. Calling JavaScript from the Java application is shown in Listing 3, and exposing a Java-implemented API to the web is shown in Listing 4.

**Listing 3. Calling the JavaScript function `sample()` in the embedded web browser from native Java code.**

When calling JavaScript, references to JavaScript objects or other return values are provided to the calling Java code.

This can be used to get a reference to the `window` object, where additional functions can be called or registered. In order to provide the Java API to the web, exactly this approach is used, as shown in Listing 4.

**Listing 4: Providing a Java-backed API that is available in the embedded web browser. An instance of the public class `ApiBridge` is registered on the `window` object, making it globally visible in the web application.**

With these possibilities, all the required building blocks for tight integration between both worlds are in place.

There are alternatives to the JavaFX `WebView` as well. For example, the Chromium Embedding Framework (CEF) can be used for Java applications as well. This is an important aspect when making a decision for an architectural approach that needs to be feasible for multiple years. Besides positive signs that the JavaFX `WebView` will receive regular updates in the future, different implementation options for the architecture make it less vendor-dependent and less risky.

## Migration Architecture

As we saw in the previous section, a technical infrastructure for bidirectional calls from the Java application to the web application, and vice versa, is available. To protect investment, it is desirable that a migration approach minimizes additional effort when the final move is made to a web-only application without a client-side Java infrastructure.

A possible way to minimize the effort at the final stage could be based on an API design for the application framework that can be mapped to a pure JavaScript client-side application framework later on. It is important to have a minimal API surface at a high-abstraction level, providing only the functions required for integration, not adding a second controller layer. On this layer, high-level functions, such as navigation and access to the business layer, are provided. Exposing legacy APIs as local HTTP services instead of adding these directly to the JavaScript API surface should be considered, decreasing the coupling and enhancing separate testability.

This approach not only provides a means for migration in small steps, but it even provides the means for parallel use of both implementations of the application framework. As soon as essential base features are provided for the web application, it can be accessed standalone, immediately allowing mobile clients without a Java runtime to benefit. If you make use of this possibility, you can gain early feedback from users, allow separate testing, or even provide an early migration for some user groups.

For the web application, the choice of JavaScript and a CSS framework is not constrained in any way. (Note: The WebKit currently used in the JavaFX `WebView` does not support web components, but that is not a shortcoming of this architectural approach.)

When choosing a framework, it should be considered how the data flow model, provided components, programming patterns, and general concepts match the existing knowledge of Swing developers. AngularJS is especially popular for concepts similar to those known by Java developers accustomed to developing JavaServer Faces or Swing applications. If the web application is developed by a third party or by different developers than those that developed the existing application, the requirement for similar concepts can be relaxed.

In the following example application, Oracle JET is used. The application can be used either standalone in a regular web browser or with the Swing application frame.

## Introducing Oracle JET

Oracle JET provides a foundation for building responsive, accessible, and localizable web applications. Under the hood, several open source libraries are used for covering cross-cutting aspects of modern client-side JavaScript applications. The following parts comprise Oracle JET:

  * jQuery is used for Document Object Model (DOM) manipulation, supporting a unified API across different browser versions and platforms.
  * The jQuery UI core is used to provide a component model for GUI components.
  * Oracle Alta UI is a visual style guide developed by Oracle; CSS and SCSS implementations are provided as part of Oracle JET.
  * Crossroads.js is used for client-side routing.
  * RequireJS provides dependency resolution for client-side JavaScript applications.
  * Knockout provides a view-model based architecture that offers data binding capabilities to web developers.
  * Hammer.js is used internally for gesture and touch support.

On top of that, Oracle JET provides various components that are commonly required to build data-driven enterprise applications. All components are equipped with support for accessibility and localization. The benefit this provides should not be underestimated, because these aspects drive big efforts if they are implemented properly. Oracle provides a website called [Cookbook](http://www.oracle.com/webfolder/technetwork/jet/uiComponents-formControls.html) where the components that are part of Oracle JET are shown. Apart from the visual presentation, the receipts contain code samples for HTML and JavaScript, along with developer documentation. The receipts are intended as copy-and-paste templates to ease the development of Oracle JET-based applications. In the long term, an even more convenient way to develop enterprise web applications would extend the cookbook and provide a GUI builder.

To learn more about Oracle JET, visit <http://www.oraclejet.org/>.

In order to work effectively with Oracle JET, a good understanding of the underlying libraries (at least Knockout) is advisable. Knockout uses observables to provide the data binding. Unlike the also-popular AngularJS framework, which uses dirty checking and requires no special treatment of the underlying model, Knockout models must be wrapped by Knockout-specific functions. If the wrapping in Knockout functions is not performed, the data binding will not work, for example, the values are not updated and keep their initial values. Each property that should be bound needs to be wrapped as an observable separately. Knockout provides a mapping plugin, which reduces the amount of boilerplate code significantly, especially when data is retrieved by HTTP calls.

**Listing 5: In order to create an observable property, the Knockout `observable` method is used. With the mapping plugin available, complete structures can be easily made observable.**

Changes on the model can be observed for various reasons apart from updating the view. For example, when a change of the model is performed from a view component, additional actions, such as update calls to the back end, might be required. This use case can be implemented using the `subscribe` function provided by Knockout. A property change will then trigger a call to all functions that subscribed to the property. As with the JavaScript built in `Function.prototype.call()`, the `this` context for the called function can be specified. This is important because the modification callback most likely will happen from a completely different context than the subscription creation.

**Listing 6: Subscribing to the `active` property shown in Listing 5. Each change will result in a call to the function `changePropagation`, which uses the `ContractService` to update the back end.**

## Example Project

As a demonstration project, a simple Swing-based desktop application was created. Use cases from invoicing software that are simplified and limited in scope were used. This boils down to a list of business partners, represented as contracts, which can be enabled or disabled. A contract is the entry point to sending email to the business partner as well. Because business is about making money, invoices have their place in the application as well. Each invoice is either due or paid, which can be toggled from the overview for each invoice.

The sample consists of several typical elements found in enterprise applications:

  * A navigation area
  * Data-driven tables
  * Pop-up dialog boxes
  * Forms
  * A message area in the footer of the dialog box

The example application includes all three stages from a desktop application to a hybrid application to a pure web application. After launching the application, users can choose which stage they would like to see (as shown in Figure 2).

![f2.png](https://community.oracle.com/servlet/JiveServlet/downloadImage/102-1001176-6-185529/f2.png)

**Figure 2. After application launch, the user is presented with the options that reflect a typical migration path from a pure desktop application to a hybrid web/desktop application with a pure web-based application as the final stage. **

On the _contracts_ overview (shown in Figure 3), a table is used to display contracts, allowing the user to enable or disable a contract and send an email to the selected person. When changing a contract, a message is shown in the bottom area of the dialog box.

![f3.png](https://community.oracle.com/servlet/JiveServlet/downloadImage/102-1001176-6-185530/f3.png)

**Figure 3. A Swing dialog showing contracts in the pure desktop mode. In the footer of the dialog box, the latest status message is shown.**

This kind of application is easy to implement as a modern browser-based client application. As can be seen in Figure 4, it is easy to use the Oracle JET components for creating a similar user interface. In order to retrieve contract data from the back end, HTTP is used along with JSON as the transport format.

![f4.png](https://community.oracle.com/servlet/JiveServlet/downloadImage/102-1001176-6-185531/555-400/f4.png)

**Figure 4. Web application implementing the same use case using Oracle JET with the Oracle Alta UI components.**

Implementing a new web application is just one part of the goal to migrate from desktop to the web. Additionally, the integration of newly developed features in the existing Swing-based application is required.

### Basic UI Integration

As shown in the example in Listing 1, adding a web view to a Swing or JavaFX application is quite easy. When embedding the web application in a straightforward way, the application contains its own navigation, which is redundant in this case and could confuse the user.

![f5.png](https://community.oracle.com/servlet/JiveServlet/downloadImage/102-1001176-6-185532/f5.png)

**Figure 5. Embedded web application inside of the Swing desktop application without adjustments. The "hamburger" navigation icon in the upper left and the user menu in the upper right indicate the missing adjustments for embedded usage. **

CSS provides a rather easy approach to this customization need: just hide the navigation section when running as an embedded part of the desktop application. A very handy feature is to specify a user stylesheet in the JavaFX `WebView`, which can contain all customization rules. This is the right place to change fonts, colors, and other graphical details to harmonize the appearance according to the existing style of the hosting application. In Listing 7 and Listing 8, the necessary Java code and used CSS styles are shown:

**Listing 7: Adding a user stylesheet in the web view when a page has finished loading.**

**Listing 8: Content of the stylesheet file to hide the navigation area.**

For this example, the user styles are kept to a minimum, implementing only the hiding of the navigation area. Additional styles could reduce the visual differences of the Swing or JavaFX components used in the desktop application.

![f6.png](https://community.oracle.com/servlet/JiveServlet/downloadImage/102-1001176-6-185533/f6.png)

> _Figure 6. After applying a user stylesheet, the navigation part of the web application is hidden._

In order to achieve complete integration, embedding the web application and visual adjustments alone are not sufficient; behavior needs to be integrated as well.

### Bridging the API

In the example, two features showcase the integration between the web application and the Java application at the API level:

  * Status updates in the message area in the lower part of the dialog box
  * Triggering a Java dialog box and passing data from JavaScript

Exposing Java classes to JavaScript requires that the classes be public and only public methods are visible at the JavaScript layer. In Listing 9, the `ApiBridge` source is shown, as used in the example application.

**Listing 9: Java class that is exposed in the web application to be called by JavaScript.**

As expected for a bridge, this Java class is a very thin layer.

When calling Java code from the JavaScript side, all passed data needs to be converted. In this sample, the `ModelConverter` class provides the transformation logic to map the data from the `JSObject` to a Java domain model. Conversion of primitive types, such as `boolean` values and `String` instances, is performed automatically, but nested data structures are not converted automatically. To access the values of custom objects, the `getMember` accessor is used.

**Listing 10: Converting data passed to Java from JavaScript using the `getMember` method of the `JSObject` type.**

Calling the Java code from JavaScript is quite easy and not different than calling other JavaScript code. Because the bridge is exposed through the `window` object with the name `appFrame`, all Java methods are available as properties on that object. In Listing 11, a call to the `updateStatus` method, which updates the footer text area, is shown.

Note that a safeguard has been placed to check whether the `appFrame` property is present to prevent errors when this JavaScript code is executed outside of the Java application framework. In order to prevent an accidental dependency on the Java framework code, continuous testing of all runtime variants should be performed. This type of dependency could lead to increased effort when the application should be run solely in a web browser without a surrounding Java application.

**Listing 11: Implementing a custom Knockout.js component called `StatusService`. This component is usable from all other Oracle JET and Knockout.js components and provides the `updateStatus` method, which delegates to the registered Java code.**

Because Knockout.js requires observables for all properties that are bound to the view, additional transformation of these objects before passing them to Java is necessary. Otherwise, the data mapping on the Java side would have to either know or determine whether a property is a plain JavaScript property or a Knockout observable. If the aforementioned mapping plugin for Knockout is installed, it can be used for this purpose as well. To keep the example small, a little trick is used: The data is converted to a JSON string, removing all observables, and then converted back to JavaScript.

**Listing 12: Mail service with passing complex objects to Java. In order to remove Knockout.js observables, a conversion to JSON and back is used.**

### Remarks About the Example Application

In some aspects, this project reflects the intention to provide a single, directly runnable example project. In real-world use cases, the Java and JavaScript projects would most likely be separated into two or more projects. Passing data between the JavaScript and Java side of the application would benefit from mapping classes with an API that is easier to approach, for example, using a fluent or builder pattern approach. In addition to that, some shortcuts were taken here. For example, the Swing table model is not capable of supporting dynamically sized lists of contracts or invoices and the exception handling is minimal.

The sample application is provided on [GitHub](https://github.com/trion-development/webbridge-oraclejet).

Because NetBeans has good Java, Swing, Maven, JavaScript, Knockout.js, and Oracle JET support, NetBeans is recommended as the development environment when exploring the sample application or make modifications to it. NetBeans is open source and available for download at <https://netbeans.org/>.

## Conclusion

This article introduced an architectural approach for the smooth migration of rich desktop applications to an API-centric architecture that supports end users as well as other systems that can call an API. Leveraging the browser and JavaFX `WebView` as integration technology opens a path to pure web-based clients for enterprise applications. By using HTTP endpoints, it is easy to provide access for external entities such as partners or native mobile clients. At the same time, this model nicely fits into a cloud-based application infrastructure, opening the option to fully deploy to the cloud as an additional benefit.

Supporting different user groups with their respective needs by providing separate clients on the front end while using the same APIs on the back end increases service reuse and reduces the cost for developing such clients. For example, an agent in the back office could use an expert system with fast data-entry capabilities while an end user could use a wizard-based application through the public internet.

Some challenges still exist. To provide a seamless experience, cross-functional features need to be part of the integration layer for all parts of the application, for example, single sign-on (SSO), single sign-out, permission and access concepts, and logging.

In addition to that, not all operations concepts can be transformed in a reasonable way from a desktop application to the web. For a frictionless integration, it might be necessary to rework some user experience concepts or user interface components to provide a smooth path to a web application.

## See Also

## About the Author

Thomas Kruse studied computer science and is an Oracle Certified Master, Java EE Enterprise Architect. He works as architect, consultant, and coach for [trion development GmbH](https://www.trion.de/). In his free time, he contributes to open source projects and leads the [Java user group in Munster](http://www.jug-muenster.de/). Kruse can be contacted by email at [tk at trion.de](mailto:tk@trion.de).

## Join the Conversation
