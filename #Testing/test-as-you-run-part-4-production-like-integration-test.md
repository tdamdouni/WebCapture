# Test as you run (Part 4) – Production like Integration Test

_Captured: 2018-01-03 at 16:25 from [blogs.itemis.com](https://blogs.itemis.com/en/test-as-you-run-part-4-production-like-integration-test)_

In the [previous part](https://blogs.itemis.com/en/test-as-you-run-part-3-interactions-with-docker-containers) of our series about test-driven development of microservices we had a look at how to use Gradle and Docker to debug a service with a database dependency in place and we created a Cassandra Docker image that contains some testdata. This is the fourth part.

The first part can be found [here](https://blogs.itemis.com/en/test-as-you-run-part-1).

Now please checkout the next step:

`git checkout step5`

Starting with the root build.gradle we see that the [testsets-plugin](https://medium.com/r/?url=https%3A%2F%2Fgithub.com%2Funbroken-dome%2Fgradle-testsets-plugin) was added to the classpath:

`classpath 'org.unbroken-dome.gradle-plugins:gradle-testsets-plugin:1.4.2'`

This plugin allows us to easily define additional test source sets with test-tasks. Looking into the service.gradle we see some new lines:

`testSets { integrationTest }  
`integrationTest.mustRunAfter(test)  
build.dependsOn(integrationTest)

A new testSet named "integrationTest" is defined using the testSets plugin and the build task got a new dependency to the integrationTest Task. Additionally we define an order between the test- and integrationTest-task to prevent the integration tests to be executed before the unit tests passed (fail early).

With these settings we're free to add integration tests to every service by putting our tests into the source-set _/src/integrationTest/java. _To run the tests we execute:

`./gradlew integrationTest`

Due to the dependency from build to integrationTest we can also execute:

`./gradlew build`

to run compilation followed by the unit tests followed by the integration tests and finalized by building a binary.

The UserService project contains a source set "integrationTest" in which the testclass "UserServiceIntegrationTest" is located.

@RunWith(SpringRunner.class)

@SpringBootTest(webEnvironment = SpringBootTest.WebEnvironment.RANDOM_PORT)

public class UserServiceIntegrationTest

{ @Autowired

private TestRestTemplate restTemplate;

@Autowired

UserRepository userRepository;

@Test

public void shouldCreateAndReadUser() throws Exception

{ //given

final User alfred = new User("alfred", "pennyworth");

final String createUserRequest = UriComponentsBuilder

.fromUriString(UserController.CREATE_USER_PATH)

.queryParam(UserController.FIRSTNAME_PARAM, alfred.getFirstName())

.queryParam(UserController.LASTNAME_PARAM, alfred.getLastName())

.toUriString();

final String getUsersRequest = UserController.GET_USERS_BY_LAST_NAME_PATH + "/" \+ alfred.getLastName();

//when

this.restTemplate.getForObject(createUserRequest, User.class);

final User[] users = this.restTemplate.getForObject(getUsersRequest, new User[]{}.getClass());

//then

assertThat(users).hasSize(1);

assertThat(users[0]).isEqualTo(alfred);

}

@Test

public void shouldGetKnownUsers() throws Exception

{ //given

final User bruce = new User("bruce", "wayne");

final User martha = new User("martha", "wayne");

final User thomas = new User("thomas", "wayne");

final String getWaynesRequest = UserController.GET_USERS_BY_LAST_NAME_PATH + "/" \+ bruce.getLastName();

//when

final User[] users = this.restTemplate.getForObject(getWaynesRequest, new User[]{}.getClass());

//then

assertThat(users).hasSize(3);

assertThat(users).containsExactlyInAnyOrder(bruce, martha, thomas);

}

}

The test looks a lot like the server tests we already know. By having a closer look we see that the TestExecutionListener for setting up the EmbeddedCassandra is missing. Futhermore the test "shouldGetKnownUsers" checks that users can be requested without adding them beforehand. These users are the ones we just put into our newly created [testdata image](https://medium.com/p/627495b65124#9624).

Let's have a look into the UserService build.gradle

apply from: '../service.gradle'

dependencies {

compile 'com.datastax.cassandra:cassandra-driver-core:3.3.0'

compile 'io.netty:netty-all:4.1.6.Final'

compile 'org.springframework.data:spring-data-cassandra'

compile 'org.springframework.boot:spring-boot-configuration-processor'

testCompile 'org.cassandraunit:cassandra-unit-spring:3.3.0.2'

}

task bootRunDebugWithCassandra(type: org.springframework.boot.gradle.run.BootRunTask) {

group = 'Application'

doFirst() {

main = project.mainClassName

classpath = sourceSets.main.runtimeClasspath

def serviceinfos = dockerCompose.debugWithCassandra.servicesInfos

setCassandraEnv(serviceinfos, environment)

}

}

apply plugin: 'docker-compose'

dockerCompose {

debugWithCassandra {

useComposeFiles = ['docker-compose-debug.yml']

isRequiredBy(this.tasks.getByName('bootRunDebugWithCassandra'))

}

integrationTestWithCassandra {

useComposeFiles = ['docker-compose-integrationtest.yml']

isRequiredBy(this.tasks.getByName('integrationTest'))

removeContainers = true

}

}

integrationTest.doFirst {

def serviceinfos = dockerCompose.integrationTestWithCassandra.servicesInfos

setCassandraEnv(serviceinfos, environment)

}

def setCassandraEnv(serviceinfos, environment) {

def cassandrainfos = serviceinfos.cassandra

def cassandrahost = cassandrainfos.firstContainer.inspection.NetworkSettings.Networks.entrySet().iterator().next().getValue().IPAddress

def cassandraport = cassandrainfos.ports[9042]

environment.put('cassandra.host', cassandrahost + ',' + cassandrainfos.host)

environment.put('cassandra.port', cassandraport)

environment.put('cassandra.keyspace', 'test')

}

Most looks familiar so let's focus on the changes:

A dockerCompose configuration named "integrationTestWithCassandra" was added in lines 29-33\. The corresponding docker-compose file "docker-compose-integrationtest.yml" has the following content:

`version: '3'  
`services:  
cassandra:  
image: usercassandra:latest  
ports:  
\- 9042

It's basically the same as the already known docker-compose file for debugging with the small difference that the Cassandra image is the testdata image we just created.

Looking into lines 31-49 of the build.gradle file above we see that much like the debug setup the integrationTest task is bound to a dockerCompose-task which will create a cassandra-container and set up the environment for the UserService before the tests are executed.

That's all we need to create a docker-based integration-test.

## **Let's test a system**

We've seen how we can test and debug our services with third party dependencies in place. Let's have a look how to create docker images for our services and use these images for a depending services integration tests in [part 5](https://blogs.itemis.com/en/test-as-you-run-part-5-building-and-testing-systems).
