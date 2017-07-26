# Privacy is UX

_Captured: 2015-09-26 at 19:37 from [alistapart.com](http://alistapart.com/article/privacy-is-ux)_

![Illustration of a shy fish hiding in a large fish tank.](http://alistapart.com/d/_made/d/ALA_429_Privacy_960_386_81.jpg) [Issue № 429](http://alistapart.com/issue/429)

> _Illustration of a shy fish hiding in a large fish tank._

Government snooping. Identity theft. Sale of personal data. Privacy is out there in a big way. But it's not _in here_, meaning on most product development teams.

I'm a member of those teams, as an experience designer with a foot in strategy and user research. I'm also a longtime public radio reporter (tech was a big topic of mine), so curiosity is my strong suit. I noticed that, at the agencies and tech companies I've worked for, privacy never seemed to be discussed much. And, as reporters do, I wondered why.

Making the case for bringing privacy into the product development process isn't easy, especially since finding examples of successful companies that value privacy isn't easy. In fact, the opposite is true--the web is littered with products or design methods that tried to promote privacy and failed, or that gained only small, niche adoption ([here](https://en.wikipedia.org/wiki/Ello_%28social_network%29), [here](http://research.microsoft.com/en-us/projects/creds/), [here](http://www.nist.gov/nstic/), [here](https://www.privacybydesign.ca/), [here](https://wickr.com/), and [here](http://techcrunch.com/2015/03/02/blackphone2-blackphone-plus/)). Knock-on effects are that privacy sometimes sits on the back burner.

There are good reasons for this: so many factors are at play in developing web products, and privacy gives us just one more thing to think about. But designers and product owners can and should work privacy into the process, and I'll explain some ways we can do that.

## The basics of privacy

Privacy is one thing, but security is another--and the latter is something that many companies do care about. If users' information gets stolen, or governments snoop on it, that's bad for trust and reputation and hence bad for business. When companies like [Apple and Facebook call for security measures or legislation](http://recode.net/2015/05/19/tech-coalition-urges-obama-to-reject-encryption-backdoors/), or encrypt their data, it's because they care about secure user data.

But, even companies that do encrypt (voluntarily--there are no laws around this right now) receive data in an unencrypted fashion, so there's nothing to stop them from making the most of it for their own purposes, or selling that information to other companies (some secure, some not).

Privacy questions come in when we talk about a company collating/snooping on users' behavior and messages, or passing data on to others. Right now, there is no blanket privacy law in the United States, but rather a patchwork covering specific areas of information and users: for example, health and financial data are subject to more intense legal scrutiny under HIPAA and the Financial Services Modernization Act, respectively. Everything else falls under the purview of the FTC, which [polices bad business practice and mandates privacy disclosures](https://www.sba.gov/content/privacy-law) (not actual privacy, mind you--just disclosures). Those are the sorts of things that would be detailed in a privacy policy. Any future American case furthering privacy protections could be made upon the [Fourth Amendment of the Constitution](http://en.wikipedia.org/wiki/Fourth_Amendment_to_the_United_States_Constitution).

There are many flavors of online privacy violations. Last year's [Uber episode](http://recode.net/2014/11/20/tech-companies-snooping-on-users-creepy-and-common/), in which the company singled out a journalist and tracked her movements without consent, was a violation of policies and may allow for legal recourse. (Other companies likely engage in these sorts of activities, but we rarely hear about it. Of course, the Facebooks and Googles of the world have access to all the messages their users write.)

Then there's the murky area of things that aren't technically illegal, but are questionable, like companies collecting information on behavior that users are not aware of. Cookies are one example of that. Of bigger concern is something like [Target predicting a woman was pregnant](http://www.nytimes.com/2012/02/19/magazine/shopping-habits.html) before she knew it herself. And, finally, there's the selling of that data--to advertisers, for example, or [during an acquisition](http://www.nytimes.com/2015/06/29/technology/when-a-company-goes-up-for-sale-in-many-cases-so-does-your-personal-data.html).

This data is typically made up of a combination of user-entered values and behavior tracked in the background (a.k.a. analytics): geographic location, clicks, time on a certain page, etc. Many companies claim they don't care about individually identifying features, but instead, about user behavior or information in aggregate. However, anonymized or partially anonymized data can often be traced to individuals--take, for example, AOL's [search data leak](https://en.wikipedia.org/wiki/AOL_search_data_leak) of 2006. One user who had searched for information on murdering his wife was identified--but he turned out to be a TV writer who worked for a crime show.

## Making a case for privacy

### Community-building requires trust

If a business wants to build some sort of community or audience, it needs to establish trust. You can make the case that privacy will help, and include product requirements and user stories around privacy.

### Legislation will come

Following privacy legislation isn't easy, but things are moving. American [states pursue their own laws](https://epic.org/state-policy/) piecemeal, and [federal legislation is outdated](http://www.forbes.com/sites/josephsteinberg/2014/06/02/your-privacy-is-now-at-risk-from-search-engines-even-if-the-law-says-otherwise/), though [Congress talks](https://epic.org/2015/07/congress-to-hold-hearing-on-en.html) about it more and more. Meanwhile, [Europe is ahead](https://en.wikipedia.org/wiki/Data_Protection_Directive) of the rest of the world when it comes to online privacy laws. If your company has designs on going global, all users will likely be stored in the same online bucket--meaning European privacy protections will need to be extended to all of them. Wherever you do business, being proactive now will save headaches later.

### Bad press is painful

Uber could've avoided some pain--and legal hot water--if it had adhered to stated policies. When violations and sketchy behaviors are brought to light, users hear about it. Witness the [intense reaction](http://www.wsj.com/articles/furor-erupts-over-facebook-experiment-on-users-1404085840) to Facebook's "social experiment." Or the response to Edward Snowden.

### It could become a selling point

Some global players are starting to think along the lines of "privacy as selling point," including [IBM](http://recode.net/2015/05/20/ibm-raises-its-security-profile-with-threat-info-sharing-initiative/), [Microsoft](http://www.microsoft.com/en-us/privacystatement/default.aspx), [Google](http://www.bbc.com/news/technology-32958765), and [Apple](http://recode.net/2015/06/12/apples-latest-product-is-privacy/). [Mark Cuban even ranted about it](http://www.inc.com/mark-cuban/playbook-biggest-mistake-social-media.html)!

### Privacy affects lives

The most common retort you hear when raising issues around privacy is "What are you so scared of?" During a 2014 talk at Carnegie Hall, Glenn Greenwald explained how he responds to this question: he proposes the asker write their email username and password on a piece of paper and give it to him. No one ever takes him up on it. People, he posits, simply want private spaces where they can do things away from others.

There are also very real things to be afraid of--things that we, as user experience designers who care about empathy, should also care deeply about. One example: Weight Watchers sharing personal information in user accounts (weight, health habits, and exercise patterns, for example) with advertisers, which [60 Minutes reported on](http://www.cbsnews.com/news/shocked-to-learn-how-data-brokers-are-watching-you/). In the same report, an expert discussed the emergence of "digital redlining." Historically, redlining is the practice of denying mortgages to applicants of color in predominantly white areas of town. Digital redlining is similar: you could be denied a mortgage if the socioeconomic status of your online social circle deems you undesirable--and Facebook just [patented technology](http://venturebeat.com/2015/08/04/facebook-patents-technology-to-help-lenders-discriminate-against-borrowers-based-on-social-connections/) for that very thing. Warrantless snooping by the government can have serious [consequences](https://www.propublica.org/special/no-warrant-no-problem-how-the-government-can-still-get-your-digital-data) too, leading to unjust detention and arrest.

Down the road, it'll really suck when health insurance companies start to get access to data from Fitbit to raise premiums (they're already [rewarding users](http://www.cbsnews.com/news/shocked-to-learn-how-data-brokers-are-watching-you/) who provide access to their data). And don't forget about users in countries whose [lives may be at risk](http://mashable.com/2011/02/25/facebook-egypt/) when their data isn't private. If we believe that treating users with respect and honesty is essential to a good experience, then we owe it to them to ponder these issues.

We also need to be aware of the processes we're complicit in--as [Mike Monteiro has said](https://vimeo.com/68470326), designers have responsibility. Trading in user data is a big part of making a living online today. If you choose to participate, you should know that you're part of further ossifying the web in this modus operandi. You may be okay with that, but know it.

So, to sum up: Arrests based on erroneous or overblown government intelligence. Insurance companies snooping around in messages and health records. Dissenters being punished by dictatorial regimes. The arrival of robot overlords in the form of targeted advertising. Lack of privacy creates real danger. But even if users don't want Google cataloging and analyzing a lifetime of their search history _just because_--well, that's valid, too. It's [Article 12 of the Universal Declaration of Human Rights](http://www.un.org/en/documents/udhr/).

## Adding privacy to your process

There's no tried-and-true path to building privacy into your process, but there are ways to get started. Here are a few.

### Use a question protocol

If your site or app uses a form, or asks the user to enter any amount of data, Caroline Jarrett's question protocol is an invaluable tool for digging deeper into what you're doing and why. As she [describes it](http://www.uxmatters.com/mt/archives/2010/06/the-question-protocol-how-to-make-sure-every-form-field-is-necessary.php):

Jarrett sees the protocol as bringing web development closer to the rigor of the scientific research process. "For example, during the census," Jarrett explains, "they will be doing extensive research around what questions to ask, how that data will be used, and the delicate balance between the cost of collecting every piece of data and the benefits. Because collecting census data is incredibly expensive, but it's very important."

In the case of product development, every piece of data we collect through a form has a cost, too.

User costsBusiness costs

**Attention**
What about your product might the user ignore if a form is onerous? 
**Data storage**
Where will you keep all of this stuff?

**Time**
How much time does a user really have to contribute to your form fields? 
**Data maintenance**
What is the cost of updating, modifying, and potentially disposing of data?

**Trust**
What happens if users don't understand why certain data is required? 
**Data quality**
What will it take to sift through made-up data to get to the real stuff?

**Physical cost**
What does it take from the user to fill out the form?
**Breach of user trust**
How would users react if data were misused or sold?

You could apply this method of deeper thinking to any piece of data you're collecting on a site, not just what gets typed into a form. Say you want to collect GPS data on users: ask why it's needed, where it'll be stored, how it'll be used, and tally up the costs around breach of trust if it comes to that.

### Write user stories around privacy

We spend a lot of time designing features--features that users experience. But things that happen in the background of an experience can still constitute bad UX.

One way to bring privacy into the conversation early on is to write user stories around a privacy epic. Here are some examples based on an online store:

  * As an online shopper, I want to know why the store requires my phone number because I feel uncomfortable giving it out, and it seems irrelevant to making a purchase.
  * As an online shopper, I want to have a choice over whether and how the store uses my search history so that I have control over my data.
  * As an online shopper, I want to have the option for my purchase history to inform recommendations the store makes so that I can shop more efficiently.
  * As an online shopper, I want to know how the store uses my data so that I can make an informed decision about whether I want to shop there. 
  * As an online shopper, I want my purchase history to remain under the purview of the relevant business so that I do not receive unsolicited marketing.
  * As an online shopper, I want my purchase history to default to private until I tell the store they may use it.

These stories may affect, or be influenced by, the privacy policy, so be sure to meet with compliance stakeholders about them. If these were your user stories, you might also find that some of them turn out to be non-functional, like the one about keeping purchase history away from third parties. The user may never see anything related to that story, but it could dictate the way databases are built, and how information is stored, tagged, and disposed of. Keep up an open dialogue with developers so they are aware of how certain stories need to be worked into their technical solutions.

### Turn privacy into a feature

Prioritizing privacy can also lead to clearer product designs, as in Microsoft's recent expansion of its privacy policy:

![Screenshot of Microsoft's privacy policy.](http://alistapart.com/d/429/Microsoft-Privacy.jpg)

> _Approachable language with content presented in an organized fashion._

There's nothing fancy or groundbreaking about this design (and in fact the content itself leaves many questions unanswered). But one thing that is innovative is how it pulls the privacy policy out from the tiny legalese fine print in the footer, and expands on it to try to make it comprehensible to users.

Here's another example:

![Two icons, one showing that a site gives your data to advertisers, and the other showing that your data is never given to advertisers.](http://alistapart.com/d/429/aza5-edit.jpg)

> _Privacy icons by Aza Raskin._

Former Mozilla designer Aza Raskin created a whole [slew of privacy icons](http://www.fastcodesign.com/1662961/mozillas-privacy-icons-tell-you-how-sites-use-your-personal-data) to instantly communicate to users how their data is used.

These examples are more about informing users than allowing them to take action. Much more could still be done to give control. But explaining--whether through approachable language, content organization, or design--is a great first step.

### Make privacy a core team skillset

Developers oftentimes don't know optimal storage configurations to help protect users. ("Let's anonymize the logs" is a typical, and unsatisfactory, solution.) Advocate hiring someone for this expertise, such as someone who went through a program specifically studying online privacy--like [Carnegie Mellon's IT master's with a privacy engineering specialization](http://privacy.cs.cmu.edu/). Or bring in a consultant to advise on a specific project, like [the Privacy Guru](http://www.theprivacyguru.com/). If you're part of a bigger company, maybe it's time to consider a chief privacy officer--[Acxiom has one](http://www.acxiom.com/jennifer-glasgow/).

### Build privacy into your product's DNA

You probably can't compete on privacy alone, but combining usability with privacy--like [Heartbeat](https://ind.ie/) does--can be an advantage. Or, build third-party products that encourage privacy, such as the [rating system for apps (PDF)](http://staff.ustc.edu.cn/~cheneh/paper_pdf/2014/Hengshu-Zhu-KDD.pdf) that would let consumers know how private and secure they are that a group of computer scientists proposed. I talked with Columbia professor [Henning Schulzrinne](http://www.cs.columbia.edu/~hgs/), who recommended an Energy Star-like privacy rating system, and futurist [Marcel Bullinga](http://futurecheck.nl/), who told me about an idea for a universal dashboard that would allow users to control their privacy across the internet. The Electronic Frontier Foundation's [Privacy Badger](https://www.eff.org/privacybadger) blocks advertisers and trackers that collect data, while [Lightbeam](https://www.mozilla.org/en-US/lightbeam/), a browser add-on for Firefox, shows you who's accessing data on every site you visit.

### Reconsider the ads you run

[Les Orchard](http://blog.lmorchard.com/2015/07/22/the-verge-web-sucks/) and [Doc Searls](https://blogs.law.harvard.edu/doc/2015/08/12/separating-advertisings-wheat-and-chaff/), among others, have written about how ad-tracking software can delay site load speeds, degrading the user's experience.

### Cultivate your privacy skills

Take a course on data analytics. Hold a lunch-and-learn at your office about [US privacy laws](http://www.acxiom.com/defining-sensitive-world-consumer-data/). Share the W3C's [guidelines on browser fingerprinting and privacy](http://www.w3.org/2001/tag/doc/unsanctioned-tracking/), the FTC's guidelines for [privacy and security for the internet of things](https://www.ftc.gov/news-events/press-releases/2015/01/ftc-report-internet-things-urges-companies-adopt-best-practices) and its older report on [protecting consumer privacy (PDF)](https://www.ftc.gov/sites/default/files/documents/reports/federal-trade-commission-report-protecting-consumer-privacy-era-rapid-change-recommendations/120326privacyreport.pdf), Microsoft's [adherence to the ISO's guidelines](http://blogs.microsoft.com/on-the-issues/2015/02/16/microsoft-adopts-first-international-cloud-privacy-standard/), or the foundational principles of "[Privacy by Design](https://www.privacybydesign.ca/index.php/about-pbd/7-foundational-principles/)."

It's tough to keep up, but there are resources to help, like the [Electronic Privacy Information Center](https://epic.org/) and writers like [David Meyer](https://twitter.com/superglaze) and [Kashmir Hill](https://twitter.com/kashhill). Write more articles like this one and come up with other ideas for "privacy by design." Maybe you've built privacy into your process in a cool way. I know I'd love to hear about it.

## Be realistic about the hurdles

Bringing privacy into your process is still challenging. First off, usage patterns are one of the basic underpinnings of UX. The vast troves of online data being generated aren't evil in themselves. On the contrary, they hold possibilities for wonderful insights and improvements to life. But there's a fine line between that and invasive--possibly even abusive--behavior. (One pretty unambiguous example is [Mattel's Hello Barbie](http://www.washingtonpost.com/blogs/the-switch/wp/2015/03/11/privacy-advocates-try-to-keep-creepy-eavesdropping-hello-barbie-from-hitting-shelves/), which records children's voices and transfers them to an online server to process and respond to them.)

Then, there are the users themselves, who seem to sort of care about privacy, but sort of don't. A 2014 [report from Pew](http://www.pewinternet.org/2014/11/12/public-privacy-perceptions/) found that while 80 percent of Americans are concerned about third parties accessing data about them on social networking sites, 55 percent "agree" or "strongly agree" with this statement: "I am willing to share some information about myself with companies in order to use online services for free." Essentially, we've grown accustomed to the commerce of personal information online in exchange for free services. There's the old saw, "If you're not paying for the service, then you're the product." User data is quite the lucrative product, too. There's arguably a _disadvantage_ to throttling its flow. (See: Google's market cap of $360 billion.) Many companies have never even considered that there may be alternatives to the current user-data-for-service model of so much of the internet.

Then there's this notion of "[Minimum Viable Product Disease](http://recode.net/2014/11/13/nico-sell-of-wickr-says-she-is-properly-paranoid-full-video/)," where products are rushed out the door before privacy is taken into account. That's no big surprise--adopting privacy as a foundational principle is time-consuming and expensive, as [ad company 4info found](http://adage.com/article/datadriven-marketing/privacy-design-crucial-easy-cheap/295145/).

## Try anyway

The fact that it's hard doesn't mean we're off the hook. Just as we have a responsibility to design accessible products, even when it'd be easier not to, we have a responsibility to consider privacy. We all have a role in shaping the way products are delivered, ensuring they serve users' interests in an era when the notion of private life has been thoroughly compromised. So let's do it mindfully, not limiting our considerations to features that users see. Instead, let's look underneath and above, reach further into the future, and think bigger about what user experience is.
