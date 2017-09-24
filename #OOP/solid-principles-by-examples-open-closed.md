# SOLID Principles by Examples: Open/Closed

_Captured: 2017-09-22 at 13:51 from [dzone.com](https://dzone.com/articles/solid-principles-by-examples-openclosed)_

This post continues the analysis of the [SOLID principles](https://ilclubdellesei.wordpress.com/2017/07/03/solid-principles-by-examples-introduction/) started some blog posts ago. This is the turn of the Open Closed Principle (OCP).

## The Definition

_"An object/entity should be open for extension but closed for modification."_

What we are basically talking about is designing our modules, classes, and functions in a way so that when a new functionality is needed, we should not modify our existing code, but rather write new code that will be used by the existing code.

## The Example

In this example, we're designing a class that represents the human resources department of a company and one of its main activities: hire people.

This class violates the OCP because if HR wants to hire a secretary, we have to add another Hire method and another IList where T is Secretary in addition to creating the new Secretary class. So our initial purpose to write new code that will be used by existing code hasn't been met.

## Refactoring

The HumanResorceDepartement class now respects the OCP because the new code (the Secretary class) can be used by old code (the Hire method). We did this by abstracting the concept of a manager/developer/secretary stating that they are all employees that sign a contract when they are hired. So, we created an interface called **IEmployee** that exposes the SignContract method.

The OCP is tightly coupled with the [Single Responsibility Principle](https://dzone.com/articles/solid-principles-by-examples-single-responsability). If we design a class with SRP in mind, it is very likely that we also respect OCP or that little work is required to meet both, and vice versa.

## TL;DR

The OCP makes our code more reusable and less coupled. This way we can write new code that with little impact in our existing codebase. SRP and OCP are closely related parents and their application makes our code more clean and maintainable. What's your experience with SOLID principles?
