# How Single-Page Applications Influence Page Speed

_Captured: 2017-05-12 at 00:37 from [dzone.com](https://dzone.com/articles/how-single-page-applications-influence-page-speed?oid=twitter&utm_content=bufferbf0ac&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Discover 50 of the latest mobile performance statistics with the [Ultimate Guide to Digital Experience Monitoring](https://dzone.com/go?i=180148&u=http%3A%2F%2Fpages.catchpoint.com%2FDigital-Experience-Monitoring-Ebook.html%3FLSD%3DREF-DZONE), brought to you in partnership with [Catchpoint](https://dzone.com/go?i=180148&u=http%3A%2F%2Fpages.catchpoint.com%2FDigital-Experience-Monitoring-Ebook.html%3FLSD%3DREF-DZONE).

Given the rise of Single-Page Applications (SPA), along with the much wider use of asynchronous HTTP requests in general for web pages, it's more difficult to determine how page loading times affect overall user experience on a website. These newer techniques for delivering content offer a different type of interaction than in the past when a user would load one web page and certain interactions (such as clicking a link) would simply load another web page to deliver the new content.

When resources were simply loaded up front, the overall time for the page to load was easily measurable with a single timing test. As things have progressed; however, this metric alone may be less meaningful for sites or apps that make heavy use of asynchronous calls to retrieve additional content as the user interacts with the page.

## Advantages of Single-Page Applications

A traditional page load simply loads all of the assets a web page will need up front (though some may be seen more quickly than others). The measure here is simple, though - the _load_ event in JavaScript is triggered when all of the requested assets have loaded. These assets can include the HTML itself, cascading style sheets (CSS), JavaScript code, images, and other media.

![](https://coschedule.s3.amazonaws.com/52932/881b7e41-dafa-41be-a89b-abfe1c674a48/client-server-sync.png)

_A typical HTTP request, which must be done for each asset that needs to be loaded (Source: [MDN](https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms/Sending_and_retrieving_form_data))._

As JavaScript became more and more popular for developing additional interaction for the user without the need to load another page, some further innovations were made. Anything from switching out which image was displayed to showing and hiding pieces of content became commonplace. However, these were often done by having all of the content loaded with the page itself, so the traditional model for page loading time was still effective.

> In fact, on certain sites like Twitter, there is nothing displayed on the screen when the on-load event fires in the browser. -- [Craig Tobe, ConstantContact](http://techblog.constantcontact.com/software-development/measure-page-load-times-using-the-user-timing-api/)

Modern websites and apps may load little or no content before the load event occurs. This causes the traditional loading time to be excellent but does not tell the entire story of what the user may experience. With the content loaded later, it is those later loading times that may make a difference in how fast the user ultimately feels the site is.

## Disadvantages of Single-Page Applications

> It can take several seconds for a mobile browser to receive the first byte on a mobile device and we only have three seconds to get the content to the user before up to 40% of them abandon the request. -- [Matt Shull on DWB](https://davidwalsh.name/measuring-performance)

In web development today, many choose to use some form of asynchronous behavior. Part of this is that it can help keep users from loading unnecessary resources until they are wanted or needed, which is certainly helpful for improving initial load times. However, in such cases, the testing cannot stop there, as the loading time of one of the subsequent requests could cause the user as much frustration as a slow initial page load.

For example, it could be handy to wait to load a list of nearby store locations until the user enters some information and requests the list. If done the traditional way, the loading of the subsequent page can be easily tested. However, if this list is loaded on the same page after the initial page load, this additional load time may not be accounted for in the quickness of loading on the site. If this takes more than a couple of seconds, it could cause the user to want to move on to another site just as a with a slow initial page loading time.

As you can see, even though the initial loading time may be excellent, it would also be helpful to be able to test subsequent asynchronous loading times to ensure that all loading time are fast, not just the initial site or app load.

## How to Optimize Single-Page Applications

In addition to initial page loading, websites and apps that use asynchronous calls will likely need further testing to ensure those additional requests are also loading quickly. The User Timing API, documented on [MDN](https://developer.mozilla.org/en-US/docs/Web/API/PerformanceTiming), is a feature in modern web browsers that will allow you to access some information you can use to test the speed of various user interactions by providing you with helpful information and functions to do so.

This API allows you to set up marks that can be measured for the time it takes for any number of asynchronous request to complete. As you can see, this could come in handy for testing load times that occur after the initial page load and help you provide an even better experience for your users. Indeed, such testing may help discover an issue that could be helped with some load balancing, autoscaling, or other features that are easily set up in the cloud.

[Is your APM strategy broken?](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE) This [ebook](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE) explores the latest in Gartner research to help you learn how to [close the end-user experience gap in APM](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE), brought to you in partnership with [Catchpoint](https://dzone.com/go?i=180149&u=http%3A%2F%2Fpages.catchpoint.com%2FGartner.html%3FLSD%3DREF-DZONE).

### Like This Article? Read More From DZone
