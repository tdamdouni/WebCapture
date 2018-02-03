# Website UI Testing

_Captured: 2018-01-31 at 21:34 from [dzone.com](https://dzone.com/articles/website-ui-testing?edition=359100&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-31)_

Planning to extract out a few microservices from your monolith? Read this [free guide](https://dzone.com/go?i=265421&u=https%3A%2F%2Ftry.split.io%2Fmonolith-breakup-stateful-services-ebook%3Futm_campaign%3D2018%252520DZone%252520DevOps%26utm_source%3Ddzone%26utm_medium%3Dpre%252520roll) to learn the best practice before you get started.

Last week, I looked at testing the [UI of mobile apps](https://www.funkysi1701.com/2018/01/08/ui-testing/), this week lets look at how we could do a similar thing for websites.

Testing the user interface is not an excuse for a lack of unit tests. Testing the user interface takes longer, so for keep creating your small unit tests that can be run after every build. That said, lets look at how you create a UI test.

Create a Unit Test project as normal. Now install the following nuget packages:

I am going to be using Selenium to achieve my website testing, and I am going to concentrate on the Chrome browser. However, packages exist for other browsers, so have a look at the following, and I expect there are others as well.

[Selenium](http://www.seleniumhq.org/) started life as a plugin for Firefox to help create automated tests, however, the latest version of Firefox is not compatible with the plugin as I write this. I have not had to install any plugins or extensions to my browsers to achieve my testing.

Enough talk - lets write a test. First, we create two instance variables to store the baseURL and the driver for the browser you are using.

Next, we need to set things up for the test to run. This creates an instance of the Chrome driver, maximizes the window, and sets it to wait 30 seconds before timing out.
    
    
        driver.Manage().Timeouts().ImplicitlyWait(TimeSpan.FromSeconds(30));

Now comes the actual test. We navigate to a URL and then compare the title of the page loaded with a known value with an Assert statement like you would find in a unit test.

Finally, we need to tidy up after ourselves.

If you are used to writing tests you will know that the are usually constructed in three sections Arrange, Act and Assert. The Arrange is done in the initialize method, which makes the actual test much simpler, the first line does the Act and the last line does the Assert.

Now we have written a simple test lets look at something more complex.

This finds any Link on the page which is click. Be careful as the string need to be exactly what appears on screen it may well be easier to specify by id or class or something that doesn't change as often. By adding .click() on the end of this command Selenium will click on the link and you can navigate to a new page.

**What about submitting form data?** Well you can find the element you want to fill in and add .SendKeys("example text") or .Submit() and this will fill in and submit form data.

**What about a screenshot? **

I have only just started playing around with web UI tests but you can see there is a fair bit you can do.

This post has already been read 102 times!

Measure the impact of feature releases, and of your DevOps program more broadly with full stack experimentation. [Learn how](https://dzone.com/go?i=265422&u=https%3A%2F%2Ftry.split.io%2Fmonolith-breakup-stateful-services-ebook%3Futm_campaign%3D2018%252520DZone%252520DevOps%26utm_source%3Ddzone%26utm_medium%3Dpre%252520roll) with this free article from CITO Research, provided by Split Software.
