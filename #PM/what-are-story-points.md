# What Are Story Points?

_Captured: 2017-08-01 at 07:17 from [dzone.com](https://dzone.com/articles/what-are-story-points?edition=311403&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-07-31)_

Reduce testing time & get feedback faster through automation. Read the [Benefits of Parallel Testing](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile), brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

Story points are a unit of measure for expressing an estimate of the overall effort that will be required to fully implement a product backlog item or any other piece of work.

When we estimate with story points, we assign a point value to each item. The raw values we assign are unimportant. What matters are the _relative values_. A story that is assigned a 2 should be twice as much as a story that is assigned a 1. It should also be two-thirds of a story that is estimated as 3 story points.

Instead of assigning 1, 2 and 3, that team could instead have assigned 100, 200 and 300. Or 1 million, 2 million and 3 million. It is the ratios that matter, not the actual numbers.

## What Goes Into a Story Point?

Because story points represent the effort to develop a story, a team's estimate must include everything that can affect the effort. That could include:

  * The amount of work to do.
  * The complexity of the work.
  * Any risk or uncertainty in doing the work.

When estimating with story points, be sure to consider each of these factors. Let's see how each impacts the effort estimate given by story points.

## The Amount of Work to Do

Certainly, if there is more of something to do, the estimate of effort should be larger. Consider the case of developing two web pages. The first page has only one field and a label asking to enter a name. The second page has 100 fields to also simply be filled with a bit of text.

The second page is no more complex. There are no interactions among the fields and each is nothing more than a bit of text. There's no additional risk on the second page. The only difference between these two pages is that there is more to do on the second page.

The second page should be given more story points. It probably doesn't get 100 times more points even though there are 100 times as many fields. There are, after all, economies of scale and maybe making the second page is only 2 or 3 or 10 times as much effort as the first page.

## Risk and Uncertainty

The amount of risk and uncertainty in a product backlog item should affect the story point estimate given to the item.

If a team is asked to estimate a product backlog item and the stakeholder asking for it is unclear about what will be needed, that uncertainty should be reflected in the estimate.

If implementing a feature involves changing a particular piece of old, brittle code that has no automated tests in place, that risk should be reflected in the estimate.

## Complexity

Complexity should also be considered when providing a story point estimate. Think back to the earlier example of developing a web page with 100 trivial text fields with no interactions between them.

Now think about another web page also with 100 fields. But some are date fields with calendar widgets that pop up. Some are formatted text fields like phone numbers or Social Security numbers. Other fields do checksum validations as with credit card numbers.

This screen also requires interactions between fields. If the user enters a Visa card, a three-digit CVV field is shown. But if the user enters an American Express card, a four-digit CVV field is shown.

Even though there are still 100 fields on this screen, these fields are harder to implement. They're more complex. They'll take more time. There's more chance the developer makes a mistake and has to back up and correct it.

This additional complexity should be reflected in the estimate provided.

## Consider All Factors: Amount of Work, Risk and Uncertainty, and Complexity

It may seem impossible to combine three factors into one number and provide that as an estimate. It's possible, though, because the effort is the unifying factor. Estimators consider how much effort will be required to do the amount of work described by a product backlog item.

Estimators then consider how much effort to include for dealing with the risk and uncertainty inherent in the product backlog item. Usually, this is done by considering the risk of a problem occurring and the impact if the risk does occur. So, for example, more will be included in the estimate for a time-consuming risk that is likely to occur than for a minor and unlikely risk.

Estimators also consider the complexity of the work to be done. Work that is complex will require more thinking, may require more trial-and-error experimentation, perhaps more back-and-forth with a customer, it may take longer to validate and you may need more time to correct mistakes.

All three factors must be combined.

## Consider Everything in the Definition of Done

A story point estimate must include everything involved in getting a product backlog item all the way to Done. If a team's definition of done includes creating automated tests to validate the story (and that would be a good idea), the effort to create those tests should be included in the story point estimate.

Story points can be a hard concept to grasp. But the effort to fully understand these points represent effort as impacted by the amount of work, the complexity of the work, and if any risk or uncertainty in the work will be worth it.

The Agile Zone is brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile). Discover how to optimize your DevOps workflows with our [cloud-based automated testing infrastructure](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).
