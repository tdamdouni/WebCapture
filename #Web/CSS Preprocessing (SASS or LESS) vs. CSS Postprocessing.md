# CSS Preprocessing (SASS or LESS) vs CSS Postprocessing

_Captured: 2015-12-12 at 23:13 from [programmers.stackexchange.com](http://programmers.stackexchange.com/questions/261993/css-preprocessing-sass-or-less-vs-css-postprocessing/262073#262073)_

The difference between postprocessing and preprocessing is non-existent, at least in the case of programming languages. Both describe a transformation from some format A (which is authored by a human) to format B (which is necessary to have, but inconvenient to write):
    
    
    “compiler”:   A    -> B
    
    == CSS-related examples ==less:         LESS -> CSS
    sass:         SASS -> CSS
    sass:         SCSS -> CSS
    autoprefixer: CSS  -> CSS
    minifier:     CSS  -> CSS
    pleeease:     CSS  -> CSS
    
    == Other examples ==
    c preprocessor: C        -> C without macros
    gcc:            C        -> machine code
    pandoc:         LaTeX    -> HTML
    pandoc:         Markdown -> HTML
    pandoc:         LaTeX    -> Markdown

A few observations on those examples:

  * The input and output format can be the same. This is the case in code tidiers, minifiers, and other processors that somehow simplify the source. E.g. the C preprocessor expands macros and constants in the source code. This is equivalent to autoprefixer, which expands unprefixed CSS directives into their prefixed variants.

  * Processors can involve multiple sub-processors that each do some part of the transformation.

    * pleeease can pipe the code through various processors such as autoprefixer or a minifer.
    * A C compiler includes a preprocessor stage.
    * Pandoc has a processor that parses the input (e.g. a Markdown document) into a common data structure, then passes this intermediate representation to another processor that turns it into the target format (e.g. HTML). Pandoc's architecture is fairly pluggable, and allows additional preprocessing stages to be added. For example, this is used to implement bibliography references in Pandoc's Markdown dialect, by expanding the syntax into a more standard Markdown form.

If pleeease calls itself a post-processor rather than a pre-processor, this is done …

  * to differentiate itself from preprocessors like LESS or SASS. The selling point of LESS and SASS/SCSS is that they extend or replace CSS syntax. Pleeease instead wants to make existing CSS code more portable.
  * to indicate pleeease is to be used after development. If you use SASS to write your styles, you have to run the compiler _before_ you serve the style sheet to your browser. And _after_ you've written the style, you can run pleeease on the result to make it more palatable to older browsers.

To summarize: There is no technical reason to differentiate between preprocessing and postprocessing in the realm of programming languages. The term "postprocessing" is not widely used in this domain, and one should therefore substitute and prefer "preprocessing", "compiling", or "transformation".

***

The goals of preprocessing and postprocessing are quite different:

* preprocessing focuses on helping programmers write simpler and more maintainable code
* postprocessing focuses on improving the runtime efficiency of code

It is true that preprocessors also delve into the realm of efficient code (one common example is minification) and the reason for that is simply because they can. Why force developers use another tool to minify LESS output when a simple pass implemented by the LESS compiler could do that?

Seeing how preprocessors have better access to the intent of the developer, they have a potential to provide better optimizations than postprocessors can. In practice, a specialized tool could yield better results.

There is no reason not to use both a preprocessor and a postprocessor, but the actual usefulness should be determined on a case by case basis (both combination of tools and use cases can influence it). It is entirely possible to obtain the best results by turning off some features of the preprocessor and relying on the postprocessor for them.
