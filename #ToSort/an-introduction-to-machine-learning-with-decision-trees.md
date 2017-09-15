# An Introduction to Machine Learning With Decision Trees

_Captured: 2017-08-24 at 23:54 from [dzone.com](https://dzone.com/articles/machine-learning-with-decision-trees?edition=317404&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-20)_

> " _**Machine learning**_ is the subfield of computer science that gives computers the ability to **learn** without being programmed." -- Arthur Samuel, 1959 

Machine learning is a buzzword in the technology world right now. It is fun, challenging, puzzling, and even a bit scary if you're one of those people who believes robots will someday steal our jobs and rule the world. Whether we like it or not, we are surrounded by adaptive smart things that can fix some of our most common daily queries in a split second.

![85e106ae-bc60-4759-8bf5-70fe3c126fd5-original](https://ramandeep2017.files.wordpress.com/2017/07/85e106ae-bc60-4759-8bf5-70fe3c126fd5-original.jpeg?w=356)

Machine learning was embodied in the famous Skynet from the _Terminator_ franchise. Some are afraid of this fantasy becoming real, while some are excited about a whole new world of opportunities we'll get in the AI world. Sure, this future AI may want to eradicate the entire human race... but for now, we can achieve much more than we can even imagine with it.

Google self-driving cars, Facebook face recognition, Amazon recommendations, speech recognition with Siri and Cortana, fraud detection by PayPal... the list is long and growing!

So, that was a brief intro into ML. Now, let's look into decision trees, one machine learning technique.

## What Are Decision Trees?

Simply put, a decision tree is a tree in which each branch node represents a choice between a number of alternatives and each leaf node represents a decision.

It is a type of supervised learning algorithm (with a predefined target variable) that is mostly used in classification problems and works for both categorical and continuous input and output variables. It is one of the most widely used and practical methods for inductive inference. (Inductive inference is the process of reaching a general conclusion from specific examples.)

Decision trees learn and train themselves from given examples and predict for unseen circumstances.

![inductivenference](https://ramandeep2017.files.wordpress.com/2017/08/inductivenference.gif?w=640)

> _A graphical representation of a sample decision tree could be:_

![Image result for decision tree](https://i1.wp.com/cloudmark.github.io/images/kotlin/ID3.png)

## Decision Tree Algorithm: ID3

ID3 stands for Iterative Dichotomizer 3. The [ID3 algorithm](https://www.cise.ufl.edu/~ddd/cap6635/Fall-97/Short-papers/2.htm) was invented by Ross Quinlan. It builds a decision tree from a fixed set of examples and the resulting tree is used to classify future samples.

The basic idea is to construct the decision tree by employing a top-down, greedy search through the given sets to test each attribute at every tree node.

![](https://ramandeep2017.files.wordpress.com/2017/08/02705-1cjv-yipk8pejnitg2vxava.png?w=640)

Sounds simple -- but which node should we select to build the correct and most precise decision tree? How would we decide that?

Well, we have some measures that can help us in selecting the best choice!

### **Entropy**

In information theory, _entropy_ is a measure of the uncertainty about a source of messages. It gives us the degree of disorganization in our data.

Given a collection S containing positive and negative examples of some target concept, the entropy of S relative to this boolean classification is:

Here, p+ and p- are the proportion of positive and negative examples in S.

Consider this entropy function relative to a boolean classification, as the proportion of positive examples p+ varies between 0 and 1.

![Screenshot from 2017-08-12 23-11-21](https://ramandeep2017.files.wordpress.com/2017/08/screenshot-from-2017-08-12-23-11-21.png?w=335)

Notice that the entropy is 0 if all members of S belong to the same class. For example, if all members are positive (p+ = 1), then p- is 0, and Entropy(S) = -1. log2(1) - 0\. log2 0 = -1. 0 - 0\. log2 0 = 0.

The entropy is 1 when the collection contains an equal number of positive and negative examples.

If the collection contains unequal numbers of positive and negative examples, the entropy is between 0 and 1.

### **Information Gain**

It measures the expected reduction in entropy. It decides which attribute goes into a decision node. To minimize the decision tree depth, the attribute with the most entropy reduction is the best choice!

More precisely, the information gain Gain(S, A) of an attribute A relative to a collection of examples S is defined as:

![Screenshot from 2017-08-12 23-53-05](https://ramandeep2017.files.wordpress.com/2017/08/screenshot-from-2017-08-12-23-53-05.png?w=640)

> _= Each value v of all possible values of attribute A_

  * **S**

  * **Sv** = Subset of S for which attribute A has value v

  * **|Sv|** = Number of elements in Sv

  * **|S|** = Number of elements in S

Let's see how these measures work!

Suppose we want ID3 to decide whether the weather is good for playing baseball. Over the course of two weeks, data is collected to help ID3 build a decision tree. The target classification is "should we play baseball?" which can be yes or no.

See the following table.

**Day**

**Outlook**

**Temperature**

**Humidity**

**Wind**

**Should I play baseball?**

D1

Sunny

Hot

High

Weak

No

D2

Sunny

Hot

High

Strong

No

D3

Overcast

Hot

High

Weak

Yes

D4

Rain

Mild

High

Weak

Yes

D5

Rain

Cool

Normal

Weak

Yes

D6

Rain

Cool

Normal

Strong

No

D7

Overcast

Cool

Normal

Strong

Yes

D8

Sunny

Mild

High

Weak

No

D9

Sunny

Cool

Normal

Weak

Yes

D10

Rain

Mild

Normal

Weak

Yes

D11

Sunny

Mild

Normal

Strong

Yes

D12

Overcast

Mild

High

Strong

Yes

D13

Overcast

Hot

Normal

Weak

Yes

D14

Rain

Mild

High

Strong

No

The weather attributes are outlook, temperature, humidity, and wind speed. They can have the following values:

  * outlook = { sunny, overcast, rain }

  * temperature = {hot, mild, cool }

  * humidity = { high, normal }

  * wind = { weak, strong }

We need to find which attribute will be the root node in our decision tree.

  * Entropy(S) = - (9/14) Log2 (9/14) - (5/14) Log2 (5/14) = 0.940

  * Gain(S,Wind) = Entropy(S) - (8/14)*Entropy(Sweak) - (6/14)*Entropy(Sstrong)

  * = 0.940 - (8/14)*0.811 - (6/14)*1.00

  * = 0.048

  * Entropy(Sweak) = - (6/8)*log2(6/8) - (2/8)*log2(2/8) = 0.811

  * Entropy(Sstrong) = - (3/6)*log2(3/6) - (3/6)*log2(3/6) = 1.00

For each attribute, the gain is calculated and the highest gain is used in the decision.

  * Gain(S, Outlook) = 0.246

  * Gain(S, Temperature) = 0.029

  * Gain(S, Humidity) = 0.151

Clearly, the outlook attribute has the highest gain. Therefore, it is used as the decision attribute in the root node.

Since outlook has three possible values, the root node has three branches (sunny, overcast, rain). The next question is, _What attribute should be tested at the sunny branch node?_ Since we've used outlook at the root, we only decide on the remaining three attributes: humidity, temperature, or wind.

  * Ssunny = {D1, D2, D8, D9, D11} = 5 examples from the table with outlook = sunny

  * Gain(Ssunny, Humidity) = 0.970

  * Gain(Ssunny, Temperature) = 0.570

  * Gain(Ssunny, Wind) = 0.019

Humidity has the highest gain; therefore, it is used as the decision node. This process goes on until all data is classified perfectly or we run out of attributes.

![](https://www.cise.ufl.edu/~ddd/cap6635/Fall-97/Short-papers/Image3.gif)

> _The decision tree can also be expressed in rule format:_

  * IF outlook = sunny AND humidity = high THEN play baseball = no

  * IF outlook = rain AND humidity = high THEN play baseball = no

  * IF outlook = rain AND wind = strong THEN play baseball = yes

  * IF outlook = overcast THEN play baseball = yes

  * IF outlook = rain AND wind = weak THEN play baseball = yes

So, that was a very quick intro to decision trees. It's as simple as depicted above. I hope this article helps you!
