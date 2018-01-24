# Test as you run (Part 1)

_Captured: 2018-01-03 at 16:24 from [blogs.itemis.com](https://blogs.itemis.com/en/test-as-you-run-part-1)_

tl;dr: It's easy to build microservices test-driven and I'm gonna show you how.

Building a microservices system in a test-driven way can seem quite hard. Based on my talk at the [Eclipsecon Europe 2017](https://www.youtube.com/watch?v=b5qX_DUMHNY) I will give an overview on how to create a docker-based microservices system in a test-driven way and how to test every reasonable scope.

Disclaimer: I will not explain every tool I use, especially neither Git nor Intellij Idea nor Spring nor Gradle nor Docker nor Cassandra; but I will try to add some links so that you can read some additional information about the used technologies.

Let's get started with an elementary example for tests.

Therefore please checkout the repository by typing the following into your shell:

`git clone https://github.com/gunkelolaf/test_as_you_run.git`

and checking out the first step:

`git checkout step1`

## Project setup

You will find this basic project setup:

![test-as-you-run-basic-setup.jpeg](https://blogs.itemis.com/hubfs/Blog/Software%20Development/test-as-you-run-basic-setup.jpeg?t=1514992779618)

The project is organized as a Gradle multi-project build. This version of the project only contains one sub-project, the CapitalizeService.

Let's have a look at the parent build.gradle:

group 'de.itemis.webengineering.blog'

subprojects {

apply plugin: 'java'

sourceCompatibility = 1.8

targetCompatibility = 1.8

repositories {

mavenCentral()

}

dependencies {

compile 'com.google.guava:guava:23.0'

testCompile 'junit:junit:4.12'

testCompile 'org.assertj:assertj-core:3.8.0'

}

}

All sub-projects get the dependencies to the test frameworks[ Junit](http://junit.org) and [Assertj](https://joel-costigliola.github.io/assertj/), a dependency to [guava](https://github.com/google/guava) (which is necessary for basically everything) and the java plugin.

When we look at the build.gradle of the CapitalizationService we only find an empty file since no additional setup is required.

## The CapitalizeService

The CapitalizeService fulfills a very simple task:

It takes a string, and capitalizes the first character. The whole business logic for that can be found in the CapitalizeUtil class. It's quite easy to write unit tests for this logic:

import org.junit.Test;

import static org.assertj.core.api.Assertions.*;

public class CapitalizeUtilTest

{

@Test

public void shouldCapitalizeSingleCharacter()

{

//given

final String singleCharacter = "c";

//when

final String result = CapitalizeUtil.capitalize(singleCharacter);

//then

assertThat(result).isEqualTo(singleCharacter.toUpperCase());

}

@Test

public void shouldCapitalizeWord()

{

//given

final String wordToCapitalize = "hello";

//when

final String result = CapitalizeUtil.capitalize(wordToCapitalize);

//then

final String expectedResult = "Hello";

assertThat(result).isEqualTo(expectedResult);

}

@Test

public void shouldNotChangeCapitalizedString()

{

//given

final String capitalizedString = "HELLO";

//when

final String result = CapitalizeUtil.capitalize(capitalizedString);

//then

assertThat(result).isEqualTo(capitalizedString);

}

@Test

public void shouldReturnEmptyString()

{

//given

final String capitalizedString = "";

//when

final String result = CapitalizeUtil.capitalize(capitalizedString);

//then

assertThat(result).isEqualTo(capitalizedString);

}

@Test

public void shouldNotAcceptNullAsInput()

{

assertThatThrownBy(() -> CapitalizeUtil.capitalize(null))

.isInstanceOf(IllegalArgumentException.class);

}

}

All these tests run on my computer in approximately 50 milliseconds so they are super fast and fit into the definition of unit tests.

## The Server Tests

Since we have unit-tested our whole business logic, we can go on and integrate it into a server.

Please checkout the next step:

`git checkout step2`

HINT: If you want to list all files changed and added in the commit please run the following command in your shell:

`git diff-tree -- no-commit-id -- name-only -r step2`

Let's have a look at the changed and added files. The root build.gradle file was extended with a buildscript dependency:

buildscript {

ext {

springBootVersion = '1.5.8.RELEASE'

}

repositories {

mavenCentral()

}

dependencies {

classpath("org.springframework.boot:spring-boot-gradle-plugin:${springBootVersion}")

}

}

Heading for line 9, we see the [Spring Boot Plugin](https://docs.spring.io/spring-boot/docs/current/reference/html/build-tool-plugins-gradle-plugin.html) added to the buildscript classpath. This configuration allows us to use the plugin in every sub-project.

The build.gradle file of the CapitalizeService project got its first line:

`apply from: '../service.gradle'`

Since gradle supports script plugins we can externalize configurations for special types of projects. Therefore, all necessary configurations for services are done in of the service.gradle file inside the root directory.

apply plugin: 'org.springframework.boot'

dependencies {

compile('org.springframework.boot:spring-boot-starter-web')

testCompile("org.springframework.boot:spring-boot-starter-test")

}

Now that all dependencies are in place, we can put our mind to the implementation:

The CapitalizeService has the CapitalizeApplication class, which is a normal Spring application start class.

The CapitalizeController is a Spring RestController providing one GET-endpoint with a path variable defining the string to capitalize. Calling the path /capitalize/hello, the result will be "Hello".

@RestController

public class CapitalizeController

{

public static final String CAPITALIZE_PATH = "/capitalize";

@RequestMapping(CAPITALIZE_PATH + "/{stringToCapitalize}")

public String capitalizeString(@PathVariable final String stringToCapitalize)

{

return CapitalizeUtil.capitalize(stringToCapitalize);

}

}

The implementation is pretty much straight forward. So how do we test this?

Spring provides us with (at least) two possible testing setups:

## The Server-Mock-Test

The following code shows a snippet of the ServerMockTest class:

@RunWith(SpringRunner.class)

@WebMvcTest

public class ServerMockTest

{

@Autowired

private MockMvc mockMvc;

@Test

public void shouldCapitalizeSingleCharacter()

{

final String singleCharacter = "c";

final String expectedResult = "C";

//given

final String requestPath = CapitalizeController.CAPITALIZE_PATH 

\+ "/"

\+ singleCharacter;

//when

this.mockMvc.perform(get(requestPath))

//then

.andExpect(status().isOk())

.andExpect(content().string(expectedResult));

}

}

In line 2 we see that the WebMvcTest-annotation is added to the test.

Because of the annotation, our application without the server (but with every layer behind the server) will get started before the actual test methods run.

The MockMvc object that is autowired in lines 5-6 provides us with the opportunity to test our endpoint with an actual request without the overhead of starting the whole server.

All these tests run in approximately 75 milliseconds, so they are also very fast and I don't feel stopped at all running them on a regular basis while developing the service. From my point of view it's absolutely feasible to use them for test-driven development.

## Server-Stack-Test

Now that we have tested our business logic with unit tests and our endpoint with Server-Mock-Tests, we're ready to test the whole server.

Spring provides us with a very convenient way to do this:

Let's have a look at the ServerStackTest class (or actually a snippet from it):

@RunWith(SpringRunner.class)

@SpringBootTest(webEnvironment = SpringBootTest.WebEnvironment.RANDOM_PORT)

public class ServerStackTest

{

@Autowired

private TestRestTemplate restTemplate;

@Test

public void shouldCapitalizeSingleCharacter()

{ 

//given 

final String inputToCapitalize = "c";

final String expectedResult = "C";

final String requestPath = CapitalizeController.CAPITALIZE_PATH 

\+ "/"

\+ inputToCapitalize;

//when

final String response = this.restTemplate.getForObject(requestPath, String.class);

//then

assertThat(response).isEqualTo(expectedResult);

}

}

The Lines 2, 5, and 6 are the first we have a look at. The SpringBootTest annotation will setup our whole server before the tests will take place. Additionally, the TestRestTemplate object that is autowired in lines 5 and 6 allows us to sent actual requests against our server. As we can see in line 16, we interact with our server just like we interact with any other REST resource.

These tests run in approximately 170 milliseconds, which feels to slow for a test-driven develpment approach. Therefore I really need the tests of the smaller scopes, like the Server-Mock-Test, to feel comfortable while developing services.

Still, considering these tests are testing the whole server, the run-time is blazing fast.

These two possibilities for server tests give us very comfortable ways of testing our software; furthermore, we're enabled to write our services test-driven with nearly no overhead.

## Let's Cross Some Borders

Testing the CapitalizeService was pretty easy, since the service has no dependencies to any other system. That's nice, but not really even near to a real-world problem. So let's go on with a service depending on a database in [part 2 of this series](https://blogs.itemis.com/en/test-as-you-run-part-2-testing-with-database-mocks).
