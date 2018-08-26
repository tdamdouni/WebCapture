# How to Model Business Rules

_Captured: 2018-05-28 at 16:49 from [dzone.com](https://dzone.com/articles/how-to-model-business-rules?edition=379196&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-05-27)_

See why over 50,000 companies trust Jira Software to plan, track, release, and report great software faster than ever before. [Try the #1 software development tool](https://dzone.com/go?i=281431&u=https%3A%2F%2Fwww.atlassian.com%2Fsoftware%2Fjira%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Djira_adexp-custproof_global-eng_dzone-pre-post-roll-text%26utm_term%3DTry-the-number-one-software-development) used by agile teams.

Today, when you design a modern business application, you have to deal more and more with constantly changing business rules. The reason for this is that not only the software industry follows the agile path. Business processes are also subject to a permanent change. At the same time, however, business processes are becoming increasingly complex as more and more information is influencing our business world. In the following article, I will show how business processes and their rules can be modeled with the help of BPMN.

## BPMN 2.0 and Event-Based Workflows

The "Business Process Model and Notation", or BPMN 2.0, is the common standard to describe a business process. BPMN was initially designed to describe a business process without all the technical details of a software system. As a result, BPMN diagrams are easy to understand and a good starting point to talk about a business process with a technician as well as with management. The [Eclipse BPMN2 Modeler](https://www.eclipse.org/bpmn2-modeler/) provides a graphical modeling tool for authoring business processes based on BPMN 2.0. One advantage of BPMN models is that they can also be executed by a workflow engine. With this approach, it is possible to model complex business logic which previously has been hardcoded.

BPMN engines basically support two modeling approaches - a task-oriented and an event-oriented one. A task-oriented workflow engine typically executes each task immediately, sequentially or in parallel, and returns the result. JBPM or Activiti are examples of implementations of this kind of engine. In contrast to this approach, an event-oriented workflow engine manages the state of a business process and waits for events to be executed. This second approach is typically for human-centric workflow engines like [Imixs-Workflow](https://www.imixs.org/). In the following, I will show some examples how to model a business process with complex business rules based on the event-oriented approach.

Take a look at the first example:

![Image title](https://dzone.com/storage/temp/9212090-bpmn-example-02.png)

This is a typical human-centric business process. After a new ticket workflow was started, the actor (e.g. a support-agent) decides if the ticket can be accepted or is invalid. The workflow engine waits in the status "New Ticket" until one of the events is fired. The exclusive gateway after the initial task is a so-called "Event-Gateway" with two exclusive events.

Events can also be concatenated to cause a sequential execution of different events. For example, to send an e-mail after a new task was submitted:

![Image title](https://dzone.com/storage/temp/9212091-bpmn-example-05.png)

This is called a follow-up event. The workflow engine will automatically fire the event "Send E-Mail" after a new ticket was submitted. We will shortly see how these events can be used to execute different business rules.

## Conditional Events

Now let's talk about more complex situations and how to model them. As I have already indicated in the beginning, business processes are often influenced by what information is available. Let us assume that an event triggers different tasks depending on the information which is available in the business task. In this situations conditional events can be used:

![Image title](https://dzone.com/storage/temp/9212094-bpmn-example-06.png)

In this example, an exclusive gateway is placed after the "Submit" event. The gateway has two conditional sequence flows (SL=1 and SL=2). Conditions can be declared within the model:

![Image title](https://dzone.com/storage/temp/9212095-bpmn-example-06a.png)

So the business logic is now part of our model and can be easily changed and adapted if the business rules will change.

## Split Events

Another situation is the need to split a task so it can be processed in parallel by different actors. In BPMN we use an inclusive gateway to start processing in parallel. The workflow engine creates a copy of the running process instance. Both instances are still running in the same model but can be processed by different actors or manage business data in different ways. A situation where this modeling approach is often used is to duplicate or archive business data. See the following example:

![Image title](https://dzone.com/storage/temp/9212098-bpmn-example-07a.png)

In this example, when a new "Offer" was rejected, the current version of the process instance will be archived and a new version will be continued in a change process.

Of course, this variant can also be combined with other variants. Take a look at the following example which combines a conditional event with a split event:

![Image title](https://dzone.com/storage/temp/9212103-bpmn-example-07.png)

In this example, the ticket with _ServiceLevel=1_ will be split into a "Medium Ticket" and a "Reporting" task. Both instances are running still in the same model but can be processed in different ways.

## Working with Different Business Models

The business logic we have modeled so far was restricted to one workflow model. But it is, of course, also possible to start new process instances in another workflow model. This is called a sub-process which is triggered by the main process but runs in an independent workflow model. See the next example:

![Image title](https://dzone.com/storage/temp/9212104-bpmn-example-08.png)

In this example, a "Sales" process provides the management of customer data. In case a new customer data was submitted, the model tests if an offer is available. If yes, a new sub-process "Order" is triggered. This process runs in a completely independent workflow model. But the workflow engine is aware of the "parent-child" relationship which allows the subprocess to interact with the parent process. For example, the submit event of the "Order" process can send business data back to the "Sales" process.

The creation of a sub-process is bound to the event "submit order":

![Image title](https://dzone.com/storage/temp/9212105-bpmn-example-08a.png)

> _This is a powerful function to control and link different processes._

## Conclusion

After this brief insight into the possibilities of modeling business logic with the help of BPMN 2.0, it becomes clear what advantages result from this. First of all, the business logic becomes more transparent because now business rules become visible and understandable. Secondly, business rules can be changed without having to change the source code of the application. This is an important factor to be able to react quickly to changes in an agile environment. In addition to these obvious advantages, BPMN also makes it possible to design very complex business rules and process flows which can be executed by a workflow engine. It may take some time to familiarize yourself with those concepts, but the benefits of creating a modern and flexible business application are worth the effort. The open source project "[Imixs-Workflow](http://www.imixs.org/)," which provides a free event-orientated workflow engine, provides additional information and more examples.

The Best teams run on _[Jira](https://dzone.com/go?i=292444&u=https%3A%2F%2Fwww.atlassian.com%2Fsoftware%2Fjira%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Djira_adexp-psa-exp_global-eng_dzone-pre-post-roll-text%26utm_term%3DTry-the-number-one-software-development)_. Here's how teams at a few of the world's most recognizable brands are teaming up in Jira to build great software that users love. _[Learn More](https://dzone.com/go?i=292444&u=https%3A%2F%2Fwww.atlassian.com%2Fsoftware%2Fjira%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Djira_adexp-psa-exp_global-eng_dzone-pre-post-roll-text%26utm_term%3DTry-the-number-one-software-development)_.
