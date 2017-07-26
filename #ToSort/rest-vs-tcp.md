# REST vs. TCP

_Captured: 2017-01-31 at 04:10 from [dzone.com](https://dzone.com/articles/rest-vs-tcp?oid=twitter&utm_content=buffer42b57&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

I was going over design documents today and I noticed some common themes in the changes that we have between RavenDB 3.5 and RavenDB 4.0.

With RavenDB 3.5 (and all previous versions), we always had the communication layer as HTTP REST calls between nodes. When I designed RavenDB, REST was the thing to do, and it is reflected in the design of RavenDB itself. However, eight years later, we sat down and considered whether this is really appropriate for everything. The answer was a resounding no. In fact, while over 95% of RavenDB is still pure REST calls, we have moved certain key functions to use TCP directly.

Note that this goes in direct contrast to this post of mine from 2012 called [Why TCP is Evil and HTTP Is King.](https://ayende.com/blog/157282/why-tcp-is-evil-and-http-is-king)

The concerns in this post are still valid, but we have found that there are a few major reasons why we want to switch to TCP for certain stuff. In particular, the basic approach is that a client will communicate with the server using HTTP calls, but servers communicate with one another using TCP. The great thing about TCP is that it is a stream oriented protocol, so I don't need to carry state with me on every call.

With HTTP, each call is stateless and I can't assume anything about the other side. That means that I need to send the state, manage the state on the other side, and deal with potential issues such as concurrency in the same conversation, restarts of one side that the other side can't easily detect, repeated validation on each call, etc.

With TCP, on the other hand, I can make a lot of assumptions about the conversation. I have a state that I can carry between calls to the other side, and as long as the TCP connection is opened, I can assume that it is valid. For example, if I need to know what is the last item I sent to the remote end, I can query that at the beginning of the TCP connection as part of the handshake, and then I can just assume that what I sent to the other side has arrived (since otherwise I'll eventually get an error, requiring me to create a new TCP connection and do another handshake). On the other side, I can verify the integrity of a connection once without requiring me to repeatedly verify our mutual state on each and every message being passed.

This has drastically simplified a lot of code on both the sending and receiving ends and reduced the number of network roundtrips by a significant amount.
