# Types of Software Testing and Automation

_Captured: 2016-03-22 at 13:55 from [medium.com](https://medium.com/agile-project-management-scrum-lean-kanban/types-of-software-testing-and-automation-5ae3d552e379#.nwtmboqh7)_

![](https://cdn-images-1.medium.com/max/2000/1*Mqs15oJAwwWhDEKG2lg6rA.jpeg)

Software testing is an important phase of the software development process. There are number of testing types and technique used by people to finding bugs or issues before identified by end-users.

True tester is an advocate of the end user, similar way the Product Owner is the voice of customer. SW industry has been taken up by Agile Methodology by storm, most of the development community has joined the bandwagon of Agile, testing community is somehow missed this train.

Test community still living the life of waterfall inside its agile projects. While in rush to implement agile in any project or organisation , we always overlooked the important aspect -- The Test Engineers.

### Dangerous Assumption

When implementing agile, one mindset is testing or test engineer is not needed, as developer should produce workable and product quality code, however that's not possible in practice.

Further digging deeper the truth and be honest, testing effort , issues or bugs in most of the cases not part of team velocity in scrum, both of these important aspect of product which define the quality lies in the grey area when comes to product,sprint backlog, effort estimation or team's velocity in agile scrum.

Since tester is a true advocate or voice of end user, how come we have given so little emphasis in our development process.

### Testing Tools

Testing community is not equipped with the tools to face the new challenges of agile project management. Organization has done too little to update their primitive process, either they make it too thin or neglect it at all , as they think its an agile way.

Comparing the agile project management tools and Testing Tools industry, SW Testing tools currently available in market is far less in number and quality comparing to the Agile Tools available today.

Agile methodology not only disrupt the developers community but also the tools industry at large, developers have more superior tools available to its arsenal comparing to the SW Test Engineers.

### Software Testing Types and Methodologies

Testing is executing a system in order to identify any gaps, errors, or missing requirements (_known as bugs)_ in contrary to the actual requirements.

### Why should we test

S**_oftware testing is an integral part of software development. The need for software testing stems from a variety of reasons._**

  * _To ensure what is created does what it's supposed to do._
  * _If it works when one person is using it, it should also work when a hundred persons are using it._
  * _There's a lot of different devices, browsers and operating systems out there, and the software needs to be compatible with all mediums._
  * _Software testing is linked to a company's ROI (Return on Investment) as its costs the company in terms of man hours to fix a bug that was not caught in the testing phase. It also means unhappy customers, which can have an effect on your sales._

### Software Testing Types

**_There are many methodologies to go about software testing, let's briefly take a look at the most common methods:_**

### **Black Box Testing**

This is a software testing method where the internal design of the software being tested is not known to the tester. This ambiguity is there on purpose. These tests can be functional or non-functional, though they are usually functional. Test design techniques may include _Equivalence partitioning, Boundary Value Analysis, and Cause Effect graphing._

### **White Box Testing**

This is the opposite of Black box testing. In this method the internal design of the software being tested is known to the tester. Test design techniques include _Control flow testing, Data flow testing, Branch testing and Path testing._

### **Gray Box Testing**

This is a software testing method which is a combination of both the Black box and White box method. In Gray Box Testing, the internal design is partially known. This entails having access to internal data structures and algorithms for designing the test cases, but testing at the user level.

### **Agile Testing**

This is a method of software testing that follows the principles of agile software development, meaning working closely with developers in sprint, testing the user stories or verifying the bugs.

### **Ad Hoc Testing**

This is a method of testing without any planning or documentation.

### **The Software Testing Life Cycle**

The software testing life cycle is a formula for the stages in the testing process. These stages may vary from organization to organization, but generally they follow the same format.

#### **Requirements/Design Review**

In this stage you review the software's requirements and design. This is the initial stage where the structure of the software is analyzed.

#### **Test Planning**

Once you have made up a general idea for what needs to be tested, the tests are planned.

#### **Test Designing**

The tests are designed with reference to the software requirement. Sometimes the tests are designed on the basis of user flow.

#### **Test Environment Setup**

You setup the test environment (server/client/network etc.) with the goal of replicating the end-users' environment.

#### **Test Execution**

You execute your Test Cases/ Scripts in the Test Environment to see whether they pass.

#### **Test Reporting**

You prepare various reports for various stakeholders. This stage should produce reports in the form of Test Results, Test/Defect Metrics, and a Test Closure Report.

Another method to go about the whole process is **Automated Testing**. Automated testing tools are capable of carrying out tests, reporting the outcomes of the tests, and comparing results between various test runs. The method or process that is used to implement automation is known as the test automation framework.

![](https://cdn-images-1.medium.com/max/1200/1*ijuj5ULiOuiVjQ1pw6rZiA.jpeg)

> _Test automation_

### Why should we automate software testing

Automation testing simplifies the testing effort to its minimal, even though its not necessary to automate the testing if its not really needed, it depend on the application or product in question. Remember Idea is to cut short the QA round so the application or release can be delivered in minimal turn around time.

#### Here are the best practice of test automation

  * Test automation require technical knowledge of coding and system.
  * Popular area of expertise in testing community, people started with manual testing and eventually moving to automation.
  * Creating scripts or recording some scenario of testing by using tool or scripts and run it automatically to safe time.
  * Possible to automate GUI level testing.
  * Record and playback type of test mutation doest require coding or scripting knowledge, but maintainability of those test cases is harder if software keep changing.
  * Most import part of automation is automatic strategy.
  * Automation need to be very structured. Identify what what to test and how.
  * Don't automate those part of GUI, that is enhancing in every release.
  * Utilise combination automation testing for interface, scripting, data driven , input-output checks.
  * If you are planning to automate any part of applicant, make sure you have build automation and continues integration in-place.

### Benefits of software testing automation

**_The benefits of automated testing are:_**

#### **1\. It is cheaper**

Technically, automated testing is a one-time cost as opposed to spending money every time testing is required.

#### **2.** **It is faster**

Automated tests are performed much faster than manual tests.

#### **3.** **It is more reliable**

Due to margin of human error, a manual tester may forget to perform a certain test. This is not the case with automated testing.

#### **4\. Reduced human and technical risks**

Let's say the person who has been working on your application are no longer available, what will you do then? Automated tests help the developers embarking on an existing project to start developing without worrying much about possible damage the changes they introduce may cause.

### **UAT Testing**

UAT (User Acceptance Testing) is the final testing performed when functional, system and regression testing has been completed. UAT testing is performed to ensure that the software meets business requirements. UAT, alpha and beta are different types of acceptance testing, and they are carried out by end users who are familiar with the business requirements of the software

### Conclusion

Test team can not keep up with the pace of development team, image in each sprint development team is adding new features so enhancement with the feature with steady speed. In the beginning of project, its possible for the test team to keep testing those feature but within six months as code base grows, with more new features, enhancement and bug fixes, test team can not keep up to deliver the product with quality, most o f the above techniques and methodologies needed to be applied to work smartly. It is difficult to define how much testing is a good testing.

We need to utilise technique as test automation, exploratory testing. Working closely with developers to test the functional aspect of the code from very beginning of its implementation.

It neither help to automate everything nor to do too much of a manual testing, best approach is to find a good balance.
