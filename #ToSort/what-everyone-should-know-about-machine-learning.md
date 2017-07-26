# What Everyone Should Know About Machine Learning

_Captured: 2017-07-02 at 11:51 from [dzone.com](https://dzone.com/articles/what-everyone-should-know-about-machine-learning?edition=306206&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-01)_

Over the last few months, I've had the opportunity to talk to a lot of decision-makers about artificial intelligence in general and in machine learning in particular. Several of these executives had been asked by their investors about their machine learning (ML) strategies and where they have already implemented ML. So how did this technical subject all of a sudden become a topic of discussion in company boardrooms?

Computers are supposed to solve tasks for humans. The traditional approach is to "program" the desired procedure; in other words, we teach the computer a suitable problem-solving algorithm. The algorithm is a detailed description of a procedure, similar to a recipe. There are many tasks that can be described effectively by an algorithm. For example, in elementary school, we all learned the algorithms used to add numbers. When it comes to carrying out algorithms of this kind quickly and flawlessly, computers are far superior to humans.

![](https://www.talend.com/wp-content/uploads/MachineLearningTalend1.png)

However, this procedure has its limitations. How do we recognize a photo of a cat? This apparently easy task is difficult to structure as an algorithm. Let's pause for a moment and think about it. Even simple instructions such as "has four legs" or "has two eyes" have their drawbacks, because these features may be hidden, or the photo might only show part of the cat. Then we encounter the next task of recognizing a leg or an eye, which is just as difficult as identifying a cat.

This is exactly where the strength of machine learning lies. Rather than having to develop an algorithm to solve the problem, the computer uses examples to learn the algorithm for itself. We train the computer on the basis of samples. Using our cat example, this could mean that we train the system using a large number of photos, with those depicting a cat labeled accordingly (supervised learning). In this way, an algorithm evolves and matures that is eventually capable of recognizing cats on unfamiliar pictures.

![](https://www.talend.com/wp-content/uploads/MachineLearningTalend2.png)

In fact, in this situation, the computer does not usually learn classical programs so much as parameters within a model, for example, edge weights within a network. This principle can be compared with the learning process in our brain (at least, as far as we understand it), in which connections between nerve cells (neurons) adapt. Like the brain, and unlike a classical program, this network with its edge weights is virtually impossible for humans to interpret.

![](https://www.talend.com/wp-content/uploads/MachineLearningTalend3.png)

In this context, a special class of learning methods for artificial neural networks called deep learning has proven to be particularly successful. Deep learning is a specialization of machine learning, which in turn is a subdiscipline of artificial intelligence, a major branch of research in computer science. As early as 2012, a Google research team successfully trained a network of 16,000 computers to identify cats (and other object categories) from images using 10 million YouTube videos. The procedure employed was deep learning.

![](https://www.talend.com/wp-content/uploads/Machine-Learning-Talend-5.png)

Many practice-related problems fall more into the category of "recognizing a cat" than "adding numbers" and cannot, therefore, be solved adequately with algorithms written by humans. It is frequently a question of identifying a pattern in some data, for example recognizing objects in images, text from language or attempted fraud in transaction data.

For a simple case example, let's look at predictive maintenance. Imagine that lots of sensors send streams of data and occasionally a machine breaks down. The challenge then is to learn the patterns in the streams of data that ultimately lead to the malfunction. Once this pattern has been learned, it can be identified during normal operation, so that a potential breakdown can be anticipated and prevented.

Although the principle of machine learning is not new, it is currently enjoying a surge in popularity. There are three main reasons for this; firstly, the availability of large quantities of data necessary for the applications and training ("big data"). Secondly, we now have the huge computing power required, especially in the cloud. And thirdly, a range of open-source projects have led to algorithms being accessible to more or less everyone.

![](https://www.talend.com/wp-content/uploads/MachineLearningTalend6.png)

Machine learning does not replace classical programming, it complements it. It provides tools that allow us to additionally address a major category of problems that had until now been too difficult or even impossible to master. Collectively, these present us with new opportunities while existing systems are also increasingly being adapted to incorporate machine learning functionalities.

Repetitive operations that follow patterns are a typical example. Imagine a computer program with a hundred functionalities accessed via a complex series of menus, but you actively use only a few of these on a day-to-day basis. By observing the steps you usually take, a computer can learn to anticipate your next move and so increase your efficiency. Or, take the allocation and transformation of data (for example, ETL jobs for populating a data warehouse); where the computer "learns" recurring data and objects, many steps can be automated and speeded up.

Further examples are to be found in just about every area: the appropriate tailoring of learning material for individual students (in particular "massive open online courses," or MOOCs), the early diagnosis of diseases, correct target groups for online marketing, customer churn, the automated identification of data quality issues, or the matching of user profiles by dating services.

![](https://www.talend.com/wp-content/uploads/Machine-Learning-Talend-7.png)

Thanks to its advanced tools, Spark (in combination with Hadoop) has established itself as a leading big data framework in the field of machine learning. This approach is also being pursued by Talend, but abstracted a level higher by modeling jobs (both for training and then deployment in production). Modeling reduces complexity and at the same time leads to a degree of independence from the underlying technologies, which continue to change rapidly and therefore are only accessible for few experts.

Only a few specialists need to really understand the finest details of algorithms in the field of machine learning. On the other hand, it is beneficial for everyone to understand the concept of ML, which basically is learning patterns from examples and being able to use these on new sets of data. Ultimately, this broadens the categories of problems that can be addressed with machines and therefore be automated: specifically by decision-making processes. This is exactly what the computer learns; it makes a decision regarding new data based on the knowledge it has accumulated from the training data. On the one hand, we can use this to our advantage -- whatever our business or circle -- by automating decisions. On the other hand, we ourselves represent a constant source of data that other people's machines will analyze in order to optimize their own business.

To sum up, I would like to leave you with the following image: Computers are now capable not only of following clear instructions (think of the addition of numbers) but also of learning through examples (think of the recognition of cats by training with sample images). Depending on the challenge, one procedure might be more suitable than the other. However, both procedures can be combined in an infinite number of ways, and ultimately lead to more opportunities for automation.
