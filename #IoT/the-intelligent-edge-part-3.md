# The Intelligent Edge (Part 3)

_Captured: 2017-12-19 at 17:28 from [dzone.com](https://dzone.com/articles/the-intelligent-edge-part-3)_

Learn how [Bluetooth mesh](https://dzone.com/go?i=262424&u=https%3A%2F%2Fblog.bluetooth.com%2Ftag%2Fbluetooth-mesh-networking-series%3Futm_campaign%3Dmesh%26utm_source%3Ddzone%26utm_medium%3Dpre-post-article-text%26utm_term%3Dbluetooth-mesh%26utm_content%3Ddec-pre-post-mesh-blog) helps you create industrial-grade networks. Download the [mesh overview](https://dzone.com/go?i=262424&u=https%3A%2F%2Fwww.bluetooth.com%2Fwhat-is-bluetooth-technology%2Fhow-it-works%2Fle-mesh%2Fmesh-tech%3Futm_campaign%3Dmesh%26utm_source%3Ddzone%26utm_medium%3Dpre-post-article-text%26utm_term%3Dtech-overview%26utm_content%3Ddec-pre-post-mesh-tech).

[This is a continuation of the blog series: The Intelligent Edge](https://dzone.com/articles/the-intelligent-edge-part-2).

## **Part 2: Novice App Dev: A Q&A with Greg Corey from FreeWave Technologies**

The Internet of Things (IoT) has changed the consumer world in ways no one ever imagined. By placing intelligence in the IoT network, the "Thing" can do whatever we want it to do. Now Industrial companies are seeking to take advantage of this edge-deployed intelligence in order to maximize profits, improve safety and streamline operations. In addition to the challenges IoT technology had to overcome -- such as cybersecurity, scalability, and interoperability -- Industrial IoT (IIoT) must also focus on reliability, ruggedness and more.

In the third installment -- and the second half of an interview we ran last week of "The Intelligent Edge" -- we sat down with Greg Corey, [FreeWave](http://www.freewave.com/) systems engineer, to talk about his new app -- [ZumDash](http://bit.ly/RemoteAccessDZ) -- and the future of app development of the Internet of Things.

**FreeWave**: Over the course of developing ZumDash, are there any lessons or things that you took away from it that if you could go back and do it again, you would change, or moving forward you kind of see as something that you will incorporate into future projects?

**Greg**: Yes, definitely. I've only been using this a couple months, and I've learned a lot about it. I think what's really important about Node-RED is that it empowers non-software developers to solve problems using software, and it's taught me a lot about the types of problems that you'll run into when doing software development. There are some challenges I've had to overcome in that. But, every release that I make of this app it gets better and it becomes more usable.

**FreeWave**: When you say more usable, what are some of the things that you've of tweaked to make that happen?

**Greg**: So, instead of having to change a setting in five different places, you change it in one and then you can store that setting and pull it from there. Bringing stuff to the forefront where a user can modify it instead of having to modify the code underneath. Basically, giving users more control over how the application runs and making it simpler after setup are two of the things I've tried to flip this on. Incorporating some UX/UI elements.

**FreeWave: **Are there any high-level industry points that you think are important to consider as well?

**Greg**: One thing is that FreeWave radios have always been just a radio product, and that goes for any radio manufacturer: you put data in and then it comes out the other side. And our radios have been put on sites to do just simply that task. If you look at the consumer space, 10 years ago, and you think of all the devices that we had in our lives, like a GPS navigation device, and then maybe an iPod, and a tablet, and then maybe a voice recorder or something like that. Those are like four or five different pieces of hardware that only did specific tasks.

Now, in 2017, everybody has a smartphone, nobody has an iPod anymore, nobody has a GPS navigation device anymore because they've all leveraged software on hardware on smartphones. Eventually, radio platforms are going to go the same way. In the industrial setting, people are going to buy a radio and put it out there, then they have all these other specific hardware devices to do these things. What if the radio could be that smartphone where you just leverage some software and were able to cannibalize all these other hardware-specific devices by using software just like the smartphone revolution.

**FreeWave**: So, 'things' are becoming not just smarter but they're having a greater possibility to put interactive software applications onto devices that didn't really used to have that capability?

**Greg**: Hardware has gotten really cheap and it's gotten really commodified, so any manufacturer can put together a little hardware solution in a very small form factor. The advantage anymore is not hardware anymore, it's software because a lot of these hardware manufacturers are using the same chipsets from the same vendors. And, really, the playing platform is equal if you're making just hardware, but the real secret sauce and the advantage comes in leveraging software on devices.

**FreeWave**: What about the Fog Computing aspect of this that seems to be a growing piece of the puzzle?

**Greg**: Fog Computing -- that's the paradigm where you can have these intelligent Edge devices that are making decisions instead of having everything centrally located. It's like mainframes back in the day, everything was centralized, and then we got decentralized, right? And then everybody got a laptop. And then going to the Internet of Things, and the IIoT, it's like we went back to something that was centralized, and now we're going back to the decentralized aspect, where we're thinking, "Maybe devices need to be independent and intelligent out on the Edge." It's a really broad category. It just depends on what you're looking to do in a network.

**FreeWave**: Are there any projects or anything that you're working on that you wanted to share?

**Greg**: I'm constantly improving the usability of the ZumDash right now. And then, I don't want to say too much, but we're working on a couple of projects where customers want to implement this type of technology, but we're not really ready to release names or corporate specifics about these projects.

**FreeWave**: Do you see any other interesting trends or challenges facing the Industrial IoT app development space?

**Greg**: There's this paradigm that in the future everybody will be a software developer. And the reason that everybody isn't a software developer today is because it's difficult to write code. If you put a semicolon in the wrong place or something like that, it will break the code. It's extremely detail-oriented, and it's like learning a language. It's like speaking Japanese. But in the future, we're going to make software tools that make software development easier. That way, technical people can leverage software tools to solve problems using software without actually knowing how to write the code. I think in the future everybody is going to be a software developer and using Node-RED, and OpenPLC, and other projects that we've been working on with ZumIQ.

**FreeWave**: That concept really provides perspective on a practical setting for a lot of the industry megatrends that we see all the time. Are there any specific barriers to reaching the point that you're talking about, where everyone is a software developer, that you could foresee potentially either derailing that or pushing back?

**Greg**: That's a good question. I think there are definitely software developers that will outright object to that idea in that, "It's not as simple as dragging pieces here and there and making something." And then there's the quality of code. Generally speaking, the easier you make it to do something, the less flexible it becomes. So, that could be a possible obstacle. Working in Node-RED, for example, there's a lot of stuff that I know how to do now, but there's some stuff that is really specific and it's just not that flexible in the framework to do it. I don't see any insurmountable obstacles when it comes to making software development easier. I've been a systems engineer for seven years now, and I've always wanted to solve problems theoretically. I know how some things should work from the system perspective, but I just didn't know how to write the code to make it all work, and using Node-RED I can do that.

For a deeper look into [Bluetooth mesh](https://dzone.com/go?i=262425&u=https%3A%2F%2Fblog.bluetooth.com%2Ftag%2Fbluetooth-mesh-networking-series%3Futm_campaign%3Dmesh%26utm_source%3Ddzone%26utm_medium%3Dpre-post-article-text%26utm_term%3Dbluetooth-mesh%26utm_content%3Ddec-pre-post-mesh-blog), check out this [technical insight](https://dzone.com/go?i=262425&u=https%3A%2F%2Fwww.bluetooth.com%2Fwhat-is-bluetooth-technology%2Fhow-it-works%2Fle-mesh%2Fmesh-tech%3Futm_campaign%3Dmesh%26utm_source%3Ddzone%26utm_medium%3Dpre-post-article-text%26utm_term%3Dtech-overview%26utm_content%3Ddec-pre-post-mesh-tech) for developers.

Opinions expressed by DZone contributors are their own.
