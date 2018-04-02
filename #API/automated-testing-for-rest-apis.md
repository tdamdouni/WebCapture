# Automated Testing for REST APIs

_Captured: 2018-02-09 at 14:32 from [dzone.com](https://dzone.com/articles/automation-testing-for-rest-api?edition=361094&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-02-09)_

Integration testing is the phase of software testing in which individual software modules are combined and tested as a group instead of testing each class independently. This can be achieved easily by using JUnit for backend code and Selenium for UI. Both of these tests can be part of Build/CI system to view the report and fail/pass the build/CI system.

Since all of us are now writing or maintaining RESTful microservices and these services/APIs are exposed to the web and distributed over different networks, they are vulnerable to risks and security threats which affect the processes based on them. Hence, testing becomes necessary to ensure they perform correctly. To test these APIs, it's very important to automate REST API test cases instead of relying on manual testing. This tutorial focuses on the basic principles, mechanics, and few ways of testing a REST API. For simplicity, the [GitHub REST API](http://developer.github.com/v3/) will be used here.

There are various technologies and tools available; a few of them are Apache HTTP client, [rest-assured](https://github.com/rest-assured/rest-assured/wiki/usage), [soapUI](http://soapui.org), [Postman](http://getpostman.com), etc. Out of all these, I will be describing Apache HTTP client, rest-assured, and soapUI.

This kind of testing will usually run as a late step in a Continuous Integration process, consuming the REST API after it has already been deployed.

When testing a REST API, the tests should focus on:

  * HTTP response code

  * Response body - JSON, XML

  * HTTP headers in the response

## 1\. Writing Test Cases With Apache HTTP Client

HttpClient provides an efficient, up-to-date, and feature-rich package implementing the client side of the most recent HTTP standards and recommendations.

  * HTTP response code
    
    
         HttpUriRequest request = new HttpGet( "https://api.github.com/events" );
    
    
         HttpResponse httpResponse = HttpClientBuilder.create().build().execute( request );     

  * Response body & header
    
    
    HttpUriRequest request = new HttpGet( "https://api.github.com/events" );
    
    
    HttpResponse response = HttpClientBuilder.create().build().execute( request );
    
    
        Event[] events = new ObjectMapper().readValue(response.getEntity().

## 2\. Writing Test Cases With rest-assured

REST-assured is a Java [DSL](https://en.wikipedia.org/wiki/Domain-specific_language) (domain specific language) for simplifying testing of REST-based services built on top of HTTP Builder. It supports POST, GET, PUT, DELETE, OPTIONS, PATCH, and HEAD requests and can be used to validate and verify the response of these requests

  * HTTP response code, response body & header.

With rest-assured, various test scenarios can be covered in a very simple way. More details about rest-assured are available [here](https://github.com/rest-assured/rest-assured/wiki/usage).

## 3\. Writing Test Cases With SoapUI

SoapUI is an open source, cross-platform testing tool. It can automate functional, regression, compliance and load testing of both SOAP and REST web services. It comes with an easy-to-use graphical interface and supports industry-leading technologies and standards to mock and stimulate the behavior of web services.

Below are the steps needed to set it up and details about each step are available [here](https://www.soapui.org/).

  1. Creation of soapUI test project.
  2. Defining endpoints.
  3. Test case and test suite creation.
  4. Addition of test steps for endpoints.
  5. Generating the project descriptor.

Once we are done with the above steps, create a maven project with below plugin added in the pom. The below snippet assumes that the name of the project descriptor file is project.xml.

If it is not available under the default Maven repo, you would need to add the following repository:

Run the following Maven command to run all your tests:
