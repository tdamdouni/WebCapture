# MythBusters: Functional Testing Edition

_Captured: 2018-03-27 at 20:35 from [dzone.com](https://dzone.com/articles/mythbusters-functional-testing-edition?edition=370191&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-03-27)_

Container Monitoring and Management eBook: [Read about the new realities of containerization.](https://dzone.com/go?i=274432&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB20689163.213735481%3Bdc_trk_aid%3D412847894%3Bdc_trk_cid%3D97535502%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D)

![](https://blog.smartbear.com/wp-content/uploads/2018/03/Blog-Mythbusters-01.png)

The other day I was looking for more information on functional testing, so of course I went to the go-to spot for testers and developers to ask their questions--Stack Overflow. Crawling through [the posts](https://stackoverflow.com/questions/tagged/functional-testing) that were tagged with "functional testing," I noticed there was a lot of confusion around this subject including some questions I had.

The next step seemed obvious to me--embrace my inner [Adam & Jamie](https://www.youtube.com/watch?v=wOS5VGkRPJk) to bust some myths around functional testing.

### **Myth 1: Functional Testing and End-to-End Testing are the Same Thing. **

Functional testing and end-to-end testing are not the same thing. [Functional testing](https://www.guru99.com/functional-testing.html) looks to make sure that each function of an application is in conformance with specified requirements.

[End-to-end testing](https://www.techopedia.com/definition/7035/end-to-end-test) is a testing methodology used to test whether the flow of an application is performing as intended from start to finish.

So, what's the difference? First of all, functional testing should be conducted before end-to-end testing. The point of end-to-end testing is to simulate a real user experience. With end-to-end testing you are required to have built out all components of an application that have a dependency including real databases, networks, third party systems, etc.

With functional testing, you can use in-memory implementations of your application to check whether the functionality meets the requirements.

### Myth 2: System Testing Is a Component of Functional Testing.

This myth is backwards--in fact, functional testing is a component of system testing. System testing is the testing of a fully integrated software product. It is a type of black box test which is completed to verify:

  * End-to-end testing scenarios 
  * User's experience with an application 
  * Fully integrated applications 

There are over 50 types of system testing which range from functional testing to hardware/software testing and usability testing. Functional testing does not incorporate the other types of testing such as load testing and regression testing that is included for system testing. This is why it's important to start with functional testing where you start testing for functional completeness before moving on to system testing.

### **Myth 3: Functional Testing Includes performance testing. **

Functional testing and performance testing are in two different categories: functional testing and non-functional testing.

As defined above, functional testing is used to ensure that the functionality of an application meets specified requirements. [Non-functional testing](https://www.guru99.com/non-functional-testing.html) checks the "readiness" of a system by examining the performance, security, reliability, scalability, and other non-functional aspects of the software system. While non-functional testing includes performance testing, it also includes many other types of testing. Some examples may include:

  * **:** How many people can your application support using full-functionality at one time? 
  * Security Testing: Is the system safeguarded against attacks? Both internal and external sources? 

### Myth 4: All Functional Testing Should Be Automated.

There is a common misunderstanding that manual testing will soon be obsolete because of automation, however this is not the case. It's important to find the [balance between automated and manual tests,](https://smartbear.com/learn/automated-testing/what-is-automated-testing/) because as long as humans are interacting with applications, manual testing will always be around.

In general, you should use manual testing when you need to mimic real-world user interactions with an application. Common manual testing practices, that should remain manual and not automated, are exploratory testing, usability testing, and ad-hoc testing. These may include when you need to run complex tests, adhere to strict regulations, create robust documentation, or working with legacy applications that are not built to support automation.

Additionally, manual testing can be useful when you are looking to test for an improved customer experience as you can only collect this feedback through manual, not automated testing.

### **Fact: Functional Testing Matters. **

You must make sure your application is functioning as you intend for it to-otherwise you risk providing a poor user experience, or no experience at all.

But there is some good news! There are plenty of [functional testing tools](http://www.softwaretestinghelp.com/top-20-automation-testing-tools/) out there to make your life easier. Whether testing the front-end, back-end, or both of your applications, SmartBear has the most powerful, yet easy-to-use [functional testing solutions](https://www.youtube.com/watch?v=552zVMfidjM). With our solutions, we help software teams create great software, faster than ever.

_[This article](http://blog.smartbear.com/testing/mythbusters-functional-testing-edition/?) was first published on the SmartBear blog._

Take the Chaos Out of Container Monitoring. [View the webcast on-demand!](https://dzone.com/go?i=274433&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB20689163.213735460%3Bdc_trk_aid%3D412858537%3Bdc_trk_cid%3D97535502%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D)
