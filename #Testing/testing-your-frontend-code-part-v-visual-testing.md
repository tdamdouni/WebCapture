# Testing Your Frontend Code: Part V (Visual Testing)

_Captured: 2017-12-10 at 20:41 from [dzone.com](https://dzone.com/articles/testing-your-frontend-code-part-v-visual-testing?edition=343111&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-10)_

A while ago, a friend of mine, who is just beginning to explore the wonderful world of frontend development, asked me how to start testing her application. Over the phone. I told her that, obviously, I can't do it over the phone as there is _so_ much to learn about this subject. I promised to send her links to guide her along the way.

And so I sat down at my computer and googled the subject. I found lots of links, which I sent her, but was dissatisfied with the depth of what they were discussing. I could not find a comprehensive guide -- from the point of view of a frontend newbie -- to testing frontend applications. I could not find a guide that discusses both the theory and the practice and that is oriented towards testing frontend applications.

So I decided to write one. And this is the fifth part of this series of blogs. You can find the other parts here:

Also, for the purpose of this blog, I wrote a small app -- [Calculator](http://frontend-testing.surge.sh/) -- that I will use to demonstrate the various types of testing. You can see the source code [here](https://github.com/giltayar/frontend-testing).

## Visual Testing

Software Testing has always been a passion of mine. These days, I find it difficult to write code _without_ having tests for it. The idea of just _running_ the code in order to verify its correctness seems so _beginning of the century_ to me. You mean to tell me that in the past every time a developer changed their code, somebody needed to manually verify that everything that previously worked is still working? Really?

So I write tests. And because I love to give talks and write blog posts, I also talk and write about Software Testing. And when the opportunity arose to join a company whose vision is to enhance Software Testing, to write code that helps other people write tests, _and_ to evangelize their products, I did not hesitate one bit.

I recently joined [Applitools](https://applitools.com/?utm_source=SOF&utm_medium=GT) (as an Evangelist and Senior Architect, if you really want to know). And because their product, Applitools Eyes, has a direct connection to the content of this series, I decided to add one more post in this series -- a post about "Visual Testing."

Remember my amazement at the fact that developers actually need to always run their application every time they change their code? Well, up to now, one aspect of software products _necessitated_ manual testing -- the _visual_ aspect of the application. There was no way to check that the application still looks good -- the fonts are correct, the alignment is right, the colors are not off, etc.

Theoretically, you could write code that checks this. We saw in part [three](https://dzone.com/articles/testing-your-frontend-code-part-iii-e2e-testing) how we can use Selenium Webdriver to test our web application's UI. We could use Selenium's `getScreenShot` API to take a screenshot of the page, save it as a baseline, and then each test will also check the page screenshot against the baseline:

![](https://cdn-images-1.medium.com/max/800/1*enU_ljfglaGjZDaQyIrlew.png)

Ha! If only it were that simple. I tried this solution once, and found so many problems that I had to abandon it, and, yes, run the application every time I changed the code. The main problem is somewhat technical: there are subtle variations in the image related to how the browser renders the content -- depending on the screen or the GPU, the content is anti-aliased in subtly different ways. No two screenshots will have exactly the same pixels. This is almost imperceptible to the human eye, but it means that a pixel by pixel comparison is pointless. You need image analysis techniques to solve this.

But there are other problems, problems which I understood only when I started working at Applitools:

  * You can't take a full page screenshot -- you can only take a screenshot of what's in the viewport.
  * If the page has animations, then you will never be able to compare them to the base image.
  * Dynamic data, like ads, will complicate figuring out the real differences against the baseline.
  * When is the page "fully loaded"? When can I take that screenshot? These days, taking a picture when the DOM is loaded is not enough. Figuring out when you can take that screenshot is difficult.

## Yes We can

But it seems we can write automated visual tests. A myriad of tools, which I was unaware of, exists to enable you to take good screenshots and compare them to base images. Some of these are:

These tools solve all or some of the problems described above. In this part of the series, I want to show how to use Applitools Eyes to write a visual test.

## Writing a Visual Test

Visual tests, since they test the final product, should be used in frontend E2E browser tests. So this is where [I put our visual test](https://github.com/giltayar/frontend-testing/blob/master/test/e2e/test-app.js). The code, interestingly enough, is smaller than our regular E2E test. It consists of three parts -- setting up the browser, setting up Applitools Eyes, and the test itself.

Let's look again at the selenium driver browser setup, which is the same setup used in the E2e test in [part four](https://dzone.com/articles/testing-your-frontend-code-part-iv-integration-tes):
    
    
      driver = new webdriver.Builder().forBrowser('chrome').build()
    
    
    after(async () => await driver.quit())

This opens a browser and waits for `driver` commands. But before starting with the test, we need to setup (and teardown) Applitools Eyes:
    
    
    const {Eyes} = require('eyes.selenium')
    
    
      await eyes.open(driver, 'Calculator App', 'Tests', {width: 800, height: 600})
    
    
    after(async () => await eyes.close())

We create some new `Eyes` (line 5), and open them (line 8) -- cute terminology, isn't it? Don't forget to get an API Key from Applitools, which we'll talk about in the next section, and give it to the Eyes (line 6).

Now that we've set up the browser and eyes, we can write the test, which is very similar to our E2E test:
    
    
    it('should look good', async function () {
    
    
       await driver.get('http://localhost:8080')
    
    
       const digit4Element = await driver.findElement(By.css('.digit-4'))
    
    
       const digit2Element = await driver.findElement(By.css('.digit-2'))
    
    
       const operatorMultiply = await driver.findElement(By.css('.operator-multiply'))
    
    
       const operatorEquals = await driver.findElement(By.css('.operator-equals'))

Comparing it to the E2E test in the [previous post in the series](https://dzone.com/articles/testing-your-frontend-code-part-iii-e2e-testing), you can see that this one's similar, but shorter. The main difference is that in this code, the validation of specific elements is replaced by one simpler line:

`await eyes.checkWindow('<check-name>')`

In the E2E test, we did this instead of this one-liner:

We waited, using retries, for the page to "stabilize." But when doing Visual Testing, you don't need to wait for the page to visualize -- `eyes.checkWindow` will do this for you!

`eyes.checkWindow` will take a screenshot of the page, and compare it against a baseline image from a previous test (see how it works in the section "Running the Visual Test" below). If the comparison says that the new image is equal to the baseline, then the test succeeds, otherwise, it fails.

## Visual Testing as a Better Validation Tool in E2E Tests

And this a huge benefit of doing visual tests -- stabilization is dealt with by the system. Moreover -- you're not just checking one element or two elements -- _you're checking the whole page in one assertion_. You will probably find problems that you weren't even looking for!

In general, it seems that **visual testing should be _the only way_ you do assertions in E2E tests**. Unfortunately, visual assertions are currently somewhat slower, so you need a good mix of regular assertions that check a specific element and visual assertions that check the whole page.

Remember -- there are no panaceas: no one type of test can do everything! A mix of various types of testing will give you the best balance, and it takes experience in testing to determine what this mix is. So start testing now! Yes, testing takes time and commitment. But once you start testing, you really can't go back.

## Running the Visual Test

How do we run the visual test and see the outcome?

`npm test` will skip the visual tests if you do not supply an API key in the environment variable `APPLITOOLS_APIKEY`. To get an API key so that you can also run the test, go to the [Applitools](https://applitools.com/?utm_source=SOF&utm_medium=GT) site, and register. In your account in the Applitools UI, you will find the API Key. Copy it to the clipboard, and then run the test with (on Linux/MacOS):

`APPLITOOLS_APIKEY=<the-api-key> npm test`

or, if you're using Windows, use:

`set APPLITOOLS_APIKEY=<the-api-key> && npm test`

Once you have that, you can run the test. The first time, the test will fail with the error`EYES: NEW TEST ENDED`.

![](https://cdn-images-1.medium.com/max/800/1*cmKtmhTxgT0-djzUxFbs2A.png)

This is because there is no baseline to test against. On the other hand, if we look at the Applitools Eyes interface, we will see this:

![](https://cdn-images-1.medium.com/max/800/1*xB6VHBxeK6ywBX7budOEHQ.png)

From the Applitools point of view, the test passed, because this is a baseline, and it assumes that the baseline is correct. You can make it "fail" by using the interface "Like/Unlike buttons" for each screenshot.

The second time you use `npm test`, the test will succeed:

And Applitools UI will show this too:

![](https://cdn-images-1.medium.com/max/800/1*BRtuHHWvek7g4Tca6jZ4pA.png)

If we explicitly fail the test, by (for example) clicking **_43_** * **_3_** instead of **_42_** * **_2, _**the test will fail, and the Applitools UI will show the test and highlight the difference:

![](https://cdn-images-1.medium.com/max/800/1*1tsSb03NaRPtSIqQaDAzCQ.png)

> _Fixing the "bug" will again make the test pass, both in Mocha and in Applitools._

## This Concludes

This concludes the series about testing frontend code. If you feel I've missed anything, or have any other questions/comments/rants, please tweet to [@giltayar](https://twitter.com/giltayar?lang=en), or respond to this article.

I must admit that I feel the itch to write one more post in this series -- a post about testing applications that include Ajax calls, as any _real_ application will have them.

Who knows?

Special thanks to [Doron Zavelevsky](https://medium.com/@zavelevsky?source=post_page).
