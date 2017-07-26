# You, Me And The Emoji: Character Sets, Encoding And Emoji

_Captured: 2017-01-31 at 11:42 from [www.smashingmagazine.com](https://www.smashingmagazine.com/2016/11/character-sets-encoding-emoji/)_

![Map of the Basic Multilingual Plane](https://www.smashingmagazine.com/wp-content/uploads/2016/11/roadmap_to_unicode_bmp.svg-650px-preview-opt.png)[61](https://www.smashingmagazine.com/2016/11/character-sets-encoding-emoji/)

> _Figure 1: A map of Unicode's basic multilingual plane (plane 0), visualized as 256 boxes of 256 code points each and color-coded (Image: Wikipedia) (Large preview)_

![Unicode planes and used code point ranges](https://www.smashingmagazine.com/wp-content/uploads/2016/09/unicode_planes_20160611_500x391.png)[64](https://www.smashingmagazine.com/2016/11/character-sets-encoding-emoji/)

> _Figure 2: Table (reproduced here as an image) depicting Unicode planes and code point ranges, both used and unused (Image: Wikipedia) (Large preview)_

![Ex representations of 4 emoji](https://www.smashingmagazine.com/wp-content/uploads/2016/09/emoji-examples500x380.png)[88](https://www.smashingmagazine.com/2016/11/character-sets-encoding-emoji/)

> _Figure 3: Example representations of four emoji shown in four styles each. (Image: Unicode, Inc.) (Large preview)_

![Parsing model diagram](https://www.smashingmagazine.com/wp-content/uploads/2016/09/parsing_model_overview392x600.png)[97](https://www.smashingmagazine.com/2016/11/character-sets-encoding-emoji/)

> _Parsing model diagram_

**More About Missing Characters: a Deep (Short) Dive**

Anyone paying attention closely enough has encountered missing characters on the web. We usually, well most of us at least, shrug it off as some sort of undiagnosed font or encoding issue. But dear reader, you are not "most of us". You aspire to know more. 🤓 (Nerd face, `U+1F913`)

As you will see shortly this is pretty low-level stuff and really beyond the scope of the article but let's discuss it briefly just to make sure there really is nothing tricky (or broken) going on.

Those Tifinagh characters are intentionally obscure. That's why I chose them. If, on the computer of the person viewing an HTML page, there is no font installed that includes glyphs for those characters then something else has to be displayed (or nothing at all).

With CSS, we're used to thinking in terms of the font-family property and lists of fonts that look something like:
    
    
    font-family: "Helvetica Neue", Arial, Helvetica, Geneva, sans-serif;

Notice that we're including lots of emoji in this document, and there is at least one Japanese character too, among other exotic characters, but no fonts with glyphs for those characters are included in any font-family list in any rule applied to this page. That seems odd at first, right? Maybe you've just assumed it has something to do with the the generic family typically included at the end of our font lists. We don't really bother to think about it I suppose.

Every modern OS has a system for handling cascading font fallbacks that is part of the lower-level system, and so typically works across all applications.

In theory it's similar fonts lists in CSS, just more complex.

For example, On the macOS and iOS platforms this is handled by [Core Text](https://developer.apple.com/reference/coretext), a low-level text layout and font handling engine.

No single font covers the entire Unicode space. When a code point is encountered for which there is no glpyh in the chosen font, a list of fallback fonts will be tried, in order to find a glyph for the code point somewhere else (i.e. in some other font).

This excerpt from [Apple's Core Text Programming Guide](https://developer.apple.com/library/content/documentation/StringsTextFonts/Conceptual/CoreText_Programming/Overview/Overview.html) essentially says the same thing:

> Core Text font references provide a sophisticated, automatic font-substitution mechanism called font cascading, which picks an appropriate font to substitute for a missing font while taking font traits into account. Font cascading is based on cascade lists, which are arrays of ordered font descriptors. There is a system default cascade list (which is polymorphic, based on the user's language setting and current font) and a font cascade list that is specified at font creation time. Using the information in the font descriptors, the cascading mechanism can match fonts according to style as well as matching characters…

This is why you can select a single display font for an application like a text editor, maybe "Source Code Pro" for example, and still copy and paste emoji chracters into the document. There are no emoji symbols in Source Code Pro. That's the font-substitution mechanism at work.

But what if a glyph still can't be found. The font handling subsystem is not out of options quite yet. There are 3 unique fonts that may come into play at this point:

  * The Unicode BMP Fallback font
  * The Unicode Last Resort font
  * GNU Unifont

The Unicode BMP Fallback font contains a glyph for every character in the Unicode BMP. Each one of these glyphs displays as a box containing the hexadecimal digits corresponding to the code point value.

If those Tifinagh characters are missing, and instead you're seeing boxes containing hex digits then you're looking at a glyph from the BMP Fallback font.

Next, the Last Resort font, is just that. It is literally named "LastResort". Unlike the Unicode BMP Fallback font, the Last Resort font contains glyphs that provide information about the missing characters.

[This font can be downloaded from the Unicode Consortium](http://www.unicode.org/policies/lastresortfont_eula.html), although there is probably no good reason to do that. The idea is that the font should be bundled into the OS and part of its text handling mechanism.

From the Last Resort font download page:

> The Last Resort font is a collection of glyphs to represent types of Unicode characters. These glyphs are designed to allow users to recognize that an encoded value is one of the following:
> 
>   * a specific type of Unicode character
>   * in the Private Use Area (no private agreement exists)
>   * unassigned (reserved for future assignment)
>   * one of the illegal character codes.
> 
> These glyphs are used as the backup of "last resort" to any other font; if the font cannot represent any particular Unicode character, the appropriate missing glyph from the Last Resort font is used instead. This provides users with the ability to tell what sort of character it is, and gives them a clue as to what type of font they would need to display the characters correctly.

More information can be found in in the [Unicode Core Spec](http://unicode.org/versions/Unicode9.0.0/) itself in "Section 5.3: Unknown and Missing Characters".

The last fallback I'll mention is the [GNU Unifont](http://unifoundry.com/unifont.html), which attempts to accomplish the same thing as the Unicode BMP Fallback font, but takes a different approach. The goal here is to create "lite" bitmapped versions of all of the fonts in the Unicode BMP. (The font has grown to include characters beyond the BMP as well.)

Whereas the the BMP Fallback font just tells us the code point value of missing glyphs, the GNU Unifont attempts to show us what the characters look like. It's intended to be a better middle ground.

Now let's pick up our story. For those of you who are seeing all of the Tifinagh characters…
