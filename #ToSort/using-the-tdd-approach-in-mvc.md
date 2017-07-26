# Using the TDD Approach in MVC

_Captured: 2017-04-14 at 20:41 from [dzone.com](https://dzone.com/articles/using-tdd-approach-in-mvc?edition=290908&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-14)_

[Learn how to design and configure a binary repository](https://dzone.com/go?i=205127&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F158041), optimize it for various workflows, and fit it smoothly into your software development lifecycle with the [Using Repository Managers Refcard](https://dzone.com/go?i=205127&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F158041) from DZone.

One of the main benefits of using MVC is its support for testability that enables the Test Driven Development approach in a simple way. An application must be created in a loosely coupled way to make it testable. Such an application allows easy testing of different application parts. The framework support is extremely important to create the testable applications. In fact, testing was a major design goal of MVC.

TDD is an approach to Test First Development in which a test is written before writing the complete production code for refactoring and fulfilling the test. It also called as the Red-Green-Refactor method of development.

## **The Workflow of TDD**

![](https://lh6.googleusercontent.com/tOzn4Zq_cfVKxW_jr_aSrvcPrXIqQf-8OpljtsUjsZbqQTk0gr3xFOt8fUe7Qv2VYEBWzoWG8iT6molVZLoArXF4qGXCX-NOgqh62gUlQONTpfmALY7FPAQBuqh9ce-sygglFGG_BUiRc5WlXA)

1\. Identify the requirement.  
2\. Write a test for automation.  
3\. Execute tests and ensure that the newer tests fail (red color).  
4\. Write the code.  
5\. Ensure that all tests have run and passed.  
6\. Perform refactoring.  
7\. Repeat the process.

## **Best Practices for Writing the Test Cases**

In order to write the unit test cases, the best method is to use the F.I.R.S.T principles described as below:

  1. Fast: The unit test cases should be written by taken their performance in consideration. It is mandatory you need to execute a large number of test cases in the release.

  2. Isolated: Every test case should be isolated to specific behavior. That is, if a failure occurs, the programmer should be aware of what went wrong without any need to look at the flow of execution. It is recommended to break a test case in smaller parts for this reason.

  3. Repeatable: Each test case must be stable such that we get consistent results for multiple runs.

  4. Self-Validating: The result of a test case should either be pass or fail. It should not have any ambiguity scenarios along with assertions.

  5. Timely: It is an important aspect for TDD since the test cases need to be created prior to the implementation.

## **Creating an MVC Application Using TDD**

To create an MVC application by using unit test, follow the below steps:

  1. Select "New Project" under the File menu in Visual Studio.

  2. Go to "Installed Templates" and click on "Visual Basic" or "C#" as per the requirement and click on "Web."

  3. Select the template of the Asp.net MVC Application.

  4. Write the same as MvcContacts.

  5. Click on OK.

  6. As soon as the dialog box for Unit Test Project appears, ensure that "Yes" is selected and then select OK. The Visual Studio will create two solutions containing two projects, the first one as MvcContacts and the other named as MvcContacts.Tests.

  7. Go the Test menu and select "Run" and then click on "All Tests of Solution." Results will be displayed in the Window of Test results. All tests are passed.

  8. Now go to the project of MvcContacts.Tests and analyze the account controller classes for the test and the model. These classes describe the ways of creating the mock interfaces.

## **Creating a Database Model**

Follow the below steps for creating a database model:

  1. Go to the Solution Explorer, right-click on "App_Data folder," and select "Add." Then click on "Existing Item." A dialog box for adding an existing item will appear.

  2. Go to the folder containing Contact.mdf file and select the file. Click on "Add."

  3. Go to the Solution Explorer and right-click on "MvcContacts Project." Select "Add" and then "New Item." A dialog box for adding a new item will appear.

  4. Now go to the Installed Templates and click on the Visual Basic or C# and select "Data." Click on the Entity Data Model for ADO.Net template.

  5. Go to the Name box and enter the ContactModel. Select "Add." A wizard for the Entity Data Model will appear.

  6. Click on the option to generate via database and select "Next."

  7. Click on Contact.mdf as the connection to be used by the application for connecting to the database.

  8. Ensure that the checkbox to save the settings of the connection string in web.config file is selected. Leave the default name of the connection string.

  9. Select "Next." A wizard will appear for specifying the database objects needed to be added to the model.

  10. Click on the node of Tables for selecting the table of contacts. Leave the namespace for default model.

  11. Click on "Finish."

## **Adding a Repository**

One of the best practices in MVC is to not include the code of any framework of data-access in the controller. Instead, the repository pattern needs to be used. The repository lies between the data store and the application. It separated business logic from the interactions with database and concentrates the access to data in a single area, making its creation and maintenance easier. The objects are returned from domain model by the repository. The simple models return the object from LINQ to SQL, EDM, and other models of data qualifying as the domain objects. While in the case of complex applications, there might be a requirement of a mapping layer, it is not always inefficient. We can make use of LINQ providers for creating queries for the data store at the back-end. Another point to note is that the repository does not need any knowledge of LINQ to SQL or EDM or any other type of data model to work with.

## **Adding Tests**

Using MVC with TDD, every test should have a particular requirement in its action method. It is not required by the test to verify the database or any other components. Another aim is that the names of the test must be descriptive because the short names will be difficult to understand with a large number of tests. For any further assistance, write to [asp.net development services](http://www.aegisinfoways.com/technologies/aspnet-web-development.html) provider. You can even share your reviews for this post in comments.

Discover [how to configure a Repository Manager](https://dzone.com/go?i=205128&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F158041) to store, manage, and share binaries, optimize it for various workflows, and fit it smoothly into your DevOps pipeline with the [Using Repository Managers Refcard](https://dzone.com/go?i=205128&u=https%3A%2F%2Fdzone.com%2Fasset%2Fdownload%2F158041) from DZone.

Opinions expressed by DZone contributors are their own.
