# A Guide to Natural Language Processing (Part 2)

_Captured: 2017-11-25 at 19:22 from [dzone.com](https://dzone.com/articles/a-guide-to-natural-language-processing-part-2?edition=337908&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-25)_

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
