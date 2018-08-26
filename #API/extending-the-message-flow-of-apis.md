# Extending the Message Flow of APIs

_Captured: 2018-05-01 at 16:14 from [dzone.com](https://dzone.com/articles/extending-the-message-flow-of-apis-1?edition=376228&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202018-05-01)_

[Site24x7](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

The Gateway of an API Manager deployment is responsible for the main business functionality of serving API traffic. The following diagram illustrates the typical message flow in the Gateway at a very high level.

![](https://lh4.googleusercontent.com/LbsCo3UiNBrUDRzKiq0K6ZDq-We1b732mOmowO5QrWw8Xm2wiSHga242OTv8a3x0KF7jMygO6DNdhJKDlTg0Pjzf6PNms6qtRNfIxGoFs-gfyNhD1CXTiBOA-evufAVfp2dygCNr)

If you are lucky the backend service will match exactly the request and responses of your designed API, but in the real world, it is not always the case. It may be required to change the default behavior of your API to meet changing and new requirements which you may have. Now what would come to your mind is that you would ideally need to write some code or change your backend service or change your front end logic to match such requirements, which is a hassle for any developer or organization. So how can you change the behavior of the API to satisfy your API consumers without having to write code?

The answer you are looking for is a method in which you can extend the default message flow of APIs, referred to as message mediation. If I describe the term "message mediation" it can be identified as a custom logic or a set of policies which have been custom designed to enable you to add common types of management capabilities to your APIs without having to modify your consumer application logic or your backend service. Let's identify some common example scenarios where message mediation would be useful for API designers. I will order them according to the complexity level. The use of these will vary depending on your requirement.

### Simple Use Cases

  * **Request/Response header manipulation** - This is useful when we do not want to manipulate the message body but only need to add/remove headers from the request and response to meet certain criteria of the front end application or backend service.
  * **Adding custom properties to the requests on the fly** - This is useful when you need to set additional properties while making the requests. For example, these properties will be the ones which are not taken from the user as input but what are actually needed by your backend service to be passed from the front end.
  * **Passing additional authorization to backend services** - If you need to include additional authorization headers which are required to authenticate your backend service then you will need the support for this to happen on the fly.
  * **Changing the message type of your request/response message** - For example, if you want to change the format of your message from XML to JSON on the fly or vice versa.

### Moderately Complex Use Cases

  * **Extracting, transforming or replacing the contents of a message** - This is useful when you want to completely change the format and contents of your request or your response. If there is a mismatch between the payload which the API consumer will send and what the backend service expects then this kind of transformation will be useful. Or in some cases, if the response sent from the backend needs to be transformed to satisfy the API consumer then also this kind of transformation will be useful.
  * **Request/Response input data validation** - Normally we do not have a control of the input which the consumers will send to our API. In that case, we need to verify the input or validate the input before we pass it on to the backend.
  * **JSON/XML schema validation** - When we need to validate JSON and XML schema to mitigate attacks and incorrect data to our APIs.
  * **Customizing backend error messages** - There may be instances where you need to overwrite the error messages returned from the backend to a more meaningful and user-friendly ones which will be returned to your API consumers. This will support a good API design.
  * **Disabling Chunking** - Some back-end servers do not accept chunked content. When you need to disable chunking before it reaches your backend this is useful.

### Advanced Use Cases

  * **Filtering messages** - When you need to filter your messages based on a set of conditions before routing to your backend.
  * **Orchestration of multiple backends using a single API -** If you have multiple backends which you require to expose using a single API. In this case based on a condition (header, property, input values) It will route to the required backend.
  * **Service Chaining** - This can be classified as one of the more advanced use cases of extending the message flow. What happens here is you require the response from an intermediate service to make the actual request to your backend service. In these kinds of scenarios, there is a much heavier transformation than the above use cases and it is recommended to utilize the "API Facade Pattern" rather than performing these transformations at the gateway. You can read further on how to achieve these kinds of heavy transformations using the API Facade [pattern](https://wso2.com/library/blog-post/2015/10/article-a-pragmatic-approach-to-the-api-facade-pattern/) here.

In order to understand how to extend the message flow of APIs in the real world, let's take an example from the moderately complex section above and look at it in detail. In this example, I will elaborate how message mediation is useful when you need to manipulate the message body being sent or received from the backend service.

## Example Use Case

#### Background

  * Your backend service returns details of a country based on a country code which you pass. The backend response is a highly elaborate response about all the country's details.
  * Your backend is only capable of returning the response in XML format.

#### What we need to achieve

  * The end user needs the response to only contain the country name being referenced by the country code and its region, omitting all other details returned in the response.
  * The end user wants the response format to be the content type which he/she request. If he/she requests for JSON, then the API should return the response in JSON. If they request it to be XML then it should return it in XML, irrespective of the format the backend service returns.

The extension to the default message flow is represented in the diagram below. This can be easily achieved without you having to change either the front end application logic or the backend service logic by following the steps in this [tutorial](https://medium.com/@shenavi21/transforming-the-response-of-an-api-on-the-fly-65f8bad57a73). For other examples of how to extend the default message flow of APIs you can refer this [message mediation cookbook.](https://docs.wso2.com/display/APICloud/Message+Mediation+for+WSO2+API+Cloud)

![Image title](https://dzone.com/storage/temp/8882273-blog-post-extending-the-message-flow-of-apis.jpg)

API Management platforms of the current era need to support the capability of being able to extend the normal message flow of API requests without the developers needing to write complex code. In the real world, with changing requirements, it is almost close to impossible for consumers and developers to facilitate their implementation to support all the changing use cases. In such situations being able to extend the message flow of APIs on the fly is essential for any API Management platform and something which I believe every API developer needs to incorporate to their APIs for a better end user experience.

[Site24x7](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

Opinions expressed by DZone contributors are their own.
