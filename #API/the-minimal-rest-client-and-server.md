# The Minimal REST Client and Server

_Captured: 2017-10-05 at 15:53 from [dzone.com](https://dzone.com/articles/the-minimal-rest-client-and-server?edition=329519&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=integration%202017-10-05)_

REST applications lie at the heart of microservices and Spring Boot obviates a lot of configuration code. This naturally begs the question: What is the minimal amount of code you have to write for a REST microservice? The answer turns out to be: Nothing or nearly nothing. We demonstrate this by working through an example.

First, we develop the domain object. We deliberately keep it simple as to not obscure the main point. We will define an Employee class with just one attribute: name. We have added JPA annotations since we will persist the object. Now, good practice requires that we add an argument bearing constructor to initialize the object, a matching pair of equals and hashcode, and maybe a toString method. To be sure your favorite IDE can generate all these. But not only does it clutter the code worse, if you ever add more attributes you have to delete these methods and regenerate the code. We avoid all this by using Lombok. At a derisory cost, Lombok will inject all this in the class binary, as you can see in the project explorer in Eclipse.

Now we use Spring Data to define a repository to persists the object (we will use the embedded H2 database, but you are free to configure say MySQL as a database).

Note that we have just defined an interface and relied on Spring Data JPA to provide the implementations. Spring Data will craft a concrete set of operations, such as save(Employee), delete(Employee), find(Employee), find(Long id), findAll() and findByName(String name). See <https://docs.spring.io/spring-data/jpa/docs/current/reference/html/>.

Now we need to expose the repository as REST endpoints. Customarily, we would write a controller somewhat like this:
    
    
      @RequestMapping(value = "/employeesAll", method = RequestMethod.GET)

This is unnecessary. As the documentation states:

"_In its core, REST defines that a system consists of resources that clients interact with. .. But implementing even the simplest tenet of REST web services for a multi-domain object system can be quite tedious and result in a lot of boilerplate code._

_Spring Data REST builds on top of Spring Data repositories and automatically exports those as REST resources. It leverages hypermedia to allow clients to find functionality exposed by the repositories and integrates these resources into related hypermedia based functionality automatically."_

Bottom line: we can expose find All() method of the Employees repository via the REST endpoint GET /employees. Likewise, we can insert an employee via POST /employees Similarly GET /employees/{id} will expose the find(id) method and so on. All other methods will return a 405 Method Not Allowed. For a full description, see <https://docs.spring.io/spring-data/rest/docs/current/reference/html/.>

To summarize what we have so far: we defined a domain object and skipped writing its boilerplate methods with Lombok. We defined a repository interface and let Spring Data JPA provide the implementations of many standard methods. We then exposed this repository as REST endpoints by using Spring Data Rest, and again we let Spring take care of providing the endpoint implementations.

If you use a browser and go to <http://localhost:7111/employees,> you will see something like this:

Where we have persisted some sample data:

Recall that the documentation said "_It leverages hypermedia to allow clients to find functionality exposed by the repositories". _What we are seeing is HAL+JSon output. HAL is a specification to include hypermedia links in a JSON object (see <http://stateless.co/hal_specification.html>).

Now, onto the client. Surely _now_ we need to write some code with RestTemplate and so on right? Nope. We can use Netflix Feign to create a client to the REST service with no code. Feign is a declarative REST client. To use it, all we have to do is to annotate the REST interface. Normally, we would use a fluent FeignBuilder to configure a JSON Encoder and decoder, but Spring Cloud Feign uses the default HttpMessageConverters used in Spring Web MVC.

Note that we defined the Feign client using an interface and the getEmployees() method returns not an Employee JSON, but a HAL+JSON Employee with links. I have to admit this had me flummoxed for a while, until I saw [Josh Long's code](https://github.com/joshlong/not-a-last-minute-demo) on GitHub, from which I shamelessly copied my method. Now, if in a browser you do localhost:8080/employeeNames, you should see

**[**"Gita","Krishna"**]**

That's it. Of course, real-world domain objects are not this trivial, and you may have a lot more attributes, but using Lombok nothing changes. Also, you may have to add more custom methods to the repository interface. But as long as you follow a prescribed naming convention for the methods, Spring Data JPA will provide the implementation. It is nice that all this boilerplate comes gratis.
