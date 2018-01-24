# Test as you run (Part 2) – Testing with Database Mocks

_Captured: 2018-01-03 at 16:26 from [blogs.itemis.com](https://blogs.itemis.com/en/test-as-you-run-part-2-testing-with-database-mocks)_

In the [previous part](https://blogs.itemis.com/en/test-as-you-run-part-1) of our series about test-driven development of microservices we created unit tests for our business logic, had a look at Server-Mock tests and ended up with a Server-Stack Test. This is the second part.

The first part can be found [here](https://blogs.itemis.com/en/test-as-you-run-part-1). Let's go on by creating a test for a service depending on a database.

Please checkout the next step:

`git checkout step3`

You will find a new sub-project, which is the UserService. Users are very simple objects with just two attributes: a firstname and a lastname.

The service allows us to store users and to request all stored users with the same lastName. We use a [Cassandra](https://cassandra.apache.org/) database to store the users. We will not talk about the actual configuration for the database, since this is very straightforward and explained in many other great [tutorials](http://www.baeldung.com/spring-data-cassandra-tutorial).

If you're curious about used configuration, take a look at the package_de.itemis.webengineering.blog.testasyourun.userservice.config.cassandra_

## Testing Every Scope

Instead, we want to focus on the testing approaches for such a setup.

At first we should take a look at the business logic,that encompasses all technology-agnostic calculations we have to do. Having a look at the UserController (which is the RestController providing the endpoints for creating a user and getting all stored users by lastName), we don't see any special business logic there. Therefore we will ignore the unit test scope for this service and directly go on to the server tests.

## Mocked Repository

The UserService uses the UserRepository, which is a [Spring abstraction for Cassandra interactions](https://docs.spring.io/spring-data/cassandra/docs/current/api/org/springframework/data/cassandra/repository/CassandraRepository.html). To verify the interactions with the UserRepository we can use a mock. The following snippet shows an example:

@RunWith(SpringRunner.class)

@WebMvcTest(UserController.class)

public class UserServiceMockedRepositoryTest

{ @Autowired

private MockMvc mockMvc;

@MockBean

UserRepository userRepositoryMock;

@Test

public void shouldSaveUserToCassandra() throws Exception

{ //given

final User catwoman = new User("selina", "kyle");

final MockHttpServletRequestBuilder createUserRequest = post(UserController.CREATE_USER_PATH)

.param(UserController.FIRSTNAME_PARAM, catwoman.getFirstName())

.param(UserController.LASTNAME_PARAM, catwoman.getLastName());

//when

this.mockMvc.perform(createUserRequest);

//then

verify(this.userRepositoryMock).save(catwoman);

}

@Test

public void shouldReadUsersByLastName() throws Exception

{ //given

final String lastName = "kyle";

final MockHttpServletRequestBuilder getKylesRequest = get(UserController.GET_USERS_BY_LAST_NAME_PATH + "/" \+ lastName);

//when

this.mockMvc.perform(getKylesRequest);

//then

verify(this.userRepositoryMock).getAllByLastName(lastName);

}

}

All we have to do, to use a mocked Repository (or any Bean) inside our service is to reference to it in the test and annotate it with the MockBean-annotation as shown in the lines 7 and 8. Instead of using the UserRepository as it is implemented, the mock object will be injected it into our production code and we can easily verify the interations with it as shown in the lines 19 and 30.

## Checking the Database Interaction

Mocking away objects used to interact with external systems is great for testing the behavior of our service. Still, it's not enough to make sure the externals are used in the intended way. We need tests checking interactions similar to the interactions we will have in production. So let's create a test that actually interacts with something that behaves like the external system which in our case is a Cassandra database.

Let's have a look at (a snippet of) the UserServiceEmbeddedTest class:

@RunWith(SpringRunner.class)

@SpringBootTest(webEnvironment = SpringBootTest.WebEnvironment.RANDOM_PORT)

@TestExecutionListeners(mergeMode = TestExecutionListeners.MergeMode.MERGE_WITH_DEFAULTS,

listeners = EmbeddedCassandraTestExecutionListener.class)

public class UserServiceEmbeddedCassandraTest

{

@Autowired private TestRestTemplate restTemplate;

@Autowired private UserRepository userRepository;

@Test

public void shouldCreateUser() throws Exception

{

//given

final User user = new User("Bruce", "Wayne");

final String request = UriComponentsBuilder.fromUriString(UserController.CREATE_USER_PATH)

.queryParam(UserController.FIRSTNAME_PARAM, user.getFirstName())

.queryParam(UserController.LASTNAME_PARAM, user.getLastName())

.toUriString();

//when

this.restTemplate.postForObject(request, null, String.class);

//then

final List<User> allUsersWithLastName = this.userRepository.getAllByLastName(user.getLastName());

assertThat(allUsersWithLastName).hasSize(1);

assertThat(allUsersWithLastName.get(0)).isEqualTo(user);

}

}

Heading to line 7 and 8, we see that the previously described TestRestTemplate is injected as well as a UserRepository.

With these injected objects we have everything in place to sent REST-calls to our Service and interact with Cassandra.

For example: We sent a REST-call to create a user (lines 15-20) and check that the user was stored inside of Cassandra (lines 22-24).

That seems nice and easy.

## Where's My Test Database?

But wait! Okay, we have everything in place to communicate with the server and with a Cassandra, but where is the Cassandra-instance? And how does the server communicate to the same Cassandra-instance as we do in the test?

To find an answer for this questions we take a look at the lines 3 and 4.

The EmbeddedCassandraTestExecutionListener is added to the TestExecutionListeners of this Test. [TestExecutionListener](https://docs.spring.io/spring/docs/current/javadoc-api/org/springframework/test/context/TestExecutionListener.html) can be used in the way the _Before, BeforeClass, After, AfterClass_ annotations known from JUnit.

Let's have a look at(a snippet of) the Listener:

public class EmbeddedCassandraTestExecutionListener extends AbstractTestExecutionListener

{

private static final String CASSANDRA_KEYSPACE = "test";

@Override

public void beforeTestClass(final TestContext testContext)

{

EmbeddedCassandraServerHelper.startEmbeddedCassandra();

System.setProperty("cassandra.host", EmbeddedCassandraServerHelper.getHost());

System.setProperty("cassandra.port", String.valueOf(EmbeddedCassandraServerHelper.getNativeTransportPort()));

System.setProperty("cassandra.keyspace", CASSANDRA_KEYSPACE);

}

@Override

public void afterTestMethod(final TestContext testContext) throws Exception

{

EmbeddedCassandraServerHelper.cleanDataEmbeddedCassandra(CASSANDRA_KEYSPACE);

}

}

The _beforeTestClass-_Method is called before any test of the test class get's executed. As we can see in line 8, that an embedded Cassandra get started, which is a lightweight Cassandra mock that can be used for tests (for more information see [CassandraUnit](https://github.com/jsevellec/cassandra-unit)). To keep our tests isolated from each other, the Cassandra get's cleared after every test (see the _afterTestMethod_-Method).

So now that we have an easy way to test our interaction with our database, we can go on to the next reasonable scope in our [next post](https://blogs.itemis.com/en/test-as-you-run-part-3-interactions-with-docker-containers).
