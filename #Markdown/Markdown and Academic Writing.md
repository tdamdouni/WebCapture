# Markdown and Academic Writing

_Captured: 2015-09-29 at 00:14 from [2012-2013.chriskrycho.com](http://2012-2013.chriskrycho.com/web/markdown-and-academic-writing/)_

Markdown took over my writing life this semester, as I've [mentioned](http://2012-2013.chriskrycho.com/web/why-i-love-markdown). I took nearly all my class notes in Markdown (after a brief interval of using Evernote and an even briefer pass with Microsoft Word--neither of them quite worked for me, especially as my addiction grew). The only hiccup with my growing delight in the combination of [Markdown](http://daringfireball.net/projects/markdown/) and [Byword](http://bywordapp.com/) was the challenge of writing papers in them. There was little question for me that it was worth the few additional wrinkles it entailed, however: a nice clean writing environment and the obviousness of Markdown (not to mention the revision-history- and version-control-friendly nature of plain text) inclined me _strongly_ toward using it.

For main paper content--all those lovely paragraphs I hammered out--Markdown was sublime. The trick for my papers this semester, though, was something core to any academic writing: footnotes. The problem isn't Markdown; just about every version out there (except the original) has support for a simple footnote syntax:
    
    
    Writing along and now we need a footnote.[^1] Then we go merrily along on our way again.
    
    [^1]: Here's the content for that footnote. Simple enough---obvious, even.
    

No, the real problem is _keeping track_ of those footnotes. My habit for blog posts and even class notes was to simply put the footnotes at the bottom of the piece. That makes sense for those kinds of content: it's easy to keep track of the order of the notes, as one generally isn't massively rearranging blog posts, much less class notes. So I'd simply go in order: `[^1]`, `[^2]`, and so on.

Then I wrote my [first major academic paper](http://2012-2013.chriskrycho.com/theology/contra-mundum-athanasius) using Markdown and Byword. Wrangling the footnotes was painful, to say the least. In fact, at one point I switched the order of some of the pieces of the text, and would have had footnotes out of order if, thankfully, the two involved hadn't been referencing the same author on the same page. In any case, I knew I had to come up with a better system when tackling my [second major paper](http://2012-2013.chriskrycho.com/theology/head-coverings-an-exegesis-of-1-corinthians-11_2-16), which promised to entail a much higher number of footnotes, given the greater complexity of the content.

The system I devised worked spectacularly well, so I thought I'd share it in case anyone else is interested in using Markdown for academic writing.

Since footnotes are essentially just another type of link, the text in them can be arbitrary. The text is simply replaced by a numeral--footnotes are always numbers or symbols, and in academic writing, they're nearly always numbers because one quickly runs out of symbols. So Markdown handles this sensibly. Also, the order of the footnotes simply matches the order they appear in the text (even if you have them out of order where you define the footnote content). Thus:[1](http://2012-2013.chriskrycho.com/web/markdown-and-academic-writing/)
    
    
    In which I make a fool of myself.[^hippies] It's not exactly like that's *hard*.[^frogs]
    
    [^frogs]: Because, you see, I have a lot of practice.
    
    [^hippies]: Why in the *world* would anyone ever put their footnotes out of order? Well, one wouldn't---at least, not on purpose.
    

The resulting output will look like this:

> In which I make a fool of myself.1 It's not exactly like that's _hard_.2

> 1Why in the _world_ would anyone ever put their footnotes out of order? Well, one wouldn't--at least, not on purpose.
> 
> 2Because, you see, I have a lot of practice. 

The order has flipped, and the letters have been replaced by numerals, just as one would hope. I put this to good use when working on my paper. As with any well-constructed academic paper, I formulated my argument and made a detailed outline up front. Although the structure of the paper flexed and changed a bit as I went along, this gave me the basic parameters within which I was working at all times. At any given point, I was working in a distinction marked off by at least one top-level (_Introduction_ or _Analysis_ or _Conclusion_) and often by a subhead. Furthermore, I was always in a paragraph. I simply combined these elements to make up the marker for any given footnote.

My footnote text formula was simple: I put together the first letter of each section followed by the paragraph number (each separated by dashes), followed by the footnote number (actually a letter) for that paragraph. Thus, if I was writing the third paragraph of Section II of the Analysis part, the first footnote would have been "numbered" `[^A-II-3a]`.[2](http://2012-2013.chriskrycho.com/web/markdown-and-academic-writing/) The dashes are useful because they made it clear that I was working on _Section 2, Paragraph 3_, not _Analysis, Paragraph 23_. Further, I kept the footnotes immediately next to the paragraph with which they belonged, making it easy to find them and move them as well. Thus, if and when I moved pieces around, I usually only had to change a few numbers related to that footnote--most frequently, just switching the paragraph numbers.

While this was certainly a bit more work than the automatic footnote generation one gets with Microsoft Word, it quickly became a smooth process. Sensible use of find and replace operations made the switches easy enough, and if it took me a few extra minutes to do those elements than it would have in Word, it took me a great deal less time in general because I work so much more quickly in Byword with Markdown than I do in Word.

I hope some people will find the approach I developed useful for their own writing!

### Addendum: Extended Example

I thought it might be useful to provide a slightly longer example to demonstrate what the foonoting looked like in practice. As a point of amusement (as well as illustrating one of the rather intriguing behaviors I laid out earlier), note that footnote `A-III-5a` comes after `A-III-5b` in the text; I switched the sentence order at some point during the editing, but never bothered changing the footnote order because I knew Markdown would generate the output correctly.
    
    
    As if anticipating the ways this passage would be abused, Paul quickly moves to restrict its interpretation in the second sub-chiasm (verses 11--12): neither are women independent of men, nor men of women. Just as woman was originally formed from man, now all men are born of women. Thus, although woman was created from and for man, he cannot claim any superiority on that basis: she has become his source just as he was hers. Even more importantly, men and women are mutually dependent "in the Lord"---language that is common throughout Paul's epistles whenever he is calling believers to unity (cf. Ephesians 2:13--21, Philippians 2:1--2, Galatians 3:28). The ontological relationship between the sexes that God established in creation is to be preserved, but characterized by mutual dependence and unity in Christ---not by domineering or abuse.[^A-III-4a]
    
    [^A-III-4a]: Egalitarian and complementarian commentators are united on this point: see e.g. Belleville, 231; Fee, 522--524; Robertson and Plummer, 234; Lockwood, 375--376.
    
    Each sub-chiasm is relatively clear on its own, but the relationships between the sub-chiasms, and between each of them and the turn in verse 10, are less immediately obvious. Indeed, the primary challenge in interpreting this section---and, arguably, of interpreting the entire passage---is understanding verse 10. Translated somewhat woodenly, the sentence reads, "For this reason, a woman ought to have authority on/over her head, because of the angels" (author's translation). The language of the first sub-chasm suggests that Paul might mean be using "authority" (ἐξουσία) metonymously, despite the linguistic oddity of this move.[^A-III-5b]. If so, the passage reads, "a woman ought to have a symbol of authority on her head."[^A-III-5a] On the other hand, Paul's language in the following sentence ("Nevertheless, in the Lord woman is not independent of man") doubly suggests that he means what the text more naturally says: "a woman ought to have authority over her [own] head."[^A-III-5c] First, the use of "nevertheless" sets the second sub-chiasm in contrast to the turn. Second, the fact that Paul begins by emphasizing that woman is not independent of man (rather than vice versa) suggests that it is her authority, not the man's, that is in view.[^A-III-5d]
    
    [^A-III-5a]: So the ASV, ESV, HCSB, NET, NIV 1984, NASB, NKJV, NRSV. Others go even further: NLT, for example, has "a woman should wear a covering on her head to show she is under authority."
    
    [^A-III-5b]: Fee takes the unique nature of this would-be construction, unparalleled in any other Greek usage, as the basis for dismissing it out of hand (519 n. 23)---apparently ignoring his own suggestion, mere pages later, that "*exousia* was one of the Corinthians' own words.... Very likely that is the reason for this choice of words, which otherwise appears to be so unusual" (521), which satisfactorily explains Paul's otherwise odd linguistic choice.
    
    [^A-III-5c]: Fee, 520.
    
    [^A-III-5d]: Fee, 522--523.
    

The resulting output:

> As if anticipating the ways this passage would be abused, Paul quickly moves to restrict its interpretation in the second sub-chiasm (verses 11-12): neither are women independent of men, nor men of women. Just as woman was originally formed from man, now all men are born of women. Thus, although woman was created from and for man, he cannot claim any superiority on that basis: she has become his source just as he was hers. Even more importantly, men and women are mutually dependent "in the Lord"--language that is common throughout Paul's epistles whenever he is calling believers to unity (cf. Ephesians 2:13-21, Philippians 2:1-2, Galatians 3:28). The ontological relationship between the sexes that God established in creation is to be preserved, but characterized by mutual dependence and unity in Christ--not by domineering or abuse.1
> 
> Each sub-chiasm is relatively clear on its own, but the relationships between the sub-chiasms, and between each of them and the turn in verse 10, are less immediately obvious. Indeed, the primary challenge in interpreting this section--and, arguably, of interpreting the entire passage--is understanding verse 10. Translated somewhat woodenly, the sentence reads, "For this reason, a woman ought to have authority on/over her head, because of the angels" (author's translation). The language of the first sub-chasm suggests that Paul might mean be using "authority" (ἐξουσία) metonymously, despite the linguistic oddity of this move.2. If so, the passage reads, "a woman ought to have a symbol of authority on her head."3 On the other hand, Paul's language in the following sentence ("Nevertheless, in the Lord woman is not independent of man") doubly suggests that he means what the text more naturally says: "a woman ought to have authority over her [own] head."4 First, the use of "nevertheless" sets the second sub-chiasm in contrast to the turn. Second, the fact that Paul begins by emphasizing that woman is not independent of man (rather than vice versa) suggests that it is her authority, not the man's, that is in view.5

>   1. Egalitarian and complementarian commentators are united on this point: see e.g. Belleville, 231; Fee, 522-524; Robertson and Plummer, 234; Lockwood, 375-376.
> 
>   2. Fee takes the unique nature of this would-be construction, unparalleled in any other Greek usage, as the basis for dismissing it out of hand (519 n. 23)--apparently ignoring his own suggestion, mere pages later, that "_exousia_ was one of the Corinthians' own words…. Very likely that is the reason for this choice of words, which otherwise appears to be so unusual" (521), which satisfactorily explains Paul's otherwise odd linguistic choice.
> 
>   3. So the ASV, ESV, HCSB, NET, NIV 1984, NASB, NKJV, NRSV. Others go even further: NLT, for example, has "a woman should wear a covering on her head to show she is under authority."
> 
>   4. Fee, 520.
> 
>   5. Fee, 522-523.

  1. Note the extra spacing between the footnotes. I'm not sure why, but footnotes behave differently than regular links, which can be stacked one after another. Footnotes have to be separated as separate paragraphs--probably because they are paragraph-like entities. Someday I'll look it up in the implementation to see why. But not today. 
  2. Because of the relatively simple structure of my paper, I actually simplified this, dropping the top-level header and making a few other adjustments. But this is the gist of my approach, and it's the framework in which I intend to work going forward. 

If you're curious, I made this footnote with a simple `[^2]`. _Boring_. 
