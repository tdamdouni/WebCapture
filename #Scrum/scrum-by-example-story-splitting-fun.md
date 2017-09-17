# Scrum By Example – Story Splitting Fun

_Captured: 2017-09-11 at 11:27 from [agilepainrelief.com](https://agilepainrelief.com/notesfromatooluser/2012/07/scrummaster-tales-story-splitting-fun.html?utm_content=buffer56a78&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer#.WbZW9eSbGaM)_

![slice](https://3hppfzjby0g1sxwjng1f4h1c-wpengine.netdna-ssl.com/wp-content/uploads/2012/07/photodune-2996181-different-colors-sliced-apple-xs.jpg)

Picking up from: [Learning How to Estimate](http://agilepainrelief.com/notesfromatooluser/2012/06/scrummaster-tales-learning-how-to-estimate.html)

The team are still in the Backlog Grooming/Refinement session. They've estimated a heap of stories and spotted several that need better Acceptance Criteria. However, there are several stories that Product Owner Sue would like to have worked on which are too large to commit to in a single Sprint. While they could estimate the Stories as they are, this seems like a waste of time. They're better off getting out the scalpel and splitting the stories into smaller parts.

_First a quick reminder from - __[Why Split User Stories_](http://agilepainrelief.com/notesfromatooluser/2010/09/story-slicing-how-small-is-enough.html)_:_

Why not just give the team large stories that span iterations. Why slice those stories into smaller parts? A number of reasons:

  * Small stories provide focus and a short horizon for the team. It's easier to get lost in the details with a larger story.
  * When you still have development to test handoffs (i.e. before you start doing [ATDD](http://www.methodsandtools.com/archive/archive.php?id=72) (Acceptance Test Driven Development), smaller stories enable more frequent handoffs and allow testers to work on smaller chunks of code.
  * Small stories give you the flexibility to reconfigure and adapt to new discoveries or changes. Perhaps the PO discovers that an existing story is now irrelevant; or while coding you discover a surprise. Small stories make it easier to adapt.
  * Small stories provide more feedback opportunities at all levels of the system and more opportunities for personal satisfaction; think of the small dopamine rush that happens every time you complete something!
  * Large stories increase the risk that your team will deliver nothing at the end of the iteration.
  * Your team has a capacity like a drain pipe and just like a pipe the larger the object you try to push through it the more likely it is that blockages and bottlenecks will occur. Perhaps one person who is tied up in the large story may also be the only person who can complete a key piece of another story.

Story #1: "As a first time book buyer I want to find the perfect mystery novel so I can while away the time on my next plane flight". **Size: 100**

Brad makes the quip that this appears to be the core of the website in a single story. (_Mark L. - Early on in our story writing career this often happens. We write large chunks of our product in a single User Story. Rather than trying to avoid it, just get it out and then split it.)_

After they finish laughing, the team get involved in discussion around the parts of the story. In the first round the discussion focuses on the database ([Pythia 22x](http://en.wikipedia.org/wiki/Oracle)); how difficult it will be to get right; what the right format for the staff reviews would be; and how to get a book home in time (FedEx vs. UPS vs. Purolater). They crank out some new stories:

  * As a first time book buyer I want to find the perfect mystery novel quickly with an Pythia 22x database
  * As a first time book buyer I want to have my perfect mystery novel shipped home via FedEx so I get it in time for my next flight
  * As a first time book buyer I want to see the star rating on a review before I read it so I can see whether the book is worth reading
  * As a first time book buyer I want to select my book and place it in the shopping cart so I can buy it
  * ….

## Analysis

Most of these revised stories have in common a focus on technology vs. solving the need of the end user. A User Story is "a single sentence that describes a small piece of valuable functionality from the point of view of the end user". Real end users don't care about our database technology nor our shopping carts. They just want working software. By writing User Stories from their point of view we delay making technical decisions until it's useful from the Point of View of the application.

## Story

Scrum Master John reminds the team to place the focus on the value for the end user; in this case, the "first time book buyer" and not the technology.

In their next attempt the team break the stories down:

  * As a first time book buyer I want to find the perfect mystery novel by reading staff reviews so I won't waste my money reading bad books
  * As a staff member I want to enter book reviews so I can delight book buyers
  * As a first time book buyer I want to see only books that get five star reviews so I don't waste my time reading reviews about weaker books
  * As a first time book buyer I want to select a single book for purchase so that I can read it _(Mark L. - the team have elegantly avoided solving the whole shopping cart problem for the moment by handling just a single book. Clearly they will later need to handle multiple books but if they can't get one book home they can't get more home)._
  * As a first time book buyer I want to ship my book home within two days so that I can get it before my next flight

The team estimate the revised stories, this time most of them are reasonably small except: "As a staff member I want to enter book reviews so I can delight book buyers" which is estimated at size 20 (they started off at 40). Sue says at first it would be fine to support only plain text and a star rating. The reviews wouldn't have to be updated once written. She's willing to offer a lot. Nonetheless the team say it's a large problem to enter text, save it in the database, and display it on the book page. Sue asks the team, "Can we display the reviews first and solve the problem of entering them in the system later?" "Ludicrous," says Martin, "What's up with that? How can we display reviews before we even have the text? Even if we could, we need to get the database right."

Sue explains that she needs to talk to the Product Steering committee in the next few weeks. Her goal is to have a [Minimum Viable Product](http://www.startuplessonslearned.com/2009/08/minimum-viable-product-guide.html) (i.e. a down payment on the vision) in place. To get continued funding for the product the team needs to be able to demonstrate the basic flow for the "first time book buyer", i.e. Read a review -> Buy the book -> Ship the book home. While the reviews need to exist to demonstrate the product we can live with reviews that were entered directly into the database. Sue goes on, "For the next couple of Sprints I could even live with fake reviews if that helps. It's about being able to demonstrate the basic experience whilst not having the back end working right now."

If the product gets continued funding from the steering committee' then they can decide how to flesh out the support for staff reviews. After some more discussion the team come to see Sue's point of view. They write a new story: "As a first time book buyer I want to read staff reviews that are displayed on the book's page so that I can buy the perfect mystery novel." After a couple of rounds of Planning Poker the team agree to estimate the story at 5 points.

## Analysis

In this case Sue was trying to get the team to consider "Independent" from [INVEST](http://xp123.com/articles/invest-in-good-stories-and-smart-tasks/) (Bill Wake's criteria for good User Stories): "Dependencies between stories limit the flexibility of both the Product Owner and development team. The Product Owner should be able to ask for stories in whatever order they make sense." When the team said that they needed to write the staff side of the review system before displaying any reviews they were taking prioritization over from the Product Owner.

N.B. If the dependency is just around sizing/effort then it's okay for the team to say, "This type of story requires a templating engine; the first one will be sized 13, all subsequent stories will be sized 2."

## End Story

There are several dozen interesting ways to split stories; some more ideas and examples are found in:

<http://www.richardlawrence.info/2009/10/28/patterns-for-splitting-user-stories/>  
<http://agilepainrelief.com/notesfromatooluser/2010/12/more-notes-on-story-splitting.html>  
<http://www.agileforall.com/2009/12/10/new-to-agile-learn-how-to-split-stories/>  
<http://lassekoskela.com/thoughts/7/ways-to-split-user-stories/>  
<http://xp123.com/articles/twenty-ways-to-split-stories/>  
<http://blogs.collab.net/agile/2012/06/20/15-ways-to-split-an-epic-a-team-exercise/>  
<http://blog.gdinwiddie.com/2011/05/01/splitting-user-stories/>

What problems have you had splitting stories? How did you split the stories in the end? What would you do differently today?
