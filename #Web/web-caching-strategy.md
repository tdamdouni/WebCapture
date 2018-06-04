# Web Caching Strategy

_Captured: 2018-05-28 at 21:35 from [dzone.com](https://dzone.com/articles/web-caching-strategy?edition=380195&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-05-28)_

Deploying code to production can be filled with uncertainty. Reduce the risks, and deploy earlier and more often. [Download this free guide](https://dzone.com/go?i=278435&u=https%3A%2F%2Ftry.rollbar.com%2Flow-risk-continuous-delivery-guide%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\)) to learn more. Brought to you in partnership with [Rollbar.](https://dzone.com/go?i=278435&u=https%3A%2F%2Frollbar.com%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\))

I am currently designing a high performant IoT solution for one of my clients. This system is also going to expose internal APIs to their clients so that they can build their systems/apps on top of it.

There will be web applications which means they will be consuming near-static/dynamic endpoints serving the data requirements. To reduce latency and enhance scalability, HTTP caching is one of the techniques I am proposing. In this article, I am going through some of the known terminologies which all of us think about while designing such systems.

I have replaced the client's system name in this document, for obvious reasons, with 'Beehive.'

## HTTP Cache

HTTP caching allows us to cache the full output of a request and bypasses the application for subsequent requests. However, caching entire responses isn't always possible even for near-static datasets.

Which means, not every response from Beehive's API endpoints are cacheable and the API specification document indicates that. Beehive employs an "Entity Tags" based caching approach when there is no shared agreement on time.

### Cache-Control

Beehive API responses use the following four cache-control headers.

#### "no-store"

No browser or intermediate caches.

#### "no-cache"

"no-cache" indicates that the browser should validate with the server if the cache is still up-to-date.

#### "max-age"

"max-age" sets the counter from now as TTL for the response. For example, "max-age=60" indicates that the response can be cached and reused for the next 60 seconds.

#### "last-modified"

"last-modified" specifies the time when the server believes that the resource was last modified.

### Conditional Requests

In these instances, the browser asks the server if the response has been updated. The browser sends some information about the cached resource and the server determines where the updated content should be returned or if the browser's copy is the most recent. When the latter is true then HTTP status code 304 is returned.

Beehive uses both time- and content-based conditional requests. For near-static datasets, a time-based conditional request is used, whereas, for dynamic datasets, content-based conditional requests are used.

### Near-Static Datasets: Time-Based Requests

For near-static datasets which live for sufficiently long periods of time, Beehive uses time-based conditional requests. APIs will use the "last-modified" cache control. If the cached copy is the latest copy of the data then the server returns the 304 status code.

To use conditional requests, the server specifies the last modified time of a resource using the `Last-Modified` response header.

On the next request, the browser sends the Last-Modified value as an `If-Modified-Since` request header.

If the resource has not been modified since Thu, 24 May 2018 12:45:57 GMT, then the server returns an empty body with the 304 response code.

### Caching Dynamic Datasets: Content-Based Requests

Each cacheable API endpoint uses one of the two Cache-Controls - "no-cache" or "max-age=?" -alongside an entity tags header. Entity tag headers allow the server to identify if the cached contents of the resource are up-to-date or not.

#### "Entity Tags": Validation Token

Entity tags are used to communicate a validation token to the HTTP client. The server generates a validation token which is the hash of the response payload and sends the validation token as an entity tag header. The client sends back the validation token in the `If-None-Match` HTTP request header.

Let's assume the response payload is "{"payload": "empty-payload"}" then the md5 hash of the payload will be 7b982db9faa6611afd5d375619fee5a0.

The server will send the hash with the response as an ETag header.

On subsequent requests, the browser will send an `If-None-Match` request header with the ETag value.

If the latest resource has the same ETag server, it will return an empty payload with a 304 HTTP status code.

## Negative Caching

Beehive caches these 3xx, 4xx, and 5xx responses:

Deploying code to production can be filled with uncertainty. Reduce the risks, and deploy earlier and more often. [Download this free guide](https://dzone.com/go?i=278436&u=https%3A%2F%2Ftry.rollbar.com%2Flow-risk-continuous-delivery-guide%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\)) to learn more. Brought to you in partnership with [Rollbar.](https://dzone.com/go?i=278436&u=https%3A%2F%2Frollbar.com%2F%3Futm_source%3Ddzone%26utm_medium%3Ddisplay%26utm_campaign%3Ddzone\(q118\))

Opinions expressed by DZone contributors are their own.
