# Refactoring Untested Code

_Captured: 2017-05-09 at 01:21 from [dzone.com](https://dzone.com/articles/refactoring-untested-code?edition=298022&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-08)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943538%26PluID%3D0%26ord%3D%255Btimestamp%255D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943538%26PluID%3D0%26ord%3D%255Btimestamp%255D).

Refactoring is, in general, restructuring code without changing its behavior. The key point here is the behavior because we need to make sure that the behavior remains the same after refactoring. How do we make sure the behavior stays same? Tests. Tests make sure our system or component behaves as expected under certain conditions. When we have tests in place, then it's easy to do the refactoring, since we have some validation in place. Nevertheless, having tests in place is just the happy path. Let's go over a more challenging path.

## Legacy Projects

We will first create a scenario. Your manager throws you into a legacy project. Nobody knows how the project works and there isn't much documentation either. So, what do we do? Quit? Sounds like an idea but no. All we need to make sure of is that the behavior remains the same. Yet, this is very challenging when you have little information. Where do we start? Testing and, again, testing.

## Smoke Tests

The first type of test that we will employ is smoke tests. Smoke tests are very good at showing that most crucial part of the system behaves as expected. We should add smoke tests as a build verification step to our deployment pipeline (create one if it does not exist). Once smoke tests are in place, we can be confident that we won't break anything terribly. The second important part is the knowledge. Once you construct the smoke tests, you should understand the system much better.

## Unit Testing

Our next testing strategy is the unit testing. Employing unit testing is much harder. However, it should be a step-by-step process. You can't write unit tests for every single component. Also, it's not really wise to write either, as you will soon refactor it. Hence, we need to make sure the core components behave as expected. Hence, choose a core component and start testing. Writing unit tests will automatically refactor the legacy code a little bit. What's more, you'll understand the internals of the project much better.

## Conclusion

After applying these strategies we won't have any untested code, so the nightmare is gone. One might argue that s/he doesn't have time to do the testing. On the contrary, skipping the testing will hurt much more and more often in the long run. Thus, you should make the testing first and top priority before doing any refactoring. If anyone argues against testing, defend it; otherwise, you will fail harshly.

Dealing with untested code might be unavoidable. So if you are to refactor untested code, then test it first. There isn't really any better strategy. Skipping testing is just signing your surrender.

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943536%26PluID%3D0%26ord%3D%255Btimestamp%255D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943536%26PluID%3D0%26ord%3D%255Btimestamp%255D).
