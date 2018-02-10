# DevOps Thoughts, Fixing Culture Roadblocks, and Cultural Anti-Pattern Practices

_Captured: 2018-02-09 at 14:33 from [dzone.com](https://dzone.com/articles/devops-thoughts-fixing-culture-roadblocks-and-cult?edition=361094&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-02-09)_

Planning to extract out a few microservices from your monolith? Read this [free guide](https://dzone.com/go?i=265421&u=https%3A%2F%2Ftry.split.io%2Fmonolith-breakup-stateful-services-ebook%3Futm_campaign%3D2018%252520DZone%252520DevOps%26utm_source%3Ddzone%26utm_medium%3Dpre%252520roll) to learn the best practice before you get started.

At the time of this writing, DevOps Days PDX just wrapped up and I'm at home, working remotely today, digging into some deployment work around building Elasticsearch Clusters for monitoring with Beats. It's a tricky beast at this point but I'm getting all the nuances figured out.

I have a host of tools at my disposal that help tremendously with this endeavor. There is Packer, to help build the base images I need that have Elasticsearch, Beats, or whatever else needs to be on an image. There is Terraform that helps me to get the images deployed and start the final configuration process. Then there is the configuration process, which is a mix of bash, go, and other things to ensure that the configuration of and services around Elasticsearch are started appropriately.

## DevOps Tooling vs. Culture

It's a cool thing to have all this tooling at my disposal. For me to be able to whip together these solutions for myself and any clients or cohort that needs these solutions. But there's so much more to the premise of _DevOps_ (or lack of premise, more on that in the future), or at least that of an efficient and forward thinking _DevOps_ culture that the tooling is almost irrelevant. Without effective cultural change in an organization, all the fancy tooling is for naught.

A momentary reflection I've had as I hack deeper into **DevOps** idealism and ideas with these notions of [immutable infrastructure](http://blog.adron.me/articles/immutable-infrastructure-some-reads-clarification-what-it-is/), [autopilot pattern applications](http://autopilotpattern.io/), [12-factor apps](http://12factor.net/), and related ideas, the more I find myself between a rock and a hard place with any existing system and existing development cultures.

This is where I fight with the world, with existing cultures, and fight to make changes. You see, I grew up with more than a few dogs. Many people always said, "you can't teach an old dog new tricks" to which I retort, "bullshit, you just suck at teaching your fellow dogs new tricks". Ok, that's my reactionary activist style response to someone saying I can't do something, but it's well founded. Because you see, every dog I ever grew up with would learn new tricks until the day that dog was laid to rest. I _respect_ dogs in that way and I _sure as hell expect more from humans_, even though we humans can be such an enthusiastic let down sometimes.

## Cultural Road Blocks to Technology Solutions

So how does culture create an environment that makes all the tools for naught and encourages me to write articles where it takes me 3-5 paragraphs to get to the meat. Here's a list of the key parts of culture that I've fought with over the years. These are greater roadblocks than any processor limit, bad code, or other simple technical limitation. The cultural roadblocks are far more of an issue than any code or technical roadblock in the vast majority of places. Suffice it to say, if you aren't working on rockets and jets with Nasa, Space-X, or fighting some disease or cancer, it's a cultural roadblock not a technical one that will stop you from progressing.

With all that said, here's my list of cultural problems along with a few suggestions on fixing them. These could also be called "cultural anti-pattern practices."

## Cultural Anti-Pattern Practices

### _"We always did it this way"_

> This practice basically defines the insanity of always repeating a practice without ever checking to see if it should still be done, if it's still needed, or if there might be a better way to do things. Someone might respond with, "If it aint broke, don't fix it!", but this goes far beyond an refuses to even check it its broke, needs fixing, or otherwise. This cultural characteristic of an organization crosses into so many other ways of thinking and other practices it's too hard to enumerate how damaging it truly is to any project or effort. It's definitely a major anti-pattern in technology in general, and a massive cultural roadblock in any group that wants a more "DevOps" Culture of forward progress.

### _"Fire Fight While you Research"_

> We all know task-switching kills productivity (re: [this](https://blog.todoist.com/2014/05/13/how-multitasking-slows-your-brain-and-kills-your-productivity/), [this](https://www.wrike.com/blog/high-cost-of-multitasking-for-productivity/), [this](http://www.umich.edu/~bcalab/multitasking.html), and [this](https://www.psychologytoday.com/blog/brain-wise/201209/the-true-cost-multi-tasking) for example) and the mother load of task switching is going from researching & testing out an idea to being thrown into the hot seat to fight a fire. In this type of task-switch, which is effectively the definition of opposing activities, the mental energy is more than merely exhausting. This type of task switch is a 10 foot thick brick wall of research & learn destruction. There is no way to recover after a fire-fight and immediately dive back into calm, thoughtful, and concentrated creative effort. This type of cultural characteristic will turn any week long project into something that has a delivery date somewhere next to infinity. You think I say that hyperbolically, but it's basically true. Have regular fires and put a team on those that needs to develop a solution for tomorrow, and you'll never have a solution for tomorrow. Simply put, DevOps shouldn't be your "quick fire fight this emergency over here" or the "why is this unique artisanal, hand made, oven baked, organic, custom configured spice rack of a server on fire?" team. This should and needs to be handled in an entirely different way.

### _"Always Silo for the Work"_

> This is not what Adam Smith meant by [division of labor](https://en.wikipedia.org/wiki/Division_of_labour). This is a serious problem that I see continuing in so many places. If you want to get some more ideas about why not to silo work, go read up on the research and work of [W. Edwards Deming](https://en.wikipedia.org/wiki/W._Edwards_Deming) and for some semantic breakdown of the problem [Don't Break Your Silos - Push Out the Silo Mentality](https://www.infoq.com/articles/break-silos-ventilators) is a great article. Creating a silo that creates walls around it and prevents communication or cross-training of necessary knowledge throughout an organization is a surefire way to squander any hopes of a DevOps Culture. The very words pulled together to for DevOps (ya know, Development and Operations) is the breaking down of barriers and silos and bringing together the skills and teamwork necessary.

These are the top three practices that I see and have experienced for a few years. In a subsequent article, I'll take these and others and write about some solutions. As discussed previously, the solutions are hard because it involves people changing their practices. At a core level that is difficult, but again, teaching old dogs new tricks isn't so hard, it just takes persistence. Keep at it and happy hacking.

Got comments, thoughts, or some other thing to ramble on about? Ping me via the Twitters [@Adron](https://twitter.com/Adron) or via wherever you saw this posted. Always happy to discuss, argue, chat, or otherwise work toward finding new solutions!

[Learn how](https://dzone.com/go?i=275425&u=https%3A%2F%2Ftry.split.io%2Fmonolith-breakup-stateful-services-ebook%3Futm_campaign%3D2018%25252520DZone%25252520DevOps%26utm_source%3Ddzone%26utm_medium%3Dpre%25252520roll) to measure the impact of every feature release on performance and customer experience metrics.
