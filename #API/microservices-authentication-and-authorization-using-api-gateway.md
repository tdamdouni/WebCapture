# Microservices Authentication and Authorization Using API Gateway

_Captured: 2018-02-28 at 16:16 from [dzone.com](https://dzone.com/articles/security-in-microservices?edition=364101&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-02-28)_

Whenever we think of microservices and distributed applications, the first point that comes to mind is security. Obviously, in distributed architectures, it is really difficult to manage security as we do not have much control over the application. So in this situation, we always need to have a central entry point to this distributed architecture. This is the reason why, in microservices, we have a separate and dedicated layer for all these purposes. This layer is known as the API Gateway. It is an entry point for a microservice's architecture.

To maintain security, the first necessary condition is to restrict direct microservice calls for outside callers. All calls should only go through the API Gateway. The API Gateway is mainly responsible for authentication and authorization of the API requests made by external callers. Also, this layer performs the routing of API requests that come from external clients to respective microservices. This allows the API Gateway to act as an entry point for all its respective microservices. So, we can say the API Gateway is mainly responsible for the security of microservices.

### **Authentication**:

We can use an OAuth delegation approach inside the API Gateway to perform authentication for each microservice call. Mainly, whenever a user sends credentials for authenticating their identity, the API Gateway will forward these credentials to the OAuth server, and, if the user is authenticated, then we will get the token from the OAuth server. Once the token from the OAuth server is obtained, the API Gateway will then store this token in some in-memory database such as Redis, Memcache, etc., along with its expiry time.

This saved token is sent back to the external client as a valid token for further API calls. Whenever an external caller makes a call to the microservice through the API Gateway, we have `AuthenticationFilter` which will get the token from the external caller and check for the validity of the token in the Redis database. And, if the token is not valid then an exception is thrown with the message, 'token is invalid.'
    
    
      TokenDetails tokenDetails = (TokenDetails) gson.fromJson(jsonTokenDetails, TokenDetails.class);

In this way, we can perform authentication protocols for each API call in the microservice's architecture through the API Gateway.

### **Authorization:**

So now we have successfully completed the authentication part for the external caller and verified their identity, but another major problem remains: authorization. Authorization is used to determine whether the user is actually allowed to have access to the API, depending on their role, access rights, etc. So to handle this type of security for each API, we need to have one more filter (`AuthorizationFilter`) in the API Gateway to validate the accessibility of the APIs. In this type of filter, we can use the Redis database which stores the API's list of applications and its allowed roles permissions list. So, by getting the appropriate role permissions for the API, and validating the user's role, we can compare and then decide whether to allow the user to call the API or not.

For both authentication and authorization, all calls need to go through the API Gateway and the individual microservices should be hidden from the outside world to make them secure. So by using the two methods described above, we can implement security protocols in our microservices where the API Gateway will play an important role.

We can also add more layers of security in our microservices as per our need at each level, which needs to be covered in depth in conjunction with a topic such as Spring Security.
