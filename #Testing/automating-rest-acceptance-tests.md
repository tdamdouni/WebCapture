# Automating REST Acceptance Tests

_Captured: 2017-10-01 at 19:49 from [dzone.com](https://dzone.com/articles/automating-spring-rest-acceptence-tests-with-cucum?edition=329500&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-10-01)_

Since the inception of Agile development, automated testing has become an indispensable facet of the life of a software project. The addition of such tests allows us to not only systematically execute our tests, but it also allows us to regression test existing functionality to ensure that core features continue to function when changes are made to a code-base. Although automated unit testing has been universally recognized as a worthwhile endeavor, automated tests at other levels are also an important aspect of creating well-functioning and stable software.

In this article, we will explore creating automated acceptance tests for a Spring web application using Cucumber and Gherkin scenarios. By its completion, we will have explored the thought process of capturing human-readable acceptance tests and executing these tests in an automated manner on a functioning system. The entirety of this article will use the following project as a basis:

![Image title](https://dzone.com/storage/temp/6716880-github-repo.png)

For more information on the design and implementation of this project, see [Creating a REST Web Service With Java and Spring, Part 1)](https://dzone.com/articles/creating-a-rest-api-with-java-and-spring).

## Capturing the Acceptance Criteria

The first step in automating acceptance tests is to capture the tests in a document. In most cases, acceptance tests are written by people other than the developers actively creating the core functionality of the system. Whatsmore, those developing the acceptance tests may not even be a developer, and thus, requiring that the acceptance tests be captured directly in software is untenable. Therefore, we must devise a human-readable format in which our acceptance criteria can be captured.

Since we will use [Cucumber](https://cucumber.io/) as our acceptance testing framework, we will use [Gherkin](https://github.com/cucumber/cucumber/wiki/Gherkin) as our acceptance test language. Gherkin is a human-readable language written in the Given-When-Then format, where a single Given-When-Then test is packaged as a scenario and one or more scenarios are grouped together to create a feature. For example, we will use the following Gherkin feature to exercise the acceptance criteria for our order management system linked above:

As seen in the Gherkin specification, these tests are simple in nature: each uses the order REST API to create, get, update, or delete an order and checks the various status codes and state of the responses that are returned upon completion of the request. This simplicity is a byproduct of the simplicity of the Gherkin language. Although we have used the most common language structures in the specification above, there are many others that aid in the development of concise and targeted acceptance test criteria. For more information on these features, see the [Feature Introduction](https://github.com/cucumber/cucumber/wiki/Feature-Introduction) section of the Gherkin documentation.

While our acceptance test specification is complete, in its current state, it cannot actually test the functionality of our system. To accomplish this, we must back our acceptance test specification with executable code.

## Backing the Criteria With Executable Code

Each step (lines starting with `Given`, `When` , `Then`, or `And`) in our specification exercise some specific action in our system. For example, "When the user gets the created order" actually means that we should execute an HTTP GET call to our `http://localhost/order/{id}` endpoint, using the ID of the last created order. In order to execute this logic, we must implement our steps in Java (or another [supported language](https://cucumber.io/docs#cucumber-implementations)) to perform these calls. A simple implementation of this step (that does nothing) can be seen below:

The core of this call is the `@And` annotation that we have decored our `theUserRetrievesTheOrder` method with. This annotation tells Cucumber that this method should be used to execute a step found in the Gherkin specification. Cucumber maps our method to a specific step using the regular expression parameter of the `@And` annotation. For example, when the string `the user gets the created order` is found in the Gherkin specification, this method is executed. At the moment, our implementation does not actually test anything: in order to properly test our REST API, we must start making calls to the API.

### Creating an HTTP Framework

Although we could manually use a class to make an HTTP request to `http://localhost/order/{id}` for us, this duplicates the functionality provided by the testing classes provided by the Spring Model-View-Controller (MVC) framework. In particular, the `[MockMvc](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/test/web/servlet/MockMvc.html)` class allows us to make REST calls directly to our controllers without having to include any base URLs (i.e. `http://localhost`) and reduces the cost of such calls by mocking the interaction with our controller. In order to make these calls within our step implementations, we will create an abstract base class that contains the mock Spring MVC logic that will be utilized by our steps:
    
    
        protected void get(String url, Object... urlVariable) throws Exception {
    
    
        protected void post(String url, String body, Object... urlVariables) throws Exception {
    
    
        protected void put(String url, String body) throws Exception {
    
    
        protected void delete(String url, Object... urlVariables) throws Exception {
    
    
        protected <T> T getLastGetContentAs(TypeReference<T> type) throws Exception {
    
    
        private static <T> T deserializeResponse(MockHttpServletResponse response, TypeReference<T> type) throws Exception {
    
    
        protected static <T> T deserialize(String json, Class<T> type) throws JsonParseException, JsonMappingException, IOException {
    
    
        protected static <T> T deserialize(String json, TypeReference<T> type) throws JsonParseException, JsonMappingException, IOException {

Although this class may seem overwhelming, if we break it down, it is strikingly simple. First, we notify the Spring framework to provide a web context configuration using a combination of the `@WebAppConfiguration`, `@ContextConfiguration` , and `@AutoConfigureMockMvc` annotations. Although not included, the `Application`class is the application configuration used by our Spring Boot application, and thus, we are reusing the configuration provided by this class. For more information, see the [Application class](https://github.com/albanoj2/order-rest-backend/blob/master/src/main/java/com/dzone/albanoj2/example/rest/Application.java) in the order management repository.

Next, we autowire our `MockMvc` object (provided by Spring MVC) into our class. This `MockMvc` object will be used later to make HTTP GET, POST, PUT, and DELETE calls to our REST API. The remaining parameters are used to store the last responses from each of the aforementioned HTTP calls. These responses must be stored after a call completes so that future steps can examine the response (i.e. the body or status code of the response) to ensure that a call was successful according to the specified criteria. For example, if we create an order in one step and then check to see if the correct status code was received in response in another step, we must store the response to be examined after the call to create the order completes.

The implementation of the HTTP calls requires further detail. In particular, the implementation of the GET call can be seen below:

The parameters of this method allow us to call it with URL path variables if we desire. For example, both `get("/order")` and `get("/order/{id}", someId)` are valid calls to this method. Both the URL and the path variables are passed to the `MockMvc` object and an HTTP GET call is performed (instructing the controller that we expect JavaScript Object Notation, JSON, data in response). Our implemented controller then responds and we capture both the last GET response and the last status code to be used by other steps at a later time.

The remaining methods are a combination or getters and deserialization helper methods; the getters are simple enough to require no further explanation, so we will focus on the deserialization methods. Although we have captured the HTTP responses for each of the desired HTTP verbs (GET, POST, etc.), the response body from these objects is captured as a JSON string. In order to treat it as the desired object (such as a JSON map), we must deserialize it.

Doing so ourselves is a tedious task, and therefore, we delegate to the [Jackson framework](https://github.com/FasterXML/jackson) to perform the deserialization for us. For more information on the deserialization process, see the [official documentation for the ObjectMapper class](https://fasterxml.github.io/jackson-databind/javadoc/2.7/com/fasterxml/jackson/databind/ObjectMapper.html). It suffices to say that using the Jackson framework, we specify the desired deserialization type (the type that we want the JSON response body to be converted to) and Jackson makes its best attempt to deserialize the JSON string to that type, or else it throws an exception.

With the completion of the deserialization methods, we can lastly move to providing an implementation of the steps in our Gherkin specification.

### Implementing the Test Steps

Since we have abstracted the HTTP actions in our `AbstractSteps`class, the logic for implementing our Gherkin steps is simple:

First, we extend the `AbstractSteps` abstract class to ensure we can utilize the logic we have previously created; many of the calls that we make within each of the step implementations is simply a call to one of the underlying methods of the `AbstractSteps` class. Next, we create two static constants: (1) a test order, as a JSON string, and (2) a type reference representing a JSON map used by Jackson. The former will be used as the request body when executing a POST to create a new order, which will, in turn, be deserialized by the REST API and used to create a new order. The latter will be used when deserializing the responses received after completing various HTTP calls, which will allow JSON string response bodies to be deserialized into a map of strings to objects; this allows us to inspect the response body using the `get`notation, such as `responseBody.get("id")`.

The remainder of the methods are implementations of the steps using the `@Given`, `@Then`, `@When`, and `@And` annotations, as we previously saw. Note that a step that is defined using one of these annotations is not restricted to its associated step. For example, a step defined using the `@Then` annotation may be used as an `And` step in our Gherkin specification, such as the following:

In this case, we use the `@Then`annotation to bind our implementation to both steps:

Within each step implementation, we use the standard JUnit assert methods to make declarations about the expected behavior of our system. JUnit then ensures that all assertions resolve to true prior to marking a test (or step, in this case) as passed. Just as with any other JUnit-driven test case, we must provide some bootstrapping code to drive the tests.

## Bootstrapping the Automated Tests

To get our tests to run with JUnit, we create the following bootstrap class:

The `@RunWith` annotation instructs JUnit to use Cucumber-supplied test runner class as the test runner, which provides Cucumber with the reins while our tests are executed. The next annotation, `@CucumberOptions(feature = "src/test/resources/acceptance")`, tells Cucumber where our `.feature` files (containing the Gherkin specifications) are located. In our case, our sole `.feature` file is located at `[src/test/resources/acceptance/order.feature](https://github.com/albanoj2/order-rest-backend/blob/master/src/test/resources/acceptance/order.feature)`. Lastly, the `@WebAppConfiguration` annotation instructs the Spring framework to use a web application context for our injected application context (which is used by the `AbstractSteps` class to make REST calls). For more information on the differences between a standard application context and a web application context, see [this explanation](https://stackoverflow.com/a/11709272/2403253).

With our bootstrap code complete, we can now run our acceptance tests by executing the following Maven command on the command line:

Upon completion of this build phase, we can see the following output:

This output reflects that all of our 3 acceptance scenarios (which are cumulatively composed of 14 steps) have successfully completed. While the time of execution will vary between runs and between test environments, for simple tests, it can take only seconds to complete. This ensures that we can pragmatically and consistently run these acceptance tests each time our system changes and ensure our high-level, customer behavior does not change as our system progresses.

## Conclusion

Acceptance tests are an essential component of all major systems and are one of the few categories of tests that exercise behavior that the customer will experience. While manual acceptance tests are required in some cases, a large portion of acceptance tests can be automated and routinely run after each change. Although this is a desirable goal, it can be difficult to combine the various testing components of SpringMVC, JUnit, and an acceptance testing framework, such as Cucumber.

In this article, we explored the interconnection of each of these parts, abstracting the HTTP calls (through the Spring MVC testing framework) from the Cucumber step implementations that utilize these calls. With this separation, we are able to simply and quickly execute our acceptance tests, ensuring that as our system rapidly changes, we continue to meet the expectation of our customers.
