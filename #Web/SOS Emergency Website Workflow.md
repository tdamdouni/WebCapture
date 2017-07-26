# SOS Emergency Website Workflow

_Captured: 2015-09-30 at 18:08 from [rocketink.net](http://rocketink.net/2015/06/emergency-website.html)_

![1-Click SOS Emergency Website Workflow → via @_patrickwelker](http://rocketink.net/uploads/2015/2015-06-12-qq-emergency-website.jpg)

> _1-Click SOS Emergency Website Workflow -> via @_patrickwelker_

[Workflow](https://itunes.apple.com/us/app/workflow-powerful-automation/id915249334?mt=8&uo=4&at=10l8771&ct=rocketink) is one of the coolest apps you can put on your home screen. So it's about time I write about it and start sharing some workflows I built. The first one with which I'd like to kick off this series is something useful: an emergency web page. I prepared a short video to give you an overview of what I'm talking about:[1](http://rocketink.net/2015/06/emergency-website.html)

Despite this being a useful workflow, I want state right at the beginning that if the unfortunate event occurs you find yourself involved in an accident, you should do the following things first:

  1. Secure the scene of the accident.
  2. Administer first aid.
  3. Make an emergency call.

I admit I'd find it cool if there was a way to email or sms with additional information to the police, the fire department or the ambulance, but as of today they only support good old reliable technology.

In that respect it seems kind of pointless to use or install such a workflow, but I think it's not. You can't predict when something happens, but if it does, at least you're _digitally_ prepared and are theoretically ready to supply paramedics, the police or as it happens - your own gang of goons with all the essential details when they are on the way to the scene or just arriving.

## Download

All instructions and the actual `Emergency Website.wflow` file are [hosted on my GitHub](https://github.com/pattulus/Workflows/tree/master/SOS%20Emergency%20Website)… but here's the [classic Workflow link](https://workflow.is/workflows/5c6f208d351b449684710cdc1464282a).

## Tips

  1. Setup a domain or subdomain like "sos.donnyk.com" and forward it to the shared Dropbox URL _(once shared it's doesn't change)_. I put this at the top of this list because I think it's a good idea when you place an emergency call, that you can say "Have a look at `www.sos.net` in a minute or two and you get additional information".[2](http://rocketink.net/2015/06/emergency-website.html)
  2. Although it takes just a few seconds to click through the workflow, you could adjust it to minimize the time spent in the workflow.  

    * For instance, with when using the "me mode" you could remove the prompt for selecting a third ICE contact.
    * Additionally, you can remove any other prompts like for the description what has happened or to add more images to the website.
    * You could modify this to serve as a true one-click template which auto-posts to all your social channels, for example, when you get mugged. Since Workflow can send emails in the background you could set up an [IFTTT](http://ifttt.com) rule that triggers sharing this link to all your social channels and alarms your family and friends so that they send for help.
  3. Populate your contacts database. In particular the notes section can be useful to add important information like your height, weight, blood type, allergies, medication, etc.
  4. Clean-up. Add a reminder on the end of the workflow to clean-up the site in 14 days. Of course you could make a workflow for this purpose which deletes all files in your Dropbox folder. Even better: save the `x-callback-url` to this workflow and create a reminder in [Due.app](https://itunes.apple.com/us/app/due/id390017969?mt=8&uo=4&at=10l8771&ct=rocketink), then with one click the site is taken down on the scheduled day.

## What is planned

Depending on the feedback and my spare time I have some more ideas:

  * **More responsive website:** I didn't had the time to setup columns. So, on a big display this one-column layout doesn't look too pleasant at the moment.
  * **Self-hosted version:** I will do an SSH version of this for those of you who want to self-host the site.
  * **A party version:** I think the possibilities are endless here. Setting up a invitation site for parties, weddings and every other thing that you do on a daily basis with the folks in your address book. This could also serve as a Day One replacement for the hard-liners.
  * **A Markdown version:** I've tried it… but currently it's not possible to compile a Markdown file in the way I'd like it to look with workflow. Since the HTML is minimal, it's not a big deal… but still plain text rules, so I'd like to give this a try again with a later version of Workflow. There are problems when adding images between text and some other things. I will give Ari and the Workflow team some feedback in the next couple of days.[3](http://rocketink.net/2015/06/emergency-website.html)

I hope you don't ever truly need to use this. Stay tuned for more Workflow workflows.

  1. In the GitHub repository is also the lost script from a really bad, and hence unpublished version, of the YouTube video. Is that worth a footnote? I do not know, but I'm bad at throwing things away. [↩](http://rocketink.net/2015/06/emergency-website.html)

  2. With the new domain names there are enough short and concise names available for about $10 a year. [↩](http://rocketink.net/2015/06/emergency-website.html)

  3. The first thing I tried was sending a Markdown file to Dropbox. You get a rendered Markdown in the browser, but on mobile devices there's only a link to the file asking you if you want to add it to your own Dropbox. The Evernote version worked, but was not reliable when appending images - often times it didn't find the note to append them to. [↩](http://rocketink.net/2015/06/emergency-website.html)
