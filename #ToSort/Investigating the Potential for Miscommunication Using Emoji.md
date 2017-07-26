# Investigating the Potential for Miscommunication Using Emoji

_Captured: 2016-06-17 at 10:21 from [grouplens.org](http://grouplens.org/blog/investigating-the-potential-for-miscommunication-using-emoji/)_

Hey emoji users: Did you know that when you send your friend on your Nexus, they might see on their iPhone? And it's not just ; this type of thing can happen for all emoji (yes, even ). In a paper ([download](http://grouplens.org/site-content/uploads/ICWSM16_Emoji-Final_Version.pdf)) that will be officially published at [AAAI ICWSM](http://www.icwsm.org/2016/) in May, we show that this problem can cause people to misinterpret the emotion and the meaning of emoji-based communication, in some cases quite significantly. , we know.

What's more, our work also showed that even when two people look at _the exact same emoji rendering_ (e.g., ), they often don't interpret it the same way, leading to even more potential for miscommunication. !

To your smartphone, an emoji is just like any other character (e.g., lower-case 'a', upper-case 'B') and needs to be rendered with a font. Since each smartphone platform (e.g., Apple, Google) has its own emoji font, the same emoji character can look quite different on different smartphone platforms. This is why when a Google Nexus owner sends to a friend with an iPhone, the iPhone owner will actually see . This problem isn't just limited to iPhones and Nexuses: check out all the different renderings of the single emoji character we've been discussing:

![Figure depicting 10 different platform renderings for the grinning face with smiling eyes emoji](http://grouplens.org/site-content/uploads/GrinningFaceWSmilingEyes-1024x205.png)

To investigate whether "emoji font" diversity can cause miscommunication, my colleagues and I conducted a survey to compare how people interpret emoji. We did this for 5 platform renderings (Apple, Google, Microsoft, Samsung, LG) of 22 of the most popular anthropomorphic (i.e., human-looking) emoji. For each emoji rendering, we asked the participants to describe the emoji rendering in words. We also asked them to assess the emotional meaning or _[sentiment](https://en.wikipedia.org/wiki/Sentiment_analysis)_ of each rendering on a scale from -5 (strongly negative) to 5 (strongly positive).

We found that in many cases, there is quite a bit of potential for miscommunication. For example, take a look at the figure below, which shows our emotion (sentiment) results for the "[Grinning Face with Smiling Eyes"](http://unicode.org/emoji/charts/full-emoji-list.html#1f601) emoji character (the one in the figure above). What this figure tells us is that if an iPhone user sends to a Windows Phone, Samsung, LG, or Nexus user, _the iPhone user is sending a mildly negative emoji to someone who will receive it as a relatively positive one._

![Figure showing the varying sentiment ratings for different renderings of the grinning face with smiling eyes emoji](http://grouplens.org/site-content/uploads/SentimentAvg-GrinningFaceWSmilingEyes.png)

More generally, we found that for 9 of our 22 emoji, the average difference in emotion rating between two platforms was greater than 2 points on our -5-to-5 scale.

We also saw that for many emoji renderings, people used different words when describing the emoji. For instance, when seeing this Apple emoji rendering , participants used words like "stop" and "clap," whereas they described the Google version of the same emoji character () with words like "praise" and "hand."

One finding that really surprised us is that a good deal of the potential for miscommunication may come from _different interpretations of the exact same emoji rendering_. In other words, two people looking at the exact same emoji on the same smartphone platform can interpret that emoji quite differently. For example, in the case of the Apple emoji , there were some people who thought it was more positive while others thought it was more negative. The figure below shows the distribution of emotion/sentiment rankings for :

![Figure showing distribution of sentiment ratings for Apple's grinning face with smiling eyes emoji](http://grouplens.org/site-content/uploads/SentimentRatings-GrinningFaceWSmilingEyes_Apple-1.png)

Overall, we found that if you send an emoji _across_ platform boundaries (e.g., an iPhone to a Nexus), the sender and the receiver will differ by about 2.04 points on average on our -5 to 5 sentiment scale. However, even _within_ platforms, the average difference is 1.88 points.

We're excited about continuing this work along a number of fronts: considering emoji in the context of full text messages, investigating emoji communication breakdowns for people from different national cultures, asking similar questions of non-anthropomorphic emoji, building systems to help test the potential for miscommunication in a new emoji rendering, and so on. More generally, a number of scholars have argued that emoji [represent a fundamental shift in language use](http://www.bbc.com/future/story/20151012-will-emoji-become-a-new-language). As such, fully understanding emoji's role in human communication will be an important step in developing the next generation of language technologies.

The paper on this research that [I](http://hannahjeanmiller.weebly.com/) co-wrote with my colleagues [Jacob Thebault-Spieker](http://jacob.thebault-spieker.com/), [Shuo (Steven) Chang](http://www-users.cs.umn.edu/~schang/), [Isaac Johnson](http://www-users.cs.umn.edu/~joh12041/), [Loren Terveen](http://www-users.cs.umn.edu/~terveen/), and [Brent Hecht](http://www.brenthecht.com/) will appear in the proceedings of the [2016 AAAI](http://www.icwsm.org/2016/) [International Conference on Weblogs and Social Media](http://www.icwsm.org/2016/) (ICWSM 2016), a top data science conference. You can download the paper [here](http://grouplens.org/site-content/uploads/ICWSM16_Emoji-Final_Version.pdf), and if you can make it to Cologne, Germany, come see my ICWSM presentation in May.

And lastly, the next time you have a conversation like this, it's probably the emoji's fault!

![Example text conversation showing emoji miscommunication](http://grouplens.org/site-content/uploads/AcrossTextConversation-cropped-1.png)

Please comment below or tweet @grouplens and/or me @hannahjean515 with your thoughts! Thanks for reading!
