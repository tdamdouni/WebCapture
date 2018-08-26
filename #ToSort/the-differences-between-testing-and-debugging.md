# The Differences Between Testing and Debugging

_Captured: 2018-04-11 at 16:41 from [dzone.com](https://dzone.com/articles/the-differences-between-testing-and-debugging?edition=372193&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-04-11)_

[Download the blueprint](https://dzone.com/go?i=228233&u=https%3A%2F%2Foffers.automic.com%2Fblueprint-to-continuous-delivery-with-automic-release-automation%3Futm_campaign%3DAMER%252520Online%252520Syndication%252520DZone%252520Platinum%252520Sponsorship%252520Ads%252520JULY-2017%26utm_source%3DDzone%252520Ads%26utm_medium%3DBlueprint%252520to%252520CD) that can take a company of any maturity level all the way up to enterprise-scale continuous delivery using a combination of Automic Release Automation, Automic's 20+ years of business automation experience, and the proven tools and practices the company is already leveraging.

When it comes to software testing, the battle between tester and developer is never-ending due to the different approaches to perfect product definition. Testing and debugging become the "weapons" that are used in that endless battle. But in fact, these terms are usually mistaken to be the same.

![The Differences Between Testing and Debugging](https://i1.wp.com/testautomationresources.com/wp-content/uploads/2018/04/Devlopers-Vs-Testers-01.png?w=1455&ssl=1)

In order to provide you a deeper view of the distinctions between them, in this article, we will be talking about the differences between testing and debugging and some tips that can help you get eager to debug more effectively.

## **1\. The Differences Between Testing and Debugging**

### **What Is Testing?**

Basically, testing is a process of exploring the system to find defects present in the software, and not only that, this process has to locate the defects and define what will happen once these defects occur. This process is performed in the testing phase by testing team, and after this phase, they will report to the developer team to debug.

Some popular testing tools: [Selenium](https://docs.seleniumhq.org/), [Katalon Studio](https://www.katalon.com/), [TestComplete](https://smartbear.com/product/testcomplete/overview/)…

### **What Is Debugging?**

Once Development team received the report from the testing team, they will start debugging. The purpose of this phase is to locate the bug and rids the software of it. It is a one-off process and is done manually. In this process, a special tool called debugger is used in locating the bugs, most of the programming environments have the debugger.

Some popular Debugger tools: [WinDbg](https://docs.microsoft.com/en-us/windows-hardware/drivers/debugger/debugger-download-tools), [OllyDbg](https://en.wikipedia.org/wiki/OllyDbg), [IDA Pro,](https://www.hex-rays.com/products/ida/)…

**Testing**
**Debugging**

Performed by testers
Performed by developer or development team

Can be done manually or automatically
Can only be done manually

Can be predefined when starting testing. The test result could be predicted
Start with unknown conditions and it is hard to predict the result

Find the programming failure
Demonstrate that it's only an unattended small mistake

Could be done automatically by using automated testing tools
Automatic debugging of software is still a dream of programmers

The purpose is to find the bug
The purpose is to find the cause of a bug
![The Differences Between Testing and Debugging](https://i1.wp.com/testautomationresources.com/wp-content/uploads/2018/04/Testing-debugging-workflow.png?w=564&ssl=1)

> _Typical testing and debugging workflow._

## **2\. 5 Tips to Make Your Debugging Process More Effective**

  * ### **Prioritize the Bug**

The first thing you have to take into consideration when debugging is the user experience. In detail, if your software has poor performing, then your user will leave you. Prioritizing the bug helps you know how much the bug affects on your user and determine which bug to fix first. If can use a risk assessment matrix to prioritize the bug.

  * ### **Reproduce the Bug**

Make sure that you have reproduced the original bug before making any changes. If you don't reproduce the bug and proceed to make changes, it will take up a lot of your time if someone re-opens a ticket because the bug hasn't been removed yet. You won't remember what you have done before. So, make sure to reproduce the original bug and in case you can't reproduce it, then ask someone who can.

  * ### **Do Not Assume Things Work the Way They Are Meant To**

A certain amount of paranoia is required when bug-fixing. Clearly something doesn't work as it's meant to, otherwise, you wouldn't be facing a problem. Be open-minded about where the problem may be - while still bearing in mind what you know of the systems involved. It's unlikely (but possible) that you'll find that the cause of the problem is a commonly-used system class - if it looks like System. If String is misbehaving, you should test your assumptions carefully against the documentation before claiming to have found a definite bug, but there's always a possibility of the problem being external.

  * ### **Know the Error Code**

Knowing the HTTP error code will give you a big advantage in diagnosing bugs, for example:

  * 404 - You might have the wrong URL in your app
  * 401 - Your credentials are likely wrong
  * 418 - You're talking to a teapot!
  * 429 - You're making too many requests

If you get an HTTP error code, always Google it to make sure you understand it. Again, it'll save you a lot of time! The same goes for Database drivers and other protocols, search the error with the name of the database and look for the official docs.

  * ### **If Completely "Stuck," Ask Someone for Help!**

If you have no idea to solve the problem you are facing and feeling very demoralized, here are some workarounds:

  * Take a break, approach the bug from a different angle.
  * Get more aggressive with tracing and logging.
  * Search engines, Forums,… are the powerful ways that you can find the answer for your problems from peers, communities and even professionals. Give them as much information as possible, they will help you figure it out.
  * Destroy something (just for stress relief!)

## **Conclusion**

By the end of the day, both testing and debugging exist for the only one reason that is to make the product better and better. No matter which team you are belonging to (the testing team or debugging team), you are all happy when getting the positive feedback for the improvements of product and it is also the time when the battle is paused.

Thank you for reading and happy testing!

[Download](https://dzone.com/go?i=228234&u=https%3A%2F%2Foffers.automic.com%2Fblueprint-to-continuous-delivery-with-automic-release-automation%3Futm_campaign%3DAMER%252520Online%252520Syndication%252520DZone%252520Platinum%252520Sponsorship%252520Ads%252520JULY-2017%26utm_source%3DDzone%252520Ads%26utm_medium%3DBlueprint%252520to%252520CD) the 'Practical Blueprint to Continuous Delivery' to learn how Automic Release Automation can help you begin or continue your company's digital transformation.
