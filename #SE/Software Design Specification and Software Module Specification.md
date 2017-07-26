# Software Design Specification and Software Module Specification

_Captured: 2015-10-24 at 18:29 from [sdesmedt.wordpress.com](https://sdesmedt.wordpress.com/2006/08/22/software-design-specification-and-software-module-specification/)_

**Introduction:**

It's probably completely out of fashion to write software design specifications in an agile world, but we are still doing it. And I believe it is a good thing. Of course, there will be exceptions and the culture of the software shop should also be taken into account, but as you don't go on holiday without planning your route, I don't think you should start coding without thinking on how you are going to implement your application.

**On the Internet:**

SDS:

SMS:

  * [A Technique for Software Module Specification with Examples. (It also contains an interesting treatment on errorhandling)](http://people.cs.uchicago.edu/~robby/contract-reading-list/parnas.05.72.pdf)

Sample specifications:

**What we ended up doing**

At my job we need to have a Software Design Specification (further referred to as SDS) and a Software Module Specification (further referred to as SMS). When looking for information about the two, you will mostly find info on SDS's and very little on SMS's.

I think the SDS is mostly a high level view of the system design describing the interaction between the different modules of a system, where an SMS provides detailed information about the implementation of a specific module: what classes does it have, what is their responsibility, what public methods do the classes have, etc…

As the SMS is more about the code itself, we create them from the code. Commenting our code and using comment extractors we create the SMS document which is then (mostly) up-to-date with our code base. The comments are those you should always write:

  * modules: what is their logical meaning? What is their responsibility?
  * classes: what is their responsibility?
  * public methods: what do they do?
  * parameters: what information do they contain, what is their purpose? What is their valid range of values? What is their direction of information flow: do they pass information into the method, or do they convey information out of the method?

We use Autoduck to comment our code and made a custom translator so our comments are extracted to an xml document. We then apply an xslt stylesheet to transform it in a SMS document as required by our quality department.

The SDS is created manually.

It has the following sections:

  1. As all our documents it has a "Version, Revision and Approval" section, briefly describing what changed (see further: SDS maintenance) and a "Table Of Contents" section
  2. An "Introduction" section, briefly describing what to expect from this document and how the partitioning of the application is done. To partition our application we use a hierarchy as follows: 
    1. Application: this is of course, well, the aplication
    2. Component: this is a functional coherent part of the application. Examples are: User Login, Logging, etc…
    3. Module: these are the building blocks of the components and map to things like static libraries, dll's and executables

The text in this section is more or less a standard text block which is repeated for each SDS.

  3. A "Bibliography" section with info on sources of information used to write the SDS, like books or articles in magazines, on the Internet, etc… It provides enough information to find the book or article back.
  4. A "Glossary" section which explains some of the terms and abbreviations used in the rest of the SDS.
  5. A "Constraints" section. In the above references you will mostly find a section "Assumptions and Dependencies" and a section "Constraints". I've wrapped these in a single section "Constraints" because a dependency can be considered as a constraint to your application. If your component is for example dependent of SQL Server, then that will also constraint your application as to what operating system it can run on, what technology to use for accessing the database, etc…
  6. The "Overview" section describes what the component described in this SDS is about and how it relates to other components in our application. For this, it states: 
    * the scope of the component: what it will be able to do, but also what it will not be able to do.
    * the components it uses, but not those it is being used by
    * a UML component diagram of the component and the components it depends on. This diagram shows the packaging of the components and the interfaces on the boundaries between the components.
  7. Next is the main part of the SDS: the "System Description" section. This is really the heart of the SDS and describes how the component will provide it's functionality. Because we develop an application which evolves continuously, their are a number of concerns which always come back in our application. These could be considered as a kind of crosscutting concerns of our application. So we have divided our template SDS in these crosscutting concerns, of course accommodating for the need of new concerns. Example concerns are User Interfaces, Security, Logging, …  
Because we have these repeating concerns, we also added some guidance on what to think about when designing for a concern. For example for the user interface; error messages, configuration screens, etc…
  8. The "Module Description" section then describes how the component is divided in modules and how these last map to libraries and executables. It's basically a table with the names of the modules, a version and the implementation type (static library, dll or executable). It also provides following UML diagrams: 
    * UML Component diagrams: showing the partitioning in libs and execs
    * UML Static Diagrams: showing the partitioning in classes and their relationship. This is not a detailed diagram of every class in the component, but more an overview of the most important classes and their relationship.
    * UML Dynamic diagrams: showing the dynamic interaction between the classes in the component

Mind the plural forms of the word "diagram" in the above summary: there may be for example several dynamic diagrams each describing the implementation of a specific concern of the component. 

  9. The last to one section is the "Module Data" section which describes things as schema's of databases, layout of text files, xml files, etc…
  10. The last section is the "Testing" section. It provides guidance on things to test in the component. For example: when using a database, test the behavior when the database is not available, a connection is lost, etc…

The actual SDS template has of course a more detailed description of each section, but above you can find the general idea behind each. And because we develop a single application which is then maintained, a lot of the detailed info is specific to our organization.

I hope the above helps you to write your own SDS template.

And then there is of course the inevitable tweaking…
