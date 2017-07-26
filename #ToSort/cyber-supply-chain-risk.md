# Cyber Supply Chain Risk

_Captured: 2017-06-01 at 00:41 from [dzone.com](https://dzone.com/articles/cyber-supply-chain-risk?edition=304109&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-31)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

Cyber supply chain risk is a difficult area to manage. According to NIST, 80% of all breaches originate in the supply chain, meaning it should be a definite priority of any security conscious organization to try and manage that risk. That number was given in a presentation by [Jon Boyens at the 2016 RSA conference](https://www.rsaconference.com/writable/presentations/file_upload/grc-w03_integrating_cybersecurity_into_supply_chain_risk_management.pdf). A lot of big companies have been breached due to suppliers with poor information security practices, for example, Target and Home Depot.

![supplychainexpansion](https://safecontrols.files.wordpress.com/2017/05/supplychainexpansion.png?w=1050)

Your real attack surface includes the people you do business with - and those that they do business with again. And this is not all within your span of control!

Most companies do not have any form of cybersecurity screening of their suppliers. Considering the facts above, this seems like a very bad idea. Why is this so?

A lot of people think cybersecurity is difficult. The threat landscape itself is difficult to assess unless you have the tools and knowledge to do so. Most companies don't have that sort of competence in-house, and they are often unaware that they are lacking know-how in a critical risk governance area.

Why are suppliers important when it comes to cybersecurity? The most important factor is that you trust your suppliers, and you may already have shared authentication secrets with them. Consider the following scenarios;

  1. Your HVAC service provider has VPN access to your network in order to troubleshoot the HVAC system in your office. What if hackers gain control over your HVAC vendor's computer? Then they also have access to your network.
  2. A supplier that you frequently communicate with has been hacked. You receive an email from one of your contacts in this firm, asking if you can verify your customer information by logging into their web-based self-service solution. What is the chance you would do that, provided the web page looks professional? You would at least click the link.
  3. You are discussing a contract proposal with a supplier. After emailing back and forth about the details for a couple of weeks he sends you a download link to proposed contract documents from his legal department. Do you click?

All of these are real use cases. All of them were successful for the cybercriminals wanting access to a bigger corporation's network. The technical set-up was not exploited; in the HVAC case, the login credentials of the supplier were stolen and abused (this was the Target attack resulting in the leak of 70 million customer credit cards). In the other two cases, an existing trust relationship was used to increase the credibility of a spear-phishing attack.

To counter social engineering, most companies offer "cybersecurity awareness training." That can be helpful, and it can reduce how easy it is to trick employees into performing dangerous actions. When the criminals leverage an existing trust relationship, this kind of training is unlikely to have any effect. Further, your awareness training is probably only including your own organization. Through established buyer-supplier relationships the initial attack surface is not only your own organization, it is expanded to include all the organizations you do business with. And their attack surface again includes the people they do business with. This quickly expands to a very large network. You can obviously not manage the whole network - but what you can do is evaluate the risk of using a particular supplier, and use that to determine which security controls to apply to the relationship with that supplier.

## Screening the Contextual Risk of Supplier Organizations

What then determines the supplier risk level? Obviously, internal affairs within the supplier's organization are important, but at least in the early screening of potential suppliers, this information is not available. The supplier may also be reluctant to reveal too much information about his or her company. This means you can only evaluate the external context of the supplier. As it turns out, there are several indicators you can use to gauge the likelihood of a supplier breach. The main factors include:

  * Main locations of the supplier's operations, including corporate functions.
  * The size of the company.
  * The sector the company operates in.

In addition to these factors, which can help determine how likely the organization is to be breached, you should consider what kind of information about your company the supplier would possess. Obviously, somebody with VPN login credentials to your network would be of more concern than a restaurant where you order overtime food for you employees. Of special concern should be suppliers or partners with access to critical business secrets, with login credentials, or with access to critical application programming interfaces.

Going back to the external context of the supplier, why is the location of the supplier's operations important? It turns out that the amount of malware campaigns a company is exposed to is strongly correlated with the political risk in the countries where the firm operates. Firms operating in countries with a high crime rate, significant corruption, and dubious attitudes to democracy and freedom of speech, also tend to be attacked more from the outside. They are also more likely to have unlicensed software, e.g. pirated versions of Windows - leaving them more vulnerable to those attacks.

The size of the company is also an interesting indicator. Smaller companies, i.e. less than 250 employees, have a lower fraction of malicious incoming communication. At the same time, the defense of these companies is often weak; many of them lack processes for managing information security, and a lot of companies in this group do not have internal cybersecurity expertise.

The medium sized companies (250-500 employees) receive more malicious communications. These companies often lack formal cybersecurity programs too, and competence may also be missing here, especially on the process side of the equation. For example, few companies in this category have established an information security management system.

Larger companies still receive large amounts of malicious communications but they tend to have better defense systems, including management processes. The small and medium-sized businesses, therefore, pose a higher threat for value chain exploitation than larger, more established companies do.

Also, the sector in which the supplier operates is a determining factor for the external context risk. Sectors that are particularly exposed to cyberattacks include:

  * Retail.
  * Public sector and governmental agencies.
  * Business services (consulting companies, lawyers, accountants, etc.).

Here, the topic of "what information do I share" comes in. You are probably not very likely to share internal company data with a retailer unless you are part of the retailer's supply chain. If you are, then you should be thinking about some controls, especially if the retailer is a small or medium sized business.

For many companies, the "business services" category is of key interest. These are service providers that you would often share critical information with. Consulting companies gain access to strategic information, to your IT network, and get to know a lot of key stakeholders in your company. Lawyers would obviously have access to confidential information. Accountants would be trusted, have access to information, and perhaps also to your ERP systems. Business service providers often get high levels of access, and they are often targeted by cybercriminals and other hackers; this is a good reason to be vigilant with managing security in the buyer-supplier relationship.

## Realistic Assessments Require Up-to-Date Threat Intelligence

There are more factors that come into play when selecting a supplier for your firm than security. Say you have an evaluation scheme that takes into account:

  * Financials
  * Capacity
  * Service level
  * And now… cybersecurity

If the risk is considered unreasonably high for using a supplier, you may end up selecting a supplier that is more expensive, or where the level of service is lower than for the "best" supplier but with a high perceived risk. Therefore it becomes important that the contextual risk assessment is performed based on up-to-date threat models, even for the macro indicators discussed above.

Looking at historical data shows that the threat impact of company size remains relatively stable over time. Big companies tend to have better governance than small ones. On the positive side, smaller companies tend to be more interested in cooperating on risk governance than bigger players. This, however, is usually not problematic when it comes to understanding the threat context.

Political risk is more volatile. Political changes in countries can happen quickly, and the effects of political change can be subtle but important for cybersecurity context. This factor depends on up to date threat intelligence, primarily available from open sources. This means that when you establish a contextual threat model, you should take care to keep it up to date with political risk factors that do change, at least on a quarterly basis, and can even change abruptly. A slower stream would be legislative processes that affect not only how businesses deal with cyber threats but also on the governmental level. Key uncertainties in this field today include the access of intelligence organizations to communications data and the evolution of privacy laws.

Also, the sector influence on cyber threat levels does change dynamically. Here, threat intelligence is not that easy to access but some open sources do exist. Open intel sources that can be taken into account to adjust the assessment of business sector risk are:

  * General business news and financial market trends.
  * Threat intelligence reports from cybersecurity firms.
  * Company annual reports.
  * Regulations affecting the sector, as also mentioned under political risk.
  * Vulnerability reports for business critical software important to each sector.

In addition to this, less open sources of interest would be:

  * Contacts working within the sectors with access to trend data on cyber threats (e.g. sysadmins in key companies' IT departments).
  * Sensors in key networks (often operated by government security organizations), sharing of information typically occurs in CERT organizations.

Obviously, staying on top of the threat landscape is a challenging undertaking, but failing to do so can lead to weak risk assessments that would influence business decisions the wrong way. Understanding the threat landscape is thus a business investment where the expected returns are long-term and hard to measure.

## How to Take Action

How should you, as a purchaser, use this information about supplier threats? Let's say you have access to a sound contextual threat model, and you are able to sort supplier companies into broad risk categories, e.g. low, medium, high-risk categories. How can you use that information to improve your own risk governance and reduce the exposure to supply chain cyber threats?

First, you should establish a due diligence practice for cybersecurity. You should require more scrutiny for high-risk situations than low-risk ones. Here is one way to categorize the governance practices for supply chain cyber risks - but this is only a suggested structure. The actual activities should be adapted to your company's needs and capabilities.

**Practice**
**Low-risk supplier**
**Medium-risk supplier**
**High-risk supplier**

**Require review of supplier's policy for information security**
No
Yes
Yes

**State minimum supplier security requirements (antivirus, firewalls, updated software, training)**
Yes
Yes
Yes

**Require right to audit supplier for cybersecurity compliance**
No
To be considered
Yes

**Establish cooperation for incident handling**
No
To be considered
Yes

**Require external penetration test including social engineering prior to and during business relationship**
No
No
To be considered

**Agree on communication channels for security incidents related to buyer-supplier relationship**
Yes
Yes
Yes

**Require ISO 27001 or similar certification**
No
No
To be considered

If you found this post interesting, please share it with your contacts - and let me know what you think in the comments!

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.
