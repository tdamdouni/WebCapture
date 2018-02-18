# Why You Should Stop Testing Every Class NOW

_Captured: 2018-02-14 at 14:08 from [dzone.com](https://dzone.com/articles/why-you-should-stop-now-testing-every-class?edition=361103&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-02-14)_

Nowadays, testing is an inseparable part of every developer's job. It is not only companies who understand the importance of testing; we developers finally understand that testing our code makes our lives easier. At least it is supposed to, in theory...

## What Is the Product?

We all can agree that the product is the running software in production which provides certain services or value for the users or customers. Although that is true, there could be yet another view of seeing the product from a testing perspective.

Let's suppose that for every possible use case in production, we have tests defining precisely how the product behaves and how the product is not supposed to behave. The tests create a list of rules which precisely draw how our software should behave and flag as soon as possible when at least one of the rules is violated.

Now let's suppose we hire a brand new team and give them only these great tests and ask them to write software which passes all those tests. The team can choose every technology it likes as long as the tests are green.

Finally, the team passes all the tests and we deliver this brand new software to production. Did the customer notice any difference? Not even one! From their perspective, this software is still doing the same things and is offering same services. So one can argue now, what really is the product? It's the software which is replaceable at any time or the tests or set of rules describing how the software behaves?

Basically, as long as tests describe what our software is doing, we can be independent of the implementation, which brings us to next topic: the root of the problem

## Test What, Not How

Although this may sound easy-peasy, it is actually the root of the problem with most of the tests we write. Why? Because most of the time even without noticing it we end up testing **implementation details **rather than the **behavior** of our software/module/class.

Sofware implementation details are always in a state of constant change because of refactoring, technology upgrades, bug fixing, and several other improvements and optimizations. When our tests are checking implementation details , suddenly we have a massive red color all over our IDE although no functional or requirement change was done. Even simple refactoring - like changing types not in an interface, or moving code around - will make a lot of tests to fail, making us waste a lot of time fixing, not counting the frustration of looking at something like `shouldCreateFieldOneWithValueTwoWhenSomeOtherFieldIsTrueAndIsSomeKindOfObejctType` .

Instead of coupling tests with implementation details, we could test our code like a **black box.** We do not care what is inside, but are rather interested in fully describing the behavior (what the outputs will be for certain inputs).

Most of the time, I found that I was actually testing _how_ the code was doing certain things rather than _what_ it was doing. There may be a lot of reasoning behind that, but from my personal experience I was doing this because I misunderstood TDD a bit, and therefore blindly followed the rule: "Test every CLASS and every public method inside."

Although, in theory, avoiding testing implementation details may make sense, from a practical point of view, there are two more questions:

  * How can I detect implementation details vs. behavior?

  * How am I going to detect my self-violating the holy rule?

### Example

Although the [current example code](https://github.com/klevis/testRightByExample) is not real, it is inspired by many like it. Let's suppose we have a very simple existing back-end application which registers people into a database. For simplicity, let's momentarily remove the Controller layer, or REST part of our application, so we have only Service, Data Access Objects (DAOs), JPA+DB.

If we look at our existing **[PersonService](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/PersonService.java) **class, it is fairly simple:

It has two public methods: **savePerson **and** updatePerson.**

  * **SavePerson**: before saving a person, it validates whether all the person's required fields are correctly filled, then converts the **[Person ](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/model/Person.java)**object into a database object **[PersonDbo ](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/entity/PersonDbo.java)**and finally calls **[PersonDAO** ](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/repository/IPersonDao.java)to save **[PersonDbo ](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/entity/PersonDbo.java)**into the database (more details in the [code](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/PersonService.java)).
  * **UpdatePerson**: before updating a person, it checks if this person already exists, then similarly converts the **[Person ](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/model/Person.java)**object to a database object **[PersonDbo](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/entity/PersonDbo.java) **and finally calls **[PersonDAO** ](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/repository/IPersonDao.java)to update **[PersonDbo ](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/entity/PersonDbo.java)**in the database (more details in the [code](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/PersonService.java)).

Now we have only one existing test for this service: **_[TestPersonService](https://github.com/klevis/testRightByExample/blob/master/src/main/test/ramo/klevis/testing/TestPersonService.java) _**as below **with 100% coverage**:

As we can see, this test describes precisely how our PersonService should behave. So far, so good - we are testing all business logic classes except [Person ](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/model/Person.java)and [PersonDBO](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/entity/PersonDbo.java) because they are just beans, and [PersonDAO, ](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/repository/IPersonDao.java)which, because of the DB, is usually tested with integration tests.

### Change 1

Everything looks fine until one day a requirement change was needed for our service. The change was as simple as to add the possibility to save addresses for each person. So basically, now our **[Person ](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/model/Person.java)can have many [Addresses](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/model/Address.java). **So we change our [Person ](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/model/Person.java)and [PersonDbo ](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/entity/PersonDbo.java)to have, respectively, [Address ](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/model/Address.java)and [AdressDbo](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/entity/AddressDbo.java).

Basically, we follow TDD in here and added a failing test first:

Indeed, the test fails, because right now, [PersonService ](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/PersonService.java)is not able to save addresses.

Continuing with TDD, we have to make our [test ](https://github.com/klevis/testRightByExample/blob/master/src/main/test/ramo/klevis/testing/change1/TestPersonServiceChange1.java)pass as soon as possible without thinking about design or anything else, because it is easy and more efficient to do one thing at one time. Additionally, since at this point, we do not have a solution yet, it may not be clear what design is better suited. [PersonService](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/PersonService.java) was changed to [PersonServiceChange1](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/change1/PersonServiceChange1.java) to pass the test (in practice, there will be no PersonServiceChange1, but for tracking purposes, we create the change in a different class). The change only consists of saving the address, as well mostly convert methods.

We made our test green following TDD, and now it is time for us to refactor and improve our code. The first thing to notice is that [PersonService](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/PersonService.java) is becoming bigger, from 90 lines to 130 ([PersonServiceChange1](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/change1/PersonServiceChange1.java)), and it is clear that it will not scale when new entities like Address need to be added to Person. Also, it is easy to notice that [PersonServiceChange1](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/change1/PersonServiceChange1.java) is not following the Single Responsibility Principle, as it is doing more than one thing, like converting Model objects to Database Objects and validating... So, we decide to separate converters into two different classes: [PersonConverter ](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/change1/PersonConverter.java)and [AddressConverter](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/change1/AddressConverter.java) and change [PersonServiceChange1](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/change1/PersonServiceChange1.java) accordingly. After this change, we make sure the [tests ](https://github.com/klevis/testRightByExample/blob/master/src/main/test/ramo/klevis/testing/change1/TestPersonServiceChangeAfterRefactor1.java)are green, and indeed, they are.

Now we think that since two classes were created [(PersonConverter ](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/change1/PersonConverter.java)and [AddressConverter](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/change1/AddressConverter.java)), it will be great to cover those with JUnit tests as well. After all, the more coverage the better, and we need to make sure those classes work as expected. So we create [TestPersonConverter ](https://github.com/klevis/testRightByExample/blob/master/src/main/test/ramo/klevis/testing/change1/TestPersonConverter.java)and [TestAddressConverter](https://github.com/klevis/testRightByExample/blob/master/src/main/test/ramo/klevis/testing/change1/TestAddressConverter.java) and happily go home.

The last step is the evil one, and it doesn't really follow TDD. At this step, we did not change the behavior, just improved/refactored **Implementation Details**, and TDD says nothing about adding new tests after the refactor step, but instead, simply says that we need those existing tests green after refactoring**.** So what we basically did there is to test the **Implementation Details **and couple our tests with those details. Also, notice that there is no code coverage increase after adding those tests.

You may think, "So what? I don't see how that could hurt; I just added a few more tests."

Let's see...maybe you'll change your mind.

### Change 2

This time, a million dollar bug was found: a _NullPointerException. _Below is the test which fails instead of handling a known exception like _PersonRequiredFieldsMissingException_:

Again, we follow the TDD rules and change the code in_ [PersonServiceChange2](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/change2/PersonServiceChange2.java) _to this code:

This changes so it additionally checks if_ Person is not null_ like below:

Now the tests are all passing, but since we are good developers and in a good mood today, we decide to follow the rule "Leave it cleaner than you found it." In order to avoid _NullPointer_ in the future, we decide to introduce new Java 8 Optional at our Converters because of the code below:

Clearly, we see that it is not transparent that this method may return **_Null_**, so we think since this is not a public API and it is just a refactor and we are not changing any behavior, it will be great and safe to change it. After all, instead of **NULL**, it will return **Optional** and we need to change only a few places the service is called. So, we decide to do just that change to [PersonConverter ,](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/change2/PersonConverterChangeRefactor2.java)[AddressConverter](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/change2/AddressConverterChangeRefactor2.java) and [PersonServiceRefactorChange2](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/change2/PersonServiceRefactorChange2.java).

After this change, [TestPersonServiceRefactorChange2 ](https://github.com/klevis/testRightByExample/blob/master/src/main/test/ramo/klevis/testing/change2/TestPersonServiceRefactorChange2.java)is passing, but we see that [PersonConverter ](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/change2/PersonConverterChangeRefactor2.java)and [AddressConverter](https://github.com/klevis/testRightByExample/blob/master/src/main/java/ramo/klevis/testing/change2/AddressConverterChangeRefactor2.java) are failing badly... They are failing in compile time (tests do not expect optional) and also in Runtime (optional has `.get()` instead of value). We have two test classes and 6 methods in total to fix, and we did not change anything functional, just a refactor! Remember, those two tests and two classes were created after the last clean/refactor step of TDD, which says nothing about adding a new test for classes created during the last step.

Since we were testing **Implementation Details **and these details changed after the refactor, we have those tests failing. Here we have only two entities and therefore only two tests, but it's not hard to imagine a case when we have 20 entities (even more in practice) like Address and Person, Photos, Buying History, Friends... In that case, the situation will be even messier (20 tests and 120 methods to fix) and maybe that "good developer" will back up from his mission to "Leave it Cleaner than he found it."

We saw that the tests, instead of priming improvement (because of the safety they're supposed to provide) actually become an obstacle for improvement and a pain to maintain without even offering more quality (these tests did not cover additional code; it was already covered). If we skipped those tests, then the change would be so easy and the quality still the same, since converters classes behavior was already covered by the PersonService tests.

## Rule Are Made to Be Broken

If there is a rule out there, it is "There is no absolute rule." So basically, applying one rule to everything is absolutely wrong:

  * Sometimes, the application is not that simple to understand and we feel the need to test its internals to understand how it works or behaves. In this way, we know how to use those internals, or maybe even extend them. In this case, it is totally fine to add tests to explore those paths. But after we fix the problem, we need to delete those tests. Wait a minute - not so fast! Maybe someone else needs those? Can we just save someone else frustration? Well, yes, but again, we need to mark those tests as optional and clearly state that anyone can delete them if they become an obstacle to improvement or important refactoring. Maybe you can document your experience and API usage instead of leaving the tests.
  * There is especially a case when we need to test _how_. For example, this is the case with **Cache**. We really need to test if the code is getting it from the cache instead, of let's say, the DB or HTTP. I would agree with such tests, but anyway, we all know that is better to switch to a built-in solution like JPA since someone else is testing those things and the cache is well one of the most difficult problems to solve, especially on your own.
  * There are also other cases when, during refactoring, we produce a lot of classes and feel the need to test them. I generally agree with testing a part of them, especially if we created a potentially public interface, but otherwise, I will skip them with no worries since they are covered anyway. Changing a requirement will flag the parent class tests to fail (since it is calling those internals anyway).

## Conclusion

  1. Test **"what," **not** "how." **Do not test **implementation details.**
  2. Do not add new tests; after the **TDD **refactor step, they are already covered.
  3. Feel free to break the rules with care when really needed.
