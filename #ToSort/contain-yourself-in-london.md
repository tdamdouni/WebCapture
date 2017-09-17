# Contain Yourself! in London

_Captured: 2017-08-29 at 10:22 from [blog.alexellis.io](https://blog.alexellis.io/contain-yourself-in-london/)_

I've just come back from my first Container.Camp and I loved it. I got to speak, listen, learn and meet some of the smartest people in tech. Container.Camp London started on Thursday night in Shoreditch and then the main event was on Friday - with both days being packed.

I wanted to say a big _thank you_ to the organisers and sponsors - it was a top couple of days and had a relaxed atmosphere. It must have been days and weeks in the planning but it looked almost seamless.

I covered the events with live Tweeting so that you can get a flavour of the event.

### Day Zero

Conferences, camps and field-days are quite new for me but I liked the idea of a _day zero_ and it worked really well to stir up the appetite and expectation. Docker London helped organise the huge meet-up in an old Victorian Boys' school in the middle of Shoreditch - it was a cool venue with plenty of food, beer and heritage ( think Harry Potter! )

Most of the talks were around Orchestration, home-brewed DevOps solutions and then Ben Hall finished with a talk on the top 5 exploits for Docker Containers. He has an excellent offering in [Katacode](https://katacoda.com/learn), which lets you [learn Docker through a webpage](https://katacoda.com/learn). If you're just starting out then I'd highly recommend it.

> -- Alex Ellis (@alexellisuk) [September 10, 2016](https://twitter.com/alexellisuk/status/774530896833708032)

### Day One - containyourself

The WiFi password was `containyourself` so this was clearly a conference _for geeks by the geeks_. I eventually found my way to Piccadilly Circus and registered for my conference badge. There was a chilled area for the speakers with coffee and thinking space - very nice touch. I met [Dustin Kirkland](http://blog.dustinkirkland.com/) from Canonical and gave him a few laptop stickers. [Liz Rice](https://twitter.com/lizrice) had an interesting live coding GoLang talk which she had borrowed from an IBM employee. The code invoked Linux syscalls to show how `chroot` etc works to produce a modified process that we would call "a container".

> Everyone is listening intently [@containercamp](https://twitter.com/containercamp) let's build a container engine (poc) in 52 lines of code [pic.twitter.com/BdjQ4YsXNR](https://t.co/BdjQ4YsXNR)
> 
> -- Alex Ellis (@alexellisuk) [September 9, 2016](https://twitter.com/alexellisuk/status/774244290390331392)

The talk that resounded the most with me was from Docker's Engineer Nishant. Docker Swarm Mode feels refreshingly simple when compared to some of the other offerings - just enough terminology to get the points across without needing a dictionary of technical jargon.

> [Solomon Hykes](https://twitter.com/solomonstre) announced at Dockercon that making the complex simple is hard, and it takes great engineers. 

> Want a secure [@docker](https://twitter.com/docker) cluster? No problem, it's built-in: two commands and you're set. [@containercamp](https://twitter.com/containercamp) [pic.twitter.com/viZ3CEy47g](https://t.co/viZ3CEy47g)
> 
> -- Alex Ellis (@alexellisuk) [September 9, 2016](https://twitter.com/alexellisuk/status/774195186998140928)

Some of the talks were very slick and well rehearsed. One of those was from [Chris Van Tuin](https://twitter.com/chrisvantuin), RedHat. While there was a focus on [Kubernetes](http://kubernetes.io) he did make some excellent points around security and silos within organisations.

> Could not agree more - break the silos. [@containercamp](https://twitter.com/containercamp) [@RedHatNews](https://twitter.com/RedHatNews) [pic.twitter.com/usoW5PhRyI](https://t.co/usoW5PhRyI)
> 
> -- Alex Ellis (@alexellisuk) [September 9, 2016](https://twitter.com/alexellisuk/status/774260432215441408)

I am a real proponent for developers doing their own testing before passing work onto test engineers. The book [Clean Coder](https://www.amazon.co.uk/Clean-Coder-Conduct-Professional-Programmers/dp/0137081073) suggests that test engineers should only really have to accept stories and not carry out reams and reams of manual testing. Gone are the days where code is checked-in and thrown over the wall. Let's break those silos.

#### Continuous learning

I learned so much and have a long list of tools to try and terms to look up. I'm definitely going to be writing some C code and hacking on Linux sys calls - it gave me a whole new perspective on what a container is.

> i.e. a forked process with some syscalls applied. Calls for namespaces give separation and calls around control groups impose resource limitations.

But Docker is way more than a bunch of carefully-curated syscalls. This industry wouldn't be the same without its leadership and achievements.

I got started hacking with `chroot`, check it out here:

  * [Oh my Chroot!](https://gist.github.com/alexellis/cce3b566311d736f63c85b9291571503) on gist.github.com

> Going old-school with the note taking. Lots to take home. [pic.twitter.com/q3tXPpcWcz](https://t.co/q3tXPpcWcz)
> 
> -- Alex Ellis (@alexellisuk) [September 9, 2016](https://twitter.com/alexellisuk/status/774245433820516352)

#### My talk

Keep checking back for the video recording of my whole talk. I suspect it will take a couple of weeks to materialise and if you can't wait you can see me in [Cambridge and Peterborough](http://blog.alexellis.io/dpip-ftw/).

For the deck head over to SlideShare:

![](https://image.slidesharecdn.com/openfaasaug24-170824163225/95/cncf-intro-demo-openfaas-framework-1-638.jpg?cb=1503592383)

For all the details about the talk and the source-code on Github check my [DockerCon 16 Speaker notes](http://blog.alexellis.io/dockercon-2016-speaker-notes/).

You may have heard me mention Pimoroni and the work they did to help build the hack in my talk. These are the parts (in addition to the [Pi Zero](http://stockalert.alexellis.io/) I used in the build):

> -- Nicolas De loof (@ndeloof) [September 9, 2016](https://twitter.com/ndeloof/status/774284729755500544)

_Salut Captain Nicolas! You have a great eye for a photo._

Watch this video snippet of the live demo from [@feelobot](https://twitter.com/feelobot).

> -- feelobot (@feelobot) [September 9, 2016](https://twitter.com/feelobot/status/774292770215305216)

_No time for technical rehearsal!_

If you want to know more, please follow along on Twitter [@alexellisuk](https://twitter.com/alexellisuk/). The community has done lots of work to get Docker and Swarm Mode working really well on the Pi.

See also:
