# REST (representational state transfer) definition

_Captured: 2015-12-17 at 00:03 from [searchsoa.techtarget.com](http://searchsoa.techtarget.com/definition/REST)_

REST (REpresentational State Transfer) is an architectural style, and an approach to communications that is often used in the development of [Web services](http://searchsoa.techtarget.com/definition/Web-Services-Glossary). The use of REST is often preferred over the more heavyweight [SOAP](http://searchsoa.techtarget.com/definition/SOAP) (Simple Object Access Protocol) style because REST does not leverage as much bandwidth, which makes it a better fit for use over the Internet. The SOAP approach requires writing or using a provided server program (to serve data) and a client program (to request data).

![](http://cdn.ttgtmedia.com/downloadOffers/images/App-Integration_CTD.png)

REST'S [decoupled architecture](http://whatis.techtarget.com/definition/decoupled-architecture), and lighter weight communications between producer and consumer, make REST a popular building style for cloud-based [APIs](http://searchexchange.techtarget.com/definition/application-program-interface), such as those provided by [Amazon](http://whatis.techtarget.com/definition/Amazon), [Microsoft](http://searchwindowsserver.techtarget.com/definition/Microsoft), and Google. When Web services use REST architecture, they are called [RESTful APIs](http://searchcloudstorage.techtarget.com/definition/RESTful-API) (Application Programming Interfaces) or REST APIs.

REST architecture involves reading a designated Web page that contains an [XML](http://searchsoa.techtarget.com/definition/XML) file. The XML file describes and includes the desired content. Once dynamically defined, consumers may access the [interface](http://whatis.techtarget.com/definition/interface).

REST, which typically runs over [HTTP](http://searchwindevelopment.techtarget.com/definition/HTTP) (Hypertext Transfer Protocol), has several architectural constraints:

1\. Decouples consumers from producers

2\. [Stateless](http://whatis.techtarget.com/definition/stateless) existence

3\. Able to leverage a [cache](http://searchstorage.techtarget.com/definition/cache)

4\. Leverages a layered system

5\. Leverages a uniform interface

REST is often used in mobile applications, [social networking](http://whatis.techtarget.com/definition/social-networking) Web sites, [mashup](http://whatis.techtarget.com/definition/mash-up) tools, and [automated business processes](http://searchcio.techtarget.com/definition/business-process-automation). The REST style emphasizes that interactions between clients and services is enhanced by having a limited number of operations (verbs). Flexibility is provided by assigning resources (nouns) their own unique [Universal Resource Identifiers](http://searchsoa.techtarget.com/definition/URI) (URIs). Because each verb has a specific meaning (GET, POST, PUT and DELETE), REST avoids ambiguity.

There are some downsides. In the world of REST, there is no direct support for generating a client from server-side-generated [metadata](http://whatis.techtarget.com/definition/metadata). SOAP is able to support this with [Web Service Description Language](http://searchsoa.techtarget.com/definition/Web-Services-Description-Language) (WSDL).

REST provides the following advantages, specifically advantages over leveraging SOAP:

  * RESTful Web services are easy to leverage by most tools, including those that are free and inexpensive. REST is becoming the dial tone for systems interaction, including the use of RESTful Web services, which are, for the most part, the way [cloud providers](http://searchcloudprovider.techtarget.com/definition/cloud-provider) externalize their [cloud services](http://searchcloudprovider.techtarget.com/definition/cloud-services).
  * SOAP services are much harder to scale than RESTful services. Thus, REST is often chosen as the architecture for services that are exposed via the Internet (like [Facebook](http://whatis.techtarget.com/definition/Facebook), [MySpace](http://whatis.techtarget.com/definition/MySpace), [Twitter](http://whatis.techtarget.com/definition/Twitter), and most [public cloud](http://searchcloudcomputing.techtarget.com/definition/public-cloud) providers).
  * The learning curve seems to be reduced. Developers are able to make use of REST from within applications faster than they can with SOAP. This saves time, which saves money.
  * REST uses a smaller message format than SOAP. SOAP uses XML for all messages, which makes the message size much larger, and thus less efficient. This means REST provides better performance, as well as lowers costs over time. Moreover, there is no intensive processing required, thus it's much faster than traditional SOAP.
  * REST is designed for use over the Open Internet/Web. This is a better choice for Web scale applications, and certainly for cloud-based platforms.

Moving forward, REST is likely to continue its growth as enterprises seek to provide open and well-defined interfaces for application and infrastructure services. The growth of public and private [cloud computing](http://searchcloudcomputing.techtarget.com/definition/cloud-computing) is driving much of this demand, and will continue to drive growth into the future.
