# Why San Francisco

_Captured: 2015-10-23 at 15:29 from [martiancraft.com](http://martiancraft.com/blog/2015/10/why-san-francisco/)_

![](http://martiancraft.com/img/blog/articles/large/20151013_sf.png)

We got our first glimpse of Apple's new sans-serif typeface, San Francisco, when the Apple Watch was unveiled in September of 2014--a new typeface designed specifically for legibility at small sizes on a tiny, high-resolution screen. Big news for type nerds and Apple fans alike. San Francisco was the first publicly released, Apple-designed typeface in over 20 years. Its name is familiar, harking back to the [previous convention](http://www.folklore.org/StoryView.py?story=World_Class_Cities.txt) of naming typefaces after "world class cities" like Chicago, Geneva, Athens. London, Venice, and yes, San Francisco.

![type specimen](http://martiancraft.com/img/blog/articles/large/20151013_sf_01-sfcompregular.png)

> _SF Compact Display Regular_

![type specimen](http://martiancraft.com/img/blog/articles/large/20151013_sf_02-sfuiregular.png)

> _SF UI Display Regular_

It looks familiar. It's been compared to Android's Roboto, the ubiquitous Swiss sans-serif typeface Helvetica, and one of my favorite typefaces DIN, designed for highways signs in Germany. It's hard to talk about San Francisco without touching on these popular sans-serif typefaces--the failings of Helvetica as a text face, and the success of Lucida Grande as a UI font.

San Francisco was originally only available on the Apple Watch.

> This year, at WWDC15, Apple announced San Francisco is coming to the Mac and iOS, completing its vision for typographic consistency across OS X, iOS, and watchOS.

The Apple Watch typeface San Francisco hasn't simply been moved to iOS and OS X; a new typeface called SF UI will be used there instead. San Francisco (as we knew it) has been renamed SF Compact.

![System Icons](http://martiancraft.com/img/blog/articles/large/20151013_sf_03-fontplatform.png)

> _System Icons_

Before we take a look at San Francisco, there are some typographic terms and concepts you should be familiar with. If you're a pro, you can skip ahead a bit.

## Form and Metrics

![Anatomy Info Graphic](http://martiancraft.com/img/blog/articles/large/20151013_sf_04-anatomy.png)

> _Anatomy Info Graphic_

![Serif](http://martiancraft.com/img/blog/articles/large/20151013_sf_05-serif.png)

> _A small stroke at the end of an arm, stem, or tail of a character._

![Baseline](http://martiancraft.com/img/blog/articles/large/20151013_sf_07-baseline.png)

> _The imaginary line upon which the text rests. Glyphs with curves at the bottom extend below the baseline. Descenders extend far below the baseline._

![Descender](http://martiancraft.com/img/blog/articles/large/20151013_sf_09-descender.png)

> _The part of the glyph that extends below the baseline to the descender line._

The height of the lowercase letters with no ascenders or descenders. It is usually calculated by the height of the lowercase x since it does not have overshoots like the curved forms.

![Cap Height](http://martiancraft.com/img/blog/articles/large/20151013_sf_11-capheight.png)

> _The distance from the baseline to the top of the capital letter in an alphabet. Oval letters will often overshoot the baseline and cap-height to achieve a visual balance between the glyphs._

![Line Height](http://martiancraft.com/img/blog/articles/large/20151013_sf_12-lineheight.png)

> _The line-height is the area defined by the ascender and descender of each glyph in a font. This is also referred to as the typographic balance, or typographic center._

![Leading](http://martiancraft.com/img/blog/articles/large/20151013_sf_13-leading.png)

> _The adjustable amount of vertical space between lines of type. The term originates from the use of lead strips to add space between the lines in letterpress printing._

![Overshoot](http://martiancraft.com/img/blog/articles/large/20151013_sf_14-overshoot.png)

> _The part of the curve that hangs below the baseline, or sits above the x-height and cap-height on curved glyphs. This makes the circular glyphs appear like they sit on lines._

![Tracking](http://martiancraft.com/img/blog/articles/large/20151013_sf_15-tracking.png)

> _The adjustable space between groups of letters. Tracking is applied equally across a line of text. Top: No tracking - set to 0 | Bottom: Open tracking - set to 120._

![Kerning](http://martiancraft.com/img/blog/articles/large/20151013_sf_16-kerning.png)

> _Kerning is the adjustable space between two glyphs to achieve an optically pleasing result. This should not be confused with Tracking which applies spacing equally between all of the glyphs._

## Glyph Widths & Spacing

Each glyph has a defined size called the em-box. The easiest way to understand this concept is to consider a monospace font. In monospace fonts the em-box width is the same for all of the glyphs. Most typefaces are not monospace, they have proportional em-boxes with optical sidebar values so each glyph occupies the space it needs. These sidebars are part of the built-in spacing metrics for a typeface (tracking and kerning can be applied). The sidebars are shown below for SF UI Display Light.

![Alphabet Sidebars](http://martiancraft.com/img/blog/articles/large/20151013_sf_17-sidebars.png)

> _Alphabet Sidebars_

Vertical strokes like the left side of the B, D, E, F, H… etc have consistent side bars. Characters that have open sides like the A, C, F, J, L… etc have smaller side bar settings since these open areas add to the optical white space seen between characters. Kerning can later be applied by the designer to correct for certain letter combinations.

The space between the glyphs represents tracking. When tracking is set to 0, the glyphs' em-boxes touch. This comes from the days of hand set type when a fonts side bars + the glyph width defined the width of a piece of cast metal type. To space out letters, they added metal between the characters.

![Proportional Numbers](http://martiancraft.com/img/blog/articles/large/20151013_sf_18-proportional.png)

> _The default numerals in most typefaces are proportional lining glyphs with optically set side bars. Shown here with SF Compact Display Light._

![Tabular Numbers](http://martiancraft.com/img/blog/articles/large/20151013_sf_19-tabular.png)

> _Tabular Numbers_

Tabular figures are alternate, monospaced numbers included in some typefaces. The glyphs are optically centered within a consistent width em-box. They can be either old-style, or lining figures. They are meant to be used for tables of data, or any place you are comparing numbers. Shown here with SF Compact Display Light.

## Legibility

There have not been many studies on what makes text legible, partly in fact because that depends on a number of variables. Serif or Sans-Serif; text or display sizes; and the context of the surrounding letters and words, etc.

There are many factors that affect legibility and readability. Some of this may be an over simplification but for the purpose of this article I'll summarize the common methods of checking legibility of a text face. If you find this interesting I encourage you to read Fabio Duarte Martins's post on [legibility](http://learn.scannerlicker.net/2014/11/14/on-legibility-in-typography-and-type-design/).

Typefaces with more open forms, specifically the apertures and counters, are easier to read at text sizes but can look too open at larger display sizes.

Wider more defined characters with ample spacing are easier to read in body copy--compressed typefaces are great for headlines and small spaces where information density is a priority and worth sacrificing some legibility.

> The best typefaces have both beautifully elegant styling, as well as precise and comfortably legible forms while offering a wide range of flexible widths, weights, and alternates.

There are three basic typographic principals that are generally followed to achieve highly legible text sizes when using sans-serif type.

  * Large x-height
  * Open Apertures
  * Comfortable spacing

Type designers are beginning to respond to new screen technologies. Most modern screen fonts are designed for high resolution displays. High resolution displays mean more detail for text of the same size on a "normal" display. More detail means more information the eye can use to differentiate characters. The more detail the eye has, the more legible the text becomes.

You have to pick a target. Fonts designed for low resolution screens don't work as well on high resolution displays--on the other hand, fonts with loads of detail fall apart on low resolution screens. People with low resolution displays should not be punished with diminished legibility.

## Large x-height

At body text sizes, even on a Retina display, a typeface has very little vertical pixels to use. In Latin based languages, we distinguish characters primarily with the information stored in the lowercase character's x-height. More specifically, the top parts of the x-height & ascender. It's common knowledge among designers to pick typefaces with larger x-heights when concerned about legibility. It makes sense in theory but I think it's a bit of an over simplification.

In general this is true, but whats more important is that the typeface has an appropriate sized x-height at the size you are using it.

There are three ways that you can compare the x-heights across multiple typefaces--each way will yield different results.

  * Same cap-height. (this may mean using different point sizes)
  * Same x-height. (this may mean using different point sizes)
  * Same point size. (x-heights and cap-heights likely will not align)

### Same cap-height

The first way to compare the x-heights is to scale all of the typefaces to the same cap-height. This will give us the ratio of the x-height to the cap-height. If we use this metric for comparison, SF Compact and Verdana perform best, and DIN the worst.

![Cap-height comparison](http://martiancraft.com/img/blog/articles/large/20151013_sf_20-capheightcomparison.png)

> _Cap-height comparison_

Same cap-height comparison: I chose these characters because they are narrow and I can fit them all on screen at a large size, but they also tell us a lot about the typeface. The capital i gives us the cap height. The lowercase j gives us the descender distance. The lowercase i gives us the x height, and the lowercase l gives us the ascender height.

![Cap-height comparison](http://martiancraft.com/img/blog/articles/large/20151013_sf_21-capheightcomparison.png)

> _Cap-height comparison_

If we use this metric to evaluate legibility, It seems obvious that a larger x-height increases legibility. This is probably true for characters like the a, e, s that need precise apertures and are likely to collapse if too small.

![Cap-height comparison](http://martiancraft.com/img/blog/articles/large/20151013_sf_22-capheightcomparison.png)

> _Same cap height comparison: 160pt Verdana Regular and 163pt DIN Regular -- In this example Verdana is more legible because of the taller x-height._

But what if you're setting type in a language that needs diacritical marks? Those usually fall between the x-height and the cap height. The closer these marks are to the x-height, the more likely it is they will blur at small sizes. If you are setting type in a language that uses diacritical marks, you would be best served by a typeface with a nice balance between the x-height and the cap-height, giving ample room for accents.

![Diacritical Marks](http://martiancraft.com/img/blog/articles/large/20151013_sf_23-diacritical.png)

> _Diacritical Marks_

Comparing fonts at the same x-height is a common metric used in legibility studies. To me, the problem with this practice is when you compare two typefaces at the same point sizes (a more real world scenario for a designer) the results are very different. This Cap-height comparison shouldn't be ignored though, it does tell us that we should use typefaces like DIN at a larger point size than typefaces like Verdana.

So what are the results when we compare these typefaces at the same point size?

### Same point size

This is how we usually compare type--set at the same size, however this form of comparison can also be flawed.

![Same point size comparison](http://martiancraft.com/img/blog/articles/large/20151013_sf_24-pointsize.png)

> _Same point size comparison: All fonts set at 160pt and aligned on their baselines._

![Same point size comparison](http://martiancraft.com/img/blog/articles/large/20151013_sf_25-pointsize.png)

> _Same point size comparison: X-height comparison shown at about 834pt._

If we look at the two ends of the spectrum from above, Verdana and DIN, we can see how different the x-heights can be when comparing two typefaces at the same size.

![Same point size comparison](http://martiancraft.com/img/blog/articles/large/20151013_sf_26-pointsize.png)

> _160pt Verdana Regular -- 160pt DIN Regular._

We have more stroke information being stored between the baseline and x-height of Verdana than we do with DIN due to Verdana's larger x-height. If you look at characters with 3 horizontal strokes all within the x-height like the a, s, and e--the larger x-height allows for more open counters and apertures. This should make the typeface more legible right? If we use this metric for comparison, we can assume Verdana is more legible than DIN and SF UI is more legible than SF Compact. Is that really the case though?

Certainly not if you are say, setting type in German. Many languages use diacritical marks above the characters. German uses the umlaut; Greek the trema; or the acute in Spanish to name a few. The larger the x-height, the smaller the space becomes for these diacritical marks which will start to decrease legibility.

![Diacritical Marks](http://martiancraft.com/img/blog/articles/large/20151013_sf_27-pointsize.png)

> _Diacritical Marks_

Even though DIN has the smallest x-height in this group, it probably would be the best choice for a language that uses diacritics. No surprise, DIN is a German typeface. Always consider your use case and be weary of any sweeping generalization.

To complicate things further, at the same font size, two fonts can render very differently on screen, especially at small sizes--and those results can be inconsistent. For example, at 12pt Verdana has a x-height of 7pixels on a 1x display while 12pt DIN has an x-height of only 6 pixels. At 13pt, they are both 7 pixels. At 14pt, Verdana's x-height is once again, 1px larger at 8px.

![Same Point Size Comparison](http://martiancraft.com/img/blog/articles/large/20151013_sf_28-pointsize.png)

> _Verdana (left) and DIN (right) at 12, 13, and 14 point_

DIN's x-height is not that different from Verdana right? Why does this happen? Subtle changes have a big impact when scaled down to a small pixel grid. We're scaling a glyph drawn at 2048pt down to 12pt. As we saw with the old-style figures and the apertures, the point's placement on that smaller pixel grid controls how the anti-aliasing is resolved--and in this case, the vertical metrics.

This is something to pay close attention to when you are just replacing a typeface, and not adjusting your font sizes. You may want to do this if you are replacing the system font in your application with a custom font for a new release but don't want to overhaul all of your type sizes.

If you scale two fonts to have the same x-height, any legibility differences caused by the different proportioned x-heights could disappear--in some cases the larger x-heights could even begin to work against the typeface, actually diminishing legibility.

![Same x-height Comparison](http://martiancraft.com/img/blog/articles/large/20151013_sf_29-pointsize.png)

> _160pt Verdana Regular and 178pt DIN Regular -- In this example DIN actually seems more legible than Verdana because it has more open apertures._

Since DIN has a smaller x-height than Verdana, it inherently has a taller ascender. Because of this, it could be argued that that smaller x-heights actually **aid** in legibility if used at the "right size".

When comparing characters like the lowercase n and h where the ascender is the differentiating stroke, the larger x-height of Verdana means it has a shorter ascender potentially causing problems when trying to distinguish between these two characters.

![Verdana vs DIN](http://martiancraft.com/img/blog/articles/large/20151013_sf_30-verdanadin.png)

> _If comparing typefaces this way, DIN seems to be more legible because of it's taller ascender._

Verdana has a pretty good balance here though so it's not the greatest example to illustrate this point (it's a Matthew Carter font after all). If the effect is exaggerated by increasing the x-height even further on Verdana, and decreasing it on DIN, you can easily see the potential problem when an x-height is too large and an ascender too small. In This example it could be argued that a smaller x-height actually aids legibility.

![Verdana vs DIN](http://martiancraft.com/img/blog/articles/large/20151013_sf_31-verdanadin.png)

> _Verdana with an extended x-height and DIN with a shortened x-height. It becomes very hard to differentiate between the lowercase n and h._

This just goes to show how important it is to look at every character when selecting a typeface.

> Rather than saying a taller x-height is better for legibility, I think it's more important to say a typeface needs to have a good balance between the x-height, and the ascenders & descenders. The vertical proportions of a typeface should always be examined and considered when setting body copy. You can adjust point size to compensate for a small x-height and this can actually aid legibility.

## Open Apertures

![Open counter vs tight counter](http://martiancraft.com/img/blog/articles/large/20151013_sf_32-aperturecomp.png)

> _Open counter vs tight counter_

As we saw looking at the x-heights above, open apertures make text easier to read. The 'white space' around a letter affects legibility as significantly as the strokes do.. I don't just mean the spacing between the letters--the apertures and counters also effect this tone.

When a glyph's aperture is too tight it will collapse on itself becoming blurry (both literally on low resolution displays or at small sizes, **and** optically when quickly scanning/reading through a series of words.

![Open apertures](http://martiancraft.com/img/blog/articles/large/20151013_sf_33-openaperture.png)

> _The open counters and apertures of DIN allow the eye to flow easily across it's forms. Note the nice balance of the text weight, to the "white space" around the text._

Verdana and Lucida Grande have very open apertures avoiding becoming blurry at nearly all sizes. The bowl of the e does not curve back into the cross bar. It renders as a sharply defined aperture. These open apertures are one of primary traits of most screen fonts designed to be used at small sized or for low resolution displays. DIN sits some where in the middle between Helvetica and Lucida in terms of open apertures and the angle of the terminals.

![Pixel apertures](http://martiancraft.com/img/blog/articles/large/20151013_sf_34-pixeltype.png)

> _Pixel apertures_

High resolution displays are become more and more common, especially with Apple users. The argument can be made that typefaces like Lucida and Verdana are no longer necessary to achieve legible text at 11-14pt. This is partly true, and Lucida doesn't look great on a retina display, but the characteristics that make faces like it legible on low resolution displays are still important considerations to make when designing or picking a screen font.

Helvetica Neue has narrow apertures, with horizontally cut terminals giving strength to the forms at large sizes, but diminishing legibility at small sizes where the details begin to blur. It has a consistent tone across the entire typeface. This works fine for display sizes--it's clean, modern, and timeless, but becomes very blurry and straining on the eyes at small sizes. It's designed to have clean forms, and perfect grey tones not be the most legible text typeface.

![Horizontal Terminals](http://martiancraft.com/img/blog/articles/large/20151013_sf_35-helvetica.png)

> _Helvetica Neue Regular - Horizontal cut terminals on arcs._

![Non Retina](http://martiancraft.com/img/blog/articles/large/20151013_sf_36-helveticapixel.png)

> _12pt Helvetica Neue Regular zoomed to 1600% - This is about what your screen renders on a non retina display. Now, image your eye zipping through a paragraph of text, or quickly scanning a UI label._

![Retina](http://martiancraft.com/img/blog/articles/large/20151013_sf_37-helveticapixel2x.png)

> _12pt Helvetica Neue Regular @2x -or- 24pt @1x zoomed to 1600%. This is what you would get on most retina displays. It's a little better, but the consistent tone of Helvetica becomes more pronounced and the apertures still blur._

![Non Retina](http://martiancraft.com/img/blog/articles/large/20151013_sf_38-lucidapixel.png)

> _12pt Lucida Grande Regular zoomed to 1600%._

![Retina](http://martiancraft.com/img/blog/articles/large/20151013_sf_39-lucidapixel2x.png)

> _12pt Lucida Grande Regular @2x -or- 24pt @1x zoomed to 1600%._

I'm spending so much time talking about the apertures because similar optical traits can be seen in all of the negative spaces: the counters, the space around the letter, and the space between letters. In typography the space around the letters is just as important as the strokes of the letters.

When you try and achieve a perfect balance between the black and white parts of the letters, you end up with something like Helvetica. The forms inside of Helvetica are drawn beautifully. It has nearly perfect grey tones--and why it fails for body copy and at small sizes.

![Aperture](http://martiancraft.com/img/blog/articles/large/20151013_sf_40-countercomparison.gif)

> _12pt Lucida Grande Regular @2x -or- 24pt @1x zoomed to 1600%._

Lucida inner shapes are a little more awkward, almost illegible when you just look at the negative space, but it serves a purpose, the text itself is very legible at low resolution. If you want maximum legibility you can use something like Input, a coding font drawn on a 12px grid. It has clumsy, chiseled looking forms when viewed large, but is extremely legible at small sizes on a low resolution display. It does all of this while maintaining very pleasing grey tones.

![Grey Tones](http://martiancraft.com/img/blog/articles/large/20151013_sf_41-graytones.gif)

> _The grey tone, the space around the letters, and the space within the letters for Helvetica Neue and Lucida Grande._

It was clear when Apple changed to Helvetica on OS X they were focusing on Retina design for the Mac.

> "For some, the choice of a font may not be a big deal. But to us, it's an integral part of the interface. In OS X Yosemite, fonts have been refined systemwide to be more legible and consistent across the Mac experience. You'll notice a fresh, new typeface in app windows, menu bars, and throughout the system. The type looks great on any Mac, and even more stunning on a Mac with a Retina display."

More legible? Really?

Marketing talk, but everyone knew Helvetica was terrible on 1x displays. Yes, Retina helped. But it can't turn a bad type selection into a good one.

## Consistent Heights

A typeface is drawn at either 1000, 1024, or 2048 units. When rendered to a screen that's usually translated to between 10 and 30 pixels (@1x) depending on the font size. Aligning similarly sized objects will give a more consistent tone to a line of text when it's displayed on screen. The placement of all of the vector points and curves becomes very important when scaling an outline so drastically.

Helvetica has numbers that are slightly smaller than the cap-height. This practice dates back to the days of metal type. Most of these fonts had only one set of numerals so it was important the numbers looked good with both uppercase and lowercase letters--this meant shortening the numbers slightly so they did not look too large when paired with the lowercase letters. The effect is subtle, but if the typeface didn't have alternate old style figures, it was the best solution at the time. Now, with digital type, a type designer can include many alternate glyphs.

DIN's capital letters and numbers both fall perfectly on the cap-height. I haven't been able to find a clear answer as to why but I'm guessing this was done to make production and installation of the physically cut letters easier. Later versions of DIN included old style figured to be used with lowercase text.

![Helvetica Numerals](http://martiancraft.com/img/blog/articles/large/20151013_sf_42-helveticanumerals.png)

> _Helvetica Neue Light_

![DIN Numerals](http://martiancraft.com/img/blog/articles/large/20151013_sf_43-dinnumerals.png)

> _DIN Numerals_

![Non-lining figures](http://martiancraft.com/img/blog/articles/large/20151013_sf_44-dinnumeralsalt.png)

> _DIN Light Alternate - Most sans-serif typefaces do not have old-style (also called non-lining) figures, it's primarily seen in serif faces meant for body copy where it will often be used with lowercase text. Some typographers will argue this should be the default numeral style._

I mention old style figures to demonstrate the concept. When the glyphs shift around as much as they do in (DIN's) old style figures, you can really see how much of an effect inconsistent heights have on the rendering at small sizes. The closer the vector points of the glyph are to the pixel grid at the given size, the sharper the glyphs will render.

![DIN Alternate Pixel Numerals](http://martiancraft.com/img/blog/articles/large/20151013_sf_45-dinaltpixel.png)

> _DIN Light Alternate 12pt zoomed to 1600%_

![DIN Numerals](http://martiancraft.com/img/blog/articles/large/20151013_sf_46-dinpixel.png)

> _DIN Light 12pt zoomed to 1600%_

In practice, the top cross bars on letters like the capital E, F and B have the same pixel density at the top as numbers like the 5 and 7. helping maintain a consistent grey tone across the font. If we compare DIN and Helvetica with both letters and numbers you can see what I mean.

![Cross Bars](http://martiancraft.com/img/blog/articles/large/20151013_sf_47-crossbars.png)

> _Cross Bars_

If the concept of similar heights is taken too literally, it can cause other legibility problems. Consistent heights are important, but you also want to be careful not to make the characters too similar when designing a face used for body copy.

Like many sans-serifs, Helvetica and Lucida Grande have no visible difference between the capital i and the lower-case L making it even more of a problematic text face--especially for dyslexic readers like myself.

![mixed case heights](http://martiancraft.com/img/blog/articles/large/20151013_sf_48-mixedcase.png)

> _The finial on the lowercase L in DIN is a unique characteristic. It's common in sans-serif designs for it to be difficult to tell the difference between a capital i and a lowercase L. Verdana solves for this by using a serif on the capital i. Some versions of DIN even have an alternate capital i with serifs like Verdana._

## Spacing

You can't set all of your letter-spacing to default values and expect legible text. All typefaces have built in spacing metrics. These metrics are usually set for an ideal size (range) at which the typeface is expected to be used. When using the typeface outside of these size ranges, or when trying to achieve a certain style, or pleasing texture to the text, we can fine tune the spacing by tracking and/or kerning the text.

You can tell where the ideal size range for a typeface is by researching the typeface design, or just by seeing what size the text looks best with 0 tracking.

Here are some tips to take control over the legibility of your typography by adjusting the spacing.

  * Use open tracking when setting type at small and body copy sizes or when on a busy background.
  * Be careful not to track out the letters too much on body copy -- the words will begin to fall apart and make the text illegible. Designers will hate you.
  * Use tighter tracking when setting type at display sizes.
  * Use open tracking for all caps, but be careful not to over do it.
  * Numbers need more space than letters
  * Pay attention to the texture of the text
  * Read the text

Pay attention to the spacing of your text when designing your applications. Ideal spacing values differ between every typeface, weight, and font size.

## Moving away from Helvetica

People have really strong feelings about Helvetica. Helvetica is not a bad typeface, it's a bad UI typeface. John Boardley said it well:

> "…type is a tool. A hammer, even the best hammer in the whole universe, is really quite useless at removing screws. It's not the hammer's fault: first, it's an inanimate object without a shred of consciousness or will; second, it is simply a tool -- frequently -- the wrong tool for the job. Need I add, the same can be said for typefaces. Hating the hammer?   
  
And that's why it's difficult for good designers to name their favorite typeface. Favorite for what? For text? For toilet tissue branding? For books? For UI? For… -- you get the point. What's your favorite tool? Hammer? Screwdriver? Chainsaw? The choice of typeface is decided only when one knows the nature of the job. It does not precede it. And sometimes, Helvetica will be one of the tools adequate for the job."

JOHN BOARDLEY on [ilovetypography.com](http://ilovetypography.com/2015/06/27/the-last-word-on-helvetica/)

Some of the most well known typefaces were designed to be used in a specific contexts. However certain characteristics of the design that makes it excel in the intended application, can make it a poor type choice for a different application. This is partly why there are so many similar typefaces. It's common for typefaces to share similar anatomy, forms, and traits, redesigning slightly to make it work well in the intended application. It looks like this is what Apple did with San Francisco and that's not a bad thing.

> Apple's new watch typeface is kinda similar to other typefaces. In other news, almost all typefaces are kinda similar to other typefaces.
> 
> \- Nick Sherman (@NickSherman) [November20, 2014](https://twitter.com/NickSherman/status/535244165098250240)

  
![](http://martiancraft.com/img/blog/articles/large/20151022_sf.png)

​

If you are not familiar with the terms used to discuss typography , or want to learn more about legibility and screen rendering make sure to read [Part 1](http://martiancraft.com/blog/2015/10/why-san-francisco/) first.

![Golden Gate Bridge](http://martiancraft.com/img/blog/articles/large/20151022_sf_01-hero.jpg)

> _Golden Gate Bridge_

![San Francisco Sample](http://martiancraft.com/img/blog/articles/large/20151022_sf_02-sanfrancisco.png)

> _San Francisco Sample_

## SF UI & SF Compact

With the Apple Watch came an entirely new, Apple designed typeface called San Francisco. It was designed to work at small sizes maximizing legibility on the new, much smaller screen of the Apple Watch. It seemed to work well in screen shots but most people wouldn't see it in person for another seven months. People quickly installed San Francisco (SF Compact) on the Mac only to find the results were less than ideal. The spacing wasn't right and it was hard to read long text strings. It was designed for the watch after all.

We didn't have to wait long for a proper version of San Francisco on the Mac. In June 2015 Apple added to it's type system with the introduction of San Francisco (SF UI) on OS X 10.11 and iOS 9. Just three months later in September, Apple announced the Apple TV which also uses SF UI.

So is San Francisco really the perfect system font for Apple's products? It's complicated.

Many critics have compared it to Helvetica and DIN. When viewed under this simplified stylistic lens, they aren't exactly wrong. There are a lot of similarities. If we put San Francisco under the microscope, we'll see that the visual similarities are just a small piece of this type system. It's a typeface designed for the digital age and it excels in this medium in ways that Helvetica, DIN, or Lucida Grande ever could.

> The system is technically complex, but when used "correctly" it seems obvious and simple; almost transparent to the reader. That's what makes a good type system. 

![system icons](http://martiancraft.com/img/blog/articles/large/20151022_sf_03-platforms.png)

> _system icons_

San Francisco has two distinct typefaces: SF UI and SF Compact. These sibling families were designed to be "related, but not equal". They share similar characteristics and features but are designed to look best on their intended platforms. SF UI is used on iOS, OS X, and now tvOS--SF Compact is used on the watch.

![Family Tree](http://martiancraft.com/img/blog/articles/large/20151022_sf_04-family.png)

> _Family Tree_

The new family includes 42 fonts consisting of two sibling families (SF UI & SF Compact), each with two optical sizes (Text & Display). Each Text size has six weights (Light, Regular, Medium, Semibold, Bold, and Heavy) with complementary italics. Each Display size has nine weights (Ultralight, Thin, Light, Regular, Medium, Semibold, Bold, Black, and Heavy). OpenType features include stylistic alternates, numerator and denominators, fractions, discretionary ligatures, lining figures, and tabular figures. It has support for latin text, cyrillic, and greek text.

![SF Compact Display Regular](http://martiancraft.com/img/blog/articles/large/20151022_sf_05-alphabet.png)

> _SF Compact Display Regular_

![SF UI Display Regular](http://martiancraft.com/img/blog/articles/large/20151022_sf_06-alphabet.png)

> _SF UI Display Regular_

At first glance the two sibling families look pretty similar. That's a good thing if you want to maintain a consistent typographic feel through out the system. The biggest difference can be seen in the round areas of the glyphs. SF Compact is a more geometric and compressed typeface--less round. The vertical strokes on the curves are straightened out and the characters slightly condensed.

![Shape Comparison](http://martiancraft.com/img/blog/articles/large/20151022_sf_07-shapes.png)

> _Shape Comparison_

You can fit more letters on a line of text with a narrow face, which means at small sizes, you can use more spacing for text occupying the same horizontal space, which helps legibility--or cram more characters onto a single line if space is limited and you're willing to sacrifice some legibility.

![Spacing Comparison](http://martiancraft.com/img/blog/articles/large/20151022_sf_08-spacing.gif)

> _You can have more spacing between letters with SF Compact in the same space as you can with SF making it slightly easier to read at small sizes without sacrificing character/word count per line_

There is a downside to compressed faces like SF Compact. It puts more strain on the eye to read long passages of text with narrow characters.

![Shape Comparison](http://martiancraft.com/img/blog/articles/large/20151022_sf_09-tones.png)

> _You can use more letter spacing with SF Compact and have paragraphs that occupy the same space due to it's narrow letterforms._

> We read longer strings of text more often on iOS and OS X than we do on the Apple Watch. Using a more body copy-friendly letterform like SF UI on these platforms makes sense. It also has similar characteristics to Helvetica, so it feels familiar, but different, and slightly better. It is Apple after all.

Unfortunately San Francisco has some of the same failings as Helvetica and Lucida Grande in mixed case settings. For example, it's difficult to distinguish between the lowercase L and the capital i. To Apple's credit though, they did take this into consideration with the vertical metrics. The ascender sits above the cap-height helping with mixed cased forms…just a little.

![Mixed Case Comparison](http://martiancraft.com/img/blog/articles/large/20151022_sf_10-mixedcase.png)

> _Mixed Case Comparison_

DIN really shines here. The finial at the end of the lowercase l adds a style and personality to the typeface. Love it or hate it for this reason--it's the most easily distinguished and therefor legible l in these examples. Admittedly, this is an edge case, and when viewed in the context of other letters in body copy, in most cases it's not really a problem.

San Francisco was designed for digital platforms where it's likely to be used in random number and letter strings, say for charts, confirmation numbers, labeling, and even code. Maybe I'm making a big deal about this for nothing -- I am dyslexic so I'm extra sensitive to things like this -- but Apple has over 500 million users; it's a safe bet I'm not the only one.

![Mixed Case Comparison](http://martiancraft.com/img/blog/articles/large/20151022_sf_11-formfield.png)

> _Mixed Case Comparison_

San Francisco's alphabet sacrifices legibility in a few areas for a cleaner more universal look. It does however make up for it in other ways with the help of some smart features built into the typeface, and the operating systems.

## Size Specific Features: Optical Sizing

One of the type designers for the San Francisco font, Antonio Cavedoni, called optical sizing "The big idea in the San Francisco family of typefaces." If you're not a type nerd, you may not be familiar with the term optical sizes.

In the days of metal type, subtle adjustments were made to the glyphs at each font size to ensure style and legibility of the typeface was retained through out the various sizes. It was common to add detail, adjusted stroke weights, and reduce spacing as the letters got larger. As the letters got smaller, spacing was increased, detail was simplified, and often, ink traps were added to maximize legibility once printed small.

In the digital age, we can make type any size we want with the click of a mouse, but this does not take into consideration how a font will look at that size. The outlines remain the same. Type designers solve for this by creating optical size cuts (multiple versions of a typeface to be used at different sizes). A typeface can have 2 or more optical sizes. Currently San Francisco has two optical sizes, Text and Display.

![Optical Sizes](http://martiancraft.com/img/blog/articles/large/20151022_sf_12-hamburger.png)

> _Optical Sizes_

The operating systems automatically switch between these two cuts at 20pt (@ 144dpi) if your app uses the system font. Since this feature is part of Apple's TextKit, design applications like Photoshop and Sketch will not make this switch automatically. Designers will need to switch between Text and Display cuts manually.

When you examine the two cuts, at first glance it looks like only the letter spacing has been increased on the Text cut to make it more legible at smaller sizes.

![Optical Sizes](http://martiancraft.com/img/blog/articles/large/20151022_sf_13-hamburger.gif)

> _The text cut has more open spacing to aid legibility at small sizes_

It's much more than that though. These optical cuts have unique adjustments made to the outlines of each glyph so they look best at their intended sizes. When the spacing differences between text and display are ignored and characters are overlaid directly on top of each other, you can see the differences in the glyph shapes.

![Optical Sizes](http://martiancraft.com/img/blog/articles/large/20151022_sf_14-ecsar.gif)

> _Optical Sizes_

As you saw in [Part 1](http://martiancraft.com/blog/2015/10/why-san-francisco/) of this article open apertures help with legibility. SF UI has open apertures, larger overshoots on the curved glyphs, and longer descenders. The nose of the r is longer, and the crossbars on the lowercase f and t are wider in the text face. The dot on the lowercase i sits above the cap-height so it doesn't blur with the stem of the i. These minor details all optimize the text face for use at small sizes.

![Optical Sizes](http://martiancraft.com/img/blog/articles/large/20151022_sf_15-flight.gif)

> _Optical Sizes_

San Francisco has "ink traps" on both the text and display cuts. Traditionally, ink traps subtract from the letters as seen with Bell Centennial. This was done because newsprint paper absorbs the ink and starts to bleed in the tight areas. The ink traps give extra space to allow the ink to fill in the rest of the letter.

![Ink Traps in Bell Centennial](http://martiancraft.com/img/blog/articles/large/20151022_sf_17-inktrap.png)

> _Bell Centennial designed by Mathew Carter in 1976 for AT&T telephone directories to solve for the technical challenges inherit to printing technologies of the time_

San Francisco's notches have "extra ink" to avid a sharp corner that will become too dull when rendered on screen effecting the overall tone of the letter. These notches are more pronounced on the text cuts.

![Ink Traps in SanFrancisco](http://martiancraft.com/img/blog/articles/large/20151022_sf_16-inktrap.png)

> _SF UI Text Regular_

> Type design has responded to technology since the beginning--from hand-cut wood and metal type precisely crafted for each size, to newsprint settings utilizing fonts with built in ink traps, to digital screen fonts designed for high resolution displays; and everything in between. In most cases type design is catching up to technology, but the evolution of technology will not change what makes text sizes easily legible. 

## Weights

A good type system has many different weights giving you control of hierarchy, mood & tone, style, and yes, legibility. San Francisco offers plenty of options. Each sibling family has nine Display weights, and six Text weights with Italics giving all the flexibility you need to create beautiful, legible typography.

![Weights](http://martiancraft.com/img/blog/articles/large/20151022_sf_18-weights.png)

The text cut has fewer weights since the extreme weights (Ultralight, Thin, and Black) would become illegible at their intended sizes. I'd even recommend avoiding using the Heavy weight in the text sizes unless you really have to. It really pushes the limits of legibility at all but the largest recommended sizes (close to 20pt).

![Weights](http://martiancraft.com/img/blog/articles/large/20151022_sf_19-weights.png)

Both SF UI and SF Compact offer the same range of weights.

![SF UI Display weights](http://martiancraft.com/img/blog/articles/large/20151022_sf_20-weights.png)

> _SF UI Display weight_

![SF UI Display weights](http://martiancraft.com/img/blog/articles/large/20151022_sf_21-weights.png)

> _SF UI Display weights_

![SF Compact Display weights](http://martiancraft.com/img/blog/articles/large/20151022_sf_22-weights.png)

> _SF Compact Display weights_

![SF Compact Display weights](http://martiancraft.com/img/blog/articles/large/20151022_sf_23-weights.png)

> _SFCompact Display weights_

## Size Specific Features: Tracking

As we've seen, generally, you need more letter spacing for small text than you do for display sizes. With San Francisco on Apple's operating systems, tracking is size specific. That means each font size is intended to used with a specific tracking value. Lucky for engineers, if you use San Francisco the operating system automatically applies the tracking values based on text size.

The example below shows 100pt text and 18pt text, each with their recommended tracking values. Although both sizes have different letter spacing, they appear to have the same optical spacing. The grey tones of the two sizes are consistent making the text more comfortable to read.

(Don't get confused by the specific tracking values shown below. I'm switching between text and display cut here and each has its own unique tracking table. There is no relationship between the tracking values of the Text and Display cuts. It's relative to each optical size. Just remember, Text has more open tracking, Display has tighter tracking)

![Optical Sizes](http://martiancraft.com/img/blog/articles/large/20151022_sf_24-opticalsize.png)

> _Top: 100pt SF Display with 7 tracking - Bottom: 18pt SF UI Text with 19 tracking_

With the two optical size cuts set at the same point size, we can see how much more open the tracking is for the text size:

![Optical Sizes](http://martiancraft.com/img/blog/articles/large/20151022_sf_25-opticalsize.gif)

> _Text vs Display: 100pt SF Display with 0 tracking - 100pt SF UI Text with 0 tracking_

Again, the system handles this automatically based on the tracking tables provided by Apple. You just have to pick the size of the text. If you need to make adjustments to the letter spacing for stylistic or layout reasons you can do so, just make sure to keep track of the system you are now building so you can hand the new metrics over to an engineer.

If we look at this spacing concept on a graph, it looks something like this:

![Tracking Table](http://martiancraft.com/img/blog/articles/large/20151022_sf_26-graph.png)

> _Graph shown for SF UI Text. The text cut would never be used above 20pt. This is just demonstrating the concept._

If you are designing your apps in something like Photoshop, or Sketch you'll need to adjust the tracking at every point size if you want a realistic view of what San Francisco will look like once built. Apple has provided us with tracking tables for both SF and SF Compact. Since the side bars of a glyph are adjusted for each weight by the type designer, the same [tracking values](https://developer.apple.com/fonts/) are used regardless of the font's weight.

![Tracking Table](http://martiancraft.com/img/blog/articles/large/20151022_sf_27-graph.png)

> _Tracking Table_

The styles look like this:

![Optical Sizes](http://martiancraft.com/img/blog/articles/large/20151022_sf_28-sizes.png)

> _Optical Sizes_

![Optical Sizes](http://martiancraft.com/img/blog/articles/large/20151022_sf_29-sizes.png)

> _Optical Sizes_

It seems pretty straight forward except for one thing. Apple says switch between text and display cuts at 20 points @2x(144ppi). This is slightly confusing for those of us use to designing at 72dpi in our design software.

When I'm designing with a 17pt font in a 1x composition (in Photoshop) @72dpi, when I increase the canvas size by 2x, the 17pt text becomes 34pt @2x. (The tracking values remain the same since those values are based on an Em, a relative unit. A tracking adjustment made at one point size will have the same effect at another point size.) Apple's chart shows @2x sizes as half the 1x size, rather than doubled as it would be in Photoshop. This has to do with dpi scaling and I won't go to far into it, but just know:

  * If you design at 1x at 72dpi switch to display at 40pt
  * If you are designing at 2x @72 dpi switch to display at 20pt
  * If you are designing at 144dpi switch to display at 20pt.

## Special Features: Numerals

Both SF and SF Compact include proportional lining, and tabular numerals. By default San Francisco uses proportional lining figures.

![Lining Figures](http://martiancraft.com/img/blog/articles/large/20151022_sf_31-lining.gif)

> _Proportional Lining Figures_

![Lining Figures](http://martiancraft.com/img/blog/articles/large/20151022_sf_32-proportional.png)

> _Lining Figures_

If you're setting data inline, or as static numerals, use the default proportional numbers. This will give the correct grey space and rhythm to the numbers. If you were to use tabular figures here, the spacing would be jumbled and look like a poorly-kerned font.

If you're animating a numeric sequence, or setting data in a table for comparison, you should use tabular figures. In Photoshop and Illustrator. you can access these characters through the glyphs palette

![Tabular Figures](http://martiancraft.com/img/blog/articles/large/20151022_sf_30-tabular.gif)

> _Tabular Figures_

![Tabular Figures](http://martiancraft.com/img/blog/articles/large/20151022_sf_33-proportional.png)

> _Tabular Figures_

San Francisco has a handful of glyphs for common fractions as well (1/2, 1/4, etc). If you need something that's not built in, it offers a full set of numerators and denominators; and a proper fraction bar (Don't use the forward slash for this…ever) to build your own unique fractions.

![Fractions](http://martiancraft.com/img/blog/articles/large/20151022_sf_34-fractions.png)

Below is an example of the same fraction set in three different ways. The first just changes the size of a single weight font. Notice how light the fraction feels here compared to the 12. The second example adjusts the weight of the fraction to closer match the 12, but it's not perfect. The third example is set with a single font using the numerators and denominators.

![Fractions](http://martiancraft.com/img/blog/articles/large/20151022_sf_35-fractions.png)

San Francisco also has alternate glyphs for several of the numbers.

I'm sure it's happen to you with certain fonts. Letters and numbers with similar forms get misread. For example, it's easy to confuse a capital B and an 8. A capital A and a 4; or a capital G and a 6. This is partly why non-lining old-style numerals exist. To solve for this legibility challenge, and add a bit more style to the typeface, San Francisco has alternates for the 4, 6, and 9 for both proportional and tabular figures.

![Alternate Numbers](http://martiancraft.com/img/blog/articles/large/20151022_sf_36-alternates.gif)

> _Alternate Numerals_

If you have seen an Apple Watch, you may have noticed them in use already.

![Alternate Numbers](http://martiancraft.com/img/blog/articles/large/20151022_sf_37-watch.png)

> _Photoshop render of the Chronograph face @2x on the left, and @4x on the right._

There's also a pretty smart feature built in using contextual alternates.

Normally, punctuation sits on the baseline., however this looks off balance in time formats. Before San Francisco, you needed a few lines of code to fix this. More importantly, you had to remember to do it. San Francisco solves for this by having an alternate glyph with the colon aligned to the cap-heights optical center. The system switches to it automatically when it recognizes a time format. You can achieve the same thing in Photoshop by turning on the contextual alternates button in the Character palette, or by selecting the character from the Glyphs palette.

![Alternate Colon](http://martiancraft.com/img/blog/articles/large/20151022_sf_37-time.gif)

> _Alternate Colon_

Now that we've taken a look at San Francisco, let's talk a little about the API that makes a lot of these features possible, Text Kit.

With the release of iOS 7 in 2013, Apple shifted their aesthetic direction from glossy buttons and skeuomorphic designs with medium and bold weights of Helvetica, to a cleaner, flatter, more typography focused design language filled with lighter text weights of Helvetica Neue. iOS 7 brought the content front and center, it also brought Helvetica Neue to everyones attention. This new design language relies heavily on good typography. There was a lot of criticism from designers for their choice of light weights of an already illegible typeface for screen design. Apple needed a new typeface, but looking back, the big news was TextKit.

## Text APIs

TextKit, an API (Application Programming Interface), is a fast and modern text layout and rendering engine making use of advanced unicode features, kerning and ligature support, dynamic sizing, and advanced layout techniques. TextKit has support for Dynamic type, Font descriptors, and Symbolic traits.

Dynamic Type introduced the concept of managed type styles--pre defined sizes, weights, and spacing values (set by Apple?) optimized for legibility, making text easier to read. Keeping accessibility in mind, Dynamic Type also gives the user the ability to globally adjust these type styles across the OS (with options for small, medium, large, and bold styles). (iOS only?)

Font Descriptors made it easier for developers to build, archive, and reference unique type styles and manage them through out their application.

![Primary Type Style](http://martiancraft.com/img/blog/articles/large/20151022_sf_38-typestyles.png)

> _Primary Type Style_

Symbolic traits allow you to create alternate styles based on your primary styles. In this example, the primary style has two Symbolic traits, or alternate styles. A Bold style, and an Italic style.

![Symbolic Traits](http://martiancraft.com/img/blog/articles/large/20151022_sf_39-typestyles.png)

> _Symbolic Traits_

You may then want to have even more alternate styles, maybe to adjust the line spacing on a specific Font Descriptor inside a style. For example, we can add styles for Loose and Tight line spacing for the primary Body style.

![Symbolic Traits](http://martiancraft.com/img/blog/articles/large/20151022_sf_40-typestyles.png)

> _Symbolic Traits_

Then add more styles to adjust the tracking of the Caption style.

![Symbolic Traits](http://martiancraft.com/img/blog/articles/large/20151022_sf_41-typestyles.png)

> _Symbolic Traits_

With TextKit we can build out a type system that is easy to manage with a level of control over the typography designers have been asking for--all within a dynamic and accessible environment.

TextKit gives designers and developers full control over the typography in their interfaces. It brings accessibility features to your apps, and give you access to all of the advanced features of typefaces like San Francisco. While these APIs did help make Helvetica more legible it couldn't overcome the challenges inherent to the letterforms of Helvetica.

## All in on Retina

San Francisco is a nice-looking font. It has the same invisible feel that Helvetica has with touches of DIN to aid in legibility and add a bit of style. I'm really excited to see Apple embracing optical size but I can't help but think they could have pushed this even further (time permitting).

I'm writing this right now on a late 2012 iMac -- non-Retina. SF UI is sharper than Helvetica Neue, but on non-Retina displays it's not _that much_ better in terms of legibility. SF UI still has blurry apertures and counters when set at most of the commonly used sizes. The grey tones are still spotty across long passages of text. It's an over simplification, but it still _looks like Helvetica_ with most of it's shortcomings on 1x displays.

On Retina displays it's a whole different story. SF UI feels more airy than Helvetica. The apertures render with clear definition and feel comfortably open. The letter are easily distinguished in a long string. It performs pretty well, even without my glasses on, especially in the text sizes. The spacing is a little tight in some areas, but not by much. I love SF UI on retina Macs and iOS devices--I deal with it on my iMac.

I could just upgrade my iMac, and I probably will now, but not everyone has that luxury or _needs_ it for work. There are still plenty of people using non-Retina Macs. Oh, and then there's the new 1080p Apple TV which also uses San Francisco. I haven't seen one in person yet, maybe they made some additional changes to the typeface for the TV, but if they didn't expect to still be squinting at your TV as you try and scan through titles. The switch to black text on a light background on the new tvOS UI will help but I'd still expect to see it perform very similar to SF on non retina, which is less than ideal. I'd bet SF UI will look great when we have a 4K Apple TV -- but we're not there yet.

> It may be a lot to ask for since traditionally Apple designs for the latest and greatest technology, but I think we need an optical cut of SF UI for non-Retina Macs. 

That was my "big idea" going into this article after looking at the developer preview in June on my non-Retina iMac, but after the _only_ 1080p Apple TV announcement this month, I think this becomes even more important. Apple embraced optical sizes which tells me they **really do care about legibility** -- they just ignored non-Retina.

These things take time though and I doubt the type design team at Apple is very large. I'm not proposing a font designed for ultra low resolution like Verdana or Input -- rather something more subtle and _on brand_. If Apple were to exaggerate the changes they made to the text sized glyphs vs the display cuts--opening the apertures and counters a bit more; and adjusted the spacing metrics…and maybe the weights, I think we could have a really nice looking, legible version of SF UI for low-resolution displays without any real impact to style. Would it be obsolete in 5-7 years? Yes, probably--but if everyone using a 1x display could have a better experience until everything is retina, isn't it worth it?

  * To download [SanFrancisco](http://www.apple.com/fonts) you need a developer account.
  * You may only use San Francisco for creating mock-ups of user interfaces to be used in software products running on Apple's operating systems. Read through the EULA included with the download. 
