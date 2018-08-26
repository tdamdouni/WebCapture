# Let’s Lean on Lean (What's in the Metrics: Part 2)

_Captured: 2018-08-09 at 00:20 from [dzone.com](https://dzone.com/articles/lets-lean-on-lean-whats-in-the-metrics-part-2?edition=385348&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-08-08)_

Take Agile to the next level with DevOps. Learn practical tools and techniques in the three-day [DevOps Implementation Boot Camp](https://dzone.com/go?i=299507&u=http%3A%2F%2Ftechtowntraining.com%2Fcourses%2Fdevops-implementation-boot-camp-icp-fdo%3Futm_source%3Ddznoe%26utm_medium%3Dheader%26utm_content%3Dcourse). Brought to you in partnership with [Techtown](https://dzone.com/go?i=299507&u=http%3A%2F%2Ftechtowntraining.com%2F%3Futm_source%3Ddznoe%26utm_medium%3Dheader).

"Hey Ramesh, we understand cumulative flow now and we also know which flow has longer cycle time. What should we do next to optimize the flow?" This a question I've received from folks who read the article on [cumulative flow diagram](https://dzone.com/articles/whats-in-the-metrics).

Let's revisit our flow diagram:

![Image title](https://dzone.com/storage/temp/9879093-cfd-5.jpg)

> _Image title_

It's evident that the cycle time is higher for work items in the flow "In Progress->Done" compared to the "Done->Shipped" flow. Let us see how we can optimize the flow.

Value stream mapping is a powerful method for identifying the waste in the entire process flow and helps to achieve the desired state. It is one of key Lean concept in manufacturing systems, but is also applicable almost in every domain. Though it has several symbols, flows, and guidelines to follow, the approach is quite simple with identification of value added, and non-value added steps in the entire flow.

Let me explain this with some examples from the development flow ("In Progress-Done" as above):

  * **Building code with built-in quality:** Value-added step.
  * **Code review:** This may be a bit confusing as this sounds important. But if we ensure the built-in quality during coding, we may not require this additional step. However, we also need to see the cost of quality if the defect is detected late in the cycle. Hence, this may be an example of a non-value added but necessary step.
  * **Build time:** Waiting for the latest build is a classic example of a non-value added step and falls into the standard type of "Delay/wait time" waste.
![Value Stream Mapping](https://dzone.com/storage/temp/9879107-lean.png)

> _Value Stream Mapping_

Lead time is what the customer feels, and value-add is what they are willing to pay for. For an ideal Lean flow, the value-add should be the highest with optimal value enablers and minimal to none non-value add.

While value stream mapping seems to be simple and straight-forward, listing below five critical points to be considered for effective outcomes:

  * **Classification is critical:** For each process step, it's important to classify (value add, non-value add but necessary, non-value add) from customer perspective than how we perceive it to be. It is possible that value-add for one process may be non-value add for another process. Also, it need not be always the cost customer willing to pay, it's equally important to understand the cost we need to avoid (in the above example, the code review will limit the cost of quality) to arrive at the proper classification.
  * **Every process step counts: **
    * What's the big deal about ignoring non-value added steps that take only few seconds? Well, think of this process step not being followed 100 times, 1000 times and so on.
    * What about the process steps we don't own? Most of the time these steps are put in a black box and we tend to leave this as is. It is immaterial if these are internal or external, we need to work with everyone involved to identify the waste at every stage. System thinking is critical in striving towards perfection. As [John Shook](https://www.lean.org/WhoWeAre/LeanPerson.cfm?LeanPersonId=4) states, "Lean isn't lean if it doesn't involve everyone".
  * **The process must tell the real story**: The value stream should depict what's happening in the proces, not what we think it could be. It's important to understand the domain or have someone with domain expertise help us putting value stream together.
  * **Scenarios**: Lead time of any process may vary time to time, which leads to the question of what to represent for value-added and& non-value added steps, best case, worst case, or regular scenario? It depends on the frequency of each scenario. Value stream mapping gives the visualization of as-is process and what represents the current process should be captured - it could be average, minimum, maximum or any other statistical measures.
  * **Automation is the cure for everything**: Manual effort reduction through automation is great. But if we are automating the process without Leaning it, we are just converting manual waste to digital waste. Let us not forget about the resources required to perform operations even if the process steps are automated.

Value stream mapping is extremely resourceful in identifying and eliminating the waste in the flow when it is leveraged in the right spirit. Over a period, the value-added steps might turn into something customer don't want. It's important to revisit the value stream mapping and optimize it frequently. After all, Lean is not a one-time activity.

Adopting a DevOps practice starts with understanding where you are in the implementation journey. Download the [DevOps Transformation Roadmap](https://dzone.com/go?i=299508&u=http%3A%2F%2Ftechtowntraining.com%2Fresources%2Ftools-resources%2Fdevops-transformation-roadmap%3Futm_source%3Ddznoe%26utm_medium%3Dfooter%26utm_content%3Dguide). Brought to you in partnership with [Techtown](https://dzone.com/go?i=299508&u=http%3A%2F%2Ftechtowntraining.com%2F%3Futm_source%3Ddznoe%26utm_medium%3Dfooter).

Topics:

lean agile management leadership ,value stream mapping ,flow efficiency ,cycle time ,value ,agile
