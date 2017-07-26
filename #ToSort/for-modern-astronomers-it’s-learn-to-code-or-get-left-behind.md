# For Modern Astronomers, It’s Learn to Code or Get Left Behind

_Captured: 2017-06-02 at 00:45 from [www.wired.com](https://www.wired.com/2017/05/modern-astronomers-teaching-code/)_

![](https://assets.wired.com/photos/w_1720/wp-content/uploads/2017/05/TelescopeTA_GettyImages-131584374.jpg)

> _ Getty Images_

Astronomer Meredith Rawls was in an astronomy master's program at San Diego State University in 2008 when her professor threw a curveball. "We're going to need to do some coding," he said to her class. "Do you know how to do that?"

_Not really_, the students said.

And so he taught them--at lunch, working around their regular class schedule. But what he meant by "coding" was Fortran, a language IBM developed in the 1950s. Later, working on her PhD at New Mexico State, Rawls decided her official training wasn't going to cut it. She set out to learn a more modern language called Python, which she saw other astronomers switching to. "It's going to suck," she remembers telling herself, "but I'm just going to do it."

And so she started teaching herself, and signed up for a workshop called [SciCoder](http://www.scicoder.org). "I basically lost the better part of a year of standard research productivity time largely due to that choice, to switch my tools," she says, "but I don't think I could have succeeded without that, either."

That's probably true. Rawls's educational experience is still typical: Fledgling astronomers take maybe one course in coding and then informally learn whatever language their leaders happen to use, because those are the ones the leaders know how to teach. They usually don't take meaningful courses in modern coding, data science, or their best practices.

But today's astronomers don't just need to know how stars form and black holes burst. They also need knowledge of how to pry that information from the many terabytes of data that will stream from next-generation telescopes like the Large Synoptic Survey Telescope and the Square Kilometer Array. So they're largely teaching themselves--using a suite of open-source training tools, focused workshops, and fellowship programs aims to help and actually prepare astronomers for the universe they're entering.

### Segmentation Fault

Back when telescopes produced less data, astronomers could get by on teaching themselves. "The old model was you go to your telescope--or you log in remotely because you're fancy--you get your data, you download it on your computer, you make a plot, you write a paper, and you're a scientist," says Rawls, who is now a postdoc at the University of Washington. "Now, it's not practical to download all the data." And "a plot" is laughable. _You_ just try using graph paper to nail down the correlation function that shows the distribution of millions of galaxies (go ahead; I'll wait).

There are social costs to that inadequate education. First, it gives a booster to people who knew, early, both that they wanted to be astronomers and that astronomy meant typing into your computer all day. You know, the kinds of kids who sat in Algebra I "hacking" their TI-83s--ones with access to autodidactic materials and the free time to do that didacting. That kind of favoring is a good way to, on average, keep astronomy's usual suspects--white guys!--on top.

Beyond the social costs, though, lie scientific ones. Let's say a scientist writes a program that analyzes quakes inside the sun ([that happens!](http://gong.nso.edu/info/helioseismology.html)). But there's no documentation on how the program works, and its kludgy, coagulated subroutines are opaque. No second scientist, then, can run that code see if they get the same result, or if the program actually does what Scientist 1 claims. "Reproducibility is held up as the gold standard for what is real or not," says Lucianne Walkowicz, an astrophysicist at the Adler Planetarium. "You need the materials upon which the experiment was performed, and you need the tools. Code is the equivalent of our beakers and Bunsen burners."

Plus, the way astrophysics programming has historically worked is inefficient. Out on overheating desktops across Earth's universities are dozens of programs that do the same thing--catch those quakes, comb for exoplanets--different research groups having made their own. Instead of applying increasingly refined algorithms to their research problems, ill-trained astronomer-coders sometimes spend their time reinventing the wheel.

### Data Drama

Walkowicz wants to help fix these problems before they get worse--which they're about to. She is the science collaboration coordinator for the Large Synoptic Survey Telescope, which will essentially make a 10-year-long HD movie of the sky, so astronomers can see--and, ideally, understand--what changes from diurn to diurn. "Part of the reason we could all get by on being self-taught is that datasets, even when they're on the fairly big side, are pretty small," says Walkowicz. "They're not as large and complex as the data from LSST will be. Problems will be amplified."

Knowing this, and knowing that astronomer apprentices are getting essentially the same training astronomers have gotten since always, she and LSST colleagues decided to help prepare those apprentices. The LSST Corporation (LSSTC) Data Science Fellowship program was born, bringing cohorts of students to six weeklong workshops over two years. To select fellows, they use a program called [Entrofy](https://github.com/dhuppenkothen/entrofy), which optimizes diversity among each class.

The idea doesn't always go over well with professors. "Reactions that I've gotten run the gamut from 'That's a good point, but our students don't have time' to 'Stop trying to turn our astronomers into computer scientists,'" says Walkowicz.

But for their part, the students--perhaps more aware of the future of their field than the more senior researchers--feel more like astronomers. "Before being in this program, I already knew my thesis and my thesis hasn't changed," says Charee Peters, a grad student at the University of Wisconsin, "but I feel more comfortable now being able to approach it. I feel more like a scientist."

Grad student Bela Abolfathi of UC Irvine has similar feelings, and thinks it makes sense that education be driven by data. "I had been trying to learn a lot of these techniques on my own, and my progress was glacial," she says. "It really helps to learn these skills in a formal way, where you can ask questions from experts in the field, just as you would any other subject."

You can often spot a formally untrained astronomer's code a light-year away--with its lack of documentation, its serpentine subroutines. But you can also spot a computer scientist's astronomy code. It's high and tight, but it doesn't display the same depth of knowledge about what the program is doing, and what those actions mean for, say, supernovae. "The key thing is combining the two approaches," says Joachim Moeyens, an LSSTC data fellow from the University of Washington. "My goal is to keep everyone guessing about whether I'm an astronomer or a software engineer." (My guess: a new kind of hybrid.)

### Put a GitHubcap on that Wheel

The LSSTC's fellowship only admits 15 students at a time--hardly the whole field. But the curriculum [is online](https://github.com/LSSTC-DSFP), and it has company. The [Banneker & Aztlan Institute](https://bannekerinstitute.fas.harvard.edu) preps undergrads from all over in Unix, Python, computational astronomy, and data visualization. There are general [boot camps](https://scipy2017.scipy.org/ehome/index.php?eventid=220975&), [astro-specific modules](https://python4astronomers.github.io/), and [continent-centric](http://www.s2ds.org/) [workshops](https://www.ska.ac.za/students/big-data-africa-summer-school/). NASA and the SETI Institute recently teamed up to start the Frontier Development Lab, which brings planetary researchers and data scientists into contact with the private sector. And the University of Washington has a whole organization--the E-Science Institute--dedicated to the cause.

Astronomers have also given each other actual tools. The open-source [AstroPy](http://www.astropy.org) is "a community effort to develop a single core package for Astronomy in Python and foster interoperability between Python astronomy packages." [AstroML](http://www.astroml.org) has a similar goal for the machine learning and data mining side. Scientists, here, can use the same code to do the same things on different data, fixing both that whole redundant wheel thing and the reproducibility problem.

Still, there's some resistance in The Academy, reluctance to integrate all of this into curricula instead of requiring students to (or just tolerating students who) boot themselves off to camp. Alexandra Amon, an LSSTC Data Science fellow and a grad student at the University of Edinburgh, feels this acutely, in thinking about how, in the view of some, her hours spent learning to deal with data detract from her science--essentially the same sentiment Rawls expressed, despite the difference in their years. "Traditionally, from a job application point of view, time spent doing data analysis is detracting from delivering science results and paper-producing," Almon says, "and therefore a hindrance."

But "doing science" means--and has meant, for a while now--doing the kind of analysis that demands data and computer science expertise. Without that, the gap between knowledge and scientists' ability to _get_ that knowledge will only grow, like, you know, the universe itself.

To view this video please enable JavaScript, and consider upgrading to a web browser that [supports HTML5 video](http://videojs.com/html5-video-support/)

Caption Settings Dialog

Beginning of dialog window. Escape will cancel and close the window.

TextColorWhiteBlackRedGreenBlueYellowMagentaCyanTransparencyOpaqueSemi-TransparentBackgroundColorBlackWhiteRedGreenBlueYellowMagentaCyanTransparencyOpaqueSemi-TransparentTransparentWindowColorBlackWhiteRedGreenBlueYellowMagentaCyanTransparencyTransparentSemi-TransparentOpaque

Font Size50%75%100%125%150%175%200%300%400%

Text Edge StyleNoneRaisedDepressedUniformDropshadow

Font FamilyProportional Sans-SerifMonospace Sans-SerifProportional SerifMonospace SerifCasualScriptSmall Caps

DefaultsDone

#### EMBED URL

<script async src="//player-backend.cnevids.com/script/video/56186b3561646d1b61000031.js"></script>

#### VIDEO URL

https://www.wired.com/video/app-uses-kids-obsession-with-phones-to-teach-coding

![](https://dnkzzz1hlto79.cloudfront.net/assets/brands/wired-3ab44ec118fd19029e81b7b879b501b1.png)

#### This live video has ended. It will be available to watch shortly.

[See what else is new](https://www.wired.com)

#### Our bad! It looks like we're experiencing playback issues.

Loaded: 0%

Progress: 0%

Mute

Current Time 0:00

Duration Time 0:00

# App Uses Kids' Obsession With Phones to Teach Coding

![](https://amplifypixel.outbrain.com/pixel?mid=00afed550a0627b348a60b11adf81cf4ce)
