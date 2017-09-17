# Continuous Testing Is Crucial for DevOps, But Not Easy

_Captured: 2017-08-23 at 19:41 from [dzone.com](https://dzone.com/articles/continuous-testing-is-crucial-for-devops-but-not-e?edition=319391&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-22)_

[Download the blueprint](https://dzone.com/go?i=228233&u=https%3A%2F%2Foffers.automic.com%2Fblueprint-to-continuous-delivery-with-automic-release-automation%3Futm_campaign%3DAMER%252520Online%252520Syndication%252520DZone%252520Platinum%252520Sponsorship%252520Ads%252520JULY-2017%26utm_source%3DDzone%252520Ads%26utm_medium%3DBlueprint%252520to%252520CD) that can take a company of any maturity level all the way up to enterprise-scale continuous delivery using a combination of Automic Release Automation, Automic's 20+ years of business automation experience, and the proven tools and practices the company is already leveraging.

_This is part 4 of a blog series exploring common mistakes and best practices in testing. This week's blog is about continuous testing in production._

As software transitions from a monolithic to a microservice architecture, organizations are adopting [DevOps](https://www.xmatters.com/solutions/devops/) practices to accelerate delivery of features to customers and improve their experience.

Jumping into continuous testing without the right infrastructure, tools, and processes can be a disaster. Continuous testing plays an important role to achieve the fastest quality to market. Continuous testing requires several levels of monitoring with [automated triggers, collaboration, and actions](https://www.xmatters.com/resource/3-use-cases-connected-systems/). Here's what is required:

  1. **Automatic Test Triggers** to execute tests as software transitions from various stages - development/test/staging/production.
  2. **Service Health Monitoring** to automate feedback on failures.
  3. **Test Result Monitoring** to automate feedback on failures.
  4. **Identifying Root Cause of Failure **and analyzing test results.

Let's take a closer look at each of these requirements.

## **1\. Automated Test Triggers**

To enable faster feedback, tests need to be classified in various layers:

  * **Health Check --** The focus of these tests is to ensure the services are up and running. Such checks are triggered by various monitoring applications.

  * **Smoke Test -- **The focus of these tests is to verify that key business features are operational and functional. Such tests should have a short test cycle, typically less than 15 minutes and executed on a continuous basis.

  * **Intelligent Regression -- **This subset of the regression test scenarios is triggered based on the code changes with deployments, and a full regression is triggered on a nightly basis.

  * **Benchmark/Load Test -- **The focus of these tests is to measure the performance of each service, triggered on a nightly basis.

  * **Reliability/Chaos Testing -- **The focus of these tests is to measure system behavior while failures are deliberately injected into services. Such tests are triggered on a weekly basis to identify key infrastructural/operational issues.

## **2\. Service Health Monitoring**

Maintaining the health of services requires:

  * **Automated Alerts -- **Automation notifies the relevant service team to take the appropriate action required by the failure.

## **3\. Test Results Monitoring**

As tests are triggered, it's essential to monitor the results and take the required steps when there are failures:

  * **Automated Notifications -- **Notify the appropriate service development teams to take necessary actions such as block release from going to production if a critical defect is introduced.

## **4\. Identifying Root Cause of the Failure**

Set up a framework to track every request made for automated test runs and how those requests traverse the various distributed services:

  * **Identifying Information --** Every request made for automation test runs includes a custom header that includes information like Test Run ID or Test Case ID. After the request is submitted, the response will contain application trace IDs which you can track under the test results log.

Every test failure triggers an automated investigation process which does the following:

  * Retrieves the test case details to identify the list of components tested in the respective tests.
  * Identifies if any one of the components has changed since the last successful test run.
  * Identifies the list of changes and retrieves the metrics for each of those components.
  * Correlates the test results based on the changes to identify a pattern.
  * Once the problem is identified, updates the service team owners to take the necessary action to fix the problem.

[Download](https://dzone.com/go?i=228234&u=https%3A%2F%2Foffers.automic.com%2Fblueprint-to-continuous-delivery-with-automic-release-automation%3Futm_campaign%3DAMER%252520Online%252520Syndication%252520DZone%252520Platinum%252520Sponsorship%252520Ads%252520JULY-2017%26utm_source%3DDzone%252520Ads%26utm_medium%3DBlueprint%252520to%252520CD) the 'Practical Blueprint to Continuous Delivery' to learn how Automic Release Automation can help you begin or continue your company's digital transformation.
