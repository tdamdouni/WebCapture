# Measuring satisfaction: Beyond the usability questionnaire

_Captured: 2016-03-22 at 14:07 from [medium.com](https://medium.com/@userfocus/measuring-satisfaction-beyond-the-usability-questionnaire-10095219998e#.lqh27i9nb)_

![](https://cdn-images-2.medium.com/max/2000/1*iyqd_8Z52vh9SNgp0dTUBw.jpeg)

A common mistake made by novice usability test moderators is to think that the aim of a usability test is to elicit a participant's reactions to a user interface. Experienced test moderators realise that a participant's reaction is just one [measure of usability](http://userfocus.co.uk/articles/discount.html). To get the complete usability picture, we also need to consider effectiveness (can people complete their tasks?) and efficiency (how long do people take?).

These dimensions of usability come from the International Standard, [ISO 9241-11](http://userfocus.co.uk/resources/iso9241/part11.html), which defines usability as:

> "Extent to which a product can be used by specified users to achieve specified goals with effectiveness, efficiency and satisfaction in a specified context of use."

The ISO definition of usability makes it clear that user satisfaction is just one important dimension of usability. People may be well disposed to a system but fail to complete business-critical tasks with it, or do so in a roundabout way. The three measures of usability -- effectiveness, efficiency and satisfaction -- [are independent](http://www.diku.dk/~kash/papers/CHI2000_froekjaer.pdf) (PDF document) and you need to measure all three to get a rounded measure of usability.

### Importance of collecting satisfaction measures

A second mistake made by people new to the field of usability is to measure satisfaction by using a questionnaire only (either at the end of the session or on completion of each task). There are many [issues to consider when designing a good questionnaire](http://userfocus.co.uk/articles/surveys.html), and few usability questionnaires are up to scratch.

For example, few usability questionnaires undergo tests of reliability. This means that the same questionnaire may yield different results at different times (this can be checked by measuring the questionnaire's test-retest reliability). Even fewer usability questionnaires are assessed for validity. This means that there is no guarantee that the questionnaire actually measures user satisfaction.

### Problems with measuring satisfaction

In our studies, we notice that participants tend to rate an interface highly on a post-test questionnaire even when they fail to complete many of the tasks. I've spoken to enough of my colleagues at conferences and meetings to know that this problem is commonplace. Is this because we are about to give the participant £75 for taking part in a test session or is there something else at work? For example, one group of researchers makes this point:

> "In studies such as this one, we have found subjects reluctant to be critical of designs when they are asked to assign a rating to the design. In our usability tests, we see the same phenomenon even when we encourage subjects to be critical. We speculate that the test subjects feel that giving a low rating to a product gives the impression that they are "negative" people, that the ratings reflect negatively on their ability to use computer-based technology, that some of the blame for a product's poor performance falls on them, or that they don't want to hurt the feelings of the person conducting the test." -- Wiklund et al (1992).

Once you ask participants to assign a number to their experience, their experience suddenly becomes better than it actually was. We need some way of controlling this tendency.

### The Microsoft Desirability Toolkit

There are alternatives to measuring satisfaction with a questionnaire. A few years back, researchers at Microsoft developed the "[Desirability Toolkit](http://www.microsoft.com/usability/UEPostings/DesirabilityToolkit.doc)" (Word document). This comprised a series of 118 "product reaction cards", containing words like "Consistent", "Sophisticated" and "Useful". On completion of a usability test, participants were asked to sort through the cards and select the five cards that most closely matched their personal reactions to the system they had just used.

The five selected cards then became the basis of a post-test guided interview. For example, the interviewer would pick one of the cards chosen by the participant and say, "I see that one of the cards you selected was 'Consistent'. Tell me what was behind your choice of that word".

I've used this approach in several usability studies and what has struck me is the fact that it helps elicit negative comments from participants. This methodology seems to give participants "permission" to be critical of the system. Not only do participants choose negative as well as positive adjectives, they may also place a "negative" spin on an otherwise "positive" adjective. For example, "Sophisticated" at first sounds positive but I have had participants choose this item to mean, "It's a bit too sophisticated for my tastes".

### An alternative implementation

Asking people to sort through a set of product reaction cards adds a level of complexity to the implementation that's not really necessary. In our studies, we now use a simple paper checklist of adjectives. We first ask people to read through the words and select as many as they like that they think apply to the interface. We then ask the participant to circle just 5 adjectives from those chosen, and these adjectives become the basis of the post-test guided interview.

### Customising the word list

The precise adjectives are not set in stone -- remember this is a technique to help participants categorise their reactions to an interface that you then explore in more depth in the post-test guided interview. This means that, for a particular study, you should replace some of the words with others that may be more relevant. For example, if we were usability testing a web site for a client whose brand values are "Fun, Value for Money, Quality and Innovation", we would replace four of the existing adjectives with those. (This makes for an interesting discussion with the client when participants don't select those terms. It gets even more interesting if participants choose antonyms to the brand values, such as "Boring", "Expensive", "Inferior" and "Traditional"). This is similar to Brand Tags: [whatever people say a brand is, is what it is](http://www.brandtags.net/).

### How to analyse the data

The real benefit of this approach is in the way it uncovers participant reactions and attitudes. You get a depth of understanding and an authenticity in participants' reactions that just can't be achieved with traditional questionnaires and surveys. So this approach is ideal as a qualitative approach to guide an interview.

But you can also derive metrics from these data. Here's how.

### Word cloud

The simplest measure is to count up the number of times a word was chosen by participants. In our studies, we find that we get a fair amount of consistency in the words chosen. For example, Figure 1 shows a word cloud from the results we obtained from a recent 12-participant usability test.

![](https://cdn-images-2.medium.com/max/800/0*-hJiuP1KbLQrCCKo.gif)

> _Figure 1: Example word cloud. The larger the font size and the greater the contrast, the more frequently participants selected the adjective._

Participants could choose from a corpus of 103 words but some words were selected more often (such as "Easy to use", which was selected by half the participants). The font size of each item in the word cloud is directly proportional to the number of times the adjective was selected (the Figure also shows less frequently selected adjectives in lower contrast text). If you don't feel comfortable hacking Word to create a word cloud, use the excellent [Wordle](http://wordle.net/create), a web site that will make these word clouds for you and provides lots of control over the font used and the placement of text.

### Verbal protocol analysis

A more robust statistic can be derived from carrying out a verbal protocol analysis of the guided interview where the participant discusses the reasons for his or her choice of words. This simply means listening to the post-test interview and coding each participant's comments. The simplest way to do this is to divide a piece of paper into two columns and write "Positive" at the top of one column and "Negative" at the top of the other column. Listen to the interview (either live or recorded) and every time you hear the participant make a positive comment about the interface, place a mark in the "Positive" column. Every time you hear the participant make a negative comment about the interface, place a mark in the "Negative" column. At the end of the interview, you add up the positive and negative totals and compute the percentage of positive comments.

So for example, if there are 5 positive comments and 5 negative comments the percentage of positive comments is 50% (5 divided by 10). Similarly, if there are 9 positive comments and 3 negative comments the percentage of positive comments is 75% (9 divided by 12). This could be used as a satisfaction metric to compare interfaces.

### Now you try

If you would like to try out this method in one of your own studies, we've developed an Excel spreadsheet that you can use to generate and randomise the word list. (Randomisation of the list prevents order effects). The spreadsheet also contains a worksheet that lets you analyse the data and generate a word cloud. We do this by using an advanced feature in [Wordle](http://wordle.net/create). (It bothers us that Wordle applies colours randomly. We want the colour to convey information like the text size does, as in Figure 1 above. So we used some Excel tomfoolery to generate colour information for [Wordle](http://wordle.net/create). This way, the most popular adjectives are also the darkest and the less popular comments fade into the distance). The Excel file contains macros; you can disable the macros if you want and still print the word list, but you'll lose the randomisation and analysis functionality. I hope you find it useful to start collecting more in-depth measures of user satisfaction.

### Literature cited

Benedek, J. and Miner, T. "[Measuring Desirability: New Methods for Evaluating Desirability in a Usability Lab Setting](http://www.microsoft.com/usability/UEPostings/DesirabilityToolkit.doc)." (Word document) Redmond, WA: Microsoft Corporation, 2002.

Wiklund, M., Thurrott, C. and Dumas, J. (1992). "Does the Fidelity of Software Prototypes Affect the Perception of Usability?" _Proc. Human Factors Society 36th Annual Meeting_, 399-403.

#### Acknowledgements

_Thanks to __[Miles Hunter_](http://www.linkedin.com/in/mileshunter)_ for developing the idea of the Excel spreadsheet and for the __[Wordle_](http://wordle.net/create)_ tomfoolery._
