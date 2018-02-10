# Top REST API Best Practices

_Captured: 2018-02-05 at 12:09 from [dzone.com](https://dzone.com/articles/top-rest-api-best-practices?edition=358116&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-02-04)_

Many giants like Facebook, Google, GitHub, Netflix, Amazon, and Twitter have their own REST(ful) APIs that you can access to get or even write data.

But why all the need for REST?

Is it that good and why is it so prevalent?

Surely it's not the only way to convey messages?

What is the difference between REST and HTTP?

Well, it turns out **REST is pretty flexible and compatible with HTTP** (which is the main protocol the internet is based upon). Since it is an architectural style and not the standard, it **provides a lot of freedom to implement various design best practices**. Did I mention it's language agnostic?

In this blog post, my goal will be to explain REST as clearly as possible so you can clearly understand when and how to use it, as well as what it is in essence.

We'll go through some basics and definitions as well as show off some **REST API best practices**. This should give you all the knowledge you need to implement REST APIs in any language in which you prefer to code.

If you are not that familiar with HTTP, I recommend reading our [HTTP series](https://code-maze.com/http-series/), or at least [part 1 ](https://code-maze.com/http-series-part-1/)of it, so you can digest this material more easily.

## So What Is REST Essentially?

REST (Representational State Transfer) is an architectural style founded by [Roy Fielding](https://en.wikipedia.org/wiki/Roy_Fielding) in his Ph.D. dissertation "[Architectural Styles and the Design of Network-based Software Architectures](http://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm)" at UC Irvine. He developed it in parallel with HTTP 1.1 (no pressure).

We use REST primarily as a way **to communicate between computer systems on the World Wide Web**.

## Is REST Bound to HTTP?

By definition, it's not. Although you can use some other application protocol with REST, [HTTP](https://code-maze.com/http-series/) has remained the undisputed champion among application protocols when it comes to the implementation of REST.

## REST and HATEOAS support

HATEOAS or the **Hypermedia As The Engine Of Application State **is the important feature of every scalable and flexible REST API.

The [HATEOAS](https://en.wikipedia.org/wiki/HATEOAS) constraint proposes that the client and server communicate entirely utilizing the [hypermedia](https://en.wikipedia.org/wiki/Hypermedia).

There are several advantages to using hypermedia:

  * It enables API designers rather than to include everything they can in each response, to provide one thing properly and hypermedia links to related endpoints and thus decouple the design
  * It helps API evolve and mature more gracefully
  * It provides the user with the means to explore the API more deeply

So it is clear that the HATEOAS was **designed with durability in mind**.

Here is how GitHub does it:

Response:

As you can see, besides the crucial information requested by the client, you can find a bunch of related hypermedia links in the response which lead you to other parts of the API you can freely explore.

## What Does RESTful API Mean?

"RESTful" implies a few features:

  * **[Client-server architecture](https://code-maze.com/http-series-part-2):** The complete service is comprised of the "Client" which is the front-end and the "Server" which is the backend part of the whole system.
  * **Stateless:** The server should not save any states between different requests. The state of the session is exclusively left to the responsibility of the client. As per the definition of REST: **_All REST interactions are stateless. That is, each request contains all of the information necessary for a connector to understand the request, independent of any requests that may have preceded it. ([Roy's dissertation ch. 5.2.2](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm))_**
  * **[Cacheable](https://code-maze.com/http-series-part-2/#caching):** The client should be able to store responses in a cache for greater performance.

So, the RESTful API is a service that follows these rules (hopefully) and uses [HTTP methods](https://code-maze.com/the-http-reference/#requestmethods) to manipulate the set of resources.

But why do we need or use RESTful APIs?

Because they give us an easy, flexible, and scalable way to make distributed applications that communicate over the internet.

## Can We Have Too Much REST?

Yes, you guessed it. Yes, we can.

There is even a phrase for the people that follow REST fanatically, as defined by [Mike Schinkel.](http://mikeschinkel.com/about/)

> A **RESTifarian** is a zealous proponent of the REST _[software architectural style](http://www.ics.uci.edu/~fielding/pubs/dissertation/abstract.htm)_ as defined by [Roy T. Fielding](http://roy.gbiv.com/) in [Chapter 5](http://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm) of his [Ph.D. dissertation](http://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm) at [UCIrvine](http://www.ics.uci.edu/). You can find RESTifarians in the wild on the [REST-discuss mailing list](http://tech.groups.yahoo.com/group/rest-discuss/). But be careful, RESTifarians can be extremely meticulous when discussing the finer points of REST, as [I learned recently](http://tech.groups.yahoo.com/group/rest-discuss/message/6845) while participating on the list. 

Too much of anything can be bad.

We need a bit **pragmatism** to make good applications and services. A theory is important to know and understand, but the implementation of that theory is what differentiates bad vs good vs excellent applications. So be smart, have the end user in mind.

So let's look at some important points that make APIs "shine" and the lives of the users a whole lot easier.

## Abstract vs Concrete APIs

When developing software we often use abstraction and polymorphism to get most of our applications. We want to reuse as much of the code as possible.

So should we write our APIs that way too?

Well, that is not exactly the case with APIs. For REST APIs, **concrete is better than abstract**. Can you guess why?

Let me show you a few examples.

Let's look at two API versions. Is it better to have an API that has one `/entities` or an API that has `/owners`, `/blogs` and, `/blogposts`separately?

Which one seems more descriptive to you as a developer? Which API would you rather use?

I would always choose the second one.

## **URI Formatting (Nouns, not Verbs): Good URL vs Bad URL Examples**

Here is another REST API best practice. How should you format your endpoints?

If you use the software development approach you will end up with something like this:

/getAllBlogPosts

/updateBlogPost/12

/deleteBlogPost/12

/getAuthorById/3

/deleteAuthor/3

/updateAuthor/3

You get the point... There will be a ton of endpoints, each one doing something else. There is a better system for sorting out this mess.

Treat the resource like a noun, and the HTTP method as a verb. If you do it like that, you'll end up with something like this:

`GET /blogposts` \- gets all the blog posts.

`GET /blogposts/12` \- gets the blog post with the id 12.

`POST /blogposts` \- adds a new blog post and returns the details.

`DELETE /blogposts/12` \- removes the blog post with the id 12.

`GET /authors/3/blogposts` \- gets all the blog posts of the author with id 3.

This is a cleaner and more precise way to use the API. It is immediately clear to the end user, and there is a method to the madness.

You can make it even cleaner by using singulars instead of plurals for the resource names. That one is up to you.

## **Error Handling**

This is another important aspect of API building. There are a few good ways to handle errors.

Let's see how the top dogs do it.

**Twitter:**

  * Request: `GET https://api.twitter.com/1.1/account/settings.json`
  * Response: Status Code 400

Twitter gives you the Status Code and Error Code with the short description of the nature of the error that occurred. They leave it up to you to look the codes up on their [Response Codes](https://developer.twitter.com/en/docs/basics/response-codes) page.

**Facebook:**

  * Request: `GET https://graph.facebook.com/me/photos`
  * Response: Status Code 400

Facebook gives you a more descriptive error message.

**Twilio:**

  * Request: 
  * `GET https://api.twilio.com/2010-04-01/Accounts/1234/IncomingPhoneNumbers/1234`
  * Response: Status Code 404

Twilio gives you an XML response by default and the link to the documentation where you can find the error details.

As you can see, the approaches to error handling differ from implementation to implementation.

The important thing is **not to leave the user of the REST API "hanging," **i.e. not knowing what happened or aimlessly wandering through the wastes of StackOverflow searching for the explanation.

## **Status Codes**

When designing a REST API, you communicate with the API user by utilizing [HTTP Status Codes](https://code-maze.com/the-http-reference/#statuscodes). There are a lot of status codes, describing multiple possible responses.

But just how many should you use? **Should you have a strict status code for every situation?**

As with many things in life, the [KISS principle](https://en.wikipedia.org/wiki/KISS_principle) applies here too. There are over 70 status codes out there. Do you know them by heart? Will the potential API user know them all, or will it once again result in googling stuff?

Most developers are familiar with the most common status codes:

By starting with these three, you can cover most of the functionalities of your REST API.

Other commonly seen codes include:

  * `401 Unauthorized`

You can use these to help the user quickly figure out what the result was. You should probably include some kind of message if you feel the status code is not descriptive enough like we discussed in the error handling section. Once again, be pragmatic, help the user by using a** limited number of codes** and descriptive messages.

You can find the complete HTTP Status codes list, as well as other helpful HTTP stuff [here](https://code-maze.com/the-http-reference).

## **Security**

There is not much to be said about REST API security because **REST doesn't deal with security**. It relies upon standard HTTP mechanisms like [basic or digest authentication](https://code-maze.com/http-series-part-4/).

Every request should be made **over HTTPS**.

There are many tricks to improve the security of your REST API, but you must be cautious when implementing them, because of the stateless nature of REST. Remembering the state of the last request goes out of the window, and the **client is where the state should be stored and verified.**

**Timestamping and logging** requests can help a bit too.

There is much more to be said on this topic, but it is out of the scope of this post. We have a nice post on **[HTTP Security](https://code-maze.com/http-series-part-5/)** if you want to learn more about that.

## **REST API Versioning**

You've already written your REST API and it has been very successful and many people have used it and are happy with it. But you have that juicy new functionality that breaks other parts of the system. The breaking change.

Never fear, there is a solution for that!

Before you start making your API, you can version your API by prefixing the endpoints by the API version: _https://api.example.com/v1/authors/2/blogposts/13_

This way you can always increment your API version number (eg. v2, v3...) whenever there are breaking changes in your API. This also signals to the users that something drastic has changed and they should be careful when using the new version.

## **Importance of Documentation**

This one is a no-brainer. You could be the best API designer in the world, but **without documentation, your API is as good as dead.**

**Proper documentation is essential** for every software product and web service alike.

You can help the user by being consistent and using clear and descriptive syntax, sure. But there is no real replacement for good ol' documentation pages.

Here are some of the great examples:

There are many tools that can help you document your API, but don't forget to add the human touch, only one human can properly understand another. For now at least (looking at you AI).

## Conclusion

We went through many concepts of the REST API building and covered some of the top REST API best practices. These might seem a bit strange or overwhelming when served at once, but try making your own REST API. And try to implement some the REST API best practices you learned here.

Make the tiniest API possible and see how it looks. You'll be surprised how well it can turn out by just following these few practices.

We have an [ongoing series](https://code-maze.com/net-core-series/) in which we will demonstrate some of these practices. Also, if you are a C# developer, check out our article on [how to consume RESTful APIs in a few different ways](https://code-maze.com/different-ways-consume-restful-api-csharp/).

And with this said, **I REST my case** ... kmhmh... you know, like in court... oh, nevermind :)

Is there anything important I've missed? If I did, let me know in the comments section!
