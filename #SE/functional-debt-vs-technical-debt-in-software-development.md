# Functional Debt vs Technical Debt in Software Development

_Captured: 2017-12-12 at 14:03 from [dzone.com](https://dzone.com/articles/functional-debt-vs-technical-debt-in-software-deve?edition=342131&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=agile%202017-12-12)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

Probably every person who has ever been involved in software development is familiar with the term **_Technical Debt_**. It is a brilliant metaphor that was brought from the financial world and that represents the behavior of code maintenance and scalability over time. I would like to talk today about software debt, including both **_functional debt_ **and** _technical debt_**.

## Technical Debt 

Whenever you are forced to leave some parts of your code with a 'To Do,' 'Refactor,' or 'Review Later' mark, it's an additional piece of debt you acquire. This way you buy yourself some time. You meet the deadline, you launch the product on time, and you have a prototype to show for an investment round. But you can't forget about the cutbacks made in code quality because it's your debt. It's something you owe, it's something you need to pay back.

If you ignore it and continue to build upon it, your product will progressively become less stable and less scalable and its maintenance cost will skyrocket. To keep the analogy with the real world, it's like taking a new loan to pay back the one you took earlier, repeatedly.

At first, things seem to work fine. But as the loan grows to cover the interests and other expenses, it's like a rolling snowball that you just can't stop. This is why it is important to allocate the needed time to refactor and even sometimes to rebuild the marked parts of your code.

Even though we are very familiar with this situation, we've found a workaround to achieve both the _Time_ (deliver on time) and avoid the _Technical Debt_. But as a result, in the very end, we get a new form of debt. Something I like to call **_Functional Debt_**.

## Functional Debt

I did some research on this idea and I found just a few references to this phenomenon, and to be honest, it was never the way I personally see it. In [this article](http://www.agileinsider.org/2009/09/functional-debt/) by Mark Barnes, it is described as the unfulfillment of the **YAGNI **principle. This is when we choose a very heavy and powerful framework for what should be a 'lightweight' and small project. When the functionality we offer overpasses the functionality we need, the development and maintenance of those extras becomes _Functional Debt_.

When I picture Functional Debt, it's not exactly what I think about. The way I see it is that in order to deliver it on time, the functionality is only partially implemented. The functionality itself suffers from cutbacks. Let's say that we need to deliver a simple form with a few fields and file input. As we are tight on time and we don't want to introduce Technical Debt, we decide to 'simplify' the functionality. We eliminate the 'drag and drop' for the file attachment, support for multiple files, and the fields' verifications on the legitimacy of the introduced data.

Our application works perfectly fine, the code is clean (the parts that are present don't need to be modified), and we deliver it on time. It is a miracle. Well, it's not. By doing this, we keep invalid data in our database and the user experience is not good enough. Our code is spotless and does exactly what we expect. We don't have Technical Debt. Our debt is Functional.

Later on, we will have to come back to this form, and add new parts, integrate a validation service, and change the UI. As time passes, the development team will no longer recall exactly what is missing. They will need time to study what has to be done, and they will need to deal with the _toxic _data that we allowed in our database. The time invested here is much higher than the time needed to implement the full functionality in the first place. It's the fee we pay, the pay off of our debt. Its effects are less harmful than the Technical Debt's effects, yet they still need to be watched and taken care off.

The developer that exposes situations like the one described above is often seen as the enemy of productivity as he asks for time to work on something that is already working. It is beneficial to stop for a moment and think about the possible Functional Debt we might be creating, as it might save us a headache or two.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
