# Duplicate Code Isn't That Bad

_Captured: 2017-04-17 at 21:20 from [dzone.com](https://dzone.com/articles/duplicate-code-isnt-that-bad?edition=291881&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-17)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

Duplicate code isn't something we want in our code for various reasons. Clearly, the straightforward reason is changing the duplicate code. You need to find the same code piece everywhere it's used and replace them all. A more complicated reason is the proper use of [design principles](http://www.oodesign.com/design-principles.html). Although it's hard to argue against any of the reasons, I still think duplicate code can be fine.

Duplicate code can make your code more readable and understandable. We all know the duplicate code goes against the old "don't repeat yourself" rule; however, our goal isn't really DRY. DRY and other principles are tools to achieve maintainability and readability. As we have a more readable and understandable code, then we have better readability and maintainability. By far the best example for this purpose is setting up code for testing. You could possibly create a function but it would be hard to go to that function to check what's populated. My example is as follows:

So, I can see two functions here. One for creating a dog and the other for creating a human. Nonetheless, this is much more readable than using functions. So, I prefer to let this duplicate code stay as is for a while.

Removing duplicate code immediately is a premature optimization. In many cases, focusing on just the duplication will make things worse or lead to complex code. It's wiser to try to keep your code clean and tested. At some point, there will be a refactoring opportunity to remove duplicates. Let's look at the example for this:
    
    
      let total = base + bonus + overtime;

In the example, one can create a function for overachieving salary. Moreover, once can create overtime salary by calling simple salary. Nevertheless, I think it's early. We can still tolerate this for a while. I like my code base to mature a little bit. Note that we have tests in place to ensure these two functions work correctly. Let's see how this might evolve. We'll add another function to calculate salary after tax. I think this is the moment to do the refactor.
    
    
      let tax = isBonus ? (salary * TAX_ON_BONUS) / 100 :  (salary * TAX_ON_BASE) / 100;
    
    
      let totalSalary = calculateAfterTax(base, false) + calculateBonusAfterTax(bonus, isOverAchieving);
    
    
        totalAfterTax += calculateTax(bonus * OVER_ACHIEVING_PERCENT / 100, true);

Consequently, I think we can live with duplicate code for a while and maybe more. Granted duplicate code is against design principles, but these principles aren't really the goal. Our goal is to deliver maintainable and understandable code. We should allow some time for duplicate code to mature.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
