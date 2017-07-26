# Mind Mapping for Successful Software Development

_Captured: 2015-10-03 at 11:30 from [blog.smartbear.com](http://blog.smartbear.com/design/mind-mapping-for-successful-software-development/)_

_It's amazing what happens when a group of people stands around a whiteboard, grabs some markers and starts [mind mapping](http://www.bettertesting.co.uk/content/?p=956). They think of new experiments to solve a thorny problem. They find better a design solution for a software feature. They identify important test cases that might otherwise have been missed. Mind maps do magic. _

![mind mapping](http://blog.smartbear.com/wp-content/uploads/imports/mind%20mapping1.jpg)

> _mind mapping_

If your software team hasn't tried mind mapping to help plan themes, design technical implementations, build a test strategy, or write user documentation, it's worth your time to learn how simply you can get started.

### Mind Map Features, Themes, Epics

Try kicking off your next major feature or theme by mind mapping. Find a space with a big whiteboard. Gather together business experts, end users, programmers, product owners, business analysts, testers, database experts, system administrators, [everyone who will be involved](http://blog.smartbear.com/software-quality/bid/218711/10-Reasons-Development-Teams-Don-t-Communicate) in delivering or using the software. If your project is geographically distributed, substitute an online whiteboard that allows real-time concurrent collaboration and a projector or huge monitor, along with good voice and video connections.

If a product owner or other stakeholder already knows what's needed in the feature, she can prepare a whiteboard ahead of time as a starting point. This saves time and helps focus the discussion. The whiteboard can be easily changed, which allows everyone to feel free to suggest changes.

Here's a whiteboard (below) from a theme planning discussion my team conducted. The product owner drew an extensive mind map ahead of time. He used color-coding to indicate UI features, other affected areas in the system such as [documentation](http://blog.smartbear.com/software-quality/bid/167295/Soft-Skills-in-Writing-Can-Boost-Any-Software-Developer-s-Career-Profile), and possible future features that we should keep in mind.

![mindmap1](http://blog.smartbear.com/wp-content/uploads/imports/mindmap1.jpg)

With so much information already available, the meeting got off to a quick start. We soon identified other areas we needed to consider, such as groundwork to be done ahead of time, development needs, and auditing requirements. We discussed each branch of the mind map in turn, adding or erasing nodes. After about an hour, everyone on both development and customer teams shared a broad and deep understanding of the work involved to deliver the necessary features.

The theme required changing a fundamental part of our data model. We thought this would be difficult and risky, and we estimated the story for just that part of the "groundwork" at 13 story points.

At the end of the meeting, one of the developers was studying the mind map, and had a sudden brainstorm. He thought of a simple way to implement the new model, and drew it in the upper right corner of the whiteboard. That took the size of the story down to three points from 13. He was convinced he would not have had that brainstorm if we hadn't used the mind map to visualize the work we needed to do.

We referred to this mind map over the next few sprints as we delivered stories for the theme. We checked off the nodes for which work was completed, so we could see at a glance how much work was left. It helped us stay on track. Customers were delighted with the finished product that we released to production.

### Mind Map Testing for a Feature or Theme

I've found mind mapping to be especially powerful as an aid in test planning. The process is similar to mind mapping the software features. Ideally, get all the same people together, but focus the discussion on testing: How will we know when we've delivered all the required features? For that matter, how will we know if we've even thought of all the features that users need? Expressing test cases and scenarios with nodes and relationships on a mind map is a great way to expand test ideas.

One benefit to using mind maps is a matter of timing. It can be hard to get stakeholders' time for multiple meetings. The testers can express their testing ideas with a mind map, then review it with developers, business experts, and other project team members. Even when the mind map is only "sort of" helpful to the development team members (some of whom are good at abstract thought without visual aids) plenty of users respond best to visual cues and drawings. This can help them understand relationships - and, incidentally, help them [get excited about the software you're building](http://blog.smartbear.com/software-quality/bid/228834/Creating-Excitement-for-Your-Next-Custom-App) to serve them.

Mind mapping helps you consider extra-functional testing, such as usability, security, performance, and stability. The process of drawing mind maps surfaces relationships, which might otherwise remain hidden. Different users may use different features in unique ways. You can start your exploratory testing with your mind map.

The visual cues of the mind map help identify resources needed. A new theme may require new test environments. What hardware and software is needed? How will you obtain or generate test data? Theme planning is the best time to think about how tests should be automated, and what is needed to accomplish that.

My team experimented with different mind map media. Drawing on the whiteboard was most effective for brainstorming. The image below shows a sample theme testing mind map. We collected questions for developers and business experts on the board as well. Every morning after stand-up, we reviewed the day's activities and questions on the testing mind map.

![mindmap2](http://blog.smartbear.com/wp-content/uploads/imports/mindmap2.jpg)

But though we always took pictures of the whiteboards and posted them on our team wiki, it was sometimes hard to find a mind map from a previous release or iteration. We started reproducing the whiteboard mind maps in an online, collaborative mind mapping tool. We used color-coding and icons to track testing as it proceeded, marking "done" tests in green. The mind map gave an instant visual picture of the project's progress.

### Mind Mapping at Lower Levels

When we dig into details at the user story level, mind maps help represent different scenarios and permutations to be tested. We can evaluate which tests can be done at the API or services level, and which must be done at the GUI level. We brainstorm about the easiest ways to test business logic as well as user experience. Mind maps help us generate more ways of exploring the software.

Testers may mind map story-level test cases individually, but I've found it's better to work in pairs.

Review the resulting test cases and strategy with customers and developers. As with the higher-level mind maps, the process of mind mapping delivers the most value, helping us to flesh out the details of each feature and user story. It's helpful to preserve that information through pictures of mind maps done on whiteboard or paper, or links to mind maps done with online mind mapping products.

In my experience, mind mapping is a great way to think of test cases for acceptance test-driven development or specification by example. In my current team, we're experimenting with mind mapping requirements and test cases in the form of examples for each small user story. Then we turn those into executable, but still human-readable, tests using rspec.

On my last team, we testers color-coded nodes on online mind maps to track testing progress for each user story. We exported pictures of the mind maps and attached them to the user story documentation. These were useful if strange behaviors appeared in production, especially if questions came up years after a new feature was delivered. The mind maps become part of a valuable knowledge base.

### Exploring

I've found mind maps especially useful when I set out to explore software that's unfamiliar to me. Here's an example from my very first [Weeknight Testing](http://weekendtesting.com/) session. Weeknight (or, more commonly, Weekend) Testing gives testers a chance to work together to test an application and exchange techniques and ideas. Our charter for this session was to test tinyurl.com.

I paired with [Darren McMillan,](http://www.bettertesting.co.uk/content/) an expert tester in the U.K. We decided to start by brainstorming test cases on a shared mind map, using an online browser-based mind mapping tool. As we each performed tests, we updated the mind map with icons showing passed and failed tests, added new tests as we thought of them, and made notes about what we learned as we tested, and questions we had. Here is the resulting mind map:

![mindmap32](http://blog.smartbear.com/wp-content/uploads/imports/mindmap32.jpg)

The mind map helped us organize our testing as we went. It also helped us ensure we didn't lose any ideas about more areas of the application to explore. Plus, it kept a history that made it easy for us to explain what we did to other participants during the de-brief portion of the session.

Recently, a developer on my team paired with me to experiment with creating a framework for acceptance test-driven development (aka specification by example). We chose a user story for which we wanted to come up with examples of desired and undesired behavior, and turn those into executable tests to help developers know what to code.

We first put the specifications for the story as nodes in the mind map. The mind map allowed us to note relationships between different components and behaviors. We then wrote test cases, which were brief descriptions of prerequisites, actions, and expected outcomes. We used these test cases in our test script, using an RSPEC-based framework.

Here's an example. A test case in our mind map states: "Put one valid panel, verify the get returns just that one panel." The test case in the script reads: "with { one_panel_in_stored_layout; response_lists_that_panel" }. This is easy to understand. Each snake-cased phrase derived from our mind map test cases represents the actual test code that executes the automated test.

### For Future Reference

Perhaps the greatest value mind maps give us is the way they promote collaboration. They help us generate ideas we might not otherwise have imagined. Visually representing software feature requirements and test scenarios helps us see relationships between components and behaviors. Mind maps are useful, too, when we need to change a feature, or when we just want to understand better how it works. They give a "big picture" of a theme, user story, or test plan.

The equipment needed for mind mapping is simple. The possibilities for creative use of [color-coding](http://www.ministryoftesting.com/2012/07/planning-testing-mindmap/), icons, and pictures are endless.

If you create mind maps on whiteboards or paper, take photos of them and keep them available on your team's wiki. Be sure to link them to the features or tests they document. Make sure they can be easily found later on. You'd be surprised what you can learn from a mind map years after it was created.

See also:
