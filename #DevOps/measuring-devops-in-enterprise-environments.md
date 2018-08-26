# Measuring DevOps in Enterprise Environments

_Captured: 2018-06-15 at 17:58 from [dzone.com](https://dzone.com/articles/measuring-devops-in-enterprise-environments?edition=383206&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-06-15)_

[Learn more](https://dzone.com/go?i=250324&u=http%3A%2F%2Fblog.scalyr.com%2F2017%2F08%2Fcareerbuilder-resolves-customer-issues-5x-faster-scalyr%2F) about how CareerBuilder was able to resolve customer issues 5x faster by using Scalyr, the fastest log management tool on the market.

A key challenge in implementing DevOps in enterprise environments is defining DevOps in a clearly quantifiable way. How do you measure if your implementation is progressing and, more importantly, how do you measure if it is having the desired results? This challenge is particularly acute for large companies which may be spread across multiple geographies and a variety of technologies.

As more enterprise companies are taking on the challenge of DevOps, the need for standard measurements has become more evident. Over the years of working with companies of all sizes, I have helped to understand and define measurement techniques which focus, not just on the DevOps methodologies, but also on the results. These methods have been applied to companies in size of upwards of $7B with over 50,000 employees.

A common complication faced in enterprise implementations of DevOps is the diversity of technologies and range of team maturities. In one implementation we had over 110 different development teams working in a highly heterogeneous environment. Organizational maturity ranged from teams that had been working together for years with a tightly honed process to teams that were newly formed and just in initial phases of process development. Teams were using a huge variety of technologies ranging from legacy waterfall methodology working on .Net environments based in data centers running Windows 2008 to agile teams with full Continuous Integration and Continuous Deployment (CI/CD) deploys to AB stacks in the cloud. The measurement techniques presented here are developed to adapt to the huge variety often encountered in large companies.

Before providing the details of how to measure DevOps it is important to clarify what is meant by DevOps. DevOps is a practice for significantly improving collaboration between Development and Operations teams. DevOps moves beyond encouraging cooperation and seeks to build this cooperation into the teams, processes, and tooling such that it is an integral part of how a company operates. It is critical to keep in mind that DevOps is not just a set of tools, it is a cultural shift. The shift towards DevOps is a shift which incorporates operations into the development cycle and, as such, does leverage automation and tooling. However, it is the cultural shift which drives the need for better tooling. In this regard, focusing only on the implementation of tools would miss fundamental elements of what we held to be core to DevOps. This understanding of DevOps may help explain the difficulty in measurement. How does one measure collaboration? And, how does one determine how effective collaboration is?

## **Focusing on Business Outcomes: Five Key Business Metrics**

One of the keys to successfully implementing DevOps in any enterprise organization is to understand what you are trying to achieve and to develop measurements by which you would determine the success of our efforts. This drives an essential focus on the "why" of DevOps implementation. It is crucial to determine why you are making a change and what are the expected outcomes. With rapidly rising and falling tech trends, it is important to ensure you are doing things for the right reasons. Don't just do DevOps because it is the latest trend. Do it to drive business results.

In determining the key business metrics which will be driven by DevOps it is critical to distill the myriad of possible metrics to a select few. At the same time, one must not be too singularly focused on a particular metric as to neglect critical elements of what you are trying to achieve or, worse, drive the wrong behavior. The following **five key business metrics** provide a wide range of business drivers where you should see improvement if your DevOps implementation is successful:

  1. Business Agility & Speed to Market - as measured by Cycle Time

  2. Infrastructure Investment - as measured by Capital Expenditure (CapEx)

  3. Stability and Scale - as measured by Availability

  4. Customer Support - as measured by Customer Satisfaction

  5. Product Quality - as measured by Rollback Percentage

## **Measuring Core DevOps Competencies**

With a clear picture of the results you are aiming to achieve, one needs to develop a way of measuring DevOps implementation across the entire organization. The five key business metrics can be used to measure the results but a similar set of measurements must be developed to measure DevOps itself. To do this it is important to define the capabilities that are critical to DevOps. These can provide a list of top-level competencies against which teams will be measured. To provide further detail in measuring these competencies they can be broken down into sub-competences.

This approach is rooted in industry standard maturity models such as the Capability Maturity Model Integration (CMMI). CMMI was developed to measure the maturity of software development processes by defining five levels of maturity. A similar approach is taken here, applying levels of maturity 1 - 5 for each of the major DevOps competency areas and each related sub-competency.

Looking at the overall landscape of DevOps and the keys to success, the **four key competency areas** are:

  1. **Automation**

  2. **Continuous Improvement**

  3. **Independence **

  4. **Operationalization**

These major competency areas can be further broken down into sub-competencies, as follows:

### **Automation**

  * Unit tests
  * Test Automation
  * Continuous Build
  * Continuous Deployment

### **Continuous Improvement**

  * Key Performance Indicators (KPI)
  * Service Level Agreements (SLA)
  * Metric Tracking
  * Remediation

### **Independence**

  * Isolated Configuration
  * Code Dependencies
  * Isolated Infrastructure

### **Operationalization**

  * Monitoring and Alerting
  * Operations Knowledge Transfer
  * Documentation

In keeping with the CMMI model, each sub-competency is rated on a scale of 1 - 5. These scores are averaged to produce an overall competency score. Again, the major competency scores are averaged to provide an overall DevOps maturity score for the team.

While this approach does yield a single score for each team it is important to make clear that a team's rating is not a value judgment, but rather, a reflection of their maturity in DevOps. Because of the potentially significant variation in initial levels of maturity of teams, some teams will have a low score. It simply may not make sense for some teams to push DevOps implementation at all. For example, legacy teams that operated high-value properties that are, nonetheless no longer under active development may have extremely high costs to move the dial in any of the major competency. For these products, it would simply not make business sense to invest in developing DevOps competencies.

It is also very important that the data collected be shared with teams involved. While it should not be seen as a measure of success, the more transparent the data is to everyone the more collaboration can occur.

Transparency around this data can also encourage healthy competition among those teams that are actively working to improve their DevOps competencies. In one institution where we developed the DevOps competency model, we built a simple web-based interface to allow teams to record their scores and track their progress. It provided a single place for teams and leadership to view scores across the organization and to track progress against these scores. This application provided both a high-level view of all teams and their scores across the main competency areas and also allowed teams to dig in and enter scores for each of the sub-competencies. Allowing teams to enter their scores and share them with the rest of the company further enhances a feeling of ownership within the teams for the efforts they are putting forward and the results they achieve.

By creating a competency model that reflected what DevOps meant for the organization and then tracking and making this data visible we were able to successfully drive a consistent DevOps model across a very large organization. The recognition that there are many competencies which comprise DevOps allows us to track in a consistent way across a large number of teams that were anything but consistent. By providing a mechanism to roll this data up into competencies and team scores we are also able to simplify these numbers to make them easier to understand and track consistently across the organization.

Using an outcome-based approach and clearly measurable competencies you can successfully drive DevOps in a large and diverse environment. By beginning with the end in mind you can ensure that improvements in DevOps competencies are driving towards the business results you want to achieve. Each business will have its own key metrics/outcomes and DevOps competencies which it values. While the fundamentals of the model can make sense for any business, this is not a one-size-fits-all model. I encourage anyone looking to use this model to consider what is important to them and modify it to make it work for you. Define your own business KPI and decide on the DevOps competencies and sub-competencies which are right for your business. And, if this all seems too much at first, start simple: decide on one or two business metrics which you hope to measure and begin with the four top-level DevOps competencies. Have teams rate themselves on these competencies. Even in the process of measuring you will learn something, drive a common understanding of DevOps and, in so doing, take a major step forward in your DevOps practice.

**[Find out more](https://dzone.com/go?i=250325&u=http%3A%2F%2Fblog.scalyr.com%2F2014%2F05%2Fsearching-20-gbsec-systems-engineering-before-algorithms%2F) about how Scalyr built a proprietary database that does not use text indexing for their log management tool.**
