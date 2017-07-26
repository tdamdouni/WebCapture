# How to Charge for your Open Source

_Captured: 2015-11-27 at 11:28 from [www.mikeperham.com](http://www.mikeperham.com/2015/11/23/how-to-charge-for-your-open-source/)_

![](http://www.slate.com/content/dam/slate/blogs/moneybox/2014/10/24/find_unclaimed_property_check_these_sites_to_see_if_somebody_owes_you_money/109471093-currency-is-seen-in-this-january-30-2001-image-afp.jpg.CROP.promo-mediumlarge.jpg)

Every month or so we hear of another high profile open source developer who flips the table and rages about open source because of burnout, most recently [Ian Cordasco](http://www.coglib.com/~icordasc/blog/2015/11/corporations-and-oss-do-not-mix.html) and [Ryan Bigg](http://ryanbigg.com/2015/11/open-source-work/). Does this sound familiar?

  1. Spend many hours writing software.
  2. Spend many hours supporting users and solving their problems.
  3. Make $0.

If you were a freelancer and did that with clients, you'd be:

  1. Overwhelmed with people asking for your help.
  2. Quickly starve with an empty bank account.

So why is it noble for OSS developers to do it? If a library would cost a client $5000 in your time to develop, why not sell the library as a product and charge each user one hour of your time, say $150? Money doesn't solve burnout but think of it this way: almost every issue email you get is a net negative on your mental health, almost every sale email you get is a net positive.

"Corporations need to step up."

99% of corporations will do what they are legally obligated to do, no more or less. So make them do something! **The easiest way to make someone value your time and software is to charge for it.** The goal of this blog post is not to rant about hypotheticals but rather **show you how easy it is to charge for your work**.

## Sidenote

I don't want to argue freedom and capitalism in the comments. If software freedom comes at the expense of burning out software developers, that's not freedom, that's [tragedy of the commons](https://en.wikipedia.org/wiki/Tragedy_of_the_commons). By charging for your work, you stop its exploitation.

## Legal

Remember: **Open Source != Free Software**. The source may be viewable on GitHub but that doesn't mean anyone can use it for any purpose. There's no reason you can't make your source code accessible but also charge to use it. **As long as you are the owner of the code, you have the right to license it however you want.**

  1. Make sure your project documents the fact that **contributors must assign all rights to you.** This allows you to accept pull requests. Some projects require a [CLA](http://oss-watch.ac.uk/resources/cla); I think that's overly conservative but IANAL.
  2. License the project as AGPL by default by adding a `LICENSE` file with the AGPL in it. The AGPL requires users to open source any software which uses your library; businesses will pay to avoid it. This is exactly what we want.
  3. Add an MIT license in a `COMM-LICENSE` file.
  4. Note in your README that the licensing is AGPL by default but an MIT license is available for purchase.

Note this is the simplest thing that might work, not what I do. MIT contains a number of serious problems for commercial software; a real business would want to use a custom license which forbids redistribution and sublicensing.

## Commerce

This assumes you are in the United States.

  1. Open a [Plasso account](https://plasso.co/). You'll also open a Stripe account as part of the signup, connected to your bank account. (I have no connection with Plasso aside from being familiar with their platform as I use it to sell Sidekiq Pro. I've also seen people use Wufoo or FastSpring.)
  2. Determine your pricing. Decide if you want to charge one-time or as a subscription. More complex projects can easily justify ongoing payment. You can also charge per major version, like books do with first edition, second edition, etc. For small libraries with no guaranteed support, I think charging your hourly rate per major version is entirely reasonable.
  3. Once you have created a product page in Plasso, put the link in your README. Here's [Sidekiq Pro's product page](https://plasso.co/s/YSeEjhi5ga) on Plasso for example.
  4. Money will appear in your bank account two days after purchase. You'll get an annual 1099-K from Stripe which (IIRC) you report as miscellaneous income on your annual tax return.

That's it! Upon purchase, the customer gets an email receipt from Plasso that says they bought the commercial license option for their records.

Well done, you just became a professional open source developer and thought leader in our industry. Tweet at @mperham so I can congratulate you personally!

Just because you charge for something doesn't guarantee you will make any money. **But if you don't charge for it, I guarantee you will make no money.**

## Denouement

Consider what we've done here: your project is still Open Source but we've added a method for grateful users to support you and a legal mechanism forcing businesses to pay if they want to use your library and not open source their application due to the AGPL.

Now it's up to you how much time and effort you want to spend evanglizing and supporting your work. If you think having users feels good, just wait until you get a few customers and can pay for a vacation each year with your OSS work. Good luck!

## Notes

  * "But what about…" Money doesn't solve all problems. This won't work for every developer, every library or every project. The world is complex and your mileage may vary.
  * Having unpaid collaborators can feel a little weird at first but reality is most smaller OSS projects have a single person doing 95% of the work. If this is true, be grateful for unpaid help but don't feel guilty about keeping 100% of the income.
  * "Then users will just use some other free library" \- and you just reduced your support load. **You don't want free users who don't value your effort.** Let someone else deal with them and suffer the burnout. Focus on making the best, most useful library you can that solves your own need.
  * "Great, now I've got two jobs!" You have just as much commitment as you had when building a free library. You aren't guaranteeing any support.
