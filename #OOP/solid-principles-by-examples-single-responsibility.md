# SOLID Principles by Examples: Single Responsibility

_Captured: 2017-09-22 at 13:49 from [dzone.com](https://dzone.com/articles/solid-principles-by-examples-single-responsability?edition=325534&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202017-09-22)_

"[Automated Testing: The Glue That Holds DevOps Together"](https://dzone.com/go?i=236222&u=http%3A%2F%2Finfo.saucelabs.com%2FAutomated_Testing_Glue_LP-DZone.html%3Futm_medium%3Dpre-roll_textlink%26utm_content%3Darticle) to learn about the key role automated testing plays in a DevOps workflow, brought to you in partnership with Sauce Labs.

This blog post will explain with simple examples the **Single Responsibility Principle** of SOLID principles to better understand how we can improve our daily coding activities. In future posts, I'll cover the other four principles.

## The Definition

"A class should have only one reason to change."

Defined by Robert C. Martin in his book "Agile Software Development, Principles, Patterns, and Practices," it is the first of the five SOLID principles. What it states is very simple, however, achieving that simplicity is not so obvious.

Let's start with the classic example, an object that can save itself.

This class violates the SRP principles because it has more than one reason to change:

  * It can change because we want to add a specific attribute for a book- the year of the first edition, for example.
  * It can change because our database structure changes and we need to update the data operations, or because we want to save our book in an XML file format.

How do we change this situation?

We move the saving logic away from this class:

This principle can help us to design better procedures or functions, too. This method, for example, is doing too much. Because of that, the **SendAlert** class could change if the validation criteria changes, and that is not the main purpose of the class.
    
    
                if (!emailTo.Contains("blackListedDomain.com"))

We can refactor like this.
    
    
                if (!string.IsNullOrWhiteSpace(validationError))

This way, the AlertService class has only one reason to change, and it doesn't have to change if something in the validation logic changes.

## TL;DR

The primary benefit the Single Responsibility Principle gives you is high-cohesion, low-coupling code. Following the SRP minimizes the chance that one class will have to change for a given requirement, and maximizes the possibility that changing one class will not impact any other classes.

Happy coding!

[Learn about the importance of automated testing](https://dzone.com/go?i=236223&u=http%3A%2F%2Finfo.saucelabs.com%2FAutomated_Testing_Glue_LP-DZone.html%3Futm_medium%3Dpost-roll_textlink%26utm_content%3Darticle) as part of a healthy DevOps practice, brought to you in partnership with Sauce Labs.
