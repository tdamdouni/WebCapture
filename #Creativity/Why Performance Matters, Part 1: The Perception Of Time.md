# Why Performance Matters, Part 1: The Perception Of Time

_Captured: 2015-12-10 at 09:46 from [www.smashingmagazine.com](http://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/#part-1-objective-time)_

![Deconstructing Performance](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2015/09/00-alice-opt-small.png)[1](http://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/)  


> _"Alice: How long is forever? White Rabbit: Sometimes, just one second." -- Lewis Carroll. "Alice's Adventures in Wonderland."_

![Every how-to, tutorial, guideline has a simple question ](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2015/09/01-tree-opt-small.png)[2](http://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/)  


> _Every how-to, tutorial and guideline has a simple "Why?" at its root. (View large version)_

![Psychological Time in our brain usually differs from Objective Time on the clock](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2015/09/02-perception-opt-small.png)[4](http://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/)  


> _Psychological time in our brain usually differs from objective time on the clock. (_

A , as , "is just what it sounds like: you set a budget on your page and do not allow the page to exceed that." For the purpose of this article, we will consider the performance budget to be directly connected to time -- for example, loading a page, responding to a user's input, etc.

Armed with these definitions, let's go down the rabbit hole.

> Now, here, you see, it takes all the running you can do, to keep in the same place. If you want to get somewhere else, you must run at least twice as fast as that!
> 
> The Red Queen in Lewis Carroll's _Through the Looking-Glass_

As we defined it earlier, objective time is time that can be measured with a clock. In this first article in our series, we will discuss how to use this time more efficiently for our projects.

This phrase, credited to Benjamin Franklin in his _Advice to a Young Tradesman_, still proves true in our contemporary world. According to a [recent study](http://blog.radware.com/applicationdelivery/applicationaccelerationoptimization/2015/03/new-findings-sotu-spring-2015/), it takes only 3 seconds for a visitor to abandon a website. For every 1 second of improvement, Walmart experienced an increase in conversions of up to a 2% on its website. When auto-parts retailer AutoAnything cut loading times in half, it experienced a 13% increase in sales. Users value their time, and a **human-to-human** style of communication is increasingly expected.

![A human-to-human style of communication is increasingly expected from online systems](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2015/09/03-human-to-human-opt-small.png)[9](http://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/)  


> _A human-to-human style of communication is increasingly expected from online systems. (View large version)_

New ways of communication require a new way of thinking in the design and development of online systems. In the web industry, we have been talking about speed and performance for quite a while. We've been emphasizing the importance of fast communication, and we're always trying to reach certain goals in seconds, kilobytes, frames per second and so on. As a result, we know how to make our websites fast using technology. Furthermore, we keep getting advice from leading developers and companies about preferred times in user-to-website interactions. In November 2014, Dimitri Glazkov, Jochen Eisinger and Chris Harrelson, in their "[State of Blink](https://www.youtube.com/watch?v=Ku3znd7JNIk)" keynote about the Blink rendering engine, suggested a [platform success model](http://goo.gl/T2kgmG) based on interaction times.

![Platform success model](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2015/09/04-success_model-opt-small.png)[13](http://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/)  


> _Platform success model from Google (View large version)_

After quite a few years of the "2-second loading time" recommendation, the [platform success model](http://goo.gl/T2kgmG) technically sets the limit on page-loading time to 1 second. Usually, the average developer or project manager is satisfied with an explanation like, "Longer times affect rankings in search results." But what recommendations are these explanations based on? How much freedom do we have in setting certain time-based goals or a performance budget? And, what is even more interesting than simple numbers, can we be creative with these durations, playing with them to deliver better experiences to our users? These are the main questions we will cover in this article.

As defined earlier, a performance budget is a limit that we set on certain time-related operations of an online system and that we do not allow the system to exceed. Usually, human-to-human conversations involve quite short time intervals between a question being asked and a response being given by the interlocutor. In psychology, we should keep four important spans of time in mind when dealing with short time durations:

![Psychological time durations](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2015/09/05-time-spans-opt-small.png)[17](http://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/)  


> _Psychological time durations (View large version)_

  * **0.1 to 0.2 seconds**  
[Research](http://www.fon.hum.uva.nl/rob/Courses/InformationInSpeech/CDROM/Literature/LOTwinterschool2006/biae.clemson.edu/bpc/bp/Lab/110/reaction.htm#Mean%20Times) points to this interval as the range of the maximum acceptable response time to simulate **instantaneous** behavior -- an interval within which users barely, if at all, notice a delay.[1](http://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/)
  * **0.5 to 1 seconds**  
This is the maximum response time for **immediate** behavior. This interval is usually the response time from an interlocutor in a human-to-human conversation.[2](http://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/) Delays within this interval are noticeable but easily tolerated by most users. During this time, the user must receive an indication that their command (such as their click of a button or link) has been accepted, assuming that the signal was not already sent during the previous interval.
  * **2 to 5 seconds**  
Psychologist [Mihaly Csikszentmihalyi](https://en.wikipedia.org/wiki/Mihaly_Csikszentmihalyi) defines a **flow** or **optimal experience** as a state when people experience concentration, absolute absorption in an activity and deep enjoyment.[3](http://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/)
  * **5 to 10 seconds**  
According to the [National Center for Biotechnology Information at the US National Library of Medicine](http://www.statisticbrain.com/attention-span-statistics/), the average attention span of a human being dropped from 12 seconds in 2000 to 8.25 seconds in 2015. Guess what? That is 1 second less than the attention span of a goldfish! As a simplification -- and to emphasize our superiority to the goldfish -- we consider 10 seconds as the absolute maximum time of a user's **attention span**.[4](http://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/) The user would still be focused on their task but would become easily distracted. This is the time for the system to engage the user in the process; if this is not done, then the user will most probably be lost forever.

Now, if we apply these time definitions to the aforementioned [platform success model](http://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/) suggested by the Blink team, we can translate its emphasis on a 1-second loading time and a 0.1-second response time into more human-to-human language:

  * The loading page should happen **immediately**.
  * Users should get feedback from a given action **instantly**.
![Load pages immediately, and give feedback on any given action instantly.](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2015/09/06-loading-feedback-opt-small.png)[27](http://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/)  


> _Load pages immediately, and give feedback on a given action instantly. (View large version)_

Humans have inner stopwatches that have been tuned well since our cave-dwelling ancestors. Hence, you can safely rely on the time spans above when choosing a performance budget for your next web project. But time on its own is useless unless put into some context. Consider an example. What do you think about in response to the statement, "A process will take 10 seconds to complete." Take your time.

![A process will take 10 seconds to complete](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2015/09/07-process-opt-small.png)[29](http://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/)  


> _"A process will take 10 seconds to complete." (_

Done? I'll bet the first thing you thought was, "What process?" Your brain iterated over possible options based on your life experience, current lines of thinking, mood and so on. Then, once your brain settled on a dominant guess, it evaluated your expectations about that process' duration against the declared 10 seconds.

That being said, most often we don't pick a random time duration on its own, but rather choose time in a certain context. First, the context could be set by our own constraints, such as a **need for performance optimization** in order to meet users' expectation of a human-to-human style of communication. Secondly, the context might also be set by competitors; in this case, we're dealing with a **chase-the-leader** scenario to reach the performance level set by others. We will look at both scenarios below.

Here is a situation that most of us can relate to to some extent. Your customer says that the search function of your website is slow. Your measurements show an average of 5 seconds to render search results. After employing some optimization techniques, you bring it down to 4.5 seconds. Happily (well, as happily as one could possibly be with a 4.5-second rendering time), you send an email to the customer with this information. All you get in return is, "Doesn't look any faster to me." That usually hurts. Let's try to understand why the customer did not notice any difference.

![Sometimes half of a second is just not enough](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2015/09/08-search-optimisation-opt-small.png)[31](http://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/)  


> _Users will not necessarily notice your optimizations, so it is too early for a party. (View large version)_

In 1834, one of the founders of experimental psychology, [Ernst Heinrich Weber](http://www.britannica.com/biography/Ernst-Heinrich-Weber), postulated a law that defines **difference threshold** or a **just noticeable difference** (JND) as the minimum difference in stimulation (weight, light, etc.) that a person can detect most of the time. Later, Weber's student [Gustav Theodor Fechner](http://www.britannica.com/biography/Gustav-Theodor-Fechner) applied the law to the measurement of sensations, setting the basis for the science of [psychophysics](http://www.britannica.com/science/psychophysics). This work by Weber and Fechner is known to us as the **Weber-Fechner Law**. The law is still regarded by many scientists as arguably the most important tool in understanding perception.

Time is not an exception to the Weber-Fechner Law. Practical experiments in psychophysics show that time intervals are prone to a JND of between 7% to 18% on average for shorter periods (with a duration of less than 30 seconds). Based on this, a good rule of thumb is to simplify the Weber-Fechner Law into a **20% rule**. That is, in order for users to barely see a difference in time duration, it has to be changed by a minimum of 20%.

![20% Rule](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2015/09/09-clock-opt-small.png)[36](http://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/)  


> _The Weber-Fechner Law can be simplified into a 20% rule for short time durations. (_

Let's go back to our example of a client noticing no difference in the rendering of search results after our optimizations. Originally, the search results were returned in 5 seconds. Using the 20% rule, we can tell that, for the user to even notice the difference, the new search results should be at least 1 second faster:
    
    
    5 seconds × 0.2 = 1 second

That is why the client simply did not notice the 0.5-second improvement.

We're talking about performance optimization, but this technique works in the opposite direction. If, for example, you are developing a feature that slows down your web page, you could apply the 20% rule to determine whether the performance decrease will be noticed by users at all. Allowing our code to be a bit slower without harming the user experience is called **regression allowance**.

**Note:** When we talk about 20%, we are talking about a "just noticeable" difference. "**Noticeable**" does not mean "**meaningful**." In order for users to appreciate your performance optimization, you should go well beyond this threshold.

But what do you do when a competitor comes to market with significantly better performance for a comparable feature? What if a 20% regression allowance relative to the competitor's time is not even technically approachable for us? In this case, we should at least aim for what G. Moore, in his book _[Dealing with Darwin_](http://www.dealingwithdarwin.com/), calls **neutralization**.

Time neutralization occurs when the time difference between two services is noticeable but does not influence the user's preference of one service over another. In this case, reliability, usability and other **quality**-related factors of the service play a much more significant role. In other words, time neutralization is a good position to be in when you have better services than competitors.

![Chasing the leader might be tough](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2015/09/10-chasing-the-leader-opt-small.png)[39](http://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/)  


> _What to do when your competitors deliver the same functionality but much more quickly? (View large version)_

Again, getting back to our example of search results taking 5 seconds to appear, assume that a competitor comes to the market with a very similar search service: the same functionality, the same results and the same feel. The problem is that their search results are revealed in 2 seconds, not 5. Applying the 20% rule to our 5 seconds would not make sense in this scenario. We're not competing with our own time; rather, we have to match the competitor's. We can make a couple of logical assumptions here:

  1. We cannot decrease the search response time to 2 seconds. (If it were that easy, we probably would have done it already.)
  2. If 2 seconds is out of reach, the next best solution would be to use the 20% rule of regression allowance relative to the competitor's time: 2 seconds + 20% = 2.4 seconds.

At 2.4 seconds, users will not notice any difference between our search results and the competitor's. But if we cannot achieve 2 seconds, then 2.4 seconds is probably also out of reach.

![We can match neither 2 seconds directly, nor a 20% regression allowance of competitors’ time](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2015/09/11-chasing-the-leader-opt-small.png)[41](http://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/)  


> _We can match neither the 2 seconds directly nor a 20% regression allowance of the competitor's time. (_

When comparing two durations (2 and 5 seconds, in our case), we'll find a "magical" psychological threshold between them. Time durations longer than this threshold will be perceived by the user as being closer to 5 seconds. Time durations shorter than that threshold will be perceived as being closer to 2 seconds. Surprisingly, [studies in animal timing](http://www.brown.edu/Research/Timelab/archive/Pdf/2006-03.pdf), particularly those conducted by R. Church, M. MacInnis, P. Guilhardi and others at Brown University, show that this threshold is not simply the average of the two durations. This threshold proved to be predictable and is found at the **geometric mean**, instead of an arithmetical one. Research with human subjects confirm the same finding.

From mathematics, we might remember that the geometric bisection between two numbers can be found using the following formula:
    
    
    √(A × B)

Applying this formula to our numbers, we get:
    
    
    √(2 × 5) ≈ 3.2 seconds

![The threshold of the difference between two times can be found through the geometric mean of the two](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2015/09/12-geometric-mean-opt-small.png)[44](http://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/)  


> _Geometric bisection as an illustration of neutralization (_

For our 2- and 5-second results, 3.2 seconds is the threshold of neutralization. At this point, users will notice a difference, but the difference will be perceived as being unimportant to their choice of service. Factors such as the quality of the service and reliability will play a much more important role, but managing these is beyond the scope of this article.

With this, we finish our basic analysis of objective time. By now, we should have a good understanding of where [some widely adopted industry standards](http://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/), such as page-loading time and the response time for a system, come from. We also have a [guideline for setting a performance budget](http://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/), and we understand how to deal with time when we have to [improve the performance of a website](http://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/) or [match that of a competitor's](http://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/).

But as we have mentioned earlier, another kind of time usually matters much more to users than the kind measured with a stopwatch. Ladies and gentlemen, let's meet in part 2 and talk about the psychological time.

![To be continued…](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2015/09/13-to-be-continued-opt-small.png)[50](http://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/)

> _[To be continued…](https://media-mediatemple.netdna-ssl.com/wp-content/uploads/2015/09/13-to-be-continued-opt.png)_

1 This is the reaction time of the average person to a simple stimulus, such as catching a falling pen or jerking one's hand away from a hot cup. This is probably the most important time we should keep in mind.

2 According to G.A. Miller, [most adults can store five to nine simple items in their short-term memory](http://www.musanim.com/miller1956/). [Research](http://www.ncbi.nlm.nih.gov/pubmed/19649155) -- confirmed by a number of experiments, in particular [the one](http://www.ncbi.nlm.nih.gov/pubmed/19399976) by [M. Greene](http://stanford.edu/~mrgreene/) and [A. Oliva](http://cvcl.mit.edu/audeoliva.html) of MIT -- shows that "the processing of complex natural images and visual object recognition" takes no more than a tenth of a second. This means that short-term memory processing of five to nine items such as this should take about 0.5 to 0.9 seconds. Hence, 1 second is considered to be the maximum time for the user's flow of thought to stay uninterrupted.

3 While optimal experience time fluctuates according to subjective parameters, for most tasks that the average user faces on the web, the time of concentration falls between 2 to 5 seconds. This is why, for some years, we operated with 2 seconds as the optimal page-loading time.

4 Of course, the state of focused attention in general spans far beyond 10 seconds and can reach 20 to 30 minutes. (This long-term attention is called "selective sustained attention.") However, first, this time span is much more exposed to fluctuation due to different uncontrolled circumstances; secondly, not many website owners out there can brag about their website being actively used by the average user for more than a couple of minutes.

_(ah, ml, al)_
