# What I Do Not Want to Hear About Microservices Anymore!

_Captured: 2018-02-09 at 22:14 from [dzone.com](https://dzone.com/articles/what-i-do-not-want-to-hear-anymore-about-microserv?edition=360096&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-01-22)_

Learn the Benefits and Principles of [Microservices Architecture for the Enterprise](https://dzone.com/go?i=274453&u=http%3A%2F%2Ftransform.ca.com%2FAPI-microservice-architecture-for-the-enterprise.html%3Fcid%3DNA-DSP-API-AEL-000195-00001674-000000492%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dmicroservices_api_acquire%26utm_content%3Dna_eb1-microservice-arch-ent-ddc-preroll%26mrm%3D)

Today, I'll allow myself a little note of humor, on some things that I've already heard about microservices, in my professional environment as well as in some articles. The wave of the hype on microservices being passed, it is time to ripen a few reflections on this subject. I'm hoping that this article also causes discussion.

## "Let's Go to Microservices - Let's Take This Java Framework!"

No, no, and no! And yes, I heard that sentence! Microservices involve several upstream issues:

  * Do I need microservices?

    * Do I think I need to scale a lot, or not? Will my little back-office program have to bear the same load as Google? Is my project big enough to cut it into lots of small projects?

  * Is the pain/gain factor good?

    * If my inescapable ops team thinks that DevOps is a detergent brand, or if they are not mature enough to host my project, it looks complicated. Similarly, if you're not able to have the adhoc infrastructure to orchestrate your microservices, it's a bit like having a big SUV to drive around town. In both cases, it is unfortunately common...

  * How will I organize myself?

    * There is a real need for communication to be put in place between business, developer, and operator. And if the project looks really big, how will I organize myself to synchronize the teams?

Once these questions have been asked, we can start thinking about what the architecture might look like. For the choice of framework, we can ask several questions:

  * Have you read the literature that says you should not hesitate to have three or four different programming languages? It's not essential, but are you sure that one fits all?

  * Who the hell told you to use that Java framework you're quoting me? Greg the intern because he worked on it during his studies? Even if it is not stupid to work in familiar environments, ask yourself the right questions in terms of ease of implementation, development, lightness of the framework, and its possible technical coverage.

By the way, as I spoke about Architecture Definition, I deeply recommend [this book](http://shop.oreilly.com/product/0636920080237.do) that is totally generic and at the same time microservice-compliant.

## "It's Written That Netflix/Google/Thelastlicorn Does That, So We Do It, Too."

Why, you work for Facebook, right? Sarcasm aside, literature presents the state of art, but you don't have to become a fundamentalist of microservices! Inspire, adapt, and you will get the best possible result. The best microservice architecture is the one adapted to your context. You have moderate means? Aren't you going to have very large peak loads? Do what works at home and for a good price!

## "You Are Using Docker? So You're Doing Microservices!"

Please, don't. Just don't.

## "Yes, Microservices Is REST, and That's All!"

I have good news for you: you're not a fundamentalist in microservices. But I do have some bad news for you, too: you are becoming one. It is often advisable to be on asynchronous exchanges in the backend to facilitate resilience and robustness. REST is only the submerged part of the iceberg, aka APIs exposed externally or for applications. However, there are many full REST microservices architectures that work well. Nobody is perfect. #microservicefundamentalistmyself

## "What Do You Have in Your Docker Image? Oh, Well, a Spring Boot, an API Manager, and Maybe...a Database."

I hesitated too, but to go and yell at the architect and tell him what I thought. Well, it was my client, so I calmed down a little bit the nanosecond after wanting to have a noisy chat. Why but why do people make Docker images where you find so much stuff? To make life easier for the developer? Take a DevOps or sedative, but please don't put your IT in a Docker image. Stay lean!

And you, what do you no longer want to hear about microservices? Feel free to engage in conversation with me in the comments!

Microservices for the Enterprise eBook: [Get Your Copy Here](https://dzone.com/go?i=274454&u=http%3A%2F%2Ftransform.ca.com%2FAPI-microservice-architecture-for-the-enterprise.html%3Fcid%3DNA-DSP-API-AEL-000195-00001674-000000493%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dmicroservices_api_acquire%26utm_content%3Dna_eb2-microservice-arch-ent-ddc-postroll%26mrm%3D)

Opinions expressed by DZone contributors are their own.
