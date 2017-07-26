# Zero Dependencies

_Captured: 2015-11-19 at 19:57 from [khanlou.com](http://khanlou.com/2015/11/zero-dependencies/)_

Last week, [I wrote](http://khanlou.com/2015/11/keeping-your-classes-shorter-than-250-lines/) about how the classes of the [Backchannel](https://backchannel.io/) [SDK](https://github.com/backchannel/BackchannelSDK-iOS) are all under 250 lines of code. This week, I'd like to discuss the experience of writing a significant application with zero dependencies.

Not having any dependencies makes it a lot easier for developers (your customers!) to incorporate your code into their project. You're assured that your dependencies won't clash with their dependencies, no extraneous weight will be added to your customer's projects, and that _your_ dependencies won't add any categories or swizzling to your customer's projects.

When I started out writing Backchannel's SDK, I had just come off the heels of releasing [Instant Cocoa](https://instantcocoa.io/), which is a library I created for reducing the intense amount of boilerplate we have to deal with as iOS developers. It includes abstractions like [data sources](http://instantcocoa.io/docs/instant-data-source/), which map index paths to objects, or [resource gateways](http://instantcocoa.io/docs/instant-model/resource-gateway/), which provide a clean interface for touching REST APIs through model objects.

I wanted to use all of this code that I had meticulously spent a year and half writing and perfecting and genericizing. However, I knew I couldn't include it. It wouldn't have been fair of me to expect other developers to import an enormous library of mine into their app just so that my development experience could be nicer.

So I turned this limitation into a feature. Not only would Backchannel not have my library, but it wouldn't have any dependencies at all. It would be a bit more work, but the developers using it would appreciate it, and that would make it worthwhile.

I had to rewrite a few of the Instant Cocoa features, like data sources. [Data sources in Instant Cocoa](http://instantcocoa.io/docs/instant-data-source/) are a lot more generic, allowing you to mix, match, and combine them in interesting ways. Since Backchannel doesn't need any of that, it was all reduced to [one simple data source](https://github.com/backchannel/BackchannelSDK-iOS/blob/master/Source/Table%20View/BAKRemoteDataSource.m), that allows for a list to be downloaded from an API, mapped to local domain objects, and presented to a table view.

Preventing Instant Cocoa from being in the project meant that the code was more tightly focused and easier to understand. `[BAKCache`](https://github.com/backchannel/BackchannelSDK-iOS/blob/master/Source/Table%20View/BAKCache.m) or `[BAKSendableRequest`](https://github.com/backchannel/BackchannelSDK-iOS/blob/master/Source/Networking/BAKSendableRequest.m) are two other examples of classes with interfaces that were limited to exactly what I wanted them to be.

Writing an application with zero dependencies means you have to take responsibility for every line of code in your app. You can't offload networking, persistence, object mapping, or any other component to someone else's code. It's just you, UIKit, and Foundation.

Backchannel was going to need Keychain access (to store the user's API access token). I didn't know much about how the Keychain API worked. I'd only heard that its API was bad, and to use something like Apple's `[GenericKeychain`](https://developer.apple.com/library/ios/samplecode/GenericKeychain/Introduction/Intro.html) to wrap it.

I set off looking for `GenericKeychain`, so that I could copy it into my project. When I found out, I realized that there's no way I could take responsibilty for that code. `GenericKeychain` is a mess, barely better than the C API it wrapped. (In a future blog post, I'm hoping to go into `GenericKeychain` as a case study of how not to write classes.) I spent about a day understanding how Apple's code worked, and wrote my own wrapper around the Keychain API, with exactly the API I wanted and the features I needed, and thus `[BAKKeychain`](https://github.com/backchannel/BackchannelSDK-iOS/blob/02a9db8776a80da8b5a78773e801a37eb09f2fc8/Source/Authentication/BAKKeychain.m) was born.

The networking API was another example of code I had to design myself. Other networking libraries couldn't be relied upon. For example, `AFNetworking` puts a category onto `UIImageView`, which could conflict with code that the developer has already written.

I turned the experience of creating a networking layer into a blog post series, analyzing what was wrong with [the currently available strategies](http://khanlou.com/2015/05/networking/), [how I structured my version](http://khanlou.com/2015/05/templating/), a follow up on advanced techniques like [pagination and mulitipart requests](http://khanlou.com/2015/07/templating-update/), and a follow up with [a Swift version of the same ideas](http://khanlou.com/2015/06/protocol-oriented-networking/). Writing my own networking code cost some development time, but I can now stand behind the code, because I wrote it and understand it fully.

A few weeks ago, Ben Sandofsky [wrote about](https://sandofsky.com/blog/third-party-libraries.html) minimizing usage of libraries. He argues for being very circumspect about which libraries you decide to import. I agree with all of his points, but I will go a step further and say that it's even more instructive to limit yourself to _zero_ dependencies. What kind of abstractions will you make when you aren't bound by the ways others have solved the same problems?

I found that I solved the problems in new and interesting ways, and many of those lessons are applicable in other apps as well. I'll almost definitely be bringing the new networking concepts to Instant Cocoa and removing its dependency on `AFNetworking`.

Making a hard rule like "no dependencies" is a great way to test the limits of your code writing ability and forces you to get creative and make some awesome stuff.

I've heard that John Carmack begins every new game he works on by writing the simple functions he needs and building everything up from little pieces. He doesn't even copy and paste his implementations from previous versions, preferring to write them from scratch. I've always been dismissive of that idea, but who knows? Maybe I'm coming around.
