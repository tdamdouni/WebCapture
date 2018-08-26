# Incremental Documentation

_Captured: 2018-04-11 at 16:48 from [dzone.com](https://dzone.com/articles/incremental-documentation?edition=372193&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-04-11)_

**The Agile Zone is brought to you in partnership with [Techtown Training](https://dzone.com/go?i=275424&u=http%3A%2F%2Ftechtowntraining.com%2F%3Futm_source%3Ddzone%26utm_medium%3Dfooter). Learn how DevOps and SAFe® can be used either separately or in unison as a way to make your organization more efficient, more effective, and more successful in our [SAFe® vs DevOps eBook](https://dzone.com/go?i=275424&u=http%3A%2F%2Fpages.aspeinc.com%2FSAFe-vs-DevOps.html%3Futm_source%3Ddzone%26utm_medium%3Dfooter%26utm_campaign%3Dsafe_vs_devops%26utm_content%3Debook).**

There are no second thoughts about the need for up-to-date documentation of an application. Outdated documentation is lost knowledge and it takes great effort to re-sync the documentation than it would have taken to updating the document along with the code changes.

Earlier in my career, I had been supporting a trading application for more than a decade (which was, in turn, decades old when we started supporting the application) and obviously we had an outdated documentation. Owing to "strict timelines," we were not able to bring the documentation up-to-date and we were following the safe method of application maintenance, a.k.a the Golden Rule: "Don't touch anything that is running fine." And, we added all necessary application changes on the circumference and round-about ways. The end result is an application with lots of code bloats. Whenever that application is going to face a terminal decision, that one is sure going to be a costly affair.

Various reasons can be attributed to an out-dated documentation, and "strict timelines" as in above example, is one. Some more interesting ones are below.

### Reason 1

People start manipulating the newer process models (such as Agile and Scrum, which prioritizes "working code over comprehensive documentation") to their advantage and carry out propagandas that "in Agile method, we don't have to document." Whereas the truth is the process "prioritizes" working code over "comprehensive" documentation - two words to note here are _prioritizing_ and _comprehensive_. With stress on these two words, when we read the statement again, the meaning of that sentence meant by the Agile process is evident.

### Reason 2

There are some thought processes on the web that delineate the in-line comments/documentation reduces the code level clarity - i.e., when the coder adds generous in-line comments, he "tends" to make the code itself less understandable (such as less expressive names for the methods or variables). While this sounds logically (and psychologically) true, we need to understand one important point of concern with this approach here.

By going through a program, one can be sure about how the processing is happening, but there are situations when the programmer needs to know why it is happening. This is the crux where the business rules get represented in the code. The programmer cannot be 100% sure of "why" something is happening like the current code, without the help of either inline comments or up-to-date documentation.

The same case applies to all automated documentation tools available in the market for the newer technologies. All these tools would be able to provide how the logic flows/processing done, but not why something is happening the way it is.

Now, let us look at few ways of how to achieve up-to-date documentation.

#### Take Advantage of the Technology

There are tools available in the market that document the system in a comprehensive manner, let alone writing few scripts by the SMEs to uncover the business flow. The only gap in this approach is that they all tell us how something is happening but not why.

#### Keep the Manual Updates to the Bare-Minimum

Yes, it's a boring task, I mean, updating the documentation - but not documenting means that we are simply and happily forgetting our ATM pin (there is a huge knowledge that is going to go waste). So, keep the "manual" portion of documentation simple and clean and let most part of it to be done by automated tools. For example, instead of describing a business flow, a flowchart by automated tool would suffice and more efficient in depicting the underlying logic.

#### In-Line Comments Wherever Possible and Have Simple Scripts to Pick These up to Update the Documentation

This is another simple work-around - to put in two or three lines along with a fix you make in the code. And, run that documenting script and it picks up the comments and puts in appropriate place in the document. Thereby, you avoid trying to remember what was fixed while you later try to update the documentation.

#### The QA Process Should Be Tied to Ensuring Updated Documentation Is in Place (Either Manually Updated or Automatically)

Unless you mandate it, it highly possible that people do not follow it.

#### Awareness Amongst the New Comers to the Industry

The newer generations coming up on board is definitely not realizing the need for documentation (in stark comparison with a programmer in the last century). The management should focus on creating this awareness to the new comers.

_P.S 1: Please feel free to add in your thoughts and new ideas if any, to encourage up-to-date documentation_

_P.S 2: Hadn't done any market study on the automated documentation tools, so please excuse us if any of our suggestions seem irrelevant - but, please note that, we have the capability and working examples for the suggestions listed above with respect to updating documentation - we are specializing in the legacy knowledge extraction field for couple of years now._

**Adopting a DevOps practice starts with understanding where you are in the implementation journey. Download the [DevOps Transformation Roadmap](https://dzone.com/go?i=266427&u=http%3A%2F%2Fpages.techtowntraining.com%2FDevOpsRoadmapDzone_DevOpsTransformationRoadmap.html%3Futm_source%3Ddzone%26utm_medium%3Dheader%26utm_campaign%3Ddevops-transformation), brought to you in partnership with [Techtown Training](https://dzone.com/go?i=266427&u=http%3A%2F%2Fwww.techtowntraining.com%2F). **

Topics:

documentation ,legacy ,update document ,agile ,incremental documentation ,documentation automation
