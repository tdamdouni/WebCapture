# A Guide to Natural Language Processing (Part 3)

_Captured: 2017-11-26 at 20:05 from [dzone.com](https://dzone.com/articles/a-guide-to-natural-language-processing-part-3?edition=337909&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-26)_

[Find out how AI-Fueled APIs from Neura](https://dzone.com/go?i=244221&u=https%3A%2F%2Fhubs.ly%2FH08wTJ10) can make interesting products more exciting and engaging.

Before reading, be sure to check out [Part 1](https://dzone.com/articles/a-guide-to-natural-language-processing-part-1) and [Part 2](https://dzone.com/articles/a-guide-to-natural-language-processing-part-2)!

## **Understanding Documents**

This section contains more advanced libraries to understand documents. We use the term somewhat loosely; we talk about how a computer can extract or manage the content of a document beyond simple manipulation of words and characters.

We are going to see how you can:

  * Generate a summary of a document (i.e. an algorithmic answer to the question, What is this article about?)

  * Sentiment analysis (Does this document contain a positive or negative opinion?)

  * Parse a document written in a natural language

  * Translate a document in another language

For the methods listed in the [previous](https://dzone.com/articles/a-guide-to-natural-language-processing-part-1) [sections](https://dzone.com/articles/a-guide-to-natural-language-processing-part-2), you could build a library yourself with reasonable effort. **From now on, it will get harder.** That is because they might require a vast amount of annotated data (i.e. a vocabulary having each word with the corresponding part of speech) or rely on complex machine learning methods. So, we will mostly suggest using libraries.

This is an area with many open problems and active research, so you could find most libraries in Python, a language adopted by the research community, though you could find the occasional research-ready library in another language.

A final introductory note is that **statistics and machine learning are the current kings of natural language processing**. So, there is probably somebody trying to use TensorFlow to accomplish each of these tasks (i.e. deep news summarization). You might try that, too, if you take into account a considerable amount of time for research.

### **Generation of Summaries**

The creation of a summary, or a headline, to correctly represent the meaning of a document is achievable with several methods. Some of them rely on information retrieval techniques, while others are more advanced. The theory is also divided into two strategies: extracting sentences or parts thereof from the original text, generating abstract summaries.

The second strategy it is still an open area of research, so we will concentrate on the first one.

#### **SumBasic**

SumBasic is a method that relies on the probability of individual words being present in a sentence to determine the most representative sentence:

  1. First, you have to account the number of times a word appears in the whole document. With that, you calculate the probability of each word appearing in the document. For instance, if the word appears 5 times and the document has 525 words, its probability is 5/525.

  2. You calculate a weight for each sentence that is the average of the probabilities of all the words in the sentence. For example, if a sentence contains three words with probability 3/525, 5/525, and 10/525, the weight would be 6/525.

  3. Finally, you score the sentences by multiplying the highest probability word of each sentence with its weight. For example, a sentence with a weight of 0.1 and whose best word has a probability of 0.5 would score 0.1 * 0. 5 = 0.05, while another with weight 0.2 and a word with probability 0.4 would score 0.2 * 0.4 = 0.08.

Having found the best sentence, you recalculate the probabilities for each word in the chosen sentence. You recalculate the probabilities as if the chosen sentence was removed from the document. The idea is that the included sentence already contains a part of the whole meaning of the document. So, that part becomes less important -- and this helps to avoid excessive repetition. You repeat the process until you reach the needed summary length.

This technique is quite simple. It does not require to have a database of documents to build a general probability of a word appearing in any document. You just need to calculate the probabilities in each input document. However, for this to work you have to exclude what is called _stopwords_. These are common words present in most documents, such as _the_ or _is_. Otherwise, you might include meaningless sentences that include lots of them. You could also include stemming to improve the results.

It was first described in [The Impact of Frequency on Summarization (PDF)](http://www.cs.middlebury.edu/~mpettit/tr-2005-101.pdf); there is an implementation available as [a Python library](https://github.com/EthanMacdonald/SumBasic).

The approach based on frequencies is an old and popular one, because it is generally effective and simple to implement. SumBasic is good enough that is frequently used as a baseline in the literature. However, there are even simpler methods. For example, Open Text Summarizer is a 2003 library that uses an even simpler approach. Basically you count the frequency of each word, then you exclude the common English words (e.g., the, is) and finally you calculate the score of a sentence according to the frequencies of the word it contains.

#### **Graph-Based Methods: TextRank**

There are more complex methods of calculating the relevance of the individual sentences. A couple of them take inspiration from PageRank -- they are called LexRank and TextRank. They both rely on the relationship between different sentences to obtain a more sophisticated measurement of the importance of sentences, but they differ in the way they calculate the similarity of sentences.

PageRank measures the importance of a document according to the importance of other documents that links to it. The importance of each document, and thus each link, is computed recursively until a balance is reached.

TextRank works on the same principle: The relationship between elements can be used to understand the importance of each individual element. TextRank actually uses a more complex formula than the original PageRank algorithm because a link can be only present or not, while textual connections might be partially present. For instance, you might calculate that two sentences containing different words with the same stem (i.e. _cat_ and _cats_ both have _cat_ as their stem) are only partially related.

The original paper describes a generic approach, rather than a specific method. In fact, it also describes two applications: keyword extraction and summarization. The key differences are:

  * The units you choose as a foundation of the relationship.

  * The way you calculate the connection and its strength.

For instance, you might choose as units n-grams of words or whole phrases. N-grams of words are sequences of n words, computed the same way you do k-gram for characters. So, for the phrase dogs are better than cats, there are these 3-grams:

  * dogs are better

  * are better than

  * better than cats

Phrases might create weighted links according to how similar they are. Or they might simply create links according to the position they are (i.e. a phrase might link to the previous and following one). The method works the same.

##### **TextRank for Sentence Extraction**

TextRank for extracting phrases uses as a unit whole sentences, and as a similarity measure, the number of words in common between them. So, if two phrases contain the words _tornado_, _data_, and _center_, they are more similar than if they contain only two common words. The similarity is normalized based on the length of the phrases to avoid the issue of having longer phrases having higher similarity than shorter ones.

The words used for the similarity measure could be stemmed. Stopwords are usually excluded by the calculation. A further improvement could be to also exclude verbs, although that might be complicated if you do not already have a way to identify the parts of speech.

LexRank differs mainly because as a similarity measure it uses a standard TF-IDF (Term Frequency--Inverse Document Frequency). Basically, with TF-IDF, the value of individual words is first weighted according to how frequently they appear in all documents and in each specific document. For example, if you are summarizing articles for a car magazine, there will be a lot of occurrences of the word car in every document. So, the word _car_ would be of little relevance for each document. However, the word explosion would appear in few documents (hopefully), so it will matter more in each document it appears.

The paper [TextRank: Bringing Order into Texts (PDF)](http://web.eecs.umich.edu/~mihalcea/papers/mihalcea.emnlp04.pdf) describe the approach. [ExplainToMe](https://github.com/jjangsangy/ExplainToMe) contains a Python implementation of TextRank.

#### **Latent Semantic Analysis**

The methods we have seen so far have a weakness: they do not take into account semantics. This weakness is evident when you consider that there are words that have similar meanings (i.e. synonyms) and that most words can have different meaning depending on the context (i.e. polysemy). Latent semantic analysis attempt to overcome these issues.

The expression _latent semantic analysis_ describes a technique more than a specific method -- a technique that could be used whenever you need to represent the meaning of words. It can be used for summarization but also for search purposes to find words like the query of the user. For instance, if the user searches for _happiness_, a search library using LSA could also return results for joy.

##### **A Simple Description**

The specific mathematical formulas are a bit complex and involve matrices and operations on them. However, the founding idea is quite simple: words with similar meaning will appear in similar parts of a text. So you start with a normal TF-IDF matrix. Such a matrix contains nothing else than the frequencies of individual words, both inside a specific document and in all the documents evaluated.

The problem is that we want to find a relation between words that do not necessarily appear together. For example, imagine that different documents contain phrases containing the words _joy_ and _happiness_ together other words _cookie_ or _chocolate_. The words do not appear in the same sentence, but they appear in the same document. One document contains a certain number of such phrases: _a dog create happiness_ and _dogs bring joy to children_. In this document, LSA should be able to find a connection between _joy_ and _happiness_ through their mutual connection with _dog_.

The connection is build based on the frequency the words appear together or with related words in the whole set of documents. This allows building connection even in a sentence or document where they do not appear together. So, if _joy_ and _happiness_ appear frequently with _dog_, LSA would associate the specific document with the words (_joy_, _happiness_) and _dog_.

Basically, this technique will transform the original matrix from one linking each term with its frequency, into one with a (weighted) combination of terms linked to each document.

The issue is that there are a lot of words, and combinations thereof, so you need to make a lot of calculation and simplifications. And that is where the complex math is needed.

Once you have this matrix, the world is your oyster. That is to say, you could use this measurement of meaning in any number of ways. For instance, you could find the most relevant phrase and then find the phrases with are most close to it, using a graph-based method.

Text summarization and singular value decomposition describe one way to find the best sentences. The Python library `sumy` offers an implementation.

### **Other Methods and Libraries**

The creation of summaries is a fertile area of research with many valid methods already devised. In fact, much more than the ones we have described here. They vary for the approaches and the objective they are designed for. For example, some are created specifically to provide an answer to a question of the user, others to summarize multiple documents, etc.

You can read a brief taxonomy of other methods in Automatic Text Summarization (PDF). The Python library sumy, that we have already mentioned, implements several methods, though not necessarily the ones mentioned in the paper.

Classifier4J (Java), NClassifier (C#), and Summarize (Python) implement a Bayes classifier in an algorithm described as such:

> In order to summarize a document, this algorithm first determines the frequencies of the words in the document. It then splits the document into a series of sentences. Then, it creates a summary by including the first sentence that includes each of the most frequent words. Finally, summary's sentences are reordered to reflect that of those in the original document. -- [Summarize.py](https://github.com/thavelick/summarize/blob/master/summarize.py)

These projects that implement a Bayes classifier are all dead, but they are useful to understand how the method could be implemented.

[DataTeaser](https://github.com/DataTeaser/textteaser) and [PyTeaser](https://github.com/xiaoxu193/PyTeaser) (both in Python, but originally DataTeaser was in Scala) use a custom approach that combines several simple measurements to create a summary of an article.

## Conclusion

That's it for Part 3! Next time, we'll talk about other uses of LSA, parsing documents, and more.

To find out how AI-Fueled APIs can increase engagement and retention, [download Six Ways to Boost Engagement for Your IoT Device or App with AI](https://dzone.com/go?i=244222&u=https%3A%2F%2Fhubs.ly%2FH08wTJ50) today.

Topics:

ai ,nlp ,python ,machine learning ,statistics ,tutorial ,sentiment analysis ,lsa

  


[Find out how AI-Fueled APIs from Neura](https://dzone.com/go?i=244221&u=https%3A%2F%2Fhubs.ly%2FH08wTJ10) can make interesting products more exciting and engaging.

Before reading, be sure to check out [Part 1](https://dzone.com/articles/a-guide-to-natural-language-processing-part-1) here!

## **Classifying Documents**

In this section, we include techniques and libraries that measure and identifies documents. For example, they can detect the language in which a document is written or measure how difficult it is to read it.

### **Text Metrics**

There are two popular metrics of a text that can be easily implemented: reading time and difficulty of the text. These measurements are useful to inform the reader or to help the writer checking that the document respects certain criteria, such as being accessible to a young audience (i.e. low difficulty).

#### **Reading Time**

The simplest way of measuring the reading time of a text is to calculate the words in the document, and then divide them by a predefined _words per minute_ (wpm) number. The words per minute figure represents the words read by an average reader in a minute. So, if a text has 1,000 words and the wpm is set to 200, the text would take five minutes to read.

That is easy to understand and easy to implement. The catch is that you have to pick the correct wpm rate and that the rate varies according to each language. For example, English readers might read 230 wpm, but French readers might instead read 200 wpm. This is related to the length of the words and the natural flow of the language (i.e. a language could be more concise than another; for instance, it might frequently omit subjects).

The first issue is easily solved. For English, most estimates put the correct wpm between 200 and 230. However, there is still the problem of dealing with different languages. This requires to have the correct data for each language and to be able to understand the language in which a text is written.

To mitigate both problems you might opt to use [a measurement of characters count](http://iovs.arvojournals.org/article.aspx?articleid=2166061) in order to estimate the reading time. Basically, you remove the punctuation and spaces, then count the characters and divide the sum by 900-1,000.

On linguistic grounds, the measure makes less sense since people do not read single characters. However, the difference between languages is less evident by counting characters. For example, an [agglutinative language](https://en.wikipedia.org/wiki/Agglutinative_language) might have very long words and thus fewer of them. So, it ends up with a similar number of characters to a fusional language like English.

This works better because the differences in speed of reading characters in each language is smaller as a percentage of the total speed. Imagine, for example, that the typical reader of English can read 200 wpm and 950 cpm, while the typical reader of French can read 250 wpm and 1,000 cpm. The absolute difference is the same, but it is less relevant for reading characters. Of course, this is still less than ideal, but it is a simple solution.

Neither of the measures considers the difficulty of the text. That texts that are difficult to read take more time to read, even with the same number of words or characters.

#### **Calculating the Readability of a Text**

Usually, the calculation of the readability of a text is linked to grades of education (i.e. years of schooling). So, an easy text might be one that can be read by fourth-graders, while a harder one might need a tenth-grade education. That is both a byproduct of the fact that the algorithms were created for educational purposes and the fact that education is a useful anchor for ranking difficulty. Saying that a text is difficult in absolute terms is somewhat meaningless; saying that it is difficult for seventh-graders makes more sense.

There are several formulas, but they are generally all based on the number of words and sentences in addition to either syllables or the number of difficult words. Let's see two of the most famous: Flesch-Kincaid and Dale-Chall.

Neither of these formulas are perfect, but both have been scientifically tested. The only caveat is that they should be used only for checking, and not as a guideline. They work if you write normally. If you try to edit a text to lower the score, the results might be incorrect. For example, if you use short words just to make a text seem easy, it looks bad.

##### **Flesch-Kincaid Readability Formula**

There are two variants of this formula: _Flesch reading ease_ and _Flesch-Kincaid grade level_. They are equivalent, but one output a score (the higher it is, the easier is the text) and the other a corresponding US grade level. We are going to show the first one.

![Image title](https://i0.wp.com/tomassetti.me/wp-content/uploads/2017/11/flesch.png?w=800&ssl=1)

The readability is generally between 100 to 20. A result of 100 indicates a document that can be easily understood by an 11-year-old student, while a result of 30 or less indicates a document suited for university graduates. You can find a complete explanation and ranking table in _[How to Write Plain English](http://www.mang.canterbury.ac.nz/writing_guide/writing/flesch.shtml)_.

The different parameters can be obtained easily. Only calculating the total number of syllables requires a significant amount of work. The good news is that it is actually doable and there is a reliable algorithm for it. The bad news is that the author of TeX (Frank Liang) [wrote his PhD thesis about his hyphenation algorithm](https://www.tug.org/docs/liang/). You can find an implementation and an accessible explanation of the algorithm in [Hyphenopoly.js](https://github.com/mnater/Hyphenopoly). The two problems are equivalent since you can only divide a word into two parts between two syllables.

An alternative is to use a hack: Instead of calculating syllables, count the vowels. This hack has been reporting to work for English, but it is not applicable to other languages -- although, if you use it you lose the scientific validity of the formula, and you just get a somewhat accurate number.

The general structure of the formula has been applied to other languages (i.e. [Flesch-Vacca for Italian](https://it.wikipedia.org/wiki/Roberto_Vacca#Indice_di_leggibilit.C3.A0_Flesch-Vacca)), but each language has different coefficients.

##### **Dale-Chall Readability Formula**

This formula relies also on the number of words and sentences, but instead of syllables, it uses the number of difficult words present in the text.

A difficult word is defined as one that does not belong to a list of 3,000 simple words, that 80% of fourth graders understand.

![Image title](https://i0.wp.com/tomassetti.me/wp-content/uploads/2017/11/dale-chall.png?w=800&ssl=1)

Thus, the formula is easy to use and calculate. The only inconvenience is that you have to maintain a database of these 3,000 words. We are not aware of the formula having been adapted to languages other than English.

The formula generally outputs a score between 4 and 10. Less than 5 indicates a text suitable for fourth-graders, a result of 9 or more indicates a text for college students. You can find a complete table of results at [The New Dale-Chall Readability Formula](http://www.readabilityformulas.com/new-dale-chall-readability-formula.php).

It is natural to think that you could modify the formula, to calculate the difficulty in understanding a specialized text. That is to say, you could define difficult words as words belonging to technical terminology. For example, you could calculate how difficult would be to understand a text for an average person, according to how much computer jargon it contains. Words like _parser_ or _compiler _could be difficult, while _computer_ or _mouse_ could be considered easy. This might work; however, you would have to calculate the correct coefficients yourself.

## Conclusion

That's it for Part 2! Next time, we'll talk more about understanding topics, and introduce generating summaries, graph-based methods, latent semantic analysis, and more.

To find out how AI-Fueled APIs can increase engagement and retention, [download Six Ways to Boost Engagement for Your IoT Device or App with AI](https://dzone.com/go?i=244222&u=https%3A%2F%2Fhubs.ly%2FH08wTJ50) today.
