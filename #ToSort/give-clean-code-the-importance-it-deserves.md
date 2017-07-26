# Give Clean Code the Importance It Deserves

_Captured: 2017-04-15 at 22:14 from [dzone.com](https://dzone.com/articles/give-clean-code-the-importance-it-deserves?oid=twitter&utm_content=buffer17c6c&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

### Why is clean code important? How important is a programmer's native language in all this? How can stakeholders and programmers approach the matter? Let's explore.

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

## What Is Clean Code?

This is not a new topic at all, it has been addressed many times in the past but I thought it could be interesting to share my own experience with it. In my case, the experience of crafting software from Uruguay to the US has put to the test many of the things one reads about software development processes and best practices, one of them being the importance of clean coding.

## The Way of the Code Crafter

I had the opportunity to work with many different people in many different projects, and I've found that a lot of us (myself included) share a similar behavior at the beginning of our careers. When we go out into the programming world we just want to get a job done as soon as possible. It feels like we all get very anxious at the dawn of our careers. The minute we are told about the first requirement for the product we are building, we are picturing a solution and two seconds later we are on to it. We need to see it working, we connect the bits and pieces with the bare essentials, we hit the ground running, we see it happening in front of us. We did it!

This kind of programming "frenzy" we get into is the cause of many problems down the road. The thing is, programming is hard… at least "good" programming is hard. So, frenzy programming will rarely produce good code. What is good code? Well, it seems that when we begin our careers, good code is more related to things like performance, reliability, flexibility, etc., but not so much with code's readability. A couple of years down the road we come to appreciate the importance of writing code that is crystal clear. To me, good code has to be readable code. Don't take it as a necessary and sufficient condition, a readable piece of code can surely be bad, but if the code is unreadable then it can't be good.

So, what is readable code anyway? Quick answer: code that humans can easily understand. But how do we make it readable? How can we tell when we are writing readable code or not? Truth is, there is no quick answer. In the rest of this article, I am going to give you some ideas on how to go about writing readable code and why I think it is so important for programmers and business stakeholders. Let's begin with the "why." Why is clean code so important?

## Whose Product Is it Anyway?

In the business of custom software development, each product we create is our client's product, no doubt about that. They can do whatever they want with it, use it internally or sell it to somebody else, but most importantly they can extend or modify it themselves. To do that, what they need is to have the source code. So when we build software for our clients, we deliver not only the executable but the source code to them.

What if the code we gave them was incomprehensible by any other developer? Will they be able to extend or modify it later? Let's use an extreme example:

### Javascript Minification

Minification is a process in which a file is transformed into a very compact version of itself, by removing spaces and by replacing variable and function names with shorter character sets like this:

![Image title](https://dzone.com/storage/temp/4925089-picture1.jpg)

When we release a JavaScript file into production we want to have it minified, not only because it saves bandwidth (JavaScript files are shortened when minified) but because it also makes it really hard for others to reuse the logic embedded in the code. The structure of the code is the same as the original, but since we made variable names and method names meaningless, the logic is now almost impossible to understand. So, we are protecting (at a very basic level) the intellectual property of that piece of code by making it unreadable.

The point is, giving our clients unreadable source code for their products can be compared to giving them the minified versions of our files. They wouldn't be the actual owners of the product, would they? They wouldn't be able to understand the logic in order to extend or modify it. In fact, they would always need us to do any modification or extension to the product.

Even more so, what if the client comes back to us a year later to have the product modified and the team that worked on it is no longer available? Will another team be able to work on the product?

## Who Wrote This?!

90% of the time that a programmer is confronted for the first time with source code written by others, they won't approve of it. You will find them saying things like: "What is this thing doing here?!" "What is this for?!" "Where is this coming from?!" "Who wrote this?! I will find you!"

This is even more frequent when the code was written in a different context than that of the reviewing programmer. For example, when the code was created by people with a different native language or even from a different company.

In my context (UruIT), we work mostly with clients in the US and our native language is Spanish. Hence, we have to be extra careful with the way we name variables and methods so that our logic is clear for someone else (more on this later). I have experienced this from the other end when working with teams in Eastern Europe and Asia. Bad naming is the source of confusion and bad naming can be the result of not being proficient with the language. The bottom line is that developers need to have some minimum level of proficiency in English for their code to be expressive but succinct at the same time.

When programmers face the reality of having to work with "cryptic" code, their motivation drops significantly. Not to mention what happens if there are deadlines to meet. Reversing this situation is hard because you need your team motivated to do so and you need to give them time to get it done.

## Clean Code Matters

Making readable code is enabling continuity of the product. It makes it possible for someone else to continue our work and enjoy doing so. It means less "Who wrote this?!" kind of curses. The end result is better software with fewer bugs and that is easier to maintain.

For product stakeholders, remember that your custom built product is not really your product unless you can understand it's source code. Also, remember that developers get motivated when working with beautiful code. Give readability the priority it deserves by encouraging the team to take the time to get it right. For developers, readability will make development and maintenance much more enjoyable. It will help reduce bugs and help your teammates cover your back when you need to. Talk about it with your team so that everybody approaches this in the same manner (more on this later).

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
