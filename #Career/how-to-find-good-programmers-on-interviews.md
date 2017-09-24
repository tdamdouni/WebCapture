# How to Find Good Programmers on Interviews

_Captured: 2017-09-21 at 19:32 from [dzone.com](https://dzone.com/articles/how-to-find-good-programmers-on-interviews?edition=326503&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-09-21)_

[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

When it comes to programming job interviews, the goal is to find the most suitable developer for a job to get done, but the harsh reality is that it's very difficult to judge someone's caliber, experience, and expertise in such a short amount of time.

Most software companies have a process to find good programmers, starting with [phone interviews](http://javarevisited.blogspot.sg/2015/02/50-programmer-phone-interview-questions-answers.html), before advancing to written tests and face-to-face interviews, but it's still difficult to hire the right programmer. The process can help you to filter candidates, but eventually, it will come down to your experience and gut feeling.

As you do more and more interviews, you will know what and what not to ask, and, like many other interviewers in the world, you will develop some of your own tips.

Similarly, I have developed a couple of [tips ](http://javarevisited.blogspot.sg/2015/08/how-to-become-better-interviewer-programming.html#axzz4ruFd0P7a)from my experience which has helped me to differentiate an average programmer from a good programmer.

Today, I would like to share one of such tips with you guys, to see if you agree with my observation and hopefully, I will get a couple of more tips to find qualified programmers.

One of my most successful tips to find good programmers in an interview is **finding gaps in the requirements**.

I have found and learned it over time that good developers have a knack for breaking requirements and finding gaps, considering [non-functional requirements](http://javarevisited.blogspot.sg/2015/01/difference-between-functional-and-nonfunctional-requirements-software-development.html#axzz4ruFd0P7a), which are very important to produce quality software and products.

Though this skill comes with experience, a good developer, even with less experience, has this ability. In this article, I will share my hypothetical interview with two programmers and see what they produced.

## Average Programmer vs Good Programmer

This is a hypothetical interview to demonstrate my advice, but it's very close to a real interview. By the way, you can change the requirement based upon your domain, the candidates' experience, and their domain expertise and job description.

The key is to give a one line requirement to a candidate and compare the quality of the program developed by multiple programmers.

In this scenario, I have used a very general requirement, which doesn't need any domain expertise e.g. finance, healthcare or manufacturing, but requires some [programming experience](http://javarevisited.blogspot.sg/2016/06/top-5-books-for-programming-coding-interviews-best.html#axzz4ruFd0P7a).

**Interviewer: Can you write a script to archive files older than 30 days and which can be run on the 1st day of the month using a cron job?**

The first programmer went straight to coding and produced a script _which does exactly what is in the requirement_. His script can find all the files in the directory provided as input, can create an archive of the same directory with the provided name, and backup date as a suffix. Looks good right? But hold on, something is missing:

1) He **did not exclude archive files created by the script itself**, which means, next month, the archiving script will also include last month's archive and you will have a bigger file, which will keep growing.

If you are not monitoring it, you will only realize this problem when you need to retrieve something from the archive or when you receive an alert that your file system is full.

2) He did not think about two contradicting part in this script, **finding files older than 30 days** and **running it on the 1st of every month**. Since the script's objective here is to back up last month's data, and month can be 28, 29, 30 or 31 days long.

So if you run this script on 1st March, it will not archive any files because all of them are less than 30 days old because February is usually 28 days long.

3) His **script was not removing files after archiving**. Though this was not stated as part of the requirement, it's an implicit requirement, unless the interviewer specifically mentioned not to do so. The whole purpose of archiving is to save space by reducing the [size ](http://www.java67.com/2017/08/how-to-find-large-files-with-size-in-Linux.html)of old files.

These are just some of the examples of missing requirements, but this case is quite common in real-world programming. Most of the users give requirements like this and experienced programmers know that _**"the devil is always in the details."**_ Reading some good books on effective programming and clean code, e.g. "[Effective Java"](http://www.amazon.com/dp/0321356683/?tag=javamysqlanta-20) by Joshua Bloch and "[Clean Code"](http://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882?tag=javamysqlanta-20) by Uncle Bob can certainly help you to develop an attention to detail.

Before doing anything, the first step is to understand the purpose of the script, and then think about what is missing. Just like when you go to the doctor and tell them that you have some problem, he asks a couple of questions to better understand the problem. **You should always ask questions to clear away any doubts**, let the user know what is missing, etc.

As an expert in the area of software development, it's _your responsibility_ to get enough details so that the product meets the user's expectation and can withstand the test of time. I like to ask this kind of question, which is not very domain specific and very general in nature.

This not only gives an opportunity to gauge candidate's expertise on any particular technology, e.g. Perl, [Python](http://www.java67.com/2017/05/top-7-free-python-programming-books-pdf-online-download.html), or Bash script but also their overall thinking process.

Any developer who can think through and find gaps in requirements is going to be an asset for a team.

By the way, like all things, this is not always the case and it's not a hard and fast rule. It's just another indicator, which can potentially help you to find good programmers.

Here are a couple more examples to differentiate between an average programmer and a good programmer.

One of the interesting questions to ask is to have a developer [write code to read a file](http://javarevisited.blogspot.sg/2016/07/10-examples-to-read-text-file-in-java.html#axzz4ruFd0P7a). A good programmer always asks questions about file content, e.g. binary or text. And, if it's text, then how is it encoded? While an average developer just writes the code to read the file.

A good developer will also make sure to [close streams the right way](http://javarevisited.blogspot.sg/2014/10/right-way-to-close-inputstream-file-resource-in-java.html#axzz4ruFd0P7a) and release file descriptors, while an average programmer forgets about that.

Another example is to ask candidates about how to quickly sort any array. Most of them will tell you about the [quicksort algorithm](http://javarevisited.blogspot.sg/2014/08/quicksort-sorting-algorithm-in-java-in-place-example.html), but good developers will ask about the size of the array. Why? Because if the array is small enough, then the fastest way to sort it will be to use an insertion sort. In fact, most of the library methods which are based upon quicksort will usually use an [insertion sort](http://javarevisited.blogspot.sg/2014/12/insertion-sort-algorithm-in-java-to-array-example.html#axzz4ruFd0P7a) for small arrays.

For example, in Java API, the implementation of the Arrays.sort() method sorts small integer arrays of fewer than 286 elements using quicksort and a tiny array of elements less than 47 using [Insertion sort](http://java67.blogspot.sg/2014/09/insertion-sort-in-java-with-example.html).

By the way, this is another reason to follow Joshua Bloch's advice, i.e. **[always use library methods if available](http://www.amazon.com/dp/0321356683/?tag=javamysqlanta-20)**. You will never get this kind of optimization right in a short duration of writing your library, forget about all the testing users have done on an open source library.

That's all about this **tip to differentiate an average programmer from a good programmer**. As I said, this is just one of several points many interviewers look at. For programmers, it's an opportunity to show their ability to think through problems, and how good they are at understanding requirements and finding gaps.

This tip has helped me in the past, but it's not a hard and fast rule to find good developers. In fact, there is no rule to find them. You just have to work through some indicator and your gut feeling. Let me know what tips you guys are using to find good programmers on interviews.

Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
