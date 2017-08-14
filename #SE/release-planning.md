# Release Planning

_Captured: 2017-07-31 at 22:19 from [www.energizedwork.com](https://www.energizedwork.com/weblog/2006/04/release-planning?utm_content=buffer36ddc&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Small releases are better. They provide a constant flow of shippable product increments and generate regular feedback from the end-users. If release dates are not being dictated by specific marketing events, then I like to release on a 4-week cycle with each release comprising four 1-week iterations. The logistics and overheads of releasing need to be minimized, but you should be striving for this anyway, regardless of your release  
frequency.

### Release Planning

The purpose of release planning is to define the contents of a release or a specific shippable product increment. This involves identifying and committing to the following:

  * A goal for the release.
  * A prioritized set of [stories](http://www.energizedwork.com/weblog/2006/02/user-stories-part-1-what-is-user-story.html) that will be developed in the release.
  * A coarse estimate for each [story](http://www.energizedwork.com/weblog/2006/02/user-stories-part-1-what-is-user-story.html).
  * A date for the release.

I prefer not to assign stories to specific iterations as part of release planning. I treat the list of stories selected for the release as a mini [product backlog](http://www.energizedwork.com/weblog/2006/01/look-after-your-product-backlog.html) that drives iteration planning. Deciding the content of an iteration is left to the Iteration Planning Meeting where the highest priority stories are selected from the list up to, but not exceeding, the team's velocity. (Actually it's never a simple selection based solely on value because the estimates, or cost of the stories need to be reviewed and any risks need to be taken into consideration.)

When release planning, remember the golden rule: Don't go into too much detail. Release planning is not a commitment to precise details. Leave that  
to iteration planning. Release plans are imprecise. It's only when the team starts to work on the release, will you get feedback and begin to understand how quickly progress can be made and what can be achieved. So, you don't need to understand the details of each user story, just concentrate on their key assumptions. And you don't need to provide estimates with minimum inaccuracy. Focus on understanding just enough information to commit to delivering the goal by the release date. And be prepared to revise the release plan as things move forward.

### Preparing for the release planning meeting

The Release Planning Meeting will run more smoothly and take less time if you're prepared. As a [scrum master](http://web.archive.org/web/20121102063213/http://www.energizedwork.com/weblog/2005/12/your-scrum-team-needs-you.html), I like to work with the [product owner](http://web.archive.org/web/20121102063213/http://www.energizedwork.com/weblog/2005/08/being-effective-onsite-customer-or.html) ahead of the meeting to complete the following tasks:

  1. **Define a goal for the release** - Derive a velocity for the team. The velocity is an empirical measure so basically it's the number of iterations in the release multiplied by the velocity of the last iteration (assuming the team hasn't changed).
  2. **Produce a prioritized wishlist of stories** for the release by selecting those user stories from the product backlog that contribute to the goal. The product backlog is already sorted by value, so ideally the goal is a reflection of the highest value user stories found at the top of the product backlog. Typically the stories would've been written previously by the product owner as part of the evolution and management of the product backlog.
  3. Time permitting, have some developers **preview the wishlist** to ensure they understand the gist of the stories. Have them review the estimates to ensure they're sensible and provide any estimates that are missing. Given the granularity of the stories, these estimates are coarse so don't worry about them. At this early stage their purpose is to help size the wishlist to approximate the team's velocity. They'll be revisited in the Release Planning Meeting. The product owner should be prepared to split any user stories that the developers have difficulty understanding or estimating. Indeed it may be necessary for the developers to conduct a [spike](http://web.archive.org/web/20121102063213/http://www.think-box.co.uk/blog/2006/02/user-stories-part-3-using-spikes-to.html) in order to provide an estimate.
  4. **Review the wishlist**. The product owner can add some of the next highest value stories from the product backlog or remove some of the lowest value stories from the wishlist until the total estimate approximates the team's velocity. The product owner should be happy with the stories in the wishlist and their priorities, and should note any questions relating to the estimates that he wishes to raise in the release planning meeting.

### Release planning meeting

The purpose of the Release Planning Meeting is to have everyone in the team understand and commit to delivering the agreed release by the agreed date. Those present at a release planning meeting include the product owner plus any other stakeholders that can add valuable input, the developers and testers, and the scrum master.

The release planning meeting takes the following route:

  1. The product owner explains the release goal to the team. When the team understands the motivation behind the release goal (and the release date, if it's governed by some external event), they're placed in a better position to help identify the scope that has the best chance of being completed by the release date.
  2. The developers provide their team's velocity. If the team hasn't changed, the velocity should be the number of iterations in the release multiplied by the velocity of the last iteration.
  3. In the order of value, the product owner introduces each story to the developers.
  4. The developers ask enough questions about the stories to be able to confirm the existing coarse estimates or provide new ones. This interaction may require the product owner to split some stories, and when there's some technical-unknown, the story should be split to include a spike.
  5. The developers assess the technical risk for each story and provide some classification, e.g. high, medium or low.
  6. Given the release goal and taking the values, estimates or costs, and risks into consideration, the product owner selects the stories from the wishlist to make up the release plan.
  7. Consensus needs to be reached on the release plan with everyone present stating their commitment verbally.

There are plenty of opportunities in the release planning meeting to get bogged down, so it's important to remain focused and to maintain a brisk pace. I like to time-box each activity and use an egg timer.
