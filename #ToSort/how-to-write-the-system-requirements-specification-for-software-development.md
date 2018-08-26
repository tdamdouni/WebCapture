# How to Write the System Requirements Specification for Software Development

_Captured: 2018-07-06 at 19:29 from [dzone.com](https://dzone.com/articles/how-to-write-the-system-requirements-specification?edition=385206&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202018-07-06)_

Maintain Application Performance with real-time monitoring and instrumentation for any application. [Learn More!](https://dzone.com/go?i=281422&u=https%3A%2F%2Fwww.nastel.com%2Fapplication-performance-monitoring%2F%3Futm_source%3DDZone%26utm_medium%3DPrePostRoll%26utm_campaign%3DDZone2018%2520for%2520all%2520pre%2Fpost-roll%2520text%2520ads%3A)

As an experienced software development company, we know that writing good system requirements specification is pivotal to the success of any software project. Working with dozens of different requests from various industries we have accumulated knowledge and created a vision of how ideal SRS documentation should look like. In this article, we share our best practices for creating outstanding SRS documentation which will be both very comprehensive for the developers and protect your project from some of the challenges you and your business may face without having well-outlined system functionality and requirements to the final software.

## What Is the System Requirements Specification?

Every software has specific goals and serves particular purposes. Each goal and purpose translates a process or several processes that the software aims to solve or to automate. To deliver the right software product, we should define well the software from the beginning. System requirement specification or SRS frameworks software development, it documents every operation and dictates how software should behave, it can be as detailed as what a button should do and should be as complete and correct as possible. The purpose of a specification document is to describe the behavior as well as the different functionalities of an application or software in a specific environment.

In this blog post, we are going to discuss System requirement specification or SRS and its needs. We will give some advice to help you while writing software requirements specifications, and we will enumerate some common bad practices and writing good requirements examples that you can you use as a guide. Then we will take a software system requirements specification example to better understand the concept. First of all, let's address the reason why it is essential to write a system requirements specification during software development process as documentation is part of software development process.

## Why Should SRS Be Included in the Software Development Process?

First of all, customers or product owners work on writing system requirements to define the objectives of the software as well as the scope of intervention of the team that develops the application or the software. A thorough description of the software helps the development team to implement and build the software. We then use the software system requirements specification to validate and check the software product to ensure that it has the required features. Development should start from a specification. If somehow the delivered software doesn't meet the requirements, the specification serves as a reference and development team works to meet all the described requirements.

Writing technical specifications for software is then an important starting point for any software development project. It involves not only the development team but also the owners and/or users of the software. It helps the software development team during the design and implementation of the product. Making sure that the specifications are complete and clear which means that they do not lead to ambiguity prevents from spending lots of time correcting, redefining and reimplementing the software. Moreover, early detection of problems in specification leads to effective time management since it is a lot easier to update specification prior to any development than to update the specification then the corresponding functionalities.

Generally, writing technical specifications for software comes after a first discussion between the development team and the product owner. Specifications serve as a reference for cost and time estimation. Since writing system requirements document aims to describe faithfully the software to develop, it makes estimation process a lot easier and much more accurate.

Additionally, development of an application is an evolving process; it will not always involve the same persons. Writing software requirements specifications aims to document the behavior of the software making it easier to hand over the development from a team to another. This is why it is essential to know how to write a requirement specification.

A good specification makes the software product easier to update. Any change in the software requires to update the project requirement specification inviting every party involved in the process to rethink the changes to be made.

Moreover, SRS can be used like Functional Specification Document (FSD) or Product Requirement Document (PRD). SRS includes requirements that help write Functional Specification Document and can even include FSD, SRS describes all functionalities and explains how the functionality will inside a given system as a part of a larger system or as an independent system. FSD is the software-only part of an SRS document. Indeed, an SRS may contain hardware requirements, system interaction requirements as well.

It is crucial to writing a good software system requirements specification. Later in this blog post, we are going to analyze system requirement specification document examples to understand the difference between well written and poorly written specification. In the following section, we are going to see how to write a system requirement specification document.

## How to Write System Requirements Specification

In this section, we are going to learn how to write SRS document. A good system requirement specification document should answer the following questions:

  * What should the application or software do? Answering this question helps identify the main functionalities and the primary purpose of the software.
  * How should the software behave? It helps to understand how the software interacts with the environment where it is deployed; it also defines the hardware specification and defines the IHM: how the software interacts with the end users. The software to be described may be a whole system, but sometimes it is part of a more extensive system. It is then essential to define how this part interacts with a bigger system, how the two systems communicate with each other. CRM system requirements specification is a good example where it is essential to understand how the software should behave.
  * What are the requirements in term of performance? It will, for instance, give information about the acceptable response time, how fast it should respond and how fast it should handle problems when they occur.
  * Are there requirements or constraints that should be taken into account or respected? It aims to determine the constraints to be taken into account during design, development, and deployment of the system.

Now that we have defined what an SRS should contain and what questions it should answer as well as how to write SRS document, let's see how to write software requirements the different steps needed to write an SRS.

The outlines may differ from a project requirement specification to another. However, we can consider the following outline:

  * An introduction: The first step for how to write a requirement specification is to agree on what should the software do, whether we are writing CRM system requirement specification or another system requirement specification. At this point, it is important that the development team and the product owners define and write this part together. The product owner doesn't necessarily have the skills to write a good SRS, but the development team doesn't know what the end users need. This is why It is important for the two parties to work closely together at this stage. In this section, it is important to put the software to build in its context. Here, we address the reason why the software needs to be built, who is going to use the software, what it should or should not do (sometimes it is helpful and necessary to mention what we should not expect from the software). Sometimes, some terms are specific to the business, and their mention in the document is important to understand the specification and to build the software. It is essential to define these technical terms so that the content can be understood. At the end of the introduction part, we can include a brief overview of the document to give the readers an idea of what they can expect from the document. It is also important to mention in the SRS all the documents that can be read to have a further understanding of the system, and all references should be documented as well.
  * A general description: in the description section, it is important to explain the different functionalities of the application. In this part, the hardware interfaces and user interfaces are defined. In what device the end users expect to access the application for instance or what are the functionalities of the software, how can users expect to see them in the application, what is displayed on the menus, what are the other parts like Reports, exports, etc.?
  * Specific requirements: In this section, the requirements are detailed so that it is made easier to design the product and validate the software according to requirements. Here, it is important to describe all inputs the software handle and all the outputs to better define interaction with other systems and facilitate integration. The functionalities enumerated in the previous section will be detailed here. The performance criteria need to be defined here as well. It may be tempting to leave for later some parts of the documentation that may change during the development process or at a later stage. However, it is important to thoroughly document the SRS and update the content if needed and when needed.
  * References: it may sound obvious now that we mention it but it is important to include information about the content so that it is easier to find the information when needed.

## SRS Bad Practices

An SRS is a technical document, and there are few practices to avoid to write a good System requirements specification. We will see these bad practices through software system requirements specification example.

  * Incomplete dictionary: An SRS may include jargons that only people familiar with the business can understand. A requirement specification aims to give everyone involved in the development of the software a better understanding of what the software does etc. it is important that everyone understands all the terms that are used in the document. Before using them, it is important to define them, even better have them at one place so that readers can find them quickly when needed
  * Mixing concepts: it may be tempting to throw all information we have at the same place, but that leads to poor documentation.
  * Include development instruction: it is important to separate software requirements from technical implementation. The product owners know better their needs and development team knows better how to develop the software that meets these needs.
  * Passive action: it is important to know what to expect from the software, but it is as important to understand who is going to interact with the software to have the expected result. For instance: reports are generated by clicking on a given button. It is important to know that we expect report generation from the software, but it is also important to know who is going to click on the button to generate the report.
  * Ambiguous and incomplete documentation: sometimes some lines in the requirements may lead to several interpretations. However, it is important that requirements are clear and don't lead to misunderstanding or interpretation for both documentation writer and the persons to whom the SRS is intended. Also, for each functionality or situation described in the SRS, it is important that the SRS does not present aspects that are not determined yet.

## The Difference Between the Bad and Good Requirements Specification Example Documents

Now that we have defined what's an SRS and seen how to write software requirements, and what is generally included in one requirement specification among with the most common bad practices, let's consider a simple yet useful system requirement specification document example.

Let's consider a system requirement example for a system managing ATM cash withdrawal. First, let's consider an example of a poorly written specification and then see how to write good requirements.

### **Poorly Written Specification**

When a customer selects from the menu that he wants to withdraw money, he will be asked to choose how much money does he want to withdraw. The system is checking his account to see if his balance allows that transaction. If his balance allows the transaction, the transaction is validated. The system releases the customer's card and delivers the cash with a receipt of the transaction. All the operations must be fast.

This system specification example seems clear. However, when we do some analysis, it presents some examples of bad practices. This specification lacks clarity, and it does not tell:

  * **For the choice of the amount:**
    * how the customer chooses or indicates the amount, he wants to withdraw.
    * Is there a list of choices
    * can he manually input money he wants to withdraw
    * how much is the limit he can withdraw during a single transaction
    * is there any rule for an acceptable amount a customer can withdraw
  * **For the validation of the transaction:** what are the rules for the validation?
  * **For the money delivery:** does the customer receive a receipt all the time?

### Writing a Good Specification Example

The previous specification can be improved as following after correcting the bad practices we have identified earlier. Earlier, we have seen how to write a software specification, in this section, we are going to apply the good practices we have mentioned.

When a customer selects the menu: "Withdraw money," he has the possibility to choose between six different amount on the screen: $10, $20, $30, $50, $100, $200, $300 or choose from the screen to input manually the amount he wants to withdraw. The amount must be multiple of one of the tickets issued by the ATM while respecting the maximum number of tickets for a transaction. Once the customer has chosen the amount, he can select the validate button to continue with the transaction or select the cancel button to cancel the transaction and get back his card. If the customer validates the amount he selected, the system validates if his balance allows him to withdraw the amount he requested and if the customer has not yet reached the maximum daily amount. The system also validated if the ATM can issue the amount: the system checks if the ATM has enough money to satisfy the customer's need and if the amount is a multiple of delivered tickets. If the validation is OK, the system asks the customer if he wants a receipt for his transaction. If the customer wants a receipt for the transaction, the system prepares the receipt, releases the customer's card, delivers the money and the receipt. If the validation is OK, but the customer does not want a receipt, the system releases the customer's card, delivers the money. If the transaction is not validated, the ATM releases the customer's card and display the reason why his transaction has been denied. Every transaction should take at most three seconds.

## In Conclusion

A system requirements specification is a must when it comes to developing software. Some good practices lead to good documentation. Since SRS is useful for both software customers and software development team, it is essential to develop a complete and clear specification document, in this blog post we have seen how to write a software specification. SRS helps the customers to define their need with accuracy, while it helps development team understand what the customers need in terms of development. Investing time in writing the SRS document will lead to successful development of the software the customers need.

Collect, analyze, and visualize performance data from mobile to mainframe with AutoPilot APM. [Learn More!](https://dzone.com/go?i=281423&u=https%3A%2F%2Fwww.nastel.com%2Fapplication-performance-monitoring%2F%3Futm_source%3DDZone%26utm_medium%3DPrePostRoll%26utm_campaign%3DDZone2018%252520for%252520all%252520pre%2Fpost-roll%252520text%252520ads%3A)
