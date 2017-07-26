# Benefits from requirements traceability when maintaining software systems

_Captured: 2017-04-06 at 17:32 from [blogs.itemis.com](https://blogs.itemis.com/en/benefits-from-requirements-traceability-when-maintaining-software-systems)_

A lot of processes and standards like Automotive SPICE, ISO 26262, IEC 61508, or DO 178b enforce traceability documentation. As a consequence, all relevant links between requirements and other artifacts in the software development process have to be maintained.

Once these trace links are available, they can be used for other purposes as well. Developers or testers can use them to navigate between related artifacts. QA-responsibles and project managers can use them to do an impact analysis for change requests and all kind of coverage analysis (implementations covered by tests, requirements covered by implementations, …).

"The ability to interrelate any uniquely identifiable software engineering artifact to any other, maintain required links over time, and use the resulting network to answer questions of both the software product and its development process. [CoEST definition of traceability]

![01_traceability-use-cases-traceability-benefits.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Traceability/01_traceability-use-cases-1.png?t=1491488351797&width=229&name=01_traceability-use-cases-1.png)

But can the benefits be quantified? How much does a development team benefit from requirements traceability when maintaining software systems?

## **Do development teams benefit from requirements traceability?**

Prof. Dr. Patrick Mader et. al. did an[ interesting empirical evaluation](http://dl.acm.org/citation.cfm?id=2769791) to answer this question. It was done in a controlled experiment with 71 subjects re-performing real maintenance tasks on two third-party development projects. In total the subjects solved 461 tasks. The findings show that subjects with traceability performed on average **24% faster on a given task** and created on average **50% more correct solutions**. That means that **traceability does **not only** save effort** but can profoundly **improve the quality of software maintenance**.

## **Study details**

For the study two existing software systems were chosen: GanttProject and iTrust. [GanttProject](http://www.ganttproject.biz) is an open-source, cross-platform tool for project scheduling, implemented in Java. iTrust is a web-based medical application that provides patients and other medical stakeholders with a means to keep up with their medical records as well as to communicate between each other. iTrust is also realized in Java. Both are of siginificant size, as outlined in Table 1.

![02_key-metrics-traceability-benefits.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Traceability/02_key-metrics.png?t=1491488351797&width=199&name=02_key-metrics.png)

The experiment included eight distinct tasks, that had to be performed by the participants - four for each software system. For Gantt they selected bug reports from the existing issue tracking system and provided them unchanged to the participants. For iTrust they compared older versions of use case specifications with current ones and selected a single change request.

![03_tasks-and-traces-traceability-benefits.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Traceability/03_tasks-and-traces.png?t=1491488351797&width=265&name=03_tasks-and-traces.png)

In addition to the time that was needed to complete the maintenance tasks, the correctness of the resulting solution was measured, as a factor of three levels: incorrect, partly correct and fully correct. Solutions were accepted if they removed the bug or led to the desired solution, even if this was not identical to the original solution of the Gantt and iTrust developers.

In order to have control of what participants could do during the experiment, they provided a specific tool with development and traceability support.

Traces were provided in a separate window and labeled with the names of artifacts they were connecting. A click on a trace opened the related source code file and highlighted the traced part. Traces were also highlighted in the file tree.

![04_tool-support-traceability-benefits.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Traceability/04_tool-support.png?t=1491488351797&width=320&name=04_tool-support.png)

A comparison of all performed tasks showed that subjects working without traceability on average spent 889s working on a task. Subjects working with traceability on average spent only 678s. That means that on average traceability facilitated a 24% faster task completion.

Comparing the correctness of performed tasks, they found that participants working without traceability created 50% correct solutions. Participants working with traceability created on average 74% correct solutions. That means that traceability facilitates 50% more correct solutions to a task.

![05_performance-results-traceability-benefits.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Traceability/05_performance-results.png?t=1491488351797&width=285&name=05_performance-results.png)

The team around Prof. Dr. Patrick Mader also asked open questions how participants would improve the provided traceability and if they had comments on the experiment. Multiple participants positively referred to traceability in general:

  * "Traceability really helped me."
  * "With traces available, I found the code sufficiently documented and have no improvement suggestions."
  * "Traceability put my focus on the relevant parts of the code and prevented me from wasting my time with understanding irrelevant code."
  * "Traceability made solving the tasks much easier."

Several participants requested additional documentation for the provided traces, for example:

  * "Sometimes traces confused me. It would be nice to have comments for them."
  * "Provide comments for traces."
  * "Provide an overview and information on traced methods."

Other improvement suggestions were:

  * "Trace more directly to the impacted code and not only to a method's corpus."
  * "Trace and highlight previous edits to the code."
  * "Show hierarchy in the traces according to the call hierarchy of the traced methods."

Multiple participants suggested tool improvements, for example:

  * "Allow to search within the traced code."
  * "Provide a visual overview of documents and highlight relevant regions."

## **Conclusion**

In the experiment traceability led to an efficiency gain of 24% and to 50% more correct solutions. All but two participants of the study replied after the experiment that they felt supported by traceability in performing.

It's important to note, that this survey only covered a subset of usage scenarios in a development process supported by traceability.

In another survey about[ „Usage Scenarios for Requirements Traceability in Practice**"**](http://link.springer.com/chapter/10.1007/978-3-642-37422-7_12) by Patrick Mader et. al. 29 different usage scenarios in six groups were identified:

  * Requirements Engineering and Management 
  * Project Management 
  * Compliance Demonstration 
  * Design and Implementation
  * Testing as well as Maintenance and Evolution 

The team asked the participants of this study, why they applied traceability in their project. The following chart shows, that there is an obvious need for better support of development activities (80%).

_![06_overview-traceability-benefits.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Traceability/06_overview.png?t=1491488351797&width=362&name=06_overview.png)_

As a conclusion, the available tool support has an important impact on the benefits and the answers of the participants suggest, that with improved and better tool support, even more benefits are realistic.

In the next blog article I will give a more detailed overview about the results of this survey.
