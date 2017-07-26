# Project: Turning a New Feature into Agile Stories and Pseudocode

_Captured: 2015-10-14 at 23:20 from [www.vikingcodeschool.com](http://www.vikingcodeschool.com/software-engineering-basics/turning-a-new-feature-into-agile-stories-and-pseudocode)_

##  Taking a new feature for the Viking Store e-commerce site and breaking it down into bite-sized stories and pseudocode. 

## Adding Pagination to the "Viking Store" E-Commerce App

Over the past few sections, you've learned about how an engineer breaks down problems, how to operate within an Agile Development framework like SCRUM and how to turn logical thought into pseudocode. You'll use all of these things in this project!

### Outline

You've no doubt used websites that need to display a large number of results and, instead of showing them all on one giant page, they break them into many pages. This is called **pagination**, and it might look like:

![pagination example](http://s3.amazonaws.com/viking_education/web_development/prep_engineering/pagination_example.png)

> _pagination example_

Think it sounds like an easy thing to pull off? Then this should be a quick project for you...

For this exercise you are assuming the role of a developer working on the Viking Store e-commerce app that you originally broke into user stories during [the assignment on Agile Stories](http://www.vikingcodeschool.com/software-engineering-basics/stories-for-the-e-commerce-app). You may not know how to code yet, but that's irrelevant right now -- you know how to solve problems! You can fill in the code later.

The early version of the Viking Store website has been making lots of sales and they now have more inventory than they used to so it doesn't all fit well on one product listing page. The owners would like you to set up pagination at the bottom of the products page so they can keep adding new products without making a mess of the main page.

Your developer partner said she would implement the code to display the correct number of products based on which page you're on but you need to come up with the code to actually make the pagination links display properly at the bottom of each page so the user can jump between pages.

### Feature Specification

The UX designer had been out drinking ale with the warriors the night before so he didn't really specify all the states that would be necessary or even provide you with a good mockup. He just said,

"Make sure you **show at least the page to either side of the current page** and that you are **always showing at least the first two and last two pages as numbers**. Make sure you use ellipses (...) whenever you skip numbers"

He went online and forwarded you the following email with the subject line, "Like this! You figure out the rest." before falling asleep at his desk:

> What a crazy night! Some examples of what we're looking for:
> 
> **On the first page:**
> 
> **On a random middle page:**
> 
> **On the last page:**
> 
> The link to the source of these images [is right here](http://www.eriktrautman.com/blog?page=16) if you want to play around with the page. 
> 
> I'm going to take a nap. Good Luck!

## Task 1: Break out the User Stories

The Product Manager had his sheep stolen by a raiding party from the next village so he's busy. He asks you to take care of creating the user stories around the feature. This isn't the first time his sheep have caused trouble so you've become pretty good at handling user stories yourself.

For this task you will need to:

  1. Think through the intended purpose of the feature and really try to understand it. What is the user trying to do with this feature? How many stories does that really represent?
  2. Add any necessary stories to your existing Pivotal Tracker project. Put these new ones at the top of the list (since the old ones will not be necessary here and can be dragged into the "Icebox" section).
  3. Make sure you think about the Acceptance Criteria for these stories -- the edge cases they cover will govern how much logic you'll have to implement later!
  4. Prioritize the stories based on achieving the easiest minimum functionality as soon as possible and then layering other stories on top of that. Hint: Next/Previous links might be a good start.
  5. For each story, estimate how much work should be required and set its points.

## Task 2: Pseudocode Each Story

Now you can go back to wearing your developer hat. Your job is to "implement" each story as if you were developing it, though you'll actually just design the solution using pseudocode instead. This "code" will govern how the pagination shows up in different situations (e.g. depending which page you are currently on) in the browser.

Follow the stories in the order of priority and mark them "finished" or "delivered" when you're done! As you work, you may need to update the stories (especially the Acceptance Criteria). That's normal and expected.

Your pseudocode will need to tell the computer:

  1. Which words or numbers to display, e.g. "3" or "Previous"
  2. Whether those words should have links attached to them (and what the links point to)
  3. Whether there should be ellipses (...) or not between numbers

### Important Things to Know

As with the elevator assignment before, there are some things you'll need to know about what kinds of information is available to you. You can make the following assumptions:

  1. You know what page you're currently on.
  2. You can ask if you're on the first or last page.
  3. You know how many total pages there are
  4. You have a list of all the available page numbers that you can cycle through if necessary.
  5. You're allowed to ask your server side code for the links to the "next" page, "previous" page and any numbered page (e.g. page 4).
  6. You will need to specify whether to add a link to a number (making it blue and active) or not (making it normal black). See the screenshots for examples.
  7. The sequence of the words / numbers is important but you don't need to write any logic about where exactly to place them 

### Scenarios to Think About

To get you started thinking about the different cases that are possible, make sure you can gracefully cover the following scenarios:

  1. You are on the first page
  2. You are on the last page
  3. You only have one page
  4. You are in the middle pages somewhere
  5. You are on the third page but there are only
  6. Any other scenarios where the unexpected might occur (and there are some)!

### A Gentle Nudge

In case you aren't really sure what this all means, we'll get you started with the following framework:
    
    
    PROGRAM DisplayPagination:
        Display the "Previous" word or link
        For EACH number in the list of pages DO
            # Your pseudocode or calls to other program modules here!
        END
        Display the "Next" word or link
    END
    
    PROGRAM DisplayPreviousWordOrLink:
        IF the current page is the first page THEN
            Print the word "Previous"
        ELSE
            Print the word "Previous" with a link to the previous lesson
        END
    END
    
    # Your other modules here!
    
    PROGRAM DisplayNext:
        # Your pseudocode here.
    END
    

## Checking Your Work

You won't be able to check your work using the computer like you normally would. In this case, you'll have to set up each of the required scenarios and edge cases in your head and walk through your "code" to see if it works out correctly. It's good practice for debugging later on and is also a great skill to have during interviews.

Okay, that's enough help... go do it!
