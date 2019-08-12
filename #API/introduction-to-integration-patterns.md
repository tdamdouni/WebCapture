# Introduction to Integration Patterns

_Captured: 2018-09-06 at 19:11 from [dzone.com](https://dzone.com/articles/introduction-to-integration-patterns?edition=391202&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=integration%202018-09-06)_

###  Let's check out an introduction to integration patterns as well as explore remote procedure invocation and messaging systems. 

The new [Gartner Critical Capabilities report](https://dzone.com/go?i=299475&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fgartner-critical-capabilities-for-full-life-cycle-api-management.html%3Fcid%3DNA-DSP-DP-AFL-000195-00001718-000002620%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dlifecycle_apig_land%26utm_content%3Dna_report-gartner-critical-capabilities-report%26mrm%3D696921) explains how APIs and microservices enable digital leaders to deliver better B2B, open banking and mobile projects.

_This article is featured in the new DZone [Guide to API Management: Comparative Views of Real World Design](https://dzone.com/guides/api-management-comparative-views-of-real-world-des). Get your free copy for more insightful articles, industry statistics, and more!_

In today's mashup-driven world, the use of integrations to extract, transform, and utilize data is at the top of mind for a majority of software engineers. It is important to understand proven integration patterns which can help streamline the integration process and flows.

## Integration Styles

When defining an integration between one or more different sources, the"how" question must be answered in order to proceed. In other words, one must determine how the integration will transpire. This is often referred to as the integration style.

## Remote Procedure Invocation

Remote procedure invocation (RPI) is a pioneer in the integration space and was the go-to manner to implement an API in the early days of computing.In this approach, a provider will allow an external process to make requests into a closed application. The external caller has the specifications to make the request and an expectation on what the response will be, but all the logic takes place using a black-box approach. In this case, RPI is the mechanism used to perform some action against the target system.

Consider an application which handles financial transactions. Prior to the popularity of RESTful APIs, the vendor may offer an API to allow transactions to be posted from an external source. This API was implemented using RPI.

The developer would write a program to gather the required information, then connect to the application using RPI. The results of the RPI/API requests were packaged in a response and that information was processed by the calling application.

## Shared Database

The shared database integration style leverages a database for the connectivity between two or more applications. As a result, each application would maintain a connection to a shared database containing the information that will be integrated.

As an example, use of an INSERT statement to a staging table in the database could trigger a stored procedure which would perform business logic -- ultimately updating attributes elsewhere in the database for other applications utilizing that same shared database integration.

## Messaging

The messaging integration style started to gain momentum with service-oriented architecture (SOA) implementations -- leveraging an enterprise service bus (ESB) as the foundation for the message itself.

Using the financial transaction example, the custom application may simply place a message on the ESB requesting a certain transaction be posted. That system submits the message and relies on the messaging integration style to handle any remaining tasks.

On the financial system side, the message being placed on the bus triggers and event which consumes the message and takes the appropriate action based upon the nature of the message. Based on the message queue used and/or metadata within the message itself, the financial system understands the task that needs to be performed.

When completed, the financial system may place a new message on the bus, which could be consumed by the original system. In this case, it might be related to unique transaction information to append to the original request for auditor validation purposes.

## The Message Concept

The courier for integrations is largely based around the concept of messaging. This no different than other technology-driven solutions, as something is used to pass around information important to the solution at hand. Using RESTful APIs as an example, the courier is often the payload that is passed to a POST request or returned from a GET request.

## Messaging Systems

A major benefit of the messaging concept is that the asynchronous messages do not require both systems to be online and available at the same time. One system may place a message with an ESB, which could be processed immediately by another system or on a schedule hours later. Either way, both conditions can be handled without impacting the other.

The message system employs channels (or queues) to organize and categorize the information that needs to be integrated. For example, if the source system needs to communicate with a financial system and an HR system, the messages would use different channels for each message type.

## Message Routing

The idea of message routing is often implemented in more complex integration scenarios, where a message may be required to route across multiple channels before reaching the target destination.

A message router can assist in this scenario, allowing messages to be submitted to a dedicated component that will analyze the message and employ business logic to determine where to route the message based upon the contents of the message itself.

In the financial transaction example, the source system will simply need to post a transaction. If the corporation maintains multiple financial systems, the source system may not have a detailed understanding of which system handles which transactions. The message router would become the source of the message and would have the proper knowledge to fulfill the delivery of the message to the proper channel.

Message routing goes even deeper and can use a vast array of patterns which assist the routing process. Some common patterns include:

  * Message Filter: Allows messages to be filtered based upon attributes within the message.
  * Scatter-Gather: Allows synchronous messages to be sent to multiple sources at the same time.
  * Message Aggregator: Allows messages from multiple sources to be processed and pushed into a single resulting message, perhaps to process the results from scatter-gather.

## Message Transformation

Connecting disparate systems often brings to light that a given response does not match the expected or preferred response from the source system. Message transformation is a mechanism which can perform the necessary conversion of data between the two systems.

Using the financial system example, the source system may wish to send data in JSON, but the financial system is expecting XML. Using message transformation, the incoming JSON data would be analyzed and converted(i.e. transformed) into XML to prepare for processing by a SOAP web service. This is basically the normalizer integration pattern in use.

Some established message transformation patterns include:

  * Content Enricher: Allows metadata to be modified in order to meet the expectations of the target system.
  * Claim Check: Temporarily streamlines the message in order to remove metadata which is not necessary at that point in time, but available for later processing.
  * Content Filter: Remove metadata from the message completely, more permanent than the claim check approach noted above.

## System Management

Building upon the integration styles and the flow and processing of a given message, the management of the integration is the core of the solution.

## Control Bus

The control bus pattern is the management tier within the integration system. As one might expect, the control bus employs the same concepts implemented by the integration system.

When the administration layer requires information to report user to the system admin, message data captured by the integration system is utilized to report the status or any known issues that have been encountered.

## Message Store

Managing any system often requires some level of historical information or metrics. The challenge with metrics examining the messages without impacting the transient nature of the messages themselves. The message store pattern meets this need by sending a duplicate copy of the message to the message store. Once a copy of the message is stored within the message store, the necessary metrics can be maintained and passed to the control bus for processing and reporting.

## Smart Proxy

Messages typically flow through to a fixed output channel. However, there are cases where a component needs to post reply messages back to a channel specified in the original request. When this need arises, the smart proxy pattern can be employed.

The smart proxy includes logic to intercept messages in order to capture the return address specified by the sender. Once processing is finished, the smart proxy replaces the fixed output channel destination with the address captured when the original request was received.

## Conclusion

Maintaining an understanding of the integration styles, message concepts and the system management patterns can help guide integration developers toward employing practices that translate across any integration project regardless of the industry. Doing so will reduce the ramp-up time as additional resources support and maintain existing integration projects.

_This article is featured in the new DZone [Guide to API Management: Comparative Views of Real World Design](https://dzone.com/guides/api-management-comparative-views-of-real-world-des). Get your free copy for more insightful articles, industry statistics, and more!_

The new [Gartner Critical Capabilities for Full Lifecycle API Management report](https://dzone.com/go?i=299476&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fgartner-critical-capabilities-for-full-life-cycle-api-management.html%3Fcid%3DNA-DSP-DP-AFL-000195-00001718-000002620%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dlifecycle_apig_land%26utm_content%3Dna_report-gartner-critical-capabilities-report%26mrm%3D696921) shows how CA Technologies helps digital leaders with their B2B, open banking, and mobile initiatives. [Get your copy from CA Technologies.](https://dzone.com/go?i=299476&u=https%3A%2F%2Fwww.ca.com%2Fus%2Fcollateral%2Findustry-analyst-report%2Fgartner-critical-capabilities-for-full-life-cycle-api-management.html%3Fcid%3DNA-DSP-DP-AFL-000195-00001718-000002620%26utm_medium%3Donlineads_onl-dsp%26utm_source%3Ddzone%26utm_campaign%3Dlifecycle_apig_land%26utm_content%3Dna_report-gartner-critical-capabilities-report%26mrm%3D696921)
