# How to Work With Someone Else's Code

_Captured: 2017-10-19 at 19:37 from [dzone.com](https://dzone.com/articles/adding-functionality-to-legacy-code?edition=334792&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-10-19)_

It's an inevitable part of being a software engineer: We get stuck with making a change or adding a feature to code we did not create, are not familiar with, and is unrelated to our part of the system. Although this can be a tedious and difficult task, there is a great deal to be gained from being flexible enough to work with code written by another developer, including increasing our sphere of influence, fixing software rot, and learning about previously unknown parts of the system (not to mention, learning techniques and tricks from another programmer).

Taking into account both the tediousness and the advantages of working with code written by another developer, there are some serious pitfalls that we must watch out for:

  * **Our ego**: We may think we know best, but we often do not. We are about to change code that we have very little knowledge about, including the intent of the original author, the decisions over the years that led to this code, and the tools and frameworks available to the original author when he or she wrote it. Humility is worth its weight in gold and it should be liberally applied.
  * **The ego of the original author**: We are about to touch code written by another developer, another human with his or her own style, constraints, deadlines, and personal lives (that consume his or her time apart from work). It is only human nature for that person to become defensive when we start questioning the decisions he or she made or questioning why the code looks so unclean. We should make every effort to get the original author to work _with_ us, rather than _hinder_ us.
  * **Fear of the unknown**: Many times, we are going to be touching code that we know very little or entirely nothing about. That can be scary: We will be responsible for any of the changes we make, but we are essentially walking around a dark house with no flashlight. Instead of being fearful, we need to establish a structure that allows us to be comfortable with making changes, both large and small and allows us to ensure that we have not broken existing functionality.

Being that developers, ourselves included, are humans, there is a lot that human nature plays into working with code written by another developer. In this article, we will walk through five techniques that we can use to ensure that we use our understanding of human nature to our advantage, gaining as much as we can from the existing code and the original author, and leaving the code in a better state than we found it in. Although this list is not comprehensive by any means, applying the techniques below will ensure that when we are finished change code written by another developer, we are confident that we have maintained the working state of the existing functionality, while at the same time, ensured that our new feature is working in harmony with the existing code base.

## 1\. Ensure Tests Exist

The only truly confident way that we can ensure that the existing functionality in code written by another developer _actually_ works as intended and that any changes we make to it do not keep it from working as intended, is to support the code with tests. When we come across code written by another developer, there are two states we can find it in: (1) without sufficient level of testing or (2) with a sufficient level of testing. In the former case, we are on the hook for creating those tests and in the latter case, we can use the existing tests to both ensure any changes we make do not break the code, as well as learning as much as we can about the intent of the code from the tests.

### Creating New Tests

This is not an envious case: we are responsible for the changes we make to another developer's code, but we do not have a way to know for sure that we did not break something while we were making changes. _Complaining will not help_. Regardless of the condition we found the code in, by nature of touching the code, we will be responsible if it breaks. Therefore, we should take ownership of our actions as we make our changes. The only way to know that we do not break something is to write the tests ourselves.

Although this is tedious, it has the major advantage of allowing us to learn through writing the tests. Assuming that the code works right now, we need to write our tests so that expected inputs result in expected outputs. As we go through this test-writing process, we will start to learn about the intent and functionality of the code. For example, given the following code
    
    
        public Person(int age, double salary) {
    
    
            return person.getAge() < 30 && 
    
    
                ((((person.getSalary() - (250 * 12)) - 1500) * 0.94) > 60000);

we do not know much about the intent or the magic numbers used in the code, but we can create a set of tests where known inputs produce known outputs. For example, by doing some simple math and solving for the threshold salary that constitutes success, we find that if a person is under 30 and makes approximately $68,330 a year, they are considered successful (by the standards of this code). Although we do not know what those magic numbers are, we do know they are they reduce the original salary. Thus, the $68,330 threshold is a base salary before deductions. Using this information, we can create a few simple tests, such as the following:
    
    
            Person person = new Person(29, THRESHOLD_NET_SALARY - 1);
    
    
            Assert.assertFalse(new SuccessfulFilter().test(person));

With just these three tests, we now have a general understanding of how the existing code works: if a person is under 30 and they make $68,300 per year, they are considered successful. While we could create many more tests to ensure corner cases (such as null ages or salaries) function correctly, a few short tests have given us not only an understanding of the original functionality, but also a suite of automated tests that can be used to ensure that we do not break existing functionality when we make changes to the existing code.

### Using Existing Tests

In the event that there exists a sufficient test suite for the code, there is a still a great deal we can learn from the tests. Just as the with the tests we created, by reading the tests, we gain an understanding of how the code is intended to work at a functional level. Whatsmore, we gain an understanding of how the _original author_ intended for the code to function. Even if the tests were written by someone other than the original author (before we came along), this still provides us with someone else's intent about the code.

While existing tests can be helpful, they should still be taken with a grain of salt. It is difficult to tell if the tests have kept up with the development changes to the code. If they have, we have a strong basis for understanding the code; if they have not, we have to be very careful not to be misled. For example, if original salary threshold were $75,000 per year, and was later changed to our $68,330 value, this outdated test could lead us astray:
    
    
        Assert.assertTrue(new SuccessfulFilter().test(person));

This test would still pass, but it would not pass for the intended reason. Instead of passing because it is _exactly_ the threshold value, it is passing because it is over the threshold value. If this test suite included a test case that expected the filter to return `false` if the salary is one dollar less than the threshold, this second test would fail, revealing that the threshold value is wrong. If the suite did not have such a test, it would be easy for stale data to mislead us about the actual intent of the code. When in doubt, trust the code: As we previously showed, solving for the threshold reveals that the test does not target the _actual_ threshold.

Additionally, consult the repository logs (i.e. Git logs) for both the code and the test cases: if the last updates to the code are much more recent than the last updates to the tests (and significant changes have been made to the code, such as changing the threshold value), then it is likely the tests have fallen out of date and should be viewed with caution. Note that they should not be disregarded entirely, as they still might provide us with some documentation about the intent of the original author (or the developer who wrote the tests more recently), but they may contain stale or incorrect data.

## 2\. Talk to the Person Who Wrote It

Communication is critical in any endeavor involving more than one person. Whether it is a company, a cross-country trip, or a software project, a lack of communication is one of the most reliable means of crippling a task. Although we should be communicating whenever we create new code, the stakes rise when we are touching existing code. In this case, we do not know much about the existing code, and what we do know may be misguided or only represent a fraction of the whole story. In order to truly understand the existing code, we need to talk to the person who wrote it.

When it comes time to ask questions, we need to be sure they are specific and are targeted at achieving our goal of understanding the code. For example:

  * Where does this piece fit into the big picture of the system?
  * Do you have any designs or diagrams for it?
  * Any pitfalls I should be aware of?
  * What does _this_ or _that_ component or class do?
  * Is there anything you wanted to put into this code that you didn't at the time? Why?

Always be humble and seek out genuine answers from the original author. Almost every developer has had an instance where he or she looked at someone else's code and asked themselves, "Why on earth did he/she do that? Why didn't they just do _this_?" only to spend hours to come to the same conclusion as the original author. Most developers are talented programmers, so it is a good idea to assume that if we come across a seemingly poor decision, there is probably a good reason for having made it (there may not be, but it is better to go into someone else's code assuming there is a good reason; if there is not, we can make that change through refactoring).

Communication also has a secondary side-effect in software development. Conway's Law, originally created by Melvin Conway in 1967, states that:

> Any organization that designs a system...will inevitably produce a design whose structure is a copy of the organization's communication structure. 

That means that a large, tightly communicating team will likely produce monolithic, tightly-coupled code, while a set of smaller teams will likely produce more independent, loosely-coupled code (for more information on this correlation, see [Demystifying Conway's Law](https://www.thoughtworks.com/insights/blog/demystifying-conways-law)). What this means for us is that our communication structure not only affects our particular piece of code but the entire code-base. Therefore, as much as it is a good idea to be in tight communication with the original author, we should check that we are not too tightly dependent on the original author. Not only will this likely annoy the original author, it may also produce unintended coupling in our code.

While this may be helpful to delve into our code, we are assuming that the original author can be reached. In many cases, the original author may have left the company or is just unreachable (i.e. on vacation). What do we do in that case? Ask someone who may have an idea about the code. This does not have to be someone who actually worked on the code, but it could be someone who was around when it was written or knows the person who wrote it. Even getting an idea from those around the author can shed some light on an otherwise unknown piece of code.

## 3\. Remove All Warnings

There is a well-known concept in psychology called the Broken Window Theory that is poignantly presented by Andrew Hunt and Dave Thomas in [The Pragmatic Programmer](https://www.amazon.com/Pragmatic-Programmer-Journeyman-Master/dp/020161622X) (p. 4-6). This theory, originally developed by James Q. Wilson and George L. Kelling, states the following:

> Consider a building with a few broken windows. If the windows are not repaired, the tendency is for vandals to break a few more windows. Eventually, they may even break into the building, and if it's unoccupied, perhaps become squatters or light fires inside. Or consider a pavement. Some litter accumulates. Soon, more litter accumulates. Eventually, people even start leaving bags of refuse from take-out restaurants there or even break into cars. 

This theory states that is it human nature to disregard care for an item or thing if it appears to be uncared for already. For example, a person is much more likely to vandalize a building if it already appears disheveled. In terms of software, this means that it is human nature to make a mess of code if a developer finds that the code is already a mess. Essentially, we say to ourselves (albeit in not so many words), "If the last person didn't care about it, why should I?" or "My mess will be hidden underneath the rest of this mess."

That is no longer an excuse for us, though. The buck stops with us. Once we touch this code that previously belonged to someone else, we will be responsible for it and we will have to answer for it if it stops working. In order to make sure that we defeat this natural human tendency, we need to take small steps to make our code less disheveled (replace the broken windows).

One simple way of doing this is to remove all warnings from the entire package or module we are working with. In the case of unused or commented-out code, remove it. If we need this code later, we can always retrieve it from a previous commit in our repository. If there are warnings that cannot be solved directly (such as a raw-types warning), annotate the call or method with the `@SuppressWarnings` annotation. This ensures that we are deliberate about our code: they are not warnings by negligence, but rather, we are explicitly noting the warnings (such as raw-types).

Once we have removed or explicitly suppressed all warnings, we must ensure that the code stays warning-free. This has two major implications:

  1. It forces us to be deliberate with any code we create.
  2. It reduces the change of code rot, where warnings now result in errors later.

This also has the psychological side-effect of showing others, as well as ourselves, that we actually care about the code we are dealing with. No longer is this a collection space, where we hold our nose, make a change, commit, and never look back. Instead, we are deliberate in our responsibility for this code. This also aids in future development, showing future developers that this is not a warehouse with broken windows: it is a code-base that is well maintained.

## 4\. Refactor

Refactoring has become a very overloaded term in the last few decades and has recently become synonymous with any change to currently working code. Although refactoring does involve changes to code that is currently working, that is not the entire picture. Martin Fowler, in his aptly named seminal book on the topic, [Refactoring](https://www.amazon.com/Refactoring-Improving-Design-Existing-Code/dp/0201485672), defines refactoring as:

> A change made to the internal structure of software to make it easier to understand and cheaper to modify without changing its observable behavior. 

The key to this definition is that it involves a change that does not alter the _observable behavior_ of a system. This means that when we refactor code, we must have a means of ensuring the externally visible behavior of the code does not change. In our case, this means in the test suite that we inherited or developed ourselves. In order for us to ensure that we have not changed the external behavior of our system, each time we make a change, we have to recompile and execute the entirety of our tests.

Additionally, not every change we make is considered a refactoring. For example, renaming a method to better reflect its intended use is a refactoring but including a new feature is not. In order to see the benefit of refactoring, we will refactor the `SuccessfulFilter`. The first refactoring we will perform is [Extract Method](https://refactoring.guru/extract-method) to better encapsulate the logic for the net salary for a person:
    
    
            return person.getAge() < 30 && getNetSalary(person) > 60000;
    
    
            return (((person.getSalary() - (250 * 12)) - 1500) * 0.94);

After we make this change, we recompile and run our test suite, which continues to pass. Already, it has become easier to see that success is defined by the age and the net salary of a person, but the `getNetSalary` method does not seem to belong to the `SuccessfulFilter` as much as it does to the `Person` class (the tell-tale sign is that the only argument to the method is a `Person` and the only call the method makes is to a method of the `Person` class, thus there is a strong affinity to the `Person` class). In order to better situate this method, we perform a [Move Method](https://refactoring.guru/move-method) to move it to the `Person` class:

In order to clean this code up further, we perform multiple [Replace Magic Number with Symbolic Constant](https://refactoring.guru/replace-magic-number-with-symbolic-constant) actions for each of the magic numbers. In order to find the meaning for each of these values, we may have to talk to the original author, or someone with enough domain knowledge to lead us in the correct direction. We will also perform more [Extract Method](https://refactoring.guru/extract-method) refactorings to ensure our existing methods are as simple as possible.

We recompile and test, and find that our system still works as intended: we have not changed the external behavior, but we have improved the reliability and internal structure of the code. For a more involved list of refactorings and the refactoring process, see Martin Fowler's [Refactoring](https://www.amazon.com/Refactoring-Improving-Design-Existing-Code/dp/0201485672) and the excellent [Refactoring Guru website](https://refactoring.guru/).

## 5\. Leave it Better Than You Found It

The final technique is strikingly simple in concept and difficult in practice: leave the code better than you found it. As we comb through code, especially someone else's code, we have a tendency to add our feature, test it, and move on, paying no mind to the software rot we contributed or to the additional confusion our new methods may have added to a class. Therefore, the entirety of this article can be summed up in the following rule:

> Whenever we make a change to code, ensure that we leave it in a better condition than when we found it. 

As previously stated, we are now responsible for the damage to that class or code we have altered, and if it does not work, we will be responsible for fixing it. In order to combat the entropy that accompanies production software, we have to force ourselves to leave any code we touch better than we found it. Instead of shying away from the problem, we have to pay up on the technical debt, ensuring that the next person who touches this code will not have to pay the price, with interest. Who knows, it may be us in the future that will be thanking ourselves for that _stitch in time_.
