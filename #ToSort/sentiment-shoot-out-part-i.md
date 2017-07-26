# Sentiment Shoot-Out: Part I

_Captured: 2017-04-28 at 22:05 from [dzone.com](https://dzone.com/articles/sentiment-shoot-out)_

Let's test out various sentiment frameworks.

## **Performance and Accuracy**

If anyone has numbers for Deep Learning-based sentiment analysis or other frameworks, let me know. Comment here. Thanks! Also, let me know if you have a large dataset that you want to offer, and we can that use for Part 2 with the numbers.

## **Round 'Em Up**

For NLP, mostly I want to do two things:

### **Entity Recognition**

This involves people, facility, organizations, locations, products, events, art, language, groups, dates, time, percent, and money, and can be quantitative, ordinal, and cardinal.

### **Sentiment Analysis**

What is it and why don't people like it?

These two features are very useful as part of a real-time streaming processing of social, email, logs and semistructured document data. I can use both of these in Twitter to ingest via Apache NiFi or Apache Spark. Don't confuse text entity recognition with image recognition that we looked at with TensorFlow previously. You can certainly add that to your flow, as well, but that is working with images, and not text.

My debate with sentiment analysis is: do you give numbers really general terms (like neutral, negative, or positive) or do you get more detailed (like Stanford CoreNLP, which has multiple of each)?

There are a lot of libraries available for NLP and sentiment analysis. The first two decisions are:

  1. **Do you want to run JVM programs**, which are good for Hadoop MR, Apache Spark, Apache Storm, enterprise applications, Spring applications, microservices, NiFi processors, Hive UDFs, and Pig UDFs, and have multiple programming language support (i.e. Java, Scala)

  2. **Or do you want to run on Python**, which is already well-known by many data scientists and engineers, is simple to prototype with no compiling, is very easy to call from NiFi and scripts, and has a ton of great Deep Learning libraries and interfaces?

## **Python Libraries**

Like most things in Python, you can use Pip to install them. You will need a Python 2.7 or 3.0 environment setup with PIP to install and use the libraries I have looked at. spaCY requires numpy and so do many of the others.

`spaCy`:
    
    
    Downloaded 532.28MB 100.00% 9.59MB/s eta 0s
    
    
    Model successfully installed to /usr/lib64/python2.7/site-packages/spacy/data
    
    
    Downloaded 708.08MB 100.00% 19.38MB/s eta 0s
    
    
    Model successfully installed to /usr/lib64/python2.7/site-packages/spacy/data
    
    
    After you install you need to download text and models to be used by the tool.
    
    
    print ent, ent.label, ent.label_

`spaCy` is new and pretty fast and does some cool NER stuff.

`NLTK`:
    
    
    ss = sid.polarity_scores(sys.argv[1])

`NLTK` is usually my go-to Python library. It's pretty quick, very stable, and standard. As you can see, the code to work with it is trivial and can be called from shell scripts, NiFi, Cron, and other streams.

Another `NLTK` option:
    
    
    ss = sid.polarity_scores(sys.argv[1])
    
    
          .format(ss['compound'],ss['neg'],ss['neu'],ss['pos']))

NLTK does sentiment analysis very easily as shown above. It runs fairly quickly, so you can call this in a stream without too much overhead.

`TextBlob`:
    
    
    Spelling in very heard to do. I do not like this spelling product at all it is terrible and I am very mad.
    
    
    Sentiment(polarity=-0.90625, subjectivity=1.0)

`TextBlob` is a nice library that does sentiment analysis and other useful text processing like language translation and spell checking.

The install will look familiar.

## **JVM**

Natural Language Processing for JVM languages (NLP4J) is one option. I have not tried this one yet.

## **Apache OpenNLP**

This one is very widely used and is an Apache project, which makes the licensing ideal for most users. I have a long example of this in this article on Apache OpenNLP.

## **StanfordNLP**

I love StanfordNLP. It works very well, integrates in a Twitter processing flow, and is very accurate. The only issue for many is that it is GPLd and for many use cases will require purchasing a license. It is very easy to use Stanford CoreNLP with Java, Scala, NiFi, and Spark. Stanford NLP has been around forever and is super solid. I have built a NiFi processor to work with this and it returns almost instantly for analyzing tweets.

## **Summary**

Do you have to use _just_ one of these libraries? Of course not. I use different ones depending on my needs. Licensing, performance, accuracy on your dataset, programming language choice, enterprise environment, the volume of data, your corpus, the human language involved, and many other factors come into play. One size does not fit all. If you have sophisticated data scientists and strong Machine Learning pipelines, you may want to pick one and build up your own custom models and corpus.

## **References**
