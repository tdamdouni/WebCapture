# Don’t be tempted to break away from your TDD principles…

_Captured: 2015-10-18 at 12:52 from [mark0790.wordpress.com](https://mark0790.wordpress.com/2015/10/18/dont-be-tempted-to-break-away-from-your-tdd-principles/?utm_source=twitterfeed&utm_medium=twitter)_

OK, you know how it is. A story comes up to do a similar thing as code that's in the system currently. You know there's high risk around altering this piece of code so you say [in a very knee-jerk way] "oh, we could just cut-n-paste the old code…only two (story) points. Done…" ….Big mistake.

You then open up the original code and GOOD GRIEF, what was the programmer doing, aside from anything than writing production code. You know it works, but can you bear to propagate this around. As it turns out, I can't. Let me give you the context.

The original code has to interface with the accounting system, which btw, is about to change. The old code is a Quartz.Net CRON job, generally run from a windows service application. Your brief is that the two jobs will need to exist in tandem for a short time, oh and also, eventually you'll not be needing to do this in the future as they will develop a process to replace yours (yeah, right)…

Your running a team that has TDD as it's core. What do you do, where do you start (after you've said that infamous line above). First thing, [mandatory] do a quick U-turn to the product owner and the scrum master (in front of the team). Of course the (default) reason is that "it's not testable" - which of course it isn't. There is an "integration test" around the old job but this is almost irrelevant because it's so complicated you can't work out what's being tested.

OK, this is how I approached it:

  1. Write an integration test to test the new job class via the only entry point. In this case its signature is  
public void Execute (IJobContext jobContext);
  2. Write the actual class that implements this, copy and pasting the original code in and creating the assembly from the dependency container. Your code should now compile.
  3. OK, a CRON job is a CRON job. It should be delegating most of the work to another class otherwise you'll be violating SRP. Create a new unit test to prove that you are calling this new class using sensible entry points using mocks.
  4. Write the new class to implement the mocked interface (for simplicity we'll call this IJobWorker). Pull code out from the job and put it in to this new class. Your code should again compile at this point. Once you are green again, move on
  5. OK, scan the pulled out code code for any dependencies from JobWorker. These will typically manifest by the use of the "new" keyword. These are your dependencies.
  6. Write a set of unit tests where you mock in the identified dependencies.
  7. Write the code to accept these dependencies (in our case we use Property injection. Your code should now compile.
  8. Write a set of tests that call the required dependencies under each condition. Don't forget to write the negative tests in this case too. Moq is fantastic for this using the "Times" class and the "It" class. [It.Is<T>](http://russellallen.info/post/2011/06/29/Unit-Testing-Good-Patterns-3-Know-Your-Moq-Argument-Matchers!.aspx)() is particularly useful here too.
  9. Write the code to implement these calls. Rinse and repeat until your completely happy
  10. Compare to the original code. What have you missed?
  11. Inject in some logging statements. You know this is critical, you will be thanked many time over when you can show good logging to support what happened.

OK, some final rules of engagement.

  1. As tempting as it is, the old job should not be touched. You know that this code will disappear as soon as the accounting system is replaced. AND, it is a critical piece of functionality.
  2. You need to end-to-end test this. As much as I hate wring them, a full integration test(s) is mandatory here. As we can trigger this through the API, saving writing integration tests in POSTMAN is something the testers can understand and build upon. Just make sure all of the inputs can be passed in via the job context (for each environment).
  3. You go through a formal code review (this is part of our SOP in any case). In this review, the reviewer is also looking for instances where the functionality may break or the tests haven't covered off the scenarios.
  4. Revisit this code right through each environment. Amazing how you think of something when it's at the back of your mind. If anything should change, write the test first!
