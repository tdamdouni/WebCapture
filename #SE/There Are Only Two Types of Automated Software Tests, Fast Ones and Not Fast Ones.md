# There Are Only Two Types of Automated Software Tests, Fast Ones and Not Fast Ones

_Captured: 2016-03-22 at 23:28 from [medium.com](https://medium.com/@geshan/there-are-only-two-types-of-automated-software-tests-fast-ones-and-not-fast-ones-70ab3b42d83d)_

![](https://cdn-images-1.medium.com/max/2000/1*0_V4duNxSvdmytqPR9Rmhg.jpeg)

Tests check that the code does what it is expected to do. It also gives confidence to the software engineer that the code works as intended. This equates to less or no bugs in the software. You must have heard about lots of types of automated software tests. There is unit testing, integration testing, functional testing, acceptance testing, smoke testing etc. As per Guru99's [post](http://www.guru99.com/types-of-software-testing.html) there are more than 100 types of software testing. In this post I am going to categorize automated software tests into two, the fast ones and not fast ones.

![](https://cdn-images-1.medium.com/max/800/1*w101yq12wfyUevObORbC2w.jpeg)

### How do you distinguish between slow and fast tests?

Generally, if your whole tests suite runs in seconds it is fast. If your whole test suite runs in minutes/hour it is slow. To make your tests small you need to make your application small. As faster tests running on your Continuous Integration (CI) service will give you faster feedback. May be it is time to go micro-services?

Lets discuss the more about fast and not fast (slow) automated software tests.

### The fast tests

Fast tests are code that test one unit of code generally a method. Unit test is a type of fast test. They don't depend on any external dependencies. External dependencies include file system, database, web server, network or any third party API or service. Unit tests even mock the other code elements they need like other classes and its methods. This makes the test focused on one unit and they run in milliseconds/seconds not minutes. A simple example is below:

<?php

namespace DataProvider\Example\Test;

use DataProvider\Example\Checkout;

use PHPUnit_Framework_TestCase;

/**

* Checkout test for Cash and Credit card.

*/

class CheckoutTest extends PHPUnit_Framework_TestCase

{

/**

* @var Checkout

*/

protected $checkout;

public function setup()

{

$this->checkout = new Checkout();

}

/**

* Data provider for testCalculateTotal

* variables are in the order of

* $paymentMethod, $expectedTotal.

* 

* @return type

*/

public function paymentMethodProvider()

{

return [

['Cash', 100.00],

['Credit Card', 95.00],

];

}

/**

* Test to check if the order total is calculated correctly

* for given payment method.

* 

* @param string $paymentMethod

* @param float $expectedTotal

* 

* @dataProvider paymentMethodProvider

*/

public function testCalculateTotal($paymentMethod, $expectedTotal)

{

$this->checkout->calculateTotal($paymentMethod);

$this->assertEquals(

$this->checkout->getTotal(),

$expectedTotal,

sprintf('Testing total calculation for %s.', $paymentMethod)

);

}

}

You can view the full code [here](http://github.com/geshan/dataprovider-example), yes it is a simple class with no code or external dependency.

Some integration tests can also be fast tests. These integration tests can test many classes. They should not dependent on any external dependencies mentioned above to obtain speed. So these tests will still run in seconds and not take minutes to finish.

### The not fast tests (slow ones)

Any test that takes long to run are not fast tests (slow tests). Generally, these type of tests need to load the whole application to test it. These types of tests depend on external dependencies. External dependencies include file system, database, web server, network, third party API or service.

Acceptance tests that need to load a full web application on a browser is a type of slow tests. Even smoke tests if it needs to load the whole application and takes long time to execute fall in this category.

@checkout

Feature: Checkout with offline payment

In order to pay with cash or by external means

As a Customer

I want to be able to complete checkout process without paying

Background:

Given the store operates on a single channel in "France"

And the store has a product "PHP T-Shirt" priced at "$19.99"

And the store ships everywhere for free

And the store allows paying offline

@ui

Scenario: Successfully placing an order

Given I am logged in customer

And I have product "PHP T-Shirt" in the cart

When I proceed selecting "Offline" payment method

And I confirm my order

Then I should see the thank you page

The above example is taken from [Sylius](https://github.com/Sylius/Sylius/blob/master/features/checkout/checkout_with_offline_payment.feature) project, to test checkout with offline payment method on the browser.

### Conclusion

Testing is super important for a robust software application. Automated testing + CI is one of the [four pillars](http://geshan.com.np/blog/2015/10/4-pillars-of-a-solid-software-application-and-tools-to-support-it/) of any solid software application. Happy testing hope your tests run in seconds not minutes.
