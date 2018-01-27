# An Introduction to Node.js

_Captured: 2017-12-21 at 14:02 from [dzone.com](https://dzone.com/articles/an-introduction-to-nodejs?edition=347101&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=web%20dev%202017-12-21)_

Tips, tricks and tools for creating your own [data-driven app](https://dzone.com/go?i=247321&u=http%3A%2F%2Fplayground.qlik.com%2Flearn%2Fnoobs%2Fintro%3Futm_source%3Ddzone_web_dev_zone%26utm_medium%3Dbumper_text_1%26utm_campaign%3Ddzone), brought to you in partnership with Qlik.

## Introduction

Node.js is an application framework and sometimes is referred to as a runtime, through which applications are built using the JavaScript programming language. Node.js is well known for its speed, due to the fact that it is non-blocking. Further, being non-blocking means one request does not wait for the other request to finish (i.e it is asynchronous). The asynchronicity is what makes Node.js the framework that it is today in terms of throughput, unlike Java application servers which are mostly blocking each request that is bound to a thread and as soon as there are no more threads available the server almost always stops receiving requests.

In this article, we will discover some aspects of Node.js. We will do so by discussing some topics such as: uses cases of Node.js, how Node.js achieves concurrency and its main design pattern.

## Why Node.js?

Node.js is a near perfect choice for any small to medium size project. However, if TypeScript is used instead of just plain JavaScript, this will open a whole new world of possibilities. Further, TypeScript is "JavaScript that scales," as Javascript is a language that was not quite intended for backend development right from its inception, and even to date, it is still not quite suitable for backend development. One of the primary reasons for JavaScript not being a suitable backend development language is due to the lack of type checking. It gets quite complicated in highly modular architectures. Being modular is the advocated approach for building systems in the Node.js community because even Node.js itself is modular. Therefore, it is a natural fit for applications built on top of it to sort of following a similar path. Typescript, on the other hand, being a "superset of JavaScript" adds a lot of "syntactic sugar" when it comes to working with Node.js on the server side. An example of syntactic sugar is type checking, which we saw that JavaScript lacked.

## How Node.js Achieves Concurrency

Node.js achieves its "concurrency" by relying upon its runtime construct called the event loop. The event loop is at the core of every Node.js application because it is through it that Node.js can achieve its high input and output (IO) volumes. The way it works at a high level is that it heavily relies on the asynchronous programming concept to enable the application to be non-blocking. That is, request/statement 2 does not wait for request 1 to finish and request/statement 3 does not wait for request/statement 2 to finish before it can proceed. And the same applies to every other task that needs to be performed by the runtime.

## Some Node.js Design Patterns

At the heart of all Node.js applications lies the observer design pattern. It is very important for any Node.js developer to understand how this design pattern works, especially if one is coming from a different environment which abstracts this pattern away completely. With that being said, there are a couple of ways to program in Node.js without worrying about this pattern at all. This is achieved through the construct of the new JavaScript specification (ES6) which Node.js 7.6 is based on. This construct is known as async-await. Further, the developer will have to ensure they are using at least Node.js 7.6 because it as only with the release of this version that async-await was no longer considered experimental.

## Putting it All Together

Just like any other technology, Node.js has its pros and cons. The main advantage is that Node.js is very fast in terms of throughput. The main disadvantage is that it becomes very complex in terms of maintainability when building large-scale enterprise applications, provided that JavaScript is used and not TypeScript. TypeScript should be the norm for implementing enterprise ready Node applications.

Explore [data-driven apps](https://dzone.com/go?i=247322&u=http%3A%2F%2Fplayground.qlik.com%2F%3Futm_source%3Ddzone_web_dev_zone%26utm_medium%3Dbumper_text_2%26utm_campaign%3Ddzone) with less coding and query writing, brought to you in partnership with Qlik.
