# Data Model Design Best Practices (Part 1)

_Captured: 2017-08-04 at 19:45 from [dzone.com](https://dzone.com/articles/data-model-design-and-best-practices-part-1?edition=313393&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-04)_

Business applications, data integration, master data management, data warehousing, big data, data lakes, and machine learning -- these all have (or should have) a common and essential ingredient: **a data model**.

The data model is the backbone of almost all high-value, mission-critical business solutions -- from e-commerce and point-of-sale to financial, product, and customer management and all the way through to business intelligence and IoT. Without a proper data model, where is the business data? Probably lost!

Data models and data modeling methodologies have been around since the beginning of time (well, since the beginning of computing, anyway). Data needs structure in order to make sense and provide a way for computers to deal with its bits and bytes. Sure, we deal with unstructured and semi-structured data, too, but for me, this simply means that we've evolved to more sophisticated paradigms than our computing predecessors had to deal with. The data model therefore remains and provides the basis upon which we build highly advanced business applications.

Looking back at the history of data modeling may enlighten us, so I did some research to refresh myself.

## A Brief History Lesson on the Data Model

![](https://www.talend.com/wp-content/uploads/320px-Hierarchical_Model_svg.png)

In the Computing Dark Ages, we used flat record layouts/arrays: all data saved to tape or large disk drives for subsequent retrieval. However, in 1958, [J. W. Young and H. K. Kent](https://en.wikipedia.org/wiki/Data_model#cite_ref-10) described [modeling](https://en.wikipedia.org/wiki/Data_model) information systems as "a precise and abstract way of specifying the informational and time characteristics of a data processing problem." Soon after, in 1959, [CODASYL](http://purl.umn.edu/40644) (Conference/Committee on Data Systems Languages) was formed by the [Charles Babbage Institute](https://en.wikipedia.org/wiki/Charles_Babbage_Institute) at the University of Minnesota, which led to standard programming languages like COBOL and the [Integrated Data Store](https://en.wikipedia.org/wiki/Integrated_Data_Store) (IDS), an early database technology designed in the 1960's at GE/Honeywell by [Charles Bachman](https://en.wikipedia.org/wiki/Charles_Bachman).

![](https://www.talend.com/wp-content/uploads/320px-Network_Model_svg-1.png)

IDS proved difficult to use, so it evolved to become the [Integrated Database Management System](https://en.wikipedia.org/wiki/IDMS) (IDMS) developed at [B.F. Goodrich](https://en.wikipedia.org/wiki/Goodrich_Corporation) (a U.S. aerospace company at the time, and yes. the tire company we know today) and marketed by Cullinane Database Systems (now owned by Computer Associates). These two data modeling methodologies -- called the hierarchal data model and the networkdata model respectively -- were both very common across mainframe computing for the next 50 years. You may still find them in use today!

In the late 1960s, while working at IBM, [E.F. Codd](https://en.wikipedia.org/wiki/Edgar_F._Codd) in collaboration with [C.J. Date](https://en.wikipedia.org/wiki/Christopher_J._Date) (author of _[An Introduction to Database Systems_](https://www.amazon.com/Introduction-Database-Systems-8th/dp/0321197844)), mapped Codd's innovative data modeling theories resulting in the _[Relational Model of Data for Large Shared Data Banks](http://www.idc-online.com/technical_references/pdfs/information_technology/A_Relational_Model_of_Data_for_Large_Shared_Data_Banks.pdf) _publication in 1970. Codd's campaign to ensure vendors implemented the methodology properly published his famous _[Twelve Rules of the Relational Model_](http://computing.derby.ac.uk/c/codds-twelve-rules/) in 1985. Actually, thirteen rules numbered zero to twelve; Codd was clearly a computer geek of his day.

![](https://www.talend.com/wp-content/uploads/280px-Relational_Model_svg-1.png)

The relational model also introduced the concept of normalization with the definition of the _[Five Normal Forms](http://www.bkent.net/Doc/simple5.htm)_. Many of us talk about 3NF (Third Normal Form), but do you know how to define it?

The next significant data modeling methodology arrived in 1996, proposed by [Ralph Kimball](https://en.wikipedia.org/wiki/Ralph_Kimball) (retired) in his groundbreaking book co-authored by Margy Ross, _[The Data Warehouse Toolkit: The Complete Guide to Dimensional Modeling](http://www.kimballgroup.com/data-warehouse-business-intelligence-resources/books/data-warehouse-dw-toolkit/)._

![](https://www.talend.com/wp-content/uploads/dim1-1.jpg)

Kimball's widely adopted [star schema](https://en.wikipedia.org/wiki/Star_schema) data model applied concepts introduced in the data warehouse paradigm first proposed in the 1970s by [W.H. (Bill) Inmon](https://en.wikipedia.org/wiki/Bill_Inmon) (named in 2007 by Computerworld as one of the ten most influential people of the first 40 years in computing). Inmon's [Building the Data Warehouse](http://fit.hcmute.edu.vn/Resources/Docs/SubDomain/fit/ThayTuan/DataWH/Bulding%20the%20Data%20Warehouse%204%20Edition.pdf), published in 1991, has become the defacto standard for all data warehouse computing. While there has been some history of disagreement between Inmon and Kimball over the proper approach to data warehouse implementation, Margy Ross of the Kimball Group presents a fair and balanced explanation for your worthy consideration in her article [Differences of Opinion](http://www.kimballgroup.com/2004/03/differences-of-opinion/).

![](https://www.talend.com/wp-content/uploads/the-data-vault-2.jpg)

Recently, a new data modeling methodology has emerged as a strong contender: [the data vault](https://en.wikipedia.org/wiki/Data_vault_modeling)! Its author and inventor, [Dan Linsdedt](http://danlinstedt.com/), first conceived the data vault in 1990 and released a publication to the public domain in 2001. The data vault model resolves many competing Inmon and Kimball arguments, incorporating historical lineage of data, and offering a highly adaptable, auditable, and expandable paradigm. I invite you to read my article, [What is "The Data Vault" and why do we need it?](https://www.talend.com/blog/2015/03/27/what-is-the-data-vault-and-why-do-we-need-it/) Linstedt's data vault proved invaluable on several significant DOD, NSA, and Corporate projects. In 2013, Linsdedt released [Data Vault 2.0](http://learndatavault.com/) addressing Big Data, NoSQL, unstructured, semi-structured data integration coupled with SDLC best practices on how to use it. Perfect timing, I'd say. So here we are…

## **A Data Model Summary**

A quick summary of the different data modeling methodologies:

  * **Flat model**: A single, two-dimensional array of data elements.
  * **Hierarchical model**: Records containing fields and sets defining a parent/child hierarchy.
  * **Network model**: Similar to the hierarchical model allowing one-to-many relationships using a junction 'link' table mapping.
  * **Relational model**: Collection of predicates over a finite set of predicate variables defined with constraints on the possible values and combination of values.
  * **Star schema model**: Normalized fact and dimension tables removing low cardinality attributes for data aggregations.
  * **Data vault model**: Records long-term historical data from multiple data sources using hub, satellite, and link tables.

## Database Development Lifecycle: DDLC

Today's dialogue seems to focus entirely on complexity and sheer volume of data. Important, sure, but again I'd like to remind you that the data model should be an important part of the discussion. As requirements evolve, the schema (a data model) must follow along -- or even lead the way. Regardless, it needs to be managed. Therefore, I present to you the Database Development Life Cycle!

For every environment where data is involved, developers need to accommodate and adapt code to its inevitable structural mutation. Similar to the Software Development Life Cycle (SDLC), a database should embrace appropriate data model design and best practices. Of the many data models that I have designed, clear precepts have emerged, which include:

  * **Adaptability**: Creating schemas that withstand enhancement or correction.
  * **Expandability**: Creating schemas that grow beyond expectations.
  * **Fundamentality**: Creating schemas that deliver on features and functionality.
  * **Portability**: Creating schemas that can be hosted on disparate systems.
  * **Exploitation**: Creating schemas that maximize a host technology.
  * **Efficient Storage**: Creating optimized schema disk footprint.
  * **High Performance**: Creating optimized schemas that excel.

These design precepts incorporate the essence of any chosen modeling methodology -- some in contradiction with others. In my experience, regardless of these dichotomies, a data model has just three stages of life:

  * **A fresh install**: Based upon the current version of the schema.
  * **Apply an upgrade**: Drop/create/alter database objects upgrading one version to the next.
  * **Data migration**: Where a disruptive upgrade occurs (like splitting tables or platform).

Designing the data model can be a labor of love entailing both the tedious attention to detail tempered with the creative abstraction of ambiguity. Personally drawn to challenging schemas, I look for cracks and crevices to correct, which often present themselves in various ways. For example:

  * **Composite primary keys**: Avoid them, rarely effective or appropriate; there are some exceptions depending upon the data model
  * **Bad primary keys**: Usually datetime and/or strings (except a GUID or Hash) are inappropriate
  * **Bad indexing**: Either too few or too many.
  * **Column datatypes**: When you only need an Integer don't use a Long (or Big Integer), especially on a primary key.
  * **Storage allocation**: Inconsiderate of data size and growth potential
  * **Circular references**: Where table A has a relationship with table B, table B has a relationship with table C, and table C has a relationship with table A; this is simply bad design.

Let's consider then a database design best practice: The design and release process of a data model. I believe that when crafting a data model one should follow a prescribed process similar to this:

![](https://www.talend.com/wp-content/uploads/DDLC_DBdesignflow-3.png)

Self-explanatory to most perhaps, yet let me emphasize the importance of adopting this process. While schema changes are inevitable, getting a solid data model early in any software development project is essential. Undoubtedly minimizing the impact to application code is desirable for delivering successful software projects. Schema changes can be an expensive proposition so understanding the database life cycle and its role becomes very important. Versioning your database model is critical. Use graphical diagrams to illustrate the designs. Create a data dictionary or glossary and track lineage for historical changes. It is a higher discipline, but it works!

## Data Modeling Methodologies

Understanding the history of the data model and the best process under which to design them is only the starting point. As a database architect for both [transactional (OLTP)](https://en.wikipedia.org/wiki/Online_transaction_processing) and [analytical (OLAP)](https://en.wikipedia.org/wiki/Online_analytical_processing) models, I have discovered that the first three steps illustrated above represent about 80% of the work. Let's consider that next.

Sometimes, data models are easy, usually due to simplicity and/or small stature. Data models can also be very hard, usually due to complexity, diversity, and/or sheer size and shape of the data and the many places throughout the enterprise where it is used. I believe we should understand as early as possible the full extent of what and where data is, how it is affected by, or affects the applications and systems using it, and why it is there in the first place. Getting your head around who needs what and how to deliver it is the challenge. Mapping it out to ensure a solid Data Model is the goal. Choosing the right data modeling methodology is paramount.

## Conclusion

In Part 2 of this series, I will illustrate and examine the basics and value of the logical and physical data model. I will also propose an expansion on the way we differentiate our data: holistically first, then separating out the conceptual details, before we even attempt a logical or physical design. These help us better understand the data, model the data, and validate the model of our database design.

Until then, ponder on the information presented here, and feel free to leave any comments, questions, and/or debate the principles presented. Cheers!
