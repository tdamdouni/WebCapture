# Discovery of Node.js by a Java Developer

_Captured: 2017-08-27 at 16:50 from [dzone.com](https://dzone.com/articles/discovery-of-nodejs-by-a-java-developer?oid=twitter&utm_content=buffer69ae0&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Start coding today](https://dzone.com/go?i=155124&u=https%3A%2F%2Fgoo.gl%2FmNOkDt) to experience the powerful engine that drives data application's development, brought to you in partnership with [Qlik](https://dzone.com/go?i=155124&u=https%3A%2F%2Fgoo.gl%2FmNOkDt).

Hello everyone, first things first. My name is Dave Ranjan, I have been a Java Developer since the beginning of time (or so it seems). I always praised Java for how good it is. I love how we can use Java in Android to make beautiful of apps, how it's the first choice for enterprises, and I am fond of (mostly used to) the verbosity of Java. I have developed at least 15 projects using Java. And I am not afraid to say that Java puts food on my table.

Of course, I knew about other languages, I have done a few tasks here and there in Ruby and PHP. I had used JavaScript in my college days, and I was quite obsessed with _document.getElementById()_. Back then, Java was**_ "the server side"_** language and JavaScript was used to manipulate stupid DOM elements. I was never a UI person, so I chose to stick with Java.

I was doing great with my dear language for a year or two, and then there was this AJAX BOOM. Everybody was using it, and no reason! Of course, this was none of my concerns. I didn't really care about the browser, remember, I am **_"the server guy."_**

Then I came to learn about some new platform, which enabled "so-called developers" _(not the real ones, real ones use Java, remember)_ to use JavaScript on the server side. I said, 'how lame. Are they going to create beautiful pages on the server?' (Only kidding here, guys).

I was wrong. Node.js grew almost exponentially. Within a year or two it was "the new thing" in the cafeteria chats. People used to talk about its quick setup of the running server, and fewer lines of codes. I defended Spring Boot. They argued back with points about non-blocking I/O; I reminded them about netty. I really tried, but they had a point. I started skipping my lunches.

A few nights back, my friend (who is also a Java developer) switched her job. In her new job, she had to use Node.js. She asked for help. So here I am, trying to share a few questions I had in my mind while I was researching Node.js.

**_CAUTION: If you find any F-word, that's a typo, I always meant Duck. :D_**

## 1\. What Is Node.js After all?

Well, the index page says:

> Node.js® is a JavaScript runtime built on Chrome's V8 JavaScript engine. Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient. Node.js' package ecosystem, npm, is the largest ecosystem of open source libraries in the world. 

Wait. Wait. Wait. What?

Ok, let me break it for you.

Node.js is simply a library written for V8. Now, the bigger question is, what is V8? Well, V8 is an implementation of JavaScript written in C++. It lets you run standalone JavaScript applications (among other things). V8 compiles and executes JavaScript source code, handles memory allocation for objects, and garbage collects objects it no longer needs. V8's stop-the-world, generational, accurate garbage collector is one of the keys to V8's performance.

If you are from the Java world, you can relate it to something like the JVM, but on steroids.

So, Node.js comes with features which I always dreamt of in Java. It's event-driven, non-blocking I/O is "the thing." If you are not familiar with the terms, here is what they really are:

  * Event-driven: So, think of a scenario, say, if you click the save button, an alert pops up. So, your 'click' is an event, which caused the alert button to pop up. Everything in Node.js is event driven. There is the main thread, which listens for 'events' and then triggers the corresponding callback function (in our case, showing the pop-up).

  * Non-Blocking I/O: First, what is a blocking I/O? Consider a scenario, where a thread asks for some records from a database. It waits there until the database returns with some records. That's a blocking I/O, you have simply blocked that thread until the database returns something to it; your JVM can't use it in the meantime. And you must know how costly (in terms of time complexity) I/O operations are.

But not in this Node world!

With Node.js event-driven programming, you can give a callback function (you must be aware of it if you ever used jQuery), which will be eventually called when your database is done doing whatever it was doing. That's a non-blocking I/O.

By now you must be aware that it's not as scary as it seems; perhaps "interesting" is a better word.

## 1\. Why Node?

#### **Because it Is Popular**

Simple right? Lots are people (and companies) are interested in Node.js. It has the fastest growing body of communities (better SO questions to copy and paste solutions) and largest library counts.

#### **Asynchronous I/O**

As told earlier, Async I/O is one of the most desired features among other communities. Node is built to handle asynchronous I/O from the ground up and is a good match for a lot of common web and network-development problems. In addition to fast JavaScript execution, the real magic behind Node.js is the Event Loop. To scale to large volumes of clients, all I/O intensive operations in Node.js are performed asynchronously.

Queries for some of the newer databases, like CouchDB, are written in JavaScript. Mixing Node.js and CouchDB requires no gear-shifting, let alone any need to remember syntax differences.

Why does this matter? Because Async I/O improves the performance of a system considerably. How? Remember the word Google?

#### **Language**

Node is all JavaScript, so you don't need different languages for front-end and back-end. So there's less dependency on "the server guy." If you know the language and the flow, you too can fix the problem. This led to a new term being coined, "Full Stack Developer." Yeah, Node.js is the culprit.

#### **Simplified Build Processes**

I love Maven. I am a fan of it. Maven has revolutionized Java programming. But there is just one issue. I have to write specifications in XML, I mean seriously, XML was not designed to support programming logic.

With Node.js, you can do it all with just one language.

#### **JSON**

When a database spits out data, developers go all out converting those tuples into meaningful objects; remember all those mappings, tons of POJOs, Hibernate, and what not? Well, you don't need to do anything like with Node, the result comes in JSON format.

Clearly, JSON is a first class citizen in Node.js. This isn't quite correct when I talk about other languages. Of course, there are mappers, but then are they are just mappers.

#### **Fast and Scalable**

Who doesn't loves speed? People love to praise the speed of Node.js. The data comes in and the answers come out like lightning. Node.js doesn't mess around with setting up separate threads with all of the locking headaches.

There's no overhead to slow down anything. You write simple code and Node.js takes the right steps as quickly as possible.

There's one thing we can all agree on: at high levels of concurrency (thousands of connections), your server needs to go to asynchronous nonblocking…you can't go creating threads for every connection.

## 2\. Why Did it Take So Long to Make Node.js?

I mean, Javascript was here, right after Java in 1995. They were like twin sisters. So what took so long to enable JS on servers, while Java was quite easily becoming the king of the server?  
Well, that's the question I am still looking into.

## 3\. What Is npm?

Well, think of npm (node package manager) as a CLI tool to get modules (or libraries in the Java world) created by others. Sounds similar to Maven (or Gradle or Ant). Yes, it is a little bit similar, but I think it is more similar to Maven Central (or JCenter)+ Maven. Maven Central is where developers can host their libraries, and Maven is a CLI tool to get those dependencies.  
In the easiest way possible, it's a way to reuse code from other developers, and also a way to share your code with them, and it makes it easy to manage the different versions of code.

npm comes as a side product when you install Node. So you need not worry about installing it, but yeah, one should definitely go through some of its commands, before diving deep into Node.js (hint: node install is the command you'll be using a lot).

## 4\. MVC Frameworks

Unlike Java MVC frameworks warfare, where Spring has almost won the battle, in Node, the war is still on. Though Express.js has the serious lead, and others like Hapi and Meteor.js are not far behind.

Express.js? Never heard of it?

Well, let's just say it's a simple framework which provides some good folder structure for starters, and provides some of the basic features out the box, like database adapters, ORMs, HTTP Request clients, etc.

Basically, it's good to have a framework because, without it, you might have to reinvent the wheel. Apart from that, others might find it difficult to understand the flow of your code.

If you managed to make it here, I guess you liked the article. So how about recommending this article, so that others can also waste 8 minutes.

[Create data driven applications](https://dzone.com/go?i=155123&u=https%3A%2F%2Fgoo.gl%2FWwzwij) in Qlik's free and easy to use coding environment, brought to you in partnership with [Qlik](https://dzone.com/go?i=155123&u=https%3A%2F%2Fgoo.gl%2FWwzwij).

### Like This Article? Read More From DZone
