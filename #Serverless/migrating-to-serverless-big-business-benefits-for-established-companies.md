# Migrating to Serverless: Big Business Benefits For Established Companies

_Captured: 2018-09-05 at 20:12 from [dzone.com](https://dzone.com/articles/migrating-to-serverless-big-business-benefits-for?edition=391198&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-09-05)_

Container Monitoring and Management eBook: [Read about the new realities of containerization.](https://dzone.com/go?i=299567&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Febook%2Fcontainer-monitoring-and-management.html%3Fcid%3DNA-DSP-APM-AEJ-000195-00001663-000000492%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dddc_apmsaas_acquire%26utm_content%3Dna_eb1-container-monitoring-mgmt-articlepreroll%26mrm%3D)

What is serverless? Serverless is a cloud computing model that was first introduced by AWS in 2014 (AWS Lambda is the market leader to this day). It abstracts away most of the server operations to the cloud provider so developers can only focus on writing code and shipping new features. Serverless adoption is rapidly growing and it's mostly due to it's promise of providing significant cost and time efficiency for technology companies.

For new startups, just starting to build their first product, it's a no-brainer to build it on serverless. It's very cheap and quick to get started. You don't have to have that much knowledge about the backend processes, since the cloud providers handle all that and you can just focus on building your product and it's functionality. The go-to-market time is much shorter than with previous computing models and it scales automatically when you get successful and have tons of users pouring on your site. See, a no-brainer!

With already established companies, it's harder to switch to serverless because of the legacy systems and processes that they have in place, but I'm here to argue that it might be worth the pain!

## Big Companies = Big Savings

For established companies (depending on their specific use case), serverless architecture gives the opportunity to save money that was previously paid for hosting idle code. With serverless, you only pay for when your code is executed. The bigger the company and the more complexity it's technology has -- the bigger the potential savings can be.

**[FINRA's experience with cost reduction:](https://aws.amazon.com/solutions/case-studies/square-enix/)**

> "Using AWS Lambda, we've increased cost efficiency by a factor of two. We only pay for what we use, and we don't have to manage on-premises server infrastructure."

For new startups these costs can be trivial, but for some companies it can be a make-or-break question to get these costs down. For example some companies have reported [close to 90% of cost reductions](https://dashbird.io/blog/saving-money-switching-serverless/) just by switching to serverless.

## A Promise of Reliability and Availability to The Users

Slightly bigger companies usually already have an established user base that is also rapidly growing. It means that they have the responsibility to keep the service reliable at all times. One of the nastiest things that can happen (and very often occurs in growing technology companies) is that your service gets a sudden peak in traffic -- either it's a really successful marketing campaign that just launched or some other reason that spikes the usage of your product very suddenly -- and your site can't handle that extra load. As a result, your customers get a bad experience with your product at the most unfortunate time -- when you are finally hitting it big.

Why serverless is so useful -- instead of constantly being ready for the potential spike and paying for the extra servers, you can let cloud providers worry about automatic scaling. Now the bigger influx of users won't just be a happy moment for your marketing team, but the engineers can also sleep well at night.

**[Square Enix experience with automatic scaling:](https://aws.amazon.com/solutions/case-studies/square-enix/)**

> At a New Year's Eve event after migration to AWS Lambda, screenshots were taken at a rate of more than 6,000 per minute. "AWS Lambda had a striking effect. Image processing that used to take several hours was finished in a little over 10 seconds."

## Saving Money and Time Because Less server Ops Is needed

In established companies that have been around for some years, you might have lots of people working only on provisioning and scaling servers. Once this is "outsourced" to cloud providers, these people can restructure their work and focus on more business-critical tasks. Depending on the size of the company and the structure of the development team, it can be a huge benefit that not only saves time and money, but can also make hiring for some positions easier.

**[Alt/S experience with reducing server ops:](https://aws.amazon.com/solutions/case-studies/alts/)**

> Zero time is now spent deploying or maintaining server instances, as Sportify's entire backend platform is based on AWS Lambda.

## Technical Team Will Focus on The Business Logic

Serverless computing shortens the time from code development to putting that code in production. This puts the focus of development team strictly on writing code that benefits the users or follows some specific business logic and goals.

Since serverless is just another layer of abstraction in cloud computing, its main benefit is to allow dev teams to write and ship better code, better functions, and therefore, better products. It's the rocket fuel for future innovations and bigger companies can't afford to stop innovating.

**[Benchling experience with better business focus:](https://aws.amazon.com/solutions/case-studies/benchling/)**

> Instead of worrying about the solution architecture and managing servers, they are freed up to focus on new projects and initiatives that can help grow the company.

## Increased Agility and More Efficient Dev Teams

It's commonly known that as companies grow, the execution speed goes down and there are more processes and more bureaucracy involved with every task. Since it's very easy and quick to launch new functionality (and also to scrap it) with serverless, established companies can reverse this process and bring back the experimental feature launching speed that small startups enjoy.

**[Autodesk experience with increased agility:](https://aws.amazon.com/solutions/case-studies/autodesk-serverless/)**

> Building our product (Tailor) on a serverless architecture made it easy to modularize it for easier sharing with other divisions, or as an open-source package with non-Autodesk entities that have a use for it.

## Why Some Companies Are Still Hesitating with The Switch?

Serverless technology is not in its infancy anymore and yet it's not fully mature either. At least that's what the hesitant-to-jump-on-new-technology big companies are saying.

**[Yaron Haviv, founder and CTO of iguaz.io, says:](https://thenewstack.io/serverless-101-how-to-get-serverless-started-in-the-enterprise/)**

> "The interesting part is that by abstracting away much of the Docker/Kubernetes complexity, serverless can be adopted faster and more easily, even though it's the newer tech."

There are also some unique challenges that come with this new computing paradigm -- slow cold starts, short-lived functions, a closed set of triggers and lack of observability and debugging options. There are workarounds and viable solutions for solving these though thanks to a growing community that works on documenting use cases and best practices.

One of the biggest problems -- lack of observability for the distributed serverless systems -- is solved by several newly emerged third-party tools, the most notable one being [Dashbird.](https://dashbird.io) It gathers CloudWatch logs along with X-Ray and API Gateway data and gives general overview of all your functions -- along with error alerts, tracing, live tailing and much more.

## Conclusion

Despite being careful about jumping on another bandwagon too quickly, established companies have a lot to win from migrating to serverless. Since serverless adoption is already skyrocketing, big businesses should not wait too long to get on board, because this new paradigm shift favors quick shipping and constant innovation -- and that's exactly what might give some new and hungry startups the edge to go against dinosaurs and beat them.

Take the Chaos Out of Container Monitoring. [View the webcast on-demand!](https://dzone.com/go?i=299568&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcompany%2Fevents%2Fwebcasts%2Fapplication-performance-monitoring-and-management.html%3Fcommid%3D286663%26cid%3DNA-DSP-APM-AEJ-000195-00001663-000000493%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dddc_apmsaas_acquire%26utm_content%3Dna_webcast1-apm-taming-chaos-articlepostroll%26mrm%3D)

Topics:

error tracking ,serverless ,lambda monitoring ,aws lambda ,alerting ,cloud ,large enterprise
