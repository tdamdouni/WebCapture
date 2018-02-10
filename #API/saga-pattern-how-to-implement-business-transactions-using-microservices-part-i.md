# Saga Pattern | How to Implement Business Transactions Using Microservices - Part I

_Captured: 2018-02-07 at 19:33 from [dzone.com](https://dzone.com/articles/saga-pattern-how-to-implement-business-transaction?edition=358124&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-02-07)_

[Learn how to track microservices](https://dzone.com/go?i=274457&u=https%3A%2F%2Fwww.appdynamics.com%2Fapp-iq-platform%2Fmicroservices-iq%2F%3Futm_source%3Ddzone%26utm_medium%3Dsponsorship%26utm_campaign%3Dmicroservics%252520sponsorship%26utm_content%3Dmicroservics%252520sponsorship%26utm_term%3Ddzone%252520microservics%252520sponsorship%26utm_budget%3Ddigital) deployed in elastic infrastructure such as containers or cloud where nodes scale up and down very rapidly.

One of the most powerful types of transactions is called a Two-Phase Commit, which is in summary when the commit of a first transaction depends on the completion of a second. It is useful especially when you have to update multiple entities at the same time, like confirming an order and updating the stock at once.

However, when you are working with microservices, for example, things get more complicated. Each service is a system apart with its own database, and you no longer can leverage the simplicity of local two-phase-commits to maintain the consistency of your whole system.

When you lose this ability, RDBMS becomes quite a bad choice for storage, as you could accomplish the same "single entity atomic transaction" but dozens of times faster by just using a NoSQL database like Couchbase. That is why the majority of companies working with microservices are also using NoSQL.

To exemplify this problem, consider the following high-level microservices architecture of an e-commerce system:

![](https://blog.couchbase.com/wp-content/uploads/2018/01/e-commerce-architecture-1024x693.png)

In the example above, one can't just place an order, charge the customer, update the stock, and send it to delivery all in a single ACID transaction. To execute this entire flow consistently, you would be required to create a distributed transaction.

We all know how difficult it is to implement anything distributed, and transactions, unfortunately, are no exception. Dealing with transient states, eventual consistency between services, isolations, and rollbacks are scenarios that should be considered during the design phase.

Fortunately, we have already come up with some good patterns for it, as we have been implementing distributed transactions for over twenty years now. The one that I would like to talk about today is called the Saga pattern.

## **The Saga Pattern**

One of the most well-known patterns for distributed transactions is called Saga. The first paper about it [ was published back in 1987, ](https://www.cs.cornell.edu/andru/cs711/2002fa/reading/sagas.pdf)and it has been a popular solution since then.

A Saga is a sequence of local transactions where each transaction updates data within a single service. The first transaction is initiated by an external request corresponding to the system operation, and then each subsequent step is triggered by the completion of the previous one.

Using our previous e-commerce example, in a very high-level design, a Saga implementation would look like the following:

![](https://blog.couchbase.com/wp-content/uploads/2018/01/Screen-Shot-2017-12-30-at-1.39.21-PM-1024x627.png)

There are a couple of different ways to implement a saga transaction, but the two most popular are:

  1. **Events/Choreography:** When there is no central coordination, each service produces and listens to the other service's events and decides if an action should be taken or not.
  2. **Command/Orchestration**: When a coordinator service is responsible for centralizing the saga's decision making and sequencing business logic.

Let's go a little bit deeper into each implementation to understand how they work.

### **Events/Choreography**

In the Events/Choreography approach, the first service executes a transaction and then publishes an event. This event is listened to by one or more services, which execute local transactions and publish (or don't publish) new events.

The distributed transaction ends when the last service executes its local transaction and does not publish any events, or the event published is not heard by any of the saga's participants.

Let's see how it would look in our e-commerce example:

![](https://blog.couchbase.com/wp-content/uploads/2018/01/Screen-Shot-2018-01-09-at-6.13.39-PM.png)

  1. _Order Service_ saves a new order, set the state as _pending_ and publish an event called _**ORDER_CREATED_EVENT**_.
  2. The _Payment Service_ listens to _**ORDER_CREATED_EVENT**_, charge the client and publish the event **_BILLED_ORDER_EVENT_**.
  3. The _Stock Service_ listens to _**BILLED_ORDER_EVENT**_, update the stock, prepare the products bought in the order and publish _**ORDER_PREPARED_EVENT**_.
  4. _Delivery Service_ listens to _**ORDER_PREPARED_EVENT**_ and then pick up and deliver the product. At the end, it publishes an _**ORDER_DELIVERED_EVENT**_
  5. Finally, _Order Service_ listens to _**ORDER_DELIVERED_EVENT**_ and set the state of the order as concluded.

In the case above, if the state of the order needs to be tracked, Order Service could simply listen to all events and update its state.

#### **Rollbacks in distributed transactions**

Rolling back a distributed transaction does not come for free. Normally you have to implement another operation/transaction to compensate for what has been done before.

Suppose that Stock Service has failed during a transaction. Let's see what the rollback would look like:

![](https://blog.couchbase.com/wp-content/uploads/2018/01/Screen-Shot-2018-01-09-at-6.36.17-PM-1024x702.png)

  1. _Stock Service_ produces **_PRODUCT_OUT_OF_STOCK_EVENT_**;
  2. Both _Order Service_ and _Payment Servic_e listen to the previous message: 
    1. P_ayment Service_ refund the client.
    2. _Order Service_ set the order state as failed.

Note that it is crucial to define a common shared ID for each transaction, so whenever you throw an event, all listeners can know right away which transaction it refers to.

#### **Benefits and Drawbacks of Saga's Event/Choreography Design**

Events/Choreography is a natural way to implement Saga's pattern; it is simple, easy to understand, does not require much effort to build, and all participants are loosely coupled as they don't have direct knowledge of each other. If your transaction involves 2 to 4 steps, it might be a very good fit.

However, this approach can rapidly become confusing if you keep adding extra steps in your transaction, as it is difficult to track which services listen to which events. Moreover, it also might add a cyclic dependency between services, as they have to subscribe to one another's events.

Finally, testing would be tricky to implement using this design. In order to simulate the transaction behavior, you should have all services running.

In the next post, I will explain how to address most of the problems with Saga's Events/Choreography approach using another Saga implementation called **Command/Orchestration**.

In the meantime, if you have any questions, feel free to ask me at [@deniswsrosa](https://twitter.com/deniswsrosa).

[Maximize your development velocity](https://dzone.com/go?i=274458&u=https%3A%2F%2Fwww.appdynamics.com%2Fdocker%2F%3Futm_source%3Ddzone%26utm_medium%3Dsponsorship%26utm_campaign%3Dmicroservices%25252520sponsorship%25252520docker%25252520%26utm_content%3Dmicroservices%25252520sponsorship%25252520docker%25252520%26utm_term%3Ddzone%25252520microservices%25252520sponsorship%25252520docker%25252520%26utm_budget%3Ddigital) and get a deep-dive into Docker metrics for immediate insight into your container.
