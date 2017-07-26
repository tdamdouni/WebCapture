# Better Unit Testing with Swift

_Captured: 2015-10-22 at 23:52 from [masilotti.com](http://masilotti.com/better-swift-unit-testing/)_

I'm a big fan of third party testing frameworks. My first foray into testing was with [Cedar](https://github.com/pivotal/cedar) and eventually [Rspec](http://rspec.info). Now that more of my work has moved to Swift I've been enjoying [Quick](https://github.com/quick/quick) and [Nimble](https://github.com/quick/nimble).

With the release of Swift 2.0 and Xcode 7 I though it was a great time to try writing my unit tests using only Apple's XCTest framework. That's right, no dependencies, no [BDD](https://en.wikipedia.org/wiki/Behavior-driven_development), and no matchers.

Here are some concepts that I've picked up over the past couple of months of "real-world" unit testing in Swift. I wish I knew these from the beginning, but hopefully they can help spark some light with seasoned Swift testers too.

## Swift Unit Testing Mindset

Before diving into details, let's highlight the general ideas when writing a Swift unit test.

  1. Everything is a protocol. Classes do not know about concrete types. 
  2. Mocks implement protocols to keep track of which functions are called with what.
  3. Static dependencies are `let` variables and injected at initialization time.
  4. Mocks are `Equatable`, enabling use of `XCTAssertEqual()` under test.

## Inject Static Dependencies

The most important of these "rules" is to inject your dependencies. Without a solid approach to DI your tests can become very difficult to write.

> To me, **dependency injection** means an object doesn't create its own instance variables. The objects are "given" to the class from somewhere else.

For example, let's look at a service layer object, `BeerService`. Its role is to retrieve data from an API and pass it along to a parser. Note that I'm assuming everything happens synchronously and cannot fail.
    
    
    class BeerService {
        let api = BeerAPI()
        let parser = BeerParser()
    
        func beer(id: UInt) -> Beer {
            let json = api.json("/beers/\(id)")
            return parser.parse(json)
        }
    }
    

How can we test that the correct path was passed to the API? There is no way to assert which objects were passed through because the service is creating the object itself. The dependency is _not_ being injected.

Well, let's inject it!
    
    
    class BeerService {
        let api: BeerAPI
    
        init(api: BeerAPI) {
            self.api = api
        }
    
        ...
    }
    

Now under test we can pass in our own `BeerAPI` instance.
    
    
    class BeerServiceTests: XCTestCase {
        func test_GettingABeer_BuildsThePath() {
            let api = BeerAPI()
            let subject = BeerService(api: api)
    
            subject.beer(42)
    
            // assert path
        }
    }
    

Great, now we can give the object under test, `subject`, any instance of `BeerAPI` that we want. It could be a "testable" subclass, a mock, or even a spied instance.

The best approach here is to make `BeerAPI` conform to a protocol, so we can inject a mock instance to run assertions on.

## Make Dependencies Protocols

Let's use a protocol to get around creating messy subclasses of concrete objects under test. In this scenario, we want `BeerAPI` to conform to something, say `API`.
    
    
    protocol API {
        func json(path: String) -> JSON
    }
    
    class BeerAPI: API {
        func json(path: String) -> JSON {
            ...
        }
    }
    

Now that the dependency is straightened out, we need to make the consumer think in terms of protocols, not concrete classes.
    
    
    class BeerService {
        let api: API
    
        init(api: API) {
            self.api = api
        }
    
        ...
    }
    

Beautiful. Now under test we create one more object to keep track of which methods get called with what. You only need to add this class to your test bundle.
    
    
    class MockAPI: API {
        var lastPath: String?
    
        func json(path: String) -> JSON {
            lastPath = path
            return JSON()
        }
    }
    

Note the instance variable, `lastPath`, which gets set upon calling `json()`. We use this property to assert that the function was called with the correct parameter.
    
    
    class BeerServiceTests: XCTestCase {
        func test_GettingABeer_BuildsThePath() {
            let api = MockAPI()
            let subject = BeerService(api: api)
    
            subject.beer(42)
    
            XCTAssertEqual(api.lastPath, "/beers/42")
        }
    }
    

To test the interaction with the `BeerParser` we follow the same path. First create a `Parser` protocol and make `BeerParser` conform to it. Then add `lastJSON` to our new `MockParser`. It may start to feel tedious having to create _three_ objects for every class. But in the long run you are given fine-grain control over how your mocks and tests work.

## Set Default Initialized Parameters

One catch with this approach is that every time you create a `BeerService` you will need to pass in the dependencies. Under test this is fine (actually, preferable) but in production code it quickly gets annoying.

To remedy this we can use Swift's [default parameter values](https://developer.apple.com/library/watchos/documentation/Swift/Conceptual/Swift_Programming_Language/Functions.html#//apple_ref/doc/uid/TP40014097-CH10-ID169) for the initializer. This means that the object knows what it needs unless it's told otherwise. Set default values for all _static_ dependencies, think anything other than a delegate or model object.
    
    
    class BeerService {
        let api: API
        let parser: Parser
    
        init(api: API = BeerAPI(), parser: Parser = BeerParser()) {
            self.api = api
            self.parser = parser
        }
    
        ...
    }
    

Now that all our classes are being injected protocols, let's move on to the actual tests. What are some best practices with writing Swift unit tests?

## Structure and Name Tests with Preconditions, the Stimulus, then Assertions

When naming tests I make sure to follow one rule.

> When I look at this test in six months I should understand what it's actually testing.

What does that mean in practice? Well let's break down the `BeerService` test example.
    
    
    class BeerServiceTests: XCTestCase { // Test Class Name
        func test_GettingABeer_BuildsThePath() { // Test Case
            let api = MockAPI()
            let subject = BeerService(api: api) // Preconditions
    
            subject.beer(42) // Stimulus
    
            XCTAssertEqual(api.lastPath, "/beers/42") // Assertion
        }
    }
    

The **Test Class Name** matches the name of the object under test. Simple.

I like to name my **Test Case** so it is obvious to see what method is being called and what the assertion is. In this example `GettingABeer` correlates to calling `beer()` on the service. I like to name these to match the behavior, not necessarily the function name. The last part introduces what the assertions are testing. Here, we want to make sure that the path that is sent to the API is correct, so `BuildsThePath`.

The **Preconditions** are where the test setup occurs. This can be injecting dependencies, initializing known values, or even other function calls. The idea is get the subject in a known state for the stimulus. I try to restrict my use of the `setUp()` method of XCTest for object instantiation.

Next, the **Stimulus** is where the actual "work" gets done. This is where you call the actual function on the object under test.

Finally, you list out your **Assertions**. By keeping these together and at the end it makes it easy to skim the tests and see what is being tested and where.

As your application's test suite grows it can becomes harder to read and understand the tests you wrote. By constraining them to a shared format and cadence you are making it easier make changes in the future.

## Make All Value Types `Equatable`

The last part of the Swift testing puzzle is making sure you can run valid assertions on your mocks and fakes.

XCTest provides a number of different assertions dealing with all sorts of primitive types. But the most valuable one, or at least the one I use most, is `XCTAssertEqual()`.

> `XCTAssertEqual(expression1, expression2)` \- causes a failure when `expression1` is not equal to `expression2`

When using this to compare Swift objects there is one minor caveat. The two instances you are comparing must conform to the `Equatable` protocol.

> [Apple](https://developer.apple.com/videos/wwdc/2015/?id=414) and [others](https://www.andrewcbancroft.com/2015/07/01/every-swift-value-type-should-be-equatable/) recommend that every Swift value type should be equatable.

Conforming to `Equatable` is easy, you just have to [implement the `==` function](http://nshipster.com/swift-comparison-protocols/#equatable) and perform the necessary equality checks. Let's use the `Beer` model from earlier as an example. Note that the function is defined _outside_ of the class and extension.
    
    
    protocol Drink {
        var name: String { get }
        var alcoholByVolume: Float { get }
    }
    
    class Beer: Drink {
        let name: String
        let alcoholByVolume: Float
    
        init(name: String, alcoholByVolume: Float) {
            self.name = name
            self.alcoholByVolume = alcoholByVolume
        }
    }
    
    extension Beer: Equatable { }
    
    func ==(lhs: Beer, rhs: Beer) -> Bool {
        return lhs.name == rhs.name && lhs.alcoholByVolume == rhs.alcoholByVolume
    }
    

Under test we can now use `XCTAssertEqual()` to ensure our mocks were called with the correct parameters.
    
    
    class BeerParserTests: XCTestCase {
        func test_ParsingValidJSON_ReturnsABeer() {
            let subject = BeerParser()
            let json = ["name": "Grimm Afterimage DIPA", "abv": 8.0]
            let expectedBeer = Beer(name: "Grimm Afterimage DIPA", 
                alcoholByVolume: 8)
    
            let actualBeer = subject.parse(json)
    
            XCTAssertEqual(actualBeer, expectedBeer)
        }
    }
    

Oh, and if you ever see [anything from Grimm ](https://www.beermenus.com/breweries/6406-grimm-artisanal-ales) I highly suggest buying it immediately.

## Recap: _IDEPEM_!

To help remember the Swift Unit Testing Mindset, just think _IDEPEM_.

  * **I**nject
  * **D**ependencies,
  * **E**verthing's a
  * **P**rotocol,
  * **E**quatable
  * **M**ocks

Remember, you use the Xcode **IDE** and [generate .**PEM** files](https://www.beermenus.com/breweries/6406-grimm-artisanal-ales) for push notifications!

## Bonus: Custom XCTest Helpers

An easy way to maintain quality in your test suite is to share assertions between tests. This can be accomplished by extracting helper methods to run common assertions.

Learn how to [extract common test behavior into helper methods](http://masilotti.com/xctest-helpers) while keeping those pesky failure messages on the right line.

If you liked this post, you can [ share it with your followers](https://twitter.com/intent/tweet?url=http://masilotti.com/better-swift-unit-testing&text=Better Unit Testing with Swift&via=joemasilotti) or [ follow me on Twitter](https://twitter.com/joemasilotti). 
