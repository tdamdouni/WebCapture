# Using Keywords to Support Behavior-Driven Development

_Captured: 2017-02-10 at 20:37 from [www.techwell.com](https://www.techwell.com/techwell-insights/2015/04/using-keywords-support-behavior-driven-development?utm_content=bufferd5d76&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

![](https://www.techwell.com/sites/default/files/stories/images/cropped_teasers/Beth%20Romanik/2015/figure%200%2C%20sweater.png)

Behavior-driven development (BDD) and keywords are both widely used techniques to facilitate automated testing. The approaches are similar in that tests can be written in a business-readable, domain-specific language.

How the approaches are used is largely up to the teams using them, but from the projects I have seen, it seems BDD scenarios work best for communication among domain users, developers, and testers. When you want to use them for automation, they need more details than humans would need.

BDD tests can be efficiently automated with keywords, thus avoiding the need of a scripting or programming language like Ruby or C# and minimizing the involvement of developers.

Here is an example from Wikipedia of a simple BDD scenario:

Given a customer previously bought a black sweater from me  
And I currently have three black sweaters left in stock  
When he returns the sweater for a refund  
Then I should have four black sweaters in stock

It follows the familiar "GWT" ("given-when-then") format. It is ubiquitous, or readable by all people involved in a project, and the scenarios can be used as a source for automation. Keywords have similar properties. They can also be made domain-specific and thus form a ubiquitous language for all to understand.

One way to support BDD scenarios with keywords is depicted here. The lines in the scenario are mapped in a spreadsheet format to "actions" that each have a keyword and arguments to describe the activities and verifications the test needs to do:

![One way to support BDD scenarios with actions: using keywords in a spreadsheet format](https://www.techwell.com/sites/default/files/shared/figure%201%2C%20using%20actions.png)

> _One way to support BDD scenarios with actions: using keywords in a spreadsheet format_

The actions used have a similar level of abstraction, staying in the language of the business domain. However, in this example they add some details, like a transaction number typically needed when handling a return, and making the initial number of sweaters a variable so the test is less dependent on the exact number of sweaters available.

An additional approach to let actions support BDD is to use a two-way automated mapping between phrases and actions. I made a utility to do this that uses mapping rules:

![Two-way automated mapping between phrases and actions](https://www.techwell.com/sites/default/files/shared/figure%202%2C%20mapping.png)

> _Two-way automated mapping between phrases and actions_

The mapping utility can be used to represent the same scenario in both BDD and actions and move from one format to the other efficiently:

![The mapping utility can be used to represent the same scenario in both BDD and actions and move from one format to the other](https://www.techwell.com/sites/default/files/shared/figure%203%2C%20conversions.png)

> _The mapping utility can be used to represent the same scenario in both BDD and actions and move from one format to the other_

Notice that words like _three_ and _four_ are translated by the utility back and forth to numbers. The utility also takes care of plurals and singulars, as you can see with the _sweater_ and _sweaters_.

In the action-based approach, in particular in a tool like TestArchitect, the high business-level actions used above can be automated by combining lower level actions like "click" (from the tool's library) in a straightforward way. Even nontechnical testers can usually take care of this.

With approaches like this, testers can efficiently create and detail scenarios and automate them with little or no involvement from busy developers. At the same time, the verbose scenarios can be used whenever needed to illustrate clearly what needs to be tested, either for humans to understand or for automation to execute.
