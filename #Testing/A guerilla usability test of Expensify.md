# A guerilla usability test of Expensify

_Captured: 2016-10-27 at 12:46 from [medium.com](https://medium.com/tradecraft-traction/a-guerilla-usability-test-of-expensify-adf1087201ab?source=userActivityShare-c79006fee040-1477565149)_

![](https://cdn-images-2.medium.com/max/2000/1*lFx64r79BC7FBHv7TvmVLQ.jpeg)

## An exercise in simplifying business bureaucracy.

In 2010 I was working for the UK government, in a department that lived up to
bureaucratic expectations. IE6 was used by default, paperwork was king, and
expenses were submitted via a printed spreadsheet with stapled receipts. When
I moved to a startup in 2011, it was a relief to start using
[Expensify](https://www.expensify.com). With its simple dashboard and easy-to-
use app, expenses became a quick process rather than a painful time-suck.

Fast-forward 5 years and a couple of companies, and I returned to using
Expensify. The app had changed significantly, and a quick usability test
showed that what was once an easy-to-use product is now confusing to first
time users. I set out to investigate how the experience had changed and what
could be done to fix it.

* * *

### Design process

I used a four step design process to analyze Expensify:

![](https://cdn-images-2.medium.com/max/800/1*ReFwx462gNHepko_ZQGejg.png)

### Step 1: Understand users

#### **Persona development**

Meet Phil. Phil is a typical Expensify user: works in sales, travels a lot,
and doesn’t have much time.

Phil is fictional. Crafting his story helped me understand the mindset and
needs of Expensify users.

![](https://cdn-images-2.medium.com/max/800/1*KGtGdCNidX3UHV29rdsTEQ.png)

#### **Guerilla usability testing**

Using my provisional persona as a guide, I conducted guerilla usability
testing to identify pain points in the Expensify iPhone app.

> Guerilla testing is “the art of pouncing on lone people in cafes and public
spaces, [then] quickly filming them whilst they use a website for a couple of
minutes” — [uxbooth](http://www.uxbooth.com/articles/the-art-of-guerrilla-
usability-testing/)

Seven users were given a pre-defined scenario and asked to perform the
following tasks on an iPhone 6:

1\. File an expense with a receipt.  
 2. File an expense without a receipt.  
 3. Log a driving trip.  
 4. Submit a report.

### Step 2: Prioritize needs

After conducting the interviews, I analyzed and synthesized the feedback. I
wrote down each pain point then grouped them in to six distinct themes:

![](https://cdn-images-2.medium.com/max/600/1*UIvOoqh1g0r2lgCYDkLntA.jpeg)

![](https://cdn-images-2.medium.com/max/800/1*z0W9doYCt3lYDg9lZdzs8w.png)

Left: Pain points grouped by person. Right: Pain points grouped by theme.

I prioritized each pain point based on how important I perceived them to be to
users and to Expensify as a business:

![](https://cdn-images-2.medium.com/max/800/1*y9AezuW1H_QLSKRFuIxpZA.png)

### Steps 3: Ideate and prototype

The prioritization chart made it clear that there are two issues that are
pressing to users _and_ important to the business.

#### **Pain point 1: Users can’t work out how to file an expense.**

> “I would like to add an expense, but it doesn’t seem very feasible.”  
“I don’t know how I’m going to take a photo of this… nope, stuck.”

Most users eventually worked out how to file an expense, but all of them
struggled.

**Before:**

![](https://cdn-images-2.medium.com/max/1200/1*tfxDGbRB1Q2ypdftZgS7hg.png)

**After:  
**I recommend making the tab bar simpler and clearer. Add labels and make all expense options accessible from the “New Expense” button.

After sketching out different options and iterating based on feedback, I
designed the following:

![](https://cdn-images-2.medium.com/max/1200/1*s41W5gJrlXXI_nc97L4C-g.png)

#### Pain point 2: Users can’t work out how to submit a report.

> “I have no clue.”

The steps required to add expenses then submit them are convoluted and
confusing. I mapped out the basic flow to understand all the steps involved.

**Before:**

![](https://cdn-images-2.medium.com/max/800/1*rMs67qmo4WTjaJIDBdY6EA.png)

That’s a lot of steps!

The current flow seems to be modelled on the original paper expenses process.
Users create a report, add expenses to it one by one, then submit the report.
Submitting expenses digitally gives us the option to move a lot of this
complexity behind the scenes and out of the way of the user.

**Recommendation  
**I recommend that expenses are _automatically submitted_ at the end of a time period. The time period is defined by the company administrator or approver. For example, expenses could be auto-submitted as soon as they’re uploaded, once a week, or once a month.

If needed, expenses could continue to be grouped into “reports” based on the
meta data contained in each expense.

With this process change, the submission process can be drastically
simplified.

**After:**

![](https://cdn-images-2.medium.com/max/800/1*5X4tg3jLH8BwIXqR7PSupQ.png)

I translated this process change to the app design through an expense status
menu and messaging. The messaging explains when expenses will be submitted,
when they were submitted or when they were approved.

![](https://cdn-images-2.medium.com/max/1200/1*oFswVNJIyrIwf2cMi4311g.png)

### Step 4: Validate

The designs shown above were the result of sketching, testing, iterating, and
testing again. I re-tested the final design with five users.

#### Pain point 1: Users can’t work out how to file an expense.

> “That was pretty straightforward.”

All users were able to scan receipts, add manual expenses and log driving
trips with no problem.

#### **Pain point 2: Users can’t work out how to submit a report.**

Users weren’t immediately clear on what would happen next to expenses. After
exploring the app they understood the process, but I would like to do further
iterations to make it instantly understandable.

**Try out the new flow in the ****[interactive prototype**](https://marvelapp.com/2g2b747)**.**

### Next steps

Expensify is a great product, and much simpler and easier to use than any
other expenses product or process that I’ve tried. That said, I enjoy bringing
logic to complex processes and wanted to see if I could solve some of the
usability issues that my testing surfaced.

The designs I created aren’t the only way to solve the usability problems.
Further rounds of testing and iteration would generate and validate
alternative solutions. The submission flow and design in particular needs
further research and consideration. For example, I would be interested to see
if each expense could be submitted immediately on the user’s side, and grouped
for presentation to the approver.

Thanks for reading! I welcome any and all feedback on this process in the
comments or by email to [[email protected]](/cdn-cgi/l/email-protection)




