# Designing Voice Experiences

_Captured: 2017-07-28 at 08:29 from [www.smashingmagazine.com](https://www.smashingmagazine.com/2017/05/designing-voice-experiences/)_

Voice-based interfaces are becoming commonplace. Voice assistants such as Siri and Cortana have been around for a few years, but this past holiday season, voice-driven devices from Amazon and Google made their way into millions of homes.

Recent [analysis from VoiceLabs](http://voicelabs.co/2017/01/15/the-2017-voice-report/) estimates that 24.5 million voice-driven devices will be shipped this year, almost four times as many as last year. As experience designers, we now have the opportunity to design voice experiences and interfaces!

A new interface does not mean that we have to disregard everything we have successfully applied to previous interfaces; we will need to adapt our process for the nuances of voice-driven interfaces, including conversational interactions and the lack of a screen. We will look at how a typical genie in a bottle works, discuss **the steps involved in designing voice experiences**, and illustrate these steps by designing a voice app for Alexa (or Skill, as Amazon calls it).

Just as mobile apps run on an OS and a device, three layers have to work together to enable voice interactions:

![Layers of Voice User Interface](https://www.smashingmagazine.com/wp-content/uploads/2017/03/voice-interface-stack-500w-opt.png)

> _The layers that enable voice interactions_

  1. voice app (Amazon Skills and Actions for Google);
  2. artificial intelligence platform (Amazon Alexa, Google Assistant, Apple Siri, Microsoft Cortana);
  3. device (Echo, Home, smartphones, computers).

Each layer uses the one below and supports the one above it. The voice interface lies in the upper two layers, both of which reside in the cloud, not on the device itself.

Let's peek under the hood to see how these layers work together, using the Alexa Jeopardy! Skill as an example.

![How voice interfaces work - Jeopardy skill example](https://www.smashingmagazine.com/wp-content/uploads/2017/03/voice-interface-stack-example-780w-opt.png)

> _The layers that enable voice interactions. (View large version)_

Voice-driven devices such as the Amazon Echo and Google Home are constantly listening, waiting for a wake word ("Alexa…" or "OK, Google…") to jump into action. Once activated, the device sends the audio that follows to the AI platform in the cloud ("… play Jeopardy!"). The platform uses a combination of [automatic speech recognition](https://en.wikipedia.org/wiki/Speech_recognition) (ASR) and [natural language understanding](https://en.wikipedia.org/wiki/Natural_language_understanding) (NLU) to decipher the user's intent (to start a trivia game) and send it to the supporting app (Jeopardy! J6 Skill on Alexa). The app processes the request and responds through text (and a visual if applicable). The platform converts the text to speech and plays it through the device ("Welcome to Jeopardy J6. Here are today's clues…"). All this in matter of seconds.

Last year, Mark Zuckerberg took on a personal challenge to [build a simple AI](https://www.facebook.com/notes/mark-zuckerberg/building-jarvis/10154361492931634) to run his home. He did, called it Jarvis and gave it the [voice of Morgan Freeman](https://www.facebook.com/zuck/videos/10103353413344571/).

![Mark Zuckerberg introduces Morgan Freeman to the AI that uses his voice](https://www.smashingmagazine.com/wp-content/uploads/2017/03/zuckerberg-freeman-500w-opt.jpg)

> _Mark Zuckerberg introduces Morgan Freeman to the AI that uses his voice. (Image: [Mark Zuckerberg](https://www.facebook.com/photo.php?fbid=10103410869691591&set=pb.4.-2207520000.1486318705.&type=3&theater))_

The rest of us who don't have the ability or resources to do the same can get away with building voice apps that run on complex AI platforms that have already been built. This frees us to only have to worry about the design and development of the voice app, that too with a simplified development process. [Amazon](https://developer.amazon.com/alexa-skills-kit) and [Google](https://developers.google.com/actions/) have provided open access to templates, code, and detailed step-by-step instructions to build different types of voice apps, to the point that even non-developers could develop an app in around an hour!

Their investment in simplifying app development is paying off, with [thousands of new voice apps being launched every month](http://voicebot.ai/2017/02/28/amazon-alexa-now-has-10k-skills-including-europe/). The growth in voice apps brings back memories of the '90s web gold rush, as well as the explosion of mobile apps that followed the launch of app stores.

![Breakdown of Alexa Skills by category as of May 2017](https://www.smashingmagazine.com/wp-content/uploads/2017/04/alexa-skills-category-may-2017-780w-opt-copy.png)

> _Breakdown of Alexa Skills by category as of May 2017. (View large version)_

In a crowded voice marketplace, good design is what will differentiate your voice app from the hundreds of other similar apps.

Designing a good voice user experience is a five-step process that should take place before starting development. Though jumping straight into development might be tempting, the time spent getting the design right is time well spent.

![Steps in designing voice experiences](https://www.smashingmagazine.com/wp-content/uploads/2017/03/designing-voice-experiences-steps-780w-opt.png)

> _The steps in designing voice experiences (View large version)_

We will discuss and apply each step to design a voice app, which could easily be developed using one of many [Skill templates for Alexa](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/content/alexa-skills-developer-training#templates).

The design journey begins with the question, "How will this voice app provide value to my users?" This question applies whether you are developing a standalone voice app (like our example) or whether your voice app is just one of many touchpoints for your customers. Take into consideration why and where people use voice apps. People use voice interfaces because of the benefits of hands-free interaction, the speed of interaction and the ease of use, primarily using it at home or in the car, as shown in Mary Meeker's [2016 Internet Trends Report](http://www.kpcb.com/blog/2016-internet-trends-report).

![Top reasons to use voice interfaces](https://www.smashingmagazine.com/wp-content/uploads/2017/03/voice-reasons-780w-opt.png)

> _Top reasons to use voice interfaces (callouts by author) (Source: [KPCB](http://www.kpcb.com/blog/2016-internet-trends-report)) ([View large version](https://www.smashingmagazine.com/wp-content/uploads/2017/03/voice-reasons-large-opt.png))_

The key is to find consistent user needs that are easier or more convenient through a voice app rather than a phone or a computer. Some examples include banks providing account information or a moviegoer finding new movies playing nearby.

If you have competitors who already have voice apps, take into consideration what they are doing and the reviews and feedback their apps have received in the app marketplace (such as [Amazon's Alexa Skill Store](https://www.amazon.com/b?ie=UTF8&node=13727921011)). The aim is not to blindly imitate, but to be aware of the capabilities bar that has been set, as well as user expectations.

(At the time of writing this, there were over 1,500 "knowledge and trivia" Alexa Skills, making it the most crowded Skill categories on Amazon. However, there wasn't a single trivia skill catering to the area of user experience. To illustrate the voice design process, we will create a UX design skill, for our readers to test their knowledge or maybe even to learn something new.)

During this step, we will define the personality of our app and the capabilities it will have.

When designing voice interfaces, we don't have access to many of the visual elements we use in web and mobile interfaces to show a personality. The personality has to come through the voice and tone of verbal interactions. And unlike Zuckerberg, who hears Freeman's soothing voice, we are constrained to hearing the default voice of the device. That makes tone and wording crucial in conveying the personality we want to convey.

The good news is that most of the groundwork in this area should have already been completed and documented in a corporate brand guide or website style guide (hint: look for the "tone of voice" section). Leverage those guidelines for your voice app, as well to maintain a consistent personality across channels and touchpoints.

When I think of personality and tone, the Virgin Group immediately comes to mind. They clearly define who they are and how they convey that to users. For Virgin America, the ideal tone is "hip, easygoing, informal, playful and tongue in cheek," and it comes across clearly in all their communication.

![Virgin America brand personality](https://www.smashingmagazine.com/wp-content/uploads/2017/03/virgin-brand-personality-730w-opt.png)

> _Virgin America's brand personality (Source: Virgin America)_

If you've ever asked Alexa to sing or tried any of the numerous [Alexa Easter Eggs](https://turbofuture.com/consumer-electronics/200-Amusing-Amazon-Echo-Easter-Eggs), then you'll know she has a personality of her own. Curious, I reached out to the team responsible for her personality, and here's what they had to say:

> When architecting Alexa's voice, we tried to give her a personality that reflects the attributes we value most at Amazon. We wanted her to feel helpful, humble and smart, while still maintaining a sense of fun. This is an ongoing process, and we expect the voice of Alexa will evolve as more developers focus on making her smarter.

Personality can also be reflected in the app's name, icon and description that are displayed to users in the app directory listing, as well as in the name used to invoke the app (the invocation name). So, make sure it shines through while publishing your app.

For our UX Design skill, we could take a straightforward or a funny approach, and that would be reflected in the wording of our quiz' Q&A options.

An example of a **normal tone** would be:

> Which UX design principle favors simplicity over complexity?
> 
>   1. Occam's Razor
>   2. Hick's Law
>   3. Aesthetic-usability effect
>   4. Satisficing

And an example of a **funny tone** would be:

> Apparently, there's a UX design principle that favors simplicity over complexity. Really! Can you guess what it's called?
> 
>   1. Occam's Razor: The best a UX guy can get.
>   2. Hick's Law: Sounds like something a UX bumpkin would come up with.
>   3. Aesthetic-usability effect: That's some fancy UX jargon.
>   4. Satisficing: I can't get no satisficing… apologies to the Rolling Stones.

Yeah, let's stick with normal.

This is where you carefully think of the functionality that will be valuable for your voice app's users. Revisit your work from the first step to identify the capabilities that are core or related to your business. Sometimes offering core capabilities is a no-brainer -- such as a bank offering information on balance, transactions and due dates. Others offer value in the form of related features, such as Tide's stain-removal guide voice app, or Glad's (makers of food storage and trash bags) voice apps, one of which helps users to remember where they stored their leftovers, or the other one that allows users to check which items should be recycled or disposed of in the trash.

If you did a similar exercise when going from web to mobile, that can serve as a starting point. For voice capabilities, consider what capabilities would benefit your users on a voice-driven device in a shared space. If a Skill has security or privacy implications, consider adding a level of protection (the Capital One Alexa Skill allows users to create a personal key for account access). While you may end up with a laundry list of functionality that would work over voice, start with one to five core capabilities, and use voice analytics to update and improve after launch.

The core capabilities of a UX design Skill could be:

  1. provide a UX design principle on demand;
  2. quiz the user (single player) on a random UX principle;
  3. quiz the user (single player) on multiple UX principle, and keep score;
  4. hold a UX quiz competition with multiple players.

Because we are building this UX design Skill using Amazon's Skill templates, our choices are currently restricted to either the first (fact skill template) or third (trivia skill template) option above. Assuming that our research has shown that our users would find a quiz more valuable than just hearing a UX principle recited, our core capability will be to quiz the user on UX principles and to keep score.

Now that you have shortlisted the capabilities of your voice app, start focusing on the detailed conversation flow that the app will have with its users. Human conversation is complex; it often has many twists and turns and may pivot anytime, with people often jumping from one topic to another. Voice AI platforms still have a long way to go to match that level of complexity, so you have to teach your Skill how to respond to users.

Your voice app can only support the capabilities you have defined in the previous step, but users always have the ability to ask the app anything and in any format. Detailing a conversation flow allows you to respond to the user, or to drive the conversation towards what the app can do for the user.

For each capability that the voice app will support, start creating conversational dialogues between the user and the app, similar to dialogues in a screenplay. As you write these dialogues, remember the personality as well as voice and tone characteristics. Start creating and curating the actual content for your voice app; for our quiz, this would mean building the list of quiz questions.

Begin with the "happy path" -- a conversational flow in which the voice app can respond to the user's request without any exceptions or errors. Then, move on to detailing the conversational flow for exceptions (in which the user does not provide complete information) and errors (in which the voice app does not understand or cannot do what the user is asking).

Because the conversation will be heard and not read, a good practice is to read it out loud to see if it sounds like a natural spoken conversation, and to check that it conveys the tone of voice you've intended.

If your voice app needs to supplement the conversation with content displayed on the phone app, design these interactions together, so that they appear seamless to the user. For instance, Tide's stain-removal Skill informs the user that they could also refer to the stain-removal steps in the Alexa app, in addition to hearing the instructions. This may soon be required if the [rumors of a touchscreen on the new Echo](https://www.engadget.com/2016/11/29/amazon-touchscreen-speaker-leak/) are true.

Here is a sample dialogue for the happy path our UX design Skill's core capability:

> **User**: "Alexa, start the UX design quiz."
> 
> **Alexa**: "I will ask you five questions, with multiple choice answers. Try to get as many right as you can. Just say the number of the answer. Let's begin. Question 1…"
> 
> **User**: [responds correctly]
> 
> **Alexa**: "That's correct! Your score is 1. Here's question 2…"
> 
> **User**: [responds incorrectly]
> 
> **Alexa**: "Oops, that's the wrong answer. The correct answer is [correct answer]. Your score is 1. Here's question 3…"
> 
> …
> 
> **Alexa** (at the end of five questions): "That's correct! You got four out of five questions correct. Thank you for playing!"

People don't always use the same words to say the same thing, and voice apps need to be taught that. Phrase-mapping is an exercise to teach voice apps to accommodate variation in the way users phrase their requests.

For each conversational path that you detailed in the previous step, think about the different ways users could word those requests. Then break down the wording of each request, and identify word variations and synonyms that they might use, taking into account any regional variations and dialects. You will have your hands full if your voice app deals with sweetened carbonated beverages (soda, pop, coke, tonic, soft drink, fizzy drink), long sandwiches (sub, grinder, hoagie, hero, poor boy, bomber, Italian sandwich, baguette) or athletic footwear (sneakers, shoes, gym shoes, sand shoes, jumpers, tennis shoes, running shoes, runners, trainers).

Make this list of variations as complete and exhaustive as possible, so that your voice app can understand user requests. Alexa needs these variations in the form of "utterances" and recommends providing "… [as many representative phrases as possible](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/defining-the-voice-interface#h2_sample_utterances)." Depending on the capabilities of your voice app, the number of utterances could easily run into the hundreds, but there are ways to [simplify the generation of utterances](http://www.makermusings.com/2015/07/21/defining-utterances-for-the-alexa-skills-kit/).

Here's a sample phrase-mapping for a capability of our UX design quiz. Alexa's AI platform does a good job of translating user intent for Skills based on their templates. However, if you make changes (like we changed "trivia game" to "quiz"), then these phrases will have to be added.

![Sample phrase mapping](https://www.smashingmagazine.com/wp-content/uploads/2017/03/phrase-mapping-780w-opt.png)

> _[View large version](https://www.smashingmagazine.com/wp-content/uploads/2017/03/phrase-mapping-large-opt.png)_

The final step in the design process is to validate and refine the voice application before spending time and effort on development. During the "detail" step, reading the conversation flows aloud helped to make sure that they sounded natural and conversational. The current step involves testing the voice interface with users.

The simplest way to test is using the Wizard of Oz technique, with a person playing the role of the voice-driven device and responding to the user based on the voice interface script. Another option is to use prototyping software such as [SaySpring](https://www.sayspring.com/) to create and test interactive prototypes.

If your voice app is being built using code templates (as our app is), then it might be easier to create the app and test it using testing tools provided by [Amazon](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/testing-an-alexa-skill#h2_servicesim) and [Google](https://developers.google.com/actions/tools/web-simulator) within the Skill development area (as shown below), or in test mode on an actual device.

![Alexa skill simulator](https://www.smashingmagazine.com/wp-content/uploads/2017/03/alexa-simulator-500w-opt.png)

This testing will give you a good feel for the voice experience in the real world, including handling of errors, repetitive responses, and unnatural, forced or machine-like replies.

Now that the voice experience has been designed, it is time to move to the build-test-submit phase. Each platform has detailed guides and tutorials to help anyone build and test skills, including [Alexa Skills Kit](https://developer.amazon.com/alexa-skills-kit#Ready%20to%20start%3F), [Develop Actions for Google](https://developers.google.com/actions/develop/conversation), and [Cortana](https://developer.microsoft.com/en-us/cortana), which offers to reuse your custom Alexa skill code!

Think about your feedback loop and the analytics that will help you to understand usage of your voice app. You can get Skill metrics (users, sessions, utterances, intents) within your developer account without any additional coding, but advanced analytics are available through free services such as [VoiceLabs](http://voicelabs.co/) (I could not get it to work, probably due to my lack of coding skills or the lack of a _VoiceLabs for Dummies_ setup guide).

After you finish building and testing your voice app, the last step is a [streamlined submission process](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/publishing-an-alexa-skill). Because the Alexa Skill marketplace has rapidly grown, discovering new and useful apps is getting difficult. Until Amazon improves this, use visible elements of your voice app listing to help users find and try your Skill, including a catchy and relevant skill icon, name and description.

The companion skill that was built as an illustration can be taken for a test drive on the Amazon Alexa Skill store: [UX Design Quiz](https://www.amazon.com/dp/B06X6FHKSL)

Here are a few guiding principles for designing voice experiences. More principles and detailed do's and don'ts are offered by [Amazon](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/alexa-skills-kit-voice-design-best-practices) and [Google](https://developers.google.com/actions/design).

Introduce the app and the ways the user can engage with it.

> Welcome to UX Design Quiz. I will ask you five questions about UX design and see how many you get right. You can ask me to repeat a question or pause if you need to. Would you like to start a new quiz?

With a voice user interface, the user has to use their short-term memory while interacting with the voice app. So, keep it short and sweet.

> **Alexa**: "This principle is attributed to a 14th-century logician and Franciscan friar and is named after the village in the English county of Surrey where he was born. In a nutshell, it states that simplicity is better than complexity. This problem-solving principle can easily be applied to user experience design, by going for the simpler design solution. What is this principle called?
> 
>   1. Your first option is Occam's Razor, sometimes known as Ockham's razor, or the law of parsimony.
>   2. Your next option is Hick's Law, also known as the Hick-Hyman Law.
>   3. Your next option is the aesthetic-usability effect.
>   4. Your last option is called "satisficing," not to be confused with "satisfying" or "sacrificing."
> 
> Please say A, B, C, or D to make your selection."
> 
> **User**: "Huh?! Alexa, repeat. On second thought, end quiz!"

> Instruction: "Please say your date of birth in the month/day/year format."
> 
> Example: "Please say your date of birth, like April 15, 1990."

This is a balancing act. Too much and it gets tiresome quickly.

If you ask Alexa to turn off the lights, you can see it happen and do not need a verbal confirmation, although she sometimes confirms with a short "OK."

![Don't interfere, reduce repetitiveness](https://www.smashingmagazine.com/wp-content/uploads/2017/03/leftover-skill-feedback-570w-opt.png)

> _User feedback for the Glad Leftover Skill highlights two principles above._

Things will go wrong: design for those situations. Examples include unintelligible questions or information, incomplete information, silence or requests that cannot be handled. Acknowledge, and give the user options to recover.

![Respect user privacy and security](https://www.smashingmagazine.com/wp-content/uploads/2017/03/bank-skill-feedback-500w-opt.png)

> _User feedback for a bank Skill highlights issues with security, despite passing [Alexa Skill Security requirements](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/alexa-skills-kit-security-testing)._

> Anytime you're dealing with trying to interact with a human, you have to think of humans as very advanced operating systems. Your highest goal is to try to emulate them.
> 
> - K.K Barrett, Her movie production designer, Wired, 2014

If you haven't seen the movie Her, take a couple of hours to watch this futuristic movie about a lonely writer who develops a relationship with an operating system. While it is science fiction, in today's world, voice experiences are increasing with the adoption of standalone voice-driven devices, such as the Amazon Echo family and Google Home. Developing a voice app is a relatively simple, template-driven process, with IKEA-like instructions provided by Amazon and Google in an attempt to establish their platforms. Though jumping into development may be tempting, a good voice user experience doesn't just happen; it has to be designed, going through the steps described in this article.

Please use the comments area to share any other feedback, tips and resources with other readers.

_(da, vf, yk, al, il)_
