# A Design Pattern for Automation Repeatability

_Captured: 2018-07-13 at 17:02 from [dzone.com](https://dzone.com/articles/a-design-pattern-for-automation-repeatability?edition=385232&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-07-13)_

Easily enforce open source policies in real time and reduce MTTRs from six weeks to six seconds with the Sonatype Nexus Platform. See for yourself - [Free Vulnerability Scanner.](https://dzone.com/go?i=290455&u=https%3A%2F%2Fwww.sonatype.com%2Fsoftware-bill-of-materials%3Futm_campaign%3Ddzone%252520-%252520AHC%26utm_source%3DDZone%252520-%252520AHC%2525202018%26utm_medium%3DDZone%252520-%252520AHC%2525202018)

Some of my customers are trying to design an automated script to perform specific workflows with a predicted outcome. Unfortunately, the automated workflow they want to execute has many variations in their environment, and they're having trouble creating a dynamic, automated script that handles environment deviation.

So, how do you code it? The short answer is, you don't code for variation; **you code for consistency and define the variation**. When tasked with an automated process, customers will code step by step until they reach a step that has variations, then they'll code a ton of conditionals to account for all the disparities. There is a better way to do this that will give you clear, defined end results: automated states.

Automated states are a design pattern for developing an automated process. Each process or state has its own goal and a state cannot advance unless you first achieve the goal of the previous state. Once you've achieved all states, you can repeat the processes. Automation states include the following:

  1. **Zero state**: This is to prepare your environment and ensure everything is in place and working (servers are up, connections are working, power is on) before you start automating. Once the script has successfully checked everything out, you can begin. This is also known in the industry as a Setup Script.
  2. **Define variation/alter/configuration/information gathering state**: As the name implies, this is to gather information about all the different types of variation that might take place during run time. Basically, you'll have to define all your variation at this state. What user do you log in with, what operating system will you be using, what user needs to be created, what scenario needs to be loaded, in what format does the information need to be written, what context are you looking for? You should gather all of this information from a stored single source of truth (SSoT) location, and the information should already be defined before you start the automated process - because if it's not, you can't automate it.
  3. **Executing/testing state**: Now that you've got everything set, defined all your variation, and gathered all your information, we can pull all that data from the previous state into the execution state. This will allow us to execute our automated script without a bunch of conditionals - whether it's a script for automating a testing environment or deploying something in production.
  4. **Diagnostic/reporting state**: Once you've executed the script, you need to determine if any errors surfaced and if they need to be reported to anyone. You might have found out a script needs to be altered or a workflow needs to be modified. Maybe you didn't gather enough information and need to redefine the parameters in the Define variation/alter/configuration/information gathering state.
  5. **Zero state**: Known in the industry as a cleanup script, this state is to make sure everything is set back to normal. If something went wrong in the other four states, this is the state where you reset the entire process, so you can repeatedly run the automation.

Scripting with this pattern in mind will help us step away from this question: If something changes, how do you script for that? The solution is that you should already know all the variation before you execute your script. Defining the variation might be difficult and might have to be defined manually before coding the automation process. Automation is predictable in nature and thus can be defined. The predictability allows the states to be repeatable and also allows the process to be nested, if necessary.

The diagram below shows how to handle repeatability and failures. For the nested process, let's say you have two processes (Process A and Process B) that are executed one after another, Process A will go through all automated states before handing it off to Process B, which will also go through all automated states. Both processes are part of an overarching project; the project itself will go through the automated states.

![](https://blog.testplant.com/hs-fs/hubfs/Automated%20States%20Hoirzontial.png?t=1529612022468&width=739&name=Automated%20States%20Hoirzontial.png)

Oddly enough, this process is based on human automation design patterns, like making breakfast.

  * **Zero state**: You know that the milk is in the fridge, the spoons are in the drawer, and the cereal is in the pantry cupboard.
  * **Define variation/alter/configuration/information gathering state**: Today, I'm going to use two-percent milk; tomorrow I might use whole milk. Next week, I want to use a gold spoon instead of a metal spoon. In June, I want to use only biodegradable spoons. Today, I'll eat cereal X. On Fridays ending in an even number, I'll eat cereal Y.
  * **Executing/testing state**: Set the silverware, pour the cereal, pour in the milk, and eat.
  * **Diagnostic/reporting state**: Did the milk go bad? Am I low on cereal? Maybe I didn't have enough time to eat, so I should wake up a bit earlier.
  * **Zero state**: Let me clean my dishes and silverware so that I can put them back in their original locations. I'll make sure I put the milk away and the cereal back where it was. So that tomorrow, I know where everything is located, and I can do it all over again.

Humans follow the process pretty well. These states that were designed for computer automation but can be used in psychology. We might even refer to this as a design pattern for human automation repeatability.

Here's a technical example: I have a new user, John Doe, who needs an Active Directory account.

  * **Zero state**: Active Directory is up and working, we have an Active LDAP connection.
  * **Define variation/alter/configuration/information gathering state**: The Active Directory will be based on nicknames separated by periods: John.Doe@company.com. New users with multiple last names will also be separated by periods. Cedilla will be put in as regular c; apostrophes in names will be removed; the new user with Role of X will contain Permissions of ABC. We already found another John Doe in the system, so we will create John.Doe.2@company.com.
  * **Executing/testing state**: Create a connection, add John.Doe.2@company.com to the Active Directory with Permissions ABC.
  * **Diagnostic/reporting state**: Send an email to John's manager stating that the task has been completed.
  * **Zero state**: Disconnect from Active Directory.

This design pattern is for thinking about how to automate a workflow - it's a thought experiment based on a defined end goal. These states will help you define specific workflows that you need to accomplish for your automated project. Remember, you don't code for variation; **you code for consistency and define the variation**.

Variation is determined at the **define variation/alter/configuration/information gathering state. **It's possible you have not gathered all the variation yet, in this case, you might want to run through the process manually to determine that. Once you've figured it out, write that data in your SSoT. **Define variation/alter/configuration/information gathering state** is implemented before the execution state, and the information gathered from that state is pulled into the execution state. There isn't a hard and fast rule that defines how to write the states; it might be a single script or a collection of scripts. The point is to keep this concept in mind when you want to automate a process. More than likely, you already follow these states. All I'm doing is putting terminology to a process that already exists so that you can better define your project scope.

I'd love to hear your feedback and experiences. Please use the comments to share your thoughts on the subject.

Automate open source governance at scale across the entire software supply chain with the Nexus Platform. [Learn more.](https://dzone.com/go?i=290456&u=https%3A%2F%2Fwww.sonatype.com%2Fwp-enforce-open-source-policies-with-confidence)
