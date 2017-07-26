# Why Target the Application Layer?

_Captured: 2017-02-19 at 00:09 from [dzone.com](https://dzone.com/articles/why-target-the-application-layer?edition=271895&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-18)_

Like an immune system for your web apps, [IMMUNIO will prevent vulnerabilities](https://dzone.com/go?i=186126&u=http%3A%2F%2Fhubs.ly%2FH05YWt10) from being exploited in the first place.

When most of us think of applications, we think of the various programs we have downloaded to our smartphones. We interact and make requests of these programs to perform whatever function we need. These requests often, if not always, require the application to communicate with another

![Why Target the Application Layer.png](https://www.immun.io/hs-fs/hubfs/Blog/Blog_Images/Why%20Target%20the%20Application%20Layer.png?t=1487087529092&width=92&name=Why%20Target%20the%20Application%20Layer.png)

application through an [API (Application Program Interface)](https://www.immun.io/blog/api-security-an-overview). For the most part, we don't think about the protocols needed to make this communication possible, unless something goes wrong. Communication between applications takes place across an IP network, typically using an OSI (Open Systems Interconnection) model, which provides standardized steps that occur at seven distinct layers. The seventh layer, and only layer that users interact with, is the application layer.

For one application to communicate with another application, computer, or data source, the request travels through seven layers of protocols:

7: Application Layer  
6: Presentation Layer  
5: Session Layer  
4: Transport Layer  
3: Network Layer  
2: Data Link Layer  
1: Physical Layer

Each layer performs a function that enables the next layer to perform its function. Once at the physical layer, the request or information is transmitted back up the stack through the same protocols to its own application layer to be communicated with the original application.

What makes the application layer so valuable to users is the information it accesses. If you go onto your mobile banking application and provide your username and password, you expect to be able to view your balance, transfer funds, deposit money, and more. In order to do this, the application on your phone needs to communicate with and receive data that is stored by your bank. The information stored by your bank travels through the seven layers, from the physical layer to the application layer, making it consumable and transferable to you on your personal device. If your banking app could only give you a static view of your balance, it would still be a little useful, but not as valuable to you as it is with all of the other information and actions it provides. The application layer facilitates the free exchange of information between the user and some other entity.

While this exchange of information is what makes the application layer so valuable to users, it is also what makes it a target to hackers. Finding and exploiting vulnerable code at the application layer means that hackers can easily access or redirect the information the legitimate user requests to themselves. This is done through common, yet prolific, vulnerabilities such as [Cross-Site Scripting](https://www.immun.io/cross-site-scripting-why-it-persists-and-what-to) or SQL Injection, or completely unknown zero-day vulnerabilities. In addition to hacking the application layer via vulnerable code, hackers might also launch [account takeover attacks](https://www.immun.io/blog/preventing-account-takeover-ato) using stolen user credentials, brute force attacks, or session farming techniques to steal data.

By design, the application layer has privileged access to information. By compromising an application, hackers have a direct route to the bounty they are seeking: information in a consumable format, which explains why so many attacks are carried out at this level. In order to protect this sensitive information, it is important to have security infrastructure embedded within the application that can detect and block such attacks in real time when they occur. To learn more about building a comprehensive application security program, check out this eBook: [You've Been Hacked: Why Web Application Security Should Start with RASP.](https://www.immun.io/youve_been_hacked_ebook_why_web_appsec_security_should_start_with_rasp)

[Download this eBook](https://dzone.com/go?i=163136&u=http%3A%2F%2Fhubs.ly%2FH04Q_560) to learn more about common vulnerabilities that affect your Ruby on Rails applications and how to protect these apps, your data and your customers
