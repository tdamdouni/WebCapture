# Lobotomize Your OO Thinking: “Elegant Objects, Vol. 1” Book Review

_Captured: 2017-07-27 at 20:32 from [dzone.com](https://dzone.com/articles/lobotomy-to-your-object-oriented-thinking-elegant?edition=311391&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-27)_

Learn how our [document data model](https://dzone.com/go?i=225226&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-3%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3D1%26jmp%3Ddzone-ad) can map directly to how you program your app, and native database features like secondary indexes, geospatial and text search give you full access to your data. Brought to you in partnership with [MongoDB](https://dzone.com/go?i=225226&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-3%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3D1%26jmp%3Ddzone-ad).

> Step one in the transformation of a successful procedural developer into a successful object developer is a lobotomy. (by David West) 

This is the first sentence in the "[Elegant Objects, volume 1"](https://www.amazon.com/Elegant-Objects-1-Yegor-Bugayenko/dp/1519166915) book by Yegor Bugayenko, and after reading it from cover to cover, I could not agree more. This book will not leave you neutral, you will either strongly agree or disagree with claims stated there, but it is definitely worth your time. It will challenge what you know about programming, it will challenge what you think a proper object-oriented design is, and it will challenge many old, well-established so-called "good practices" you have seen during your career. Fasten your seatbelts, move your coffee mug away from your keyboard, and keep reading.

![](http://tomaszdziurko.com/wp-content/uploads/2017/07/elegant-objects-cover-206x300.png)

## Content

"Elegant Objects, vol. 1", in over 200 pages, gives you 23 practical tips to write more object-oriented, thus more maintainable code. The author uses a very interesting allegory by treating every object as a human being and splitting these suggestions into four anthropomorphized chapters: birth, school, employment, and retirement.

The _Birth_ chapter is rather short and covers object creation, starting from naming strategies through suggestions how to keep constructors clean and easy to test. _Education_ and _Employment_ are the core of the book and contain paragraphs describing how to build encapsulated, immutable, and easy to test objects, how to use interfaces with stub implementations to simplify testing without mocking hell. Then we could read some rants about "encapsulation by getters/setters," sections about the clear distinction between data structures known from procedural languages, and well-defined classes and objects from OO programming. The last paragraph _Retirement_ is about avoiding nulls, using only checked (yes, yes, no typo here) exceptions, and recovering from errors.

Each suggestion is clearly described with code snippets showing bad, then proper approaches to solve the discussed topic. There are also links to discussions on author's blog, so you could read what other have to say about each suggestion. Most paragraphs are short, so the reader could split reading sessions into smaller ones without the need to re-read several pages. Paragraphs are also rather autonomous, so you could read them in any order. Even if there is a reference to something covered elsewhere, it will be a direct reference to the paragraph number where the reader should look for the mentioned information.

## My Notes

During the reading, I put many sticky notes with sentences worth remembering below the most important or intriguing topics.

  * Avoid names ending with "-er", as it suggests that such an object is only a collection of procedures that manipulate data and not a fully independent entity that is capable of acting on its own.
  * Each class should have only one primary constructor with initialization logic there. Non-primary (secondary) constructors should only prepare data (param conversions, etc.) and call the primary one.
  * Each class should have a maximum of four properties. They author makes an analogy to coordinates in the universe (x, y, z, and time)
  * Instantiation should be strictly separated from execution. A _new_ operator is allowed only inside secondary constructors.
  * Every public method must be a part of some interface. Why? See below.
  * Avoid mocking hell by using no mocks. Provide default (fake) implementations of all interfaces that could be later used in your tests. This way, other developers won't have to set up everything in each test. They could simply use fake implementations that need to be written once.
  * Avoid mutable states.

Mutable objects are an abuse of the entire object-oriented paradigm.

  * Avoid temporary coupling between lines: With immutable objects, you do not have two separate phases of object instantiation and object initialization (first "new", then multiple setters), so we cannot accidentally put any logic before the object is fully ready to use. The immutable object is either a non-existing or fully initialized entity ready to work for you, so reordering lines won't have any effect on application logic, the same immutable object will be used.
  * Show your respect to others by writing code that assumes they are junior programmers. Don't show. Write simple, easy-to-follow code.
  * Favor small objects with well-defined scopes and responsibilities -> max four public/protected methods. If this number goes above five, think carefully, as this class probably has more than one responsibility.
  * **Static methods are like a cancer to your objects.**
  * You can't trust objects returning null. Every time, at some point, you will have to check for nullability.

As you can see, some of them are only slightly stricter rules than we apply during our daily jobs, but some are quite radical. If you want to better understand them or see if readers agree or disagree with the presented approach, you could use a link to the discussion on Yegor's blog (e.g. [Don't mock, use fakes](http://www.yegor256.com/2014/09/23/built-in-fake-objects.html)). I am not sure that applying all of them is possible, but in my opinion, the more you try, the better your code will be.

## Summary

Without any doubt, I am placing "Elegant Objects, vol. 1" next to my other favorite programming books like "Clean Coder," "Clean Code," "Software Craftsman," and "The Pragmatic Programmer: From Journeyman to Master" (some of them have [reviews here on my blog](http://tomaszdziurko.com/tag/books/)). It shows a very different point of view to object-oriented programming and challenges much that we all take for granted. It presents something I would call a radical Object-Oriented paradigm that will broaden your horizons and make you think twice before following any standard approach. There is a second part named "[Elegant Objects, volume 2"](https://www.amazon.com/Elegant-Objects-2-Yegor-Bugayenko/dp/1534908307) that I am planning to read as well.

Discover when your data grows or your application performance demands increase, [MongoDB Atlas](https://dzone.com/go?i=225227&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-3%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3D2%26jmp%3Ddzone-ad) allows you to scale out your deployment with an automated sharding process that ensures zero application downtime. Brought to you in partnership with [MongoDB](https://dzone.com/go?i=225227&u=https%3A%2F%2Fwww.mongodb.com%2Fcloud%2Fatlas%2Flp%2Ftry-3%3Futm_medium%3DDisplay%26utm_source%3Ddzone%26utm_campaign%3DWW_Reg_ATLAS_Dzone%26utm_content%3Dpre-post-roll%26utm_term%3D2%26jmp%3Ddzone-ad).
