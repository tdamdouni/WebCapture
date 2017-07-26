# Looking at Test-Driven Development

_Captured: 2017-03-16 at 21:23 from [dzone.com](https://dzone.com/articles/looking-at-test-driven-development?edition=283884&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-16)_

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

![TDD Cycle](https://i2.wp.com/www.funkysi1701.com/wp-content/uploads/2017/03/tdd_flow.gif?resize=287%2C300&ssl=1)

A few weeks back, I attended a talk at [Agile Yorkshire](http://www.agileyorkshire.org/event-announcements/tuesfebruary21st-drolivershawtestdrivendevelopmentthemostmisusedterminsoftwaredevelopmentandkeithwilliamsdependenciesinjectionandabstractionforfunandprofit) about test-driven development (TDD) by Dr. Oliver Shaw. I was impressed at how easy the Oliver made it look, so, as I have never tried it, I thought I should give it a try.

TDD is a way of development that starts with writing a unit test. First, you write a failing test. Then, you write the code to make it pass. Then, you refactor your code. This can be remembered by thinking of "red, green, refactor" -- "red" being the failing test, "green" being getting the test to pass, and "refactor" being the refactoring.

During the demonstration, Oliver used a language called Scalar and a system that automatically reran all the tests after every change. I code with Visual Studio in C#... is there a way I can get my tests to run automatically, as well?

After a bit of googling and configuring, I can answer this as "yes."

The Nuget package called [Giles ](http://testergiles.herokuapp.com/)is a watcher that will rerun your tests similar to how Oliver did it with his scalar environment. Fans of _Buffy the Vampire Slayer_ will get the joke of why a watcher is called Giles. I couldn't get this to work with MSTest, but it works fine with NUnit. There is a PowerShell script `giles.ps1` that which you need to run and that will update every so often with how many tests have passed or failed. However, you may not see this if you are coding in Visual Studio, but there is a way to get a notification.

If you install the application [Growl](http://www.growlforwindows.com/gfw/), you can get notifications from Giles that pop up and then disappear. So, whatever you have on the screen, you can find out almost instantly if you have broken tests.

Another thing that I wanted to configure is a way of viewing code coverage and which methods are tested and which aren't. If you are familiar with VSTS, after a build, it gives you a percentage score for test coverage. I don't find this overly useful, as it doesn't tell you what is covered and what isn't. Also, what if you want to use GitHub? How do you calculate the code coverage then?

The Nuget packages [OpenCover ](https://www.nuget.org/packages/OpenCover/)and [ReportGenerator ](https://www.nuget.org/packages/ReportGenerator/)allow an HTML report of code coverage to be produced. I created a batch script that can be run whenever you require this information.

The commands are fairly straightforward; the only tricky bit is sorting out all the file paths to the different programs.

Now that I have all this plumbing set up, it's time to give TDD a try and see what I can build!

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).
