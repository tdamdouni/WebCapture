# Markdeep Feature Demo

_Captured: 2015-11-01 at 23:52 from [casual-effects.com](http://casual-effects.com/markdeep/features.md.html)_

This document shows the features of [Markdeep](http://casual-effects.com/markdeep). Markdeep is a text formatting syntax that extends Markdown, and a Javascript program for making it work in browsers. The two most powerful features are its ability to run in any **web browser** on the client side and the inclusion of **diagrams**.

[Click here](http://casual-effects.com/markdeep/features.md.html?noformat) to see this document without automatic formatting.

Markdeep is free and easy to use. It doesn't need a plugin, or Internet connection. There's nothing to install. Just start writing in Vi, Nodepad, Emacs, Visual Studio, Atom, or another editor! You don't have to export, compile, or otherwise process your document.

# Section Header

Text formatting: **bold**, **bold**, _italic_, _italic_, strikethrough, [hyperlink](http://casual-effects.com), `inline code`.

Hyperlinked explicit URL <http://casual-effects.com> and e-mail [president@whitehouse.gov](mailto:president@whitehouse.gov). Even URLs with ? and & in them: [http://foo.com/bar?arg=value&hello](http://foo.com/bar?arg=value&hello).

Markdeep intelligently does not apply bold or italic formatting to math expressions such as x = 3 * y - 2 * z or WORDS_WITH_INTERNAL_UNDERSCORES. It also protects HTML `<tags>` in code blocks from disappearing.

## Subsection Header

  1. Monday 
  2. Tuesday 
    1. Morning 
    2. Afternoon 
  3. Wednesday 
    * Bullets 
  4. Thursday
  5. Friday

Ut at felis diam. Aliquam massa odio, pharetra ut neque sed, commodo dignissim orci. Curabitur quis velit gravida, blandit diam nec, lacinia quam. Maecenas pharetra, velit in vestibulum auctor, diam ipsum suscipit arcu, non sodales orci nibh sit amet leo. Nulla dictum.

  * Bread
  * Fish
  * Milk
  * Cheese

> This is an indented blockquote: Ut at felis diam. Aliquam massa odio, pharetra ut neque sed, commodo dignissim orci. Curabitur quis velit gravida, blandit diam nec, lacinia quam. Maecenas pharetra, velit in vestibulum auctor, diam ipsum suscipit arcu, non sodales orci nibh sit amet leo. Nulla dictum

Lists can also:

  * Use asterisks
  * Instead of
  * Minus signs
  * `or have code`
  * _and_ other formatting

or

  * Use plus
  * Signs

## Images

There's no natural way to embed an image into something that is readable as a text document. Markdeep follows markdown's somewhat reasonable syntax:

![A picture of a robot](http://casual-effects.com/markdeep/robot.jpg)

> _or, just use a raw HTML <img> tag, which allows better format control:_

## Arrows, Dashes, Times

Markdeep converts `==>` and `<==` to arrows if they aren't in a code block. Examples:

  * if this -> then that
  * here <- there

If there is an em dash--like that, or an en dash-like that, they will be converted to the appropriate character.

An "x" between numbers, such as 1920×1080, will be converted to the times symbol.

Negative numbers, such as −5 and minus signs between numbers such as 2 − 1, will have a minus sign instead of a hyphen.

## Fenced Code Blocks

Fenced code blocks with syntax coloring and automatic programming language detection:
    
    
    void insertion_sort(int data[], int length) {
        for (int i = 0; i < length; ++i) {
    
            for (int j = i; (j > 0) && (data[j] < data[j - 1]); --j) {
                int temp = data[j];
                data[j] = data[j - 1];
                data[j - 1] = temp;
            }
    
        }
    }

Alternative back-tick markup:
    
    
    def insertionSort(data):
        for i in range(0, len(data)):
            j = i;
    
            while (j > 0) and (data[j] < data[j - 1]):
                temp = data[j]
                data[j] = data[j - 1]
                data[j] = temp
                --j

You can even have HTML in a code block:
    
    
    <b>Show this</b> HTML as <i>source</i>,
    <code>not code</code>.

...and of course, Markdeep inside Markdeep (although the syntax coloring sometimes goes crazy):
    
    
    - Do not 
    - Format
      - this as a **list**!

## Tables

MaineIowaColorado

1
4
10

ME
IA
CO

Blue
Red
Brown

## Definition Lists

Apple
    Pomaceous fruit of plants of the genus Malus in the family Rosaceae.
Orange
    The fruit of an evergreen tree of the genus Citrus.

## Diagrams

Diagrams can be inserted alongside, as in this example, or between paragraphs of text as shown below. 

The diagram parser leaves symbols used as labels unmodified, so characters like > and ( can appear inside of the diagram. In fact, any plain text may appear in the diagram. In addition to labels, any un-beautified text will remain in place for use as ASCII art. Thus, the diagram is rarely distored by the beautification process.

# Diagram Examples

## Lines with Decorations

## Graph with Large Nodes

## Graph with Small Nodes

## Flow Chart

## Line Ends

## Trees

## Circuits

## Big Shapes

## Small Shapes

## Overlaps and Intersections

## Big Grids

## Small Grids

## Graphics Diagram

## Icon Diagram

## Various Syntaxes for Horizontal Rules

The following are all produced by different patterns in the source:

# Embedded Math

Markdeep automatically includes [MathJax](http://mathjax.org) if your document contains equations and you have an Internet connection. That means you get the **full power of LaTeX, TeX, MathML, and AsciiMath notation**. Just put math inside single or double dollar signs. Lo(X,o)=Le(X,o)+∫ΩLi(X,i)fX(i,o)|⋅i|diYou can also use LaTeX equation syntax directly to obtain numbered equations:

If you don't have equations in your document, then Markdeep won't connect to the MathJax server. Either way, it runs MathJax after processing the rest of the document, so there is no delay.

Markdeep is smart enough to distinguish non-math use of dollar signs, such as $2.00 and $4.00 on the same line. Note that inline math requires a space after the dollar sign to distinguish it from regular text usage.

Unless you've changed out the default MathJax processor, you can define your own LaTeX macros by executing `\newcommand` within dollar signs, just as you would in LaTeX. MathJax provides a handful of commands defined this way by default because they're things that I frequently need:

CodeSymbol

`\O(n)`
O(n)\O(n) 

`\mathbf{M}^\T`
MT\mathbf{M}^\T

`45\degrees`
45∘45\degrees

`x \in \Real`
x∈Rx \in \Real

`x \in \Integer`
x∈Zx \in \Integer

`x \in \Boolean`
x∈Bx \in \Boolean

`x \in \Complex`
x∈Cx \in \Complex

` \n `
ˆn\n 

` \w `
ˆω\w 

` \wo `
ˆωo\wo 

` \wi `
ˆωi\wi 

` \wh `
ˆωh\wh 

` \Li `
Li\Li 

` \Lo `
Lo\Lo 

` \Lr `
Lr\Lr 

` \Le `
Le\Le 

# Headers

In addition to the underlined headers, you can also use ATX-style headers, with multiple # signs:

## H2

### H3

#### H4

##### H5

H6

Although: do you really need six levels of subsection nesting?!

# Custom Formatting

Markdeep uses CSS for styling. That means you can embed a style sheet to override anything thatn you don't like about the built-in styling. For example, if you don't want section numbering, just use:
    
    
    <style> h1:before, h2:before { content: none; }</style>

Markdeep uses Markdown's syntax, even where I disagree with the choices. But you aren't stuck with that. Do you wish that Markdown had specified single-asterisk for `*bold*`? You can have that:
    
    
    <style>em.asterisk { font-style: normal; font-weight: bold; }</style>

# Unicode (in UTF-8 encoding)

To support Unicode input, you must add <`meta charset="utf-8"`> to the _top_ of your document (in the first 512 bytes).

  * Asian characters 林花謝了春紅 太匆匆, 無奈朝來寒雨 晚來風 胭脂淚 留人醉 幾時重, 自是人生長恨 水長東
  * Asian punctuation: 、。！，：
  * Matching pairs «»‹›""''〖〗【】「」『』〈〉《》〔〕
  * Greek ΑΒΓΔ ΕΖΗΘ ΙΚΛΜ ΝΞΟΠ ΡΣΤΥ ΦΧΨΩ αβγδ εζηθ ικλμ νξοπ ρςτυ φχψω
  * Currency ¤ $ ¢ € ₠ £ ¥
  * Common symbols (C) ® ™ ² ³ § ¶ † ‡ ※
  * Bullets •◦ ‣ ✓ ●■◆ ○□◇ ★☆ ♠♣♥♦ ♤♧♡♢
  * Phonetic ᴁ ᴂ ᴈ
  * Music ♩♪♫♬♭♮♯
  * Punctuation "" '' ¿¡ ¶§ª \- ‐ ‑ ‒ - -- ― …
  * Accents aaaaaaaeç eeee iiii ðñooooo øuuuuýþÿ ÀÁÂÃÄÅ Ç ÈÉÊË ÌÍÎÏ ÐÑ ÒÓÔÕÖ ØÙÚÛÜÝÞß
  * Math ° ⌈⌉ ⌊⌋ ∏ ∑ ∫ ×÷ ⊕ ⊖ ⊗ ⊘ ⊙ ⊚ ⊛ ∙ ∘ ′ ″ ‴ ∼ ∂ √ ≔ × ⁱ ⁰ ¹ ² ³ ₀ ₁ ₂ π ∞ ± ∎
  * Logic & Set Theory ∀¬∧∨∃⊦∵∴∅∈∉⊂⊃⊆⊇⊄⋂⋃
  * Relations ≠≤≥≮≯≫≪≈≡
  * Sets ℕℤℚℝℂ
  * Arrows <-->↑↓ ↔ ↖↗↙↘ ⇐⇒⇑⇓ ⇔⇗ ⇦⇨⇧⇩ ↞↠↟↡ ↺↻ ☞☜☝☟
  * Computing ⌘ ⌥ ‸ ⇧ ⌤ ↑ ↓ -> <- ⇞ ⇟ ↖ ↘ ⌫ ⌦ ⎋⏏ ↶↷ ◀▶▲▼ ◁▷△▽ ⇄ ⇤⇥ ↹ ↵↩⏎ ⌧ ⌨ ␣ ⌶ ⎗⎘⎙⎚ ⌚⌛ ✂✄ ✉✍
  * Digits ➀➁➂➃➄➅➆➇➈➉
  * Religious and cultural symbols ✝✚✡☥⎈☭☪☮☺☹☯☰☱☲☳☴☵☶☷
  * Dingbats ❦☠☢☣☤♲♳⌬♨♿ ☉☼☾☽ ♀♂ ♔♕♖ ♗♘♙ ♚♛ ♜♝♞♟
