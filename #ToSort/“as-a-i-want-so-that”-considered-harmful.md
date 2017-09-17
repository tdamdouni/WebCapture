# “As a, I want, So that” Considered Harmful

_Captured: 2017-08-24 at 16:49 from [blog.crisp.se](http://blog.crisp.se/2014/09/25/david-evans/as-a-i-want-so-that-considered-harmful?utm_content=buffer6f8e0&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

If you are working on an agile project, it is almost certain that you are using Stories to describe your backlog of work. It is another near-certainty that if you are using Stories, you write them down using this format:

"**As a** <user or stakeholder type>  
**I want** <some software feature>  
**So that** <some business value>"

As someone who cares about the state of agile practice, I want to offer some alternatives, so that agile teams remember that the point of the story is in the telling, not the template. The shared understanding comes from the conversation, not the card. By offering you different ways to 'tell' the story in its short written form, I hope you will be able to re-ignite a greater level of meaning, interest and engagement in your team's discussions about the work they are doing to build great software that matters to people.

## Who, What, Why

Let's start with what's good about the "As a…I want…So that…" format.

  * It identifies the Who, What and Why of the story. Who will use this, or find it valuable? What feature are we providing? Why is this valuable or important? These are all fundamentally important things in the discussion of the story.
  * It's memorable. Once learned, nobody is likely to forget the structure.
  * It's well known. People who are already used to the structure don't lose any time getting their head around a new format on a new team or project.
  * It's brief. The structure encourages the who/what/why to be expressed in a single sentence.

So, what is wrong with a simple, memorable structure that gets the key points across in one sentence? In my opinion, the runaway success of this format has been its own undoing. It is like a creative, original song that became a hit and has since been turned into elevator musak due to its popularity. It is so widely used, it's no longer a handy suggested primer, it's the law. It's no longer a form of expression, it's a story-shaped mask hiding a lack of imagination. Now anyone can make any lazy bunch of words sound like an agile story.

## Why bother?

Arguably the most important purpose of a Story when it is first proposed is articulating the reason why there is value in making a change. From the implementation team's point of view, doing nothing is always the cheapest and simplest option, so there needs to be a good reason for making a change in the first place. That's meant to be the purpose of the "So that…" clause in the common template, but putting it last means the logic is the wrong way around, and this phrase often ends up just being a grudging re-phrasing of the "I want" clause. Instead we should always start with the reason why we need a change, before proposing what the change should be.

Chris Matts is credited with what I think is the best improvement made to the story format so far. He suggests replacing "So that…" with "In order to…" and placing it at the beginning of the sentence. This is absolutely the right place to be expressing value to a stakeholder.

Hence a simple and effective alternative format is:

"**In order to** <achieve some business value>,  
As a <stakeholder type>  
I want <some new system feature>"

## Who cares?

The intention of the "As a…" part of the story format is to encourage us to tell stories from a user's perspective, rather than just itemise a long list of things the system should do. It is there to humanise our work and remind an agile team that they are not just building software, they are making an impact on the way people work.

To get the most out of this part of the story description, you should be specific about the persona that typifies who gets the benefit of the impact that this story will make. Use adjectives if it helps to bring the story to life, such as "busy executive", "risk-averse investor", "regular commuter", "stressed mother", "bored teenager" and so on. Avoid generic roles like "user" or "customer" - if your story benefits all users equally, then just leave out the "who" clause altogether, and save it for stories that benefit from the differentiation. Definitely avoid using non-persons such as "the system", "the database" or even "the Product Owner". As Gojko Adzic once said, "The system doesn't want to do anything - the system wants to sleep."

A story does not always need to be told from the user's point of view. It does not always make sense to say "As <someone> I want <something>" because we can deliver value without necessarily answering a specific user need. Good software is like good service in a restaurant - often we are delighted by the little things that happen without us asking for them.

Therefore you can try formats that still identify who benefits from the change, but express it as a pro-active change. Consider this clunky example in the traditional format:

_"As a shopper, I want to not see the card types that don't match my card number when I type it in, so that I can only see cards types which do match the number."_

This sounds contrived and awkward, and would read a lot better in a format such as this:

_"In order to increase visual feedback for shoppers entering card details, we will progressively hide the card types that do not match the card number as it is entered."_

Notice how in this format we still identify the "who" (shoppers entering card details) but the "what" action is introduced as "we will", since it is the product team that is prompting this improvement.

## What's new?

Having identified the "why" of the story in an "In order to…" phrase, and identified the "who" in a "for…" or "as a…" phrase, the story culminates with a call to action, describing "what" is to be added or changed in the software.

One of the common problems I see in stories is that the "I want…" phrase is not specific enough, and often states behaviour or features that overlap with what already exists.

To combat this and help keep the "what" of the story short and to the point, I like to **start with a verb** that highlights the new action or behaviour the product will have, that it does not have now.

Note that although I often precede this verb phrase with "we will…" (as a replacement for "I want…"), the verb phrase should describe an action or behaviour that the product takes, not the action that the implementation team does to put the feature or behaviour there.

For example, if the "what" of the story is about hiding card types that don't match an entered credit card prefix, the following product-centric use of "we" is valid:

"we will **hide the card types** that do not match the entered card number…"

But this team-centric use of "we" is not:

"we will **make an AJAX call** to the card validation service after 2 digits are entered…"

Similarly, this is valid: "we will **include** settlement date in the transaction report"

But not this: "we will **add** a column SETTLEMENT_DATE to the Transaction table"

If the distinction is too subtle and you find yourself writing implementation details, try using "the system will…" or name your product, as in "Ex-Sell will…"

## Where's my Change?

As I mentioned earlier, the short description of a story often leaves a lot of ambiguity about what the scope of the required change will be. Even if the required new behaviour (the "what") is accurately described, the amount of work required of the team to implement it depends on how much it differs from current behaviour, and that might not be clear to everyone.

For example, imagine your job is to estimate the size of this story for a financial trading system:

_"In order to continue trading while avoiding breaching regulations,  
As a trader, I want a warning message when the total volume of trades reaches 90% of my daily trading limit"_

The requirement is pretty clearly described, but unless we are very familiar with what the relevant part of the system does already, we can't tell on the face of it if this is a major change or not. Consider the following possibilities:

  * Is there already any concept of daily volume limits in place? (If not, this story has to build a lot of new things, and would be relatively complex to implement.)
  * Does the system already have daily limits which it prevents traders from exceeding? (If so, much of the existing logic could be re-used to trigger the required warning, and it would be only a moderate change.)
  * Is there already a warning in place, but which is triggered at 80% of the volume limit? (Changing this warning threshold to 90% would be a very simple change.)

The point is that the description of the required behaviour alone, even if complete and accurate, is not enough to indicate how complex the story is to implement. We also need to know how much of a change it represents compared to the current behaviour.

## Try a "Whereas currently…" clause

A technique I like to use to address this problem is to add another clause to the story template starting "Whereas currently…" or "Instead of…"

The wording of this extra clause should make as clear as possible the contrast between what is needed and what we already have in the product.

For the example story above, applying these techniques might result in the story being amended as follows:

_"In order to help traders make best use of trading volume limits,  
The system will warn traders when the total volume reaches 90% of the daily trading limit;  
Whereas currently no warning is given until the daily limit is reached and all trades are blocked."_

## Don't obsess about the format!

I've given you some ideas for adjusting the way you express the short form of stories, but remember that the format does not matter as much as the process you use to identify, discuss, elaborate and ultimately implement the story.

A story is ideally just a token for the real information that needs to be discussed - the story card is a promissory note to hold a conversation about how you can improve your product. Assuming the information you write on the card is not false, any of the formats is probably good enough to start that discussion. But if the information on the card is false, all formats will be equally bad.

Remember that your customers are not buying your stories; they are buying the results of those stories. Varying styles and experimenting with different formats might help you to see whether something new comes out during discussions, or results in quicker or more reliable implementation and better shared understanding. Try these ideas for example:

  * Name stories early, but add details later, after a conversation
  * Let the Product Owner write the 'why' phrase, let the developers write the 'what' phrase
  * Avoid spelling out common or obvious solutions
  * Think about more other stakeholders who would be interested in or affected by the story, not just the primary actor
  * Ask a question, like "How can we reduce reconciliation time?"
  * Use a picture instead of words - Chris Matts recalled a story card that only had these Kanji symbols, meaning "Japan", to represent a story about Japanese translation.

For more advice and ideas to improve your stories, see our new book:

_"50 Quick Ideas to Improve Your User Stories"_

By Gojko Adzic and David Evans
