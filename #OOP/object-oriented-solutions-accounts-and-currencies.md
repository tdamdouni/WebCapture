# Object-Oriented Solutions: Accounts and Currencies

_Captured: 2017-03-24 at 18:58 from [dzone.com](https://dzone.com/articles/object-oriented-solutions-accounts-and-currencies?edition=286910&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-24)_

What every Java engineer should know about microservices: [Reactive Microservices Architecture](https://dzone.com/go?i=153025&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone). Brought to you in partnership with [Lightbend](https://dzone.com/go?i=153025&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone).

This article is about a simplified version of real code running at a financial institution and how maintenance problems with this code can be avoided by using Object-Oriented Design. The purpose of the code is to represent retail money _Accounts_ and enable transferring money, define recurring transfers and to support the usual functionality you find at any bank.

First, there is an _Account_ interface and a _Money_ class:

All _Accounts_ have a given _Currency_ in which the money is held in the _Account_. All operations on an _Account_ must use the same _Currency_ with which the _Account_ is defined, so it is not possible to transfer _Money_ to or from the _Account_ if the _Currencies_ do not match. Currency is an enumeration:

For all these components, there are _Services_ to execute a given business case, like _Cash Transfer_ for example.
    
    
                if (account.getCurrency() != money.getCurrency()) {

The _Service_ above contains the logic to transfer _Money_ between _Accounts_ and the first step is to check whether the _Currencies_ match.

This kind of design is surprisingly common in the Java Enterprise field, and a lot of developers would perhaps not see any problem with this approach at all. Unfortunately, this design leads **directly** to code quality problems, unreadable and unmaintainable code. Let's see what the next feature request caused with this code:

## International Accounts

After the code above was already in production the bank decided that customers should have the possibility of choosing a new type of _Account_ which would accept any _Currency_ and would convert between mismatching _Currencies_ "on the fly". Let's see how this feature was implemented to the above-shown parts of the _Account_:

The new _Account_ type had no default currency, so it's implementation simply returned null:

Of course, the condition in the _CashTransferService_ also needs to be modified, because it now has to handle _null_ values for _Currency_:

The developer responsible for this modification then even took the time to make the code more readable by extracting the condition into a method in the _Service_:
    
    
          return account.getCurrency() == null || account.getCurrency() == money.getCurrency();

Although this code is generally not regarded as "bad," **the death spiral of code quality has already begun** and it will not stop until structural changes are made. Specifically, the following pitfalls can be already clearly seen:

  * The modification required the knowledge of _other_ code. We knew, that the condition in _CashTransferService_ had to be modified, but in fact it is very easy to miss other places where a _null_ value as _Currency_ might cause problems. In short, the change is not localized.
  * _Null_ value has special semantics. The developer decided that _null_ as _AccountCurrency_ means that all _Currencies_ are accepted. This is completely arbitrary and non-obvious, thus the API of _Account_ became more obfuscated. Note that _[Optional](https://docs.oracle.com/javase/8/docs/api/java/util/Optional.html)_ does **not** help with this at all. Neither does documentation.
  * Duplicated code. The same condition is in fact found in many places, since there are multiple _Services_ working with _Accounts_. Each of those now has to in effect duplicate the _Currency_ checking logic. Moving the "_hasMatchingCurrency_()" method to a utility is only a band-aid, but does not solve the problem.
  * Business functionality diffuses, becomes less clear. Since checks need to be done externally to the Account, it is inevitable that some logic will diffuse and probably will lead to multiple versions of the same check. It also contributes to changes not being local, and eroding responsibilities.

## Fixing the Code With OO, First Step

These kinds of problems almost always have the same cause: **misplaced responsibilities**. The original _Account_ interface, through publishing the base _Currency_ of the account, places the responsibility to check for _Currency_ conformity at the caller site. The callers (which are all related _Services_) need to know how the _Account_ works, and need to be able to check for preconditions. This indirectly leads to all the problems listed above.

To fix this, the responsibility of checking for this condition needs to be put into the _Account_ itself. For example this way:

This is a small, very important, and sometimes confusing step. The basic idea is, that we are not asking the object for data (like _getCurrency()_ does), instead we **trust** the _Account_ to **make a decision** itself.

With this interface, defining the _International Account_ is easy:

Please also note the following consequences:

  * There is no need to adjust any of the _Services_ (if they already use the new interface), introducing the _InternationalAccount_ is completely localized.
  * There is no need to introduce _null_, or any other special values or meaning.
  * There is still some duplicated code, since all _Services_ still need to know to call the _allowsTransactionCurrency()_ method, but it is less code than before.

### Daily Account

The next feature request was, that there should be an _Account_ type, which can be easily used daily, with low fees, quicker transactions, but all the transactions should be limited to some amount, let's say 200 EUR.

As before, the first solution looked like this:

It introduced an _Account_ limit value, which of course then needs to be checked in every _Service_ that transfers money from the _Account_ (of which there are many).

Again, this might seem like a perfectly reasonable solution for many developers, but unfortunately leads to exactly the same problems as before. There will be _Accounts_ with no inherent limits, then those need special values, and all this has to be checked by all _Services_ the same way. Introducing duplication, diffusing responsibility, and starting bit rot.

The same solution as above can be applied here this way:

Although this is a much better approach, let's look at the _CashTransferService_ again:
    
    
                if (!account.supportsWithdrawAmount(amount) || !account.allowsTransactionCurrency(currency)) {

All these features start to accumulate in the _Services_, probably with copy-paste code to check for the different conditions an _Account_ might have, depending on what transaction the _Service_ wants to initiate.

## Fixing the Code With OO, Second Step

So what is wrong with the code above? Why are these problems still popping up? The answer to that might seem familiar: **misplaced responsibilities**.

The problem is still that we don't trust the _Account_ object enough, that is why we have to know how to micromanage it. We ask it to make **some** decisions, but we don't trust it with the big picture. The big picture being: transferring money to an external account.

Instead of externalizing logic on how to transfer _Money_ out of an _Account_, this is something the _Account_ is actually perfectly capable of doing, if we just let it:

This approach does not only get rid of all the superfluous "checks" that were previously in the _Account_ class, but it gets rid of the _Services_ related to _Accounts_.

Not only that, but it is actually a truer representation of the business. It is easier to understand what an _Account_ can be used for, and it is easier to understand the relations between different business objects.

## Summary

This article demonstrates through a simplified example what it means to think more in an Object-Oriented way instead of the usual Data- and Service-oriented approach.

It also shows how to use Object-Oriented Design to avoid maintenance problems and make implementing new features easy by localizing changes, placing code that needs to be changed together in the same class, and thinking about trusting objects with responsibilities instead of micromanaging them.

Microservices for Java, explained. Revitalize your legacy systems (and your career) with [Reactive Microservices Architecture](https://dzone.com/go?i=153026&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone), a free O'Reilly book. Brought to you in partnership with [Lightbend](https://dzone.com/go?i=153026&u=https%3A%2F%2Finfo.lightbend.com%2FCOLL-20XX-Reactive-Microservices-Architecture-RES-LP.html%3Flst%3DDZ%3Futm_source%3Ddzone%26utm_medium%3Dpartner-resources%26utm_campaign%3DCOLL-20XX-Reactive-Microservices-Architecture%26utm_term%3Dnone%26utm_content%3Dnone).
