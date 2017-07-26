# Web Push Notifications

_Captured: 2017-06-23 at 13:13 from [dzone.com](https://dzone.com/articles/web-push-notifications-1?edition=305129&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-22)_

[Try RAD Studio for FREE!](https://dzone.com/go?i=219227&u=https%3A%2F%2Fwww.embarcadero.com%2Fproducts%2Frad-studio%3Futm_source%3DDzone%26utm_medium%3DOnlineDisplay%26utm_campaign%3DRadStudioDzone%26utm_content%3DPostRollText) It's the fastest way to develop cross-platform Native Apps with flexible Cloud services and broad IoT connectivity. [Start Your Trial Today!](https://dzone.com/go?i=219227&u=https%3A%2F%2Fwww.embarcadero.com%2Fproducts%2Frad-studio%3Futm_source%3DDzone%26utm_medium%3DOnlineDisplay%26utm_campaign%3DRadStudioDzone%26utm_content%3DPostRollText)

Push notifications have readily been available for mobile platforms for quite some time. But push notifications for the web are still a new technology that isn't supported widely yet. At the time of writing this article, only Chrome, Firefox, and Opera supported push notifications. Safari has support for push notifications through a propriety API that is beyond the scope of this article.

So let's see how we can implement push notifications in the browsers that do support them.

## Service Workers

Before we dive into push notifications, it's important to get an idea about service workers. Service workers are basically scripts that will be run in the background by the browsers, whether the website they belong to is currently open or not. These scripts can be used for many things, but our focus is going to be on how service workers help us display the push notifications.

## High-Level Overview

Before we dive into the code, let's look at how push notifications work at a very high level. Strictly speaking, from an implementation perspective, there are 3 major components.

  1. **The Browser**. The browser provides the mechanisms to detect push notifications and display them. It will also provide cryptographic keys we can use to encrypt our message and an endpoint to which we can submit the push messages.
  2. **Backend Server**. This is where we will store the push subscription data (encryption keys and the endpoint) and submit our messages to the given push notification endpoints.
  3. **Browser Provided Endpoint**. This is an endpoint maintained by servers owned by browsers. We will submit our push messages to this endpoint.

We will go into more details when we start implementing push notifications.

## Cryptography Overview

If you are already familiar with asymmetric or public key cryptography you may skip this section, if not, please read on.

Reversible cryptography, that is where encrypted messages can be decrypted, falls into two categories.

  1. Symmetric key cryptography, also known as private key cryptography.
  2. Asymmetric key cryptography, also known as public key cryptography.

Metaphor time! Let's compare encrypting a file to locking a door. In symmetric key cryptography, there is only one key available for locking and unlocking the door. The key that's used to lock the door (encrypt the file) must be the one used to unlock the door as well (decrypt the file). This key is called a private key. If you lose that key, you can't unlock the door. If someone manages to copy your key, they can use it to unlock the door as well. The problem is this key must be kept by whoever locks the door as well as whoever unlocks the door, doubling the risk of someone stealing the key.

In asymmetric key cryptography, however, there are two keys. One to lock the door, and another one to unlock the door. The key that locks the door is called the public key. It doesn't matter who has a copy of that key because it can only lock the door, never unlock it. You can give the public key to your neighbors and their dogs and suffer no consequence. The key that can unlock the door is called (you guessed it!) the private key. It must be kept secure. The advantage here is that we can distribute the public key without any risk, we only need to secure the private key in one location.

We are using asymmetric key cryptography for encrypting our push messages when we submit them to the server.

## Implementation

Let's see how we can implement push notifications for the web. You will first need to have [npm](https://www.npmjs.com/) and [Node.js](https://nodejs.org/en/) installed in your system. The installation instructions are pretty clear and straightforward. We are going to develop a demo using the Node.js library [web-push](https://github.com/web-push-libs/web-push).

Go ahead and create a directory named `push-notifications `or any other name you want to give this project, and initialize it using npm.

Go ahead and install the `web-push` library now, we are going to need it to generate a pair of cryptographic keys later.

### Client Side

For the client side, we need three core files: a JavaScript file that will check if push notifications and service workers are supported (and basically register the service worker) and that sends the subscription information to the backend; the service worker that will be triggered when there's a push message available and display the push message as a notification; and a simple HTML file to load the main JavaScript file. Everything else (CSS, JS libraries, etc.) is just icing on the cake.

Our demo's client side is going to be a single page with a single button that will let you subscribe and unsubscribe from push notifications. If push notifications aren't supported for some reason, we will display a message in the button text and disable it.

Now, let's take a look at how these files should look.

This is just going to contain some text, and a button to subscribe and unsubscribe from push notifications. This is where our JavaScript files and libraries are loaded.
    
    
    <html xmlns="http://www.w3.org/1999/html">
    
    
        <meta name="viewport" content="width=device-width, initial-scale=1">
    
    
        <link rel="stylesheet" href="css/bootstrap-theme.min.css"/>
    
    
        <link rel="stylesheet" href="css/bootstrap.min.css"/>
    
    
        <script src="js/jquery-3.1.0.min.js"></script>
    
    
                <button class="btn btn-primary" id="btnPushNotifications" name="btnPushNotifications">
    
    
    <script src="js/main.js"></script>

As you can see, we are loading Bootstrap CSS, a jQuery library, and a JavaScript file named `main.js` in here. We will look the `main.js` file in detail later.

Let's talk about something called VAPID before we go any further. VAPID is an acronym for Voluntary Application Server Identification. This is a mechanism that lets the servers at the push notification endpoints identify you through a signed [JWT](https://jwt.io/introduction/) (JSON web token).

The web push notification specification does not address the need for any kind of a mandatory authentication mechanism. VAPID is entirely voluntary, however, in reality, only Firefox currently provides a push service without any authentication. Chrome requires either the VAPID scheme or their proprietary [FCM](https://firebase.google.com/docs/cloud-messaging/) (Firebase Cloud Messaging) authentication.

Due to the increased risk of a denial of service attack inherent in the web push notification architecture, it's not unreasonable to think authentication mechanisms similar to VAPID might become mandatory. In this demo, we will be using VAPID as the authentication mechanism to prevent any vendor lock-in with Google's FCM.

There's no need to go into the finer details on how VAPID is implemented since that will be handled by the library we are going to use. However, it's important to note that we will need a pair of asymmetric cryptography keys - a public key and the corresponding private key.

We can generate them using the library `web-push` we installed before. Now to invoke the library through the CLI you have two options: one is to use the `-g` option to install it globally and use it by invoking the command `web-push` from the CLI; or, my preferred method, use the following command:

This assumes that your current working directory is the root of your project. `node_modules` is the directory `npm` installs in all of your dependencies.

You should get an output similar to this:

This is the key pair we will be using in our project to implement the VAPID scheme, so note it down.

If you want to get more information about VAPID, you can go through the specification [here](https://tools.ietf.org/html/draft-ietf-webpush-vapid-02).

The following code snippets make extensive use of JavaScript promises. While diving into JavaScript promises is out of scope here, let's quickly go through how we can use promises so you won't be caught off guard.

A promise will resolve into success or failure, that is to say, an operation encapsulated in a promise will complete successfully or end in failure. That is denoted by `then` and `catch`methods respectively. If the operation is successful, then the function passed to the `then`method will be invoked with the designated parameters. Likewise, on operation failure, the `catch` method will be invoked with an error parameter.

#### The Service Worker

Let's look at the service worker first. The file is named `sw.js`, it's only responsibility is to display the push message once it's received in the browser.
    
    
    self.addEventListener('push', function(event) {
    
    
        if (!(self.Notification && self.Notification.permission === 'granted')) {
    
    
            data = event.data.json();

`self` refers to the service worker implicitly. We need to add an event listener to the `push`event, which will be triggered when a message is received by the browser.

We are checking if the `Notification` is available in the service worker and whether the necessary permission has been granted.

Then we use the `showNotification` method to display the notification. The `waitUntil` method prevents the browser from terminating the service worker until the operation has been completed.

Next, we want to do something when the user clicks on the notification.

We need to register an event listener to the `notificationclick` event of the service worker. In the event listener, we close the notification and open a new tab with the URL provided in the push message. As you can see, the code for the service worker here isn't very complicated.

#### Main JavaScript File

Let's call this file `main.js` (yeah it's a real surprise). This is going to be doing the majority of the work in the front-end.

Some common and UI related methods have been omitted in the following sections for brevity's sake.

#### **Requesting User Permission**

First, we need to request permission from the user to display notifications. If the user denies us permission, it's game over. Otherwise, we can proceed to registering our service worker.

#### **Registering the Service Worker and Checking for Browser Support**

Let's look at how we can check if the browser supports service workers and how we can register the service worker.

You can see the service worker states, as it is installed, in the `handleSWRegistration` method below.

Next, there are two things we need to check: one is whether the browser supports notifications on service workers; the other is whether it supports web push through the `PushManager` interface.

#### **Checking Subscription Status**

Once the service worker is ready, we get the subscription details from the `PushManager`and set the button state depending on whether the user has subscribed to the push message notifications. We can do this by using the `pushManager.getSubscription` method.

#### **Subscribing**

Let's see how we can subscribe to push notifications. We will get the subscription details from the browser's API and send it over to our backend server.

Remember the key pair we generated when we were talking about the VAPID scheme before? This is where it comes into play in the front-end. We need to provide the public key in our key pair as one of the parameters to the `pushManager.subscribe` method.

However the public key we have is encoded in [URL base64](https://en.wikipedia.org/wiki/Base64#URL_applications), we need to decode it into an Uint8Array object to pass on as a parameter to `pushManager.subscribe`.

This is the `urlB64ToUint8Array` method used to decode our public key.
    
    
        const padding = '='.repeat((4 - base64String.length % 4) % 4);
    
    
        const rawData = window.atob(base64);
    
    
        for (var i = 0; i < rawData.length; ++i) {

The next interesting snippet is how we extract the subscription details and pass it on to the backend server.

We are retrieving the endpoint we will be submitting our push messages to. It will look something like this:

Here we are retrieving the public key and the shared secret for our subscription. These will be used to encrypt the push messages before submitting them to the endpoint. We will look at the encryption algorithm in the server side development section later.

Sending these data to the backend server is a straightforward operation.
    
    
        var encodedKey = btoa(String.fromCharCode.apply(null, new Uint8Array(key)));
    
    
        var encodedAuth = btoa(String.fromCharCode.apply(null, new Uint8Array(auth)));
    
    
                console.log('Subscribed successfully! ' + JSON.stringify(response));

Note how we are encoding the public key and the shared secret (which are in bytes) into base64 format to transmit over HTTP.

#### **Unsubscribing**

Unsubscribing from push notifications programmatically is similar to subscribing, but less complex.

We need to call the `unsubscribe` method on the `swRegistration` variable, on which we stored the service worker registration object at the time of registration.

We have covered all of the important operations taking place in the `main.js` file. You can see the complete file from [here](https://github.com/thihara/web_push_notifications/blob/master/static/js/main.js)

### Server Side

Thanks to the web-push library we are using it's pretty straightforward to develop the server side application for our demo.

#### Push Message Encryption

Even though the library we are using encapsulates all the encryption details well, it' still important to understand what's happening in the backend at a high level.

If you aren't mathematically inclined it will be difficult to grasp the details of the encryption scheme. But that's perfectly alright, you can completely skip the encryption part and still send push notifications without knowing anything about the encryption algorithms supporting it.

Remember how we talked about encryption before and how we retrieved a public-key and a shared secret from our push subscription in the browser? Well, the methodology used to actually encrypt our message is called **Elliptic Curve Diffie-Hellman (ECDH) on a P-256 curve**.

Whoa! WTF is that? Well, it does sound complicated when you read it the first time around. Let's try to break it down a little bit and see if that helps.

#### **Elliptic Curve (EC) and P-256 Curve**

Elliptic curve cryptography is a family of public-key encryption algorithms based on the algebraic structure of elliptic curves over finite fields. If that algebraic nonsense went kind of over your head, don't worry, that just means a set of points that satisfy a mathematical equation.

The equation and the resulting graph looks like this.

**y2= x3\+ ax + b**

![The elliptic curve](http://thihara.github.io/images/web_push/eliptic-curve.png)

P-256 is the name of the elliptic curve used in the algorithm. It's one of the standard curves published by [NIST](https://www.nist.gov/). You can find the full list of their published curves [here](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.186-4.pdf).

#### **Diffie-Hellman (DH)**

Diffie-Hellman, or simply DH, is a protocol (method) for exchanging cryptographic keys securely over public channels. It was named after [Whitfield Diffie](https://en.wikipedia.org/wiki/Whitfield_Diffie) and [Martin Hellman](https://en.wikipedia.org/wiki/Martin_Hellman).

If you wish to learn more there's a nice post about elliptic curve cryptography [here](http://arstechnica.com/security/2013/10/a-relatively-easy-to-understand-primer-on-elliptic-curve-cryptography/).

We are using the ECDH algorithm to encrypt the message we want to send, before posting it to the subscription endpoint. The servers handling that endpoint have access to the private key of our subscription and will use it to decrypt the message and push it to the browser.

Another important aspect to keep in mind is that we need to provide the VAPID private key that matches the public key we provided in the front-end (remember when we subscribed to push notifications in the front-end?). If you provide an incorrect key, **Chrome will reject** your push notification.

You can get more information about the web push encryption scheme from [here](https://tools.ietf.org/html/draft-ietf-webpush-encryption-07).

#### Implementation

Whew, finally some solid footing. Let's go into the server implementation of our demo.

We are using node and [express](http://expressjs.com/) frameworks to build our server side application. All the subscriber data is stored in an in-memory array (this is a small demo after all) and will be lost in case of a server restart. Apart from the `package.json` file we only have one file for the server side application, `index.js`. Let's go through the code in there now.

#### **Initialization**
    
    
    let express = require("express");
    
    
    let webPush = require("web-push");
    
    
    app.use(bodyParser.json());
    
    
    app.use(express.static('static'));

We are retrieving our VAPID keys and subject from environmental variables, validating them to make sure they are actually available, and providing them to the `web-push` library. The only unfamiliar thing here is the VAPID subject field. It should be a contact URI for the application server as either a `mailto:` (email) or an `https:` URI. For example, I have my `VAPID_SUBJECT` variable set to `mailto:thihara@favoritemedium.com`.

Also, note that we are retrieving an environmental variable named `AUTH_SECRET`. You can place any value in here; you will see how it's used down the line.

The rest of the code is just initializing the `express` framework and serving all the content of the static folder (which has all the front-end files) publicly.

#### **Subscribe**

Subscribe route is simply accepting the subscription data sent from the front-end and storing them in an array. It's organizing the subscription data in the format the `web-push` library expects.

```javascript app.post('/subscribe', function (req, res) { let endpoint = req.body['notificationEndPoint']; let publicKey = req.body['publicKey']; let auth = req.body['auth'];

#### **Unsubscribe**

The unsubscribe route iterates over the subscription array and removes the element that matches the passed endpoint parameter.

```javascript app.post('/unsubscribe', function (req, res) { let endpoint = req.body['notificationEndPoint'];

#### **Notifications**

First of all, even though this is a simple demo app, we can't really let anyone who comes along send your subscribers push messages. Do you really want to see an inappropriate message on your screen (or your boss's) when some prankster gets wind of the public demo API? So we have added rudimentary validation through a header named `auth-secret`. It should contain the same value you placed in the `AUTH_SECRET`environmental variable. Otherwise, the request will be rejected with an HTTP `401` response code.

We are accepting three parameters in the `notify/all` route, and if any of them aren't present we are providing some default values.

  1. message - This is the message that will be displayed in the notification dialog.
  2. clickTarget - This is the URL we will point users to when they click the notification dialog.
  3. title - This is the title that will be displayed in the notification dialog.
    
    
    app.get('/notify/all', function (req, res) {
    
    
         let message = req.query.message || `Willy Wonka's chocolate is the best!`;
    
    
         let clickTarget = req.query.clickTarget || `http://www.favoritemedium.com`;
    
    
         let title = req.query.title || `Push notification received!`;
    
    
             let payload = JSON.stringify({message : message, clickTarget: clickTarget, title: title});
    
    
                 console.log("Status : "+util.inspect(response.statusCode));
    
    
                 console.log("Headers : "+JSON.stringify(response.headers));
    
    
                 console.log("Body : "+JSON.stringify(response.body));
    
    
                 console.log("Status : "+util.inspect(error.statusCode));
    
    
                 console.log("Body : "+JSON.stringify(error.body));

As you can see, we iterate over the subscribers array and send the notification to all the subscribers using the `webPush.sendNotification` method.

And we are finally done.

You can check out the complete source code for the demo using this [GitHub repository](https://github.com/thihara/web_push_notifications).

Quick startup instructions can be found in the README of the repository.

#### **Testing**

You can test the code by using a curl command like the one below:
    
    
    curl -G --header "auth-secret: qwertyuiop" "http://localhost:8080/notify/all" \

Or through an app like [POSTMAN](https://www.getpostman.com/docs/introduction).

## Conclusion

Now you know how to leverage push notifications in the browsers that support them. While it could be tempting to just use one of the many web push services that have popped up recently, it's not hard to implement your own service as you can see from this post.

A word of caution though, these interfaces and features are still experimental and might change without warning. If that happens, it's back to dredging through the new documentation while your production notifications suffer downtime.

Get Your Apps to Customers 5X Faster with [RAD Studio](https://dzone.com/go?i=219226&u=https%3A%2F%2Fwww.embarcadero.com%2Fproducts%2Frad-studio%3Futm_source%3DDzone%26utm_medium%3DOnlineDisplay%26utm_campaign%3DRadStudioDzone%26utm_content%3DPreRollText). Brought to you in partnership with [Embarcadero](https://dzone.com/go?i=219226&u=https%3A%2F%2Fwww.embarcadero.com%2Fproducts%2Frad-studio%3Futm_source%3DDzone%26utm_medium%3DOnlineDisplay%26utm_campaign%3DRadStudioDzone%26utm_content%3DPreRollText).
