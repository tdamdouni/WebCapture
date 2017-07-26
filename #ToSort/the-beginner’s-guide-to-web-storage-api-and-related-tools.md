# The Beginner’s Guide to Web Storage API and Related Tools

_Captured: 2017-05-07 at 19:19 from [dzone.com](https://dzone.com/articles/the-beginners-guide-to-web-storage-api-and-related)_

Web storage is a software method and protocol used for storing data in a web browser. It is similar to HTTP session cookies, for storing name-value pairs on the client side, but with a greatly enhanced capacity. Web storage offers a storage capacity between 2MB and 10 MB depending on the browser. Check the detailed list of all the storage capacities for various browsers [here](http://dev-test.nemikor.com/web-storage/support-test/).

In this article, I will give you a brief overview of web storage API and we will go through some of the libraries or tools related to web storage.

## **localStorage and sessionStorage**

There are two kinds of storage areas within web storage:

  * **sessionStorage** that maintains a separate storage area for each given origin that is available for the duration of the page session.
  * **localStorage** is similar to sessionStorage but persists even when the browser is closed and reopened. It comes in handy for transferring data between windows or tabs, if that's required.

These storage areas are available via the [window.sessionStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/sessionStorage) and [window.localStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage) properties.

## **Storing and Reading Data**

Data is added to storage through the method _setItem()_. It takes a key-value pair as arguments. The key must be of type string, but the type of value may vary.

For example:

Alternatively, the data can be also set as follows. Note that it is recommended to use the web storage API ( _setItem()_ ) to prevent the drawbacks associated with using plain objects as key-value stores.

Data can be read from storage via _getItem()_.

We can also iterate over stored data as follows:

## **Removing Stored Data **

When we no longer need the storage data, we must explicitly remove them, especially for localStorage, as it persists even if the browser is closed. To remove individual key-value pairs, we can do as follows:

To remove all the data at once, we can use clear().

## JavaScript Libraries and Tools for Web Storage

There are several libraries and tools out there which improve the way we work with web storage APIs. Let's look at some of them.

### Proxy Storage

This JavaScript library manages an adapter that implements an interface similar to [Web Storage](https://developer.mozilla.org/en-US/docs/Web/API/Storage) to normalize the API for document.cookie, window.localStorage and window.sessionStorage.

### webStorage

This JavaScript library improves the way you work with localStorage or sessionStorage.

### ngx-webstorage

It provides an easy to use service to manage the web storages (local and session) for your ng2 application. It also provides two decorators to synchronize the component attributes and the web storages.

### h5webstorage

It is a web storage library for Angular 2 applications.

### Ember localStorage

This addon provides a _storageFor_ computed property that returns a proxy and persists the changes to localStorage or sessionStorage. It ships with an ember-data adapter that works almost the same as the JSON API Adapter with some relationship sugar added.

### vue-ls

This plugin is for working with local storage from a Vue context.

### react-native-storage

It is a local storage wrapper for both react-native (AsyncStorage) and browser (localStorage).

## Wrapping Up

Web storage does well while storing insensitive data on the client or data which do not need a frequent refresh. It's more of a balancing act wherein the ease of client-side storage is purchased at the cost of performance. Keep things as light as possible. If you wish to explore further, here are some references.
