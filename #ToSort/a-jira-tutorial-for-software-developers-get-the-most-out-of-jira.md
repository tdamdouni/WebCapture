# A JIRA Tutorial for Software Developers: Get The Most out of JIRA

_Captured: 2018-05-13 at 19:16 from [dzone.com](https://dzone.com/articles/a-jira-tutorial-for-software-developers-get-the-mo?edition=376290&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-05-13)_

See why over 50,000 companies trust Jira Software to plan, track, release, and report great software faster than ever before. [Try the #1 software development tool](https://dzone.com/go?i=281431&u=https%3A%2F%2Fwww.atlassian.com%2Fsoftware%2Fjira%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Djira_adexp-psa-exp_global-eng_dzone-pre-post-roll-text%26utm_term%3DTry-the-number-one-software-development) used by agile teams.

Jira can be a developer's best friend!

It's one of the most common applications for managing software projects, but it's not just for project managers. More and more software developers find themselves behind the wheel on a Jira project, but without the tools or knowledge to make it work best. But with this Jira for developers tutorial, I aim to show you how to make Jira a valuable tool for you and the rest of your team. Whether you're having to plan a project yourself as a developer, or just want to know more about how to use Jira better, this tutorial is for you.

## The Truth about JIRA

Jira is designed to be a tool for [agile](https://stackify.com/agile-methodology/) project managers. And most of the official documentation is written with this in mind. But the reality is that people use Jira in a variety of non-agile projects--and many of those people aren't even project managers.

Most developer-targeted Jira documentation is written with the idea that, as a software developer, you'll mainly just want a nice dashboard to look at the issues that someone else assigned to you. Wishful thinking. In many organizations, developers have to at least occasionally plan projects. And even if you aren't planning them yourself, knowing how Jira works can help you consult with your project manager to make the best use of Jira.

And let's be honest. Many organizations don't make the best use of Jira. The first time I used Jira was in a very large enterprise environment. The project managers just opened up a project using the default settings of a template called [Scrum](https://stackify.com/what-is-scrum/).

The problem was that most people on the team had zero familiarity with agile. Terminology like "[stories](https://searchsoftwarequality.techtarget.com/definition/user-story)" and "[epics](https://www.atlassian.com/agile/project-management/epics)" confused them. No one knew what a "Scrum" was.

Jira based its Scrum template on organizing a project into discrete "stories" with a point value indicating the level of effort required. These are then put into "[sprints](https://www.scrum.org/resources/what-is-a-sprint-in-scrum)," which are short periods of work. Unfortunately, none of us really knew how to do any of this properly, so our sprints disintegrated. This made our entire team look bad to upper management and clients.

We made our problem much worse by adding all kinds of fields into our issues. Filing an issue required facing a form with over 20 fields. We thought we were making our project easier to organize, but we were instead just adding layers of complexity.

![if jira has too many fields, it can get pretty ridiculous](https://stackify.com/wp-content/uploads/2018/05/jira-has-too-many-fields.png)

We also tried to create some custom workflows and roles to make everything easier, but we ended up with such high complexity that we'd spend a lot of time just dealing with that and not working on the software we were supposed to be building. The most common email our project manager got was "Help, I accidentally created an issue and I can't delete it!", or "I can't figure out how to move an issue into testing."

## JIRA Done Well

These days, I know better. If I'm creating a project from scratch and mainly leading it myself in an environment where agile knowledge and practice is spotty, I keep it simple. Thank goodness that the latest version of [Jira has a new template called "Agility."](https://confluence.atlassian.com/jirasoftwarecloud/get-started-with-agility-boards-945104903.html) This template is much simpler and contains significant usability improvements.

![the agility template for jira is a new option](https://stackify.com/wp-content/uploads/2018/05/the-agility-template-for-jira-is-a-new-option.png)

In previous versions, adding an issue presented you with a large and unwieldy form with unnecessary fields. Now, you can click to add a task instantly!

![adding tasks to a board is easy with agility projects in Jira](https://stackify.com/wp-content/uploads/2018/05/adding-tasks-to-a-board-is-easy-with-agility-proje.png)

Need to add a "testing" stage? I usually do, for things going through QA. Before this version, you had to configure a workflow. Now you just add a column and drag it where you want it.

![adding a column to an agility board is easy, just click](https://stackify.com/wp-content/uploads/2018/05/adding-a-column-to-an-agility-board-is-easy-just.png)

![naming your column in your Agility Jira board](https://stackify.com/wp-content/uploads/2018/05/naming-your-column-in-your-agility-jira-board.png)

![ordering Jira Agility board columns is just a matter of drag and drop](https://stackify.com/wp-content/uploads/2018/05/ordering-jira-agility-board-columns-is-just-a-matt.png)

If this all seems a bit familiar to you, remember that last year [Atlassian bought Trello](https://www.atlassian.com/blog/announcements/atlassian-plus-trello). So this is pretty much like a Trello board. It's also something that is easy for anyone to understand at a glance.

Another boon is it uses only labels for organization. Previous versions of Jira had a baffling array of options to choose from for organizing things ranging from epics to components. You should only use these when you need them--and usually, that's never.

Now if you're using previous versions of Jira, I am very sorry. Getting a simple project going is frankly just not very easy. I usually start from "Task tracking." This at least has a pretty simple task structure, though adding in a testing stage involves configuring a workflow.

![adding a testing step to the Jira workflow](https://stackify.com/wp-content/uploads/2018/05/adding-a-testing-step-to-the-jira-workflow.png)

Other versions of Jira have the "bug tracking" template, which is also called "basic software development." Unfortunately, it's anything but basic. In this situation, I recommend removing agile-style issue types such as "epic" and "story" unless your team really knows how to do those right.

![removing unneeded issue types can make your Jira project easier to use](https://stackify.com/wp-content/uploads/2018/05/removing-unneeded-issue-types-can-make-your-jira-p.png)

Jira's default fields are also an area I simplify. Most just don't get any use on a no-frills developer-led project.

![Hiding fields in Jira can make issues simpler](https://stackify.com/wp-content/uploads/2018/05/hiding-fields-in-jira-can-make-issues-simpler.png)

If your install of Jira is very very old, you may only have access to one other template besides Scrum, which is Kanban. The name has caused all kinds of confusion. Kanban is a system of workflow optimization that predates even agile, and [Kanban practitioners have never been thrilled by people using Jira and thinking they're doing Kanban.](https://twitter.com/lki_dja/status/677011468164968448) Either way, it's a board similar to the Agility one (though sadly much harder to use). And at least it doesn't assume everything is organized into sprints. I definitely recommend the Kanban template over the Scrum one, if you don't have access to anything else.

### But I Don't Have Admin Access to JIRA!

I've been in this situation too. Here, I just keep it simple. I work with my team to talk about how we'll use the settings we have. We identify and prioritize just a few customizations that we can ask the admin for. And make sure to allocate time for training people who need specific instructions on using Jira, such as QA or contractors.

### Getting the Most out of JIRA

Even if you're not in charge of Jira in any way, it's still a valuable tool that you'll want to get the most out of, whether by integrating it with other software or using it to optimize your software process.

#### Integrating Your Favorite Software

These days, many software products have Jira integrations. My favorite ones are those that allow you to pass data into Jira to create issues. At Stackify, for example, they [use Zendesk](https://stackify.com/5-tools-to-for-successful-customer-app-support/) to create issues in Jira. Also, you can [easily make issues out of things caught by Stackify itself.](https://support.stackify.com/errors-error-details-and-sharing-options/)

Of course, there _is_ software that will create issues automatically, but I recommend first testing these integrations with a test instance of Jira, lest you flood your product with hundreds of erroneously created issues. Someone I know did this--they accidentally had all warnings in software tests turned into issues. Oh and the issues all got emailed to everyone. And it crashed their email server. Hilarious, unless it happens to you.

#### Custom Tracking

Now as I said before, creating too many custom fields can be a problem. But sometimes a custom field really can be a solution. My general rule is to think about the business case for tracking something. Is the time saved by this solution more than the time spent filling in (or even scrolling past) an extra field? It might be worth it. Treat this as a potential cost and measure the results. If it's not working, remove it. For example, [Stackify created a custom field to track which stage in deployment a bug was found](https://stackify.com/measure-defect-escape-rate/). They use this metric to keep costly bugs out of production.

#### Filter with JQL

JQL stands for "Jira Query Language." It's worth knowing a bit about JQL because it allows you to do to pull data from Jira in a very precise way. Jira's [own tutorial](https://confluence.atlassian.com/jiracore/blog/2015/07/search-jira-like-a-boss-with-jql\)) is a great start. I keep a text file with some of my own favorite queries. For example, I can filter for all the items I've sent to testing with this:

Or when I was working on a Scrum project, I could pull out all the issues I'd resolved for a particular sprint and show how important I am:

Here's the way to use these queries--do a search using them, and then see that Jira gives you the option to save the search as a filter. Use the filters to create custom reports.

#### Reports

Good reporting is crucial for showing off your work to managers, clients, and other stakeholders. If you're using a board, that itself is a great tool. But Jira also has great [reporting](https://confluence.atlassian.com/jirasoftwarecloud/reporting-764478415.html) options.

![There are many options for reporting data in Jira](https://stackify.com/wp-content/uploads/2018/05/there-are-many-options-for-reporting-data-in-jira.png)

Newer versions of Jira have a nice dashboard that shows your options with a description. The dashboard displays commonly used options first. I often use created vs. resolved, which shows how much work a team both takes in (those bugs QA filed!) and finishes. You can use the JQL filters to drill down and show very specific data.

### Is JIRA Your Best Friend Now?

While Jira can be overcomplicated and confusing, it's also extremely powerful and flexible. With this knowledge, you can use it to organize projects well, even if you're just using it on a small team without a project manager. Jira also will be a powerful tool to show off your team's work to clients and other stakeholders.

See why over 50,000 companies trust Jira Software to plan, track, release, and report great software faster than ever before. [Try the #1 software development tool](https://dzone.com/go?i=281432&u=https%3A%2F%2Fwww.atlassian.com%2Fsoftware%2Fjira%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Djira_adexp-psa-exp_global-eng_dzone-pre-post-roll-text%26utm_term%3DTry-the-number-one-software-development) used by agile teams.
