# Is it Possible to Do Outside-In TDD on the Front End?

_Captured: 2018-06-29 at 17:25 from [dzone.com](https://dzone.com/articles/is-it-possible-to-outside-in-tdd-on-front-end?edition=383278&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-06-29)_

[Learn more](https://dzone.com/go?i=250324&u=http%3A%2F%2Fblog.scalyr.com%2F2017%2F08%2Fcareerbuilder-resolves-customer-issues-5x-faster-scalyr%2F) about how CareerBuilder was able to resolve customer issues 5x faster by using Scalyr, the fastest log management tool on the market.

Traditionally, because of lack of tools or knowledge, there have not been that many good practices in front-end development. You probably just made the jQuery work and if you were lucky you used Selenium to automate the tests from a user perspective.

Which led to this:

![](https://codurance.com/assets/custom/img/blog/2018-06-17-frontend-outside-in/inverted-pyramid.jpg)

An inverted testing pyramid, which gives slow feedback (I'm looking at you, 8h test battery) alongside [many other issues](https://martinfowler.com/bliki/TestPyramid.html).

Latest frameworks (React, Vue, Angular...) are encouraging unit testing and people are embracing the power it provides. But we still have some way to go to be as mature as backend development is.

## How the Front-End Is Usually Tested

In the best case, you probably have:

  * Mounted (shallow rather) individual components to test their behavior, mocking their dependencies and not rendering their children.
  * Tested your dependencies separately: actions, reducers, services, store...

If you are doing TDD, of course, you will have done that writing every test first, right?

Well, you have done a classicist approach, which is completely fine.

But probably testing the correctness of the system is left to the e2e tests, making the top of the testing pyramid painfully big (and slow), when at that point you shouldn't be testing for accuracy.

## What We're Going to Do

Either for the sake of being able to do outside-in or to be able to leave the e2e to test browser integration and some happy paths instead of everything.

These are going to be our next steps:

  1. Create a brand new app with 1 use case
  2. Mock our APIs
  3. Mount our whole application
  4. Start testing our acceptance criteria
  5. Drive our design from that test, creating unit tests and implementing components
  6. Enjoy the robustness and speed of our tests

If you already want to see the final solution, it is in [this repository](https://github.com/nachogarcia/learning-outside-in).

### Create an App

This is our acceptance criteria:

> When I am in the home page
> 
> Then 5 random phrases from Chuck Norris will show

We have joined with our backend folks and we have come up with an API definition. This contract will go to a mock server for development purposes.

In this case, we're going to create a React app using [Create react app](https://github.com/facebook/create-react-app). Of course, this could have been any other framework (or without one), the methodology remains the same.

### Setup Tests (Mock API and Mount App)

We're going to mock our API so it returns a fixture with the example in our contract. We don't want to test the correctness of our system alongside backend: That will be done in e2e tests and it would make this tests much more fragile with almost no benefit.

If you are consuming a 3rd party and you're worried about the contract changing, make a contract test.

If the contract is owned by your team, just don't break it ;).

Since we're using [axios](https://github.com/axios/axios) for the requests, we will use it for mocking.

To mount the application we will use [Enzyme's](http://airbnb.io/enzyme/docs/api/) mount (because we want the whole app) and [one little hack](https://github.com/facebook/jest/issues/2157) to wait for promises resolution.
    
    
    axiosMocked.onGet(API_URL + '/jokes/random/5').reply(200, randomPhraseResponse)
    
    
      const app = mount(<Provider store={store}>

### Test Our Acceptance Criteria

There are discussions about what to call this kind of test: Component testing, integration testing, acceptance testing...

But here we're going to see that the hardest part was how to name them and the setup, because the test itself if this simple:
    
    
        const phraseTexts = randomPhraseResponse.value.map(phrase => phrase.joke)
    
    
        const phraseComponents = app.find('.phrase')
    
    
          const text = phraseComponents.at(index).text()

It will probably remind you of how tests are written with tools like Selenium. It is pretty standard.

### Outside-In TDD

We have created our acceptance criteria from a user perspective. Now what?

It's time for the [TDD double loop](https://codurance.com/videos/2015-05-12-outside-in-tdd-part-1/) to kick in!

![](https://codurance.com/assets/custom/img/blog/2018-06-17-frontend-outside-in/tdd-double-loop.png)

We will begin by creating unit tests for our container. For instance, let's test that it shows the phrases:
    
    
        wrapper = shallow(<App phrases={randomPhrases}/>)
    
    
        randomPhrases.forEach((phrase, index) => {
    
    
          expect(phraseComponent.prop('joke')).toEqual(phrase.joke)

These are unit tests, so we delegate the logic of showing the phrase to that `Phrase` component, which we will create empty in the beginning, and then unit test it and implement it _\- red, green, refactor. Remember?_

The same goes for the store, actions, etc.

The acceptance tests will help us remember not to forget anything, and will test the interaction between all the collaborators.

### Enjoy Our App

This is the moment to realize we have developed a whole app without even starting the browser. Of course, there will be work remaining (that CSS that we like so much, right?) but the feature itself will be pretty much done.

Our tests have been running smoothly and quickly providing us valuable feedback. If we need to, now is the moment to implement an e2e test (maybe we want to test the interaction with the backend, automated visual regression tests, or some features that are a cross-browser pain).

If you didn't before, you might want to check the final solution, it is in [this repository](https://github.com/nachogarcia/learning-outside-in).

Keep in mind that this solution is one of many to solve our needs. You can use many other frameworks like [Cypress](https://www.cypress.io/) or [Protractor](https://www.protractortest.org/) with their advantages and disadvantages.

_This article was first published on the [Codurance blog](https://codurance.com/publications/)._

**[Find out more](https://dzone.com/go?i=250325&u=http%3A%2F%2Fblog.scalyr.com%2F2014%2F05%2Fsearching-20-gbsec-systems-engineering-before-algorithms%2F) about how Scalyr built a proprietary database that does not use text indexing for their log management tool.**
