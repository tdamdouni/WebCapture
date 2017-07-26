# Applications Of Machine Learning For Designers

_Captured: 2017-04-24 at 18:44 from [www.smashingmagazine.com](https://www.smashingmagazine.com/2017/04/applications-machine-learning-designers/)_

  * [0 Comments](https://www.smashingmagazine.com/2017/04/applications-machine-learning-designers/)

Today, too many websites are still inaccessible. In our new book _Inclusive Design Patterns_, we explore how to craft **flexible front-end design patterns** and make **future-proof and accessible interfaces without extra effort**. Hardcover, 312 pages. [Get the book now!](https://shop.smashingmagazine.com/products/inclusive-design-patterns?utm_source=magazine&utm_campaign=inclusive-design-patterns&utm_medium=html-ad-content-1)

As a designer, you will be facing more demands and opportunities to work with digital systems that embody machine learning. To have your say about how best to use it, you need a good understanding about its applications and related design patterns.

This article illustrates the power of machine learning through the applications of detection, prediction and generation. It gives six reasons **why machine learning makes products and services better** and introduces four design patterns relevant to such applications. To help you get started, I have included two non-technical questions that will help with assessing whether your task is ready to be learned by a machine.

Big data and big promises. We are expecting a great many things to happen once the big data deluge has been funnelled into a nurturing stream of bits. Data can be used in many ways. One is to build smart products, and another is to make better design and business decisions. The latter also, ultimately, trickle into products.

Machine learning is a very promising approach radically shaping future product and service development. Machine learning is a branch of artificial intelligence. It employs many methods: Deep learning and neural networks are two well-known instances.

Machine learning means that, instead of programmers providing computers with very detailed instructions on how to perform a task, computers learn the task by themselves. A recent, remarkable milestone was when Google's AlphaGo software learned to master the game of Go at the level of a world champion!

> Pretty much anything that a normal person can do in <1 sec, we can now automate with AI.

This story will lead you into problem discovery through examples of what sorts of problems machines today readily chew on. A basic understanding of machine learning, commonly known as ML, will help. If you are unfamiliar with ML, I suggest you read my [friendly introduction](https://sc5.io/posts/basics-of-machine-learning/) to the topic or [Nvidia's clear explanation](https://blogs.nvidia.com/blog/2016/07/29/whats-difference-artificial-intelligence-machine-learning-deep-learning-ai/) of the differences between ML, AI and deep learning.

As a designer, you will be facing more demands and opportunities to work with digital systems that embody machine learning. As the hype around machine intelligence intensifies, this will lead to technology-driven pressure to extensively utilize machine learning. This may happen with little understanding of its actual benefits and its impact on product desirability and customer experience.

As a designer, to have your say about any plans for machine intelligence and how it is best implemented on the human interface layer, you need to know what it can do and how digital services can utilize it. This post provides an overview of applications, with concrete examples, as well new design guidelines that you can put to work. This will help with making actual design decisions and identifying the right design patterns, including situations when no directly applicable solution exists and you must transfer ideas across domains.

To exploit the capability of machine learning, you must grasp the nature of a task as a computer might see it. The concept I'll use to describe it is the **core problem of learning**. This refers to defining what exactly we would like the computer to learn in order for it to complete the task we have assigned to it. These goals are not always evident at the practical, holistic level of a finished product (say, Tesla's autopilot function). This story will help you to see what goes on under the surface.

Say you want the computer to drive your car.

This is a very high abstraction level learning goal. We need to go further down and break it into smaller chunks. We need to ask questions such as, can the computer accelerate and decelerate, and can the machine recognize red and green lights? To identify the core problem is already a move towards understanding whether the overarching task is a good fit for a machine to learn. Once the core problem of learning is defined well, then it is possible to say whether the ML computers of today can solve it **with adequate accuracy and in a decent amount of time**. This is what matters most for actually making the application work.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/03/AMLD-Robot_bus_warning-780w-opt.jpg)[8](https://www.smashingmagazine.com/2017/04/applications-machine-learning-designers/)

> _Small autonomous buses (in the background) started operating on Aalto University Espoo campus in autumn 2016. The street sign warns about their presence, reminiscent of the first automobiles in the 19th century. (Picture of [Project Sohjoa](http://sohjoa.fi/)[9](https://www.smashingmagazine.com/2017/04/applications-machine-learning-designers/) demonstration in Espoo. Copyright Metropolia UAS, used with permission.) ([View large version](https://www.smashingmagazine.com/wp-content/uploads/2017/03/AMLD-Robot_bus_warning-large-opt.jpg)[10](https://www.smashingmagazine.com/2017/04/applications-machine-learning-designers/))_

Suppose you manage to teach some skill to a machine. How would your product or service benefit from it? Here are six possible benefits:

  * augment,
  * automate,
  * enable,
  * reduce costs,
  * improve safety,
  * create.

In rare cases, machine learning might enable a computer to perform tasks that humans simply can't perform because of speed requirements or the scale of data. But most of the time, ML helps to **automate** repetitive, time-consuming tasks that defy the limits of human **labor cost** or **attentional span**. For instance, sorting through recycling waste 24/7 is more reliably and affordably done by a computer.

In some areas, machine learning may offer a new type of expert system that augments and assists humans. This could be the case in design, where a computer might make a proposal for a new layout or color palette aligned with the designer's efforts. Google Slides already offers this type of functionality through the [suggested layouts feature](https://support.google.com/docs/answer/7130307?co=GENIE.Platform%3DDesktop&hl=en). Augmenting human drivers would improve traffic safety if a vehicle could, for example, start braking before the human operator could possibly react, saving the car from a rear-end collision.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/03/Google_Presentation_Explore-780w-opt.jpg)[12](https://www.smashingmagazine.com/2017/04/applications-machine-learning-designers/)

> _Large preview_

Google Slides provides design assistance via the Explore function. Right pane demonstrates the variations it has generated from elements initially composed by the user.

In 2016, the most celebrated milestone of machine learning was [AlphaGo's victory](https://gogameguru.com/tag/deepmind-alphago-lee-sedol/) over the world champion of Go, [Lee Sedol](https://gogameguru.com/tag/deepmind-alphago-lee-sedol/). Considering that Go is an extremely complicated game to master, this was a remarkable achievement. Beyond exotic games such as Go, Google Image Search is maybe the best-known application of machine learning. Search feels so natural and mundane when it effectively hides away all of the complexity is embeds. With **over 30 billion search queries** every day, Google Image Search constantly gets more opportunities to learn.

There are already more individual machine learning applications than are reasonable to list here. But a [major simplification](https://hbr.org/2016/11/what-artificial-intelligence-can-and-cant-do-right-now) is not sufficient either, I feel. One way to appreciate the variety is to look at successful ML applications from Eric Siegel's book _Predictive Analytics_ from 2013. The listed applications fall under the following domains:

  * marketing, advertising and the web;
  * financial risk and insurance;
  * healthcare;
  * crime fighting and fraud detection;
  * fault detection for safety and efficiency;
  * government, politics, nonprofit and education;
  * human-language understanding, thought and psychology;
  * staff and employees, human resources.

His cross-industry collection of examples is a powerful illustration of the omnipresence of predictive applications, even though not all of his 147 examples utilize machine learning as we know it. However, for a designer, knowing whether your problem domain is among the nine listed will give an idea of whether machine learning has already proven to be useful or whether you are facing a great unknown.

As I see it, the power of learning algorithms comes down to two major applications: **detection and prediction**. Detection is about interpreting the present, and prediction is about the way of the future. Interestingly, machines can also do **generative** or "creative" tasks. However these are still a marginal application.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/03/AMLD-Table_of_functions-780w-opt.png)[17](https://www.smashingmagazine.com/2017/04/applications-machine-learning-designers/)

> _Three main categories of ML applications and their common use cases (_

When you **combine** detection and prediction, you can achieve impressive overall results. For instance, combine the detection of traffic signs, vehicles and pedestrians with the prediction of vehicular and pedestrian movements and of the times to vehicle line crossings, and you have the **makings of an autonomous vehicle**!

This is my preferred way of thinking about machine learning applications. In practice, detection and prediction are sometimes much alike because they don't yet cut into the heart and bones of machine learning (recall the [basics of machine learning](https://sc5.io/posts/basics-of-machine-learning/)), but I believe they offer an appropriate level of abstraction to talk about machine learning applications. Let's clarify these functions through examples.

There are at least four major types of applications of detection. Each deals with a different core learning problem. They are:

  * text and speech interpretation,
  * image and sound interpretation,
  * human behavior and identity detection,
  * abuse and fraud detection.

Text and speech are the most natural interaction and communication methods. Thus, it has not been feasible in the realm of computers. Previous generations of voice dialling and interactive voice response systems were not very impressive. Only in this decade have we seen a new generation of applications that take spoken commands and even have a dialogue with us! This can go so smoothly that we can't tell computers and humans apart in text-based chats, indicating that computers have [passed the Turing test](http://www.bbc.com/news/technology-27762088).

Dealing with speech, new systems such as personal assistant Siri or Amazon's Echo device are capable of interpreting a wide range of communications and responding intelligently. The technical term for this capability is **natural language processing** (NLP). This indicates that, based on successful text and speech detection (i.e. recognition), computers can also interpret the meaning of words, spoken and written, and take action.

Text interpretation enables equally powerful applications. The detection of emotion, or **sentiment**, from text means that large masses of text can be automatically analyzed to reveal what people in social media think about brands, products or presidential candidates. For instance, Google Translate just recently witnessed [significant quality improvements](https://www.nytimes.com/2016/12/14/magazine/the-great-ai-awakening.html) by switching to an ML approach to translations.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/03/AMLD-Amazon-Echo-Dot-780w-opt.jpg)[22](https://www.smashingmagazine.com/2017/04/applications-machine-learning-designers/)

> _Amazon Echo Dot is surfacing as one of the best-selling speech-recognition-driven appliances of early 2017. (View large version)_

> Jeff Bezos says the Echo "isn't about" getting people to shop on Amazon, and he may be right <https://t.co/UuDdAms0Yt> [pic.twitter.com/erodS8hoJg](https://t.co/erodS8hoJg)

Computer vision gives metaphorical eyes to a machine. The most radical example of this is a computer reconstruction of human perception from brain scans! However, that is hardly as useful an application as one that automates the tagging of photos or videos to help you explore Google Photos or Facebook. The latter service recognizes faces to an even scary level of accuracy.

Image interpretation finds many powerful business applications in industrial quality control, recording vehicle registration plates, analyzing roadside photos for correct traffic signs, and monitoring empty parking spaces. The recent applications of computer vision to [skin cancer diagnosis](http://www.computerworld.com/article/2860758/ibm-detects-skin-cancer-more-quickly-with-visual-machine-learning.html) have actually proven more proficient than human doctors, leading to the discovery of new diagnostic criteria!

![](https://www.smashingmagazine.com/wp-content/uploads/2017/03/AMLD-Google_Photos_tagging-780w-opt.jpg)[28](https://www.smashingmagazine.com/2017/04/applications-machine-learning-designers/)

> _A search for "dog" in my personal Google Photos collection brings up several correct instances of dogs I've chanced upon, but also a few false positives. However, I've never tagged a single dog, so the noise is acceptable given the added value of finding any dogs. (Screenshot from February 2017, edited to remove personal information (albums).) ([View large version](https://www.smashingmagazine.com/wp-content/uploads/2017/03/AMLD-Google_Photos_tagging-large-opt.jpg)[29](https://www.smashingmagazine.com/2017/04/applications-machine-learning-designers/))_

Speech was already mentioned, but other audio signals are also well detected by computers. Shazam and SoundHound have for years provided reliable detection of songs either from a recording fragment or a sung melody. The Fraunhofer Institute developed the [Silometer](https://play.google.com/store/apps/details id=de.fraunhofer.idmt.hsa.Silometer), an app to detect varieties of coughs as a precursor to medical diagnosis. I would be very surprised if we don't see many new applications for human and non-human sounds in the near future.

Given that computers are seeing and hearing what we do, it is not surprising that they have became capable of analyzing and detecting human behavior and identity as well -- for instance, with Microsoft Kinect recognizing our body motion. Machines can identify movements in a football game to automatically generate game statistics. Apple's [iPad Pro recognizes](https://backchannel.com/an-exclusive-look-at-how-ai-and-machine-learning-work-at-apple-8dbfb131932b) whether the user is using their finger or the pencil for control, to prevent unwanted gestures. A huge number of services detect what kind of items typically go together in a shopping cart; this enables Amazon to suggest that you might also be interested in similar products.

In the world of transportation, it would be a major safety improvement if we could detect when a driver is about to fall asleep behind the steering wheel, to prevent traffic accidents. **Identity detection** is another valuable function enabled by several signals. A Japanese research institute has developed a [car seat](http://newatlas.com/japanese-car-seat-identification/20947/) that recognizes who's sitting in it. Google's [reCAPTCHA](https://security.googleblog.com/2014/12/are-you-robot-introducing-no-captcha.html) is a unique system that tells apart humans from spam bots. Perhaps the most notorious example of guessing people's health was Target's successful [detection of expectant mothers](http://www.nytimes.com/2012/02/19/magazine/shopping-habits.html). This was followed by a marketing campaign that awkwardly disclosed the pregnancy of Target customers, resulting in much bad publicity.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/03/AMLD-ReCaptcha-large-opt.png)[35](https://www.smashingmagazine.com/2017/04/applications-machine-learning-designers/)

> _Google's reCAPTCHA has simplified spam-fighting in web forms with the help of micro-intelligence from machine learning._

Machine learning is also used to detect and prevent fraudulent, abusive or dangerous content and schemes. It is not always major attacks; sometimes it is just about blocking bad checks or preventing petty criminals from entering the [NFL's Superbowl arena](https://www.wired.com/2001/02/call-it-super-bowl-face-scan-i/). The best successes are found in anti-spam; for instance, Google has been doing an excellent job for years of filtering spam from your Gmail inbox.

I will conclude with a good-willed detection example from the normal human sphere. [Whales can be reliably recognized](http://danielnouri.org/notes/2014/01/10/using-deep-learning-to-listen-for-whales/) from underwater recordings of their sounds -- once more, thanks to machine learning. This can help human-made fishing machinery to [avoid contact with whales](http://www.meetcortex.com/blog/how-machine-learning-can-save-the-whale/) for their protection.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/03/AMLD-Humpback_whale_pixabay-780w-opt.jpg)[39](https://www.smashingmagazine.com/2017/04/applications-machine-learning-designers/)

> _This humpback whale would be all the merrier if all fishing boats were equipped with machine-learning technology to detect their signals. (View large version)_

### Design Pattern: Suggested Features

Text and speech prediction have opened up new opportunities for interaction with smart devices. Conversational interfaces are the most prominent example of this development, but definitely not the only one. As we try to hide the interface and underlying complexity from users, we are balancing between what we hide and what we reveal. Suggested features help users to discover what the invisible UI is capable of.

Graphical user interfaces (GUIs) have made computing accessible for the better part of the human race that enjoys normal vision. GUIs provided a huge usability improvement in terms of **feature discovery**. Icon and menus were the first useful metaphors for direct manipulation of digital objects using a mouse and keyboard. With multitouch screens, we have gained the new power of pinching, dragging and swiping to interact. Visual clues aren't going anywhere, but they are not going to be enough when interaction modalities expand.

Haptic interaction in the first consumer generation of wearables and in the foremost conversational interfaces presents a new challenge for feature discovery. Non-visual cues must be used that facilitate the interaction, particularly at the very onset of the interactive relationship. **Feature suggestions** -- the machine exposing its features and informing the user what it is capable of -- are one solution to this riddle.

In the case of a chatbot employed for car rentals, this could be, "Please ask me about available vehicles, upgrades and your past reservations."

Specific application areas come with specific, detailed patterns. For instance, [Patrick Hebron's recent ebook](http://www.oreilly.com/design/free/machine-learning-for-designers.csp) from O'Reilly contains a great discussion of the solutions for conversational interfaces.

Several generations of TV watchers have been raised to watch weather forecasts for fun, ever since regular broadcasts began [after the Second World War](https://en.wikipedia.org/wiki/Weather_forecasting#Broadcasts). The realm of prediction today is wide and varied. Some applications may involve non-machine learning parts that help in performing predictions.

Here I will focus on the prediction of human activities, but note that the prediction of different **non-human activities** is currently gaining huge interest. Predictive maintenance of machines and devices is one such application, and more are actively envisioned as the Internet of Things generates more data to learn from.

Predicting different forms of human behavior falls roughly into the following core learning challenges and applications:

  * recommendations,
  * individual behavior and condition,
  * collective behavior prediction.

Different types of **recommendations** are about predicting user preferences. When Netflix recommends a movie or Spotify generates a playlist of your future favorite music, they are trying to predict whether you will like it, watch it or listen through to the end of the piece. Netflix is on the lookout for your rating of the movie afterwards, whereas Spotify or Pandora might measure whether you are returning to enjoy the same song over and over again without skipping. This way, our behaviors and preferences become connected even without our needing to express them explicitly. This is something machines can learn about and exploit.

In design, predicting which content or which interaction models appeal to users could give rise to the **personalization** of interfaces. This is mostly based on predicting which content a user would be most interested in. For a few years now, Amazon has been heavily personalizing the front page, predicting what stuff and links should be present in anticipation of your shopping desires and habits.

Recommendations are a special case of predicting **individual behavior**. The scope of predictions does not end with trivial matters, such as whether you like Game of Thrones or Lady Gaga. Financial institutions attempt to predict who will default on their loan or try to refinance it. Big human-resource departments might predict employee performance and attrition. Hospitals might predict the discharge of a patient or the prognosis of a cancer. Rather more serious **humans conditions**, such as divorce, premature birth and even death within a certain timeframe, have been all been predicted with some success. Of course, predicting fun things can get serious when money is involved, as when big entertainment companies try to [guess which songs](http://www.wired.co.uk/article/song-prediction-algorithm) and movies will top the charts to direct their marketing and production efforts.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/03/AMLD-HowOld-780w-opt.png)[44](https://www.smashingmagazine.com/2017/04/applications-machine-learning-designers/)

> _Microsoft's ML platform demonstrator How Old Do I Look? guesses age (a human condition) based on any uploaded photo or search. (View large version)_

The important part about predictions is that they lead to **individual assessment** that are actionable. The more reliable the prediction and the weightier the consequences, the more profitable and useful the predictions become.

Predicting **collective behavior** becomes a generalization of individuals but with different implications and scope. In these cases, intervention is only successful if it affects most of the crowd. The looming result of a presidential election, cellular network use or seasonal shopping expenditure can all be subject to prediction. When predicting financial risk or a company's key performance indicators, the gains of saving or making money are noticeable. J.P. Morgan Chase was one of the first banks to increase efficiency by predicting mortgage defaulters (those who never pay back) and refinancers (those who pay back too early). On the other hand, the recent US presidential election is a good reminder that none of this is yet perfect.

In a close resemblance to tools for antivirus and other present dangers, future trouble is also predictable. **Predictive policing** is about forecasting where street conflicts might happen or where squatters are taking over premises, which would help administrators to distribute resources to the right places. A similar process is going on in energy companies, as they try to estimate the capacity needed to last the night.

### Design Pattern: Personalization

Once a computer gets to know you and to predict your desires and preferences, it can start to serve you in new, more effective ways. This is **personalization**, the automated optimization of a service. Responsive website layouts are a crude way of doing this.

The utilization of machine learning features with interfaces could lead to highly personalized user experiences. Akin to giving everyone a unique desktop and homescreen, services and apps will start to adapt to people's preferences as well. This new degree of personalization presents opportunities as well as forces designers to flex their thoughts on how to create truly adaptive interfaces that are largely controlled by the logic of machine learning. If you succeed in this, you will reward users with a superior experience and will impart a [feeling of being understood](http://www.slideshare.net/UXSTRAT/ux-strat-usa-belmer-negrillo-a-personalization-model-for-adaptive-learning).

![](https://www.smashingmagazine.com/wp-content/uploads/2017/03/AMLD-Amazon_personalization-780w-opt.png)[48](https://www.smashingmagazine.com/2017/04/applications-machine-learning-designers/)

> _Amazon.com's front page has been personalized for a long time. The selection offered to me looks somewhat relevant, if not attractive. (_

Currently, personalization is foremost applied in order to curate content. For instance, Amazon carefully considers which products would appeal to potential buyers on its front page. But it will not end with that. Personalization will likely lead to much bigger changes across UIs -- for instance, even in the presentation of the types of interactive elements a user likes to use.

Say you are now convinced that your users and customers would benefit from a ML-boosted service. Next, you must consider the **business and technology** perspectives. The first question to ask is, If ML works at least as well as you want, what value would it add to your product? Be honest: Traditional business logic applies here, too.

If machine learning doesn't create value, then it is probably a waste of resources. Marketing people might fancy your new implementation, but the business folks will not necessarily fund your next machine learning experiment unless you have a business case for **why machine learning** would improve the customer experience or revenue directly.

OK, suppose you've cleared the viability check box. I expect you also have at least a hypothesis of the core learning challenge. This might be, for example, Can a computer learn to predict when the user would need to take an umbrella or a waterproof jacket when they leave the house in the morning.

Next, you'll need to figure out whether you can expect the machine to learn the job you wish to get done. We've come to **matters of data**. Data broadly refers to any information you can feed the computer: weather data, shopping data for umbrellas and waterproof gear, social media updates and so forth.

Here are two simple diagnostic questions to assess the data situation:

  * Do we have enough examples for the machine to learn from?
  * Are there patterns in the teaching material that can be recognized by a human expert?

The first question looks easy but is difficult to answer in advance. You need both good quality and a sufficient quantity of data. Some signals are noisy (that is, have poor quality). You might need more examples in these cases than in others. Some features are very prominent and easy to learn, such as in the case of detecting nighttime or daytime in photos. This can be solved with as few as [30 training images](https://www.wolfram.com/mathematica/new-in-10/highly-automated-machine-learning/distinguish-daytime-from-nighttime-pictures.html)!

Typical applications require thousands of instances of input data and possibly the desired answers. The more complicated the task, the more material will be needed. AlphaGo learned to master the game after analyzing a [staggering 30 million games](https://www.tastehit.com/blog/google-deepmind-alphago-how-it-works/) and then playing some against itself! This is likely excessive in most situations, but it gives you an idea of the scale of what computers can and may need to swallow -- from 30 to 30 million. This is one of the reasons why increasing computing capacity and certain hardware really makes computers smarter by speeding up the learning of truly big data.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/03/AMLD-AlphaGo-game-780w-opt.png)[52](https://www.smashingmagazine.com/2017/04/applications-machine-learning-designers/)

> _The complexity of Go pushed machine learning capacity to its extremes. Playing the game at random, or by brute force, would be futile. (Image: YouTube) (View large version)_

The second question is, Are **there patterns in the teaching material** that can be recognized by a human expert? If a human can do the task, then there's a fair chance that there are regularities in the data that might be picked up by the computer as well.

If you have a positive answer to least one of the questions, you can go forward with some confidence that machine learning might indeed be of use to you. What you'd do after this discovery is mostly beyond the scope of this article.

In order to build a machine learning solution, it is best to boldly go and prototype your desired functionality. If you have enough samples, your data scientist teammate will quickly discover whether the machine shows proficiency in the learning task (particularly if you use scalable could computing). If not, you'll need to get more data.

What follows is a series of iterations on the learning mechanisms and a process of integrating it with the product or service. The appearance of intelligent applications can be achieved by carefully putting together several pieces of machine learning and even conventional programming. This is called an **ensemble approach**. What at best appears as a seamless interactive experience for the user may in fact be the product of a very complex rubric of different machine learning components working together.

Human intelligence is heavily needed to tweak the learning algorithms. Such was the [architecture underlying Watson](https://www.quora.com/Whats-the-system-architecture-of-the-IBM-Watson), the Jeopardy-winning artificial intelligence system created by IBM and the algorithm that claimed the [Netflix Prize](https://en.wikipedia.org/wiki/Netflix_Prize). In the latter competition, several teams combined their individual tweaks during the final months of the competition to eventually exceed the criteria for success. This is also what the Google Translate team did to ascend to the next level. And that work is something I consider to fall under the domain of traditional software development.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/03/AMLD-Four_design_patterns-780w-opt.png)[57](https://www.smashingmagazine.com/2017/04/applications-machine-learning-designers/)

> _Illustration: Joonas Haverinen, SC5(_

Thus far, I've talked about the possibilities of machine learning and given some practical advice on how to figure out its feasibility. I've also introduced two general design patterns that are tightly connected to machine learning. However, they are not enough.

A designer engaged in service and interface design will have several questions concerning interaction in their mind by now. How can we and will we communicate machine intelligence to users, and what kinds of new interfaces will machine learning call for?

This entails both **opportunities** to do things in a new way, as well as **requirements** for new designs. To me, this means we will need a rise in importance of several design patterns or, rather, abstract design features, which will become important as services get smarter. They include:

  * suggested features,
  * personalization,
  * shortcuts versus granular controls,
  * graceful failure.

I have already covered [suggested features](https://www.smashingmagazine.com/2017/04/applications-machine-learning-designers/) and [personalization](https://www.smashingmagazine.com/2017/04/applications-machine-learning-designers/) as a part of detection and prediction, but what are granularity and graceful failure?

Photoshop is an excellent example of a tool with a steep learning curve and a great deal of **granularity** in controlling what can be done. Most of the time, you work on small operations, each of which has a very specific influence. The creative combination of many small things allows for interesting patterns to emerge on a larger scale. Holistic, black-box operations such as transformative filters and automatic corrections are not really the reason why professionals use Photoshop.

What will happen when machines learn to predict what we are doing repeatedly? For instance, I frequently perform certain actions in Photoshop before uploading my photos to a blog. While I could manually automate this, creating yet another user-defined feature among thousands already in the product, Photoshop might learn to predict my intentions and offer a more prominent **shortcut**, or a highway, to fast-forward me to my intended destination. As Adobe currently puts effort into bringing AI into Creative Cloud, we'll likely see something even more clever than this very soon. It is up to you to let the machine figure out the appropriate shortcuts in your application.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/03/AMLD-Photoshop-ML-prediction-780w-opt.jpg)[61](https://www.smashingmagazine.com/2017/04/applications-machine-learning-designers/)

> _A mockup of a possible implementation of "predictive history" in Photoshop CC. The application suggests a possible future state for the user based on the user's history and preceding actions and on the current image. ([View large version](https://www.smashingmagazine.com/wp-content/uploads/2017/03/AMLD-Photoshop-ML-prediction-large-opt.jpg)[62](https://www.smashingmagazine.com/2017/04/applications-machine-learning-designers/))_

A funny illustration of a similar train of thought comes from Cristopher Hesse's machine-learning-based [image-to-image translation](http://affinelayer.com/pixsrv/index.html), which provides interesting content-specific filling of doodles. Similar to Photoshop's content-aware fill, it creates most hilarious visualizations of building facades, cats, shoes and bags based on minimal user input.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/03/AMLD-Edges2cats-780w-opt.png)[64](https://www.smashingmagazine.com/2017/04/applications-machine-learning-designers/)

> _The edges2cats algorithm employs machine learning to finish your cat doodle as a photorealistic cat monster. (View large version)_

I call the final pattern **graceful failure**. It means saying "sorry, I can't do what you want because…" in an understandable way.

This is by no means unique to machine learning applications. It is innately human, but something that computers have been notoriously bad at since the time that syntax errors were repeatedly echoed by Commodore computers in the 1980s. But with machine learning, it's slightly different. Because machine learning takes a fuzzy-logic approach to computing, there are new ways that the computer could produce unexpected results -- that is, things could go very bad, and that has to be designed for. Nobody seriously blames the car in question for the death that occurred in the Tesla autopilot accident in 2016.

The other part is that building applications that rely on modern machine learning is still in its infancy. Classic software development has been around for so long that we've learned to deal with its insufficiencies better. As Peter Norvig, famous AI researcher and Google's research director, [puts it like this](https://www.youtube.com/watch?v=zMBStaBkezw&t=736s):

> The problem here is the methodology for scaling this up to a whole industry is still in progress.… We don't have the decades of experience that we have in developing and verifying regular software.

The nature of learning is such that computers learn from what is given to them. If the algorithm has to deal with something else, then the results will not be to your liking. For example, if you've trained a system to detect animal species from pet photos and then start using it to classify plants, there will be trouble. This is more or less why Microsoft's Twitterbot Tay [had to be silenced](https://techcrunch.com/2016/03/24/microsoft-silences-its-new-a-i-bot-tay-after-twitter-users-teach-it-racism/) after it picked up the wrong examples from malicious users when exposed to real-world conditions.

The uncertainty in **detection and prediction** should be taken into consideration. How this is done depends on the application. Consider Google Search. No one is offended or truly hurt, but merely amused or frustrated, by bad search results. Of course, bad results will eventually be bad for business. However, if your bank started using a chatbot that suddenly could not figure out your checking account's balance, you would be rightfully worried and should be offered a quick way to resolve your trouble.

To deal with failure, interfaces would do well to help both parties adjust. Users can tolerate one or two "I didn't get that, please say that again" prompts (but no more) if that's what it takes to advance the dialogue. For services that include machine learning, extensive testing is best. Next comes informing users about the probability and consequences of failure, and instructions on what the user might do to avoid it. The good practices are still emerging.

With machine learning, our vision of tomorrow is quickly becoming today's reality.

Overall, there hardly seems to be an application that machine learning could not be used to detect or predict. I've introduced plenty of examples of deploying machine learning to varying success. In all of the examples, I've tried to illustrate some **core learning challenge** to help you understand what sorts of tasks machines respond to. Now it is time to face the question of what machine learning can do for you!

I don't expect that this guide alone will suffice for radical innovation in the sphere of intelligent products and services. I do hope that it will open the eyes of several designers to the opportunities that **machine learning solutions afford us today**. It is important to understand approximately what you can realistically ask from a machine. In the near future, good questions will become ever more important, so that the answer will be, "Yes, Dave. I can do that."

_Thanks to Max Pagels, Janne Aukia, Antti Rauhala, Teemu Kinnunen and Patrick Hebron for discussing the topic. _

Article by [Fabien Girardin: Experience Design in the Machine Learning Era](https://medium.com/@girardin/experience-design-in-the-machine-learning-era-e16c87f4f2e2)

Video of [Andrew Ng: Artificial Intelligence is the New Electricity](https://www.youtube.com/watch?v=21EiKfQYZXc&feature=youtu.be&t=43m16s) (Stanford GSB). Ng talks of product management, but his insights are relevant to design as well.

_(rb, yk, al, il)_
