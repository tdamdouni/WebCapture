# A Basic Understanding of Web Protocols: HTTP and HTTPS

_Captured: 2017-04-28 at 22:15 from [dzone.com](https://dzone.com/articles/easy-understanding-of-web-protocols-http-and-https?oid=twitter&utm_content=buffer4bffd&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Start coding today](https://dzone.com/go?i=155124&u=https%3A%2F%2Fgoo.gl%2FmNOkDt) to experience the powerful engine that drives data application's development, brought to you in partnership with [Qlik](https://dzone.com/go?i=155124&u=https%3A%2F%2Fgoo.gl%2FmNOkDt).

Before we dive deeper into understanding about HTTP and HTTPS protocol, let's simply try to understand the meaning of the word "protocol."

A protocol is a set of rules that we use for specific purposes. In the current scenario, when we are talking about _protocols, _it is about communication--the way we talk to each other. For instance, a news anchor in the USA speaks in English and because it's English, (most!) Americans are able to understand it. English is the protocol. The moment the news anchor starts speaking in a language that you don't understand, the protocol beats its purpose. Thus, we need both the parties to agree to a set of rules for the communication to take place. The protocol, in this case, is for verbal human communication.

Now, talking about the web in particular, multiple protocols are used to communicate. Primarily for end users the most important and visible protocols are HTTP and HTTPS. Though there are many other protocols as well, HTTP and HTTPS are protocols that cater to most of the population and easily visible in URLs.

## Now, What Does HTTP Mean?

HTTP stands for Hypertext Transfer Protocol. Simply put - these are rules for sending and receiving text-based messages. As we all know, computers work in a language of 1's and 0's i.e. binary. Therefore, potentially every set of 1's and 0's construct something--it could be a word.

Let's say I want to write 'a'. Now, if 0 stands for 'a', 1 stands for 'b', and 01 stands for 'c', I can infer that a combination of 0's and 1's can construct a word as well. In this case, the text is already constructed and is being sent on the wire. The computer works using many languages - pure binary, text, and some other formats like byte codes. Here, what is being transferred is text. I am emphasizing 'text' because this text is interpreted by the browser, and the moment the browser interprets it, it becomes hypertext, and the protocol that transfers the text is referred to as _hypertext transfer protocol - HTTP._

Using HTTP, you can definitely transfer images, text, and even sound, but not videos.

## So, Why HTTPS Protocol? HTTP Seems to Suffice.

We agreed upon the fact that what is being transferred from one point to another is often text. To understand why we need HTTPS protocol, we first should know how wi-fi routers function.

Let's say you are at an airport and you are connecting to the wi-fi which is the property of a third party. Now, when you are communicating over HTTP, the text is being transferred by their router. And if I go to a low version of the router, I can comfortably check and read the text that is being transferred. There could be a password that I might use to log in to your bank site and do a fraudulent transaction! Point being - this is fundamentally insecure. This is called a _man in the middle attack._

![user-web-application-man](https://cdnwp.izooto.com/2016/07/Screenshot-431.png)

> _Now, to save our data from such attacks, we need to encrypt that data._

## ![Understanding web protocols](https://cdnwp.izooto.com/2016/07/Screenshot-430.png)

Encryption and Encryption Levels

Encryption, in simple terms, is hiding information and there are various ways to go about doing this. You must have heard these terms - _128 bit encrypt HTTPS_ and _64 bit encrypt HTTPS_. 128 bit encrypt is a high encryption technique and it's very difficult to decrypt (decode). In the case of HTTPS, when the data is being transferred on the wire, the man in the middle may still know what is being transferred, but can not make sense out of it as the data is encrypted. Only the browser will decrypt it and show it, and the server will decrypt it and use it for transactions.

_For the curious ones out there - There also happens to be a movie on encryption, The Imitation Game. The entire plot of the movie is based on Alan Turing's work in decrypting the German Enigma code, which was to change the course of WWII and help spur the digital revolution. _

### How Does This Work When You Request to Open a Site Via Browser?

To understand this, let's imagine that there is one server that resides somewhere serving all the request for one domain. Now, when I type xyz.com, it's a server that I am connecting to, taking data from, and rendering it in the browser.

To simplify further, imagine a domain name google.com being broadcasted from one server. There resides one machine somewhere connected to the internet and the moment you type google.com in your browser, you connect to that machine, grab data from that machine, and show it in the browser. If you save your picture there, it gets uploaded to that machine. Now, if you want to see that picture, you go to google.com/show-me-my-picture, which transfers the picture from the machine to the browser to be shown to you.

This process cannot be completed if I am not able to reach that particular machine. For this to happen, every machine has an address (the way we have a mobile number) called the IP address and every domain has an IP map. The moment you enter this user-friendly URL - google.com, it converts this name into IP and connects with the router to reach out to that particular server line associated with this URL. Once it reaches the server, it raises a request of what is needed. It is represented as 'google.com/s=', helping the user understand the request made. As a result, the server gives back the results according to the request, which gets rendered to the browser.

### **What Happens When a Request for a Website URL Is Made Which Is on HTTP Protocol?**

As the first step, it is the job of HTTP to find the server and once the communication route is established, the server sends text to the browser. This text could either be in its pure form or encrypted form, which is then rendered by the browser or used for whatever purpose it's meant for.

To determine how difficult an encrypted message is to decrypt, one can look at the number of bits. The higher the number, the more difficult it is to decrypt. However, it only increases the level of complexity, making it very difficult to decrypt, but not impossible.

## Deciding Between HTTP and HTTPS

![understanding the importance of HTTPS protocol](https://cdnwp.izooto.com/2016/07/HTTPS-Schema.jpg)

> _Source: http://en.flossmanuals.net/basic-internet-security/_all/_

Anything and everything is personal. If you are searching for "How to install an SSL Certificate", that search would be private to you, right? Whether you are browsing, looking for a product, or reading an article, you generally do not want others to know about it. As an end user, I would want to keep these activities private. There are things I might not care to keep private and for those, I can use HTTP. However, for personal information, banking, and transnational information, HTTPS has become a standard.

### HTTPS Sounds Great. What Else Should I Know About It?

There is no denying the fact that privacy has a cost to it. There are a couple of cons:

  1. HTTPS requests take more time to process.
  2. Because they need more time to process, they require more hardware - the server that you are utilizing. This also means additional cost.

Whereas, for HTTP you use less energy as compared to HTTPS because the communication happens faster (without encryption and decryption), I would not refer to this as a _limitation _for HTTPS. It is highly subjective to change and personally I consider it a very low cost that we pay to ensure our privacy.

The idea of building a secure web has been around for a while. Making the web more secure is an agenda being driven by the likes of Google, Facebook, Akamai, and so forth. I mentioned this primarily to reiterate the importance of HTTPS to leading businesses in the space.

Just simply think about the following two reasons:

  1. User Data and User Privacy: Using HTTPS ensures that you as a developer value your users' data, privacy, and security.
  2. Protecting Your Data: As a developer, we would never want to give away our critical data to malicious participants.

### What Is at Stake If You Don't Move to HTTPS?

Here are some of the features which are now only available on HTTPS.

  * GeoLocation: You can no longer seek user's location if you are on HTTP.
  * Web Push Notification: Push Notifications are only available on HTTPS. 
  * GetUserMedia: You can no longer trigger permissions of using a user's camera/microphone if you are on HTTP.
  * HTTP/2: All major browsers, support HTTP/2 for HTTPS now.

Soon to be removed:

  * AppCache: A feature that allows developers to cache content in the browser and make it available for offline viewing will soon be restricted to HTTPS sites.
  * Encrypted Media Extensions: The ability to manage playback of protected content will soon just be relegated to HTTPS.

## Some Frequently Asked Questions

**What is the "Cost" for migrating a website with X user traction from HTTP to HTTPS?**

It is a typical question, but I am afraid there is no answer to this. The cost will depend on nothing but the amount of data you are transferring. There are a lot of variables that will influence the cost, not just the user traction. Here, if we are talking about banking data, you'll need to bear the cost, however significant or insignificant it might be. Any upfront cost of moving from HTTP to HTTPS will most certainly outweigh any costs later down the road.

The entire cost calculation itself is very subjective and I'm afraid don't really have an estimated number for this.

**Does being on HTTPS impact the load time of your website?**

Yes, it does absolutely!

**Why do web push notifications need SSL?**

Yes, web push notifications have been there for a while and can only work on websites that are on HTTPS protocol. Before we answer that question, let us understand a commonality between HTTP and HTTPS...

When the book of protocols was written, it was mentioned that HTTP is a Connection-Less-Protocol. It means that the server sitting in the data center cannot do anything until the browser raises/makes a request. And once the response is given, the browser will decide if it wants to do something about it or not. It is entirely the browser's decision, the server cannot command the browser to take actions. The idea of a random server controlling your browser or your screen/machine is scary. To prevent this possibility, HTTP is and continues to be a Connection-Less-Protocol.

However, messages sent to and from the server can still be decrypted. The reason for the web push notifications to work only on the HTTPS protocol is that the data being pushed and received is private data. To ensure the privacy, it is supported only on HTTPS protocol. Notifications are fundamentally personal to users. We definitely want this communication to be secure.

## Popular Misconceptions or Myths

  * My website is not transactional in nature. It does not need to be on HTTPS protocol.
  * SSL Certificates are expensive.
  * Migrating to HTTPS protocol from HTTP will impact website performance drastically.
  * Impact on other 3rd parties.

Watch this video from the [Progressive Web App Summit ](https://www.youtube.com/watch?v=e6DUrH56g14)to bust all these misconceptions

### More About Web Push Notifications

Interestingly, in the case of web push notifications, it's actually the server pushing data to the browser. But it is saved in a manner that the server is only sending a _blip _to the browser intimating that there is a notification waiting for you - that's it. Here is a step-by-step process of what actually happens:

  * Server sends a blip to the browser
  * Then the protocol kicks in, asking for data. This data could be very personalized. I might be sending you message - 'You have transacted XX amount'.
  * Notification is fetched by the service worker and displayed to the end user.

### The Idea Behind a Service-Worker

There is another angle to it - to keep the sanity of HTTP, we have service workers. As the server is merely sending a _blip that you have a notification, _it switches to the old conventional connection-less protocol, asking what it needs to show and then showing it. So, the server doesn't push data. It just tells them that there is something. Yes, it becomes a bit complicated, but those who understand service workers, know that they're meant to keep HTTP as sacred as it was supposed to be.

## Conclusion

It's probably pretty obvious but if I had to decide which protocol to use today, I would definitely choose HTTPS. It just makes sense if you want to have access to all of the latest features of the modern web, get high placement in Google search rankings, and of course to keep your users and yourself secure.

[Create data driven applications](https://dzone.com/go?i=155123&u=https%3A%2F%2Fgoo.gl%2FWwzwij) in Qlik's free and easy to use coding environment, brought to you in partnership with [Qlik](https://dzone.com/go?i=155123&u=https%3A%2F%2Fgoo.gl%2FWwzwij).
