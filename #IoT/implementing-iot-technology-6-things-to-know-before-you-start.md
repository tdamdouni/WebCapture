# Implementing IoT Technology: 6 Things to Know Before You Start

_Captured: 2017-05-16 at 20:01 from [dzone.com](https://dzone.com/articles/implementing-iot-what-to-know-before-you-start)_

As we closed out 2016, we learned that implementing IoT technology still remains a challenge for most manufacturers looking to digitize their products or services.

Our research suggested that by the end of the year, we surpassed 10,000 global enterprise IoT projects. While most of them are still in the PoC (Proof-of-concept) stage, some of them end up in frustration. As one (unnamed) project manager recently put it: "Our implementation had serious flaws. In hindsight, I wish we had asked the right people and more questions beforehand."

In recent months, the IoT Analytics team performed extensive research on IoT technology implementations, interviewing dozens of decision-makers both on the end-user and the IoT technology vendor side. We also compiled a list of 640+ real enterprise [IoT projects](https://iot-analytics.com/product/list-of-640-iot-projects/) last September. But even with last year long gone, the lessons are still as relevant as ever. Companies implementing IoT solutions should read these helpful insights to avoid the mistakes others have made.

## Key IoT Components

Whether companies are working on a predictive maintenance solution for wind energy, vehicle tracking in the supply chain, or precision farming in agriculture, the basic IoT technology is the same. We summarized the technology in 15 components (see below):

![Image title](https://iot-analytics.com/wp/wp-content/uploads/2016/11/iot_figures_solution-development_preview20-1-min-e1478014119996.png)

> _[Image title](https://iot-analytics.com/wp/wp-content/uploads/2016/11/iot_figures_solution-development_preview20-1-min-e1478014119996.png)_

_(Click to enlarge)_

Not only is the technology similar, we also found that some common problems emerge when talking to those who have implemented IoT technology.

Here are six lessons:

## Organizational and Cultural Changes Are Often Underestimated

This is the number one challenge we hear about when we talk to end-users who have implemented IoT projects and ask them about their biggest lessons learned.

Take the German cleaning machine manufacturer Karcher, for example. Their director of digital product, Friedrich Volker, mentioned that when they started rolling out their connected fleet management solution "our team had no experience in pitching software and virtual offerings to the customers. Rather than making a one-off sale, they are now in continued talks with the customer regarding the ongoing performance of the machine. This change in mindset, as well as the education of the sales team, takes time, and it is just one of many organizational challenges we are faced with."

IoT initiatives are usually part of a larger digital company transformation that requires the product development organization to adopt agile approaches and the billing process to support subscription-based customer billing, or even pay-per-use based billing.

**Takeaway**: Take the organizational change management efforts seriously, start early and use agile methods!

## IoT Projects Take Much Longer Than Anticipated

This might be a no-brainer to some, but implementing IoT really takes a long time. Our research found that the fastest IoT technology implementations went from business case development to commercial roll-out in nine months. But these are exceptions. The current **average of time-to-market is around 18-24 months.** Reasons for prolonged project timelines are manifold, including both business-related issues (e.g., not having the buy-in from the right stakeholders), as well as technical issues (e.g., not working with an infrastructure that supports scaling the solution in a commercial deployment scenario).

What's more: Profitability is usually not achieved for another few years, as most firms are focused on achieving a critical mass on their IoT solution at first.

**Takeaway**: Teach all stakeholders to be patient and build in little success stories that help satisfy shareholders and senior management on the way.

## Necessary Skills Are Not Available In-House

End-to-end IoT solution development requires a broad range of skills, including embedded system design, cloud architecture, application enablement, data analytics, security design, and back-end system integration (e.g., into ERP/CRM).

Unfortunately, manufacturers have limited experience in working with the technology elements that are unique to the Internet of Things such as MQTT or AMQP protocols, LPWAN communication, and edge analytics.

Our research suggests that the **skills gap in data science** is particularly worrying.

**Takeaway**: Map the IoT skill gaps, cross-train, and upskill the workforce with a focus on new technologies unique to IoT. Work with true IoT technology experts from different fields with deep domain knowledge.

## Security Is Often an Afterthought

Security is too often an afterthought when teams start to develop IoT technologies. The security features are commonly cut from initial designs to accommodate additional device functionality. However, global data and device security need to play a central role in IoT technology development, for companies and customers to broadly adopt the 'Internet of Things.'

One example is a manufacturer of connected medical devices, which employs a so-called "ethical hacker" whose sole role is to detect security vulnerabilities in the network. This security-breaking expert applies typical hacking techniques to root a device, penetrate, lift and de-obfuscate code.

**Takeaway**: Follow security best practices, such as employing a secure boot process or using unique identity keys and map the attack surface (e.g. using the STRIDE model).

## Interconnectivity Issues Are a Major Complexity Driver

When you download an app on your phone, you take for granted that it is ready to be used within seconds. People who are not too familiar with IoT often have the misconception that it must be similar with IoT technology.

However, today's reality is far from that. Protocol translation still takes up a majority of today's IoT development efforts. During the IoT technology implementation of an industrial OEM, it took nearly four months to develop all necessary protocol translations and make equipment and applications work seamlessly.

**Takeaway**: Build on a standardized ecosystem that is relevant for your use case and industry.

## Scalability Becomes an Issue When Going to Thousands of Devices

There are not many people who report this issue, but when they do, they are in deep trouble -- because in most cases, the products are already in the market.

A large manufacturer of construction equipment initially created neat dashboards to monitor their machines remotely. A year later, the project was amended to start performing predictive maintenance and fault analysis of the hydraulic systems. That is when the team realized that the data model did not support the necessary backend processing capacity.

In another example, the processing power of the hardware wasn't powerful enough when a manufacturer wanted to add functionality to the connected device.

**Takeaway**: Even though you should start small, you must think big from the beginning. Build your IoT technology in a modular fashion and challenge your hardware design and data model.
