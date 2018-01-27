# UX, You Only Need One Button

_Captured: 2017-12-27 at 13:20 from [dzone.com](https://dzone.com/articles/ux-you-only-need-one-button?edition=347121&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-24)_

[Get deep insight into Node.js applications](https://dzone.com/go?i=200144&u=http%3A%2F%2Fpages.nodesource.com%2Fnsolid-free-trial-dzwd.html%3Futm_campaign%3DDZONE%26utm_source%3Dbumper%26utm_content%3Dbtext) with real-time metrics, CPU profiling, and heap snapshots with N|Solid from NodeSource. [Learn more](https://dzone.com/go?i=200144&u=http%3A%2F%2Fpages.nodesource.com%2Fnsolid-free-trial-dzwd.html%3Futm_campaign%3DDZONE%26utm_source%3Dbumper%26utm_content%3Dbtext).

Practically every single website and web app out there looks like it could _"solve everything,"_ from cooking recipes to splitting atoms. The web is not alone here. Below is an image of Microsoft Word. Jesse James Garrett, the guy who coined the terms Ajax and UX, once famously said about Microsoft Office, _"That's not a solution, that's a problem. This is the equivalent of saying we couldn't solve it, and hence we left the problem for you to solve."_

![Image title](https://dzone.com/storage/temp/7131664-shot-classic-justify.png)

How many menu commands do you think there are in Microsoft Office? 1,000? 5,000? 10,000? How many of these menu items could you find if asked? And how many of them do you know what they do?

If you somehow were able to find a guy who had never used a computer and asked him if he could use the above Microsoft Office program, do you think he'd understand where to even begin? Below is an alternative UX, with a single button, that can still do everything Microsoft Word can do. Which do you think is more easily understood?

![Image title](https://dzone.com/storage/temp/7131693-one-button-to-rule-em-all.png)

Which of the two above software systems would you want to use, if all other parameters were equal?

In fact, when it comes to computer interactions, we **already have this amazing tool: Speech**. It allows us to communicate in our mother tongue, and, if intelligently parsed by the computer, allows our computers to understand what we want to accomplish.

I have created a web component that allows your computer to understand what you're saying, and translate your phrases and words into computer code. It is called [Hyperlang or Hyperlanguage](https://github.com/polterguy/hyperlang). It is basically a drop-in replacement for every single UX element you could possibly create yourself, allowing you to control any web applications you could possibly create, with any language you'd want to use. It supports English, Swedish, Spanish, Swahili, ~60 other languages - and probably Klingon or Vulcan if you tried hard enough.

It allows you to easily configure new commands if you have _"root privileges,"_ by simply speaking some phrase it doesn't understand, and say _"I will teach you."_ At which point a Hyperlambda CodeMirror module is automatically loaded, allowing you to type in some code you want to associate with your phrase.

It features a nice _"never-ending scrolling experience"_ (pun!) for administrating your database of commands, and it is capable of introspective analysis of itself. It is open source, free software, and you can [start using it today](https://github.com/polterguy/phosphorusfive/releases)! It is created in .NET and C# and builds upon Hyperlambda and Phosphorus Five, and its internals are probably easily understood by any .NET system developer in a couple of days.

To see it in action, you can check out this article, where I have a [YouTube video demonstrating the system](https://gaiasoul.com/2017/11/06/ux-one-button-to-rule-em-all/). In this article, you can also find installation instructions, and an example _"dictionary file."_

Notice, for the record, I have spent 7 days creating this, and it is still in BETA. Have that in mind if you try it out.

Node.js application metrics sent directly to any statsd-compliant system. [Get N|Solid](https://dzone.com/go?i=222222&u=http%3A%2F%2Fpages.nodesource.com%2Fnsolid-free-trial-statsd-dz.html%3Futm_campaign%3DDZONE%26utm_source%3Dbumper%26utm_content%3Dbtext)

Opinions expressed by DZone contributors are their own.
