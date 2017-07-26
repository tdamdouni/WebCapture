# Should I Test at the GUI Level or the API Level?

_Captured: 2017-02-20 at 10:25 from [dzone.com](https://dzone.com/articles/should-i-test-at-the-gui-level-or-the-api-level?oid=twitter&utm_content=buffera451a&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

![](http://eviltester.com/images/blog/automating/where_to_test_levels_360x349.png)

**Question:** Is there a rule of thumb when deciding to test at the GUI level or API level? Are any rules to help decide when to test at one level over the other?

**Answer: **I don't think I use a simple rule of thumb -- but I will try and explore some of the thought processes I use to make the decision.

When I am trying to decide whether to test at the GUI or the API level, I have to figure out:

  * What am I trying to test?
  * Can I isolate the functionality I'm testing to a specific level?

I think the word "isolate" might be the "rule of thumb" you are looking for.

  * Test heavily where you can isolate.

  * Test the integration heavily for the isolated unique integration functionality.

  * Test the integration as heavily as the implementation requires.

  * Test the integration for emergent behavior.

  * Test the overlap between systems, during integration, more lightly.

For example, if the system has "Create user" functionality:

  * Exposed through the GUI via an admin interface.
  * Exposed via an API REST call.

I need to test at both levels because the functionality of 'create user' is not isolated to one level.

The questions I have to ask though are 'how much' and 'what' do I have to test at each level? I may decide not to test as much through the GUI if my GUI calls the REST API because I can model that as (at least) two communicating systems. A GUI system and an API system.

I can heavily test the parts of functionality that are isolated in the API at theAPI level, and then lightly test the overlap of the integration between the GUI and the API. And I want to test the unique functionality in the GUI. e.g. the GUI may have ajax calls triggered from GUI interaction -- I want to test that at the GUI level.

Depending on the development process we may find that the 'ajax' calls have already been covered by JavaScript unit tests. But they haven't been integrated into the browser page, or from all the browsers and operating systems the GUI is used in. Therefore, depending on the libraries used, I may want to test that cross browser and on different operating systems.

If the GUI calls a different backend endpoint than the API, then I need to test both routes through to the backend code until I get to the point in the backend system where I encounter shared code -- assuming there is shared code in the system used by both the REST API and the GUI triggered backend flow.

But at this point, I also need to consider how much coverage we have from unit tests which cover the shared code.

I guess my rule of thumb might look like a list:

  * Build a model of the system such that you can identify the integration points and the 'isolated' shared functionality.
  * Test isolated functionality at the lowest points you can.
  * Work back out to higher (or peer) levels of integration and abstraction and consider the system in terms of integrating systems.
  * Look for unique functionality at the higher (or peer) levels of abstraction, you will need to test them there.
  * If you exercise unique functionality in isolation by mocking out the integrating systems, then you might need to look at this from a technical risk perspective and decide if, or how much, you need to exercise it while integrated.

I could also model the above as:

  * Create multiple overlapping models of the system.
  * Consider coverage of the multiple models of the system.
  * Consider coverage of flows through the different models of the system.
  * Consideration of technical risk relating to the implementation and the environments the system runs on.

P.S. When I explain this, people often map this on to their favorite pyramid model. I don't use any pyramid models. I prefer to model the system that I'm working with, rather than have a general model. Other people prefer pyramid models.

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

### Like This Article? Read More From DZone
