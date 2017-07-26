# RawHtmlWiki

_Captured: 2015-11-09 at 17:10 from [meatballwiki.org](http://meatballwiki.org/wiki/RawHtmlWiki)_

[MeatballWiki](http://meatballwiki.org/wiki/MeatballWiki) | [RecentChanges](http://meatballwiki.org/wiki/RecentChanges) | [Random Page](http://meatballwiki.org/wiki/action=random) | [Indices](http://meatballwiki.org/wiki/IndexingScheme) | [Categories](http://meatballwiki.org/wiki/back=CategoryCategory)  
Why not allow Raw HTML in [MeatballWiki](http://meatballwiki.org/wiki/MeatballWiki). (Its a trivial patch to suppress wiki-specific formatting and implicit links, when a page starts with <HTML> or something like that). With Raw HTML you automatically get scripting capability.). Of cause we could impose additional security measures on this feature. Communities like [Google:MySpace](http://www.google.com/search?q=MySpace) already allow Gadgets on the profile pages of their members. As alternative [WikiEngine](http://meatballwiki.org/wiki/WikiEngine) Builders could integrate [[Wikipedia:WikiGadgets]](http://en.wikipedia.org/wiki/Wikipedia:GADGETS) \-- [FridemarPache](http://meatballwiki.org/wiki/FridemarPache)

**Pro**

  * It can give substantial support to building a friendly [GlobalBrain](http://meatballwiki.org/wiki/GlobalBrain)
  * It's an easy way to implement hypermedia etc. 
  * Lots of people already know HTML: for anyone used to, say, [SlashDot](http://meatballwiki.org/wiki/SlashDot) or [AdvoGato](http://meatballwiki.org/wiki/AdvoGato), there's nothing new to learn on a HTML wiki 
  * It allows collaborative literary programming. 
  * You can add multimedia. 
  * It looks cool. 
  * It reduces the learning curve by removing yet another markup. 
    * _except..._ the community conventions to prevent rampant destruction of the site might be harder to grok. 
  * New features of DynamicHtml[?](http://meatballwiki.org/wiki/action=edit&id=DynamicHtml) can be explored and mutated with less effort in a community than otherwise 
  * CrossBrowserCompatibility[?](http://meatballwiki.org/wiki/action=edit&id=CrossBrowserCompatibility) of JScript and [JavaScript](http://meatballwiki.org/wiki/JavaScript) can be easier tested collaboratively 

**Con**

  * One of the problems with using anything more complex than text is the ability of the community to support it. 
  * Raw HTML means losing too much control. The syntax and features are all decided, and some of those decisions may not suit the Wiki owner. For example, a site might not want to allow blinking text at all; it might want to reserve certain colours to mark [MetaContent](http://meatballwiki.org/wiki/MetaContent). 
  * From the contributors point of view, HTML involves much verbiage. [WardsWiki](http://meatballwiki.org/wiki/WardsWiki)-style markup involves a lot less typing, which is nice when the primary text entry method is an HTML form 
  * Full HTML allows users to exploit browser security holes, like insecure plugins, third-party cookie retrieval, and Java implementation bugs. Many users still use old browsers that are vulnerable. 
    * Even new browsers may be vulnerable. Since this page was last edited multiple exploitable flaws have been found in current browsers. See <http://www.nando.net/technology/story/body/0,1634,500237093-500347090-502004906-0,00.html> for a story on a recent (August 2000) vulnerability. 
  * It reduces the overall accessibility of the site. It's trivial to ensure the site is viewable by all people when you control the markup; it's impossible (and unlikely) if you allow arbitrary markup. <FONT SIZE=2></FONT> may be popular, but it isn't a good thing to do to people like me who like to jack the font size up on high resolutions. 
  * It's easy to make a mistake that will wreck the entire page. Wiki markup is remarkably resilient to errors. 
  * To allow raw HTML creates two classes of users. Those who can cope with HTML and those who don't and are repelled. Raw HTML reduces the chance that wiki will make it to a general audience. 
  * **[HtmlIsAssembler](http://meatballwiki.org/wiki/HtmlIsAssembler)**
  * Who includes the Wiki - navigation? 

**Other Comments**

We can provide an HTML subset. That gives most of the advantages (of familiarity) without the drawbacks of hypermedia.

**Existing practice**

  * [WikiHTML](http://meatballwiki.org/wiki/WikiHTML) uses HTML <http://www.wikihtml.com>
  * [WardsWiki](http://meatballwiki.org/wiki/WardsWiki) doesn't. See [Wiki:TextFormattingRules](http://c2.com/cgi/wiki?TextFormattingRules)
  * **usemod.com** doesn't. The site admin ([CliffordAdams](http://meatballwiki.org/wiki/CliffordAdams)) is interested in HTML support in wikis, but is not willing to host an arbitrary-HTML wiki site. [UseModWiki](http://meatballwiki.org/wiki/UseModWiki) 0.8 supports a raw HTML option, but it is not enabled by default. 
  * **CLiki** uses HTML, because its author is lazy (his words) and didn't want to invent another markup language. _(If I had the necessary tuit supply, I'd do an HTML or HTMLish subset a la [AdvoGato](http://meatballwiki.org/wiki/AdvoGato). One day ...)_
  * [AdvoGato](http://meatballwiki.org/wiki/AdvoGato) uses an HTML subset 
  * **wikis.com** allows HTML, along with an interesting set of macro commands. It also has almost as many features as all other wikis combined. For a sample of HTML usage, see [FoxWiki:Survey_MonitorResolution~Wiki](http://fox.wikis.com/wc.dll?Wiki~Survey_MonitorResolution~Wiki). ([FoxWiki](http://meatballwiki.org/wiki/FoxWiki) was the inspiration for several features on [UseModWiki](http://meatballwiki.org/wiki/UseModWiki).) 
  * [PhpWiki](http://meatballwiki.org/wiki/PhpWiki) supports embedded HTML, if the administrator allows it. 
  * [WxWikiServer](http://meatballwiki.org/wiki/WxWikiServer) supports embedded HTML by default - but it can be turned off. There are two seperate syntaxes for it - 
    * Multiline uses a doxygen-style syntax. HTML is enclosed between @html and @endhtml. 
    * Single line uses [$html:<tags>] 
  * Siggma's Wiki: <http://siggma.net/wiki>, depends on the wysiwyg editing in [InternetExplorer](http://meatballwiki.org/wiki/InternetExplorer) to keep the code readable. Only minimal support is available to add layout to a page, to keep the pages clean. Non-IE users get the raw HTML code sadly enough 

What can we learn from these?

  * ''One "lesson" that I've learned is that [WxWikiServer](http://meatballwiki.org/wiki/WxWikiServer) (and its support for raw html) is a great productivity tool that has increased the rate at which I now publish pages by a factor of four in the last few months that I've been using it. I would be pleased to explain what it is about this tool that works for me if anyone in this community cares enough to activate WxWikiServerUses[?](http://meatballwiki.org/wiki/action=edit&id=WxWikiServerUses). -- [HansWobbe](http://meatballwiki.org/wiki/HansWobbe)

## Discussion

_ needs to be adapted to the intro, which itself needs actualisation, responding to the current (2009) trend of a socially programmable Web_.

Speaking of multimedia, I added <EMBED/> to [UseModWiki](http://meatballwiki.org/wiki/UseModWiki) in an afternoon. Perl's a lot more forgiving to people with Carpal Tunnel Syndrome than Java, so I hacked it in. (It's something we need on the Intranet). I really like the idea of &StoreRaw(). It made my life easier. I guess now I'm going to have to submit patches along with feature requests, eh? -- [SunirShah](http://meatballwiki.org/wiki/SunirShah)

What we're debating is another [TechnologySolution](http://meatballwiki.org/wiki/TechnologySolution) vs. [CommunitySolution](http://meatballwiki.org/wiki/CommunitySolution).

[[CategoryWikiTechnology](http://meatballwiki.org/wiki/CategoryWikiTechnology)]

Long before I learned about wikis, I worked up a first-token of line dot-coded system (Hy-Dyn, for Hypertext Dynamic -- delusions of grandeur are always with us...) for getting HTML markup into submissions via textarea boxes. It was macro-ish, and look much like nroff mark-up. The codes were transmuted into HTML for display by the Hy-Dyn Perl engine. I even had a two-way Hy-Dyn-VAX Document filter. Such a system would gain the formatting of HTML without the security concerns. A technology solution to lubricate community solutions? -- [JerryMuelver](http://meatballwiki.org/wiki/JerryMuelver)

### The Case of the Advogato Virus

Recently [AdvoGato](http://meatballwiki.org/wiki/AdvoGato) was subjected to what was termed the [[Advogato Virus]](http://advogato.org/article/545.html) which exploited the (inadvertent) use of raw HTML in the name fields of users. The virus was essentially a blob of raw HTML and script in the name field of a person's profile. Upon visiting an infected person's profile, the scripted virus would launch an IFRAME and alter the reader's profile on Advogato to also include the virus. Although even most experts probably don't think of intrasite infection as a problem, and some users may think that running scripts inside the sandbox of a browser is safe (although that would be foolish), raw HTML enables any number of clever attacks on the unsuspecting reader. It's far easier to build a syntax constructively (i.e. from the ground up) than by exclusion (i.e. by "sanitizing" raw HTML) as it's much easier to prove formally.

[CategoryCase](http://meatballwiki.org/wiki/CategoryCase) html<table border=1000> <td style ="{position: fixed; width:100}">sdf</td><td>sdfsdfsdf</td>

_When I worked on a wiki on HTML, I had a go at the sanitizing option anyway. Since I agree that allowing the full set of layout-options of HTML allows pages to get ugly and heavy-loaded with fonts and colors, I guess a HTML-wiki could do without the iframe and script tags altogether. Events and suspicious src="javascript fragments are filtered out also. If you might now more dangerous HTML contstructions, please let me know. -- [StijnSanders](http://meatballwiki.org/wiki/StijnSanders)_

### From a basic user perspective

My need as a basic user is probably to be seen from the community side. Everyday I need to produce content that will be sent to wikis, forums (like phpbb2), email, blogs or attached doc file depending on their use and goal. I am just tired of using different tag format and editors for each different tool, specialy when one same content has to be used and reproduced in different format for different medias for different purposes (example: a wiki + a forum). My dream would be to play with a universal text editor that would provide the main editorial functions such as text formating, tables, image insertion. Is it too much to ask for? -- Jean-François (JeanFrancoisNoubel[?](http://meatballwiki.org/wiki/action=edit&id=JeanFrancoisNoubel))

No, the answer is _plain text_. -- [AlexSchroeder](http://meatballwiki.org/wiki/AlexSchroeder)

One workaround I seem to be using more and more is reStructured Text. When I type it into systems that don't understand it, it looks like highly readable plain text, and so it has most of the benefits of using plain text. See [Wiki:ReStructuredText](http://c2.com/cgi/wiki?ReStructuredText), [["A ReStructuredText Primer"]](http://docutils.sourceforge.net/docs/user/rst/quickstart.html), [CommunityWiki:PlainText](http://www.communitywiki.org/PlainText), [Wiki:PowerOfPlainText](http://c2.com/cgi/wiki?PowerOfPlainText). -- [DavidCary](http://meatballwiki.org/wiki/DavidCary)

''moved from [InterMap](http://meatballwiki.org/wiki/InterMap), part of a discussion of a [PublicallyEditableInterMap](http://meatballwiki.org/wiki/PublicallyEditableInterMap)

Possible consequences of browsing arbitrary HTML include:

  * Performing actions on third-party websites. (There was an example posting of this recently on [SlashDot](http://meatballwiki.org/wiki/SlashDot). The post contained a link which would automatically submit a posting under the user's name/id (using their cookies), using text chosen by the attacker. All the unwary user had to do was click on an ordinary-looking link (without looking at the status line, which displayed the target URL). And, of course, if you allow arbitrary HTML, you can easily add [JavaScript](http://meatballwiki.org/wiki/JavaScript) to confuse the status line.) 
  * Reading arbitrary files on the local system. (Recent versions of Netscape have had this flaw.) 
  * Executing arbitrary programs locally. This could include installing backdoor programs or other security holes. 

The usual first response to these flaws is to suggest disabling features like Java, Javascript, etc. Unfortunately, the users who have old browsers are probably less likely to disable these options. --[CliffordAdams](http://meatballwiki.org/wiki/CliffordAdams) (who doesn't visit [MetaBaby](http://meatballwiki.org/wiki/MetaBaby) anymore because of these issues) [[jual cctv murah]](http://www.manfaatalam.com/daftar-harga-jual-kamera-cctv-murah-wireless-outdoor-terbaik.html) [[cctv murah]](http://www.manfaatalam.com)
