# Unit Testing Patterns to Follow

_Captured: 2017-02-24 at 23:43 from [dzone.com](https://dzone.com/articles/unit-testing-patterns-common-patterns-to-follow-fo?edition=271920&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-24)_

### In this article we take a look at how several different types of application testing patterns, so you can decided which would work best for you team.

Download this free eBook to [learn how to implement an effective ChatOps workflow](https://dzone.com/go?i=141027&u=https%3A%2F%2Fraygun.com%2Fdzone-chatops%3Futm_source%3DDzone%26utm_medium%3DBanner%26utm_term%3DJavascript%26utm_content%3DEbook%26utm_campaign%3DDzone_ChatOps) to make issue management and resolution easy within software development teams, brought to you in partnership with [Raygun](https://dzone.com/go?i=141027&u=https%3A%2F%2Fraygun.com%2Fdzone-chatops%3Futm_source%3DDzone%26utm_medium%3DBanner%26utm_term%3DJavascript%26utm_content%3DEbook%26utm_campaign%3DDzone_ChatOps).

Not long ago I wrote about the anatomy of a unit test along with helpful guidelines and test-double concepts. Today, I'm going to walk you through the common unit testing patterns that I follow.

The five core unit testing patterns I use are:

  * Result test pattern
  * State test pattern
  * Fluent builder test pattern
  * Database test pattern
  * Fluent database builder test pattern
  * Integration test pattern

Different uniting test patterns will be applicable to different scenarios, so I've highlighted when it's best to use each one.

### Result Test Pattern

To start off, let's take a look at a very simple unit test:

Whether or not you've ever written a unit test before, you can probably get what's going on here. I take the value 0, pass it into the Increment method, and then assert that the result is incremented to 1.

### State Test Pattern

Here's another simple unit test to warm up with.
    
    
      Vector2 vector = new Vector2(5,6); // Arrange
    
    
      Assert.AreEqual(1, vector.Length); // Assert

Although I've listed these first two unit testing patterns under different headings, they are both very similar and equally simple. You set up some kind of input, call a method, and assert the expected result.

The **input** may be a primitive value, an object with a specific state, or sometimes nothing at all.

The **value** you assert could be the return value of the method, an out parameter, or the state of the original object acquired through calling a property or method. All of these scenarios fall into the result/state test patterns. In [cleanly structured code,](https://raygun.com/blog/2014/10/5-interesting-data-structures-algorithms/?utm_source=dzone&utm_medium=article&utm_term=unit_testing_patterns) all if not most unit tests will be this simple to write.

In general, you write many unit tests for each method you are testing in order to cover all code paths and to assert that various inputs produce the expected result. You don't, and usually, can't, test all possible inputs, but instead will want to test a variety of types of inputs such as negative, positive, and zero numbers, large and small values and so on.

[Unit testing frameworks](https://dzone.com/articles/unit-testing-frameworks-in-c-comparing-xunit-nunit) can also provide a way for you to test multiple inputs through a single unit test by providing the inputs in a test method attribute.

### Fluent Builder Test Pattern

The fluent builder pattern isn't specifically used for unit tests but can come in handy during the arrange step as I'll explain. A builder class is made up of two main things:

  1. Several clearly named Set methods, each responsible for setting a single piece of state of the resulting object. Each of these methods returns the builder itself so that you can chain all the method calls together.
  2. A Build method which uses the previously set state to build and return the object:

Here's an example of using the above builder by chaining the methods to build a Person object:

Outside of unit testing, the most common reason I've seen for using the builder pattern is to replace constructors with long parameter lists, especially when a lot of the parameters have the same type. By looking at the invocation of such constructors, it's not always clear what each parameter is for.

[In C# at least,](https://raygun.com/blog/2014/02/c-sharp-performance-tips-tricks/) you don't need to specify the name of each parameter, and so you may need to look into the constructor definition to find out what each parameter really is. In the simplified example above, though, using a builder is very clear to read since setting each piece of the object state is spelled out for you. So this is great for unit tests because we always want them to be clear to read.

If arranging the state for several unit tests is a bit messy or complicated, then have a go at using the fluent builder pattern. The state under test becomes very clear to read. In some cases, using the fluent builder pattern in unit tests can help to prevent code duplication, because a single method on the builder could encapsulate a lot of state-setup code that can be written once and used by many tests.

This state-setup code is hidden away behind methods with clear names, which is all you need to know when reading a unit test to understand what is being tested.

You are not limited to using Set methods on the builder, and the Build method is not limited to only calling a constructor. Arranging the state of the object may also involve calling methods that add objects to child collections, or void-parameterless methods that update the objects state in some way. If the project you are testing already provides a fluent builder, you might be able to use that, otherwise, add one to the unit test project.

### Database Test Pattern

There are quite a few ways of tackling tests for units dealing with databases. Some of which are frowned upon, though, such as pointing directly to the production database. I would not recommend you do that.

#### **Using an ORM**

The easiest way of testing with databases is made possible if the unit your are testing uses an ORM. LightSpeed, for example, provides an IUnitOfWork that connects to a database and provides collections of objects that you work with directly using C#. Each collection is like a table, and each object is a record.

The objects contain properties that map to columns in the table. By simply faking or mocking the IUnitOfWork, you can completely remove the need to connect to an actual database while running the unit tests. You can then set up the fake/mock to return specific sets of objects as needed for the unit tests. When running the unit tests, the unit will fetch those objects and function in the same way as though it was interacting with a database. Like any unit test, you can assert that results returned from the function you're testing is expected, or verify that certain methods are called on the unit of work - depending on if you prefer state vs. implementation testing.

#### **Find a Database Mocking Framework**

If your project doesn't use an ORM, or at least nothing that provides an interface to fake/mock, then another option could be to use a database mocking framework. These are frameworks that aid in mocking databases, so that again you can test queries without actually connecting to a database. I haven't used any myself, nor looked too much into how well this approach works so I can't comment further, but I wanted to point it out if you're interested in exploring this path.

#### **Create a Testing Database**

The main remaining option is to resort to setting up and connecting to a test database. Please note that despite the name of this blog post, we are now delving into 'integration testing' territory - because instead of testing a single unit by itself, we are testing the function of a unit while it is connected to an external technology. I personally find that this is a good path to take, especially when raw database queries are involved.

To test the function of a unit, setup a database full of all the test data you'll need before running any tests. Once this is done, the tests will:

  * Create the unit under test.
  * Tell it to use the test database.
  * Call methods on the units.

#### **Only Add Data to the Database When the Tests Need It**

Keeping all the possible testing data in a single test database is going to stack up quite a bit over time. If you need to debug why a test has started to fail because of a recent change, you'd need to sift through all the data and follow the indices to understand the state under test.

When writing new tests, you'd have the same problem sifting through the data to see if the state that you want to test exists, or otherwise, you need to add more data. An alternative then is to set up just the data you need on a per-test basis. Or better yet, set up data that you need to support several tests within the test fixture setup method. The database itself can still be set up once before all tests and could contain common data.

By wrapping up the per-test or per-fixture data in a transaction, you can then roll it back when no longer needed. Overall, this means the state under test is more clearly outlined within the appropriate context, but the downside, of course, is that with more database interaction, the testing process will be slower compared to setting up the database once it's full of all testing data.

  

    
    
    [TestFixture]
    
    
    public class Execute_SingleSession
    
    
    {
    
    
      private LightSpeedContext _context;
    
    
      private IDataNodeModelUnitOfWork _unitOfWork;
    
    
      private IDbTransaction _dbTransation;
    
    
      private readonly ISessionForErrorInstanceQuery _query = new SessionForErrorInstanceQuery();
    
    
      [TestFixtureSetUp]
    
    
      public override void TestFixtureSetUp()
    
    
      {
    
    
        _context = new LightSpeedContext("LightSpeedContext");
    
    
        _unitOfWork = _context.CreateUnitOfWork();
    
    
        _dbTransation = _unitOfWork.BeginTransaction();
    
    
        var cmd = new NpgsqlCommand(
    
    
    @"INSERT INTO session VALUES(1, 1, '1', 1, 1, 1, 'US', '127.0.0.1', '2015-01-01 00:00:00.000000', '2015-01-01 00:10:00.000000', '2015-01-01 00:10:00.000000');
    
    
      INSERT INTO ""user"" VALUES(1, 1, 'jason@raygun.com', 'Jason', null, 'jason@raygun.com', '2015-01-01 00:00:00.000000', '2015-01-01 00:10:00.000000', FALSE, 'Raygun');");
    
    
        UnitOfWork.PrepareCommand(cmd);
    
    
        cmd.ExecuteReader();
    
    
      }
    
    
      [Test]
    
    
      public void SessionIdIsCorrect()
    
    
      {
    
    
        var sessionForCrash = _query.Execute(_unitOfWork, 1, "jason@raygun.com", new DateTime(2015, 1, 1, 0, 7, 0), true);
    
    
        Assert.AreEqual(1, sessionForCrash.SessionId);
    
    
      }
    
    
      [TestFixtureTearDown]
    
    
      public void FixtureTearDown()
    
    
      {
    
    
        _dbTransation.Rollback();
    
    
        _dbTransation.Dispose();
    
    
        _unitOfWork.Dispose();
    
    
      }
    
    
    }

###   
Fluent Database Builder Test Pattern

If you're fine with the database integration testing technique explained above, here's a way to take it further. Say you have already pinpointed an issue. What happens when a new column is added to a table that doesn't have a default value?

Well, now we need to go through all the tests and update the queries that add the testing data:
    
    
        return String.Format("INSERT INTO session VALUES({0}, 1, '1', 1, 1, 1, '{1}', '127.0.0.1', '{2}', '{3}', '{3}');", _id, _country, _start, _end);

After preparing all the individual strings from the various builders, append them together and run them as a single query. The result of this implementation is that the query for each type of record now only exists in one place. If a database change occurs, fixing thousands of unit tests should only require changing a few lines. Another perk we get out of this implementation is clear state setup code. We can now clearly see what each value represents because it's written out in the builder methods. The query string has a list of various numeric, string, and date time values whose purpose and ordering would need to be looked up in the database schema.

### Integration Test Pattern

A lot of software integrates with various external technologies and services. [Redis](https://redis.io/) and [RabbitMQ](https://www.rabbitmq.com/) are a couple of examples of such technologies. Slack, GitHub, and Facebook are examples of third party services. You may even have your own separate systems that integrate together. When testing your software, you may want to assert that messages are being published to a Rabbit exchange/queue under certain circumstances, or that the response from a service is interpreted and acted upon correctly.

One way to do this would be to spin up an instance of RabbitMQ on the test server to which you can connect, or create test accounts in third party services to integrate with. What we'd be doing is testing that multiple systems work together correctly. This testing scheme is called integration testing.

However, we still want to be able to test units of code by themselves as much as possible.

#### **Connecting to External Systems Directly Within Your Business Classes Makes Them Difficult to Unit Test**

Say we have a class in the code we want to test that publishes messages to a Rabbit queue. This class could create an instance of ConnectionFactory directly within it and use this to get a Channel to publish messages on. Outside of this class, such as in a unit test, the only control we're likely to have is specifying a RabbitMQ host name.

![unit testing patterns using RabbitMQ](https://raygun.com/blog/wp-content/uploads/2017/02/Processor-1-1.png)

> _Image showing the processor and Rabbit MQ_

Using this class in a unit test is going to cause it to try and connect to a real RabbitMQ host, which as mentioned above is what we want to avoid when writing unit tests. We need to remove the need for running RabbitMQ from the equation, and making this possible generally comes down to the use of interfaces in the software you are testing.

#### **Use Interfaces to Separate External System Implementations from Your Business Logic**

Using the same example above, let's say the class we are testing instead takes an IConnectionFactory into the constructor. The class then uses this to get an IChannel and publish messages into it.

![Using a processor this way is much easier when designing unit testing patterns](https://raygun.com/blog/wp-content/uploads/2017/02/Processor-2.png)

In the running software, an actual ConnectionFactory instance will be created and passed into the constructor either explicitly or through dependency injection.

![](https://raygun.com/blog/wp-content/uploads/2017/02/Processor-3.png)

In the unit tests, rather than using a ConnectionFactory provided by the RabbitMQ library, we'll pass in either a fake or a mock of IConnectionFactory and any surrounding classes we need. I covered fakes and mocks in the [previous post](https://raygun.com/blog/2016/09/unit-testing-examples-and-anatomy/), but here is a quick recap:

**A fake** is our own implementation that functions just enough for the unit tests to work. Rather than connecting to a RabbitMQ host, though, we can have an in-memory queue to store published messages and then assert that the message exists.

**A mock** is an object that we can setup with hard-coded responses to various method calls. We can use this to verify that the BasicPublish method on an IChannel was called appropriately.

![](https://raygun.com/blog/wp-content/uploads/2017/02/Processor-4.png)

By using an interface in the constructor, we're able to separate the specifics of using RabbitMQ from the surrounding logic within the unit. Now we can focus on testing just that logic such as processing the inputs that result in correct messages being posted to the appropriate queues - all without RabbitMQ actually being involved.

#### **Create an Interface if One Doesn't Exist**

Sometimes, you may come across third party tech/service integration frameworks that don't provide interfaces for the classes that communicate with the external software. To help with unit testing your classes that use such integrations, you can create your own interface so that you can follow the pattern outlined above. You can add whatever methods you want to this interface based on the ways that you will be communicating with the external software. Then, implement this interface, using whatever the integration framework provides.

This implementation should be as minimal as possible. It will only be used as a means to communicate with the external software, and will not contain any of your business logic such as whether or not messages should be sent, or acting upon messages received. We will not be writing unit tests for this class because it will require a connection to the real external software, so integration tests would be more suitable. We created this class due to the need for an interface to fill in what the framework did not provide for us. With this interface, we can now use it in the constructor of the class that will contain the business logic around the integration. Use the unit testing pattern above to test this business logic.

#### **Refactor Code to Make this Unit Testing Pattern Possible**

If you come across a class in your codebase that you need to test which is somewhat hard-coded to interact directly with external software, have a go at refactoring it to pass an interface into the constructor. While describing this pattern, I've been talking about integrations with external software, but this pattern can be applied to classes within the same system too. Any interfaces passed into a unit you're testing is best to fake or mock. If a class is creating instances of other classes internally that have various responsibilities such as memory management or processing, you could refactor those out to pass interfaces of those responsibilities into the constructor. This allows you to test the logic of just this one unit, and also means the class isn't coupled to a single implementation of those responsibilities.

Just because we've been doing this work to make unit testing these classes easier, doesn't mean integration tests are out the door. The unit tests are great for testing that our business logic interacts correctly with an external integration, as long as it's functioning in an expected way from the perspective of our business logic class. Our fakes or mocks are setup to respond to and return results that we know it should. Integration tests are still valuable to test that since after updating them, they still accept and return messages that our software expects.

## Go Forth and Write Unit Tests

I hope that all these unit testing patterns and scenarios made sense and were easy to follow - just like unit tests should be.

When it comes to error resolution, the more unit tests you have, the more exceptions you may become aware of before releasing software. If you use a [software intelligence platform like Raygun](https://raygun.com/?utm_source=d_zone&utm_medium=article&utm_term=unit_testing_patterns) which helps you find and resolve an exception, you could then add unit tests if necessary to assert the fix that you made.

If you have any feedback on any of these unit testing patterns or have any other unit testing patterns that you follow, we'd love to hear from you in the comments below.

Download this free eBook to [learn how to build robust JavaScript applications](https://dzone.com/go?i=141026&u=https%3A%2F%2Fraygun.com%2Fdzone-javascript-error-monitoring%3Futm_source%3DDzone%26utm_medium%3DEbook%26utm_campaign%3DJavascript) and ensure effective error monitoring is in place, brought to you in partnership with [Raygun](https://dzone.com/go?i=141026&u=https%3A%2F%2Fraygun.com%2Fdzone-javascript-error-monitoring%3Futm_source%3DDzone%26utm_medium%3DEbook%26utm_campaign%3DJavascript).
