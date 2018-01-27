# The Intelligent Edge (Part 1)

_Captured: 2017-12-19 at 17:26 from [dzone.com](https://dzone.com/articles/freewave-blog-series-the-intelligent-edge)_

[Download Red Hat's blueprint for building an open IoT platform](https://dzone.com/go?i=250323&u=https%3A%2F%2Fwww.redhat.com%2Fen%2Fresources%2Fintelligent-systems-solution-internet-things)--open source from cloud to gateways to devices.

The Internet of Things (IoT) has changed the consumer world in ways no one ever imagined. By placing intelligence in the IoT network, the "Thing" can do whatever we want it to do. Now Industrial companies are seeking to take advantage of this edge-deployed intelligence in order to maximize profits, improve safety and streamline operations. In addition to the challenges IoT technology had to overcome such as cybersecurity, scalability, and interoperability, Industrial IoT (IIoT) must also focus on reliability, ruggedness and more.

In the first edition of "Making Waves," we at FreeWave sat down with Jesse Steiner, FreeWave systems engineer, to discuss how he is helping industrial customers understand the power of deploying intelligent applications in an industrial network.

**FreeWave: We're starting this blog series to interview people who are contributing new applications and ideas for IIoT environments. You have an interesting story to tell around that -- can you share that with us?**

Steiner: Sure -- so I started getting involved with IoT apps once we released ZumIQ, the App Server Software platform that is deployed on our ZumLink 900 Series radios. I don't have a whole lot of programming experience -- I've used a handful of different languages at a pretty novice level over the years.

The first thing I used it for was to write a simple app to monitor the level in the water tank out at a remote ranch location that wasn't often manned. It was the second property for the ranch owner. He had this big water tank, 22,000 gallons, that he needed to keep an eye on the level because it provided irrigation water, drinking water, bathing water, all that. He'd had issues in the past where the circuit breaker on the pump tripped, or had a leak, and he went out to his second property to find he had no water to use. So we took a ZumLink 900 Series radio with ZumIQ, wrote an application for it that would pull a sensor for the level in the tank, it would format that data, and then send it over the radio network to the internet and to the cloud, and then to the ranch owner so he could look at his water tank anywhere. It was really done as proof of concept, and as a learning exercise for me, but it's been deployed for a month, month and a half maybe, and it's already proven very useful on multiple occasions

**FreeWave: So how did you write the app?**

Steiner: I don't want to call it a programming language, but I used a programming environment called Node-RED. It's basically a graphical interface to Node.js. It's a graphical thing where you lay these function blocks down and connect lines but you've also got the ability to write your own Javascript code that gets inserted and run in that environment.

From there, it got sent to a cloud hosting service called dweet.io, which is really good for very beginner use -- it doesn't require any advanced IT knowledge or programming knowledge and you can get data in there and store it really quickly. And for actually viewing it, I used a service that's owned by the same company as dweet called freeboard.io. You basically build a dashboard and point it towards the data you have stored in dweet, and it will pull that out and display it in a graphical way.

**FreeWave: What other applications could the tank level monitoring be used for?**

Steiner: That application caught the eye of the company who installed the pump and tank system out at that property in the first place, and they've since reached out us and said, "Hey, we're interested in this. We'd like to see if we could develop it further." As FreeWave, we're not selling the software or any of the service. But we did provide the radios and pretty much the same code that we had used before to this company, so they can develop something that would be more than proof of concept -- really, a marketable software product where you could choose the number of tanks, monitor multiple tanks of different sizes, keep an eye on pump status, potentially control the status of pumps and valves -- really for a whole monitoring and control system when it comes to remote irrigation.

What that comes down to is intelligence, monitoring, and control in remote locations, where is kind of where FreeWave has been used for 20 years out in the oilfields.

**FreeWave: Any sort of learnings you took away from going through the process of writing the application?**

Steiner: For a non-developer, the Node-RED environment is a very useful, powerful tool. It's great for getting simple projects up and running very quickly without vast programming knowledge. The projects I've worked on since then have become a bit more complicated, so more and more I wasn't just using pre-made blocks in these applications, it was just more code in the traditional sense. So Node-RED is a great platform for getting going -- and I still use it, I just rely less and less on its built-in features and I'm kind of adding my own. Once we got in a situation where we needed to make things truly available anywhere, basically once I grew out of the freeboard.io dashboard, I started making things from scratch in Javascript and HTML, but it was really a good springboard to get me introduced.

In terms of tips for somebody that would be just starting, really the biggest tip is, "Don't be intimidated." Don't think you need to be an expert coder to put together a really useful application in a short amount of time.

**FreeWave: If you had to put your analyst hat on, what's the potential for app development in respect to the IIoT and where FreeWave plays?**

It's a tough one. We're kind of playing in a market that we haven't before. We're now talking about software which is outside of what we've typically done. There are a lot of cases where our hardware, the radio itself, has been paired up with other hardware, like a PLC, that we can replace. Not in every circumstance, but in many we can combine that and the radio into one ruggedized hardware platform -- typically saves costs, saves power, has a number of different savings. It's potentially a PLC replacement, it's potentially optimization out at the edge -- we can take these devices where traditionally they'd be pulled on a regular basis, every 10 seconds or every minute, and each of those pulls takes up our valuable over the air bandwidth, instead of doing a pull response method, we can know change that into a report by exception -- just send a value when it gets out of a certain range or when it changes, and free up our over the air throughput.

I'm still kind of trying to figure out all the different places are we can apply this. It's easy to just think of we can take the brains from a PLC and partner it with just more low-level logic and provide a replacement for a PLC/radio combination. But once we get into non-I/O applications, like where we're taking data that's already available to us and we're changing it at the edge and sending it in a different way, it opens up possibilities of a whole bunch of things I've never played with before.

**FreeWave: What about the opportunity for developers or people that want to become developers?**

Steiner: When looking at developers, I would pitch this piece of hardware as a ruggedized Linux PC. It's powerful enough to do quite a bit. So it has all the benefits of Linux PC that can run anywhere in the world, so if somebody has a particular code language that they're familiar with they can continue to use that and deploy code on ZumIQ with that.

**FreeWave: What sorts of apps are you working on now? Anything cool you're working on you want to highlight?**

Steiner: Right now actually, I'm wrapping up a deployment that we're using here on our manufacturing floor where we're monitoring the light stacks that are on our manufacturing machines. There's a green, yellow, red light and they can be on/off or flashing and depending on the combination of the three lights or three states, means that machine is in a different state. So we've deployed three radios out there, looking at the status of those lights, determine the state of the individual machines, and then sending real-time data up to screen that's on our manufacturing floor that shows essentially our operational efficiency through the day.

On the face of it, it doesn't sound that complicated but it was a much, much bigger project than the original water tank level monitoring. All the data acquisition and storage and display is done from scratch. We're using Node-RED as the foundation, but we've really built quite a bit more on top of it. And it actually inferences with our existing IT infrastructure here so we use the databases we already have set up and we're interfacing with them and storing data. It's exciting for me because I get to see this application in use every day to see it helping our bottom line.

----

By building applications on the back of proven technology for the IIoT, Steiner has made exploring the software side of the Internet of Things a bit of an easier journey. In future editions of "Making Waves," we'll sit down with more team members from FreeWave and across the industry to talk shop and learn more about the IIoT, application development, and the ways that FreeWave is exploring a new frontier.

[Build an open IoT platform](https://dzone.com/go?i=250322&u=https%3A%2F%2Fwww.redhat.com%2Fen%2Fresources%2Fintelligent-systems-solution-internet-things) with Red Hat--keep it flexible with open source software.
