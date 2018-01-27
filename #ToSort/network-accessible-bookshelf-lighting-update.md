# Network Accessible Bookshelf Lighting: Update

_Captured: 2017-12-10 at 14:53 from [www.tomarcher.co.uk](http://www.tomarcher.co.uk/2017/12/08/network-accessible-bookshelf-lighting-update/)_

![](http://www.tomarcher.co.uk/wp-content/uploads/2017/12/audio-1170x550.png)

> _Since the first post I've ended up tinkering with the code for this project every night._

Some notable additions:

  * A smarter homepage,
  * A new sound-reactive mode,
  * An improved Manual mode,
  * Behind the scenes tidying to the API.

Sound Reactive Mode

After my housemates got access to the server, one of them innocently suggested that it'd be cool if Disco mode reacted to the music I was playing. Now I've previously experimented with [audio visualisations](http://www.tomarcher.co.uk/2016/10/28/raspberry-pi-audio-visualiser/) so could have written something from scratch but decided to see what was available on the web. I came across the fantastic [Audio Reactive LED Strip](https://github.com/scottlawsonbc/audio-reactive-led-strip) GitHub repository which looked like it would meet my needs exactly.

The code provides various configuration options, but in the end I went for running it on my PC (which is where my music is played) and sending the data across the network. I replaced the Disco mode on the server with a UDP receiver responsible for taking packets of LED data and displaying them on the Mote sticks. It was then trivial to get the library running on my PC and processing the music I was playing. A nice side effect of this setup is that is also responds to music played on my record player as that's piped through my PC.

While the PC code is running I get a nice display of what's happening and a choice of three different visualisation options:

![](http://www.tomarcher.co.uk/wp-content/uploads/2017/12/visualisation.png)

> _The effect looks really cool:_

Improved Manual Mode

One of the things I really liked about the Mote library's built-in Cheerlights example was the soft transitions as new colours were requested and it was something I coveted for Manual mode. My first instinct was that I'd be able to just spawn a new thread each time a new colour is requested, but the downside of this was that requesting changes quickly in succession caused some really nasty flickering. In the end I created a single thread that runs for the duration of Manual mode (much like the other modes). This thread is then passed a combination of colour and channel and responsible for smoothly transitioning the current colour of that channel to the new colour. This approach means that if a request occurs in the middle of a transition, it will be handled gracefully with the thread abandoning the existing transition and fading seemlessly to the newly requested colour instead. Much nicer!

Smarter Homepage & API Improvements

With some new modes implemented I finally decided it was time to tidy up the homepage. Up to this point I'd been turning the server on and off by navigating to a separate URL. This was a bit fiddly, so I've added a big on/off button to the top-right of the homepage. In addition to this I've clarified how the different modes are activated and added a separate link for Manual mode configuration. These is all done in CSS with Javascript hooking everything into the API.

![](http://www.tomarcher.co.uk/wp-content/uploads/2017/12/Screenshot_20171208-175159.png)

Behind the scenes I've done a lot of tidying of the API to support all the changes mentioned above. If you're interested you can take a look at the [GitHub repository](https://github.com/Tom-Archer/mote-server/). I'm sure I'll continue tinkering with this project, so keep an eye out for future updates!
