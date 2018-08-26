# REST APIs: From Idea to Release

_Captured: 2018-08-09 at 15:07 from [dzone.com](https://dzone.com/articles/rest-apis-from-idea-to-release?edition=385351&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=integration%202018-08-09)_

The new [Gartner Critical Capabilities report](https://dzone.com/go?i=299475&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fgartner-critical-capabilities-for-full-life-cycle-api-management.html%3Fcid%3DNA-DSP-DP-AFL-000195-00001718-000002620%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dlifecycle_apig_land%26utm_content%3Dna_report-gartner-critical-capabilities-report%26mrm%3D696921) explains how APIs and microservices enable digital leaders to deliver better B2B, open banking and mobile projects.

We often think of API definition as beginning with the description file, most of us are using swagger or [OpenApi](https://www.openapis.org/). The challenge with this approach is that API producers often get into the weeds on resource names and methods before actually determining what the API capabilities need to be.

When a company decides to release an API, depends on the API type, she must first accomplish an MVP (Minimal Viable Product). Then, this API must go through some feedbacks from the API consumers in order to make sure the API provided is functional, reliable, and usable.

![](https://blog.restcase.com/content/images/2018/05/MVP2-2.png)

> _Let's quickly go over the types of APIs, as most of the APIs can be divided into 3 groups -- public, private, and partner._

## Private APIs

This is the most closed format of providing and consuming APIs. Often, private APIs are built to enhance process automation inside a company between systems. In other words, this is about integration economy inside one company.

## Partner APIs

Partner APIs are revealed to other companies with whom we are ready to build a more tight connection. The other company might use some of our product data to expose our offering to their clients.

The company [building REST API](https://apibldr.com) is providing other companies with a machine-readable API spec (swagger or OpenApi). Why? With that partner (candidate) could generate a mockup API mimicking your production API and develop integration against it. That would speed up integration and also reduce your work amount.

## Public APIs

These APIs are listed in catalogs and not hidden from anyone. They are online and anyone can access those APIs (sometimes with authorization keys or another authentication mechanism) and the API definitions are public and visible to all.

## Minimum Viable Product

Many organizations opt for the fast, easy win by releasing an "MVP" into the market with the intent to build on those concepts from there. While that may work for traditional products, it is far more challenging with APIs because of their role in applications that depend on them.

If you are going to provide an API that is both desirable and stable, you need to ensure that your initial API release is functional, reliable, and usable. A death knell for APIs is releasing constant breaking changes or updates that require the app developer to rework their app.

![](https://blog.restcase.com/content/images/2018/05/mvp.png)

Nowadays, most of the companies have embraced the LEAN and the Agile methodologies, especially the working in sprints and doing a demo for clients each sprint. By doing this, the company allows refining the required vs desired capabilities before diving into the details of how to implement those capabilities, this is not only saving money in the long run but making sure that the API/product has actual value.

The main goal of this is understanding the value to the customer and constantly readjusting based on feedback got from the API consumers.

## Getting Feedback

Taking the time to test your APIs in the market before committing to code or a roadmap can be a big investment of time and money. But making that investment pays off in many ways. Let's look at some of the benefits of this approach:

  * Planning the capabilities first allows you to think strategically about your release plans and your potential partners. When you commit yourself first to the inner workings of the API, you become locked to the technology rather than the strategy.
  * By gathering feedback on your roadmap and capabilities, you can be agile about changing both of those because you haven't already committed to an API design and code.
  * Your potential API consumers are into your API as they have provided direction and strategic thought to help form your API. You are building what they asked for and they know it.

If you ask for feedback on your API concepts, you need to be prepared to react to that feedback and make sure that your organization is able to react to changes in plans. In other words, you may have to sacrifice speed for quality.

## Establishing Feedback

Depending on the complexity of your API and the urgency to release it, you can use any number of techniques to get feedback on your API.

![](https://blog.restcase.com/content/images/2018/05/feedback-1.png)

### Developer Focus Groups

Organize a developers group in order to get feedback first of all from those that are going to actually use your API on the development level and on the concept/idea of the API itself. The goal of this is to make sure the API is something that is needed and can be adopted by developers.

Here are some tips for organizing a developer focus group:

  * To keep this conversational, the ideal size for this type of gathering is no more than 30 people.
  * Make sure you include a variety of participants -- enterprise devs, start-up devs, product managers, all from a variety of verticals.
  * Be prepared to show your concepts and encourage honest feedback. Do not convince, do not justify; this is a listening exercise. Explore the feedback with questions, questions, and more questions.

### Publicly Available Mock

Ideally, you follow the focus group sessions with what you believe will be your first [version of the API](https://blog.restcase.com/restful-api-versioning-insights/), but in mock form. The goal of this API (mock) is to move from concept to reality by exposing the API interface along with some mock data in a playground setting.

This will let developers make calls to the API, encourage feedback on the interface design and payload construction.

Providing client SDK can benefit later on, but not recommended for the first stage as developers will not actually use your API as they want and will be stuck in the SDK and what he allows.

Some things to consider when you make API mock available:

  * Your API design should be as clean as possible. You need to consider security and versioning from this point and forward.
  * Publish your draft documentation along with the API provided. API documentation is not a separate deliverable -- it is part of the part the API itself. Do not forget to give many examples of both good and bad calls.

## Beta/Invite Only

Okay, so we have gotten feedback on the API from focus groups before writing a single line of code, and we created a mocked API along with first-draft documentation. Now it's time to hit production.

This is where you really need to evaluate your risk tolerance. If your API does not involve secure information or mission-critical capabilities, you can deploy to production and open it for general use.

It is advised to slowly roll out the API to General Availability stage by providing the API to a limited audience.

This gives you yet another opportunity to gather feedback and make improvements before making it more widely available.

Here are some general guidelines for the Invite-Only phase that can help you ensure your API is solid and meets market needs:

  * Identify up front the size of the developer community you want to provide access to and keep the guardrails up to make sure it stays within that range.
  * Decide how you want to build that community -- do you want to reach out to specific developers who were engaged in the earlier iterations? Or do you want to have a publicly available sign-up form that you use to select your initial community?
  * Be prepared to make changes based on this first real-world trial. You may feel that you've already done enough iterations. But bear in mind that this is the first-time developers are trying to build meaningful production-ready apps using your API. They will find things they didn't find before -- Oauth issues, documentation inaccuracies, rate limitations, performance problems, etc.

**Set a pre-defined time range for this phase. Being in beta is addictive.**

## Releasing an API

For this, I personally recommend creating release criteria for an API (same as a regular product):

  * Zero high priority bugs
  * Penetration testing was done and passed
  * For all open bugs, documentation in release notes with workarounds
  * All planned QA tests run, at least 90% pass
  * Number of open defects decreasing for the last three weeks.
  * Feature x unit tested by developers, system tested by QA, verified with customers A, B in the Invite-Only stage, before release

Once you meet your release criteria, you are ready to release.

Good luck!

The new [Gartner Critical Capabilities for Full Lifecycle API Management report](https://dzone.com/go?i=299476&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fgartner-critical-capabilities-for-full-life-cycle-api-management.html%3Fcid%3DNA-DSP-DP-AFL-000195-00001718-000002620%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dlifecycle_apig_land%26utm_content%3Dna_report-gartner-critical-capabilities-report%26mrm%3D696921) shows how CA Technologies helps digital leaders with their B2B, open banking, and mobile initiatives. [Get your copy from CA Technologies.](https://dzone.com/go?i=299476&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fgartner-critical-capabilities-for-full-life-cycle-api-management.html%3Fcid%3DNA-DSP-DP-AFL-000195-00001718-000002620%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dlifecycle_apig_land%26utm_content%3Dna_report-gartner-critical-capabilities-report%26mrm%3D696921)
