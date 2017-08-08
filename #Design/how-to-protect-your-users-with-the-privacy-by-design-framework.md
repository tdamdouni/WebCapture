# How To Protect Your Users With The Privacy By Design Framework

_Captured: 2017-07-28 at 08:16 from [www.smashingmagazine.com](https://www.smashingmagazine.com/2017/07/privacy-by-design-framework/)_

Many companies try to create a great experience for customers. But few are willing to make the changes required to deliver on that promise. In fact most don't even realize just how bad their experience can be. This is why we made a new book called "User Experience Revolution," a **practical battle plan for placing the user at the heart of your company**. [Get the book now!](https://shop.smashingmagazine.com/products/user-experience-revolution?utm_source=magazine&utm_campaign=ux-revolution&utm_medium=html-ad-content-1)

In these politically uncertain times, developers can help to **defend their users' personal privacy** by adopting the _Privacy by Design (PbD)_ framework. These common-sense steps will become a requirement under the EU's imminent data protection overhaul, but the benefits of the framework go far beyond legal compliance.

**Note:** This article is not legal advice and should not be construed as such.

Let's give credit where credit is due. The global political upheaval of the past 12 months has done more to get developers thinking about privacy, surveillance and **defensive user protection** than ever before. The risks and threats to ourselves, and to our users, are no longer theoretical; they are real, they are everyday, and they are frightening. One need only look at the ongoing revelations regarding Cambridge Analytica, a British company with odd links to Canada, which ran a complex data-mining operation on behalf of Donald Trump's presidential campaign to aggregate [up to 5,000 pieces of data on _every American adult_](http://wapo.st/2eQnPI0), to fathom what is at stake for all of us.

As developers and decision-makers, we need to do something to respond to that challenge. The political uncertainty we are living through obliges us to change the ways we approach our work. As the creators of applications and the data flows they create, we can play a critical and positive role in **protecting our users from attacks on their privacy**, their dignity, and even their safety.

One way we can do this is by adopting a _privacy-first best-practice framework_. This framework, known as _Privacy by Design (PbD)_, is about anticipating, managing and preventing privacy issues before a single line of code is written. The best way to mitigate privacy risks, according to the PbD philosophy, is not to create them in the first place.

PbD has existed as a best-practice framework since the 1990s, but few developers are aware of it, let alone use it. That's about to change. The EU's data protection overhaul, GDPR, which becomes legally enforceable in May 2018, _requires_ privacy by design as well as data protection by default across all uses and applications.

As with the previous EU data protection regime, any developer serving European customers must adhere to these data protection standards even if they themselves are not located in Europe. So, if you do business in or sell to Europe, privacy by design is now your responsibility.

This presents a monumental opportunity for developers everywhere to rethink their approach to privacy. Let's learn what PbD is and how it works.

The PbD framework was [first drawn up in Canada](https://www.ipc.on.ca/privacy/protecting-personal-information/privacy-by-design/) in the 1990s. Its originator, Dr. Ann Cavoukian, then Privacy Commissioner of Ontario, devised the framework to address the common issue of developers applying privacy fixes after a project is completed:

> The Privacy by Design framework prevents privacy-invasive events before they happen. Privacy by Design does not wait for privacy risks to materialize, nor does it offer remedies for resolving privacy infractions once they have occurred; it aims to prevent them from occurring. In short, Privacy by Design comes before-the-fact, not after.

The PbD framework has seven foundational **principles**:

  1. Privacy must be **proactive**, not **reactive**, and must anticipate privacy issues before they reach the user. Privacy must also be **preventative**, not **remedial**.
  2. Privacy must be the **default setting**. The user should not have to take actions to secure their privacy, and consent for data sharing should not be assumed.
  3. Privacy must be **embedded into design**. It must be a core function of the product or service, not an add-on.
  4. Privacy must be **positive sum** and should **avoid dichotomies**. For example, PbD sees an achievable balance between privacy and security, not a zero-sum game of privacy or security.
  5. Privacy must offer **end-to-end lifecycle protection** of user data. This means engaging in proper data minimization, retention and deletion processes.
  6. Privacy standards must be **visible, transparent, open, documented** and **independently verifiable**. Your processes, in other words, must stand up to external scrutiny.
  7. Privacy must be **user-centric**. This means giving users granular privacy options, maximized privacy defaults, detailed privacy information notices, user-friendly options and clear notification of changes.

PbD has always been available for any developer to use as a voluntary best-practice framework. Its popularity has tended to be greater in cultures that have a traditionally positive view of privacy, such as Canada and many European countries. Privacy, however, is not traditionally seen as a positive value in the US, whose companies dominate the tech world. For this reason, and for too long, web development has been approached with what at times has felt like the complete opposite of a PbD viewpoint. It has almost become normal for developers to ship apps that require social media registration, that request **unnecessary permissions** such as microphone access and location data, and that demand access to all of a user's contacts.

The notion of privacy by design as a voluntary concept is about to change.

In Europe, the regulation that governs all collection and processing of personal data, regardless of use, sector or situation, has had a complete overhaul. This new set of rules, known as the [General Data Protection Regulation](http://ec.europa.eu/justice/newsroom/data-protection/infographic/2017/index_en.htm) (GDPR), is already on the books but becomes legally enforceable on 25 May 2018. Your business should already be working towards your wider GDPR compliance obligations ahead of this deadline, which will come up fast.

Crucially, GDPR makes PbD and privacy by default **legal requirements within the EU**. Not only will you have to develop to PbD, but you will have to document your PbD development processes. That documentation must be made available to a European regulatory authority in the event of a data breach or a consumer complaint.

Remember that European data protection and privacy laws are **extraterritorial**: They apply to the people within Europe whom data is collected _about_, _regardless_ of where the service is provided _from_. In other words, if you develop for European customers, you must comply with EU data protection and privacy standards for those individuals, even if you yourself are not located within Europe.

Also remember that the EU, through its data protection system, has some of the strictest and most clearly defined privacy frameworks in the world; the US, by contrast, has no overarching data protection and privacy framework at all. Culture is important to remember as well. In Europe, privacy is considered a fundamental human right. Living and developing in a country where privacy is not a fundamental human right does not negate your moral or legal obligations to those who do enjoy that right.

Developers outside the EU, therefore, should consider adopting the PbD principles within the GDPR guidelines as a development framework, despite being located outside Europe. The guidelines will give you a clear, common-sense and accountable framework to use in your development process -- and that framework is a lot better than having no guidelines at all.

European data protection law defines personal data as any information concerning an individual's

  * racial or ethnic origin,
  * political opinions,
  * religious or philosophical beliefs,
  * trade union membership,
  * health data,
  * genetic data,
  * biometric data,
  * sex life or sexual orientation,
  * past or spent criminal convictions.
![If you are collecting personal data, you have to abide by the rules](https://www.smashingmagazine.com/wp-content/uploads/2017/07/privacy-by-design-800.png)

The data users generate within your app is personal data. Their account information with your company is personal data. The UID identifying their device is personal data. So is their IP address, their location data, their browser fingerprint and any identifiable telemetry.

For app developers, PbD compliance means factoring in data privacy by default

  * at your app's initial design stage,
  * throughout its lifecycle,
  * throughout the user's engagement with your app,
  * after the user's engagement has ended,
  * and after the app is mothballed.

There is no checklist of ready-made questions that will get you there; General Data Protection Regulation requires developers to come up with the questions as well as the answers. But in a proactive development environment, the answers would likely take the practical forms required under GDPR, such as the following.

  * Create a privacy-impact assessment template for your business to use for all functions involving personal data, which we will come to a bit later on.
  * Review contracts with partners and third parties to ensure the data you pass on to them is being processed in accordance with PbD and GDPR.
  * Don't require unnecessary app permissions, especially those that imply privacy invasion, such as access to contacts or to the microphone.
  * Audit the security of your systems, which we will also come to shortly.
  * **Minimize the amount of collected data**.
  * Minimize the amount of data **shared with third parties**.
  * Where possible, **pseudonymize personal data**.
  * Revisit contact forms, sign-up pages and customer-service entry points.
  * Enable the regular deletion of data created through these processes.
  * Provide clear privacy- and data-sharing notices.
  * Embed granular opt-ins throughout those notices.
  * Don't require social media registration to access the app.
  * Don't enable social media sharing by default.
  * Separate consent for essential third-party data sharing from consent for analytics and advertising.
  * Periodically remind users to review and refresh their privacy settings.
  * Allow users to download and delete old data.
  * **Delete the data of users who have closed their accounts**.
  * Delete all user data when the app's life comes to an end.

Good PbD practice, and its absence, is easy to spot if you know what you are looking for.

Let's give this popular UK pub chain's app a quick PbD audit.

The app has no settings page, which suggests no user control over privacy. This implies that downloading the app entails granting consent for data-sharing, which does not meet the second PbD principle.

![Screen grab of an app with no privacy settings](https://www.smashingmagazine.com/wp-content/uploads/2017/06/app-example-1-800w-opt.png)

This suggestion is confirmed in the "Edit Account" option, which only allows users to edit their name and email address. This does not meet the third PbD principle "Privacy must be **embedded into design**."

![Screen grab of an app with no account-editing options](https://www.smashingmagazine.com/wp-content/uploads/2017/06/app-example-2-800w-opt.png)

The link to the privacy policy provides a blurry scan of a five-page PDF that is written for the outdated 1995 data protection directive. There are **no user controls or granular options**. If I wanted to exercise control over my data, I would have to write an email to a generic customer-service address or, alternatively -- in the time-honored tradition of privacy policies that are really trying to fob users off -- send them a letter in the post. This does not meet the seventh PbD principle of giving users **granular privacy options** with **maximized privacy defaults**.

![Screen grab of legal blah blah](https://www.smashingmagazine.com/wp-content/uploads/2017/06/app-example-3-800w-opt.png)

The privacy policy informs me that my data will be shared with third parties but gives me **no indication as to who those third parties are**, nor does it give me the option to withhold that data sharing. There is no distinction between third parties whose services are necessary for the transaction (for example, PayPal) and unnecessary services, such as ad networks. This does not meet the sixth PbD principle.

But let's say I write about this stuff for a living, and so I just really need a beer. I go to the pub and fire up the Wi-Fi to use its app. When I connect to the Wi-Fi, I notice its "Settings" page. That page merely provides links to three legal documents. As with the pub's own app, there are no settings to change, no options and no choices. There is no PbD whatsoever.

![Screen grab of a Wi-Fi settings page with no settings](https://www.smashingmagazine.com/wp-content/uploads/2017/06/sky-wifi-800w-opt.jpg)

It's clear that the only way I can ensure my privacy with this pub chain is to not use the app or its Wi-Fi at all. This creates the zero-sum dichotomy, which the fourth PbD principle seeks to avoid.

This pub chain does not meet good PbD practice, or GDPR compliance, by any definition.

By contrast, Twitter's recent privacy overhaul demonstrates **very good PbD practice** and early GDPR compliance. Here's the catch: Its new privacy choices could have a [detrimental and negative effect on users' privacy](https://www.cnet.com/how-to/change-your-twitter-privacy-settings-now/). The difference, however, is that it has been open and transparent and has given users educated choices and options.

![Screen grab of Twitter's privacy options](https://www.smashingmagazine.com/wp-content/uploads/2017/06/twitter-2-800w-opt.png)

The privacy overhaul offers a range of granular privacy options, which are clearly communicated, including a clear notice that it may share your data with third parties. **Users can disable some or all options.**

![Screen grab of Twitter's privacy options](https://www.smashingmagazine.com/wp-content/uploads/2017/06/twitter-3-800w-opt.png)

A prominent splash screen drew users' attention to the changes, increasing the likelihood that they would take the time to educate themselves on their privacy options.

![Screen grab of Twitter's privacy splash screen](https://www.smashingmagazine.com/wp-content/uploads/2017/06/twitter-1-opt.jpg)

> _Twitter is clearly using a PbD framework well in advance of GDPR._

A _privacy impact assessment (PIA)_ is simply a process of documenting the issues, questions and actions required to implement a healthy PbD process in a project, service or product. PIAs are a **core requirement of GDPR**, and in the event of a data protection issue, your PIA will determine the shape of your engagement with a regulatory authority. You should use a PIA when starting a new project, and run a PIA evaluation of any existing ones.

The steps in a PIA are as follows:

  1. Identify the need for a PIA.
  2. Describe the information flows within a project or service (user to service provider, user to user, service provider to user, user to third parties, service provider to third parties).
  3. Identify the privacy- and data-protection risks.
  4. Identify and evaluate the privacy solutions.
  5. Sign off and record the PIA outcomes.
  6. Integrate the outcomes into the project plan.
  7. Consult with internal and external stakeholders as needed throughout the process.

Take some time to come up with a PIA template unique to your business or project that you can use as needed. The [guidance from ICO](https://ico.org.uk/media/for-organisations/documents/1595/pia-code-of-practice.pdf), the UK data-protection regulator, will help you to do that.

Good PbD practice gives users clear information and informed choices. Privacy information notices are central to that. The days of privacy policies being pages upon pages of dense legal babble, focused on the needs of the service provider and not the user, are over.

Your app, product or service should have a **privacy information notice**, including the following details:

  * What data are you collecting?
  * Why are you collecting it, and is that reasoning legally justifiable?
  * Which third parties are you sharing it with?
  * What third-party data are you aggregating it with?
  * Where are you getting that information from?
  * How long are you keeping it?
  * How can the user invoke their rights?
  * Include any information regarding the use of personal data to fulfil a contract.

Many European data protection regulators are devising standardized templates for privacy information notices, and you should check with yours to follow the progress on any required format ahead of the May 2018 deadline.

Under GDPR, the old privacy policy trick of stating "we may share your data with third parties" will no longer be considered compliant. GDPR and PbD require you to list exactly who those parties are and what they do with user data.

![Screen grab of PayPal's third party sharing notice](https://www.smashingmagazine.com/wp-content/uploads/2017/06/paypal-third-parties-800w-opt.jpg)

As one dramatic example, PayPal's recent updated notice lists [over 600 third-party service providers](https://www.paypal.com/uk/webapps/mpp/ua/third-parties-list). The fact that PayPal shares data with up to 600 third parties is not news. That information is simply being brought into the open.

Good PbD compliance is not just about UX. Healthy compliance also involves implementing adequate **technical and security measures to protect user data**. These measures, as with other aspects of full GDPR compliance, must be documented and made accountable to a regulator on request.

PbD compliance on a technical and security level could include:

  * password hashing and salting;
  * data sandboxing;
  * pseudonymization and anonymization;
  * automated background updates;
  * encryption at rest and in transit;
  * responsible disclosure;
  * staff training and accountability on data protection;
  * physical security of servers, systems and storage.

Under GDPR, companies processing certain kinds of data must appoint a _Data Protection Officer (DPO)_, a named individual with legally accountable responsibility for an organization's privacy compliance, including PbD. This requirement is **regardless of a company's size**, which means that even the tiniest business engaged in certain kinds of data processing must appoint a DPO.

![If you are collecting personal data, you have to abide by the rules](https://www.smashingmagazine.com/wp-content/uploads/2017/07/do-you-need-a-data-protection-officer-800.png)

A DPO does not have to be in-house or full-time, nor are legal qualifications required. Very small businesses can appoint a DPO on an ad-hoc or outsourced basis. Check with your EU member state's data-protection regulator for information on your national requirements for a DPO.

We would encourage _all_ organizations to voluntarily appoint a DPO regardless of the nature of their work. Think of a DPO as the health and safety officer for privacy. Having someone act as the "good cop" to keep your development processes legally compliant -- and acting as the "bad cop" if your practices are slipping -- can save you from a world of troubles down the road.

The PbD framework poses challenges that only you can answer. No one else can do it for you: it is your responsibility to commence the process. If you are within Europe, have a look at your national data-protection regulator's GDPR and PbD resources. If you are outside Europe, we have provided some links and resources below.

Don't view PbD as a checklist of boxes to be ticked because "the law says so," nor think of it as something you have to do "or else." Instead, use PbD to think really creatively. Think of all the ways that your users' data can be misused, accessed, stolen, shared or combined. Think of where data might be located, even if you might not be aware of it. Think of what **liabilities you might be creating** for yourself by collecting, retaining and aggregating data that you don't really need. Think of how the third parties you share data with, even if they are your business partners, could create liabilities for you. And in our current political climate, think about the ways that the data you collect and process could be used to do harm to your users. There are no wrong questions to ask, but there are questions that it would be wrong _not_ to ask.

Adopting PbD into your development workflow will create new steps to follow and new obligations to meet. These steps, as onerous as they might feel, are necessary in our rapidly changing world. So, view PbD as a culture shift. Use it as an opportunity to improve your policies, practices and products by incorporating privacy into your development culture. Your users will be better protected, your business's reputation will improve, and you will be well on the road to healthy legal compliance. In an often bewildering world, if these steps are all we can take to make a difference one app at a time, they are worth a lot.

  * "[Privacy by Design](https://ico.org.uk/for-organisations/guide-to-data-protection/privacy-by-design/)," The UK ICO's guidance on PbD, specific to the UK but in plain English.

_(al)_
