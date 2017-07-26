# Application Modernization/Migration: What, Why, When, and How?

_Captured: 2017-03-08 at 01:04 from [dzone.com](https://dzone.com/articles/application-modernizationmigration-what-why-when-and-how?edition=276883&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-07)_

[Bitbucket](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) is for the code that takes us to Mars, decodes the human genome, or drives your next car. What will your code do? [Get started with Bitbucket today, it's free.](https://dzone.com/go?i=186132&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-code-that-takes-us-to-mars%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)

I have been working on modernizing and migrating several different types of Java/JEE applications (yes, I mean 'different' types) over the last few years and wanted to share my experiences in the hopes that it might help someone out there trying to do the same. I plan to write a series of articles, so please watch this space for more.

The technology landscape is ever-changing, and business applications almost always have a hard time keeping up with it due to various limitations. Application modernization is an area of technology consulting that is catching up so fast that several large consulting organizations have realized the need to create a separate consulting practice with qualified staff to be able to meet the growing demand to migrate applications to newer technology platforms.

Throughout this and future articles, I'll refer the legacy applications as SOURCE and modernized applications as TARGET.

Production-quality Java (EE) applications can vary at several levels, with some of them listed here:

  * Size of the application (small, medium, or large based on few factors like LOC, number of users, etc.)
  * Type of application (intranet/Internet/thin client/desktop/thick client)
  * Quality and maturity of Java code
  * Complexity in terms of functionality
  * Technology stack they were built on
  * Complexity of the infrastructure they were deployed on.
  * The sustainment process used to maintain them
  * The change management process used to track/manage changes
  * The mindset of the management (both delivery and customer organizations) responsible for these applications
  * The release management process employed with the application
  * Quality of testing, with a great emphasis on performance/load testing

"Some" of the challenges you may face during this process:

  * Lack of knowledge or know-how of the SOURCE application (especially if it is an application built using technologies from a couple of decades ago)
  * Lack of 'up-to-date' technical and business documentation of SOURCE
  * 'Retrofitting' the legacy architecture to the target architecture of the application, keeping changes to the applications to minimum - users don't like changes, especially when they are made due to the need to modernize the technology stack of an application!
  * Matching or exceeding the performance levels of the SOURCE application with the TARGET application
  * If the SOURCE application has business functions managed by several different business groups internal and external to the organization, identifying all relevant stakeholders and educating them about the need for the TARGET application is a huge challenge, especially when the application is working 'fine.'
  * Classloading issues in the TARGET application environment
  * JNDI naming issues between app servers in SOURCE and TARGET environments
  * Incompatible application packaging issues between SOURCE and TARGET environments
  * Incompatible build and deployment processes SOURCE and TARGET environments

For any modernization effort to be successful, the 3 Ps should be taken into consideration (borrowing from Marcus Lemonis from CNBC's "The Profit" show):

  * **People**: Identify the relevant stakeholders of the SOURCE and TARGET applications. Identify the 'right' teams to do the job!!

  * **Product**: Identify the state the TARGET application needs to be in, making sure there are no functional gaps compared to SOURCE application

  * **Process**: The process to build the TARGET application is extremely important. Modernization projects are almost always going to change the 'running' production applications, and you are sure to hear a lot of voices saying 'DO NOT' try to change this or that! There is a fear factor involved that the process needs to overcome! So, lay out the process to the stakeholders (People,) before you do anything!

In the next article, I will try to suggest some processes/frameworks from my experience that will help these types of efforts.

[Bitbucket is the Git solution](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text) for professional teams who code with a purpose, not just as a hobby. [Get started today, it's free.](https://dzone.com/go?i=186133&u=https%3A%2F%2Fbitbucket.org%2Fproduct%3Futm_source%3Ddzone%26utm_medium%3Dpaid-content%26utm_content%3Dtext-teams-who-code-with-a-purpose%26utm_campaign%3Dbitbucket_adexp-bbtofu_dzone-text)

Opinions expressed by DZone contributors are their own.
