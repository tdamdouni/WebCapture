# A Rite of Passage for Smart Objects

_Captured: 2017-12-07 at 23:27 from [blog.hackster.io](https://blog.hackster.io/a-rite-of-passage-for-smart-objects-1a7dec75df4a)_

There are certain rites of passage that mark important events in people's lives; birthdays, marriages, and passing of the seasons. They can be solemn, but are often times, not. For instance, there's nothing solemn about [rolling cheese down a hill](https://en.wikipedia.org/wiki/Cooper%27s_Hill_Cheese-Rolling_and_Wake).

Back in the day, learning to write code, a developer's first big project was often times to write a text editor. Everybody uses an editor, and almost invariably hates the editor they're using. Writing your own was [scratching the itch](http://amzn.to/2BOQVCs) that was most obvious, and painful. It also taught new developers the lesson that, even something as apparently simple as a text editor, was harder than it first appeared. It was a rite of passage, and the declaration that you were going to write your own editor was often times greeted with knowing nods from older, and wiser, friends and colleagues.

Similarly in the opening years of the mobile decade, the first app that you tended to build was a Twitter client. Like a text editor a Twitter client appears, on the face of things, to be fairly simple. However once past the initial stages there is enough hidden complexity to teach new developers the same valuable lesson that things are always harder than they appear.

When you start working with physical computing the first thing pretty much everybody does is to blink an LED on, and off, again. When things were harder, this too was a rite of passage. Just to get to the stage where you could turn an LED on and off could take a week or more of hard work. The arrival of the Arduino changed all that, relegating it to a simple parlour trick, the "Hello World" of hardware.

Turning what used to be fairly tough hardware problems into much simpler software problems, the Arduino left us without a unifying rite of passage as hardware developers. But the new ubiquity of Internet-connected devices has, perhaps, created another.

The [Amazon Dash Button](https://www.amazon.com/Dash-Buttons/) was launched two years ago on April 1st. The initial reaction by a lot of people was that it could well be a joke, John Gruber [said at the time](https://daringfireball.net/linked/2015/04/01/amazon-dash-button) that _"I'm not sure whether this is genius, or the stupidest thing Amazon has tried yet."_ But despite the scepticism there were some people convinced that it was the smartest thing that Amazon could do, for instance Simon Wardley [commented](http://blog.gardeviance.org/2015/04/so-amazon-fired-warning-shot-at.html) that, "_Supermarkets will be an antiquated concepts faster than you realise."_

Either way, in the two years since its release, makers have taken the little Internet-connected button into their hearts, and [into their homes](https://blog.cloudstitch.com/how-i-hacked-amazon-s-5-wifi-button-to-track-baby-data-794214b0bdd8).

People quickly started to build their own versions of the button, and "Dash-like" buttons started to appear everywhere. However, just like the other developer rites of passage, there was actually far more hidden complexity here than there appeared on the surface.

So building an Internet-connected button became a rite of passage for developers making their way [into physical computing](https://medium.com/@aallan/walking-across-the-phosphor-2297ccd537f3). But the availability of IFTTT and [their Maker Channel](https://makezine.com/2015/06/26/ifttt-adds-new-channel-makers/), and the [ubiquity of capable hardware](https://medium.com/@aallan/capable-computing-50867847a8d8) quickly made building your own first version of the button a fairly simple task.

> _A simple Internet-connected button using an ESP8266 board and the IFTTT Maker Channel._

But, perhaps surprisingly, the hidden complexity of the button remains. Not as an introduction to physical computing, but as a "full stack" problem.

Building an Internet-connected button has become the first big project that most developers, intent on building a smart device, undertake. From soldering hardware together, to writing the firmware that runs on the hardware, to building a cloud service for your new Internet-connected device to talk to, putting together a button takes skills at all levels of the stack.

Almost like a rite a passage in fact.

So making it do something interesting that hasn't been done before many times before is, at times, challenging. Which makes slightly sideways takes at the problem, like Google's voice-controlled [Paper Signals](https://papersignals.withgoogle.com/), interesting.

> _Voice-controlled Paper Signals, by Google. (📹: Google)_

I've been [thinking about voice-controlled objects](https://blog.hackster.io/building-voice-controlled-objects-with-googles-aiy-projects-voice-kit-352d3272cede) a lot lately, and about the how the user experience of voice interfaces can be changed by modifying the form of the object. About how voice fits into the world.

> _Paper Signals, "Track the rain in Seattle." (📷: Google)_

In a way this is the same Internet-connected button that we've been building for the last few years, but flipped around. The action occurs in the cloud, not the world. The effect happens in the world, rather than on the Internet. Yet voice control ties the two halves together. Configuration, which for the typical Internet-connected button happens in code, is here something that is exposed to the world with a voice interface.

Technology is never really mature until it is invisible, and while voice interfaces are a step towards that I still feel that these interfaces still need to be further embedded, hidden, into the environment.

The Internet-connected button became a rite of passage for developers building smart devices because, not despite, it was such an obvious interface. Because, not despite, it was an everyday interface we were used to using.

For me the developer rite of passage brackets eras of computing. They mark the commoditisation of computing, as technology is wrapped and simplified to the point where it is accessible, the rite changes. Today, our text editors are "good enough" and also so obviously complicated that we subconsciously rule them out as a first big project.

As was we see machine learning increasingly [begin to eat software](https://petewarden.com/2017/11/13/deep-learning-is-eating-software/), the appearance of a voice interface as a proxy to our current rite of passage is intriguing. A signal that we're entering an era of computing where the form and function of the objects offering a computing interface is something we need to experiment with; a point in time where the user experience of an object is created not just by how we handle it, but how we address it with our voice, or even just how [we look at it](https://blog.hackster.io/announcing-the-aiy-projects-vision-kit-234505bc6eef).

If you watch closely enough, you can see here the passing of an era.
