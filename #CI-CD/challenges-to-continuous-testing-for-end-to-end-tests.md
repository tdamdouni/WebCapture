# Challenges to Continuous Testing for End-to-End Tests

_Captured: 2018-03-16 at 13:17 from [dzone.com](https://dzone.com/articles/challenges-to-continuous-testing-for-end-to-end-te?edition=368203&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202018-03-16)_

Container Monitoring and Management eBook: [Read about the new realities of containerization.](https://dzone.com/go?i=274432&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fcontainer-monitoring-and-management.html%3Fcid%3DNA-DSP-APM-AEJ-000195-00001663-000000492%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dddc_apmsaas_acquire%26utm_content%3Dna_eb1-container-monitoring-mgmt-articlepreroll%26mrm%3D)

It's a fact: digital risk is inherent to the world we live in today. Today's businesses must be built for change, and change is not always a good thing! Change many times comes with adverse effects, especially in the enterprise software space, where we have to manage mission-critical business processes that can span multiple applications. Testing is a way to offset these risks. As we continuously change, we've got to continuously test. But like degrees of risk, there are degrees of difficulty when it comes to continuous testing. Consider the different types of tests we see as an application moves through the Software Deliver Life Cycle (SDLC):

![Image title](https://dzone.com/storage/temp/8342596-tyimage1.png)

It is also important to note that end-to-end tests are not just a bunch of unit and functional tests strung together. The scope of what is being tested and the goal of the test are considerably different between functional tests and end-to-end business process tests.

![Image title](https://dzone.com/storage/temp/8342597-tyimage2.png)

Then consider the different types of applications that could be involved in end-to-end business process tests:

![Image title](https://dzone.com/storage/temp/8342598-screenshot-2018-02-08-123225.png)

When we talk about end-to-end business process testing, we're talking about testing just like a user, which by definition means there are going to be hundreds -- if not thousands -- of tests that we have to manage across multiple applications and UIs. Just building automation for an end-to-end test is a challenge. In fact, according to the 2017-18 World Quality Report, only 16 percent of end-to-end business scenarios are executed with test tools.

Which brings up another core challenge when it comes to implementing CI/CD across enterprise applications: transferring the knowledge needed from domain experts to automation specialists can take months. The harder companies try to work around these legacy systems by developing customized surrounding apps, the more the problem is compounded. Customized apps still need to be tested against the supporting business processes. If testing against the supporting business process is still manual, all efficiency gains achieved on the custom development side from the agile process can be lost.

But for now, let's go forward in an imaginary scenario: We've bought a test automation tool like [Worksoft Certify](https://www.worksoft.com/products/worksoft-certify). We've created our end-to-end test automation libraries. Now, we're ready for on-demand continuous test automation, so we can just schedule it. Right? Not exactly.

If you have tried this, you are probably familiar with the following core challenges.

### **Access**

Unlike custom app virtual devtest environments that can be spun up in minutes, tests for systems like SAP need to be run many times in pre-production, where there is limited availability. Automation that acts like a user needs an active user session. This means installing local agents and logging in to remote machines. Then, you need to figure out a way to keep the machine awake for the life of the test and prevent things like Windows updates from interrupting the tests.

### **Orchestration**

You must be able to orchestrate that workflow. The tests often need to be scheduled in sequence, with complex dependencies. It's difficult to manage distributed and diverse testing resources. The ability to just say "Go run these thousand tests and let me know when they're done," without the right solution, is extremely difficult to manage. The testing time, especially in global situations, is often strictly limited or closely scrutinized. In my former life, we had a two-hour testing window that we always had to fit within for a global e-commerce site. You want to minimize that downtime, so that you can maximize your value effectively.

### **Scale**

Then, from a global perspective, we often need to get everything done that I mentioned, in a two-hour window. Not only that, but when I say everything, the scale of everything can be "industrial scale." We can have many, many tests that need to happen very quickly within these windows.

### **Test Data**

Data has to be correlated across the end-to-end test. The business process needs to have the context of the job to be done, positive or negative test, standard orders or out-of-stock orders, etc. Without correlating the data with the business process being validated, the end-to-end test will fail.

In my next blog, I'll talk about how to overcome these core challenges.

Take the Chaos Out of Container Monitoring. [View the webcast on-demand!](https://dzone.com/go?i=274433&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcompany%2Fevents%2Fwebcasts%2Fapplication-performance-monitoring-and-management.html%3Fcommid%3D286663%26cid%3DNA-DSP-APM-AEJ-000195-00001663-000000493%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dddc_apmsaas_acquire%26utm_content%3Dna_webcast1-apm-taming-chaos-articlepostroll%26mrm%3D)

Topics:

test automation ,end to end testing ,agile adoption ,continuous testing ,continous delivery ,performance

Opinions expressed by DZone contributors are their own.
