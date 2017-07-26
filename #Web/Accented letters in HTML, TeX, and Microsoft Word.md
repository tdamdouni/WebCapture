# Accented letters in HTML, TeX, and Microsoft Word

_Captured: 2015-10-08 at 17:41 from [www.johndcook.com](http://www.johndcook.com/blog/accented_letters_page/)_

This page explains the patterns behind how HTML, TeX, and Microsoft Word represent accented letters. The page begins with explanations for [HTML](http://www.johndcook.com/blog/accented_letters_page/), [LaTeX](http://www.johndcook.com/blog/accented_letters_page/), and [Word](http://www.johndcook.com/blog/accented_letters_page/) and concludes with a [chart](http://www.johndcook.com/blog/accented_letters_page/) summarizing how accents are handled across languages.

## HTML

HTML uses "entities", escape sequences, to represent accented letters (diacritics) with only ASCII characters. For example, a is encoded as `&agrave;`. The general pattern for constructing an HTML entity for an accented letter is

> & \+ letter + accent code + ;

The letters that can be accented this way are **a**, **c**, **e**, **i**, **n**, **o**, **u**, and **y**, in both their lower-case and upper-case forms.

The possible accent codes are **grave**, **acute**, **circ** (circumflex), **tilde**, and **uml** (umlaut).

Not all combinations of letters and accents are possible. For example, the entity `&agrave;` places a grave accent on the letter "a", but there is no entity `&ngrave;` to put such an accent on top of a letter "n."

There are three additional accent codes that can only be applied to a single letter. The code **ring** can only be applied to "a." `&aring;` produces a and `&Aring;` produces Å. The **cedil** (cedilla) code can only be applied to "c." `&ccedil;` produces ç and `&Ccedil;` produces Ç. Finally, **slash** only applies to "o." `&oslash;` produces ø and `&Oslash;` produces Ø.

The ae ligature follows a pattern similar to accents: `&aelig;` produces ae and `&AElig;` produces Æ.

Note that most HTML entities are not legal in XHTML. See [Greek letters in HTML, XML, TeX, and Unicode](http://www.johndcook.com/blog/greek_letters/) for an explanation of how to denote Unicode symbols in ASCII text in XML.

## TeX and LaTeX

TeX uses a consistent pattern for adding diacritical marks to letters:

> \ + code + letter

The code is a single character indicating the kind of diacritical mark to add. Unlike HTML entities, any mark can be added to any letter. Letters may be upper-case or lower-case.

TeX supports 14 diacritical mark codes. The ones corresponding to HTML entities listed above are ``` (grave), `'` (acute), `^` (circumflex), `~` (tilde), `"` (umlaut), and `c` (cedilla).

Examples: jalapeño is written `jalape\~no` in TeX. garçon is written `gar\ccon`.

TeX uses `\ae` and `\AE` for ae and Æ, `\o` and `\O` for ø and Ø, and `\aa` and `\AA` for a and Å.

Note that the above remarks only apply to text mode. LaTeX handles accents differently in math mode.

## Microsoft Word

Microsoft Word is nearly identical to HTML in the accent-letter combinations it supports, but similar to TeX in the key strokes that it uses.

To add a grave accent to a vowel in Word, hold down the control key and press ``` (sometimes call the back tick or back quote symbol, often in the top left of a US keyboard) then type the letter to accent. In short, `CTRL` \+ ``` is the escape sequence.

Use `CTRL` \+ `'` for an acute accent, `CTRL` \+ `^` for circumflex, `CTRL` \+ `SHIFT` \+ `~` for tilde, `CTRL` \+ `SHIFT` \+ `:` for umlaut, and `CTRL` \+ `,` for cedilla.

Word uses `CTRL` \+ `SHIFT` \+ `&` for ae and Æ, `CTRL` \+ `/` for ø and Ø, and `CTRL` \+ `SHIFT` \+ `@` for a and Å.

## Combined chart

**Accent** **HTML** **TeX** **Word**

grave
`grave`
`\\``
`CTRL` \+ ```

acute
`acute`
`\'`
`CTRL` \+ `'`

circumflex
`circ`
`\^`
`CTRL` \+ `^`

tilde
`tidle`
`\~`
`CTRL` \+ `SHIFT` \+ `~`

umlaut
`uml`
`\"`
`CTRL` \+ `SHIFT` \+ `:`

cedilla
`cedil`
`\c`
`CTRL` \+ `,`

ae, Æ
`&aelig;`, `&AElig;`
`\ae`, `\AE`
`CTRL` \+ `SHIFT` \+ `&` \+ a or A

ø, Ø
`&oslash;`, `&Oslash;`
`\o`, `\O`
`CTRL` \+ `/` \+ o or O

a, Å
`&aring;`, `&Aring;`
`\aa`, `\AA`
`CTRL` \+ `SHIFT` \+ `@` \+ a or A
