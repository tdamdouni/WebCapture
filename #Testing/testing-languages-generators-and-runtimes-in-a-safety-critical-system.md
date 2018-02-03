# Testing Languages, Generators and Runtimes in a Safety-Critical System

_Captured: 2018-02-01 at 09:52 from [blogs.itemis.com](https://blogs.itemis.com/en/testing-languages-generators-and-runtimes-in-a-safety-critical-system?utm_source=hs_email&utm_medium=email&utm_content=60339995&_hsenc=p2ANqtz-9_sCug88NcG1SXduu9_LNoHNdJUWzVutSPRNbRypPFX5T944qeL14PTg_0IOlaRYN8Sunh6oWsm7nrJe593PClFegjww&_hsmi=60339488)_

Last year we ran a project with [Voluntis](http://www.voluntis.com/) in which we built DSLs for use in the healthcare domain. The benefits of the approach are readily obvious: the domain experts can much more easily review, test, explore, or even write the application logic. The overall development process will be streamlined, and ultimately, Voluntis will be able to create more products in a shorter time, which is good for business.

Unfortunately, the potential problem is also readily obvious: what good are nicely correct models, if the final application - the code that actually runs on the target device - cannot be guaranteed to be correct relative to the logic expressed in the model? Of course, preventing errors in code generators is important in any DSL-based project. But here, with patients at risk, it becomes especially critical.

So, as part of the project, we spent significant effort assuring the correctness of everything downstream from the model. We wrote a detailed paper about this, which is currently under review. I am also in the process of preparing a short talk for a software conference, and the video below is a dry run of that talk to find out how long it will take me to present the talk (21 minutes, it turns out).

So, until we can publish the paper, you might want to check out this talk to get an idea of how we went about assuring the correctness of languages, generators, and runtimes for a safety-critical system.
