# 5 + 1 questions a requirements traceability matrix answers

_Captured: 2017-07-07 at 07:00 from [blogs.itemis.com](https://blogs.itemis.com/en/5-plus-1-questions-a-requirements-traceability-matrix-answers?utm_source=hs_email&utm_medium=email&utm_content=53882164&_hsenc=p2ANqtz-8728ImoOag1619D2qxLKQHCDXAElXwn8MxyiqRYZwAqLlxyd9jtELcXOtgM8JyR5NLEedZ6fDY9gVjK5a0oIU8VgTmxw&_hsmi=53881289)_

In the previous part we had a short introduction to requirements traceability and took a look at [how to create a requirements traceability matrix](https://blogs.itemis.com/en/how-to-create-a-requirements-traceability-matrix). Now it is time to see how we can harness the information it contains and use it to answer five important questions in day-to-day project work.

To have a simple example at hand we will assume the following very simple traceability graph, where we trace from "Customer Requirements" to "Tests".

![trace-from-customer-requirements-to-test-traceability.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Traceability/trace-from-customer-requirements-to-test-traceability.png?t=1499351211930&width=2172&height=150&name=trace-from-customer-requirements-to-test-traceability.png)

From this graph we derive a set of traceability matrixes that again are extremely simple to keep this post comprehensible.

![set-of-traceability-matrixes.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Traceability/set-of-traceability-matrixes.png?t=1499351211930&width=2172&height=786&name=set-of-traceability-matrixes.png)

For each link in our trace graph we created a matrix, each containing the existing artifacts and how they are linked. We also added a fourth matrix that condenses the other three into a single view. If you'd prefer a slightly bigger example feel free to download the Excel sheet used in part one.

## Question #1: Are you building the product correctly?

This is the classic example of **forward traceability**. Customers or stakeholders usually accept a product only if it fulfills all the requirements that have been specified. With proper traceability in place, you won't have any problem to verify that you have built exactly what has been agreed upon. Use the set of traceability matrixes to determine whether each requirement is covered by a test case, and to ensure that these test have been executed successfully. Sometimes a requirement can only be tested meaningfully by testing its derived development artifacts. In this context, I'd like to recommend an excellent blog post about [requirements coverage and how it can be analyzed](https://blogs.itemis.com/en/what-is-requirements-coverage-and-how-can-it-be-analyzed), if you want to dig deeper into this complex topic.

The minimalistic approach, however, is to analyse the coverage by following the traces from each requirement to its implementation or realisation, and from the implementation to the test case that confirms it is working as specified. In the example above, you could follow e.g. the trace from "CustReq. 1" to "IntReq. 1" to "Impl. 1" to "Test case 1".If all of your requirements are linked to test specifications that are linked to successful test, your work is done. You have created what has been specified and, more importantly, you are able to prove that it works as intended.

In the example above, however, there is still quite some work to be done, since you can't follow any trace from customer requirements 2 and 3 to any test case that confirmed their fulfillment.

## Question #2: Are you building the right product?

**Backward traceability** allows to find validations or development artifacts that are not derived from any requirement. In other words, there should be a trace from each test and each development artifact back to a top-level requirement. The rationale is that projects are usually short on time and budget, therefore it is crucial to assign available resources to only implement what has been required.

Whenever you find features or other development artifacts in your product that cannot be traced back to a requirement, you either have a visionary on your team who can predict the next feature request - or you are wasting valuable resources. This is especially problematic if other requirements - those that have been agreed upon - are not being worked on. In this case, you are basically not developing the right product.

When reading the traceability matrix in the opposite direction, i.e. from development artifact to requirement, it's easy to identify ghost features that should not be part of the product. For example, have a look at "TestCase 2": It is linked to "Impl. 2"_, _which makes sense, however, the latter is not connected to any internal requirement and can thus not be traced to any customer requirement as well. So the feature "Impl. 2" has never been requested by a customer. From the perspective of to build only what has been specified, this feature is obsolete, should not be tested and should not have been implemented in the first place.

However, be aware that not all features that you find this way are "useless" or "too much"! You findings might also indicate that your requirements are incomplete. Possibly important aspects of the product have been overlooked, forgotten or underestimated when engineering the requirements. This happens all the time, and as long as you have a good awareness of the current situation, it is possible to manage it properly and make informed decisions.

## Question #3: What is the impact of change?

In most cases, requirements are not set in stone. Sometimes customers change their minds, the market situation changes, or new legislation has to be considered. Obviously changes can also be introduced, because you gained new knowledge about the domain or your users.

In her recent blog post "[How to convince customers of design decisions by the use of traceability"](https://blogs.itemis.com/en/how-to-convince-customers-of-design-decisions-by-the-use-of-traceability), my colleague [Sandra Schering](https://blogs.itemis.com/author/sandra-schering) describes the importance of impact analysis from the perspective of an usability engineer.

No matter the reason, requirements will change over time. And whenever this happens, it raises important questions:

  1. How long will it take to implement the change?
  2. How expensive will it be? (Who will pay for it?)
  3. Do I still have the right development resources? 

To answer these questions, you first have to find all relevant information related to the changed requirements. Then assess the impact of each of them individually. Let's say that you have great domain experts who have the necessary experience and knowledge to do the individual assessments. However, the biggest challenge is to find out which artifacts are affected by the change in total. Especially in big projects with tens of thousands of requirements and artifacts it is nearly impossible to take everything into account, at least without a traceability tool.

Luckily we have a set of requirements traceability matrixes that contain all the links from the changed requirements down to the last well-hidden line of code.

Take a look at the example and assume "CustReq. 1" has changed. You can easily derive that this impacts "IntReq. 1" and "IntReq 3", both of which are linked to tested implementations. So in total six development artifacts are affected by the change of a single requirement.

While you still need to analyse the impact on each individual artifact, you can be sure that you are always looking at the complete picture. This makes your impact analysis more reliable and empowers you to make the best-informed decisions possible.

## Question #4: What it the status of the project?

Admittedly this is obvious, but customers and bosses want to be informed on the progress. Most likely they won't settle with your word that "it is coming along fine", so you need some data to back your statement. Luckily the traceability data contains the information we need to quickly access the current project state.How many requirements are there in total? How many requirements have been implemented and tested successfully? Just iterate along the traces in your RTMs and you will have the answers.

At the current state of the example, "CustReq. 1" is fully implemented according to the specification, while for "CustReq. 2" at least Internal requirements have been derived. "CustReq. 3" has not been touched at all. Depending on the level of detail that is required, the RTM can help you to provide reliable project status information whenever you need it.

If you save the metrics regularly, it's is easy to monitor progress (or lack thereof) over time.

## Question #5: What to do next? + How to manage and plan work?

One of the challenges in project management is to determine when to do what. Clearly this is a complex task that relates to many different aspects and is definitely a topic of its own. One aspect, and in my eyes not the least important one, is to know how different development artifacts, and the tasks meant to produce them, are related to each other and which dependencies exist amongst them. In [part one](https://blogs.itemis.com/en/how-to-create-a-requirements-traceability-matrix) of this series we also discussed that it makes sense to order requirements in the matrix according to their priorities. The combination of priority and traceability gives you a thread to follow.

Let's have a last look at the example and derive some tasks from it.

  * Find and clarify inconsistencies (backward traceability): 
    * _"_Impl. 2" and "Impl. 5" are not linked to any internal requirement. What is their purpose? Why are they there? Who is responsible? Is it an error in the traceability or in the project? -> Fix it!
    * _"_IntReq. 4" is not linked to any customer requirement. What is its purpose? Why is it there? Who is responsible? Is it an error in the traceability or in the project? -> Fix it!
  * Work towards completion of customer requirements according to their priorities (forward traceability):
    * Create implementation for "IntReq. 2".
      * Create or link suitable test cases.
    * Create internal requirements for "CustReq. 3"
      * Create or link suitable implementation. 
        * Create or link suitable test cases.

This is a tiny example for sure that is by far not comparable to any real-world project. Still it shows how a simple tool like a requirements traceability matrix maintained in Excel or a spreadsheet can help you to gain a better understanding of the complex relationships in your project, of how work can be distributed more efficiently, and how the impact of change can be assessed with confidence. Being able to make informed decisions that are based on facts instead of gut feeling, will help you to keep your project on track and your customers happy.

![how-a-requirements-traceability-matrix-answers-5-questions.jpg](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Traceability/answer-5-questions.jpg?t=1499351211930&width=2172&name=answer-5-questions.jpg)

But make no mistake, traceability is only of use if it is maintained continuously. It takes effort that dramatically increases with the size of your project. When done with discipline, this effort pays off, as research of Prof. Dr. Mader imposingly shows, see "[Benefits from requirements traceability when maintaining software"](https://blogs.itemis.com/en/benefits-from-requirements-traceability-when-maintaining-software-systems). Therefore it is crucial to have a tool that makes maintaining traceability as convenient and as simple as possible. We need a traceability tool that scales with our project. This is a topic I will address in my next blog post.
