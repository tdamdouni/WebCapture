# Scrum By Example – the Story of an Incomplete Sprint

_Captured: 2017-02-21 at 01:37 from [agilepainrelief.com](https://agilepainrelief.com/notesfromatooluser/2011/09/scrummaster-talesthe-story-of-an-incomplete-sprint.html?utm_content=bufferb23f4&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer#.WKuLoqS1Kf0)_

![missing piece](https://agilepainrelief.com/wp-content/uploads/2011/09/photodune-7068646-missing-puzzle-xs-200x300.jpg)

[Last time](http://agilepainrelief.com/notesfromatooluser/2011/07/the-scrummaster-tales.html) we met John (ScrumMaster) and the team, they had just discovered that their backlog had many large stories and no-estimates. The team delayed the start of their first sprint, did some [Product Backlog Grooming](http://www.romanpichler.com/blog/product-backlog/grooming-the-product-backlog/). When we meet them again their first sprint in is in progress.

# Story

Coming out of the planning meeting the team committed to five stories totalling 42 Story Points. Their overall Sprint Goal get the customer's book home:

  * As a book buyer I want to add my book to my shopping cart so that I can purchase it - **Story Points**: 13
  * As a book buyer I want to tell Amazon where I want my book shipped to so I can get it - **Story Points**: 8
  * As a book buyer I want to see the price for my books with shipping and tax so I can see whether I'm ok with the price - **Story Points**: 3
  * As a book buyer I want to choose my payment type (MasterCard, Visa, Amex or Paypal) so that I can pay for my book(s) - **Story Points**: 3
  * As a book buyer I want to pay for my book(s) so I can get it home - **Story Points**: 13
  * As a book buyer I want a confirmation message so I can see that the purchase was successful - **Story Points**: 2

The team (7 team members including John) started work on the first four stories right away (27 Story Points in total). Tonia the team's on QA specialist spent the first few days with Brad (the BA) clarifying the acceptance criteria for the stories and designing her manual test cases. She also worked with a couple of developers to clarify the details of the stories. By Monday (Day 5 of the Sprint) she had completed all of this work and was hungry for an application to test. In fact she was wondering why she hadn't seen it as promised on Friday. Lacking an application to test she found other things to do outside the team. It wasn't until Wednesday (Day 7) that she finally had the first story ("add my book to my shopping cart") ready for test. Tonia scrambled but it was a big story and took much of the day just to get the environment ready to test. By day's end she had found a dozen issues and shared them with Ian. "Add my book to my shopping cart" was clearly not ready yet. In the meantime other stories were piling up in front of Tonia and she was unable to keep up with the testing. At the end of the Sprint Sue only accepted two stories as complete "see the price for my books with shipping and tax" and "choose my payment type" for a total of 5 Story Points. Everything else was incomplete.

In the retrospective the team identified a number of things that contributed to the problem:

  * They over-committed
  * They took on large stories with splitting them down more
  * They had too much work in progress

For the next sprint they identified several improvements they could make:

  * Always split stories of size 13 or larger
  * Never have more 3 stories in progress at once (that forces people to collaborate on Stories)
  * Handoff incomplete Stories for early testing. Early feedback on partially complete work will help save team members going down many dead ends.
  * When working on larger stories 5 and 8 swarm them

# Analysis

Nearly every time I've seen a team take on a story of 13 points or more the team doesn't succeed in completing it in that Sprint. Usually because stories of that size have alot of hidden complexity and surprises.

I've also noticed that limiting the number of stories in progress to less than half the team size i.e.

**Team Size**
**Limit on # of Stories in Progress**

5
2

6
3

7
3

8
4

9
4

Helps ensure that work is completed before new work is started. Kanban folk achieve the same effect by setting up their Kanban board and setting WIP limits.

Finally when a team is new and is having trouble seeing the effects I create a simple table on a white board:

**Story Points by Day**

M
T
W
T
F
M
T
W
T
F

**Development**
27
27
27
27
27
27
27
14
9
9

**QA**
0
0
0
0
0
0
0
13
18
9

N.B. The QA/Development split isn't meant to encourage this to happen its just a reflection of what most teams deal with when they first start.

Combined with a Sprint Burndown (in Story Points) it help the team spot problems as they start to happen and diagnose them in the Retrospective.

What tools do you use to help teams see these problems?
