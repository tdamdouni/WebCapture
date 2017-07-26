# How to create a requirements traceability matrix

_Captured: 2017-04-13 at 23:58 from [blogs.itemis.com](https://blogs.itemis.com/en/how-to-create-a-requirements-traceability-matrix?utm_source=hs_email&utm_medium=email&utm_content=50499857&_hsenc=p2ANqtz-82-fM7-RdzgrpWHxFWIznxk0DzWpzLipiI6pVZbdBGcjL_rVri2XBpqbKw8lW1qlhQA7I9kDMYSUXba7oDahcC2wpxCQauRKZ9-Dac4k9MVYWQjKM&_hsmi=50498919)_

In this blogpost I'll tell you what a requirements traceability matrix (RTM) is and how you can create it. If you are new to requirements traceability, here is a short recap to get you started.

The term [traceability](https://en.wikipedia.org/wiki/Traceability) is used in a large variety of different contexts, while this article only considers [requirements traceability](https://en.wikipedia.org/wiki/Requirements_traceability). It is basically defined as the ability to track each requirement from its origin through the entire development to its validation on each level.

![\(Customer Requirements <-&gt System Requirements <-&gtDetailed Software Architecture <-&gt Code\) <-&gt Validation](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Traceability/requirements-traceability-graphic.png?t=1492099761217&width=320&name=requirements-traceability-graphic.png)

> _(Customer Requirements <-> System Requirements <->Detailed Software Architecture <-> Code) <-> Validation_

The graphic above shows a very simple representation of a traceability graph on an abstract level. The _blue_ nodes represent different development artifact types. The _green_ nodes are the _validations _that ensure the quality and proper implementation of the artifact. Direct connections are referred to as links, while _link chains_ are called traces.

The structure and the level of detail that is appropriate for your **traceability graph**, obviously depends on your product and the process you are following. When developing a website for a local tailor, it looks different as if you're building safety relevant car parts or medical equipment. However, introducing traceability and using it for analysing your project, is beneficial in any case. Learn more about the [benefits of requirements traceability in software projects](https://blogs.itemis.com/en/benefits-from-requirements-traceability-when-maintaining-software-systems).

**Traceability** can be evaluated in different directions. There is **forward traceability **(e.g. requirement to validation) and **backward traceability **(validation to requirement). Each direction allows to assess different aspects of the project state and will be most beneficial for different roles in the project team. Clearly the goal is to establish **forward and backward ** traceability, which is consequently referred to as **bidirectional traceability. **This is where the traceability matrix comes into play.

## What is a requirements traceability matrix?

A **requirements traceability matrix** (RTM) is a simple and effective tool that allows to establish and maintain **bidirectional traceability** for your project.

As the name suggests a RTM is nothing more than a table that displays the relation between different development artifacts. Due to its simplicity it can be created with the most basic tool. It sometimes even makes sense to draw it on a white board to make it visible to everyone on the team. Depending on the purpose you are creating the RTM for, it can visualize direct links between 'linked' artifacts, shows cumulated views on entire 'traces'.

Here is a very simple example of a requirements traceability matrix that represents a cumulated view of an entire _trace graph_ from "Requirement" to "Validation"and can be maintained in any basic spreadsheet tool.

![Excel-Speadsheet: Requirements Traceability Matrix \(RTM-example\)](https://blogs.itemis.com/hs-fs/hubfs/Blog/YAKINDU%20Traceability/requirements-traceability-matrix-example.png?t=1492099761217&width=340&name=requirements-traceability-matrix-example.png)

> _Excel-Speadsheet: Requirements Traceability Matrix (RTM-example)_

Note that it does not contain the concrete development artifacts, but references them by an unique ID. Although there are good arguments to include more detailed information about the artifacts this would reduce the simplicity and make the information more difficult to access and less easy to comprehend. Traceability is only useful if it's maintained properly, and it's only maintained when it's as simple as possible.

The example represents a compressed representation of the project state. Showing the relations between requirements (Req. 1-15) and validations (Val 1-13), in many to many cardinality. Whenever a requirement is traceable to a validation it's marked with an 'x'. In the sense of **forward traceability** you can see at a glimpse that _Req. 10, Req. 11, Req. 13_ are not validated properly. When flipping the reading direction (**backward traceability)** it is obvious that _Val. 9 _validates no requirement. At this point it's important to understand that the RTM for its own can't tell you what and why there's a problem, but it's extremely efficient in identifying problems and where to look for them.

In a future article we'll shed some additional light on how to exploit all the information that's contained in a RTM, but for now let's concentrate on how establish detailed traceability for an entire project.

## How to create a traceability matrix?

There are only three mandatory steps required to establish traceability for your project. If you're willing to go the extra mile and take a fourth step you'll be able to boost your benefits even further. Let's get started. [Feel free to have a look at the attached example and adapt it to your needs](https://info.itemis.com/en/yakindu/traceability/example-matrix/).

### Identify your "artifact types"

First of all you need to find out which types of artifacts are involved in your project. What do you want to keep track of? What's relevant and useful for your team? What's required by the customer or other authorities? Make sure each artifact can be identified by a unique ID later.

For the purpose of this example we chose 4 artifact types _Customer Requirements, Internal Requirements, Implementation _and _Test Cases._

Other examples for artifact types are:

  * requirements (system-, hardware-, legal requirements)
  * UI-design-documents (paper prototypes, mock ups, style guides, mood boards,...)
  * software architecture (component diagrams, statecharts, class diagrams) 
  * implementation (interfaces, protocols)
  * tests (unit test, manual tests)

### Define the relations between those artifacts

The next step is to define how the artifacts should be linked to each other. You should only consider direct links. The example contains three link types _Customer Requirements_ _to_ _Internal Requirements, Internal Requirements to Implementation _and _Implementation to Test Case._

Other link examples are:

  * customer requirement <--> system requirement
  * software requirement <--> software architecture 
  * software detailed design <--> implementation (code)
  * implementation (code) <--> unit test

When creating your links make sure that each artifact type can be traced back to a requirement. It often helps to draw a sketch of your traceability graph to visualize it. If you end up with artifacts types that are not (at least transitive) connected to a requirement you either missed a link type or it's arguably not important for your project at all.

### Create a traceability matrix for each link between artifact types

Finally we need to create one traceability matrix for each link type. List one link participant on one axis, the other one on the other. Use the sketch from the previous step to ensure that you did not miss any links. It is a good idea to include a status field for each artifact, to increase the accuracy of the reflected project state. For example it is possible that an artifact is created, but still under development. In the example we flagged such artifacts as _not realized_.

After we created the entire set of traceability matrices, we are ready to go and have established **bidirectional traceability **for our project. In order to follow a trace in any direction you have to combine the matrices belonging to that trace just like you would arrange domino stones (see example).

### (Optional) Create additional metrics that help to answer important questions immediately.

In addition to the possibility to maintain and evaluate _direct links, _it is possible to use the RTM to create accumulated view for entire traces. To do so, you simply combine the information from multiple matrices into a single one in order to make important information more accessible. In the attached example you find a combined view, showing the relation from _Customer Requirements_ to _Test Case_, which immediately reveals that only 47% of the _Customer Requirements _are covered by a test.

Please feel free to download the example and use it as a template for your own project. If you want to learn more about the benefits of a requirements traceability matrix check our following blog post.
