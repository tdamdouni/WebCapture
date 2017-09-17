# Automated GUI Testing: How to Get It Right

_Captured: 2017-09-01 at 21:00 from [dzone.com](https://dzone.com/articles/automated-gui-testing-how-to-get-it-right?edition=321391&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-09-01)_

[Download the blueprint](https://dzone.com/go?i=228233&u=https%3A%2F%2Foffers.automic.com%2Fblueprint-to-continuous-delivery-with-automic-release-automation%3Futm_campaign%3DAMER%252520Online%252520Syndication%252520DZone%252520Platinum%252520Sponsorship%252520Ads%252520JULY-2017%26utm_source%3DDzone%252520Ads%26utm_medium%3DBlueprint%252520to%252520CD) that can take a company of any maturity level all the way up to enterprise-scale continuous delivery using a combination of Automic Release Automation, Automic's 20+ years of business automation experience, and the proven tools and practices the company is already leveraging.

The right combination of manual and automated testing? We're all for it. Most high-quality bugs are still found by humans, and manual testing isn't going anywhere (ever).

That said, automation is critical to:

  1. Empower human testers to uncover more complex issues
  2. Help cover quality for existing functionality
  3. Provide constant, steady feedback on quality and performance

One of the trickiest aspects of any software to automate is graphical user interface (GUI) testing. That's because user behavior is complex. The complexity of automating GUI test cases can lead QA teams to have to constantly update their scripts, not automate enough (and not the reap the benefits above) or to create overly simplistic automated scripts that aren't valuable.

These tips will help you combat the complexity of GUI automated testing without forsaking value.

## **1\. Remove System Functionality From GUI Testing**

First thing's first: remove anything from GUI testing that isn't actually GUI testing.

Most system critical functionality can be [completely divorced ](https://www.stickyminds.com/presentation/behavior-patterns-designing-automated-tests) from GUI. When automated scripts rely too heavily on UI elements, then they become "brittle" as [Clint Hoagland ](https://www.stickyminds.com/articles/fixing-brittleness-problem-gui-tests)says: "Brittleness will kill an automation suite. It's all over as soon as someone says 'We shouldn't make that change; fixing the scripts will take too much time.' Automation should speed development up, not slow it down."

Any automated test whose script refers to the names of fields and buttons could need to be rewritten when those fields and buttons are renamed.

One way to bypass the complications of GUI testing is to not use GUI elements in the test scripts whatsoever. Program reasonable tests with context and expected results using back-end functions directly, instead of calling upon those functions in the way that a user would.

## **2\. Use Abstractions**

Using abstractions is another way to more easily maintain an automation suite of GUI tests. [An abstraction ](https://www.stickyminds.com/articles/fixing-brittleness-problem-gui-tests) takes the place of the specific details of how a test is done. It's a [form of refactoring ](http://searchmicroservices.techtarget.com/definition/refactoring)-wherein you change code to improve it internally without altering its behavior.

An easy example of this is a file upload.

**Here is a problematic script:**

On the Media Library page, click the button called "New Upload"

Select the file "test.pdf"

Click the button called "Upload"

In the field called "Title" enter "My Test PDF"

In the field called "Description" enter "Single page PDF"

In this script, we're detailing the process of the upload, meaning that if the process of the app or website changes, then this script (and countless others) need to change as well.

**But we can rewrite this script to be less susceptible to change by abstracting those details:**

On the Media Library page, upload "test.pdf"

On the File Details page, use the "Title" of "My Test PDF" and the "Description" of "Single page PDF"

When refactoring your scripts to include more abstractions and fewer details, first ask yourself whether that step needs to be rewritten or removed. For example, you don't want to include the login process in every single script, but only in the appropriate cases where logging in needs to be thoroughly tested.

## **3\. Learn From Manual Testing**

Far from replacing manual testing, automated testing actually takes much of its learnings and development from the manual testing of a product. At its core, [each manual test consists of three components ](https://www.stickyminds.com/sites/default/files/presentation/file/2013/07STRER_W3.pdf):

  1. The task to be performed.
  2. The related data needed to perform the task.
  3. The expected result.

Using the upload example again, the task would be uploading a file; the related data would be the PDF file, and the expected result would be that the upload is allowed.

A test doesn't have to include how to get to there-meaning how to get to the upload feature in the first place.

To keep your GUI test scripts agile, you want to program them with only the context required and nothing more. That's why we don't want to think in terms of navigation ([which is where our mind usually goes when thinking about GUI](http://usabilitylab.walkme.com/gui-testing-checklist/)). Rather than navigating through scripts like a user, we want to think like a manual tester.

The manual tester checks that they are in the right product area, decides how to perform a task, makes sure the environment and context are in place, and checks for the expected result.

A high-quality GUI script should be a singular event that begins with being in the right place. So rather than navigating us through an app to the right place, a script might simply begin with _On the "Account Settings" Page. _

## **4\. Rely on the Right Tools**

Choosing the right automation tools is critical to increasing the likelihood of ROI. Any automation project should be treated like a software development project, meaning it is going to be continually reiterated upon. Automation is an active, ongoing process. So, you'll want to choose an automation suite that works you and your team.

At the very least, you'll want to check for these factors:

  * **Easy to learn**: has syntax and classes that are intuitive and don't require complex coding so that with any organizational changes or team member handovers, the suite can be maintained
  * **Simple commands**: with GUI automated testing especially, you'll want a [small set of simple commands ](https://www.getautoma.com/docs) (things like click and scroll up) to use when writing scripts so that the language used is forcibly standardized and stable
  * **Recording**: to automatically write test scripts, you'll want to choose a [GUI testing tool ](http://www.softwaretestinghelp.com/best-gui-testing-tools/) that will record your actions and generate a script using object recognition (rather than record low-level events or rely on visuals), allowing you to review, modify, save and rerun the test
  * **Integrations**: the biggest [challenge with test automation ](https://www.capgemini.com/thought-leadership/world-quality-report-2016-17) is making use of the results, and to combat this you'll want the tool to integrate with your existing bug tracking system in a way that you will respect and trust -not overwhelm your system with low quality, repetitive bugs

Automating GUI tests can provide continuous feedback on the user's environment, verification of performance and functionality and comparison of repetitive test results. With the visual nature of GUI and the need for continual design improvements, the benefits of GUI automation testing can be easily overwhelmed by its fluidity. By streamlining scripts, you can protect their longevity and free up time for other quality enhancement projects.

_"[Automated GUI Testing: How to Get It Right](https://testlio.com/blog/how-to-automate-gui-testing/)" was originally published on [Testlio](https://testlio.com/)._

[Download](https://dzone.com/go?i=228234&u=https%3A%2F%2Foffers.automic.com%2Fblueprint-to-continuous-delivery-with-automic-release-automation%3Futm_campaign%3DAMER%252520Online%252520Syndication%252520DZone%252520Platinum%252520Sponsorship%252520Ads%252520JULY-2017%26utm_source%3DDzone%252520Ads%26utm_medium%3DBlueprint%252520to%252520CD) the 'Practical Blueprint to Continuous Delivery' to learn how Automic Release Automation can help you begin or continue your company's digital transformation.
