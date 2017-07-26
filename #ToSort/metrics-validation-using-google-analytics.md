# Metrics Validation Using Google Analytics

_Captured: 2017-05-24 at 13:31 from [dzone.com](https://dzone.com/articles/metrics-validation-using-google-analytics?edition=299096&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-23)_

Need to build an application around your data? [Learn more](https://dzone.com/go?i=200129&u=http%3A%2F%2Fhubs.ly%2FH06Pr9h0) about dataflow programming for rapid development and greater creativity.

This article helps us understand how to leverage the tools and techniques provided by Google Analytics to proactively look for any issues/deviations after a production deployment. It talks about capturing KPIs and baseline metrics, identifying and analyzing deviations, generating meaningful reports/dashboards from the data captured, and the related capabilities of Google Analytics.

Though there are other analytics tools that provide similar capabilities, this paper considers only Google Analytics.

## Abbreviations

**Abbreviation**

**Expansion**

GA

Google Analytics

KPI

Key Performance Indicators

## **Challenges Faced**

  * Desktop applications are distributed free of cost to users across the globe. Close to 50M users currently use this application. The company promotes and sells their products using the free desktop version and has a revenue of close to 12M USD per year.

  * We have close to two releases every month. The changes are complex in nature and impacts various life cycle events like installations, reporting, clicks, uninstallations, offer volume, landing page visits and purchases.

  * Due to the huge and diverse user base, some of these changes have a good chance of introducing bugs in the application. Any adverse impact on the application takes a week's time before it is communicated to the engineering teams. By that time, there is a significant impact on the business, like reductions in userbase or revenue.

  * We wanted a practice that will proactively identify any issues after a deployment. We would like to achieve this with as minimal manual intervention.

## **What Is Metrics Validation?**

Metrics validation is a method of proactively identifying KPIs, gathering metrics for those KPIs, and comparing the metrics with the baseline values. The deviations, if any, are analyzed to find out if there was any defect/bug introduced.

## **Solution Approach/Remedial Action**

We needed a practice that will be able to:

  * **Identify KPIs**. Identify the KPIs that directly or indirectly impacts the business goals (purchases, uninstalls, cohort data, life cycle events like installs, user activities and landing page visits are some examples).

  * **Baseline the metrics for each KPI**. Capture the metrics for each of these KPIs. The baseline metrics should be aligned with the releases and updated regularly and the metrics should be as granular as possible. If possible, have one metric for every logical flow in the application. For example, if we have used a different API for Windows 8.0, capture the metrics for Windows 8.0 separately.

  * **Do what needs to be done post-deployment**. Gather the identified metrics after the deployment. Compare the metrics that are gathered with the baseline metrics. Identify and analyze any deviations. Apply a threshold if required.

  * **Find the cause for the deviation**.

![Image title](https://dzone.com/storage/temp/5338426-one.jpg)

> _As-is process and the new process._

## **GA Tools**

The following GA tools can be leveraged for this purpose.

  * **Custom alerts**. Alert the required teams when a particular metrics deviates beyond a threshold.

  * **Dashboards**. Dashboards contain one or more widgets (up to 12 per dashboard) that give an overview of the dimensions and metrics you care about most.

  * **Lifecycle funnels**. There will be a certain number of steps that users have to take in order to generate revenue. Funnels help us see this process (or processes) easily, by giving us a visual representation of the conversion data between each step.

  * **Real-time data**. Real-time data allows monitoring activity as it happens on the site or app. The reports are updated continuously and each hit is reported seconds after it occurs. This is especially useful if we would like to validate the behavior immediately after a deployment.

![Image title](https://dzone.com/storage/temp/5338427-two.jpg)

## Benefits

  * **Reduced calls to call center**. As the bugs are resolved immediately after they are introduced, calls to the call center support regarding issues with the product are reduced.

  * **Reduced impact on business**. Turnaround time for the bug fixes is reduced, thereby reducing the impact on business.

  * **A large volume of data**. Rather than depending only on the information provided by the end users, we can gather all the required information regarding the bug. This helps us analyze the scope of the bug. For example, a bug would have been reported for only Windows 10 but the bug might have been present in Windows 8.0, as well.

  * Improved user experience.

## **Learning/Improvements**

Any team that's constantly pushing changes and anticipates any bugs can use this practice. The applications should be diverse and should have a large user base. Teams should ensure that the deviations are properly analyzed. For example, a market trend should not be mistaken as an issue with the application.

[Check out](https://dzone.com/go?i=200130&u=http%3A%2F%2Fhubs.ly%2FH06Pr9h0) the Exaptive data application Studio. Technology agnostic. No glue code. Use what you know and rely on the community for what you don't. [Try the community version](https://dzone.com/go?i=200130&u=https%3A%2F%2Fexaptive.city%2F%23%2Flanding%3Freferrer%3DGeneral).

Opinions expressed by DZone contributors are their own.
