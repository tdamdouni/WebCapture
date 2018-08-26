# Antipattern of the Month: Unresolved Proxy

_Captured: 2018-05-07 at 06:58 from [dzone.com](https://dzone.com/articles/antipattern-of-the-month-unresolved-proxy-1?edition=377214&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-05-06)_

**[Download this white paper](https://dzone.com/go?i=283441&u=https%3A%2F%2Fwww.scrum.org%2Fresources%2Fcharacteristics-great-scrum-team-0%3Futm_source%3DDZone%26utm_medium%3DArticle%26utm_campaign%3Dcharacteristics-whitepaper%2520) to learn about the ways to make a Scrum Team great, brought to you in partnership with [Scrum.org](https://dzone.com/go?i=283441&u=https%3A%2F%2Fwww.scrum.org%2FAbout%2FAll-Articles%2FarticleType%2FArticleView%2FarticleId%2F1029%2FCharacteristics-of-a-Great-Scrum-Team%3Futm_source%3DDZone%26utm_medium%3DArticle%26utm_campaign%3DGreatScrumTeam). **

Just as a Scrum Master is considered to be a "Servant Leader" to his or her team, so a Product Owner might be described as a "Value Maximizer" representing the interests of stakeholders. These are the euphemisms which perhaps best describe the accountabilities of each respective job. Both roles are, of course, essential to Scrum, and yet they do not scale in quite the same way. For example, many development teams, each with its own Scrum Master to help it, could potentially draw work from a single Product Backlog. That backlog must, however, be curated by exactly one Product Owner. Only the PO has this one-to-one relationship with the product being developed.

In Scrum, empiricism is achieved by releasing increments of completed work early and often. Product ownership can be seen as the associated art and science of maximizing value for the benefit of stakeholders. Who counts as a stakeholder, though?

Well, a stakeholder is really anyone who is significantly impacted by the product. The most obvious stakeholders might be those who are funding the initiative and are able to articulate their interest to a PO. Other stakeholders can be much further removed. For example, the dependents of people with savings accounts can be seen as stakeholders in the bank's IT infrastructure, even though those dependents may be quite unaware of any technical systems, or even of the accounts existing at all. If any infrastructure was to fail, they would nevertheless be affected. A good PO exercises a moral duty to represent and balance all stakeholder interests in a product, and to provide a clear authoritative voice to the Development Team concerning the necessary requirements. The role cannot be filled by a committee.

Finding a Product Owner who has the above competencies is a huge challenge for many organizations. Not only must someone have the skills, they must have the time to spend on an emergent product. Very often the best-qualified person can be "high up" in the organization, and is seen as "too busy" to make the necessary commitment. That's when a "proxy" Product Owner is often resorted to. The idea is that they should provide effective representation in the field, and only involve the genuine PO when things get out of hand or certain defined tolerances are exceeded. In practice, this can be seen as a special case of _Management by Exception_.

Any proxy must be respected as having executive authority regarding value, so as not to be undermined. This includes authority over the articulation and ordering of work on a Product Backlog and how it is represented to the Development Team. The proxy must be a genuine and competent representative of the "real" PO, and recognized as being fully able to take decisive action and to provide information in a timely way.

Unfortunately, though, a proxying model can be resorted to as a salve when genuine product ownership is weak. Stakeholders might expect a certain product capability to be available, but none may necessarily wish to own it. This can be the case with middleware for example. Several proxies might then be used, each of whom will represent certain capabilities on behalf of a notional though absent Product Owner. Great discipline is needed when a single clear proxy is unrecognized, since all must then agree to establish compensatory protocols through which they collaborate beyond their narrow interests.

Remember that a strong case can be made against having a "proxy" PO of any type. After all, if a product does not have a true owner, and there is no clear authority for its value to be maximized, is it really worth developing in the first place?

_Unresolved Proxy is Antipattern of the Month at [agilepatterns.org](http://www.agilepatterns.org)_

## Unresolved Proxy

**Intent**: Conceal weak Product Ownership by distributing it

**Proverbs**: That which is owned by everyone ends up being owned by no-one

**Motivation**: Multiple stakeholders can have an interest in a product and each may only be able to articulate the requirements in their area. Consequently, a senior product owner may be tempted to delegate ownership to multiple proxies.

![Image title](https://dzone.com/storage/temp/8992910-unresolvedproxy.png)

**Structure**: A development team tries to negotiate a Sprint Backlog with a Product Owner. However, the PO is represented by multiple proxies and it is unclear which one has authority over the Product Backlog and the backlog items which are to be negotiated.

**Applicability**: Unresolved proxies can be found where Product Owners do not exercise authority or control over the Product Backlog or how it is represented. They are especially common in projects where multiple stakeholders consume a service, such as that which may be provided by shared components or middleware.

**Consequences**: Sprint Planning will be compromised as it is unclear which proxy represents the Product Owner and has authority to negotiate a Sprint Backlog. Increments are likely to be of low quality if the team do not know who to consult with regarding the approval of work. The Definition of Done may be unclear.

**Implementation**: Scrum does not provide for proxy product ownership, although it is widely used and misapplied in a Scrum context. DSDM provides for several business roles which can reduce to unresolved ownership of a backlog (Prioritized Requirements List) unless discipline is maintained. XP mandates that the team liaise with a clear customer role and hence proxying is effectively forbidden.

**[Learn more](https://dzone.com/go?i=259322&u=https%3A%2F%2Fwww.scrum.org%2Fresources%2Fconvergence-scrum-and-devops%3Futm_source%3Ddzone%26utm_medium%3Ddevops) about the myths about Scrum and DevOps. [Download the whitepaper](https://dzone.com/go?i=259322&u=https%3A%2F%2Fwww.scrum.org%2Fresources%2Fconvergence-scrum-and-devops%3Futm_source%3Ddzone%26utm_medium%3Ddevops) now brought to you in partnership with Scrum.org.**

Topics:

agile patterns ,product ownership ,product owner ,product owner proxy ,agile ,agile anti patterns

Opinions expressed by DZone contributors are their own.
