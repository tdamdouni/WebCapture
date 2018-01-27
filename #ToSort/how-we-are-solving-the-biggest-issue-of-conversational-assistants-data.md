# How we are solving the biggest issue of conversational assistants: Data

_Captured: 2017-11-23 at 20:08 from [medium.com](https://medium.com/snips-ai/how-we-are-solving-the-biggest-issue-of-conversational-assistants-data-f34600048e80)_

# How we are solving the biggest issue of conversational assistants: Data

## [Data Generation](https://www.producthunt.com/posts/data-generation-by-snips) is the solution for making assistants smarter

There are two terrible parts to moving into a new apartment. First, is actually getting everything from one place to the next, and second is not knowing how to work any of your new appliances. Last night I prepared the ingredients needed to cook the first meal in my beautiful new kitchen, only to spend an hour in a fight with my oven trying to override the child-proof settings. With my guests first making fun of me, and then simply annoyed and hungry -- I thought to myself, there must be a better way…

![](https://cdn-images-1.medium.com/max/2000/1*gWnIlgKUVZdLte_Snspvsw.jpeg)

> _The culprit_

For decades we have had to learn how each device works. One at a time, every coffee machine, dishwasher, TV, phone, app or website requires us to spend time figuring out how its unique interface and logic works. And most of the time we don't even use them the right way, hacking our way through instead of using all the built-in features. The more we want to use technology in our daily lives, the more effort and energy it takes. Keeping a mental map of how everything works is simply not scalable.

We are dangerously close to reaching our technological saturation point, creating a growing gap between the techno-savvy and the device-fatigued. So why aren't we using the most natural interface we have? Talking to a machine is the easiest way to communicate with it: we can ask what we want without having to care about how it works. Not only would that help to democratize access to technology (anyone who can speak can now use technology), but it would also make it so intuitive and effortless that we start forgetting it exists. Just like electricity, we can become surrounded by smart machines, without even noticing them. Artificial Intelligence can make our technology disappear into the background!

### Voice is the future

It is therefore not surprising that so many companies are now rushing to add a voice assistant to their product. In fact, since launching Snips in June, we've had over 5,000 developers join our voice platform, and more than 300 companies reaching out to us. The adoption of voice is simply insane, and is expected to grow 3x year on year going forward. Not including smartphones, there will be over 2.5 billion voice-enabled devices by 2021!

![](https://cdn-images-1.medium.com/max/1600/1*4KO2UQMj5ZOAl9U10wtS6g.png)

> _Source: 2017 Voicelabs report_

Although the initial growth has been fueled by general purpose assistants such as the Amazon Echo and the Google Home, we are now seeing a verticalization of voice. Companies are building a voice assistant dedicated to their product, restricting the interaction to whatever the product does. Your coffee machine will have a coffee assistant, your oven a cooking assistant and your bluetooth speaker a music one.

This solves multiple challenges:

  * users no longer need to figure out what the assistant can do, as this is implicit in the product itself. If you are talking to your coffee machine, then you expect it to understand coffee stuff!
  * it enables the voice assistants to be much more robust and lightweight, as you no longer need to pack the entire knowledge of the world in it. Your coffee machine assistant only has to understand coffee stuff, and using this prior knowledge enables the voice assistant to be more focused.
  * companies can keep control of the branding and user experience of their device. Saying "Alexa" or "OK Google" simply doesn't convey the same thing as having Georges Clooney talk back to you in your Nespresso machine ;)
  * it's an easier sell, as consumers no longer have to buy an Amazon Echo or Google Home on top of their new product: the product itself contains a voice assistant. What we see now is a lot of hybrid models, where companies have their own voice assistant AND build an integration with general purpose ones (Siri, Alexa, Google, …). In my opinion, the hybrid approach is the right one, as it combines the best of both worlds.

### How voice assistants understand you

There are multiple steps involved in understanding voice. Each of them require a dedicated algorithm, and comes with its own set of problems to solve.

![](https://cdn-images-1.medium.com/max/2000/1*3NZS30jTdMdipz7yXvhCnA.png)

First, the voice assistant needs to recognize when you are talking to it, something called "wakeword" detection. This is what happens when you say "Alexa", "OK Google" or "Hey Snips". This in itself is an actual challenge, as you need to listen 24/7 and make sure you trigger only when the user is actually talking to you.

The second step involves transcribing the sound of your voice into text, something called "Automatic Speech Recognition", or ASR for short. This is what happens when you are dictating a text on your phone for example. It is also one of the hardest problems to solve, as there are as many ways to pronounce things as there are people on the planet.

The third step involves analyzing that text, and extracting the meaning. This is called "Natural Language Understanding", or NLU. The goal here is to go beyond spotting keywords, and actually understanding the semantic of the sentence. NLU algorithms typically first identify the intention of the user (what they are asking about), then extract the parameters of their query.

From that point, two things can happen: either the assistant can fulfill your query, in which case it will just execute an action or talk back to you, or it will ask for additional information, and engage in dialog. The difference between voice assistants and chatbots is that the latter only involved NLU and dialog, while the former needs the whole voice part too. Therefore, chatbots are a subset of voice assistants in terms of technology.

### Training conversational assistants

Most conversational assistants today build a model for each of the steps above, using a technique called Machine Learning. In a nutshell, it learns to understand what people ask by looking at examples of people asking stuff. As such, the more "training examples" you give it, the better it becomes at understanding users. The algorithms themselves can be as sophisticated as you want, if they don't have enough data to learn from, they won't do much.

Digging down into what training data is needed for each step, we quickly realize that the ASR part only requires to be trained once per language. Basically, you need hundreds of hours of hundreds of peoples speaking, with the corresponding text. But once you've done it for a language, it can transcribe anything the user says into the corresponding text, so the effort only needs to happen once.

![](https://cdn-images-1.medium.com/max/2000/1*inS8q_W_KK0GmHvIC1uS2A.png)

> _"[Hey Keecker, lets start a yoga session!"](https://medium.com/snips-ai/when-snips-meets-keecker-the-home-multimedia-robot-d1e9fcb8e97e)_

While the ASR model needs to be trained only once per language, interpreting the transcribed text (the NLU part) requires training for each specific use case (called "intents") you want it to understand. If you want your coffee machine to understand coffee, you need to train it with examples of people asking for coffee, which have to be annotated to include which part of the sentence is which parameter in the intent (quantity, sugars, milk, etc..). The more parameters exist, the more examples you will need to effectively train the NLU. Voice assistants and chatbots share this logic for the NLU, so you will need to find training data for every single intent you want them to handle.

Since most assistants are completely new products, the data to train it does not exist. It doesn't matter if you are Google or Facebook, if nobody ever spoke to their coffee machine, you will not have coffee machine data. As such, the biggest issue facing anyone building an assistant is how to find the NLU data to train it, **before** the product is actually launched.

To deal with that issue, developers of assistants do two things: first, they manually input a bunch of examples of how they expect people to talk to their assistant, and second, they track how real users talk to their assistant, improving the performance over time. There are multiple issues with this approach however:

  * there is only a limited number of examples anyone can think of, leading to assistants being trained with an average of 30 examples only. This is why assistants are usually terrible when they get launched: they simply didn't have enough data to learn from!
  * tracking user data means invading their privacy, as what they say can be highly sensitive. In fact, 48% of consumers are now concerned about their privacy when using a voice assistant, so this is clearly an issue.
  * the data needs to be manually annotated (you need to say which part of the sentence is which parameter), which is a very tedious, error-prone process.
  * the above steps need to be replicated for every single intent the assistant has. Given that even the simplest assistants can have a dozen intent, you can see how quickly this becomes a huge pain.

It comes to no surprise then to hear that only a handful of assistants are actually being used by people. The work required to make them perform well is so tedious and repetitive that most developers simply hate doing it!

### Data generation to the rescue!

For the past 5 years at Snips, we have been exploring the intersection of AI and Privacy. To us, user data is toxic data, and so we never want to touch it. But we still need data to train our AI assistants, which is why we came up with a radically new concept: **Data Generation**.

In a nutshell, the idea is to create synthetic ("fake") user data based on a small set of examples. Instead of manually creating the dataset or waiting months for real user data, we simply **generate thousands of training examples** by extending from a handful given initially.

This, it turns out, has a number of advantages:

  * it vastly simplifies the life of the developers, as they no longer have to spend hours figuring out all the training examples.
  * it preserves the privacy of end users, as their data no longer needs to be tracked.
  * it solves the day-0 quality problem, as assistants can now be trained with the equivalent of months of user data, before they are even launched.
  * it can be done in parallel, for every intent

This still required manual work, so we took it a step further, making our Data Generation system able to:

  * automatically annotate the slots in generated examples
  * identify ambiguous training examples and flag them
  * generate lots of high quality, high variability examples, thereby increasing linguistic coverage
  * do all of that in a few hours on average
![](https://cdn-images-1.medium.com/max/1600/1*x0V3ru7btqJrq0nksJWT4g.png)

> _Some example generated queries for a movie assistant_

Data Generation not only saves weeks of work for developers building voice assistants and chatbots, it also drastically improves the performances of the NLU! Our [recent benchmark](https://medium.com/snips-ai/benchmarking-natural-language-understanding-systems-google-facebook-microsoft-and-snips-2b8ddcf9fb19) showed that the average F1-Score over multiple intents **increased from an average of 70% to over 93%**!

This is why we are so excited and betting big on Data Generation. From every point of view, this is a better way to build AI assistants.

### Now, you can use it too!

Today, we are launching our Data Generation service on our website [Snips.ai](http://Snips.ai). Our patent-pending technology, which uses a combination of human operators and algorithms, took our 40-people team a year to build. We have been using it with our enterprise customers for months, with amazing results.

Making this available to anyone who needs it is a major step in our roadmap to put an AI assistant in every device. We strongly believe that this will radically improve the user experience of conversational assistants for end users and developers, and thus accelerate the adoption of AI in every aspect of our lives.

> _Screencast of our Data Generation service in action!_

Using our Data Generation service is extremely simple:

  1. create an account on snips.ai
  2. create a new intent
  3. add a description and give a few examples queries
  4. choose the number of training examples to generate, and pay for them
  5. inspect and validate the results, then train your Snips assistant or download the data to use on another platform such as Alexa, Dialogflow or Wit.

That's it.

As someone who has been doing machine learning for over 15 years now, nothing gets me more excited than seeing data flowing in. Being able to create training data out of thin air really feels like magic!

### What else can you do with Snips?

Although our Data Generation service can be used as a standalone product, it is integrated into our voice platform for connected devices. The Snips Voice Platform offers everything from custom wakewords, to Speech Recognition, Natural Language Understanding and Dialog.

Not only does it rely on state of the art deep learning, it also runs completely on-device, with not a single piece of data being sent to the cloud. This means the assistants you build can work offline, guarantee Privacy by Design and GDPR compliance!

> _Our first Snips ad :))_

Our voice platform is free for makers and developers who want to use it for non-commercial purposes (aside from Data Generation). It contains a boatload of super cool features:

  * custom intents builder
  * store containing pre-trained intent that can be forked and extended
  * on-device wakewords such as Hey Snips, [Chappie](http://www.imdb.com/title/tt1823672/) and [Jarvis](http://www.imdb.com/title/tt0371746/?ref_=nv_sr_1), with more being added soon!
  * 100% on-device ASR, NLU and multi-turn dialog
  * Multi-room support
  * Data Generation as a Service
  * Automatic Entity extension from Wikidata when creating a dictionary
  * ASR specialization (we use the information from the NLU to make the ASR better)
  * ASR available in English and French, and NLU available in English, French, Spanish, German and Korean. A lot more are coming soon!
  * Performance metrics per intent, to help you improve them
  * Runs on Raspberry Pi, Android or Linux, with iOS coming soon

Since launching it in June, over 5,000 developers have joined, creating over 14,000 voice assistants! Their projects range from controlling lights to playing voice crosswords or teaching kids geometry.

Have fun and enjoy our product! We can't wait to see what you have built with it :)

![](https://cdn-images-1.medium.com/max/1600/1*bVumt549qc822mpAPvOmrg.png)

_If you liked this article and want to support Snips, please __[upvote it on Product Hunt_](https://www.producthunt.com/posts/data-generation-by-snips) 💙

_Follow us on Twitter __[randhindi_](http://twitter.com/randhindi)_ and __[snips_](https://twitter.com/snips)_._

_If you want to work on AI + Privacy, check our __[jobs page_](https://snips.ai/jobs/)_!_
