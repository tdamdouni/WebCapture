# Creating Simple Rules for Complex Decisions

_Captured: 2017-04-20 at 13:49 from [hbr.org](https://hbr.org/2017/04/creating-simple-rules-for-complex-decisions?utm_campaign=hbr&utm_source=twitter&utm_medium=social)_

![apr17-19-50695325](https://hbr.org/resources/images/article_assets/2017/04/apr17-19-50695325-300x169.jpg)

Machines can now beat humans at complex tasks that seem tailored to the strengths of the human mind, including poker, the game of Go, and visual recognition. Yet for many high-stakes decisions that are natural candidates for automated reasoning, like doctors diagnosing patients and judges setting bail, experts often favor experience and intuition over data and statistics. This reluctance to adopt formal statistical methods makes sense: Machine learning systems are difficult to design, apply, and understand. But eschewing advances in artificial intelligence can be costly.

Recognizing the real-world constraints that managers and engineers face, we developed a [simple three-step procedure](https://arxiv.org/abs/1702.04690) for creating rubrics that improve yes-or-no decisions. These rubrics can help judges decide whom to detain, tax auditors whom to scrutinize, and hiring managers whom to interview. Our approach offers practitioners the performance of state-of-the-art machine learning while stripping away needless complexity.

**To see these rules in action, consider pretrial release decisions. When defendants first appear in court, judges must assess their likelihood of skipping subsequent court dates. Those deemed low-risk are released back into the community, while high-risk defendants are detained in jail; these decisions are thus consequential both for defendants and for the general public. To aid judges in making these decisions, we used our procedure to create the simple risk chart below. Each defendant's flight risk is computed by summing scores corresponding to their age and number of court dates missed. A risk threshold is then applied to convert the score to a binary release-or-detain recommendation. For example, with a risk threshold of 10, a 35-year-old defendant who has missed one court date would score an eight (two for age plus six for missing one prior court date), and would be recommended for release.  
**

![W170328_JONGBIN_SIMPLEWAY](https://hbr.org/resources/images/article_assets/2017/04/W170328_JONGBIN_SIMPLEWAY-159x300.png)

Despite its simplicity, this rule significantly outperforms expert human decision makers. We analyzed over 100,000 judicial pretrial release decisions in one of the largest cities in the country. Following our rule would allow judges in this jurisdiction to detain half as many defendants without appreciably increasing the number who fail to appear at court. How is that possible? Unaided judicial decisions are only weakly related to a defendant's objective level of flight risk. Further, judges apply idiosyncratic standards, with some releasing 90% of defendants and others releasing only 50%. As a result, many high-risk defendants are released and many low-risk defendants are detained. Following our rubric would ensure defendants are treated equally, with only the highest-risk defendants detained, simultaneously improving the efficiency and equity of decisions.

Decision rules of this sort are fast, in that decisions can be made quickly, without a computer; frugal, in that they require only limited information to reach a decision; and clear, in that they expose the grounds on which decisions are made. Rules satisfying these criteria have many benefits, both in the judicial context and beyond. For instance, easily memorized rules are likely to be adopted and used consistently. In medicine, frugal rules may reduce tests required, which can save time, money, and, in the case of triage situations, lives. And the clarity of simple rules engenders trust by revealing how decisions are made and indicating where they can be improved. Clarity can even become a [legal requirement](https://arxiv.org/abs/1606.08813) when society demands fairness and transparency.

**PLAY**3:06

Play

Mute

Current Time 0:00

/

Duration Time 0:00

Loaded: 0%

Progress: 0%

Stream TypeLIVE

Remaining Time -0:00

Playback Rate

1

  * Chapters

Chapters

  * descriptions off, selected

Descriptions

  * subtitles off, selected

Subtitles

  * captions settings, opens captions settings dialog
  * captions off, selected

Captions

Audio Track

Fullscreen

Share

This is a modal window.

Caption Settings Dialog

Beginning of dialog window. Escape will cancel and close the window.

TextColorWhiteBlackRedGreenBlueYellowMagentaCyanTransparencyOpaqueSemi-TransparentBackgroundColorBlackWhiteRedGreenBlueYellowMagentaCyanTransparencyOpaqueSemi-TransparentTransparentWindowColorBlackWhiteRedGreenBlueYellowMagentaCyanTransparencyTransparentSemi-TransparentOpaque

Font Size50%75%100%125%150%175%200%300%400%

Text Edge StyleNoneRaisedDepressedUniformDropshadow

Font FamilyProportional Sans-SerifMonospace Sans-SerifProportional SerifMonospace SerifCasualScriptSmall Caps

DefaultsDone

Close

Share Video: Share via:

  * [Facebook](https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fhbr.org%2F2017%2F04%2Fcreating-simple-rules-for-complex-decisions%3Futm_campaign%3Dhbr%26utm_source%3Dtwitter%26utm_medium%3Dsocial&title=)
  * [Google+](https://plus.google.com/share?url=https%3A%2F%2Fhbr.org%2F2017%2F04%2Fcreating-simple-rules-for-complex-decisions%3Futm_campaign%3Dhbr%26utm_source%3Dtwitter%26utm_medium%3Dsocial)
  * [Twitter](https://twitter.com/intent/tweet?original_referer=https%3A%2F%2Fabout.twitter.com%2Fresources%2Fbuttons&text=&tw_p=tweetbutton&url=https%3A%2F%2Fhbr.org%2F2017%2F04%2Fcreating-simple-rules-for-complex-decisions%3Futm_campaign%3Dhbr%26utm_source%3Dtwitter%26utm_medium%3Dsocial)
  * [tumblr](http://www.tumblr.com/share?v=3&u=https%3A%2F%2Fhbr.org%2F2017%2F04%2Fcreating-simple-rules-for-complex-decisions%3Futm_campaign%3Dhbr%26utm_source%3Dtwitter%26utm_medium%3Dsocial&t=)
  * [Pinterest](https://pinterest.com/pin/create/button/?url=https%3A%2F%2Fhbr.org%2F2017%2F04%2Fcreating-simple-rules-for-complex-decisions%3Futm_campaign%3Dhbr%26utm_source%3Dtwitter%26utm_medium%3Dsocial&description=&is_video=true)
  * [LinkedIn](https://www.linkedin.com/shareArticle?mini=true&url=https%3A%2F%2Fhbr.org%2F2017%2F04%2Fcreating-simple-rules-for-complex-decisions%3Futm_campaign%3Dhbr%26utm_source%3Dtwitter%26utm_medium%3Dsocial&title=&summary=&source=Classic)

Start From:

Direct Link:

Embed Code:

Restart

Simple rules certainly have their advantages, but one might reasonably wonder whether favoring simplicity means sacrificing performance. In many cases the answer, surprisingly, is no. We compared our simple rules to complex machine learning algorithms. In the case of judicial decisions, the risk chart above performed nearly identically to the best statistical risk assessment techniques. Replicating our analysis in 22 varied domains, we found that this phenomenon holds: Simple, transparent decision rules often perform on par with complex, opaque machine learning methods.

To create these simple rules, we used a three-step strategy, [detailed here](https://arxiv.org/abs/1702.04690), that we call _select-regress-round_. Here's how it works.

  1. **Select** a few leading indicators of the outcome in question -- for example, using a defendant's age and number of court dates missed to assess flight risk. We find that having two to five indicators works well. The two factors we used for pretrial decisions are well-known indicators of flight risk; without such domain knowledge, one can create the list of factors using standard statistical methods (e.g., stepwise feature selection).
  2. Using historical data, **regress** the outcome (skipping court) on the selected predictors (age and number of court dates missed). This step can be carried out in one line of code with modern statistical software. 
  3. The output of the above step is a model that assigns complicated numerical weights to each factor. Such weights are overly precise for many decision-making applications, and so we **round** the weights to produce integer scores. 

Our select-regress-round strategy yields decision rules that are simple. Equally important, the method for constructing the rules is itself simple. The three-step recipe can be followed by an analyst with limited training in statistics, using freely available software.

Statistical decision rules work best when objectives are clearly defined and when data is available on past outcomes and their leading indicators. When these criteria are satisfied, statistically informed decisions often outperform the experience and intuition of experts. Simple rules, and our simple strategy for creating them, bring the power of machine learning to the masses.
