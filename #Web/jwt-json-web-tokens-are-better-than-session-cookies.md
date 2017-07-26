# JWT (JSON Web Tokens) Are Better Than Session Cookies

_Captured: 2017-04-04 at 16:58 from [dzone.com](https://dzone.com/articles/jwtjson-web-tokens-are-better-than-session-cookies?oid=twitter&utm_content=buffer055e0&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Discover [how to focus on operators for Reactive Programming](https://dzone.com/go?i=190137&u=https%3A%2F%2Fblog.wakanda.io%2Freactive-programming-operators%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how they are essential to react to data in your application. Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190137&u=https%3A%2F%2Fwww.wakanda.io%2F).

## What Is a Token-Based Authentication System?

The token-based authentication systems allow users to enter their username and password in order to obtain a token which allows them to fetch a specific resource - without entering their username and password at each request. Once their token has been obtained, the user can use the token to access specific resources for a set time period.

JWT (pronounced 'jot') is a token based authentication system. It is a compact, URL-safe means of representing claims to be transferred between two parties. The claims in a JWT are encoded as a JSON object that is digitally signed using JSON Web Signature. The JWT is a self-contained token which has authentication information, expire time information, and other user defined claims digitally signed.

## How We Used to Do Authentication

HTTP is a _stateless_ protocol. That means it doesn't store any state from request to response. If you login for one request, you'll be forgotten and will need to login again to make another request. As you can imagine, this can get very annoying, very fast.

The old-school solution was to create what's called a "session." A session is implemented in two parts:

  1. An object stored on the server that remembers if a user is still logged in, a reference to their profile, etc.

  2. A cookie on the client-side that stores some kind of ID that can be referenced on the server against the session object's ID.

![Image title](https://dzone.com/storage/temp/4804843-flow-cookie-session-large.jpg)

This solution still works, but nowadays we have different requirements, i.e. hybrid application or single page application contacting multiple backends (split up into separate micro-service authetication servers, databases, image processing servers, etc). In these types of scenarios, the session cookie we get from one server won't correspond to another server.

![Image title](https://dzone.com/storage/temp/4804973-flow-jwt-large.jpg)

##### ![Image title](https://dzone.com/storage/temp/4805005-multiserver-jwt-large.jpg)

JWTs don't use sessions and have no problem with micro-service architectures. Instead of making a session and setting a cookie, the server will send you a **JSON Web Token **instead. Now you can use that token to do whatever you want to do with the server (that you have authorization to do).

Think of it like a hotel key: you register at the front-desk, and they give you one of those plastic electronic keys with which you can access your room, the pool, and the garage, but you can't open other people's rooms or go into the manager's office. And, like a hotel key, when your stay has ended, you're simply left with a useless piece of plastic (i.e., the token doesn't do anything anymore after it's expired).

## **Advantages of JWTs **

  1. **No Session to Manage (stateless): **The JWT is a self contained token which has authetication information, expire time information, and other user defined claims digitally signed.

  2. **Portable:** A single token can be used with multiple backends.

  3. **No Cookies Required, So It's Very Mobile Friendly**

  4. **Good Performance: **It reduces the network round trip time.

  5. **Decoupled/Decentralized: **The token can be generated anywhere. Authentication can happen on the resource server, or easily separated into its own server.

[Learn how divergent branches can appear in your repository](https://dzone.com/go?i=190138&u=https%3A%2F%2Fblog.wakanda.io%2Fanimated-git-4-understand-divergent-branches-appear-fetching-remote-repository%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how to better understand why they are called "branches". Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190138&u=https%3A%2F%2Fwww.wakanda.io%2F).
