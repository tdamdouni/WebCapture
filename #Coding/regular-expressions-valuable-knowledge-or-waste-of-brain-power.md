# Regular Expressions: Valuable Knowledge or Waste of Brain Power?

_Captured: 2017-12-05 at 13:45 from [dzone.com](https://dzone.com/articles/regular-expression-valuable-knowledge-or-waste-of?edition=343093&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-04)_

[Build vs Buy a Data Quality Solution: Which is Best for You?](https://dzone.com/go?i=251321&u=http%3A%2F%2Fwww.melissa.com%2Fresources%2Fwhitepapers%2Fbuild-vs-buy-challenge.html) Gain insights on a hybrid approach. Download white paper now!

I was in a training class this week, covering some of the new features within the [MuleSoft Anypoint Design Center](https://www.mulesoft.com/platform/anypoint-design-center).

The training class was being held over WebEx and was running in the PST time zone. Me being in the EST time zone, this made for a late start for the class (11 a.m.) and an even later ending for each day's sessions (after 7 p.m. local time).

Seven members of the [CleanSlate Technology Group](https://www.cleanslatetg.com/) team, including myself, were attending the training. One individual (let's call him Dave), was very new to the MuleSoft space and had a background in technology that does not include a great deal of programming knowledge.

During the class, the instructor brought up the idea of using regex to enforce validation for a particular element to the API we were jointly creating. The instructor asked that we include the following line in our RAML-based API configuration:

`pattern: ^[A-Z]{2,2}[0-9]{2,2}[a-zA-Z0-9]{1,30}$`

Initially confused, Dave asked, "What is all that text about?"

## Regex Explained... on the Fly

What I found interesting was the dialog that ensued, where some of the other five team members (excluding myself) attempted to explain regular expressions to Dave... in a matter of a few words. Some of those who offered insight had 10+ years of programming experience, while another had just a year of programming experience under his belt. With each attempt, Dave seemed to get further confused and simply decided to accept not understanding the concept.

For the record, this is how Wikipedia defines a [regular expression](https://en.wikipedia.org/wiki/Regular_expression):

> "A regular expression is, in theoretical computer science and formal language theory, a sequence of characters that define a search pattern. Usually this pattern is then used by string searching algorithms for "find" or "find and replace" operations on strings."

I added my insight, which is basically to say, "At one time, I really understood regex, but now I simply use Google to locate the right regular expression to meet my situation." I must confess that my response may have been related to working four hours before the 8-hour class started, allowing some slight fatigue to have an impact on my opinion.

## Is Knowing Regex Really Worth Your Time ... and Brain Power?

Basically, I decided to let go of my regex knowledge in order to allow other more-valuable elements to remain in the [prefrontal cortex](https://en.wikipedia.org/wiki/Prefrontal_cortex) of my brain. I realized years ago that Google and StackOverflow are amazing sources for finding the best regular expression for the need being solved. To me, this is no different than memorizing the aspects of an API when nearly every development tool provides the ability to use a dot (.) in order to provide a list of available methods or functions once the object is declared.

So, in my personal view, being a pro at regular expression creation is not a high priority.

What I am not sure of is if my views represent the majority or the minority of our current reader base. As I was driving home from the class, I decided I would create this article to state my views and hope others will provide their comments to compliment or contrast my views.

My core question is: **Are you still taking up some of your valuable brain power to maintain regular expression creation ability?**

Have a really great day!

[Build vs Buy a Data Quality Solution: Which is Best for You?](https://dzone.com/go?i=251322&u=http%3A%2F%2Fwww.melissa.com%2Fresources%2Fwhitepapers%2Fbuild-vs-buy-challenge.html) Maintaining high quality data is essential for operational efficiency, meaningful analytics and good long-term customer relationships. But, when dealing with multiple sources of data, data quality becomes complex, so you need to know when you should build a custom data quality tools effort over canned solutions. [Download our whitepaper](https://dzone.com/go?i=251322&u=http%3A%2F%2Fwww.melissa.com%2Fresources%2Fwhitepapers%2Fbuild-vs-buy-challenge.html) for more insights into a hybrid approach.

Opinions expressed by DZone contributors are their own.
