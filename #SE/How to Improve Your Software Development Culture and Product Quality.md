# How to Improve Your Software Development Culture and Product Quality

_Captured: 2016-12-19 at 23:32 from [www.business2community.com](http://www.business2community.com/strategy/improve-software-development-culture-product-quality-01730187?utm_source=feedburner&utm_medium=twitter&utm_campaign=Feed%3A+B2CMarketingInsider+%28Business+2+Community%29#p32YFMWTTgAmEiF0.97)_

![software-development-culture](http://cdn2.business2community.com/wp-content/uploads/2016/12/Software-Development-Culture.png-900x450.png)

Aside from the raw product you're selling, company culture is [everything](https://www.thebalance.com/what-is-company-culture-2062000).

It's made up of your **work environment, ethics, mission, expectations, and goals**. You can have a great product, but without a solid culture to back it up, its development can fall apart.

Buffer, for example, has a notable culture of transparency. All employee salaries are [published](https://open.buffer.com/introducing-open-salaries-at-buffer-including-our-transparent-formula-and-all-individual-salaries/) for co-workers and the public to see. They emphasize [working out loud](https://technkl.com/work-loud-dont-just-share/) and [being receptive](https://open.buffer.com/receptivity/) to one another.

On the other hand, Amazon is[ noted for its toxic culture](http://www.nytimes.com/2015/08/16/technology/inside-amazon-wrestling-big-ideas-in-a-bruising-workplace.html?_r=0) that exhausts employees and holds "unreasonably high" expectations.

Which side of the spectrum are you on?

In software companies, it's important to promote a culture of communication and transparency. What would an issue tracking system look like for a company with poor culture? Pretty desolate.

In this article, I'm going to give examples of how different software companies bolster their QA efforts with a strong culture, and why that's so important.

## A culture of transparency

Transparency can mean a few different things, from being transparent to the public, to making all information available to every member of the team. For the purposes of software QA, I'll focus on the latter.

> "transparency is about making obvious: the reasons we are doing the work, the way we are doing the work, the quality of the work and functionality of the work."

Transparency helps teams make good decisions based on the activity of other members. How can you know when a feature will be ready if the developer working on it is keeping their progress a secret?

![](http://cdn.business2community.com/wp-content/uploads/2016/12/transparency-value-1024x715.png-900x629.png)

Buffer's company culture guidelines for transparency

The main reason to be transparent in your software team is to reduce the risk of error. With all logs out in the open, there's a clear insight into who's doing what, and this helps other members jump into help and spot mistakes before they make it into production.

## How to build transparency into your software team

[John Piekos](https://twitter.com/jpiekos), VP of Engineering at [VoltDB](https://www.voltdb.com/), [says](http://agilemakingprogress.blogspot.com/2011/03/transparency-keep-it-visible.html) the best way to start building transparency is to hold daily agile standup meetings, and to:

> "make a list of work you are doing, order it according to priority, and discuss the list with your manager. In particular, I suggest that they work with their manager to help set the right priority of the various work items. This conversation often opens the eyes of both the manager and the employee, quickly addressing the tension and frustration experienced by both parties."

However, as [Philip Arkcoll](https://twitter.com/parkcoll) at [Workalytics](http://www.worklytics.co/) points out, [it's not human nature to be transparent](http://www.worklytics.co/blog/creating-a-culture-of-transparency-on-software-development-teams/). It's a learned behavior. It's something managers can teach their teams by being transparent and open about their own work, sharing news from the company, and making it mandatory to post regular updates on work, whether that's through group Slack channels, Trello comments or JIRA issues.

A great place to start is with daily standup meetings, where you ask each team member three questions:

  * What did you do yesterday?
  * What are you working on today?
  * Is there anything you need help with?

You can use a checklist like the one below to track standup meetings:

I have regular meetings with the marketing team here at Process Street where we are open with each other about what we're working on, our next steps, and any problems holding us back. After the meetings, I feel motivated to start work because I'm 100% clear on what I need to do, and any obstacles have been addressed.

Open-source software giant [Ubuntu](https://www.ubuntu.com/) is a [great example of transparency](http://www.theserverside.com/feature/Collaboration-and-transparency-as-the-key-to-successful-application-development). Since the software is open source, everything is transparent for the general public and the team itself. Internally, the company uses open source values as part of its management structure and culture policy:

> "The way in which we build Ubuntu is that we **identify what we want to do, we write everything down and we assign work items**. And then we execute on that work in a predictable manner until we get to our deadlines and we hit them. […] You want to** make sure your senior management understands what's going on**. And you want to make sure that your engineers are very clear, at the detail level, about what they need to do as well." -- [Jono Bacon](http://www.jonobacon.org/about/), Leader in Community Management/Strategy, Ubuntu

As well as transparency, ownership is an important part of QA culture.

## A culture of ownership

As I looked at in [my previous article](https://www.process.st/software-testing-methods/) about Google's company culture, ownership is one element of a strong company culture that helps reduce software errors.

The way Google does it is to [make all developers responsible](https://www.infoq.com/news/2011/03/Ensuring-Product-Quality-Google) for writing tests for the code they submit for review. Nothing will be reviewed without tests. This means that QA/QC isn't an abstract department that gets burdened with appalling code then blamed for errors -- it's **a responsibility for the whole team**.

> "Quality is a development issue, not a testing issue. To the extent that we are able to embed testing practice inside development, we have created a process that is hyper incremental where mistakes can be rolled back if any one increment turns out to be too buggy" -- James Whittaker, Director of Test Engineering, Google

Google found that this tactic -- combined with daily updates on per-commit tests --[ improved code coverage by 10%](https://testing.googleblog.com/2014/07/measuring-coverage-at-google.html) over their 2 billion lines of code.

When talking about ownership on this level, it's important not to overlook transparency: if one developer owns and controls the code from a particular module, this [creates artificial barriers and dependencies](http://swreflections.blogspot.com/2013/04/code-ownership-who-should-own-code.html). Similarly, if multiple developers own the code, it can become messy and inconsistent.

![mission-culture](http://cdn.business2community.com/wp-content/uploads/2016/12/mission-culture.jpg.jpg)

[Research by Microsoft](https://www.microsoft.com/en-us/research/publication/dont-touch-my-code-examining-the-effects-of-ownership-on-software-quality/) found that throughout the development of Windows XP and Windows 7, the more developers that touch the code, the lower the quality.

As a result, they made a number of policy changes that you can read about in detail in [this report](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/bird2011dtm.pdf). To summarize, the changes they made are:

  * Changes made by minor contributors should be reviewed with more scrutiny
  * Potential minor contributors should communicate desired changes to developers experienced with the respective binary
  * Components with low ownership should be given priority by QA resources

In short, **when ownership is diluted amongst several developers, quality standards fall.** This doesn't mean code can never be a collaborative effort, but **communication is vital to avoid errors**.

## How to build a culture of ownership

The roots of ownership lie in **making smart hiring decisions**.

[According to Geneca CEO Joel Basgall](https://www.entrepreneur.com/article/237896), ownership is starkly different from accountability:

> Ownership isn't assigned or given. Ownership is taken. I can't appoint ownership. It happens when an employee comes forward and says, "I'm going to make this happen. Here's what I will do. Here's what I will accomplish. And here's how I will measure progress." Ownership means saying, "You will" is unnecessary because the employee has already said, "I will."

Joel believes a culture of ownership is built by hiring the right people. Early hires are the most important, because they will often graduate to management roles and set the tone. By hiring owners -- people who are eager to take responsibility for the company's future -- culture can take care of itself.

With hiring as the basis, Management Education has a few tips to [help promote a culture of ownership](http://managementeducationgroup.com/2013/08/be-clear-create-an-ownership-culture/):

  * Share big-picture and organizational plans early and often.
  * Enlist employee participation in goal setting for the work unit.
  * Conduct regular "keep interviews"-conversations about what will keep the employee motivated, engaged, and retained.
  * Give employees ample opportunity to own their assigned projects and progress.
  * Communicate reasonable expectations and check with employees to make sure they are clear on those expectations.
  * Give frequent and immediate feedback so employees know when they are meeting your expectations.
  * Give specific and timely feedback when employees are not meeting your expectations.
  * Ask employees to make recommendations for addressing ongoing organizational challenges.
  * Seek customer feedback and share it directly with employees in a timely manner.
  * Break away from micromanaging. Set expectations and allow space for employees to learn. Learn to let go.
  * Create a reward system to reinforce ownership behavior.

## Your next steps

Improving transparency and ownership isn't something that happens overnight. Unlike revenue or conversion rate, you can't measure it in percentile points.

What you can do, however, is start implementing the advice in this article and see these tangible metrics improving.

As Philip Arkcoll recommends, start with standup meetings. Review your policies on code quality, and make it mandatory for developers to regularly update each other on their progress by commenting inside whichever issue tracker / project management tool you use.

Imagine the alternative: software full of bugs, oblivious team members, and developers not caring about the quality of their work. That certainly seems worse.
