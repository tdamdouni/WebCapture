# Multi-Browser and Multi-Environment Testing in Serenity BDD

_Captured: 2017-05-10 at 22:09 from [dzone.com](https://dzone.com/articles/multi-browser-and-multi-environment-testing-in-ser?edition=298048&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-10)_

### If you've designed a web application, but need to make sure it works on several browsers, or runs in several environments, try Serenity BDD.

[Learn how to build modern digital experience apps](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) with Crafter CMS. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).

When we write automated acceptance tests, we often want to run the same test in different environments, or on different browsers, and still see each test run appear in the reports.

The latest version of Serenity BDD allows you to implement multi-browser and multi-environment testing using the notion of _contexts_. A context is a way of running the same test several times, and showing all of the results in the same report.

### Simple Test Contexts

For example, you could run your tests using the Chrome WebDriver, providing a context called "chrome":

You might then run the tests again (or in parallel, on a different machine) using Firefox:

You might also run the tests a third time using PhantomJS:

Serenity will now include test runs for all three browsers in the same report:

![](https://i2.wp.com/johnfergusonsmart.com/wp-content/uploads/2017/05/Screen-Shot-2017-05-02-at-9.28.44-am.png?resize=1024%2C264&ssl=1)

### Adding More Readable Tags

Serenity will add a "context" tag to each of your tests, but you might want to make your reports even clearer by adding a more meaningful tag. You can do this using the "injected.tags" system property:
    
    
    $ mvn verify -Dcontext=chrome -Dwebdriver.driver=chrome -Dinjected.tags="browser:chrome"

This way, you would get tags for both the browsers and the test contexts appearing in the reports:

![Serenity BDD supports multi-browser and multi-environment testing.](https://i2.wp.com/johnfergusonsmart.com/wp-content/uploads/2017/05/Screen-Shot-2017-05-02-at-9.28.35-am.png?resize=1024%2C607&ssl=1)

> _Serenity BDD supports multi-browser and multi-environment testing._

(You can disable the context tag entirely if you prefer by setting the _serenity.add.context.tag _property to false).

### Cross-Browser and Cross-OS Tests

There are a couple of common use-cases for contexts: running the same test in different browsers and running the same test on different operating systems. If you use the name of a browser (e.g. "chrome", "firefox", "safari", "ie"), the context will be represented in the reports as the icon of the respective browsers. If you provide an operating system (e.g. "linux", "windows", "mac", "android", "iphone"), a similar icon will be used. If you use any other term for your context, it will appear in text form in the test results lists, so it is better to keep context names relatively short.

### Aggregating Test Results

You may also choose to run a large test suite on several machines in parallel, and then merge the reports together. You can do this simply by:

  1. Providing a different context for each test run.
  2. Copying the contents of the _target/site/serenity_ directories into the target/site/serenity directory of your main project.
  3. Generate the aggregate reports from this main project (using "mvn serenity:aggregate" or "gradle aggregate").

These features will work with version 1.4.0 of serenity-core.

Crafter is a [modern CMS platform for building modern websites](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) and content-rich digital experiences. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).
