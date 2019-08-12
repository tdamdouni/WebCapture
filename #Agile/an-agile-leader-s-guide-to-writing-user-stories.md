# An agile leader's guide to writing user stories

_Captured: 2019-02-02 at 08:54 from [techbeacon.com](https://techbeacon.com/app-dev-testing/agile-leaders-guide-writing-user-stories)_

![Typewriter](https://techbeacon.scdn7.secure.raxcdn.com/sites/default/files/styles/article_hero_image__3x/public/field/image/agile-user-stories.jpg?itok=lyEPjjqH)

One of the biggest challenges in software development is the nearly impossible task of gathering clear requirements and then getting those requirements to remain unchanged during code development. In the [waterfall approach](http://techbeacon.com/devops-waterfall-dont-waste-your-time) to software development--despite efforts to define, document, and approve every possible contingency before development begins--the delivered product is rarely what the customer wants.

The agile alternative? User story creation.

One of the biggest advantages of using an agile approach to software development is that the requirements aren't set in stone, but instead are expected to change, with constant feedback from stakeholders and the business. Agile methodologies such as Scrum and extreme programming (XP) replace traditional, lengthy requirements documents with a prioritized product backlog made up of concise user stories, the details of which emerge closer to when the story is ready to be implemented.

Though user story creation is more art than science, this tutorial will give you the information, examples, and steps you'll need to create high-quality user stories.

### The history of user stories

XP [first introduced](http://guide.agilealliance.org/guide/user-stories.html) the concept of user stories in 1998, comparing them to use cases. In _Object-Oriented Software Engineering: A Use Case Driven Approach,_ Ivar Jacobson introduced use cases as a way to document requirements by defining interactions between a role (a person using the system) and the system itself to achieve a goal using the [Unified Modeling Language](http://www.uml.org/) (UML).

This approach was popular in object-oriented development and is still used as a key process in software development frameworks, such as the [Unified Process](http://www.methodsandtools.com/archive/archive.php?id=32) (UP), the IBM [Rational Unified Process](http://www.ibm.com/developerworks/rational/library/content/03July/1000/1251/1251_bestpractices_TP026B.pdf) (RUP), and the [Oracle Unified Method](http://www.oracle.com/partners/en/products/applications/oracle-unified-method/get-started/index.html) (OUM). Using use cases, rather than user stories, allows for iterative and incremental development and is considered an agile approach to requirements definition.

With the introduction of the much shorter user stories and [the popularity of XP and Scrum](http://techbeacon.com/agility-beyond-history%E2%80%94-legacy%E2%80%94-agile-development), a product backlog made up of user stories became the more commonly known approach to agile requirements definition. Many practitioners still think that user stories are the _only _acceptable agile approach. However, [Alistair Cockburn](http://alistair.cockburn.us/A+user+story+is+to+a+use+case+as+a+gazelle+is+to+a+gazebo), one of the Agile Manifesto's signatories, prefers use cases to user stories.

Though there are plenty of strong opinions about the [meaning of "agile,"](https://techbeacon.com/uncle-bob-martin-agile-manifesto-15-years-later) both use cases and user stories are compatible with that approach. Some say [user stories eventually become similar to use cases](http://www.boost.co.nz/blog/2012/01/use-cases-or-user-stories/) once the team agrees upon the details of the implementation. In the early stages, the user story is simply a short sentence, but it isn't complete until the details and acceptance criteria are defined.

### Creating user stories

There are varying opinions on the definition of a user story and how to best go about creating one. Some guidelines for a good user story include the following:

  * It should be written by someone who represents business users (usually the product owner)
  * It should initially include brief descriptions of the "who, what, and why," but not the "how"
  * It should produce a vertical slice of working code
  * It should be small enough that it can be coded and tested in one iteration (usually a one-to-four-week period)

Various templates, techniques, and acronyms are used to help product owners write user stories. Three of the most common techniques are the [role-feature-reason](http://guide.agilealliance.org/guide/rolefeature.html) template, the [Three C's](http://guide.agilealliance.org/guide/threecs.html) (card, conversation, confirmation), and [INVEST](http://guide.agilealliance.org/guide/invest.html) (independent, negotiable, valuable, estimable, small, testable).

#### **Examples**

Say you're developing an application that would allow trainers to upload courseware and attract students who are interested in taking a class. Here's how you would apply user story techniques.

**Role-Feature-Reason**

As Mike Cohn of Mountain Goat Software [explains](https://www.mountaingoatsoftware.com/blog/advantages-of-the-as-a-user-i-want-user-story-template), the role-feature-reason template, or RGB (role, goal, benefit), looks something like this:

_"As a [type of user] I want [some feature] so that [some reason]."_

Although there are variations, this short sentence structure keeps the focus on the _who, what, _and_ why_. This prevents the product owner from giving the development team too much information about _how _they should implement a solution. By focusing on the who, what, and why, the development team is empowered to find the best technical solution.

**Example 1: Provide a trainer with the ability to add a course**

As a _trainer_, I'd like to be able to _add a new course_, so that _I'll have the potential to attract new students._

**Example 2: Provide a student with the ability to search for a course**

As a _student_, I'd like to be able to _search the course offerings_, so that _I'll be able to find an offering that most interests me._

**The role (who)**

The role describes _who_ will benefit from this function. Notice that the role is not simply "the user." There are different types of users, and so we want the role to be more specific than "user" but describe the type of user that will benefit from the story. Product owners are often tasked with getting in the mind of their users in order to understand what would be most valuable for them.

Example 1 Role = trainer

Example 2 Role = student

**The feature (what)**

This step very briefly describes _what_ the user wants. This most closely represents the requirement that you describe in traditional software development. However, you want to be careful not to be too specific or describe how to write the code. That will be determined eventually, but not when you first create the user story. The user story should be written from the perspective of the user who will benefit from the function, not from the perspective of the developer who will be coding it.

Example 1 Feature = add a new course

Example 2 Feature = search the course offerings

**The reason (why)**

Finally, we want to state why the user wants this feature. What value will the user get from it? This helps the product owner evaluate how to prioritize the user story on the backlog. If the value or benefit can't be articulated, it might be something that's not necessary. Understanding the value often helps the development team find innovative ways to implement the code in order to solve the objective--ways that may be different from what the product owner has in mind.

Example 1 Reason = attract new students

Example 2 Reason = find an offering that most interests me

#### **The Three C's: Card, Conversation, Confirmation**

The Three C's formula, developed by Ron Jeffries, helps to reach agreement between the business and the technical team on the meaning of the user story. The Three C's guide them through the progressive elaboration of a story, from a brief statement to a fully developed user story.

**Card**

The user story starts out purposely brief, with a simple statement that could fit on a 3x5 index _card_, typically following the role-feature-benefit format that I just covered. For example:

As a _trainer_, I'd like to be able to _add a new course_, so that _I'll have the potential to attract new students._

**Conversation**

Though the user story starts as a simple statement, details must emerge before the team starts working on the story. Rather than describe what's needed in documentation, the team will include 1) representation from the business (usually the product owner), and 2) the development team itself, including developers, testers, business analysts, or anyone else on the team.

This _conversation _allows the development team to ask questions to ensure they have a clear understanding of what's being asked for and the value being provided. For example:

**Developer: **Will the trainer need to upload the courseware onto a website?

**Product owner: **No, the trainer will just be adding information about the course that will be offered, and the feature should include a way for the student to get on an interest list. This story gives the trainer the ability to advertise a course.

**Developer: **What fields should be included?

**Product owner: **Course title, abstract, dates and times, location.

**Developer: **Will this only be for advertising face-to-face classes?

**Product owner: **Yes. We may add a virtual class option later, but this story will only cover adding course information for face-to-face class offerings.

**Developer: **What information should be gathered when a potential student asks to get on an interest list?

**Product owner: **Name, phone number, and email address.

The team will update the user story with the information they've gathered from the conversation, and they will discuss the implementation--or the "how"--which often creates specific tasks that must be done in order to complete the story. Although the user story is written from the perspective of the user, the development team writes the tasks for the developers and includes the technical implementation details.

**Confirmation**

The development team needs to have a clear understanding of how the feature will work in different situations, including error conditions. They need to get _confirmation_ regarding the acceptance criteria from the product owner. These are the criteria that must be met for the story to be considered done and accepted. Here's an example of acceptance criteria:

  * A trainer is able to add a new course by entering course title, abstract, dates and times, and location to a form and press an "add course" button.
  * If any fields are missing or dates or times are invalid, error messages will appear.
  * Once the course has been properly added, it will be publicly displayed on the course website and there will be a button for a student to express interest.
  * The interest button will allow a user to enter name, email address, and phone number, and this data will be stored and associated with the new course.  


#### **INVEST: The attributes of a solid user story**

INVEST is an acronym that helps evaluate whether you have a high-quality user story. Here's how the attributes in the acronym apply to the story we've been working on.

**I = Independent**--Can this story be completed by the team? We want the team to be able to complete the whole story rather than be dependent on a different team to do the GUI, for example.

**N = Negotiable**--The story is not so detailed as to describe exactly how long the fields should be or give specifics about date formats and the like. Most likely there will be common routines or libraries that will allow the development team to implement in the way that makes the most sense for them.

**V = Valuable**--The product owner describes that the value being sought is the ability for the trainer to be able to advertise upcoming classes. This is clear in the "why" of the original statement and re-emphasized in the conversation.

**E = Estimable**--The team will ask enough questions and gather the details to feel confident in their ability to estimate the story.

**S = Small**--The team needs to feel confident that they'll be able to complete the story within a sprint. If they do not, they might split the story. For instance, in our sample story, they may decide to make the ability to gather the student information be a different story and simply display information about the class for this story.

**T = Testable**--With clear acceptance criteria, both the happy path and error conditions can be tested.

_[ Webinar: [World Quality Report 2019: Focus on the Financial Services Sector](https://www.brighttalk.com/webcast/8653/345220?utm_source=techbeacon&utm_medium=techbeacon&utm_campaign=WQRFin)]_

### **Aligning to a vision **

I've covered the basics of creating a user story, but you still need to understand the big picture before creating your own user stories. There's much work you must do up front, at a higher level, to determine what the highest-value features are that should be delivered to the customers. Those are ultimately decomposed into user stories.

It's important for the team to first understand the high-level vision and to make sure the features, and ultimately the user stories, align to that high-level vision.

Typically, you break the product down into groupings that go by names such as "themes" or "features." Though the labeling of these backlog items can differ depending on the agile method and tools you use to describe them, the idea is to make sure they align so that the work can be traced up to your vision, which will ensure that you're meeting the goals and values of the product vision.

Again, don't start a project by creating user stories; start by creating a vision. For our example, I simply show a sample vision statement, which leads to some sample features, which can be further decomposed into user stories.

#### **Vision**

Provide a high-quality website that will allow trainers to advertise courses and allow students to take those courses.

#### **Features**

  * Provide a course offering page that will allow students to sign up for courses.
  * Provide a home page that will tell users what our site is all about.
  * Provide a registration process allowing users to log in, create a profile, and keep track of their classes.
  * Provide a blog that will help advertise our offerings and gain publicity for our website.

#### **User stories**

  * Provide trainer with ability to add a course on the course offering page.
  * Provide students with ability to search for a course.

In the example above, you can see how the user stories originated. The user stories were part of a feature to "provide a course offering page" that aligns to the high-level vision.

### **Impact mapping**

Though aligning to a vision will help you populate your initial backlog, it's not the only way to do so. There are a many tools and techniques that product managers can use to create the stories that go in a new backlog and that align with the vision.

One strategic planning technique used to help understand the big picture, impact mapping, was popularized by Gojko Adzic, author of _[Fifty Quick Ideas to Improve Your User Stories_](https://leanpub.com/50quickideas)_ and_ _[Impact Mapping: Making a big impact with software products and projects_](http://www.impactmapping.org/). Impact mapping is a mind map that starts with the goal, which should address the question of value and why you're building the product.

The next level lists the "actors," or people who will help accomplish the goal. Next, the map lists the behaviors, or "impacts," that the actors will perform to help accomplish that goal. The final level of the map presents the "deliverables" that the team can implement. These enable and support the actors to create the desired impacts. It's from these deliverables that you derive the software features and stories.

  * Goal: Make widely available courses that students will want to take
  * Actors: Trainers, students
  * Impacts: Trainers will provide high-quality classes that are of interest to students; students will provide referrals and recommendations
  * Deliverables: High-quality classes that are accessible to students
  * Potential stories:
    * "As a trainer, I want to advertise classes, so that I can get students.
    * "As a trainer, I want to get feedback from students, so that I can continually improve."
    * "As a trainer, I want to find out what students want, so I can add to my curriculum."
    * "As a student, I want to find classes that most interest me."
    * "As a student, I want to find classes that I'm able to take online, so that I won't need to travel."
    * "As a student, I want to read reviews from others, so that I can decide which classes will best suit me."

Mapping out user stories in this manner allows traceability into the thought process of how the stories ultimately create value and how you use them to achieve the end goal. The idea isn't to implement everything, but to find the shortest path through the map to achieve your goal.

### **Splitting stories**

One of the most common problems agile teams run into is when stories are too big and can't be completed in an iteration. When the team creates the tasks associated with the story, they realize that there are too many unknowns, or that the tasks involved will take more time than the team has available in a single iteration. Teams sometimes address this by [splitting a bigger story into smaller stories](https://techbeacon.com/practical-guide-user-story-splitting-agile-teams).

Remember, however, that you want a user story to deliver working software that will add value for the user. Rather than creating a user story that will only partially complete a function, split stories into "vertical slices" that will deliver end-to-end functionality.

### **Turn to the community for deeper learning**

Detailed solutions on how to solve the toughest problems relating to requirements and user stories are unique to each situation. However, one common trait of successful agile practitioners is that they're eager to help others and share what they know.

Cohn's [userStories](http://www.userstories.com/) website allows those who work with product backlogs and user stories to share products, resources, and knowledge. The products page includes an impressive list of tools, many available for free, with opportunities for user reviews and input. Cohn notes on the site that he hopes to expand the site so the product backlogs can be shared.

There's never going to be a one-size-fits-all answer on how to write perfect user stories. However, over time, with a healthy mix of experience, advice from the experts, and experimentation with suggested tools and techniques, you can continually improve.

_Image credit: [Flickr](https://flic.kr/p/fHEzZe)_
