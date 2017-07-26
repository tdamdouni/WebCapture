# Testing is a Team Problem

_Captured: 2017-07-08 at 09:27 from [janetgregory.ca](http://janetgregory.ca/testing-is-a-team-problem/?utm_content=bufferec0cb&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

During a recent Q & A session for my webinar "[What a testing mindset brings to your agile team](https://www.youtube.com/watch?v=ZqTJUissSdw&feature=youtu.be)", one of the participants asked me this question:

Why do you approach testing as a team problem vs quality as an overall responsibility of the team? Have you found that using it as a problem vs quality outcome is a way to help with the adoption?"

Normally, I talk about quality as a team responsibility, but I didn't in this particular talk, which focused on testing. However, this question made me think about the difference. I blogged on the quality subject here <http://janetgregory.ca/a-quality-discussion/> so I won't repeat except to say, the conversation is hard for teams to have.

The other part of the question is what I will address in this post. This slide is one that prompted the question. However, like all slides, it only shows a very small part of what I say.

![Team-Testing-1](http://janetgregory.ca/wp-content/uploads/sites/16/2017/06/Team-Testing-1.png)

When we approach testing as a team problem, we look at the testing question in a completely different way. Instead of making it a tester's problem (or challenge), we can look at all team members can use their strengths to make the product better, and in this case - as it pertains to testing. Testing is tangible and can be broken down into concrete types of tasks and teams can discuss who might be the best person(s) to do that task.

Let's look at the testing problem and some of the "smaller" challenges associated with it, and who might help.

  1. What do we test? At a minimum, we could test:
  * **Ideas / requirements:** testers, business reps, programmers (all from different perspectives) to answer the question - "Are we building the right thing?"
  * **Code**: programmers in the form of unit tests, anyone in the form or reviews to answer the question "Are we building it right?"
  * **The product / the system**: testers, business reps, end users to answer two questions. Before you start, ask "What business problem are we trying to solve?" and then before you release, ask, "Did we solve the business problem?".

Using models like the agile testing quadrants, enables the team to talk about which types of testing should the team do for "Story Done", or "Feature Done", or even" Release Done".

As a team, you could brainstorm using a mind map to think of specific tests that might be needed for a feature or story. By involving the whole team, you get multiple perspectives.

  2. When do we start testing?
  * Using practices like ATDD (acceptance test driven development) means that you involve the whole team from the beginning. Note: You may know this practice as BDD (behavioural driven development) or SBE (specification by example). The product owner - with acceptance tests, the team - vetting those tests using example to get to shared understanding of what we are going to build, collaborating with programmers to decide what automation we need, automating, exploring, etc., finishing up with the product owner (hopefully) accepting. And then, there's UAT, and load, and ………
  * In other words, the whole team needs to be involved to help solve this problem. ![Testing-Team-2](http://janetgregory.ca/wp-content/uploads/sites/16/2017/06/Testing-Team-2.png)

  3. What testing artifacts do we need? Considerations - regulatory, business needs, team needs.
  * If we think about automated test results, you would probably need programmers or operations to help get the continuous results displayed and kept.
  * We need to understand what the needs are from a regulatory and / or business standpoint, so we would need their viewpoints.
  * How do we show coverage? Either automated / exploratory.
  * What is the value of any artifacts created, either within the team or external to the team? Is there a way we could make it simpler? When all team members are part of this discussion, often we can find simpler ways of doing things.
  4. How do we automate tests?
  * Using models such as the automation test pyramid, we can use the whole team to discuss which layer would be appropriate for any given test, thinking about value, visibility and maintenance. Better choices are made when the whole team is involved since it raises the level of transparency and trust within the team.
  5. What else is worth automating?
  * Just asking this question, opens the door for programmers to help testers or business users with automation, or testers to ask for help in automating or learning new tools to help them in their work.

As you can see, none of these testing challenges are small, but in my experience when the whole team starts to look at testing as a team problem, then the solutions are tackled in a completely different way using everyone's strengths. If the testing problem is solved, by its very nature, the quality of the product will rise.

Remember two questions to ask if nothing else.

  1. What is the business problem we are trying to solve? -- so, you can test for that.
  2. How are we going to test that? - for every story and feature to help make them testable within the system.
