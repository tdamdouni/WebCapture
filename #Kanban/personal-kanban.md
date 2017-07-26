# Personal Kanban

_Captured: 2017-05-07 at 11:00 from [hackernoon.com](https://hackernoon.com/personal-kanban-11f6a5196b00)_

![](https://cdn-images-1.medium.com/freeze/max/30/1*XQxWW_v685cJksr2F2ZLNg.png?q=20)![](https://cdn-images-1.medium.com/max/1000/1*XQxWW_v685cJksr2F2ZLNg.png)

Kanban is a great planning method to visualize simple productivity processes. And it's not just for teams, it's also extremely useful as a personal board for any kind of project.

To get started you can use free tools like [Trello](http://trello.com/) or even a whiteboard with sticky notes. If you have multiple projects you are working on, I recommend to create multiple boards. One for each project. As an exception smaller projects could be summarized into a single board. It really depends on a number of todos and information you have to deal with. You get the best use out of Kanban when you don't fill it up with too many things -- as with most tools.

Let's start! Create multiple lists or columns from left to right:

  * **Inbox** (or backlog) = collect here every idea, feature request, bugs or all the unprocessed "stuff". Means you don't have to prioritize or put it into a specific category. It's just a place to dump whatever is coming your way for later review. So you don't have to deal with it now. This list could contain an unlimited amount of items. But you should review and purge regularly everything you don't really need anymore.
  * **Next Up** = All the things which you want to do next. This is a kind of general action list. Put here the stuff, which is important in near term for you and which you have "validated" as something worth doing. You can pull items from "Inbox" into this list. This list should have a limit of 5-10 items.
  * **Doing Now** = The name says it. Keep things here, which you are working on right now. You will pull cards from "Next Up" into this list when you are done with what you were doing last. Keep a very tight limit here of 1-3 cards. That's like a focused Action List.
  * **Done** = Once the task is finished, you can pull and park the task here. This is just a temporary place for the next review. Once you do your review, you can archive all the cards inside this list.
  * **Trash** = This is a place for all the cards which became irrelevant. Since you note down almost everything into your inbox, many things might not be considered as something worth doing. You can park those items here until the next review. Just like the done list purge this list also regularly. Avoid keeping around cards with little information and low impact outcome. They create noise in your system and make it harder to manage. If it turns out to be important in the future, it will come up again. Then you can dig out of your archive or create a new card.

**Bigger Projects**

If you have bigger projects, you might add more lists, like I did above for developing NotePlan. Instead of "Next Up", I have made two lists: "Later" (limit = 20), "Soon" (limit = 10).

Instead of using "Later" and "Soon" this could be also split up into a rough estimate, such as "This Month", "This Quarter", "This Year", "Some Day", etc. It depends on how many cards you have and how many you really want to manage. It also depends, if you have a team, which works on the cards. Kanban is very flexible. You can add a new list anytime and fine-tune your workflow.

For example: If you test a software release before uploading it to the public, you can add a list "Test" before moving cards to "Done". Or "Code Review" or just a general "Review", if it's not a software project.

If you are using Trello, I recommend the chrome extension [WIP](https://chrome.google.com/webstore/detail/kanban-wip-for-trello/oekefjibcnongmmmmkdiofgeppfkmdii) to create a card limit for your lists.

#### Some important points to keep things working

  * Limit the number of cards for each list (like 10-20). Also called "Work in Progress" Limit.
  * Limit the length of the card's title (like max. ~140 characters)
  * Add any extra information inside the card's description or as a comment, if the software you are using supports that.
  * Review your cards regularly (more on that later).

#### For "Product People": Capturing Feedback

If you work on any kind of product, you will have feedback from your customers. Copy this feedback in its raw form and paste it into a card as a reference (for example into the comments section).

This will help you in multiple ways:

  1. You will have an overview of who and how many people are speaking about a certain part of your product -- feature, bug or more general problems. This gives you an idea how important a feature for example is and where you should focus on.
  2. It helps your development team (or yourself, if you are the developer) to find the best solution and reading the raw feedback makes it easier to understand the pain. Furthermore, it's more motivating to read feedback, which came directly from a real customer instead of receiving something processed. The raw, unbiased version is very useful to uncover simple solutions to complicated sounding problems (once you figure out what the actual problem is).

#### Tagging

Use colored tagging to create categories of tasks. Such as "Bugs", "Marketing", "Design" or "Support".

This helps you prioritizing cards on-the-fly and important things won't get drowned so easily between the less important cards. Above I have tagged critical features, bugs and marketing activities. I don't tag every card, only the significant ones.

#### Reviews

Like in any other productivity system, it's important to review cards and clean up the system to keep an overview. Here every 1-2 weeks all cards should be reviewed, re-prioritized, purged and updated. If you don't review and clean up, you will end up with a dozen old cards, which will never be finished or which are not really actionable and actually belong somewhere else. They create noise and make it harder to keep an eye on the things, which are critical for you. Eventually, you will probably stop using the system altogether, because it will confuse you more than help. Hence review all cards to keep your boards healthy.

#### List Based Systems And Kanban

Compared to a purely list-based system (taggable lists with todos), Kanban can visualize a workflow much better. In this example the Kanban board replaces the project related notes for the development part. But Kanban boards are really bad for storing reference material like long pieces of text, spread-sheets, checklists, specs, etc. Basically anything with a lot of content or anything which creates a lot of cards, which are not very actionable. If the new information doesn't fit into your Kanban workflow, it doesn't fit into your Kanban system. Hence it makes sense to keep a list based system for storing non-actionable items and a Kanban board to visualize your workflow.

I personally moved managing the development of NotePlan from a simple text-based list to Trello, because I needed something more dynamic, where I can move around blocks of text (or cards) much easier. It's also hard to visualize your workflow inside lists.
