# Lifecycle of a User Story

_Captured: 2017-07-31 at 22:22 from [agilepainrelief.com](https://agilepainrelief.com/notesfromatooluser/2013/11/lifecycle-of-a-user-story.html?utm_content=bufferc70aa&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer#.WX-RWaCbGaM)_

![Life Cycle from: http://askabiologist.asu.edu/monarch-life-cycle](https://3hppfzjby0g1sxwjng1f4h1c-wpengine.netdna-ssl.com/wp-content/uploads/2013/11/LifeCycle.png)

[User Stories](http://agileatlas.org/articles/item/user-stories) are often used as a lightweight form of Agile requirement. Their goal is to replace heavy weight-specification documents with "a Card, a Conversation and a Confirmation". When people first discover User Stories it's hard to see how they work because we often take a static viewpoint - i.e. we only see them at Release Planning or during implementation. We're left with many questions: Where do User Stories come from? When are they created? Who is involved in their creation?

To illustrate this I will use vignettes from the WorldsSmallestOnlineBookStore. Each vignette will show what happened to one User Story.

_"As a frequent book buyer I want to save my address so that I don't have to retype it every time I visit the bookstore"_

During the team's first Release Planning Session (aka Initial Product Backlog Refinement) this Story was identified. After a few rounds of planning poker the consensus estimate was that it was size 20, allowing for both the initial entry of the address, updating and deleting old addresses. Since this Story appeared to be low priority in the short term, the team moved to other items.

….

In Sprint #5, during a Backlog Refinement session, the PO Sue revisited the Story and asked the team if their understanding of the problem had changed in the past two months. They conferred for a few minutes and decided that it was still a 20. Sue grumbled and suggested it was a fairly small piece of functionality for such a large number. Doug suggested a Story split - using CRUD (Create Read Update Delete), he proposed in the short term that the User be allowed to add a new address and use it. However, they wouldn't be able to update and delete. This would separate the Stories. After a few minutes of conversation around the implications Sue asks them to estimate the three split Stories:

_"As a frequent book buyer I want to save my address so that I don't have to retype it every time I visit the bookstore."_

_"As a frequent book buyer I want to delete old addresses so that I don't have to worry that my books will ship to the wrong house."_

_"As a frequent book buyer I want to update my existing address to correct small errors so that I don't have to retype them from scratch."_

The team determines the "save address" Story is size 8, the "delete address" Story size 5, and the "update address" Story size 8. Based on this Sue moves the "save address" Story to the top of the Product Backlog, "delete address" about 15 items further down and "update address" has been moved so far down it will never be tackled.

Since the slimmer "save address" is now the top Story in the Product Backlog without acceptance criteria, the team spends a few minutes creating criteria for it. They start off by drawing a quick pencil sketch to get the key points across. Based on this sketch they start creating a table of examples:

1 Sussex Drive, Ottawa, Ontario, Canada, K2K 010
Valid

Buckingham Palace, London, UK
Address outside of Canada/US

1600 Pennsylvania Avenue NWWashington, DC 20500
Valid

Rather than try to create an exhaustive list at this point they just create enough to outline the boundaries of the problem.

During the team's next Sprint Planning session, Sue asks if the team can commit to this Story. They give it the "thumbs up".

Before the team starts work on the Story, Tonia (QA specialist), Brad (BA), Doug (Developer) and Ian (Developer) meet to finish hammering out the acceptance criteria.

915 E 7th St. Apt 6LBrooklyn NY 11230
Valid

24 Willie Mays Plaza, San Francisco, CA 94107
Valid

24 Willie Mays Plaza, San Francisco, CA
No Postal Code

24 Willie Mays Plaza, San Francisco, 94107
No State

45 Rosenfeld CrOttawa, ONK2K 2L2
Valid

45 Rosenfeld Cr, Ottawa, ONK2K 2L2
Valid

45 Rosenfeld CrOttawa, ONK2K 222
Invalid Postal Code

45 Rosenfeld Cr, Ottawa, ON
Missing Postal Code

….

(This style is referred to as [Specification By Example](http://en.wikipedia.org/wiki/Specification_by_example) - where the emphasis is that it provides the specification before something is built).

Brad goes off to see if there are any edge cases that the examples don't cover. Ian and Tonia pair off to turn the examples into Executable Specifications (i.e. acceptance tests) in [Fitnesse](http://fitnesse.org/)[[1]](https://agilepainrelief.com/notesfromatooluser/2013/11/lifecycle-of-a-user-story.html?utm_content=bufferc70aa&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer). Doug starts to take a crack at the GUI, seeing what parts he will need to assemble. Once the initial tests are written Ian tries build the business logic to support the examples.

A few days later when Ian and Doug think they've completed the Story and it meets the examples, they show it to Tonia. Once she sees that satisfies the test cases she spends a while doing some exploratory testing - seeing how the application behaves when a real User plays with it. Satisfied, she calls Sue over for additional feedback. Sue is delighted with the behavior but asks for a few changes to the layout. Once those are made she agrees the Story will be complete.

During the Sprint Ian demonstrates the different ways we can now support accepting addresses from both Canada and the United States.

At the end of the Sprint the team takes the completed Story off the wall and archive it in the filing cabinet (they keep them around for later auditing).

------

During Sprint #6, Brad (BA) sees Ian (Developer) in the hallway and they start chatting about the warehouse runners, i.e. the people who fill the book orders. Brad comments he's seen the runners spend a lot of time retracing their steps because the list of books in for an order is alphabetical - but unfortunately the warehouse isn't laid out in alphabetical order. They create a new Story:

"_As a runner I want the list of books to be printed in the same order I will find them in the warehouse so I don't have to run as far_"

During the [Backlog Refinement session](http://agileatlas.org/atlas/scrum#backlog-refinement) a few days later they bring up the Story. Sue gives it some thought and says, "We're in the fourth month of operations, and we're only just starting to see reasonable sales numbers roll in. All improvements right now must be focused on the book buyers and making it easier for them to buy books. At this stage I can't afford to do any work for the warehouse runners or any other back office staff. Once sales start to increase we can afford to improve the system for our internal Users". Sue took the index card that the Story was written on and ripped it up.

----

User Stories aren't static, one-sentence descriptions written by one person. The User Story is most effective as a tool when several people are involved in its creation. They work as a tool to record the team's share, understanding not as a one-way missive from the Product Owner. In addition a good User Story evolves over time - as the team gains a greater understanding of the business problem they rewrite it, split it and add acceptance criteria.

_Lifecycle image via Wikimedia Commons_
