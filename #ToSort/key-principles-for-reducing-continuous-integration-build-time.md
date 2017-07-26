# Key Principles for Reducing Continuous Integration Build Time

_Captured: 2017-03-22 at 21:58 from [blogs.agilefaqs.com](http://blogs.agilefaqs.com/2014/10/03/key-principles-for-reducing-continuous-integration-build-time/?utm_content=buffer840ae&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Many teams suffer daily due to slow [CI builds](http://blogs.agilefaqs.com/2006/06/21/continuous-integration-mumbo-jumbo/). The teams certainly realise the pain, but don't necessarily take any corrective action. The most common excuse is we don't have time or we don't think it can get better than this.

![Waiting for the build](http://blogs.agilefaqs.com/wp-content/uploads/2014/10/Waiting-for-the-build.png)

Following are some key principles, I've used when confronted with long running builds:

  * **Focus on the Bottlenecks** - Profile your builds to find the real culprits. Fixing them will help the most. IMHE I've seen the 80-20 rule apply here. Fixing 20% of the bottlenecks will give you 80% gain in speed.
  * **Divide and Conquer** - Turn large monolithic builds into smaller, more focused builds. This would typically lead to restructuring your project into smaller modules or projects, which is a good version control practice anyway. Also most CI servers support a build pipeline, which will help you hookup all these smaller builds together.
  * **Turn Sequential Tasks to Parallel Tasks** - By breaking your builds into smaller builds, you can now run them in parallel. You can also distribute the tasks across multiple slave machines. Also consider running your tests in parallel. Many static analysis tools can run in parallel.
  * **Reuse** - Don't create/start from scratch if you can avoid it. For ex: have pre-compiled code (jars) for dependent code instead of building it every time, esp. if it rarely changes. Set up your target env as a VM and keep it ready. Use a database dump for your seed data, instead of building it from an empty DB every time. Many times we use incremental compile/build, instead of clean builds.
  * **Avoid/Minimise IO** (Disk & Network) - IOs can be a huge bottleneck. Turn down logging when running your builds. Preference using an in-process & in-memory DB, consider tmpfs for in-memory file system.
  * **Fail Fast** - We want our builds to give us fast feedback. Hence its very important to prioritise your build tasks based on what is most likely to fail first. In fact long back we had started a project called [ProTest](http://sourceforge.net/projects/protest/), which helps you prioritise your tests on which test is most likely to fail. 
    * Push unnecessary stuff to a separate build - Things like JavaDocs can be done nightly
  * **Once and Only Once** - avoid unnecessary duplication in steps. For ex: copying src files or jars to another location, creating a new Jenkins workspace every build, empty DB creation, etc.
  * **Reduce Noise** - remove unnecessary data and file. Work on a minimal, yet apt set. Turn down logging levels.
  * **Time is Money** -I guess I'm stating the obvious. But using newer, faster tools is actually cheaper. Moving from CVS/SVN to Git can speed up your build, newer testing frameworks are faster. Also Hardware is getting cheaper day by day, while developer's cost is going up day by day. Invest in good hardware like SSD, Faster Multi-core CPUs, better RAM, etc. It would be way cheaper than your team waiting for the builds.
  * **Profile, Understand and Configure** - Ignorance can be fatal. When it comes to build, you must profile your build to find the bottleneck. Go deeper to understand what is going on. And then based on data, configure your environment. For ex: setting the right OS parameters, set the right compiler flags can make a noticeable difference.
  * **Keep an Open Mind** - Many times, you will find the real culprits might be some totally unrelated part of your environment. Many times we also find poorly written code which can slow things down. One needs to keep an open mind.

Are there any other principles you've used?

BTW [Ashish](http://ashishparkhi.com/about/) and I plan to present [this topic](http://confengine.com/agile-pune-2014/proposal/458/techniques-to-speed-up-your-build-pipeline-for-faster-feedback) at the upcoming [Agile Pune 2014 Conference](http://pune.agileindia.org/). Would love to see you there.

  1. [Continuous Integration ](http://blogs.agilefaqs.com/2006/06/21/continuous-integration-mumbo-jumbo/) What is the purpose of Continuous Integration (CI)? To avoid last minute integration surprises. CI tries to break the integration...
  2. [Impact of Continuous Integration on Team Culture ](http://blogs.agilefaqs.com/2011/04/17/impact-of-continuous-integration-on-team-culture/) Better productivity and collaboration via improved feedback and high-quality information. Impact of Continuous Integration on Team Culture: Encourages an Evolutionary Design...
  3. [Running Unit Tests in Parallel ](http://blogs.agilefaqs.com/2007/03/25/running-unit-tests-in-parallel/) Quicker feedback is more important than ever when it comes to developer testing. More and more developers are switching to...
  4. [Key Attributes of a Metrics ](http://blogs.agilefaqs.com/2009/06/09/key-attributes-of-a-metrics/) A good metrics: Guides/Drives me. When I look at it, I know what to do (how to react to the data...
  5. [Continuous Deployment Demystified - Agile India 2012 Proposal ](http://blogs.agilefaqs.com/2011/11/01/continuous-deployment-demystified-agile-india-2012-proposal/) "Release Early, Release Often" is a proven mantra, but what happens when you push this practice to it's limits? .i.e....
  6. [OO Design Principles ](http://blogs.agilefaqs.com/2012/06/07/oo-design-principles/) Following Object Oriented Design Principles have really helped me designing my code: Single Responsibility Principle Open Closed Principle Liskov Substitution...
  7. [I'm not Attacking the Agile Manifesto Principles, I'm begging for Improvement ](http://blogs.agilefaqs.com/2010/03/19/im-not-attacking-the-agile-manifesto-principles-i-begging-for-improvement/) In 2001, following were a great set of principles for a Software Development team. Our highest priority is to satisfy...
  8. [Stay away from Design Patterns; master Value, Principles and Basics Skills first ](http://blogs.agilefaqs.com/2012/06/07/stay-away-from-design-patterns-master-value-principles-and-basics-skills-first/) Unfortunately many developers think they already know enough values and principles, so its not worth spending anytime learning or practicing...
