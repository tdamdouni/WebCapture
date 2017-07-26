# Improving Conversion Rate for “Checkouts” App Installs

_Captured: 2015-12-31 at 22:19 from [medium.com](https://medium.com/@xsvfat/improving-conversion-rate-for-checkouts-app-download-9b1e2c3d1723#.8fstkasdo)_

### _Phase 1: Understanding the Problem_

_This phase gives background context on Checkouts and frames the problem surrounding their goal of improving app installs._

#### Background

[Checkouts is a Shopify plugin](https://apps.shopify.com/slick-checkout) that lets store owners offer Apple Pay to their customers visiting from a mobile browser.

"Checkouts" has two components:

  1. **An iOS app for consumers: **Apple Pay is normally reserved for use within iOS apps (e.g. Uber) or in physical store locations (e.g. Chipotle). "Checkouts" is an iOS app that lets users access Apple Pay while shopping online from a mobile browser like Safari or Chrome.
  2. **A plugin for online store merchants: **Checkouts is available as a plugin to merchants who own online stores powered through Shopify. Merchants who install and add the Checkouts plugin to their store receive an additional "Apply Pay" button added to their store's cart page. Customers with eligible devices will be able to see and use the button when checking out.

Merchants are very open to using the Checkouts plugin so that it can help reduce the [shopping cart abandonment rate from mobile devices](http://baymard.com/lists/cart-abandonment-rate), which is 68.53%.

Customers who have completed the initial setup of the Checkouts app and Apple Pay can then quickly make payments at eligible online stores. A user can simply touch their finger to the phone and, following a quick fingerprint scan, the app will populate their shipping and billing information.

#### Goal

Increase the conversion rate of users who download the Checkouts app from the shopping experience flow.

#### Current App Download Flow

![](https://cdn-images-1.medium.com/max/1200/1*_e-cemW_nSaW7KeH496j0A.png)

#### Design Constraints and Considerations

  * The checkout screen (Image 1, above) is the only opportunity for a user to click on the Apple Pay button. Unlike other official Shopify payment providers (e.g. PayPal, Amazon, Google), the Apple Pay option is not elligible appear on any other screens in the checkout process.
  * Customization needs to be limited for the placement, positioning, and size of the Apple Pay button on the checkout page.
  * 35% of current users that checkout through the Checkouts app apply a discount.

### Phase 2: Rapid Usability Tests and Iterations

_This phase covers the results of several rounds of rapid Usability Tests and Design Iterations on the "Checkouts" app download flow._

#### Plan of Attack

While I had some assumptions on what could be changed from the current flow, my plan was to first conduct several rounds of rapid Usability testing in order to:

  1. Identify all the sticking points potential customers might experience.
  2. Better understand the various user personas.

I chose to do this style of rapid testing and iterations because I knew that I would not be able to gather enough test participants to reach any sort of statistical significance for this type of product.

#### Usability Test Round 1

I conducted an initial Usability Test for Checkouts to begin to get a feel for the overall range of problems so I could identify which areas to focus on going forward.

**Test Participant: **Patty (Designer)

**Where/How: **Remote Usability Test using a live site

**Test Results:**

Patty started from the homepage of fazeclanstore.com. She was then directed to add an item to her cart, proceed to the checkout area, and then stop.

![](https://cdn-images-1.medium.com/max/400/1*ShACc_1CQCbxmUQaaYhEYA.jpeg)

![](https://cdn-images-1.medium.com/max/400/1*M1dvSVybIPXomGYq42CtQQ.jpeg)

> _1. Homepage-> 2\. Product Page->3.Cart Page_

![](https://cdn-images-1.medium.com/max/400/1*VIv1-VvLohZADkSVjlrOuw.jpeg)

**Reaching the Checkout Button Area:**

![](https://cdn-images-1.medium.com/max/600/1*8gsOeFbLpVnxXbNOqIAAmA.jpeg)

_Q: What are the different options you see that you could use to purchase this item?_

A: I see a Checkout Button, an Apple Pay Button, a PayPal button, and then a bunch of other payment methods.

I am afraid if I click the Checkout Button, I won't be able to get back to the PayPal button on the next screen. So I would normally go ahead and click the "PayPal Check out" button here.

_Q: What do you think would happen next if you clicked the Apple Pay button?_

A: I'm not sure what will happen next when I click the Apple Pay button, and that is enough to discourage me from clicking it. Also, the text saying "Apply discount on next step" is confusing. I'm not sure what discount on next step is.

_Q: Do you find this or anything else on this screen confusing?_

A: Yes. There is no parallelism between any of the buttons here. It is very confusing. The Apple Pay button looks like it is very high priority.

_Q: Have you used Apple Pay before?_

A: I have not used Apple Pay before but I have heard of it and I know what it does.

-

**Reaches the Informational Page:**

I instruct the user to click on the Apple Pay button so we can proceed to the next page.

![](https://cdn-images-1.medium.com/max/600/1*dUDc-9nrRpson0lIXeEItQ.jpeg)

_Q: Walk me through what you think when you look at this page._

A:

This looks like a sales page. It makes me want to immediately click the back button.

It looks like it's selling me on a service called Apple Pay.

I thought after clicking on the Apple Pay button I would be able to immediately pay.

This page is not from the original store buyer. I've completely left that site and I'm now on somebody else's sites.

It definitely does not look like something from Apple.

_Q: Does this page feel trustworthy to you?_

A: It does not feel trustworthy; it feels like an ad.

_Q: What do you think are the factors that make this page seem untrustworthy to you?_

A:

  * The domain name slick.checkout.com sounds extremely "scammy."
  * This looks like something to sell people on shopping carts.
  * Nobody uses language such as "Get checkouts." That's not how you talk people.
  * The text, "The quickest way to make purchases on iPhone. Ever." sounds extremely sales-y.

_Q: What do you think would happen next if you clicked the button at the bottom of the page?_

A: I can download this?! I thought this was a marketing page somebody wanted to use for a shopping cart. This is something I can personally put on my phone? I had no idea it was prompting me to download an app.

**Initial Conclusion**

Based on my initial usability test, I determined I already had enough to work with; I wanted to focus on testing and optimizing the pages the user sees before he or she reaches the app download page. Once the informational page was optimized, I would then update the style of the app download page so the designs matched.

#### Round 1 Iterations

**Updates to the Apple Pay Button**

While the test participant found the discount language confusing, it is worth considering that a certain percentage of users may be clicking the Apple Pay button solely because of this discount text. Therefore, I would recommend conducting a live A|B test on the Apple Pay button with and without the discount text to settle this issue.

Additionally, Checkouts should also test:

  * button discount copy
  * button text copy
  * button color
  * button width.

**Design Updates to the Informational Page**

The informational page had a few key areas for improvement:

  1. Increase trustworthiness
  2. Better inform the user that they are still connected to the site they were previously shopping on
  3. Better explain the reason why the user should download the Checkouts App
  4. Use language and tone that's more in line with an Apple-associated product
  5. Improved call-to-action (CTA) button to accurately reflect the next steps in the process
  6. Clearly convey that "Checkouts" is an app

With this in mind, I created a new design (see below) as a starting point for my next round of Usability Testing.

![](https://cdn-images-1.medium.com/max/800/1*ENqCSe3wBfGlqgrA0MMkwg.png)

**Changes to Usability Testing Questions**

I reviewed my initial usability test questions and result with my Design Lab mentor, [Francine Lee](https://medium.com/u/a01b5f296910), and she recommended I update my question:

_Does this page feel trustworthy to you? -> Would you feel comfortable entering in your credit card information on a page that followed from here? (_Re-calibrated to be more specific as to what I am actually testing for.)

#### Usability Test Round 2

I conducted four more Usability Tests for Checkouts, making iterations between each test.

**Test Participants: **Various

**Where/How: **Remote Usability Test via Invision App

![](https://cdn-images-1.medium.com/max/600/1*V3aW9hWIlR5zdFM0CFCHJQ.png)

![](https://cdn-images-1.medium.com/max/600/1*4Abw3XE_T-V0x30exp9C8g.png)

#### **Key Findings:**

The design modifications were overall effective in increasing trustworthiness that Checkouts was part of their shopping transaction. The users felt confident that they were still connected to the previous site they had been on and mostly understood the next steps they needed to take.

While the users understood that Checkouts was an app they had to download, the users still didn't understand why they _needed_ to use it. This is a tough problem to solve because of two main reasons:

  1. Even users who were familiar with, and have used, Apple Pay did not realize that it can't be used on websites.
  2. Users who were not familiar with Apple Pay had a very difficult time understanding what was going on. Even the lengthier explanation and diagram did little to help explain the need to download the app.

### Phase 3: Developing Recommendations

_This phase covers how I analyzed my test results and developed a final set of recommendations._

After a few quick rounds of Usability Tests and Design Iterations, several new factors became clear:

  1. **The informational page needs to balance several different user needs** -- Some users are already familiar with Apple Pay or may not care about the exact details of how the Checkouts App functions; for these users, the informational page needs to be short, clean, and concise in order to have the least amount of friction. Other users, however, are not as familiar with Apple Pay and its benefits and a need more detailed explanation of why they need the Checkouts App; in this case, the informational page needs to clearly answer their questions.
  2. **Additional Usability Testing would not be helpful -- **I wanted to test the correct balance of different screen designs with varying levels of information; however, I knew it was improbable to test a large enough number of users in order for my findings to have statistical significance. To gain any meaningful data, it would be better to offer suggestions of several options to be conducted via live A|B tests. Checkouts currently processes several hundred transactions a day so this would also be a much quicker way to get the information I needed.
  3. **Re-consider a higher level approach with our live A|B testing -- **Given that the best approach would be to conduct a large amount of A|B tests to determine the optimal decision, it is absolutely necessary to test alternative approaches, as well. The test needs to determine how a user responds to being sent directly to the app download page or presented an iOS alert instead of an informational page.

#### **A**|**B Testing Recommendations**

Using the below images, a successful A|B test will try to find the right balance of informing the user while not fully disrupting the shopping process. A screen with more content will do the best at informing the user but will also cause the greatest disruption; a screen with the least amount of content will cause no friction but may not achieve its goal.

![](https://cdn-images-1.medium.com/max/800/1*vAJQSvuTnm6VCPvtrfncUQ.png)

> _A third set of tests should also be performed, taking the user directly to the app download page rather than having them rely on informational pages or notifications._

A second A|B test could then look at an alternative set of designs (see below). In these images, information is collapsed to try to accommodate two user groups: former Apple Pay users and those who have never used it before.

![](https://cdn-images-1.medium.com/max/800/1*ikJcql-3xGN7NWJzMIvotw.png)

#### **App Store page design changes**

The App Store page design was also tweaked to match Apple's style. The focus of these changes was mostly on improving the screenshots.

The icon remains the same for now. A test on Usability Hub compared the current icon to a new design; the current icon, albeit not the prettiest, had better results in the test.

![](https://cdn-images-1.medium.com/max/800/1*JBT9L9_Nmiw3ar5W1XTCOw.png)

#### Final Results

This post was made recently, I'll update this post with results when the updates go live!

#### Additional Note

I thought Checkouts was a poor name choice and wanted to test whether there was a better alternative.

There were a few problems with the current name:

  1. We needed to use the word "checkouts" in text descriptions, but had to avoid the word because it was already in the app name.
  2. "Checkouts" doesn't accurately explain what the app actually accomplishes. The app is truly more of a connection (or bridge) between Apple Pay and the store where the user is shopping.
  3. There was a concern that "Checkouts" sounded like it was part of a a scam; it didn't leave users with an overall impression of trust and security.

Using a new app name, Bridge Payments, I created a mockup of an App Store page. I then ran a test on Usability Hub asking users to compare this screen (see below) to the current App Store page for the Checkouts app.

![](https://cdn-images-1.medium.com/max/800/1*IZpg-a3XKuxKpT0WyTC5aw.png)

It wasn't even close; the Bridge Payments screen performed very badly in the test. Lesson learned: although it's good to listen to instinct, sometimes you just need to rely on the data.
