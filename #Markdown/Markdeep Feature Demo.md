# Markdeep Feature Demo

_Captured: 2015-10-17 at 10:12 from [home.in.tum.de](http://home.in.tum.de/~amdouni/html-data/features.md.html)_

This document shows the features of [Markdeep](http://casual-effects.com/markdeep). Markdeep is a text formatting syntax that extends Markdown, and a Javascript program for making it work in browsers. The two most powerful features are its ability to run in any web **browser** on the client side and the inclusion of **diagrams**.

[Click here](http://home.in.tum.de/~amdouni/html-data/features.md.html?noformat) to see this document without automatic formatting.

Markdown is free and easy to use. It doesn't need a plugin, or Internet connection. There's nothing to install. Just start writing in Vi, Nodepad, Emacs, Visual Studio, Atom, or another editor! You don't have to export, compile, or otherwise process your document.

Text formatting: **bold**, **bold**, _italic_, _italic_, , [hyperlink](http://casual-effects.com), `inline code`.

Hyperlinked explicit URL <http://casual-effects.com> and e-mail [president@whitehouse.gov](mailto:president@whitehouse.gov).

Markdeep intelligently does not apply bold or italic formatting to math expressions such as x = 3 * y - 2 * z or WORDS_WITH_INTERNAL_UNDERSCORES. It also protects HTML `<tags>` in code blocks from disappearing.

## Subsection Header

Lists and floating diagrams:

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

## Images

There's no natural way to embed an image into something that is readable as a text document. Markdeep follows markdown's somewhat reasonable syntax:

![A picture of a robot](http://home.in.tum.de/~amdouni/html-data/robot.jpg)

or, just use a raw HTML `<img>` tag, which allows better format control:

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

## Diagrams

Diagrams can be inserted alongside, as in this example, or between paragraphs of text as shown below.

The diagram parser leaves symbols used as labels unmodified, so characters like > and ( can appear inside of the diagram. In fact, any plain text may appear in the diagram. In addition to labels, any un-beautified text will remain in place for use as ASCII art. Thus, the diagram is rarely distored by the beautification process.

## Lines with Decorations

## Graph with Large Nodes

## Graph with Small Nodes

## Flow Chart

## Line Ends

## Trees

## Big Shapes

## Small Shapes

## Overlaps and Intersections

## Big Grids

## Small Grids

## Graphics Diagrams

## Icon Diagram

## Various Syntaxes for Horizontal Rules

The following are all produced by different patterns in the source:

Markdeep automatically includes [MathJax](http://mathjax.org) if your document contains equations and you have an Internet connection. That means you get the **full power of LaTeX, TeX, MathML, and AsciiMath notation**. Just put math inside single or double dollar signs.

Lo(X,o)=Le(X,o)+∫ΩLi(X,i)fX(i,o)|⋅i|di

You can also use LaTeX equation syntax directly to obtain numbered equations:

If you don't have equations in your document, then Markdeep won't connect to the MathJax server. Either way, it runs MathJax after processing the rest of the document, so there is no delay.

Markdeep is smart enough to distinguish non-math use of dollar signs, such as $2.00 and $4.00 on the same line. It also contains some useful extra commands by default default (well, useful if you work on computer graphics) as shown in the examples below. Note that inline math requires a space after the dollar sign to distinguish it from regular text usage.

CodeSymbol

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
