# Test as you run (Part 5) – Building and Testing Systems

_Captured: 2018-01-03 at 16:23 from [blogs.itemis.com](https://blogs.itemis.com/en/test-as-you-run-part-5-building-and-testing-systems?utm_source=hs_email&utm_medium=email&utm_content=59754756&_hsenc=p2ANqtz--tYRmRnArsY2sr83H6rWwTIdudlvNeW1vdPh14W_1fgcEsIz2oEzdGULrPecfdvcLY8Id84VGqlFAzteTK4K4onICZzw&_hsmi=59754756)_

In the [previous part](https://blogs.itemis.com/en/test-as-you-run-part-4-production-like-integration-test) of our series about test-driven development of microservices we created some debug configurations and integration tests with all dependencies in place. This is the fifth part.

The first can be found [here](https://blogs.itemis.com/en/test-as-you-run-part-1).

Let's have a look on how to test a whole system.

Please checkout step 6:

`git checkout step6`

A new Service was added to the project called the BFFService that is basically facade or simplistic [BFF](http://samnewman.io/patterns/architectural/bff/) for the other two services. It uses the UserService to store users and the CapitalizeService to capitalize the users first- and lastname.

## **Unit Tests first**

The project has two testing sourcesets: test and integrationTest.  
The testing sourceset contains small Unit-tests for the BFFService logic to check the interaction with the UserService and the CapitalizeService.

Let's have a look into (a snippet) of this test:

@RunWith(SpringRunner.class)

@WebMvcTest(BFFController.class)

public class BFFControllerTest

{ 

@Autowired private MockMvc mockMvc;

@MockBean CapitalizeServiceClient capitalizeServiceClient;

@MockBean UserServiceClient userServiceClient;

@Test

public void shouldCallUserServiceToSaveUsers() throws Exception

{

//given

final String firstName = "john";

final String lastName = "doe";

final MockHttpServletRequestBuilder createUserJohnDoe = post(BFFController.CREATE_USER_PATH)

.param(BFFController.FIRSTNAME_PARAM, firstName)

.param(BFFController.LASTNAME_PARAM, lastName);

//when

this.mockMvc.perform(createUserJohnDoe);

//then

verify(this.userServiceClient).createUser(firstName, lastName);

}

@Test

public void shouldCallUserServiceToAskForUser() throws Exception

{

//given

final String lastName = "doe";

final MockHttpServletRequestBuilder requestBuilder = get(BFFController.GET_USERS_BY_LAST_NAME_PATH + "/" \+ lastName);

//when

this.mockMvc.perform(requestBuilder);

//then

verify(this.userServiceClient).getUsersByLastName(lastName);

}

@Test

public void shouldCallCapitalizeServiceWhenAskedForUsers() throws Exception

{

//given

final String firstName = "john";

final String lastName = "doe";

when(this.userServiceClient.getUsersByLastName(lastName))

.thenReturn(ImmutableList.of(new User(firstName, lastName)));

final MockHttpServletRequestBuilder getUsersWithLastNameDoe = get(BFFController.GET_USERS_BY_LAST_NAME_PATH + "/" \+ lastName);

//when

this.mockMvc.perform(getUsersWithLastNameDoe);

//then

verify(this.capitalizeServiceClient).capitalizeString(firstName);

verify(this.capitalizeServiceClient).capitalizeString(lastName);

}

}

The RestClients used to communicate with the UserService and CapitalizeService are mocked in lines 6 and 7 and interactions are verified based on these mocks.

## **Check the System**

Okay, so we have created a service that interacts with other services and we created some unit tests for these interactions. That's nice and it helps us to find problems early, but it's not enough for testing the the system created out of the three services. So let's have a look at the integration test:

@RunWith(SpringRunner.class)

@SpringBootTest(webEnvironment = SpringBootTest.WebEnvironment.RANDOM_PORT)

public class BffServiceIntegrationTest

{ @Autowired

private TestRestTemplate restTemplate;

@Test

public void readAndWriteUser() throws Exception

{ //given

final User alfred = new User("alfred", "pennyworth");

final String createUserRequest = UriComponentsBuilder.fromUriString(BFFController.CREATE_USER_PATH)

.queryParam(BFFController.FIRSTNAME_PARAM, alfred.getFirstName())

.queryParam(BFFController.LASTNAME_PARAM, alfred.getLastName())

.toUriString();

final String getUsersRequest = BFFController.GET_USERS_BY_LAST_NAME_PATH + "/" \+ alfred.getLastName();

//when

this.restTemplate.getForObject(createUserRequest, User.class);

final User[] users = this.restTemplate.getForObject(getUsersRequest, new User[]{}.getClass());

//then

assertThat(users).hasSize(1);

assertThat(users[0].getFirstName()).isEqualTo("Alfred");

assertThat(users[0].getLastName()).isEqualTo("Pennyworth");

}

@Test

public void shouldGetKnownUsers() throws Exception

{ //given

final User bruce = new User("Bruce", "Wayne");

final User martha = new User("Martha", "Wayne");

final User thomas = new User("Thomas", "Wayne");

final String getWaynesRequest = BFFController.GET_USERS_BY_LAST_NAME_PATH + "/" \+ bruce.getLastName().toLowerCase();

//when

final User[] users = this.restTemplate.getForObject(getWaynesRequest, new User[]{}.getClass());

//then

assertThat(users).hasSize(3);

assertThat(users).containsExactlyInAnyOrder(bruce, martha, thomas);

}

}

The test looks a lot as we expected; it's a server-stack test checking the service with real requests. For this tests all dependencies of the BFFService have to be in place so let's have a look into (a snippet of) the BFFService build.gradle:

apply from: '../service.gradle'

apply plugin: 'docker-compose'

dockerCompose {

useComposeFiles = ['bff-docker-compose.yml']

}

integrationTest.doFirst {

setDependenciesEnv(environment)

}

dockerCompose.isRequiredBy(integrationTest)

def setDependenciesEnv(environment) {

def serviceinfos = dockerCompose.servicesInfos

def userserviceinfos = serviceinfos.userservice

def userservicehost = userserviceinfos.firstContainer.inspection.NetworkSettings.Networks.entrySet().iterator().next().getValue().IPAddress

def userserviceport = userserviceinfos.ports[4583]

def capserviceinfos = serviceinfos.capitalizeservice

def capservicehost = capserviceinfos.firstContainer.inspection.NetworkSettings.Networks.entrySet().iterator().next().getValue().IPAddress

def capserviceport = capserviceinfos.ports[3491]

environment.put('capitalizeservice.host', capservicehost)

environment.put('capitalizeservice.port', capserviceport)

environment.put('userservice.host', userservicehost)

environment.put('userservice.port', userserviceport)

}

integrationTest.dependsOn(':UserService:buildDockerForIntegrationTest')

integrationTest.dependsOn(':CapitalizeService:buildDockerForIntegrationTest')

composeUp.mustRunAfter(':CapitalizeService:buildDockerForIntegrationTest')

composeUp.mustRunAfter(':UserService:buildDockerForIntegrationTest')

The integrationTest task depends on docker-compose and uses the following compose-file:

`version: '3'  
`services:  
cassandra:  
image: usercassandra:latest  
expose:  
\- 9042  
userservice:  
image: testasyourun/userservice:integrationtest  
ports:  
\- 4583  
depends_on:  
\- cassandra  
environment:  
\- cassandra.host=cassandra  
\- cassandra.keyspace=test  
\- cassandra.port=9042  
capitalizeservice:  
image: testasyourun/capitalizeservice:integrationtest  
ports:  
\- 3491

By orchestrating the docker containers shown above the CapitalizeService, the UserService, and the testdata Cassandra are started and the UserService get's automatically connected to the Cassandra. By having a look at the setDependenciesEnv method in the build.gradle we see that all necessary information of the two services directly used by the BFFService are passed to it throw the environment as we've seen before. That's pretty straight forward.

## **Where do all these images come from**

We want to have docker images of the UserService and the CapitalizeService to use them for the integrationtests of the BFFService. To build these docker-images we use the gradle [docker plugin](https://medium.com/r/?url=https%3A%2F%2Fgithub.com%2FTransmode%2Fgradle-docker) as you can see in the root build.gradle:

`classpath 'se.transmode.gradle:gradle-docker:1.2'`

Futhermore the service.gradle file was extended:

apply plugin: 'docker'

docker {

group = 'testasyourun'

baseImage "openjdk:8-jre"

}

task buildDockerForIntegrationTest(type: Docker, dependsOn: build) {

version = 'integrationtest'

applicationName = jar.getBaseName().toLowerCase()

entryPoint(['java', '-jar', "${jar.archiveName}"])

addFile {

from jar

}

}

A task was added to every service using the docker plugin to create a docker image. Executing this task will give us the images defined in the above docker-compose file used by the integrationtests of the BFFService.

To ensure that the images of the UserService and the CapitalizeService are build before they are used by the BFFServices integration test the tasks are defined as dependencies of the integration-test-task (see the lines 30-33 in the BFFServive build.gradle). If we want to test and build our complete system now, all we have to do is to type:

`./gradlew build`

into our console :-)

## Let's sum it up

Testing Microservices in every reasonable scope is quite easy if we follow some best practices:

  * separate your business logic from the framework specific logic and test it with unit tests.
  * Test the small scopes first with some advanced mock frameworks well fitting to your technology stack
  * create fully automated integration tests against your complete setup

I hope you enjoyed the article and I would be glad to get some feedback.

I've you miss some explanation please have a look into the git-repository since it contains some more configurations and tests I haven't explained here in detail.
