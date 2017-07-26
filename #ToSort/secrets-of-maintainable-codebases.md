# Secrets of Maintainable Codebases

_Captured: 2017-03-03 at 19:24 from [dzone.com](https://dzone.com/articles/secrets-of-maintainable-codebases?edition=273883&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-03)_

Reduce testing time & get feedback faster through automation. Read the [Benefits of Parallel Testing](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile), brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=124039&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-benefits-of-parallel-testing.html%3Futm_campaign%3Dparalleltestingwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).

You should write maintainable code. I assume people have told you this, at some point. The admonishment is as obligatory as it is vague. So, I'm sure, when you heard this, you didn't react effusively with, "oh, good idea -- thanks!"

If you take to the internet, you won't need to venture far to find [essays](https://www.justsoftwaresolutions.co.uk/articles/maintainable_code.html), [lists](http://culttt.com/2014/12/03/6-principles-writing-maintainable-code/), and [stack exchange questions](http://programmers.stackexchange.com/questions/134855/what-characteristics-or-features-make-code-maintainable) on the subject. As you can see, software developers frequently offer opinions on this particular topic. And I present no exception; I have little doubt that you could find posts about this on my own blog.

So today, I'd like to take a different tack in talking about maintainable code. Rather than discuss the code _per se, _I want to discuss the codebase as a whole. What are the secrets to maintainable codebases? What properties do they have, and what can you do to create these properties?

In my travels as a consultant, I see so many codebases that it sometimes seems like I'm watching a flip book show of code. On top of that, I frequently find myself explaining concepts like the cost of code ownership, and regarding code as, for lack of a better term, inventory. From the perspective of those paying the bills, maintainable code doesn't mean "code developers like to work with" but rather "code that minimizes spend for future changes."

![](http://www.daedtech.com/wp-content/uploads/2017/02/code-flip-book.jpg)

Yes, that money includes developer labor. But it also includes concerns like deployment effort, defect cycle time, the universality of skills required, and plenty more. Maintainable codebases mean easy, fast, risk-free, and cheap change. Here are some characteristics in the field that I use when assessing this property. Some of them may seem a bit off the beaten path.

## A High-Value Test Suite

You had to see this coming, so I'll get it out of the way right off the bat. You want unit tests. That notion is up there with death and taxes among life's inevitabilities. And yet, so often we miss the mark with interim valuations.

People tend to look for the presence of unit tests or the number of unit tests at first, and then mature to look for unit test coverage. I don't, personally, find any of these metrics highly predictive of maintainable codebases (though the absence of any automated testing generally correlates with low maintainability).

Surprising? Not if you consider how easily people can spray low-value unit tests at an existing codebase. Want coverage? Write a bunch of tests that invoke that gigantic Singleton at the heart of your application, swallow all exceptions, and don't assert anything. You can probably get your coverage up near 30% in just a few hours while doing absolutely nothing to improve your maintainability.

I look for two basic things when doing a snap evaluation of a test suite: if I delete a line of production code, does a test go red, and do the unit tests have high code churn? This indicates a high-value suite via Goldilocks triangulation. I know that any line in the codebase was created according to a plan and I know that the tests themselves are not unduly adding to the maintenance burden.

## High Cohesion, Low Coupling

Here, I offer a broad concern, but that's because I look for it thematically, in all facets of the codebase. The easiest way that I can express these concepts in a narrative sense is as follows:

  * High Cohesion: does stuff that needs to change together occur together?
  * Low Coupling: do you avoid making otherwise independent concerns dependent?

This represents a surprisingly holistic concern when talking about codebases. Developers will want to have a sense of these concepts when creating classes or even methods. But it rolls up from there as well. When eyeing more strategic application concerns, the team should consider cohesion and coupling for namespaces, projects, and even disparate applications as well. Does your codebase take on external service dependencies cavalierly or sparingly?

Low cohesion tends to drive risk and reputation related problems. If I use my couch to sleep, and I also put wheels on it and use it to get to work, my life gets weird in a hurry, and I offer explanations to others that make no sense. This happens because my couch is doing two disparate things. "Sorry I was late to the office -- one of the legs broke off of my couch." In code that becomes, "sorry you couldn't log in for a while -- we messed up the CSS for a maintenance screen."

High coupling tends to create business capability nightmares. "Oh, yeah, I can't move out of my apartment ever. It turns out that I cemented my couch to my refrigerator and now the whole thing won't fit through the door." Fusing weird things together in your code will make "no way" the answer to "can we add feature X" way too often.

## Low Time to Comprehension

The last secret that I'll mention covers more ground than it may seem like at first. Frequently, I'll see advice on maintainable code that includes things like, "indent consistently" or, perhaps more profoundly, "take the time to think of good names." Yes, and yes. Definitely, both of these pieces of advice will serve you well.

But the broader concern here, particularly at the codebase level, has to do with the 0 to comprehension. Generic pieces of advice about code readability address the wide audience of developers and assume a relatively fluid influx and efflux of team members. But the maintainability of a particular codebase, maintained by a particular team at a particular point in time, will hinge heavily on how quickly that team understands the code.

Obviously, a critical factor here is the development labor effort. If I get a defect in my queue and trace it to some part of the code, then I'll have a fix more quickly when I understand the code more quickly. But low time to comprehend extends way beyond this simple concern. Absent barriers to comprehension, knowledge transfer and communication become simpler. The team benefits via more stability in general maintenance and development, and via a substantially increased likelihood of collaboration.

To put it another way, you'll spend a lot less money on a codebase where no one says, "oh, that's in Bob's code… you're going to have to take that up with Bob." Even assuming Bob can fix his own, inscrutable stuff quickly, the cost of ownership of that code includes the caveat, "and it gets a lot more expensive if Bob ever takes a vacation."

## You Maintain Codebases, Not Code

It may seem, to some extent, as though I'm quibbling. But I really don't think that's the case at all. Nobody maintains a method or six files of code -- they maintain applications.

Certainly applications consist of code, and certainly, that code being maintainable helps the application's maintenance footprint. And you should strive to keep any bit of code that you write clean and maintainable.

But don't lose sight of the real goal here. Understand that you need to think about the application and that you need to think about the cost of owning it in a whole variety of ways. When you start thinking that way, you'll find yourself in on the secrets of maintainable codebases.

The Agile Zone is brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile). Discover how to optimize your DevOps workflows with our [cloud-based automated testing infrastructure](https://dzone.com/go?i=121022&u=http%3A%2F%2Finfo.saucelabs.com%2FHow-to-Get-the-Most-out-of-CICD-Workflow.html%3Futm_campaign%3Ddevops%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-agile).
