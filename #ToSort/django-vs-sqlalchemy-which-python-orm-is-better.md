# Django vs. SQLAlchemy: Which Python ORM Is Better?

_Captured: 2017-06-13 at 23:10 from [dzone.com](https://dzone.com/articles/django-vs-sqlalchemy-which-python-orm-is-better?edition=303098&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-13)_

Learn how to [move from MongoDB to Couchbase Server](https://servedby.flashtalking.com/click/8/76151;2454368;369307;211;0/?ft_width=1&ft_height=1&url=14283402) for consistent high performance in distributed environments at any scale.

Before going into the difference between Python's ORM frameworks (Django and SQLAlchemy), let's make sure we fully understand the use of ORM frameworks in general.

ORM stands for Object Relational Mapping. Looking at each of these words will explain their use in the real world:

  * **Object**: This part represents the objects and programming language where the framework is used; for example, Python.
  * **Relational**: This part represents the RDBMS database you're using (Relational Database Manager System). There are numerous popular relational databases out there, but you're probably usin MSSQL, MySQL, Oracle Database, PostgreSQL, MariaDB, PerconaDB, ir TokuDB. What's common between most relational databases is their relational structures (tables, columns, keys, constraints, etc.).
  * **Mapping**: This final part represents the bridge and connection between the two previous parts.

The ORM is here to connect between the programming language to the database in order to simplify the process of creating an application that relies on data

## Active Record vs. Data Mapper

Django ORM uses the active record implementation. You'll see this implementation in most ORMs. Basically, what it means is that each row in the database is directly mapped to an object in the code and vice versa. ORM frameworks such as Django won't require predefining the schema to use the properties in the code. You just use them, as the framework can understand the structure by looking at the database schema. Also, you can just save the record to the database, as it's mapped to a specific row in the table.

SQLAlchemy uses the data mapper implementation. When using this kind of implementation, there is a separation between the database structure and the object structure (they are not 1:1 as in the active record implementation). In most cases, you'll have to use another persistence layer to keep interacting with the database (for example, to save the object). So you can't just call the `save()` method as you can when using the active record implementation (which is a con) but on the other hand, your code doesn't have to know the entire relational structure in the database to function, as there is no direct relationship between the code and the database.

So which of them wins this battle? Neither. It depends on what you're trying to accomplish. Itbeliefelieve that if your application is a mostly a CRUD (Create, Read, Update, Delete) application with no hard and complex rules to apply to the relationships between the different data entities, you should use the active record implementation (Django). It will allow you to easily and quickly set up an MVP for your product without any hassle. If you have a lot of "business rules" and restrictions in your applications, you might be better with the data mapper model, as it won't tie you up and force you to think strictly as active record does.

## Working With Complex Queries

In some cases, Django and SQLAlchemy can be used together. The main use case I got to see numerous times in the real world is when Django is used for all regular CRUD operations, while SQLAlchemy is used for the more complex queries, usually read-only queries.

For some more information and an example on this aspect, look into [BetterWorks engineering blog](https://engineering.betterworks.com/2015/09/03/sqlalchemy-and-django/) (we have no affiliation with them what so ever, we just liked their blog post :)).

## Primary Key Automatic Generation

Another difference between the two frameworks is that Django can create primary keys automatically for your tables. SQLAlchemy won't do that for you. You'll have to manually create them for each table yourself. It's both a pro and a con; who do you think knows best which primary key will be most suited for your table? It's up to you to decide, according to your team's knowledge and experience.

## Autocommit

Django has autocommit on by default, while SQLAlchemy doesn't. It will impact the way you use the framework (transactions, rollbacks, etc.).

## Supported Databases

Both Django and SQLAlchemy can be used with MySQL, PostgreSQL, Oracle, and SQLite. If you're using MSSQL, you should go for SQLAlchemy, as it's fully supported by it and you'll find more information and documentation about it.

## Learning Curve

It's a common opinion over the web that Django will be a lot easier to learn. Well, it's probably obvious, as it's usually used for less complex use cases. So you should think how much you're willing to invest in learning the framework to receive more flexibility with SQLAlchemy (in case you really need it).

## Community Size

Without a doubt, SQLAlchemy has the largest community among Python ORM frameworks. If community is important to you (and I think it should be), SQL Alchemy should be your choice. It doesn't mean though that you won't find any help for other frameworks such as Django. You'll get bug fixes, answers for questions in StackOverflow, and any other help you'll need, but your chances are just higher with SQLAlchemy.

## Performance

It would be irresponsible of me to just write "X is faster than Y" here. It would be very hard to get to that conclusion with ORMs, as they have such a variety of features and capabilities, and they are different in each framework. From my experience, the way you use the framework's features will have a large impact on the overall performance of your application's database layer. So my suggestion here is not to choose a framework by its performance, but to learn how to use the framework properly to get the most out of it.

## Summary

As in any comparison, I think it's better to leave the decision-making to you, the readers. Each use case is different, and a different technology can be better suited for each situation. Look into the differences specified above and let us know which decision you made.

Want to deliver a whole new level of customer experience? Learn how to make [your move from MongoDB to Couchbase Server](https://servedby.flashtalking.com/click/8/76151;2454369;369307;211;0/?ft_width=1&ft_height=1&url=14283403)[.](https://servedby.flashtalking.com/click/8/76151;2454369;369307;211;0/?ft_width=1&ft_height=1&url=14283403)

### Like This Article? Read More From DZone
