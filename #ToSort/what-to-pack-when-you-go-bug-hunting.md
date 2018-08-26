# What to Pack When You Go Bug Hunting

_Captured: 2018-03-02 at 20:28 from [dzone.com](https://dzone.com/articles/what-to-pack-when-you-go-bug-hunting?edition=365213&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202018-03-02)_

Container Monitoring and Management eBook: [Read about the new realities of containerization.](https://dzone.com/go?i=274432&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fcontainer-monitoring-and-management.html%3Fcid%3DNA-DSP-APM-AEJ-000195-00001663-000000492%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dddc_apmsaas_acquire%26utm_content%3Dna_eb1-container-monitoring-mgmt-articlepreroll%26mrm%3D)

## Bug Hunting

Bug Hunting is common practice for many testing organizations worldwide, yet some test managers wrongly feel they go Hunting when their testers informally play with the application in order to find "border-case defects".

## What Bug Hunts Are, and What They Are Not

![](http://9975-presscdn-0-95.pagely.netdna-cdn.com/wp-content/uploads/2009/05/ladybugs-48641_640-150x150.png)

**Bug Hunts are Informal Testing exercises**; this should not be mistaken as playing with the system without a purpose or objective, nor should it be confused with "[Exploratory Testing](https://www.practitest.com/help/tests/exploratory-tests-et/)" for the following reasons:

  * Bug Hunts need to be conducted as group activities, while Exploratory Testing can be done by a single tester.
  * Bug Hunts are there in order to involve non-testers and find less-conventional bugs. Exploratory Testing is meant to find "regular bugs" and usually involves only testers.
  * Exploratory Testing can be used in all stages of the testing process. Bug Hunts require the system to be stable to be useful.

In order to achieve something (and not waste your time!!) during these Bug Hunts, you need to follow a specific methodology, perform planning and preparation actions, and monitor and control the process throughout its execution.

Even if there is no written book (at least that I am aware) on Bug Hunts, I follow a process that I caught some years ago during one of the STAR conferences.

*Update* - I will be presenting and attending the upcoming [UKStar event this March](https://ukstar.eurostarsoftwaretesting.com/speaker/joel-montvelisky/) (12-13, 2018) if you care to meet and chat "shop" .

### How to Plan a Bug Hunt

I plan Hunts based on _Pair-Testing_ and _Soap Opera Scenarios_, combined as a _tournament_ between teams.

**Pair Testing** is when you take 2 engineers and they work as a team on 1 computer (or environment). The idea comes from [pair programming ](http://qablog.practitest.com/pair-programming-for-testers/)with all its known advantages such as knowledge sharing, brainstorming, and positive pressure from working with a partner. I've had very good results pairing engineers from different teams, especially when taking development engineers and paring them with test engineers, leveraging the advantages and points of view from both sides of the process.

**Soap Opera Scenarios** are relatively short end-to-end scenarios that take the system from beginning to end of a complex operation on a fast (and sometimes exaggerated) chain of events. Working under extreme conditions we are able to find issues that we missed during our controlled scripts and scenarios.

**The Tournament** activity is where the human factor comes into play. You want people to be motivated, and what better motivation for an engineer than a price? I keep track of many statistics like the number of original bugs detected per day, the most serious bug detected, the worst system crash, etc., and give a prize to the pair who exceed on each category (we usually give away t-shirts and in one extreme case we even gave an iPod!). In any case it is not the price but the spirit that makes the difference.

### Rules of Thumb I Give QA Organizations Before They Start Planning Their Bug Hunts:

1\. Make sure you've reached a minimal _application maturity level_; if it is still too easy to detect critical bugs or the system keeps crashing all the time you may be ahead of your time.

2\. Work on testing environments with _real-life data_. Your tests need to be far from sterile in order to simulate a real working environment.

3\. Create a _balanced activity schedule_. I work based on 2-day bug hunts, where each day starts with 4 hours of _Exploratory Testing_ around a specific application area (each team or two working on a different part of the application); and during the second half of the day we run our Soap Opera scenarios, where each team receives a user profile and a list of high-level tasks.

4\. Manage the activity using a _tracking system_. Any [bug tracking system](https://www.practitest.com/product/) will help you keep track of the issues detected by the teams; if possible use a _dashboard_ to make sure all team members are updated on the position of the rest of their peers.

5\. Have a _bug referee_, she will decide whether the findings are real bugs and also stop duplications from been reported and counted.

6\. Create _anticipation_ by having internal teasers and "publicity campaigns" ahead of the activity.

7\. During the hunt generate an _informal atmosphere_ by playing music, giving each team bells to signal whenever they find and report a new bug, bringing pizzas and sodas, and using other out-of-the-ordinary things that will create the feeling of a special occasion.

Bug Hunts are as much about the [right atmosphere](http://qablog.practitest.com/keep-your-mind-open-when-testing/) and state-of-mind as they are about the methodology and scenarios you run. Make sure you and your team have fun and it will surely generate the outputs your expect it to produce or more.

### **About PractiTest**

[Practitest](https://www.practitest.com/) is an end-to-end test management tool, that gives you control of the entire testing process -- from manual testing to automated testing and CI.

Designed for testers by testers, PractiTest can be customized to your team's ever-changing needs.

With fast professional and methodological support, you can make the most of your time and release products quickly and successfully to meet your user's needs.

Take the Chaos Out of Container Monitoring. [View the webcast on-demand!](https://dzone.com/go?i=274433&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcompany%2Fevents%2Fwebcasts%2Fapplication-performance-monitoring-and-management.html%3Fcommid%3D286663%26cid%3DNA-DSP-APM-AEJ-000195-00001663-000000493%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dddc_apmsaas_acquire%26utm_content%3Dna_webcast1-apm-taming-chaos-articlepostroll%26mrm%3D)
