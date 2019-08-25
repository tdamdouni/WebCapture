# The Magic of Small User Stories - DZone Agile

_Captured: 2019-08-18 at 14:48 from [dzone.com](https://dzone.com/articles/the-magic-of-small-user-stories?edition=518297&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202019-08-17)_

I often run into teams that like big User Stories. Why spend time writing, planning and estimating a bunch of small stories when you can write, plan and estimate just one big story? Bigger stories mean better efficiency, right? Not necessarily.

  * **Focus**: Small stories keep us focused and help us see that the end is not too far off. It’s easy to get overwhelmed with details when we work on large stories. Small stories also promote higher team satisfaction; humans get a small dopamine rush whenever they finish something.
  * **Transparency**: Small stories provide much higher transparency/visibility into sprint progress during the Daily Stand-up and for stakeholders. Progress is easy to track when we see a series of completed, small stories; it’s more difficult to estimate and visualize the true progress of a large story each day.
  * **Predictability**: Small stories tend to result in a more accurate and reliable velocity trend, which reduces variability and improves predictability. Relative story point estimates using the Fibonacci sequence are, by design, increasingly less accurate for larger estimates — as the “cone of uncertainty”. A 13 or 20-point story is likely much less predictable than several 2, 3, or 5-point stories.
  * **Flexibility**: Small stories provide more frequent opportunities for feedback and course correction. They provide more flexibility to adapt as we learn. When circumstances change or stories become irrelevant, there’s less waste in revamping or purging a small story.
  * **Throughput**: Small stories allow testers to begin testing sooner in the sprint, and work on smaller chunks of code.
  * **Reduced Risk**: Large stories increase the risk that the team will not deliver anything at the end of the sprint that is 100% done. Team capacity is like a funnel. When we try to force a large object (large stories) through it, the funnel gets clogged. For example, a developer working on a large story may also be the only one with the skill set to complete another critical story.

## **How Do I Create Smaller Stories?**

You will find lots of good articles and blogs about splitting user stories with a few google searches; however, here are a handful of questions I’ve found useful in determining how to create smaller stories:

  * If there are several outcomes in a single user story, are they all necessary right now? Is there an 80/20 split that provides most of the value? Can you develop 20% in a different story?
  * Are there multiple business rules or persona’s in the user story? Can rules be built separately, or different persona’s handled in separate stories? Can simpler rules suffice for now to get it working?
  * Can the “happy path” be coded first without all the exception conditions? Exception conditions can often be put into additional stories.
  * Are there multiple platforms or interfaces (inputs or outputs) associated with the user story? Can we develop them one at a time?
  * Are there multiple operations involved in the user story i.e., CRUD? Can we develop one operation at a time?
  * What test scenarios apply? Are some scenarios complex and not very relevant? Can a simpler first iteration be developed to prove the design?
  * Does most of the story's complexity come from non-functional requirements like security or performance? If so, can the story be separated to first make the functionality work, then modified later to satisfy non-functional requirements?

## **How Small is “Small”? What’s the Right Size?**

This is a highly subjective question and one that depends on several factors including team capabilities, sprint length, and others. A good starting point for determining story size is to use the acronym I.N.V.E.S.T. If you are unfamiliar with this approach, just google “agile invest” to learn more about it. A story must deliver value. Delivering a story that has little discernable benefit just to keep it small probably doesn’t make sense. The bottom line is that smaller user stories are usually better than larger ones. Use common sense to ensure a user story can deliver real value, and can also be completed within a single sprint.
