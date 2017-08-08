# How to Choose the Right Product Validation Technique in Scrum

_Captured: 2017-08-04 at 23:47 from [www.romanpichler.com](http://www.romanpichler.com/blog/beyond-product-demo-validation-techniques-in-scrum/?utm_content=buffer79245&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

### Feedback and Data in Scrum

Collecting feedback and data is a vital aspect of Scrum. It enables you to learn if the right product with the right features is created. Scrum employs a [three-step process](http://www.romanpichler.com/blog/the-scrum-cycle/) to achieve this: A product increment is created, which is then exposed to the users, the customers, and the other stakeholders. This generates feedback and data, which triggers product backlog changes, as the following picture shows.

![DataCollectionAndTheScrumCycle](http://www.romanpichler.com/wp-content/uploads/2014/04/DataCollectionAndTheScrumCycle.jpg)

To leverage this process, the techniques used to gather the data and validate the product are crucial. If you use the wrong method, you are likely to collect wrong or insufficient data and draw the wrong conclusions. While there is a range of techniques available, Scrum recognises only one: the product demo, which is performed in the sprint review meeting.

But this does not mean that you should or cannot employ another technique! The opposite is true: The sprint demo may or may nor be right for product. Additionally, using a single data collection method over an extended period of time is usually a mistake. Every technique has its strengths and limitations, and none is always appropriate. You should hence choose the one that is most helpful for your product and combine complementing techniques.

### A Selection of Helpful Techniques

To help you select the right method, I have complied five techniques happily used in Scrum in the table below. I discuss each technique in the following sections.

T**echnique**
**Description**
**Strength**
**Weakness**

[Product demo](http://www.romanpichler.com/blog/beyond-product-demo-validation-techniques-in-scrum/?utm_content=buffer79245&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)
Demo the latest increment. Listen to the feedback, and ask open questions.
Test limited functionality: Helps people imagine what using the product would be like. Feedback is available immediately.
Feedback is based on what users hear and see; danger of influencing users.

[Usability test](http://www.romanpichler.com/blog/beyond-product-demo-validation-techniques-in-scrum/?utm_content=buffer79245&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)
Observe how users interact with the prototype or product in a controlled environment such as a lab.
Understand if users employ the product as anticipated. Possibly collect data using analytics software. Data is available immediately.
Artificial environment: users do not use the product "in the wild"; observer effect.

[Release](http://www.romanpichler.com/blog/beyond-product-demo-validation-techniques-in-scrum/?utm_content=buffer79245&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)
Release the software to a group of target users and collect data using analytics.
Find out how the product is used in its target environment. Reach a larger test group. Run A/B tests.
Does not explain _why_ users employ the product in a certain way. Can take time to collect enough data.

[Observation](http://www.romanpichler.com/blog/beyond-product-demo-validation-techniques-in-scrum/?utm_content=buffer79245&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)
Observe users employ the product preferably in its target environment.
Understand how users interact with the product.
Can be time consuming; danger of observer effect and bias.

[Spike ](http://www.romanpichler.com/blog/beyond-product-demo-validation-techniques-in-scrum/?utm_content=buffer79245&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)
Create an executable prototype to address an architecture risk.
Understand if an architecture or technology choice is feasible.
Can lead to an over-engineered solution.

### Product Demo

As its name suggests, the product demo presents the latest product increment to the appropriate users, customers, and internal stakeholders. The presenter explains how the users would employ the product to get a job done. Product demos are particularly valuable in the early sprints, as they allow you to get immediate feedback on limited functionality and very small increments: By wrapping the increment in a story, people can imagine what it would be like to use the product.

This strength is also a major weakness: The feedback is based on what people see and hear, not on their actual experience of using the product. What's more, the presenter can influence the users inappropriately by talking up the product or asking closed questions, and powerful individuals like a senior manager can influence the views of the group. My post "[The Product Demo as an Agile Market Research Technique](http://www.romanpichler.com/blog/the-product-demo-as-an-agile-market-research-method/)" shares more tips and tricks on employing product demoes effectively.

### Usability Test

A usability test allows you to understand how users interact with your product. Usability testing takes typically place in a controlled environment such as a meeting room or lab. Target users are asked to perform a task using the latest product increment, which may be a paper prototype or executable software. You then observe and record how people employ the product, and you can end the test with asking the participants about their experiences and impressions. It is often possible to conduct the test in the sprint review meeting.

While a usability test quickly generate real user data, the artificial environment and the observation can cause the users to act differently compared to working with the product in "the wild", that is, in the environment in which the product will be used, for instance, at home, at work, in the car, on the train. This is where the next technique comes in.

### Release

Releasing software means giving a group of target users access to an early version of the product and asking them to use it in its target environment. The usage data is then recorded by an analytics tool, for instance, Google Analytics. The product is now employed in its target environment, and a larger test group can be employed, which reduces the risk of collecting data that is not representative for the market segment targeted. With the right analytics software, you can also collect data such as who interacts with which product feature when and how often, and which variant of a feature people prefer (A/B test).

On the downside, the technique cannot explain _why_ people use a certain feature, or why they don't. Additionally, there is a delay: It takes people time to download, install, and start using the latest increment before enough data is available to draw the right conclusions. In a Scrum context, this means that you either have to postpone the next sprint or continue with a different feature to mitigate the risk of moving in the wrong direction.

If you primarily use releases then your sprint review meeting changes: It is now used to synch the internal stakeholders and review the project progress rather than to validate the product.

### Observation

Observation means watching users carefully as they employ the product in its target environment. This helps you understand how people interact with the product and use its features. It also allows you to debrief with the user and to learn about the user's experience whilst interacting with the product.

The main drawback of observations that they can be time consuming particularly if you want to observe more than a few users. Users may also act differently with somebody watching them (observer effect), and your own biases may interfere with you ability to see clearly.

### Spike

Spikes are prototypes to test an architectural or technology-related assumption, for instance, that Enterprise JavaBeans will be able to deliver the desired performance. They are usually cheap to create, generate the relevant knowledge quickly, and allow you to see if you can meet critical [nonfunctional requirements](http://www.romanpichler.com/blog/agile-nonfunctional-requirements/).

Spikes become problematic if you employ them too much, if you worry more about how to build the product than why and what to build. If this happens the result is in an over-engineered product and a solution-centric mindset rather than a user-centric one. I once met a team that had been building spikes for nearly two years without having to show any shippable code. Telling them to stop it and think about the users was quite shocking for them.

### Choosing the Right Technique

All the techniques discussed have their strengths and weaknesses. While you should always choose the technique that helps you meet your sprint goal and validate the increment effectively, I find it a helpful rule of thumb to use product demos, usability tests and spikes in the early sprints, and releases and observation in the later sprints, as the following picture illustrates.

![ChoosingTheRightValidationTechnique](http://www.romanpichler.com/wp-content/uploads/2014/04/ChoosingTheRightValidationTechnique.jpg)

The diagram above tries to balance the strengths and weaknesses of the different techniques, and it corresponds to a risk-driven approach where the key risks and critical assumptions are tackled in the early sprints. (For more info assumptions, risks and learning in Scrum see my post "[Get Your Focus Right: Learning and Execution in Scrum](http://www.romanpichler.com/blog/learning-and-execution-in-scrum/)".)

Whichever techniques you choose, don't make the mistake to rely on a single technique for an extended period of time. Every technique has its benefits and drawbacks, and no single technique is perfect. Combine qualitative and quantitative techniques, for instance, releases and observation, to leverage their respective strength and mitigate their weaknesses. Don't be shy to experiment with different techniques to find out what works best for your product, and use the sprint retrospective to review their effectiveness.

## Learn More

You can learn more about selecting the right product validation techniques with the following:

**Source:** <http://www.romanpichler.com/blog/beyond-product-demo-validation-techniques-in-scrum/>
