# The linguistics behind chatbots

_Captured: 2017-03-24 at 02:02 from [medium.com](https://medium.com/icapps/the-linguistics-behind-chatbots-ecaa7045589f#.n51v3jwfv)_

![](https://cdn-images-1.medium.com/max/800/1*lgqyyFHbouXXr55PUFEQfw.jpeg)

I've been working as a UX designer for more than 5 years now, but I actually graduated in Applied Linguistics before I ended up where I am now. Though I didn't turn it into my profession, linguistics still interest me.  
At iCapps we are noticing the upcoming trend of chatbots. For me personally, it's very exciting because it actually has a lot to do with linguistics. Chatbots work with a "conversational interface", where the language itself is the UI. In this blogpost, I would like to share with you some of my insights on chatbots from a linguistic point of view.

**What are chatbots?**

Matt Schlicht, founder of Chatbot Magazine, describes a chatbot as follows: "A chatbot is a service, powered by rules and sometimes artificial intelligence, that you interact with via a chat interface". Chatbots are offered through popular messenger services such as Facebook messenger. As a business, you can offer a chatbot as a service to your customer. It can handle simple requests such as making or cancelling appointments. This way, businesses can cut down their response time to customers and thus provide a better service.  
One example is Madison Reed, a company that sells hair colouring products to use at home. Their chatbot assists you in choosing the right colour shade by analysing your current hair colour based on a picture and asking you which colour you want to achieve.

![](https://cdn-images-1.medium.com/max/800/0*c56Ucgnz9tHr19cX.png)

_Madison Reed's chatbot gives clients advice on which colour to choose_

Not only businesses can make use of chatbots; there are also chatbots that can tell you about the weather (Poncho), give medical advice (Lybrate) or give you the latest news on politics (Purple).

**How does it work?**

How do these chatbots understand what the user wants? And how is it able to formulate an answer? To understand this, you should first know that there are two types of chatbots: chatbots based on rules, and chatbots based on artificial intelligence (AI).

Chatbots that are based on rules are quite simple: when the user says A the bot says B, because it's programmed that way. It can only respond to specific commands. It does not actually understand language. It can cope with typos to some extent, but for the rest it is only as smart as it is programmed to be.

Chatbots based on AI are something else: they are able to analyse the natural language of the user, not just commands. It also continuously learns from the conversations it has with people, so it gets smarter along the way. Let's take a closer look at this second type.

Artificial intelligence is something that has intrigued humans for a long time. The Greeks already contemplated the idea of AI in their myths. Take for example the myth of Prometheus: as a punishment, Zeus sent a giant bronze automaton in the form of an eagle to eat Prometheus' liver over and over again. There are also myths that describe huge guardians of metal, robotic dogs etc.  
However, the field of AI was not formally coined until 1956 at a conference at Dartmouth College. It was only then that AI became an official field that was funded for research.  
Fast forward to 2011, when IBM's computer Watson won the quiz show Jeopardy. Watson was able to understand the questions that were asked and determine independently when it was its turn to answer. During the quiz, it processed huge amounts of data, looked at the possible answers and determined which one was the most plausible, all in a few milliseconds, without human intervention. Watson made use of natural language processing (NLP) to analyse the meaning of the questions and give answers in understandable language.

**Natural language processing as the basis for near-human interaction**

Natural language processing (NLP) is a way for computers to analyse, understand and derive meaning from human language. If you want an intelligent system like a chatbot to understand instructions and act upon them, you will need to implement NLP (unless it's a rule-based chatbot like mentioned before). We are already involved with NLP in our daily lives. Think of spellcheck, Google translate, Siri or Cortana, all services that make use of NLP to structure the language you write or utter

Language is considered to be the main 'giveaway' of artificial intelligence, and there is a specific test for it: the Turing Test. During this test, an evaluator communicates with both a human and a machine and needs to tell which one is which. If the evaluator cannot reliably tell the machine from the human, the machine has passed. What's interesting is that the test does not check the ability to give correct answers, only how closely these answers resemble those a human would give.

So how does a computer analyse human language? The process of NLP consists of roughly 5 steps.

1 / The first step is lexical analysis. The lexicon of a language is, simply put, a collection of words and phrases in a language. As a first step, the computer will thus analyse the text and divide it into paragraphs, sentences and words.

![](https://cdn-images-1.medium.com/max/800/0*dmoZWMBGKInSqdMz.png)

_Example of lexical analysis_

2 / The second step is the **syntactic analysis**: the computer analyses the grammatical role of each word in a sentence and identifies the relationship between each word. This is something you probably learned in school: what is the subject of the sentence? Is there a predicate?

![](https://cdn-images-1.medium.com/max/800/0*DBIp1QAyDE6n7z0G.png)

_Example of syntactic analysis_

3 / In the third step, the **semantic analysis**, the computer checks the intrinsic meaning of the words, so that means looking up the meaning of the words as stated in the dictionary. A word can have several meanings, so the computer also needs to map this with the syntactic structures analysed in the previous step to derive the correct meaning.

![](https://cdn-images-1.medium.com/max/800/0*KbdpdIQfwq9RDjUZ.png)

_Example of different meanings of a word. Source: Oxford Dictionaries_

4 / The fourth step is **discourse integration**, which means looking at the meaning of a sentence compared to the sentence that comes before it. We can assume that there is cohesion between the different sentences in a text, so NLP must also take this into account.

![](https://cdn-images-1.medium.com/max/800/0*w3bbVoDFdxYlLvu6.png)

_Example of discourse integration_

5 / Finally, there is the **pragmatic analysis**, which is also the most difficult step for a computer. The pragmatic analysis involves re-interpreting what is said as what was actually meant. This involves taking knowledge from the real world into account because as humans, what we say is not always what we mean. Take for example the sentence: "There's beer in the fridge". If you say this to a guest entering your house, you are not simply describing the contents of your fridge, you are actually offering them a drink. This ambiguity is hard for a computer to handle.

To use NLP in practice, these five steps are poured into computer algorithms. The main programming language that is used for this is Python. Through the algorithms, the language of the user is tokenised and tagged. This corresponds to the lexical analysis I described before: first each word and punctuation mark is defined as a token, a separate unit. Next, each token is tagged to indicate what type of token it is, e.g. a noun, adjective, verb etc. The tokens are then parsed to define their function in the sentence, which corresponds to the syntactic analysis.

![](https://cdn-images-1.medium.com/max/800/0*kSqUB1PFgt13o8SK.png)

_Example of NLP in Python. Source: NLTK.org_

So does a programmer have to manually code endless rules of text in order to have a working bot? No! That is where machine learning comes in; by inserting a large number of correct parses, the bot can learn the most common patterns for the interpretations and apply it to new sentences.

**Machine learning makes bots smarter**

Machine learning (ML) can be defined as an algorithm of making systems learn, by using observations or past experience. Instead of hand-coding large sets of rules, NLP can rely on ML to automatically learn these rules by analysing a **corpus**. A corpus can be a book, news articles, reports or even conversations. **If a bot contains algorithms for machine learning, it becomes smarter the more people talk to it.**

A good example of a bot that makes extensive use of ML is Xiao Ice, and advanced chatbot developed by Microsoft for the Chinese market. This is a so called 'chatterbot' whose main goal it is to have a casual conversation with the person it's talking to. **To learn how to talk like a human, Xiao Ice constantly mines the Chinese internet for human conversations.**

However, ML can also go wrong. Take for example Tay, a Twitter bot that was developed by Microsoft in 2016. Tay constantly learned from what users tweeted to it. In the first 24 hours after Tay was released, it was "attacked" by users that tweeted numerous racist and sexist comments to it. Because of the way Tay worked, it started to reproduce those tweets, because of which Microsoft took it offline.

![](https://cdn-images-1.medium.com/max/800/0*qey0eGicIeLJv9H9.png)

_Tay tweeting racist and sexist comments_

**No visual UI, but UX needs to be flawless**

You may probably wonder: do I need to know all these NLP and ML rules to build a bot? The good news is: no you don't. There are a lot of existing engines that you can use to input your own data.  
Most are however rule-based. It's still quite difficult to make an engine that also generates language, but there are companies that are moving in the right direction.

Also, Google has released their Google Cloud Natural Language API, a new service that gives developers access to Google-powered sentiment analysis, entity recognition, and syntax analysis. This API offers a lot of functionality to work with, so **you don't have to be a linguistic genius to build a great bot**.

Now what is our role as UX designers in relation to bots? Chatbots have a so-called 'conversational interface', the language is in fact the UI. This means we have to design with language. We need to make sure every word or sentence that is uttered by the bot is meaningful and functional. However, we don't need to do this on our own; it could prove useful to cooperate with people who are specialised in human conversation, such as linguists, copywriters, novelists and even comedians. So **even though there is no visual UI, we as UX designers still have an important role to make sure the user experience of chatbots is flawless**.
