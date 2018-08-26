# How to Improve Your Continuous Testing While Balancing Velocity, Coverage, and UX Risk

_Captured: 2018-04-27 at 15:54 from [dzone.com](https://dzone.com/articles/how-to-improve-your-continuous-testing-while-balan?edition=376213&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-04-27)_

[Discover the easy-to-use control panel and API](https://dzone.com/go?i=286445&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F417595668%3B219047635%3Bx) that let you spend more time coding and less time managing your infrastructure. Brought to you in partnership with [DigitalOcean](https://dzone.com/go?i=286445&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F417595668%3B219047635%3Bx)

## A Stage-Based Methodology

Continuous testing is one of the keys to the DevOps kingdom. Your pipeline needs to move fast to keep up with ever-shrinking release schedules but you can't afford to sacrifice quality or UX in the name of speed. The solution? During each stage of development, Development teams need to balance testing _every scenario _against the amount of time needed to generate meaningful test results. However, it's understood that a "test everything" approach isn't practical; therefore, you're left with a balancing act for teams to negotiate. This blog focuses on a continuous testing methodology to determine which devices to test at each stage of development. The highest-performing teams are the ones whose game plans match target platforms with each development stage; this stage-specific testing strategy is fundamental to meeting your fast feedback needs while ensuring a great UX.

### Breaking Down the DevOps Team Processes by Stage

  * **Unit Testing**
    * Developers execute unit tests to get fast feedback - _"does the code I just wrote behave as expected? Is it ready for integration and more rigorous testing?"_ Maximizing platform coverage in this stage is inefficient and unnecessary. In this early stage of development, unit tests executed before or after a commit often use [emulators and simulators](http://blog.perfecto.io/mobile-application-testing/mobile-testing-the-balance-between-real-devices-and-emulators/) to provide a quick thumbs up or down on whether the code works. In later test phases, most top teams agree that moving to real devices is required to assure user experience.
  * **Acceptance Testing**
    * Teams typically focus on verifying that new functionality- as well as old- works according to the user story, and tests are executed over a large set of platforms that mirrors realistic customer patterns.
  * **Test in Production**
    * Many teams adopt DevOps; testing in production becomes part of the continuous testing scope. Once code ships, the objective changes from "does it work" to "is it still working as expected?" Teams recognize the value of leveraging hourly testing of key flows to create an early warning mechanism. Early awareness of production issues jump starts resolution efforts while (hopefully) few users are negatively impacted.

## Factors: Your Coverage Crib Sheet for Continuous Testing

We've established that it's important to know which platforms to test against, in which environments, and when to execute, in order to streamline the continuous testing process. Everyone involved in the product release should understand both the testing trigger points that must be defined in each stage and how their tests fit into the overall pipeline in order to meet project schedules and reduce UX risk. Perfecto's Factors reference guide gives you a head start with guidelines for determining which platforms you need to cover and how to fit them into your DevOps process. The table below summarizes the Perfecto's research.

Our methodology:

  * **Unit testing should be executed by devs on a small subset of platforms that may include emulators and simulators and should be triggered pre- and post-commit locally against the developer workstation.**
  * **Build acceptance tests** should be executed on a larger number of platforms (real devices and web platforms) daily and as part of the continuous integration (CI) process.
  * **Acceptance tests** should be executed on the full set of platforms in the lab to get maximum coverage and quality visibility. These cycles should run on a nightly basis, orchestrated by the CI process.
  * **Production testing should run hourly and continuously** to detect regression defects, outages, or performance degradations in the service. Such tests should not focus on maximum coverage of platforms; select the top 2-3 platforms from the web and mobile and execute against these.
![Image title](https://dzone.com/storage/temp/8787804-screen-shot-2018-04-11-at-55031-pm.png)

[Learn about the optimized the configuration process](https://dzone.com/go?i=286446&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F417595650%3B219047638%3Br) to save your team time when running and scaling distributed applications, AI & machine learning workloads, hosted services, client websites, or CI/CD environments. Brought to you in partnership with [DigitalOcean](https://dzone.com/go?i=286446&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F417595650%3B219047638%3Br)
