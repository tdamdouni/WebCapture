# Common Math Symbols in HTML, XML, TeX, and Unicode

_Captured: 2015-10-02 at 22:03 from [www.johndcook.com](http://www.johndcook.com/blog/math_symbols/)_

HTML provides a mnemonic form for 252 of the most common symbols. (See a full list from the [W3C](http://www.w3.org/TR/html4/sgml/entities.html).) These are called "character entities." You can simply put Unicode characters directly into an HTML page as long as you have an input method and the content-type of your HTML page is correctly set. However character entities let you specify non-ASCII characters in HTML using only ASCII text.

See notes below

## Table of symbols

**Symbol** **TeX** **Entity** **Unicode**

¬
\neg
&not;
x00AC

±
\pm
&plusmn;
x00B1

*
\cdot
&middot;
x00B7

->
\to
&rarr;
x2192

⇒
\Rightarrow
&rArr;
x21D2

⇔
\Leftrightarrow
&hArr;
x21D4

∀
\forall
&forall;
x2200

∂
\partial
&part;
x2202

∃
\exists
&exist;
x2203

∅
\emptyset
&empty;
x2205

∇
\nabla
&nabla;
x2207

∈
\in
&isin;
x2208

∉
\not\in
&notin;
x2209

∏
\prod
&prod;
x220F

∑
\sum
&sum;
x2211

√
\surd
&radic;
x221A

∞
\infty
&infin;
x221E

∧
\wedge
&and;
x2227

∨
\vee
&or;
x2228

∩
\cap
&cap;
x2229

∪
\cup
&cup;
x222A

∫
\int
&int;
x222B

≈
\approx
&asymp;
x2248

≠
\neq
&ne;
x2260

≡
\equiv
&equiv;
x2261

≤
\leq
&le;
x2264

≥
\geq
&ge;
x2265

⊂
\subset
&sub;
x2282

⊃
\supset
&sup;
x2283

°
^\circ
&deg;
x00B0

×
\times
&times;
x00D7

⌊
\lfloor
&lfloor;
x230A

⌋
\rfloor
&rfloor;
x230B

⌈
\lceil
&lceil;
x2308

⌉
\rceil
&rceil;
x2309

## Hex forms

The hex representation of a character in HTML is the Unicode value in hex with `&#` added on the left and `;` on the right. For example, the symbol ∞ can be written `&infin;` or `&#x221E;` based on its Unicode value x221E. Internet Explorer 4.01 did not support hex representations, but all newer browsers do.

## XML

Most HTML entities are not legal in XML. You must use the hex representations instead. Note that you can insert other Unicode characters this way, even if they do correspond to an HTML character entity. However, you run the risk of some users not having the necessary fonts installed on their computer.

## Browser compatibility notes

The symbols above display correctly in Internet Explorer 4.01 and later with three exceptions: `&empty;`. `&notin;`, and `&sdot;` do not work in IE until version 7. Otherwise all symbols work in a wide variety of browsers.

You can access a huge collection of symbols by inserting Unicode characters. However, you cannot count on a client having the necessary fonts installed to display less common symbols. See [Unicode Codepoint chart](http://inamidst.com/stuff/unidata/).

## Other resources

A complete list of LaTeX symbols is available [ here](http://web.archive.org/web/20150409230511/http://www.tex.ac.uk/tex-archive/info/symbols/comprehensive/symbols-a4.pdf).

You can find more about Unicode from the [Unicode Consortium](http://www.unicode.org/).

See also [Greek letters in HTML, XML, TeX, and Unicode](http://www.johndcook.com/blog/greek_letters/).
