# Technical Debt: Everything You Need to Know

_Captured: 2017-06-12 at 13:49 from [dzone.com](https://dzone.com/articles/technological-debt-everything-you-need-to-know?edition=304169&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-11)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

Sometimes there comes a date which must be circled on the calendar. It looks different for different people: for a programmer, it can be a "spaghetti code" where it is necessary to add a new feature, and for an IT Director it will be the need to implement a new tool and integrate it with a complex ecosystem of years of patchwork IT infrastructure. Something that connects these situations, a specific phenomenon which often occurs at the last minute, may be something we are not yet aware of - the phenomenon of technical debt. This debt, even subconsciously, gives us a sense of comfort, as it allows us to indefinitely postpone hard decisions, effort, or even admitting a mistake. And this is life on credit, which Billy Gibbons warned of when he sang: "It's too easy, it's too easy to feel good."

## Get to Know Your Enemy

Technical debt means additional work that must be done in order to accomplish a task, due to past neglect within the project. This phenomenon often occurs in IT projects when negligence in terms of the work done means that there is a time-based debt which should be devoted to getting the project up to the expected state. In the earlier example of the IT Director, facing the challenge of the implementation of new tools, paying off the debt will be based on the fact that integration with obsolete and poorly-documented infrastructure, which may have been used for years, is likely to be a long and painful process. In addition to the implementation process, a lot of work will have to be undertaken to adapt the entire system and repair unsolved problems which have built up over the years.

Debt is also used to refer to problems that arise in sloppily written code. Personally, I am inclined to say that the problems themselves are not technical debt, but more interest on the debt incurred. **We incur debt while doing any activity that contributes to the delivery of any code which is not quite up to expectations, not only in terms of the tasks to be undertaken, but also performance, readability, maintainability, and how it can be developed in the future**. There may be many reasons for this state of affairs.

## The Sources of Technical Debt

To face up to a challenge which puts us in technical debt, we must take a look at the causes, among which the following phenomena can most often be found:

  * Lack of employee involvement in the tasks to be undertaken.
  * Insufficient coverage of functionality in terms of testing.
  * Lack of automated testing.
  * Outdated tools/technologies used in the project.
  * Lack of experience on the team.
  * Time pressure.
  * Lack of documentation/low quality of documentation.

This list is not complete, of course, and some aspects may be closely linked to each other. Programmers can write low-quality code for many reasons: because of a lack of motivation, knowledge or experience, or because of time pressure or lack of proper tools. The programmer is often only an indirect cause of the debt, as management of this debt is the responsibility of the project manager who makes decisions regarding time, tools, technology, and how they are allocated - without outside input. Sometimes it is difficult to identify the causes of the debt. Small errors in a project or strategic decisions - such as the need to provide a solution in a very short time - can lead to the creation of such debt. The origins of the phenomenon in each project can vary and are very complicated, but it does not change the fact that, regardless of its origin, technical debt must be managed effectively.

## Debt's Not Always That Bad

It would be a mistake to unambiguously define technical debt as something that should always be avoided at all costs. Just as a loan may allow the company to spread its wings, technical debt, if incurred reasonably, can be helpful in many cases.

Technical debt may be divided into [three types](https://agilemichaeldougherty.wordpress.com/2015/07/24/types-of-technical-debt/), which clearly show that not all debts are created equal:

  * **Naive debt** - resulting from negligence, bad practices, and immaturity in business.
  * **Unavoidable debt **- debt which we are not able to predict. Good decisions taken today may be a cause of debt in the future.
  * **Strategic technical debt **- debt is incurred consciously, when the benefits incurred are greater than the consequences.

It may turn out that the incurrence of debt brings with it very tangible benefits, especially in such situations as when the project hangs in the balance and providing a sufficient batch of code becomes the be-all-end-all for the project. The decision to incur such debt could even save the whole project (and sometimes the entire company). One should, however, take extreme care when making this type of decision, because poor management of the resulting debt can lead to disaster.

## Am I in Debt?

If we are aware of our debts, we are able to pay them off regularly - the debt itself is not a problem if it doesn't harm ongoing operations. Ignorance, in this case, is absolutely not bliss, because we do not expect the impact, nor do we know when it will occur. Fortunately, in IT projects, symptoms that indicate the existence of the technical debt appear quite quickly and are visible to the naked eye.

Here are a few diagnostic questions:

  * Does the programming solution work slower and slower?
  * Is there partial or total downtime in the operation of the system?
  * Are the same errors repeating themselves?
  * Is the time taken to implement new solutions constantly increasing?
  * Does the application work slowly?
  * Are your programmers reluctant to work on the project?
  * Did you push your team to implement new functionalities quicker than planned?
  * Are there instances of errors which are difficult to recreate or solve?

Even if the answer to all these questions is no, you should not feel overly safe. Some experts are of the opinion that technical debt is a permanent element of the possession or development of software and IT infrastructures.

So let's assume that technical debt occurs in every IT project in some form. This means that the effective management of the debt is very important. In other words, it is not enough to merely control and neutralize the effects - much more important is a [methodical approach to the quality](http://nearshore-it.eu/images/stories/Folder_QA_eng_jcommerce.pdf) of the application, and preventing the occurrence of debt where we don't want to incur it.

## How to Manage Debt

You need to manage debt and fight it on all fronts. The following are of crucial importance:

  * **Building awareness of the importance of quality within the company**. Quality itself must be seen as a value which we should care about. Without this, it's difficult to manage debt, because we can't do much without the proper approach from employees. Their involvement is key.
  * **Controlling processes**. Constant feedback about what's going on in the project helps us to react quickly when issues arise.
  * **Quality assurance**. Caring about the quality of software, getting it checked by specialists, not just in terms of testing, but including all aspects of quality.
  * **Tests**. The quicker testing begins, the sooner problems can be found. Tests at the level of documentation and unit testing eliminate debt very quickly.
  * **The application of best practices**, such as: 
    * Adherence to rules for naming functions, procedures, etc.
    * The application of coding style, involving the introduction of appropriate indentation.
    * The creation of technical documentation.
    * The prevention of basic mistakes, e.g. table overflow, problems with the initialization of variables, etc.
    * Management of versions/backups.
    * Refactoring - the improvement of the code in order to obtain better readability, easier maintenance, and future development.
    * Algorithmics - simplifying functions.
    * Pair programming - to create better quality code.
    * Code review - reflecting on those solutions used, and the removal of visible errors.
  * **Training employees.**
  * **Promotion of unit testing**. As a basic tool, including TDD as a standard tool for creating software for programmers.

Just as before, unfortunately, this list is incomplete, as debt can have very different sources, often specific to a particular company, or even a project. A company should, therefore, develop its own technique of debt management - most importantly, it should not ignore debt until it's too late - until disaster strikes and the bailiffs knock on the door.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
