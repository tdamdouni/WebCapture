# A Guide to Natural Language Processing (Part 4)

_Captured: 2017-11-28 at 09:55 from [dzone.com](https://dzone.com/articles/a-guide-to-natural-language-processing-part-4?edition=337920&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-27)_

[Bring the power of Artificial Intelligence to IT Operations](https://dzone.com/go?i=247358&u=http%3A%2F%2Fwww.bmc.com%2Fit-solutions%2Ftruesight.html). Brought to you in partnership with [BMC](https://dzone.com/go?i=247358&u=http%3A%2F%2Fwww.bmc.com%2Fit-solutions%2Ftruesight.html).

Be sure to check out [Part 1](https://dzone.com/articles/a-guide-to-natural-language-processing-part-1), [Part 2](https://dzone.com/articles/a-guide-to-natural-language-processing-part-2), and [Part 3](https://dzone.com/articles/a-guide-to-natural-language-processing-part-3) first!

## Understanding Documents

We're still talking about understanding documents here. Let's continue!

### **Other Uses**

You can apply the same techniques employed to create summaries to different tasks. That is particularly true for the more advanced and semantic-based ones. Notice that the creation of only one summary for many documents is also a different task. That is because you have to take into account different documents lengths and avoid the repetitions, among other things.

A natural application is the identification of similar documents. If you can devise a method to identify the most meaningful sentences of one document, you can also compare the meaning of two documents.

Another objective with common techniques is information retrieval. In short, if a user search for one word -- say, _car_ -- you could use some of these techniques to find documents containing also automobile.

Finally, there is _topic modeling_, which consists in finding the topics of a collection of documents. In simple terms, it means grouping together words with similar themes. It uses more complex statistical methods that the one used for the creation of summaries. The current state-of-the-art is based on a method called Latent Dirichlet allocation.

[Gensim](https://radimrehurek.com/gensim/index.html) is a very popular and production-ready library, that have many such applications. Naturally is written in Python.

[Mallet](http://mallet.cs.umass.edu/) is a Java library mainly designed for topic modelling.

### **Parsing Documents**

Most computer languages are easy to parse. This is not true for natural languages. There are approaches that give good results, but ultimately, this is still an open area of research. Fundamentally, the issue is that the parsing a sentence (i.e. analyzing its syntax) and its meaning are interconnected in a natural language. A subject, a verb, a noun, or an adverb are all words and most words that can be _subject_ can also be _object_.

In practical terms, this means that there are no ready to use libraries that are good for every use you can think of. We present some libraries that can be used for restricted tasks, such as recognizing parts of speech that can also be of use for improving other methods, like the ones for creation of summaries.

There is also the frustrating fact is that a lot of software is made by academic researchers, which means that it could be easily abandoned for another approach or lacking documentation. You cannot really use a work-in-progress, badly maintained software for anything productive. Especially if you care about a language other than English, you might find yourself seeing a good working demo, which was written ten years ago, by somebody with no contact information and without any open-source code available.

#### **You Need Data**

To achieve any kind of result with parsing or generally extracting information from a natural language document, you need a lot of data to train the algorithms. This group of data is called a _corpus_. For use in a system that uses statistical or machine learning techniques, you might just need a lot of real world data possibly divided in the proper groups (i.e. Wikipedia articles divided by category).

However, if you are using a smart system, you might need this corpus of data to be manually constructed or annotated (i.e. the word dog is a noun that has these X possible meanings). A smart system is one that tries to imitate human understanding, or at a least that uses a process that can be followed by humans. For instance, a parser that relies on a grammar which uses rules such as phrase > subject verb (a phrase is made of a subject and a verb), but also defines several classes of verbs that humans would not normally use (i.e. verbs related to motion).

In these cases, the corpus often uses a custom format and is built for specific needs. For example, this [system that can answer geographical questions about United States](http://www.cs.utexas.edu/users/ml/geo.html) uses information stored in a Prolog format. The natural consequence is that even what is generally available information, such as dictionary data, can be incompatible between different programs.

On the other hand, there are also good databases that are so valuable that many programs are built around them. [WordNet](https://en.wikipedia.org/wiki/WordNet) is an example of such database. It is a lexical database that links groups of words with similar meaning (i.e. synonyms) with their associated definition. It works thus as both a dictionary and a thesaurus. The original version is for English, but it has inspired similar databases for other languages.

#### **What You Can Do**

We have presented some of the practical challenges to build your own library to understand text. And we have not even mentioned all the issues related to ambiguity of human languages. So, differently from what we did for past sections, we are just going to explain what you can do. We are not going to explain the algorithms used to realized them, both because there is no space and also without the necessary data they would be worthless. Instead, in the next paragraph, we are just going to introduce the most used libraries that you can use to achieve what you need.

##### **Named-Entity Recognition**

Named-entity recognition basically means finding the entities mentioned in the document. For example, in the phrase _John Smithis going toItaly_, it should identify _John Smith_ and _Italy_ as entities. It should also be able to correctly keep track of them in different documents.

##### **Sentiment Analysis**

Sentiment analysis classifies the sentiment represented by a phrase. In the most basic terms, it means understanding if a phrase indicates a positive or negative statement. A naive Bayes classifier can suffice for this level of understanding. It works in a similar way a spam filter works: It divides the messages into two categories (i.e. spam and non-spam) relying on the probability of each word being present in any of the two categories.

An alternative is to manually associate an emotional ranking to a word. For example, a value between -10/-5 and 0 for catastrophic and one between 0 and 5/10 for _nice_.

If you need a subtler evaluation you need to resort to machine learning techniques.

##### **Parts of Speech Tagging**

Parts of Speech Tagging (usually abbreviated as POS-tagging) indicates the identification and labelling of the different parts of speech (i.e. what is a noun, verb, adjective, etc.). While is an integral part of parsing, it can also be used to simplify other tasks. For instance, it can be used in the creation of summaries to simplify the sentences chosen for the summary (i.e. removing subordinates' clauses).

##### **Lemmatizer**

A lemmatizer return the lemma for a given word and a part of speech tag. Basically, it gives the corresponding dictionary form of a word. In some ways, it can be considered an advanced form of a stemmer. It can also be used for similar purposes; namely, it can ensure that all different forms of a word are correctly linked to the same concepts.

For instance, it can transform all instances of _cats_ in _cat_, for search purposes. However, it can also distinguish between the cases of _run_ as in the verb to _run_ and _run_ as in the noun synonym of a _jog_.

##### **Chunking**

Parts of speech tagging can be considered equivalent to lexing in natural languages. Chunking, also known as shallow parsing, is a step above parts of speech tagging, but one below the final parsing. It connects parts of speech in higher units of meaning, for example complements. Imagine the phrase _John always wins our matches of Russian roulette_:

  * A POS-tagger identifies that Russian is an adjective and roulette a noun

  * A chunker groups together _(of) Russian roulette_ as a complement or two related parts of speech

The chunker might work to produce units that are going to be used by a parser. It can also work independently, for example to help in named-entity recognition.

##### **Parsing**

The end result is the same as for computer languages: [a parse tree](https://tomassetti.me/guide-parsing-algorithms-terminology/#parsingTree). Though the process is quite different, and it might start with a probabilistic grammar or even with no grammar at all. It also usually continues with a lot of probabilities and statistical methods.

The following is a parse tree created by the Stanford Parser (we are going to see it later) for the phrase _My dog likes hunting cats and people_. Groups of letters such as NP indicates parts of speech or complements.

##### **Translation**

The current best methods for automatic machine translation rely on machine learning. The good news is that this means you just need a great number of documents in the languages you care about, without any annotation. Typical sources of such texts are Wikipedia and the official documentation of the European Union (which requires documents to be translated in all the official languages of the Union).

As anybody that have tried Google Translate or Bing Translator can attest, the results are generally good enough for understanding, but still often a bit off. They cannot substitute a human translator.

[TrueSight is an AIOps platform](https://dzone.com/go?i=247359&u=http%3A%2F%2Fwww.bmc.com%2Fit-solutions%2Ftruesight.html), powered by machine learning and analytics, that elevates IT operations to address multi-cloud complexity and the speed of digital transformation.

  


[Bring the power of Artificial Intelligence to IT Operations](https://dzone.com/go?i=247358&u=http%3A%2F%2Fwww.bmc.com%2Fit-solutions%2Ftruesight.html). Brought to you in partnership with [BMC](https://dzone.com/go?i=247358&u=http%3A%2F%2Fwww.bmc.com%2Fit-solutions%2Ftruesight.html).

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

[TrueSight is an AIOps platform](https://dzone.com/go?i=247359&u=http%3A%2F%2Fwww.bmc.com%2Fit-solutions%2Ftruesight.html), powered by machine learning and analytics, that elevates IT operations to address multi-cloud complexity and the speed of digital transformation.
