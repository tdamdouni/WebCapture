# How to Deal With Legacy Code

_Captured: 2018-06-29 at 19:40 from [dzone.com](https://dzone.com/articles/lets-deal-with-legacy-code?edition=382219&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-06-29)_

This article is in continuation with the [previous article](https://dzone.com/articles/lets-define-legacy-code) where we defined some of the key aspects of legacy code. In this article, we will take a look at legacy code and add a new feature to it.

But, before we begin with an example, let's take a moment to understand the broken window theory.

## Broken Window Theory

The broken window theory was proposed by James Q. Wilson and George Kelling in 1982 that used broken windows as a metaphor for a disorder within neighborhoods.

> One broken window, if left unrepaired for a substantial amount of time, instills a sense of abandonment. So another window gets broken. People start littering. Graffiti appears. Serious structural damage begins. In a relatively short time, the building becomes damaged beyond the owner's desire to fix it, and the sense of abandonment becomes reality. 

Let's not abandon our code; let's repair the code as soon as we get an opportunity to repair it. Let's not get ourselves into a situation where the damage is beyond our capacity to fix. Now, let's see our theory in action.

## Problem Definition Overview

The following code belongs to a hypothetical application called "Movie Rental." This hypothetical app allows customers to rent either a regular or a children's movies for a fixed number of days. The application also allows generation of a statement that the business calls the "Text Statement." This application has been running in production for a long time without issues and has become very popular. Now, businesses want to generate an HTML statement with the exact same logic for the amount computation.
    
    
        private List<Rental> rentals = new ArrayList<>();
    
    
            String result = "Rental Record for " + getName() + "\n";
    
    
                        if (each.getDaysRented() < 2)
    
    
                            thisAmount += (each.getDaysRented() - 2) * 1.5;
    
    
                        if (each.getDaysRented() < 3)
    
    
                            thisAmount += (each.getDaysRented() - 3) * 1.5;
    
    
                result += "\t" + each.getMovie().getTitle() + "\t" +
    
    
            result += "Amount owed is " + String.valueOf(totalAmount) + "\n";

The team decides to discuss the different ways to handle this new requirement in legacy code.

And, the team agrees to improve the code before implementing the new functionality. In this example, Scott and Jessica will be pairing on this.

But, where do they start?

As mentioned in their discussion, they need to understand the code first, so they decide to write characterization test(s).

## First Characterization Test

Scott: How many tests should we write?

Jessica: Let's look at the code. It should give us some hints.

Scott: I get it. We need a few rentals consisting of regular and children's movies and the number of days rented that were greater than 2 or 3. So, one test should cover a **decent** functionality.

Jessica: I couldn't agree more. So, let's write it then.
    
    
            Rental rental1     = new Rental(regular, 3);  
    
    
            Rental rental2     = new Rental(children, 4);
    
    
            String statement = john.statement();

Scott: Let's run this and see it fail.

Jessica: Great. We have made some progress. Let's correct our test.
    
    
            Rental rental1     = new Rental(regular, 3);
    
    
            Rental rental2     = new Rental(children, 4);

Jessica and Scott agree to write one test case covering a decent portion of the code. If this gives us confidence, we can live with one test for now. Otherwisee, we can write a few more or include movies with daysRented < 2.

Scott: Jessica, what type of test should a characterization test be? Unit, Functional, or Integration?

Jessica: Scott, it is not always possible to write unit or functional tests for legacy code. You might end up writing an integration test, to begin with, because you just want to know what the system does. But, as soon as you get an opportunity, write your tests closer to the code.

Scott: Sure Jessica, let's begin with the fun part. Let's fix a broken window.

## Refactoring

Scott: Where do we start from?

Jessica: I believe that the `statement()` method is a long method. We should try and make it a little shorter.

Scott: Agreed.

Jessica and Scott agreed that `statement()` method is a long method. But, this agreement was not based on the number of lines in the method. It was based on how easy it is to comprehend the method and that the method was doing more than one thing at a time, which it can be decomposed further.

Jessica: Switch statement has gone out and the extracted amount() method does one thing which is getting an amount for a given rental.

Scott: Let's continue refactoring. I am in a mood to clean up everything.

Jessica: Hold on Scott, we need to run tests before we move on.

And, the test ran successfully.

While working with legacy code, it is important to take smaller steps and follow the refactoring cycle. Refactor --> Run Tests --> Refactor

Scott: Sure. Jessica. Are we in a position to remove the comment, "determine amounts for each line" from the previous code?

Jessica: Yes, we can remove it.

Remove comments from the legacy code when you have captured their complete essence. Though I did take some liberty to rename variables along with removing a comment, it is always ideal to take smaller steps when you are beginning to understand legacy code. As you grow in confidence, you might want to take bigger steps, but if you have one test failure, the reality reveals itself.

Scott: Let's look at the `amount()` method. It depends on `priceCode` from the movie, but it is placed in `Customer`. We should move this method to the place where it belongs.

Jessica: Yes, let's do a few method movements (in the interest of this article).

I did a few movements. I moved the `amount()` method to `Rental `and then to `Movie` and ran the tests. It should be noted that this is our first opportunity to write unit tests for `Rental` and ` Movie` . I won't, for this article, but I assume you will.

Scott: Jessica, I have a question. `Movie` has a switch statement based on different types of movies. Shall we introduce some polymorphism here?

Jessica: I don't think it is coming in our way of implementing HTML statement functionality.

Scott has raised a valid point, but we need to remember one thing, "we refactor the code that comes in our way." At this point in time, we need to implement an HTML statement and switch the code that does not come in the way of our new feature, neither do the magic numbers 2 or 1.5. If you want to continue with small refactorings that are not coming in your way, for example, changing Magic Numbers to Constants, go ahead and do it, but do not move away from your actual task that is implementing the HTML statement.

Scott: I get that. Thank you. The `statement()` method in `Customer` is short enough. Shall we pause our refactoring here?

Jessica: We could, but one thing that is bothering me is that the method seems to be generating three parts of the statement and I can see it clearly -- header, body, and footer. If the effort is not huge, we should try and extract this code into different methods.

Scott: You clearly have an eye for refactoring. Let's do it.

I cheated again. I ended up doing a lot more than what I should have done -- renamed methods to be **text*,** duplicated for loops (over rentals) to calculate `totalAmount()`, and repeated the same in `textBody().`

Is that justified? Well, how many rentals do we expect to have for a customer? What is the cost of iterating over them twice? If it is not significant, go ahead and use it. Most of the times premature optimization results in a complicated code.

Jessica: Now that we are done with refactoring, we can introduce HTML statement functionality.

Jessica and Scott are comfortable now. They have refactored, gained a fair understanding of the code, and can introduce the new functionality.

## Conclusion

Jessica and Scott went on to implement HTML functionality (with tests) and they did a lot to clean up the existing code. This is much more understandable that it used to be.

They might not have cleaned up everything, but they clearly have left a great deal of understanding trace for others to follow.

They followed Cover and Modify, Boy Scout rule, Refactoring Cycle, and refactored enough to finish the new functionality. In short, they handled legacy code like professionals.

## References
