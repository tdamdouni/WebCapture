# Dev Whistleblowers and the Need for Developer Ethics

_Captured: 2018-04-03 at 18:41 from [dzone.com](https://dzone.com/articles/dev-whistleblowers-and-the-need-for-developer-ethi?edition=371203&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=agile%202018-04-03)_

**[See how three solutions work together](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) to help your teams have the tools they need to [deliver quality software quickly](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150123399%3Bdc_trk_aid%3D321096583%3Bdc_trk_cid%3D81552442%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204124&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413346%3Bdc_trk_aid%3D321098505%3Bdc_trk_cid%3D81553809%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). **

Whistleblowers have a long-established, respected but tumultuous history in exposing some of the worst examples of human rights abuse and unethical or illegal activity by governments, corporations, and industries. Their [alumni](https://en.wikipedia.org/wiki/List_of_whistleblowers) include W. Mark Felt (a.k.a "Deep Throat"), Cathy Massiter, Sibel Edmonds, Aaron Schwartz, and Chelsea Manning.

Over the last week two additional names were added to the group:

  * [Sandy Parakilas](https://www.theguardian.com/uk-news/live/2018/mar/21/facebook-whistleblower-gives-evidence-to-mps-on-cambridge-analytica-row-live) \- former platform operations manager at Facebook who claimed that his warnings about the firm's lax data protection standards were ignored, during a session with the _Digital, Culture, Media and Sports_ committee of the UK Government.

  * [Christopher Wylie](https://www.theguardian.com/news/2018/mar/17/data-war-whistleblower-christopher-wylie-faceook-nix-bannon-trump) \- former researcher and data scientist at Cambridge Analytica who came forward to The Guardian Observer and New York Times with the news that his company had misused the data of Facebook users without their permission.

Both have been sharing their stories respectively. What is telling about both whistleblowers, is that one (Parakilas) only took his concerns outside the company several years after the fact, and the other (Wylie) only after an extensive investigation by journalists, lead by Carole Cadwalladr.

Further, they are hardly in a position of heroism like other whistleblowers. Whilst we can assume Wylie presumably signed away some kind of criminal evidence waiver (yet who knows how this will pan out in terms of civil lawsuits) it's notable that both have gotten off pretty lightly. Wylie is hardly an example of an ignorant coder working in a siloed compartment of a bigger project; he was a strategist and decision maker with a reasonable amount of weight. However, Cambridge Analytica tries to dismiss him as a contractor gone rogue. So far Wylie's biggest laments are of his banning from social media:

![Screen Shot 2018-03-21 at 14.57.16 \(1\)](https://passportloverblog.files.wordpress.com/2018/03/screen-shot-2018-03-21-at-14-57-16-1.jpg)

Parakilas now works for Uber and let's face it, Wylie has an acumen of skills that people are going to be clamoring for. Hardly the stuff of historic whistleblowers who risked life and limb to reveal wrongdoings.

## When Developers Speak Out

They're not the first in tech to come forth with evidence of wrongdoings. In 2016, Bill Sourour started a lively stream of confessions and stories on sites such as Medium and Reddit with his post "[The Code I'm Still Ashamed Of](https://medium.freecodecamp.org/the-code-im-still-ashamed-of-e4c021dff55e)," in which he recounts that sixteen years ago, Sourour built a website at his client's request promoting a prescription drug while masquerading as an online quiz -- despite Canada's strict laws on medical marketing. No matter how people answered, the site always recommended the same drug. Right before the happy client took the team out for a steak dinner, a co-worker sent him a news story about a teenaged girl who'd committed suicide after taking their drug. It's side effects had included severe depression and suicidal thoughts.

Other confessions followed, including these on [Reddit](https://www.reddit.com/r/programming/comments/5d56fo/the_code_im_still_ashamed_of/):

> "Reminds me of an interview I had with Facebook. I was asked a question on strategies to get users to use a new feature on the site. I came up with a list of things like prominence on the page, messaging, or showing it on a feed. The interviewer looked a little displeased. He then said 'What if you had to be a bit forceful and coercive with the users?' That gave me a lot of insight into how the people at Facebook and a lot of other big companies think."

>   
"Buddy of mine worked for a payday loans company where they modified a function that takes payment from a customer to retry with a lesser amount if it failed. So no matter how little money you have left they still take it.The result was an immediate increase in profit and a company-wide celebration. The devs chose not to attend."

> "I can attest to this. In a job I used to hold I developed software to be used after accidents or incidents in companies to determine the cause, and if the cause could be determined how to fix it and how much it would cost to fix it vs the cost to not fix it (imagine that scene in Fight Club).   
  
The algorithm on how much it'd cost to fix or leave was flawed in the direction of leaving it. This was software used by _massive_ companies to make decisions about the safety of their customers and workers. I still feel a little shitty about it."

### How Do You Learn Developer Ethics?

Any ethics training you receive as a developer may very well depend on whether you undertook a degree such as Engineering, which included ethics in its course curriculum, attended a boot camp, or are self-taught (notably Wylie the whistleblower is a self-taught coder with a Law degree, hardly cause for pleading ignorance.)

Indeed the notion of developer ethics brings up a zillion questions with a waterfall of potential answers:

  * What are the ethical responsibilities that come with writing code?
  * Who polices you if you write something unethical?
  * How can you complain? 
  * Who can you complain to?
  * What if you lose your job? 

According to [Paul Murray,](https://medium.com/@pmurray.bigpond.com/engineers-used-to-wear-a-special-engineers-ring-on-the-right-pinkie-24aa9201898b) engineers used to wear a special engineers ring on the right pinkie. The surface of it was stippled or ridged so that it would drag on the drafting paper when the engineer did his drawings. The idea of it was that it as there to remind the engineer of the grave responsibility he had. That every decision he made could possibly kill someone.

### **But Assistance is Available**

Harvard University and MIT are jointly offering [a new course](https://www.media.mit.edu/courses/the-ethics-and-governance-of-artificial-intelligence/) on the ethics and regulation of artificial intelligence. The University of Texas this year introduced "[Ethical Foundations of Computer Science](https://www.cs.utexas.edu/~ans/classes/cs109/syllabus.html)" -- with the idea of eventually requiring it for all computer science majors.

In terms of professional bodies, the IEEE has their own [code of ethics](https://www.ieee.org/about/corporate/governance/p7-8.html), as [does ](https://www.acm.org/about-acm/code-of-ethics)the [Association for Computer Machinery](http://www.sigcas.org/).

There's also the [ACM Code of Ethics and Professional Conduct](https://www.acm.org/about-acm/code-of-ethics) and the [Software Professional Code of Ethics](http://www.softwareethics.org/). SIGAS, the ethics body for the ACM, offer a detailed list of [ethics resources. ](http://www.sigcas.org/ethics)

If you're interested in getting more involved in developer ethics, it's worth contacting the [Center for Humane Tech](http://humanetech.com/) and [Good Technology Collective.](https://goodtechnologycollective.com)

Everyone can play a part in protecting the rights of others. As Bill Sojour notes:

> "As developers, we are often one of the last lines of defense against potentially dangerous and unethical practices."

**Discover how TDM Is Essential To [Achieving Quality At Speed For Agile, DevOps, And Continuous Delivery](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=204125&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11226848.150413345%3Bdc_trk_aid%3D321095198%3Bdc_trk_cid%3D81552443%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D). **

Opinions expressed by DZone contributors are their own.
