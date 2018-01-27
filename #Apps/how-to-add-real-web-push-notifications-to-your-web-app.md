# How to Add Real Web Push Notifications to Your Web App

_Captured: 2017-11-28 at 09:56 from [dzone.com](https://dzone.com/articles/how-to-add-real-web-push-notifications-to-your-web?edition=337920&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-11-27)_

You've probably seen web notifications before. YouTube shows them when it goes to a new song, Facebook pings them when a new message comes in, scammy websites ask for permissions and you say no. The usual.

You can fire those notifications from anywhere inside your JavaScript.

That creates a new browser notification and shows it to the user. Since Chrome 60-something on a Mac, they're integrated with native notifications. It's great.

![](https://d3nulzlctd9uky.cloudfront.net/blog/wp-content/uploads/2017/11/Screen-Shot-2017-11-16-at-09.37.29.png?x24020)

You can close the browser notification with `notification.close`, and you can listen for click events with `notification.onclick = () => ...`. Most often you'd want to use that click event to focus on your browser tab.

To make this work, however, the user must keep your web app open and you must keep your fingers crossed that the browser hasn't throttled your JavaScript too much for inactivity. Browsers do that, you know.

But did you know you can also add _real_ push notifications to your web app? The kind that comes from a server and works even with no open tabs? Oh yes, just like a mobile app.

I had no idea this has been part of Chrome since version 40-something. Firefox supports it, too. Safari and Internet Explorer, no.

It is not a part of the JavaScript standard yet. [MDN lists web push notification support as experimental](https://developer.mozilla.org/en-US/docs/Web/API/Push_API).

Here's what you'll need to make it work:

  * A service worker.
  * Some code to register the service worker.
  * Some code to ask for notification permissions.
  * Bit of code to subscribe to web push notifications.
  * A server to trigger the push notification.

## Service Worker That Listens for Push Events

You can think of service workers as a piece of JavaScript that lives in your user's browser and does stuff. They can do stuff even when your site isn't loaded, or even open.

Most commonly they're used for caching in what's called progressive web apps - PWA. They intercept requests and serve code from a local cache. Even if the browser is offline.

But none of that right now. We're using them for push notifications.

A service worker will live in our user's browser and listen for `push` events. The browser gets these events from a so-called push service, triggers the service worker, and our service worker does whatever.

For security reasons, we can't control _which_ push service the browser uses. The browser tells us instead. You'll see how in the section about subscribing.

For privacy reasons, we also have to accept a sort of gentleman's agreement with the browser where we promise to always show a notification when a push event comes in.

So... a service worker is just a JavaScript file. Nothing fancy going on. You use `self` to refer to the global scope because there's no `window` and no `document`.
    
    
            const { body, title, tag } = JSON.parse(event.data.text());
    
    
                        .showNotification(title, { body, tag, icon })

That's all the code that goes into our service worker.

In `showNotification`, we return a `Promise` that resolves once we're done showing our notification.

We use `JSON.parse` to unpack notification parameters using the convention of putting JSON into the `message` portion of our push notification.

Before showing our push notification with `self.registration.showNotification`, we can clear any existing notifications with the same `tag` using `self.registration.getNotifications`. This gives us a list of notifications that we can `.close`.

I've noticed (at least on a Mac) that subsequent notifications with the same `tag` sometimes don't show up unless you close the previous ones.

We use `self.addEventListener` to listen for both `push` and `onclick` events. In the push handler, we call `showNotification` to show our web push notification, and in `notificationclick` we open our site.

That's the service worker!

## Register the Service Worker

Registering said service worker happens in our regular JavaScript code. Usually in the main `index.js` entry point because there can be only one service worker for an entire domain.
    
    
            .catch(e => console.error("ServiceWorker failed:", e));

We call `navigator.serviceWorker.registe` with the URL of our service worker and wait for the promise to resolve. If all goes well, we print a success message, otherwise, we print an error.

This is not a piece of code you'll have to write often. Once per project at most. Many just find it online and copypasta when they need it, I think.

One caveat to keep in mind is that service workers are limited to the scope they're served from. You can't serve that file from a CDN, or from a `static.domain.com`, or even `domain.com/static/`.

This is a security precaution.

My solution was to use the Webpack `[sw-loader`](https://github.com/idiotWu/sw-loader) and configure it to compile this particular file into a different location and with a different publicPath than all other JavaScript, which goes into CDNs and has fingerprinting and stuff.

That part was tricky, but it's very specific to every web app, so it's not a good candidate for this article.

## Ask for Web Notification Permissions

If you've ever used web notifications before, you already know this part: you have to ask the user for permission.

Here's how that goes:

Yep, that's it.

Running `Notification.requestPermission` pops up a little dialog for our user asking them to grant us web notification permissions. If they do, the permission is set to `granted`. Other options include `denied`, and I think it stays null if they ignore us.

You can check permission status at any time with `Notification.permission`.

## Subscribe to Web Push Notifications

Here comes the interesting part: subscribing to web push notifications. This is where we ask the browser, _"Hey, which push service do you wanna use?"_

The process has 2 to 3 steps depending on how you count:

  1. Create VAPID keys for our server, one-time.
  2. Ask browser to subscribe.
  3. Save subscription info for our user.

[VAPID keys](https://blog.mozilla.org/services/2016/04/04/using-vapid-with-webpush/) are a way for our server to identify itself with the push service. That way our user's browser can be sure that push notifications are coming from us and not from some random spammer who got in the way.

I used the `[Webpush`](https://github.com/zaru/webpush) gem to generate these keys, there's a `[web-push`](https://github.com/web-push-libs/web-push) package for node as well.

You will have to send the `public_key` to your frontend somehow because you'll need it to subscribe to web push notifications. The subscription itself happens like this:

We call `registration.pushManager.subscribe` to subscribe with our `applicationServerKey`. That's the `vapid.public_key`. And as I mentioned earlier, we promise to always show a notification with `userVisibleOnly: true`.

Not a single browser currently supports `userVisibleOnly: false` because it could lead to privacy issues. Think about sending a push and having your service worker send back a detailed GPS location for your user. No bueno.

That `pushSubscription` will have a bunch of data inside. Everything from which API endpoint to use when sending notifications to info about how to authenticate with the service.

The browser is in full control.

You should save that info on the backend and associate it with your user. As far as I can tell, it's unique for every subscription request and definitely for every browser.

The tricky part here is when the same user is using multiple browsers and devices. If you want to send push notifications to all of them, you're going to have to keep multiple copies of this info.

## Trigger a Web Push Notification

To trigger a web push notification from your server, I suggest using a library. Something like [Webpush for Ruby](https://github.com/zaru/webpush) or [web-push for node](https://github.com/web-push-libs/web-push). I'm sure libraries exist for other languages as well.

Here's how you'd send a notification in Ruby/Rails:

We use a database JSON field called `web_push_subscription` to save the `pushSubscription` info on our users.

If that field has info, we can use `Webpush` to send a notification to the API. The API then sends it out to our service worker, which then shows a notification.

## Fin

You should now be able to add web push notifications to your web app. I left out some details on setting up Webpack to serve service worker code correctly, but we can get into that some other day.

If you do decide to add push notifications to your web app, please use them responsibly. Remember what happened to mobile app notifications and what a mess that has become.

Wouldn't want to train users to automatically deny notification permissions, now, would we?
