# Naming Conventions From Uncle Bob's Clean Code Philosophy

_Captured: 2018-03-21 at 15:21 from [dzone.com](https://dzone.com/articles/naming-conventions-from-uncle-bobs-clean-code-phil?edition=367211&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-03-21)_

This article is the result of reading the book "Clean Code" by Robert C Martin. All the recommendations made here are suggested by [Robert C Marin](https://en.wikipedia.org/wiki/Robert_C._Martin). This article covers the abstract of naming conventions suggested by Clean Code.

## 1\. Introduction

The clean code philosophy is seems be to emerged from the fundamentals of Software Craftsmanship. According to many software experts who have signed the [Manifesto for Software Craftsmanship](http://manifesto.softwarecraftsmanship.org/), writing well-crafted and self-explanatory software is almost as important as writing working software.

Following are the snippets from the book, show why naming is hard and disputable and the mindset to address this problem:

> "The hardest thing about choosing good names is that it requires good descriptive skills and a shared cultural background. This is a teaching issue rather than a technical, business or management issue."

> "Focus on whether the code reads like paragraphs and sentences, or at least tables and data structure."

## 2\. Naming Conventions

### 2.1. Use Intention-Revealing Names

Basically, don't name a variable, class, or method which needs some explanation in comments.

For example:

Can be named as:

### 2.2. Avoid Disinformation and Encodings

Don't refer to a group of accounts as "accountList," whereas it is actually not a List. Instead, name it "accountGroup," "accounts," or "bunchOfAccounts."

Avoid unnecessary encodings of datatypes along with the variable name.

It may not be necessary where it is very well known to the entire world that in an employee context, the name is going to have a sequence of characters. The same goes for Salary, which is decimal/float.

### 2.3. Make Meaningful Distinctions

If there are two different things in the same scope, you might be tempted to change one name in an arbitrary way.

What is stored in cust, which is different from customer?

How are these classes different?

How do you differentiate between these methods in the same class?

So, the suggestion here is to make meaningful distinctions.

### 2.4. Use Pronounceable Names

Ensure that names are pronounceable. Nobody wants a tongue twister.

This

vs

### 2.5. Use Searchable Names

Avoid single letter names and numeric constants, if they are not easy to locate across the body of the text.

vs

Use single letter names only used as local variables in short methods. One important suggestion is that "the length of a name should be correspond to the size of its scope."

### 2.6. Don't Be Cute/Don't Use Offensive Words

vs

vs

vs

vs

### 2.7. Pick One Word per Concept

Use the same concept across the codebase.

#### FetchValue() vs GetValue() vs RetrieveValue()

If you are using fetchValue() to return a value of something, use the same concept; instead of using fetchValue() in all the code, using getValue(), retrieveValue() will confuse the reader.

#### dataFetcher() vs dataGetter() vs dataFetcher()

If all three methods do the same thing, don't mix and match across the code base. Instead, stick to one.

#### FeatureManager vs FeatureController

Stick to either Manager or Controller. Again, consistency across the codebase for the same thing.

### 2.8. Don't Pun

This is exactly opposite of previous rule. Avoid using the same word for two different purposes. Using the same term for two different ideas is essentially pun.

For example, say you have two classes having the same add() method. In one class, it performs addition of two values, in another, it inserts an element into a list. So, choose wisely; in the second class use insert() or append() instead of add().

### 2.9. Solution Domain Names vs Problem Domain Names

The clean code philosophy suggests using solution domain names such as the name of algorithms or the name of design patterns whenever needed, and use a problem domain name as the second choice.

For example, accountVisitor means a lot to a programmer who is familiar with the Visitor design pattern. A "JobQueue" definitely make more sense to a programmer.

### 2.10. Add Meaningful Context as a Last Resort

While there are a few names which are meaningful themselves, most are not. Instead, you have to place names in context for your reader by enclosing them in well-named classes, functions, or namespaces. If not possible, prefixing the names may be necessary as a _last resort._

For example, the member variable named "state" inside the address class shows what it contains. But the same "state" may be misleading if used to store "Name of The State" without context. So, in this scenario, name it something like "addressState" or "StateName."

The "state" may make more sense in a context where you are coding about addresses when named "addrState."

### 3\. Summary

Robert C. Martin says, "One difference between a smart programmer and a professional programmer is that the professional understands that clarity is king. Professionals use their powers for good and write code that others can understand." I hope this article will help you to be more professional and write clean code, for further reading refer to "[Clean Code: A Handbook of Agile Software Craftsmanship](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882/ref=sr_1_1?ie=UTF8&qid=1520625319&sr=8-1&keywords=clean+coding)."

### 4\. References

### Appendix

#### Manifesto for Agile Craftsmanship

As aspiring Software Craftsmen, we are raising the bar of professional software development by practicing it and helping others learn the craft. Through this work we have come to value:

Not only working software,

but also well-crafted software

Not only responding to change,

but also steadily adding value

Not only individuals and interactions,

but also a community of professionals

Not only customer collaboration,

but also productive partnerships

That is, in pursuit of the items on the left we have found the items on the right to be indispensable.
