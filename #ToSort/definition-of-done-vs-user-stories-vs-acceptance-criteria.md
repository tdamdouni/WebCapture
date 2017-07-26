# Definition of Done vs. User Stories vs. Acceptance Criteria

_Captured: 2017-05-31 at 19:25 from [agilepainrelief.com](https://agilepainrelief.com/notesfromatooluser/2017/05/definition-of-done-vs-user-stories-vs-acceptance-criteria.html#.WS8KioW1KaM)_

## Definition of "Done"

The [ScrumGuide](http://www.scrumguides.org/docs/scrumguide/v1/scrum-guide-us.pdf) says that:

> "When a Product Backlog item or an Increment is described as 'Done', everyone must understand what 'Done' means."

I can promise you, that sentence and the paragraphs that follow are the most poorly understood aspects of the ScrumGuide.

The definition of "Done" exists to ensure that the Development Team agree about the quality of work they're attempting to produce, whereby "Done" becomes a checklist that is used to check **each** Product Backlog Item (aka PBI) or User Story for completeness. When Scrum is used as intended, "Done" is our tool for ensuring that we're ready to release at the end of every Sprint (minimum), or continuously through the Sprint (modern preference).

The goals of "Done" are:

  * to build a common understanding within the Team about Quality and Completeness
  * to be a checklist that User Stories (or PBIs) are checked against
  * to ensure the increment shipped at the end of the Sprint has high quality and that the quality is well understood by all involved.![done](https://agilepainrelief.com/wp-content/uploads/2010/12/photodune-8431094-done-text-and-check-mark-xs.jpg)

"Done" is structured as a list of items, each one used to validate a Story or PBI. Items in "Done" are intended to be applicable to all items in the Product Backlog, not just a single User Story.

##### Example Definition of "Done":

(Simplified) from the World's Smallest Online Bookstore

**Item**

Whenever changes are made to existing code, a Unit Test is written to cover that method

Usability Review Completed

Tested on iPad, iPhone and Android Phone

Performance Tests run

Code Peer Reviewed (if not written using Pair Programming)

So "Done" differs from Acceptance Criteria because "Done" is intended to be universally applicable. It also differs in that it has a formal definition, whereas Scrum doesn't require either User Stories or Acceptance Criteria to be used, so they have none. User Stories encapsulate Acceptance Criteria.

## User Story

A User Story is a tool to move the focus from _What_ we're building (what often happens with traditional requirements) to _Why_ and _Who_. It's intended to start a conversation between the people who will implement the Story and the Customer/Product Owner, with the goal of ensuring that the team solves the underlying business problem instead of just delivering a requirement.

The best unofficial definition of "User Story" that I've heard: a User Story is an invitation to a conversation.

The goals of a User Story are:

  * ![User Story slices, image by Agile Pain Relief Consulting](https://agilepainrelief.com/wp-content/uploads/2017/05/User-Story-slices.png)

to focus on the business problem that needs to be solved, not the solution to that problem
  * to start a conversation about why a problem needs solving, who needs it, and what problem to solve
  * to demonstrate a need in as concise and simple a form as possible
  * to be a small vertical slice of functionality through the entire system, not a description of the component layers or technical need. (As illustrated by the picture). Traditional approaches often describe work to be done in technical layers (e.g. Business Logic or Database). This leads to waste in the form of Over Production. User Stories avoid this waste by challenging teams to build only the pieces in each layer required at that moment.

Since User Stories are not official Scrum tools, there is no required format, but a common structure is "As a <role> I want <to do> so that <value>".

The three components of User Stories, often referred to as the three C's:

  * Card: A token (with a Story title/description), used for planning, and acts as a reminder to have conversations.
  * Conversations: Conversations that discuss the Story details and result in one or more test confirmations.
  * Confirmations: Acceptance criteria that can be turned into automated acceptance tests. These automated tests are vital, and they are what enable the simple and light approach implemented by the first two C's: card and conversations.

##### Example User Stories:

_As a first time book buyer I want to find the perfect mystery novel so I can while away the time on my next plane flight._

_As a frequent book buyer I want strong passwords so that my credit card information remains secure._

Each User Story (or PBI) and its associated Acceptance Criteria (which we'll discuss next) are checked against the Definition of "Done" to ensure correctness and completeness.

## Acceptance Criteria

A User Story (or PBI) is deliberately vague, allowing the precise details that will help the implementation to be discovered at the last responsible moment. Acceptance Criteria are the precise details. Some of the Acceptance Criteria will be discovered in Ongoing Backlog Refinement events before the Sprint starts, and others will be discovered right after Sprint Planning when 3-4 people sit down to have a conversation about the Story.

_(For more details on the Lifecycle of a User Story and Acceptance criteria [visit this article](https://agilepainrelief.com/notesfromatooluser/2013/11/lifecycle-of-a-user-story.html).)_

The goals of Acceptance Criteria are:

  * to clarify what the team should build before they start work
  * to ensure everyone has a common understanding of the problem
  * to help the team members know when the Story is complete
  * to help verify the Story via automated tests.

So Acceptance Criteria are attributes that are unique to the User Story or Product Backlog Item.

##### Example Acceptance Criteria:

This User Story:

_As a frequent book buyer I want strong passwords so that my credit card information remains secure._

results in the following Acceptance Criteria:

_The password is at least 8 characters. The password contains a character from each of the following groups: Lower case alphabet, Upper case alphabet, Numbers Special Characters (!,@,#,$,%,^,&,*)_

The trouble with Acceptance Criteria written in a plain English format, as above, is that they're full of ambiguity. So a popular approach to describing Acceptance Criteria is "Specification By Example", also known as Behaviour Driven Development (BDD) or Acceptance Test Driven Development (ATDD).

Story: Strong passwords  
Acceptance Criteria:

![Acceptance Criteria - Specification By Example, image by Agile Pain Relief Consulting](https://agilepainrelief.com/wp-content/uploads/2017/05/Acceptance-Criteria-Specification-By-Example.png)

> _Conclusion_

Definition of "Done" is the global checklist that can be applied to all Product Backlog Items or User Stories. Acceptance Criteria are the things that are specific to the individual PBI or User Story. User Story is a placeholder for conversation about User need.

_Image attribution: Agile Pain Relief Consulting_
