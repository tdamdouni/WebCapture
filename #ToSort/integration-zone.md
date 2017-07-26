# Integration Zone

_Captured: 2017-06-22 at 03:03 from [dzone.com](https://dzone.com/articles/restful-services-2?edition=305124&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-21)_

[Modernize your application architectures with microservices and APIs](https://dzone.com/go?i=224221&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503462%3Bdc_trk_aid%3D321267892%3Bdc_trk_cid%3D81668997%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) with best practices from this free virtual summit series. Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=224221&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503462%3Bdc_trk_aid%3D321267892%3Bdc_trk_cid%3D81668997%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

Recently, one of the most advocated means of creating services has been through the use of RESTful services. Before we continue, we would like to explain exactly what REST means and what criteria must be met before a service is indeed RESTful.

REST was a word coined by Roy Fielding in his Ph.D. thesis meaning **_Representational State Transfer._** It is an architectural design that relies heavily on the use of hypermedia to transmit information from one system to another. Its whole engine is based on the concept of Hypermedia As The Engine of Application State (HATEOAS). So, what constraints make a service a fully RESTful service? Some of the key constraints we would be looking at include:

  1. Client-Server
  2. Uniform Interface

A service is indeed RESTful if there is a separation between the client presenting the view and the server computing the logic of the application. A service is indeed RESTful provided a separation of concerns exists between the layer of the client and the server. The relationship of the client and server is such that the client and server can exist independently, communicating only through hypermedia calls and implementation. This feature makes RESTful services fundamental in today's world where the division of labor between the client and server is becoming more obvious and fundamental.

A request between a client and server must always contain all the information needed to understand the communication. Managing the state of a request has no business on the server and can only be stored on the client if need be. The server does not keep certain information about an ongoing transaction except for what is passed from the client to the server and nothing more. It has its advantages and disadvantages. The advantage in that the server is reliable in that whatever is sent to the server produces a certain type of information. Scalability is also enhanced in that the server does not store any extra information. However, the disadvantage is such that repeated information is communicated to the server every time similar information is needed.

A cache is temporary memory storage. RESTful services afford the opportunity to make some services cacheable in the client memory so that fewer calls are made to the server, as the stateless nature of the service ensures that a lot of data is communicated between the client and server. However, this becomes an issue when data becomes stale and such information is still returned to the client.

### **Uniform Interface**

Information is communicated in a standardized and uniform manner. The mode of action expected from a server by a client is usually defined in a uniform mode, and as such, different applications cannot define extra action types to the server. Such action types, like getting information from the server, updating information, and creating or deleting information on the server, are done uniformly.

This allows the RESTful services to be composed of different layers where the different layers act more like independent sections in the transmission of data from the client to the server and vice versa. Different layers can, in turn, see different forms of data and can work directly on that piece of information only. This allows for speed in some cases, but sometimes can be a cause for latency.

### **Code on Demand**

The code to execute a certain action is only available when you ask for it. As such, this makes a service really lightweight, in that only the code that is needed is used and nothing more. A function to create a certain user is only made available when a request to create a user is made.

These are some of the constraints any service that claims to be a RESTful service must always obey.

The Integration Zone is proudly sponsored by [CA Technologies](https://dzone.com/go?i=224222&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503463%3Bdc_trk_aid%3D321267794%3Bdc_trk_cid%3D81669195%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Learn from expert microservices and API presentations at the [Modernizing Application Architectures Virtual Summit Series](https://dzone.com/go?i=224222&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11298547.150503463%3Bdc_trk_aid%3D321267794%3Bdc_trk_cid%3D81669195%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).
