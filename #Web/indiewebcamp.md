# Getting Started

_Captured: 2015-11-20 at 23:13 from [indiewebcamp.com](https://indiewebcamp.com/Getting_Started)_

## Contents

[[hide](https://indiewebcamp.com/Getting_Started)] 

  * [1 IndieWebify.Me](https://indiewebcamp.com/Getting_Started)
  * [2 Connect & getting help](https://indiewebcamp.com/Getting_Started)
  * [3 Get a personal domain](https://indiewebcamp.com/Getting_Started)
  * [4 Get a place for your content](https://indiewebcamp.com/Getting_Started)
    * [4.1 Web Hosting](https://indiewebcamp.com/Getting_Started)
    * [4.2 Home Server](https://indiewebcamp.com/Getting_Started)
  * [5 Set up your home page and web sign-in](https://indiewebcamp.com/Getting_Started)
  * [6 Set up your authorship information](https://indiewebcamp.com/Getting_Started)
  * [7 Publish content on your domain](https://indiewebcamp.com/Getting_Started)
  * [8 Add microformats to your content](https://indiewebcamp.com/Getting_Started)
  * [9 Publish (on your) Own Site, Syndicate Elsewhere](https://indiewebcamp.com/Getting_Started)
  * [10 Share and Join Us](https://indiewebcamp.com/Getting_Started)
  * [11 Optional / Bonus Steps](https://indiewebcamp.com/Getting_Started)
    * [11.1 Port old silo content to your site](https://indiewebcamp.com/Getting_Started)
    * [11.2 Set up a personal URL shortener](https://indiewebcamp.com/Getting_Started)
  * [12 See Also](https://indiewebcamp.com/Getting_Started)

**Get started** on the indieweb by [connecting with](https://indiewebcamp.com/IRC) the indiewebcamp community, getting a [personal domain](https://indiewebcamp.com/personal_domain), a [place for your content](https://indiewebcamp.com/web_hosting), and setting up your [home page](https://indiewebcamp.com/home_page) & other [indieweb essentials](https://indiewebcamp.com/IndieMark).

Perhaps you relate to all the reasons [why](https://indiewebcamp.com/why) you should be on the indieweb, but you're not sure how to get there.

Here are a few simple steps you can take to get you on your way to being on the indieweb. Each of these steps is a just a bit more challenging and will give you more independence.

The <http://indiewebify.me/> is a step-by-step guidance on how to get started. It also includes tools to test and validate whatever is needed to be done.

##  Connect & getting help 

Join our chat room to connect with other indieweb people who have a variety of experience:

  * **Join the [IRC](https://indiewebcamp.com/IRC) channel**

**Why?** This step alone will help you quickly get questions answered about next steps. It's not required, but will almost certainly accelerate your progress.

##  Get a personal domain 

You need your own personal domain to serve as your online identity:

  * **Get your own personal domain name** \- Ask a friend or colleague for a [domain name registrar](https://indiewebcamp.com/domain_name_registrar) that they use and like/trust/respect etc. 
  * **Domain Privacy** \- Note that most domain name registrars will make your personal information (name, mailing address, phone number and email address) publicly available via whois lookups. Some registrars offer domain privacy options, so that instead of your personal details the registrar's details will be in the whois directory. Only use domain privacy if you fully trust the provider of the service -- disputes about domain name administration or transfers may get tricky if you are not listed as the legal owner of the domain. 

**Why?** All the reasons listed in [why](https://indiewebcamp.com/why). This is the key first step to joining the indieweb.

##  Get a place for your content 

You need a place for your content.

The easier, free -- but limited -- path is to use a free service as described in [Transitional Steps](https://indiewebcamp.com/Transitional_Steps).

However, ideally you should get your own web hosting provider.

Sign up for [web hosting](https://indiewebcamp.com/web_hosting)

  * Sign up with a web hosting provider (ask friends and colleagues who they use for their personal websites that they're happy with, also see Lifehacker's [list of 5 best web hosting companies](http://lifehacker.com/5911651/five-best-web-hosting-companies)) 
  * Set up your domain name to be served by your web hosting provider 

You can also self-host on your own server. Interesting to hobbyists are the many [Small Computers](https://indiewebcamp.com/Small_Computers) available that can be used as servers, including Raspberry Pi, Beaglebone Black, Intel Galileo, and a host of other small, low-power computers.

##  Set up your home page and web sign-in 

Create and upload a simple `index.html` [home page](https://indiewebcamp.com/home_page) with your name, [icon](https://indiewebcamp.com/icon), and [rel-me](https://indiewebcamp.com/rel-me) links to your social network profiles. Make sure that the profiles link back to your domain.

The website <http://indiewebify.me/validate-rel-me/> has a handy tool to validate that your domain name and profiles are linked together correctly.

**Why?** This ensures that it is easy to see that your profile on the social networks are all the same person as your domain name. This will also allow you to sign in to sites that support [IndieAuth](https://indiewebcamp.com/IndieAuth) -- like this wiki!

##  Set up your authorship information 

Update your `index.html` home page to include your basic information in an [h-card](https://indiewebcamp.com/h-card). This h-card can be as simple as your name.

The website <http://indiewebify.me/validate-h-card/> has a handy tool to validate your h-card.

**Why?** When you publish content, you can link back to your home page using [rel-author](https://indiewebcamp.com/rel-author) and your authorship information can be retrieved from the h-card.

**Advantages:** While you are not yet publishing content on your own site, at this point you have:

  1. Staked your claim on the indieweb 
  2. Set up an identity that you own and control 

These are small but important steps to declaring your independence from content [silos](https://indiewebcamp.com/silo).

##  Publish content on your domain 

Browse the indieweb [projects](https://indiewebcamp.com/projects) page, pick one, and install it.

Your web hosting provider may have a control panel like like [cPanel](https://indiewebcamp.com/wiki/index.php?title=cPanel&action=edit&redlink=1) or [Fantastico](https://indiewebcamp.com/wiki/index.php?title=Fantastico&action=edit&redlink=1) that allows you to set up a content management system in a few clicks.

##  Add microformats to your content 

Add the [h-entry](https://indiewebcamp.com/h-entry) microformat markup to your posts.

The website <http://indiewebify.me/validate-h-entry/> has a handy tool to validate your h-entry.

**Why?** This will allow other people's software to easily read and understand your content. This is useful for a variety of things like recognizing [comments](https://indiewebcamp.com/comments), [likes](https://indiewebcamp.com/likes), [reposts](https://indiewebcamp.com/reposts), and displaying [reply-contexts](https://indiewebcamp.com/reply-context) for your posts.

##  Publish (on your) Own Site, Syndicate Elsewhere 

Set up [syndication](https://indiewebcamp.com/syndication-models) so copies of your IndieWeb content can be published (semi-automatically) to social silos. By setting up POSSE, you can have your posts pushed to specific [silos](https://indiewebcamp.com/silos) with a personal [permalink](https://indiewebcamp.com/permalink)/permashortlink or citation identifier back to the original on your own site.

**Why?** By POSSEing your content to silos, you allow those that read content on those silos to continue seeing what you have to say, while you retain ownership and control of your content on your own site.

**Remember:** Incremental progress is OK and encouraged! POSSE does not have to be totally automatic to be effective. If there is not a pre-existing plugin for your platform, try simply posting on your site and sharing to silos _manually_ (include a link back to the original). This will help you figure out what works for you and what is worth the effort to automate.

Next steps:

  * Share what you did / discovered in the process of building your IndieWeb site, even if it is only a single page, with a simple design. 
  * Ask what you can/should do next in the [IRC](https://indiewebcamp.com/IRC) channel. 
  * Check the list of [events](https://indiewebcamp.com/events) and join us at the next IndieWebCamp or [Homebrew Website Club](https://indiewebcamp.com/Homebrew_Website_Club) meetup! 

##  Optional / Bonus Steps 

###  Port old silo content to your site 

Once you are posting on your own site and [POSSE](https://indiewebcamp.com/POSSE)'ing out content to social silos, port your old silo content to your own site with permalinks on your site. Typically this involves a one-time export and batch import process. Here are some popular social content silos:

###  Set up a personal URL shortener 

**How?**

  * For others, take a look at porting the existing open source [Whistle](http://tantek.com/w/Whistle) algorithmic URL shortener to your system. 

##  See Also 

  * [IndieMark](https://indiewebcamp.com/IndieMark) \- a good way to measure your IndieWeb progress 
