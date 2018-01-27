# Using JWT to Secure a Stateless API World

_Captured: 2017-11-03 at 18:40 from [dzone.com](https://dzone.com/articles/using-jwt-to-secure-a-stateless-api-world?edition=334833&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-03)_

Information security is one of the most important concerns facing an increasingly connected world. And since APIs are the glue of the digital landscape, API security is more important than ever.

In this scenario, user identity and access management are core concepts to deal with. In API architectures, in particular with the emerging microservices approach, the real challenge is to enable a strong security and identity management support while keeping efficiency and reliability.

In a microservices environment, the services are scoped and deployed in multiple containers in a distributed setup, and the service interactions are frequent and remote, mostly over HTTP. In this distributed and stateless world, even user identity has to be managed in a distributed and stateless way.

What we need here is a solution that allows reliable user identity management and authorization checking without additional overhead, and using [JSON Web Tokens](https://jwt.io) (JWT for short) can be the answer,

Quoting from the [jwt.io introduction](https://jwt.io/introduction/), a **JWT** can be defined as follows:

> JSON Web Token (JWT) is an open standard ( [RFC 7519](https://tools.ietf.org/html/rfc7519)) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object. This information can be verified and trusted because it is digitally signed. JWTs can be signed using a secret (with the HMAC algorithm) or a public/private key pair using RSA. 

In a world where service-to-service communication security is a real concern, using a JSON Web Token offers many advantages:

  * **Performance and easy distribution:** The JWT representation is _compact_, and thanks to its small size, the transmission of a JWT token is fast and can be effectively performed using the HTTP protocol, for example using a URL, POST parameter, or inside an HTTP header.
  * **Efficiency:** A JWT token is _self-contained_, carrying in its payload all the identity information (including authorizations), avoiding the need to perform additional calls (for example a database query) to obtain user information.
  * **Simplicity and standardization:** JWT is an open standard and uses JSON to represent the identity information, a widely used and supported data format.
  * **Granular security:** With JWT, you can provide fine-grained resource access control.
  * **Debuggability: **JSON Web Tokens can be easily inspected, differently, for example, from an opaque API key.
  * **Expiration control**: A JWT supports an expiration time, easy to set and control.
  * **OAuth2 compliance**: OAuth2 uses an opaque token that relies on a central storage. You can return a JSON Web Token instead, with the allowed scopes and expiration.

## OK, Now Let's Get Our Hands Dirty

I'll take the simple API application example of my previous article, [Spring Boot, Jersey, and Swagger: Always Happy Together](https://dzone.com/articles/spring-boot-jersey-and-swagger-always-happy-togeth), as a starting point to show you how to use the [Holon Platform](https://holon-platform.com) to secure API operations using JWT. The [Holon Platform JWT support](https://docs.holon-platform.com/current/reference/holon-core.html#JWT) relies on the [jjwt](https://github.com/jwtk/jjwt) library to encode, decode and verify the JWT tokens.

The source code of the updated example API application can be found on GitHub, in the **jwt branch** of the **[spring-boot-jaxrs-swagger-api-example** repository](https://github.com/holon-platform/spring-boot-jaxrs-swagger-api-example/tree/jwt).

In a typical scenario, the JSON Web Tokens emission, interchange, and consumption process involves at least three actors: the **issuer**, the **protected resource**, and the **client**.

### 1\. The JWT Issuer

The **issuer **is in charge to issue a JSON Web Token as a response to a valid authentication request. This step can include the user account credentials validation.

The produced JSON Web Token can contain detailed user information, including for example user profile information and authorizations, in addition to system and validation related data, such as the issuer name and the _expiration time_. These pieces of information are called [claims](https://tools.ietf.org/html/rfc7519#section-4) in JWT terminology, and they constitute the JWT payload. In addition to the set of _reserved_ claims, you can provide a number of custom claims to represent the user identity and account information.

The issuer role can be easily interpreted by an **OAuth2 UAA **(User Account and Authentication) server, which returns a JWT instead of an opaque and randomly generated token.

In this example, we'll simulate the JSON Web Token generation by a UAA server, using the Holon Platform authentication and authorization APIs from a JUnit test class. The [Holon Platform authentication architecture](https://docs.holon-platform.com/current/reference/holon-core.html#Auth) relies on the [Authentication](https://docs.holon-platform.com/current/api/holon-core/com/holonplatform/auth/Authentication.html) interface to represent the authenticated principal (which can represent a user but also another entity). The `Authentication` structure supports permissions to represent the authorization grants and generic parameters to specify the account details.

To build a JSON Web Token from an `Authentication`, the [JwtTokenBuilder](https://docs.holon-platform.com/current/api/holon-core/com/holonplatform/auth/jwt/JwtTokenBuilder.html) class can be used. This builder will translate the `Authentication` permissions and parameters into JWT _claims_.

The JWT token builder needs to know which kind of token to build (signed or not), which algorithm has to be used to sign the token and any additional _reserved_ claim (such as the token unique id, the issuer name and the expiration time) to add to the token itself before encoding it. This information can be collected and provided to the builder using the [JwtConfiguration](https://docs.holon-platform.com/current/api/holon-core/com/holonplatform/auth/jwt/JwtConfiguration.html) interface and the Holon Platform [Spring Boot](https://projects.spring.io/spring-boot/) support can be used to build a `JwtConfiguration` using the **application configuration properties**.

To enable the Holon Platform JWT support, we just have to add the `holon-auth-jwt` artifact dependency to the dependencies section of our project's `pom`:

Now we can use a set of Spring Boot configuration properties, with the `**holon.jwt**` prefix, to auto-configure a `JwtConfiguration` instance which will be made available as a Spring component. The list of all the configuration properties is [available here](https://docs.holon-platform.com/current/reference/holon-core.html#configuration-3).

In this example, we want to setup the **issuer name** to be used, the **expiration time** and the **signature algorithm** to use. For the sake of simplicity, in this example we'll use a symmetric signing algorithm (HMAC with SHA-256), so we only need a single secret key, which has to be shared between the parties.

So you want to modify the `**application.yml**` configuration file adding the following configuration properties:

The `expire-hours` property is used to specify an expiration time of one hour, but other configuration properties are available to use a different unit of time (for example,`expire-minutesexpire-seconds`, `expire-ms`).

From now on, we can simply obtain the `JwtConfiguration` which represents these configuration properties as an injected dependency.

So, let's see an example of a JSON Web Token generation from an `Authentication` object (you can find more examples in the [ApiTest](https://github.com/holon-platform/spring-boot-jaxrs-swagger-api-example/blob/jwt/src/test/java/com/holonplatform/example/test/ApiTest.java) unit test class of the source repository):

The JWT produced in the example above will look like this:

This token can be easily transmitted using the HTTP protocol, using, for example, an `Authorization` header.

See [this example](https://github.com/holon-platform/holon-examples/tree/master/jax-rs/spring-boot-auth-jwt) for a simple JWT authorization server which issues JSON Web Tokens as the response of a POST invocation providing username and password using the HTTP `Basic` scheme authorization header.

### 2\. The Protected Resource

Now it's time to protect our API operations using JWT.

We'll leverage again on the [Holon Platform authentication architecture](https://docs.holon-platform.com/current/reference/holon-core.html#Auth), using the [Realm](https://docs.holon-platform.com/current/api/holon-core/com/holonplatform/auth/Realm.html) security abstraction and the Holon Platform Spring Boot support to allow API resources access only to authenticated clients.

We'll use HTTP **`Authorization`** header with the **`Bearer`** scheme to obtain the JWT provided by the client. The JSON Web Token will be validated according to the JWT configuration properties (checking the sign, the issuer name and the expiration time), then the JWT claims can be used to obtain the required user identity information.

We want to implement a simple _authorization_ control too, so the permission claims will be used to obtain the user roles and check if it was granted to access an API operation.

First of all, we have to setup the Holon Platform security [Realm](https://docs.holon-platform.com/current/api/holon-core/com/holonplatform/auth/Realm.html), specifying:

  * An `AuthenticationTokenResolver` to translate the JWT into an authentication token which can be interpreted by the Realm's _authenticators_.
  * The `Authenticator` which the Realm has to use in order to perform the account authentication.
  * An `Authorizer`, responsible for authorization control. The default Authorizer relies on the `Authentication` permissions to check the user authorization against the required permissions/roles.

The **`Realm`** is configured as a Spring component in the `Application` class and will be automatically located and used by the Holon Platform authorization and authentication architecture:

The `JwtConfiguration` bean is automatically created using the application configuration properties, as seen before.

Finally, we enable the API endpoint protection simply by using the Holon Platform `**@Authenticate**` annotation on the JAX-RS resource class:

The [Holon Platform JAX-RS module](https://holon-platform.com/modules/#jaxrs) automatically setup Jersey enabling the following behavior:

  * A resource method annotated with `**@Authenticate**` is only accessible by a valid, JWT authenticated, client request. If the `**@Authenticate**` annotation is declared at class level, all the JAX-RS class methods inherits the authentication setup. If the authentication is not present or not valid, a **`401 - Unauthorized`** status error response is returned.
  * The JAX-RS [SecurityContext](https://docs.oracle.com/javaee/7/api/javax/ws/rs/core/SecurityContext.html) of an authenticated request returns the [Authentication](https://docs.holon-platform.com/current/api/holon-core/com/holonplatform/auth/Authentication.html) instance associated to the request from the `getUserPrincipal()` method. The Holon Platform translates back the JWT claims into the Authentication permissions and parameters, so they can be simply accessed from the JAX-RS method.
  * The standard `javax.annotation.security.*` annotations (**`@PermitAll`**, **`@DenyAll`**, **`@RolesAllowed`**) are enabled to perform role-based resource access control, using the Authentication permissions provided by the JWT. If authorization control is not successful, a **`403 - Forbidden`** status error response is returned.
  * For more advanced authorization controls, the **`Realm`** component can be injected in the JAX-RS endpoint to leverage on the `Realm` API operations using the current `Authentication`.

For example, to declare that no role is required to access the original **`/ping`** operation, the `@PermitAll` annotation can be used:

The ROLE2 authorization is required to access the following API operation, and the JAX-RS `SecurityContext` is used (injected through the standard JAX-RS `@Context` annotation) to obtain the authenticated _principal_ name:

Finally, we add an API operation which uses the **`Authentication`** obtained from the JAX-RS `SecurityContext` to read the custom JWT claims (`"firstName"`, `"lastName"`, `"email"`) and the Holon Platform `Realm` for additional authorization control. The example response is the JSON representation of a `UserDetails` example class:

### 3\. The Client

The last actor is the **client**, which obtains the JSON Web Token from the issuer and uses it to perform the API calls, providing it as HTTP `Authorization` header `Bearer` token.

In a service-to-service communication scenario, the JWT obtained from the original API request can be passed around to perform additional **inter-service calls**. No additional overhead, such as querying the database, is needed to obtain the identity information, which is encapsulated in the JWT payload.

See the [ApiTest](https://github.com/holon-platform/spring-boot-jaxrs-swagger-api-example/blob/jwt/src/test/java/com/holonplatform/example/test/ApiTest.java) class to learn how to use the Holon Platform [RestClient](https://docs.holon-platform.com/current/reference/holon-core.html#RestClient) to perform RESTful API invocations providing the JWT as `Authorization` header `Bearer` token.

## API Documentation

In my [previous article](https://dzone.com/articles/spring-boot-jersey-and-swagger-always-happy-togeth), we've seen how to use the [Holon Platform](https://holon-platform.com)** Swagger** support to create and provide a standard API documentation. Now we want to complete the API documentation, adding the authorization information.

Let's suppose to use **OAuth2** to obtain the JWT bearer token. In this example, the OAuth2 authorization server is available at the `https://example.org/api/oauth2` URL.

Our authorization example roles (`ROLE1` and `ROLE2`) will be represented as OAuth2 _**scopes**_.

Using the standard [Swagger](https://swagger.io/) annotations, we'll add API authorization definitions in the JAX-RS endpoint class this way:

1\. Declare the API security schemes (OAuth2 in this example) using the `@SwaggerDefinition` annotation, including the available authorization scopes, then declare the authorization scheme (that we called **`jwt-auth`**) in the `@Api` annotation:

2\. Declare the authorization _scopes_ (the roles), required to access a specific API operation, in the `@ApiOperation` annotation. For example:

Thanks to the Holon platform Swagger auto-configuration, the API documentation can be obtained in JSON format from the URL:

`http://hostname:9999/api/docs`

Using the [Swagger Editor](https://editor.swagger.io/) to display the API documentation, it will appear like this:

![](https://holon-platform.com/contrib/uploads/swagger_api_example2.jpg)

The API authorization scheme can be inspected clicking on the _lock_ icons, for example:

![](https://holon-platform.com/contrib/uploads/swagger_api_example3.jpg)

## Summary

We've seen how JWT can be a lightweight and versatile alternative to other traditional authentication systems, mostly in the _stateless_ API and microservices world, and how the [Holon Platform](https://holon-platform.com) can make its implementation simple and reliable.

The source code of this example API application can be found on GitHub, in the **jwt branch** of the **spring-boot-jaxrs-swagger-api-example** repository: <https://github.com/holon-platform/spring-boot-jaxrs-swagger-api-example/tree/jwt>.

See [my previous article](https://dzone.com/articles/spring-boot-jersey-and-swagger-always-happy-togeth) to learn how to create the API example application using Spring Boot, Jersey, and the [Holon Platform JAX-RS module](https://holon-platform.com/modules/#jaxrs).
