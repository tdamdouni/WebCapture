## Pandoc's markdown

Pandoc understands an extended and slightly revised version of John Gruberâs [markdown](http://daringfireball.net/projects/markdown/) syntax. This document explains the syntax, noting differences from standard markdown. Except where noted, these differences can be suppressed by using the `markdown_strict` format instead of `markdown`. An extensions can be enabled by adding `+EXTENSION` to the format name and disabled by adding `-EXTENSION`. For example, `markdown_strict+footnotes` is strict markdown with footnotes enabled, while `markdown-footnotes-pipe_tables` is pandocâs markdown without footnotes or pipe tables. 

### Philosophy

Markdown is designed to be easy to write, and, even more importantly, easy to read: 

> A Markdown-formatted document should be publishable as-is, as plain text, without looking like itâs been marked up with tags or formatting instructions. â [John Gruber](http://daringfireball.net/projects/markdown/syntax#philosophy)

This principle has guided pandocâs decisions in finding syntax for tables, footnotes, and other extensions. 

There is, however, one respect in which pandocâs aims are different from the original aims of markdown. Whereas markdown was originally designed with HTML generation in mind, pandoc is designed for multiple output formats. Thus, while pandoc allows the embedding of raw HTML, it discourages it, and provides other, non-HTMLish ways of representing important document elements like definition lists, tables, mathematics, and footnotes. 

### Paragraphs

A paragraph is one or more lines of text followed by one or more blank lines. Newlines are treated as spaces, so you can reflow your paragraphs as you like. If you need a hard line break, put two or more spaces at the end of a line. 

#### Extension: `escaped_line_breaks`

A backslash followed by a newline is also a hard line break. Note: in multiline and grid table cells, this is the only way to create a hard line break, since trailing spaces in the cells are ignored. 

### Headers

There are two kinds of headers: Setext and ATX. 

#### Setext-style headers

A setext-style header is a line of text âunderlinedâ with a row of `=` signs (for a level one header) or `-` signs (for a level two header): 

    
    
    A level-one header
    ==================
    
    A level-two header
    ------------------
    

The header text can contain inline formatting, such as emphasis (see [Inline formatting](pandocs-markdown.html#inline-formatting), below). 

#### ATX-style headers

An ATX-style header consists of one to six `#` signs and a line of text, optionally followed by any number of `#` signs. The number of `#` signs at the beginning of the line is the header level: 

    
    
    ## A level-two header
    
    ### A level-three header ###
    

As with setext-style headers, the header text can contain formatting: 

    
    
    # A level-one header with a [link](/url) and *emphasis*
    

##### Extension: `blank_before_header`

Standard markdown syntax does not require a blank line before a header. Pandoc does require this (except, of course, at the beginning of the document). The reason for the requirement is that it is all too easy for a `#` to end up at the beginning of a line by accident (perhaps through line wrapping). Consider, for example: 

    
    
    I like several of their flavors of ice cream:
    #22, for example, and #5.
    

#### Header identifiers

##### Extension: `header_attributes`

Headers can be assigned attributes using this syntax at the end of the line containing the header text: 

    
    
    {#identifier .class .class key=value key=value}
    

Thus, for example, the following headers will all be assigned the identifier `foo`: 

    
    
    # My header {#foo}
    
    ## My header ##    {#foo}
    
    My other header   {#foo}
    ---------------
    

(This syntax is compatible with [PHP Markdown Extra](https://michelf.ca/projects/php-markdown/extra/).) 

Note that although this syntax allows assignment of classes and key/value attributes, writers generally donât use all of this information. Identifiers, classes, and key/value attributes are used in HTML and HTML-based formats such as EPUB and slidy. Identifiers are used for labels and link anchors in the LaTeX, ConTeXt, Textile, and AsciiDoc writers. 

Headers with the class `unnumbered` will not be numbered, even if `\--number-sections` is specified. A single hyphen (`-`) in an attribute context is equivalent to `.unnumbered`, and preferable in non-English documents. So, 

    
    
    # My header {-}
    

is just the same as 

    
    
    # My header {.unnumbered}
    

##### Extension: `auto_identifiers`

A header without an explicitly specified identifier will be automatically assigned a unique identifier based on the header text. To derive the identifier from the header text, 

  * Remove all formatting, links, etc. 
  * Remove all footnotes. 
  * Remove all punctuation, except underscores, hyphens, and periods. 
  * Replace all spaces and newlines with hyphens. 
  * Convert all alphabetic characters to lowercase. 
  * Remove everything up to the first letter (identifiers may not begin with a number or punctuation mark). 
  * If nothing is left after this, use the identifier `section`. 

Thus, for example, 

Header  Identifier 

Header identifiers in HTML 

`header-identifiers-in-html`

_Dogs_?âin _my_ house? 

`dogs--in-my-house`

[HTML](http://www.w3.org/html/), [S5](http://meyerweb.com/eric/tools/s5/), or [RTF](http://en.wikipedia.org/wiki/Rich_Text_Format)? 

`html-s5-or-rtf`

3\. Applications 

`applications`

33 

`section`

These rules should, in most cases, allow one to determine the identifier from the header text. The exception is when several headers have the same text; in this case, the first will get an identifier as described above; the second will get the same identifier with `-1` appended; the third with `-2`; and so on. 

These identifiers are used to provide link targets in the table of contents generated by the `\--toc|--table-of-contents` option. They also make it easy to provide links from one section of a document to another. A link to this section, for example, might look like this: 

    
    
    See the section on
    [header identifiers](#header-identifiers-in-html-latex-and-context).
    

Note, however, that this method of providing links to sections works only in HTML, LaTeX, and ConTeXt formats. 

If the `\--section-divs` option is specified, then each section will be wrapped in a `div` (or a `section`, if `\--html5` was specified), and the identifier will be attached to the enclosing `<div>` (or `<section>`) tag rather than the header itself. This allows entire sections to be manipulated using javascript or treated differently in CSS. 

##### Extension: `implicit_header_references`

Pandoc behaves as if reference links have been defined for each header. So, instead of 

    
    
    [header identifiers](#header-identifiers-in-html)
    

you can simply write 

    
    
    [header identifiers]
    

or 

    
    
    [header identifiers][]
    

or 

    
    
    [the section on header identifiers][header identifiers]
    

If there are multiple headers with identical text, the corresponding reference will link to the first one only, and you will need to use explicit links to link to the others, as described above. 

Like regular reference links, these references are case-insensitive. 

Explicit link reference definitions always take priority over implicit header references. So, in the following example, the link will point to `bar`, not to `#foo`: 

    
    
    # Foo
    
    [foo]: bar
    
    See [foo]
    

### Block quotations

Markdown uses email conventions for quoting blocks of text. A block quotation is one or more paragraphs or other block elements (such as lists or headers), with each line preceded by a `>` character and an optional space. (The `>` need not start at the left margin, but it should not be indented more than three spaces.) 

    
    
    > This is a block quote. This
    > paragraph has two lines.
    >
    > 1. This is a list inside a block quote.
    > 2. Second item.
    

A âlazyâ form, which requires the `>` character only on the first line of each block, is also allowed: 

    
    
    > This is a block quote. This
    paragraph has two lines.
    
    > 1. This is a list inside a block quote.
    2. Second item.
    

Among the block elements that can be contained in a block quote are other block quotes. That is, block quotes can be nested: 

    
    
    > This is a block quote.
    >
    > > A block quote within a block quote.
    

If the `>` character is followed by an optional space, that space will be considered part of the block quote marker and not part of the indentation of the contents. Thus, to put an indented code block in a block quote, you need five spaces after the `>`: 

    
    
    >     code
    

#### Extension: `blank_before_blockquote`

Standard markdown syntax does not require a blank line before a block quote. Pandoc does require this (except, of course, at the beginning of the document). The reason for the requirement is that it is all too easy for a `>` to end up at the beginning of a line by accident (perhaps through line wrapping). So, unless the `markdown_strict` format is used, the following does not produce a nested block quote in pandoc: 

    
    
    > This is a block quote.
    >> Nested.
    

### Verbatim (code) blocks

#### Indented code blocks

A block of text indented four spaces (or one tab) is treated as verbatim text: that is, special characters do not trigger special formatting, and all spaces and line breaks are preserved. For example, 

    
    
        if (a > 3) {
          moveShip(5 * gravity, DOWN);
        }
    

The initial (four space or one tab) indentation is not considered part of the verbatim text, and is removed in the output. 

Note: blank lines in the verbatim text need not begin with four spaces. 

#### Fenced code blocks

##### Extension: `fenced_code_blocks`

In addition to standard indented code blocks, Pandoc supports _fenced_ code blocks. These begin with a row of three or more tildes (`~`) and end with a row of tildes that must be at least as long as the starting row. Everything between these lines is treated as code. No indentation is necessary: 

    
    
    ~~~~~~~
    if (a > 3) {
      moveShip(5 * gravity, DOWN);
    }
    ~~~~~~~
    

Like regular code blocks, fenced code blocks must be separated from surrounding text by blank lines. 

If the code itself contains a row of tildes or backticks, just use a longer row of tildes or backticks at the start and end: 

    
    
    ~~~~~~~~~~~~~~~~
    ~~~~~~~~~~
    code including tildes
    ~~~~~~~~~~
    ~~~~~~~~~~~~~~~~
    

##### Extension: `backtick_code_blocks`

Same as `fenced_code_blocks`, but uses backticks (```) instead of tildes (`~`). 

##### Extension: `fenced_code_attributes`

Optionally, you may attach attributes to fenced or backtick code block using this syntax: 

    
    
    ~~~~ {#mycode .haskell .numberLines startFrom="100"}
    qsort []     = []
    qsort (x:xs) = qsort (filter (< x) xs) ++ [x] ++
                   qsort (filter (>= x) xs)
    ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    

Here `mycode` is an identifier, `haskell` and `numberLines` are classes, and `startFrom` is an attribute with value `100`. Some output formats can use this information to do syntax highlighting. Currently, the only output formats that uses this information are HTML and LaTeX. If highlighting is supported for your output format and language, then the code block above will appear highlighted, with numbered lines. (To see which languages are supported, do `pandoc --version`.) Otherwise, the code block above will appear as follows: 

    
    
    <pre id="mycode" class="haskell numberLines" startFrom="100">
      <code>
      ...
      </code>
    </pre>
    

A shortcut form can also be used for specifying the language of the code block: 

    
    
    ```haskell
    qsort [] = []
    ```
    

This is equivalent to: 

    
    
    ``` {.haskell}
    qsort [] = []
    ```
    

If the `fenced_code_attributes` extension is disabled, but input contains class attribute(s) for the codeblock, the first class attribute will be printed after the opening fence as a bare word. 

To prevent all highlighting, use the `\--no-highlight` flag. To set the highlighting style, use `\--highlight-style`. For more information on highlighting, see [Syntax highlighting](syntax-highlighting.html), below. 

### Line blocks

#### Extension: `line_blocks`

A line block is a sequence of lines beginning with a vertical bar (`|`) followed by a space. The division into lines will be preserved in the output, as will any leading spaces; otherwise, the lines will be formatted as markdown. This is useful for verse and addresses: 

    
    
    | The limerick packs laughs anatomical
    | In space that is quite economical.
    |    But the good ones I've seen
    |    So seldom are clean
    | And the clean ones so seldom are comical
    
    | 200 Main St.
    | Berkeley, CA 94718
    

The lines can be hard-wrapped if needed, but the continuation line must begin with a space. 

    
    
    | The Right Honorable Most Venerable and Righteous Samuel L.
      Constable, Jr.
    | 200 Main St.
    | Berkeley, CA 94718
    

This syntax is borrowed from [reStructuredText](http://docutils.sourceforge.net/docs/ref/rst/introduction.html). 

### Lists

#### Bullet lists

A bullet list is a list of bulleted list items. A bulleted list item begins with a bullet (`*`, `+`, or `-`). Here is a simple example: 

    
    
    * one
    * two
    * three
    

This will produce a âcompactâ list. If you want a âlooseâ list, in which each item is formatted as a paragraph, put spaces between the items: 

    
    
    * one
    
    * two
    
    * three
    

The bullets need not be flush with the left margin; they may be indented one, two, or three spaces. The bullet must be followed by whitespace. 

List items look best if subsequent lines are flush with the first line (after the bullet): 

    
    
    * here is my first
      list item.
    * and my second.
    

But markdown also allows a âlazyâ format: 

    
    
    * here is my first
    list item.
    * and my second.
    

#### The four-space rule

A list item may contain multiple paragraphs and other block-level content. However, subsequent paragraphs must be preceded by a blank line and indented four spaces or a tab. The list will look better if the first paragraph is aligned with the rest: 

    
    
      * First paragraph.
    
        Continued.
    
      * Second paragraph. With a code block, which must be indented
        eight spaces:
    
            { code }
    

List items may include other lists. In this case the preceding blank line is optional. The nested list must be indented four spaces or one tab: 

    
    
    * fruits
        + apples
            - macintosh
            - red delicious
        + pears
        + peaches
    * vegetables
        + broccoli
        + chard
    

As noted above, markdown allows you to write list items âlazily,â instead of indenting continuation lines. However, if there are multiple paragraphs or other blocks in a list item, the first line of each must be indented. 

    
    
    + A lazy, lazy, list
    item.
    
    + Another one; this looks
    bad but is legal.
    
        Second paragraph of second
    list item.
    

**Note:** Although the four-space rule for continuation paragraphs comes from the official [markdown syntax guide](http://daringfireball.net/projects/markdown/syntax#list), the reference implementation, `Markdown.pl`, does not follow it. So pandoc will give different results than `Markdown.pl` when authors have indented continuation paragraphs fewer than four spaces. 

The [markdown syntax guide](http://daringfireball.net/projects/markdown/syntax#list) is not explicit whether the four-space rule applies to _all_ block-level content in a list item; it only mentions paragraphs and code blocks. But it implies that the rule applies to all block-level content (including nested lists), and pandoc interprets it that way. 

#### Ordered lists

Ordered lists work just like bulleted lists, except that the items begin with enumerators rather than bullets. 

In standard markdown, enumerators are decimal numbers followed by a period and a space. The numbers themselves are ignored, so there is no difference between this list: 

    
    
    1.  one
    2.  two
    3.  three
    

and this one: 

    
    
    5.  one
    7.  two
    1.  three
    

##### Extension: `fancy_lists`

Unlike standard markdown, Pandoc allows ordered list items to be marked with uppercase and lowercase letters and roman numerals, in addition to arabic numerals. List markers may be enclosed in parentheses or followed by a single right-parentheses or period. They must be separated from the text that follows by at least one space, and, if the list marker is a capital letter with a period, by at least two spaces.[1]

The `fancy_lists` extension also allows â`#`â to be used as an ordered list marker in place of a numeral: 

    
    
    #. one
    #. two
    

##### Extension: `startnum`

Pandoc also pays attention to the type of list marker used, and to the starting number, and both of these are preserved where possible in the output format. Thus, the following yields a list with numbers followed by a single parenthesis, starting with 9, and a sublist with lowercase roman numerals: 

    
    
     9)  Ninth
    10)  Tenth
    11)  Eleventh
           i. subone
          ii. subtwo
         iii. subthree
    

Pandoc will start a new list each time a different type of list marker is used. So, the following will create three lists: 

    
    
    (2) Two
    (5) Three
    1.  Four
    *   Five
    

If default list markers are desired, use `#.`: 

    
    
    #.  one
    #.  two
    #.  three
    

#### Definition lists

##### Extension: `definition_lists`

Pandoc supports definition lists, using the syntax of [PHP Markdown Extra](https://michelf.ca/projects/php-markdown/extra/) with some extensions.[2]

    
    
    Term 1
    
    :   Definition 1
    
    Term 2 with *inline markup*
    
    :   Definition 2
    
            { some code, part of Definition 2 }
    
        Third paragraph of definition 2.
    

Each term must fit on one line, which may optionally be followed by a blank line, and must be followed by one or more definitions. A definition begins with a colon or tilde, which may be indented one or two spaces. 

A term may have multiple definitions, and each definition may consist of one or more block elements (paragraph, code block, list, etc.), each indented four spaces or one tab stop. The body of the definition (including the first line, aside from the colon or tilde) should be indented four spaces. However, as with other markdown lists, you can âlazilyâ omit indentation except at the beginning of a paragraph or other block element: 

    
    
    Term 1
    
    :   Definition
    with lazy continuation.
    
        Second paragraph of the definition.
    

If you leave space before the definition (as in the example above), the text of the definition will be treated as a paragraph. In some output formats, this will mean greater spacing between term/definition pairs. For a more compact definition list, omit the space before the definition: 

    
    
    Term 1
      ~ Definition 1
    
    Term 2
      ~ Definition 2a
      ~ Definition 2b
    

Note that space between items in a definition list is required. (A variant that loosens this requirement, but disallows âlazyâ hard wrapping, can be activated with `compact_definition_lists`: see [Non-pandoc extensions](pandocs-markdown.html#non-pandoc-extensions), below.) 

#### Numbered example lists

##### Extension: `example_lists`

The special list marker `@` can be used for sequentially numbered examples. The first list item with a `@` marker will be numbered â1â, the next â2â, and so on, throughout the document. The numbered examples need not occur in a single list; each new list using `@` will take up where the last stopped. So, for example: 

    
    
    (@)  My first example will be numbered (1).
    (@)  My second example will be numbered (2).
    
    Explanation of examples.
    
    (@)  My third example will be numbered (3).
    

Numbered examples can be labeled and referred to elsewhere in the document: 

    
    
    (@good)  This is a good example.
    
    As (@good) illustrates, ...
    

The label can be any string of alphanumeric characters, underscores, or hyphens. 

#### Compact and loose lists

Pandoc behaves differently from `Markdown.pl` on some âedge casesâ involving lists. Consider this source: 

    
    
    +   First
    +   Second:
        -   Fee
        -   Fie
        -   Foe
    
    +   Third
    

Pandoc transforms this into a âcompact listâ (with no `<p>` tags around âFirstâ, âSecondâ, or âThirdâ), while markdown puts `<p>` tags around âSecondâ and âThirdâ (but not âFirstâ), because of the blank space around âThirdâ. Pandoc follows a simple rule: if the text is followed by a blank line, it is treated as a paragraph. Since âSecondâ is followed by a list, and not a blank line, it isnât treated as a paragraph. The fact that the list is followed by a blank line is irrelevant. (Note: Pandoc works this way even when the `markdown_strict` format is specified. This behavior is consistent with the official markdown syntax description, even though it is different from that of `Markdown.pl`.) 

#### Ending a list

What if you want to put an indented code block after a list? 

    
    
    -   item one
    -   item two
    
        { my code block }
    

Trouble! Here pandoc (like other markdown implementations) will treat `{ my code block }` as the second paragraph of item two, and not as a code block. 

To âcut offâ the list after item two, you can insert some non-indented content, like an HTML comment, which wonât produce visible output in any format: 

    
    
    -   item one
    -   item two
    
    <!-- end of list -->
    
        { my code block }
    

You can use the same trick if you want two consecutive lists instead of one big list: 

    
    
    1.  one
    2.  two
    3.  three
    
    <!-- -->
    
    1.  uno
    2.  dos
    3.  tres
    

### Horizontal rules

A line containing a row of three or more `*`, `-`, or `_` characters (optionally separated by spaces) produces a horizontal rule: 

    
    
    *  *  *  *
    
    ---------------
    

### Tables

Four kinds of tables may be used. The first three kinds presuppose the use of a fixed-width font, such as Courier. The fourth kind can be used with proportionally spaced fonts, as it does not require lining up columns. 

#### Extension: `table_captions`

A caption may optionally be provided with all 4 kinds of tables (as illustrated in the examples below). A caption is a paragraph beginning with the string `Table:` (or just `:`), which will be stripped off. It may appear either before or after the table. 

#### Extension: `simple_tables`

Simple tables look like this: 

    
    
      Right     Left     Center     Default
    -------     ------ ----------   -------
         12     12        12            12
        123     123       123          123
          1     1          1             1
    
    Table:  Demonstration of simple table syntax.
    

The headers and table rows must each fit on one line. Column alignments are determined by the position of the header text relative to the dashed line below it:[3]

  * If the dashed line is flush with the header text on the right side but extends beyond it on the left, the column is right-aligned. 
  * If the dashed line is flush with the header text on the left side but extends beyond it on the right, the column is left-aligned. 
  * If the dashed line extends beyond the header text on both sides, the column is centered. 
  * If the dashed line is flush with the header text on both sides, the default alignment is used (in most cases, this will be left). 

The table must end with a blank line, or a line of dashes followed by a blank line. 

The column headers may be omitted, provided a dashed line is used to end the table. For example: 

    
    
    -------     ------ ----------   -------
         12     12        12             12
        123     123       123           123
          1     1          1              1
    -------     ------ ----------   -------
    

When headers are omitted, column alignments are determined on the basis of the first line of the table body. So, in the tables above, the columns would be right, left, center, and right aligned, respectively. 

#### Extension: `multiline_tables`

Multiline tables allow headers and table rows to span multiple lines of text (but cells that span multiple columns or rows of the table are not supported). Here is an example: 

    
    
    -------------------------------------------------------------
     Centered   Default           Right Left
      Header    Aligned         Aligned Aligned
    ----------- ------- --------------- -------------------------
       First    row                12.0 Example of a row that
                                        spans multiple lines.
    
      Second    row                 5.0 Here's another one. Note
                                        the blank line between
                                        rows.
    -------------------------------------------------------------
    
    Table: Here's the caption. It, too, may span
    multiple lines.
    

These work like simple tables, but with the following differences: 

  * They must begin with a row of dashes, before the header text (unless the headers are omitted). 
  * They must end with a row of dashes, then a blank line. 
  * The rows must be separated by blank lines. 

In multiline tables, the table parser pays attention to the widths of the columns, and the writers try to reproduce these relative widths in the output. So, if you find that one of the columns is too narrow in the output, try widening it in the markdown source. 

Headers may be omitted in multiline tables as well as simple tables: 

    
    
    ----------- ------- --------------- -------------------------
       First    row                12.0 Example of a row that
                                        spans multiple lines.
    
      Second    row                 5.0 Here's another one. Note
                                        the blank line between
                                        rows.
    ----------- ------- --------------- -------------------------
    
    : Here's a multiline table without headers.
    

It is possible for a multiline table to have just one row, but the row should be followed by a blank line (and then the row of dashes that ends the table), or the table may be interpreted as a simple table. 

#### Extension: `grid_tables`

Grid tables look like this: 

    
    
    : Sample grid table.
    
    +---------------+---------------+--------------------+
    | Fruit         | Price         | Advantages         |
    +===============+===============+====================+
    | Bananas       | $1.34         | - built-in wrapper |
    |               |               | - bright color     |
    +---------------+---------------+--------------------+
    | Oranges       | $2.10         | - cures scurvy     |
    |               |               | - tasty            |
    +---------------+---------------+--------------------+
    

The row of `=`s separates the header from the table body, and can be omitted for a headerless table. The cells of grid tables may contain arbitrary block elements (multiple paragraphs, code blocks, lists, etc.). Alignments are not supported, nor are cells that span multiple columns or rows. Grid tables can be created easily using [Emacs table mode](http://table.sourceforge.net/). 

#### Extension: `pipe_tables`

Pipe tables look like this: 

    
    
    | Right | Left | Default | Center |
    |------:|:-----|---------|:------:|
    |   12  |  12  |    12   |    12  |
    |  123  |  123 |   123   |   123  |
    |    1  |    1 |     1   |     1  |
    
      : Demonstration of pipe table syntax.
    

The syntax is identical to [PHP Markdown Extra tables](https://michelf.ca/projects/php-markdown/extra/#table). The beginning and ending pipe characters are optional, but pipes are required between all columns. The colons indicate column alignment as shown. The header cannot be omitted. To simulate a headerless table, include a header with blank cells. 

Since the pipes indicate column boundaries, columns need not be vertically aligned, as they are in the above example. So, this is a perfectly legal (though ugly) pipe table: 

    
    
    fruit| price
    -----|-----:
    apple|2.05
    pear|1.37
    orange|3.09
    

The cells of pipe tables cannot contain block elements like paragraphs and lists, and cannot span multiple lines. Note also that in LaTeX/PDF output, the cells produced by pipe tables will not wrap, since there is no information available about relative widths. If you want content to wrap within cells, use multiline or grid tables. 

Note: Pandoc also recognizes pipe tables of the following form, as can be produced by Emacsâ orgtbl-mode: 

    
    
    | One | Two   |
    |-----+-------|
    | my  | table |
    | is  | nice  |
    

The difference is that `+` is used instead of `|`. Other orgtbl features are not supported. In particular, to get non-default column alignment, youâll need to add colons as above. 

### Metadata blocks

#### Extension: `pandoc_title_block`

If the file begins with a title block 

    
    
    % title
    % author(s) (separated by semicolons)
    % date
    

it will be parsed as bibliographic information, not regular text. (It will be used, for example, in the title of standalone LaTeX or HTML output.) The block may contain just a title, a title and an author, or all three elements. If you want to include an author but no title, or a title and a date but no author, you need a blank line: 

    
    
    %
    % Author
    
    % My title
    %
    % June 15, 2006
    

The title may occupy multiple lines, but continuation lines must begin with leading space, thus: 

    
    
    % My title
      on multiple lines
    

If a document has multiple authors, the authors may be put on separate lines with leading space, or separated by semicolons, or both. So, all of the following are equivalent: 

    
    
    % Author One
      Author Two
    
    % Author One; Author Two
    
    % Author One;
      Author Two
    

The date must fit on one line. 

All three metadata fields may contain standard inline formatting (italics, links, footnotes, etc.). 

Title blocks will always be parsed, but they will affect the output only when the `\--standalone` (`-s`) option is chosen. In HTML output, titles will appear twice: once in the document head â this is the title that will appear at the top of the window in a browser â and once at the beginning of the document body. The title in the document head can have an optional prefix attached (`\--title-prefix` or `-T` option). The title in the body appears as an H1 element with class âtitleâ, so it can be suppressed or reformatted with CSS. If a title prefix is specified with `-T` and no title block appears in the document, the title prefix will be used by itself as the HTML title. 

The man page writer extracts a title, man page section number, and other header and footer information from the title line. The title is assumed to be the first word on the title line, which may optionally end with a (single-digit) section number in parentheses. (There should be no space between the title and the parentheses.) Anything after this is assumed to be additional footer and header text. A single pipe character (`|`) should be used to separate the footer text from the header text. Thus, 

    
    
    % PANDOC(1)
    

will yield a man page with the title `PANDOC` and section 1. 

    
    
    % PANDOC(1) Pandoc User Manuals
    

will also have âPandoc User Manualsâ in the footer. 

    
    
    % PANDOC(1) Pandoc User Manuals | Version 4.0
    

will also have âVersion 4.0â in the header. 

#### Extension: `yaml_metadata_block`

A YAML metadata block is a valid YAML object, delimited by a line of three hyphens (`\---`) at the top and a line of three hyphens (`\---`) or three dots (`...`) at the bottom. A YAML metadata block may occur anywhere in the document, but if it is not at the beginning, it must be preceded by a blank line. (Note that, because of the way pandoc concatenates input files when several are provided, you may also keep the metadata in a separate YAML file and pass it to pandoc as an argument, along with your markdown files: 

    
    
    pandoc chap1.md chap2.md chap3.md metadata.yaml -s -o book.html
    

Just be sure that the YAML file begins with `\---` and ends with `\---` or `...`.) 

Metadata will be taken from the fields of the YAML object and added to any existing document metadata. Metadata can contain lists and objects (nested arbitrarily), but all string scalars will be interpreted as markdown. Fields with names ending in an underscore will be ignored by pandoc. (They may be given a role by external processors.) 

A document may contain multiple metadata blocks. The metadata fields will be combined through a _left-biased union_: if two metadata blocks attempt to set the same field, the value from the first block will be taken. 

When pandoc is used with `-t markdown` to create a markdown document, a YAML metadata block will be produced only if the `-s/--standalone` option is used. All of the metadata will appear in a single block at the beginning of the document. 

Note that YAML escaping rules must be followed. Thus, for example, if a title contains a colon, it must be quoted. The pipe character (`|`) can be used to begin an indented block that will be interpreted literally, without need for escaping. This form is necessary when the field contains blank lines: 

    
    
    ---
    title:  'This is the title: it contains a colon'
    author:
    - name: Author One
      affiliation: University of Somewhere
    - name: Author Two
      affiliation: University of Nowhere
    tags: [nothing, nothingness]
    abstract: |
      This is the abstract.
    
      It consists of two paragraphs.
    ...
    

Template variables will be set automatically from the metadata. Thus, for example, in writing HTML, the variable `abstract` will be set to the HTML equivalent of the markdown in the `abstract` field: 

    
    
    <p>This is the abstract.</p>
    <p>It consists of two paragraphs.</p>
    

Note: The `author` variable in the default templates expects a simple list or string. To use the structured authors in the example, you would need a custom template. For example: 

    
    
    $for(author)$
    $if(author.name)$
    $author.name$$if(author.affiliation)$ ($author.affiliation$)$endif$
    $else$
    $author$
    $endif$
    $endfor$
    

### Backslash escapes

#### Extension: `all_symbols_escapable`

Except inside a code block or inline code, any punctuation or space character preceded by a backslash will be treated literally, even if it would normally indicate formatting. Thus, for example, if one writes 

    
    
    *\*hello\**
    

one will get 

    
    
    <em>*hello*</em>
    

instead of 

    
    
    <strong>hello</strong>
    

This rule is easier to remember than standard markdownâs rule, which allows only the following characters to be backslash-escaped: 

    
    
    \`*_{}[]()>#+-.!
    

(However, if the `markdown_strict` format is used, the standard markdown rule will be used.) 

A backslash-escaped space is parsed as a nonbreaking space. It will appear in TeX output as `~` and in HTML and XML as `\&#160;` or `\&nbsp;`. 

A backslash-escaped newline (i.e.Â a backslash occurring at the end of a line) is parsed as a hard line break. It will appear in TeX output as `\\\` and in HTML as `<br />`. This is a nice alternative to markdownâs âinvisibleâ way of indicating hard line breaks using two trailing spaces on a line. 

Backslash escapes do not work in verbatim contexts. 

### Smart punctuation

#### Extension

If the `\--smart` option is specified, pandoc will produce typographically correct output, converting straight quotes to curly quotes, `\---` to em-dashes, `\--` to en-dashes, and `...` to ellipses. Nonbreaking spaces are inserted after certain abbreviations, such as âMr.â

Note: if your LaTeX template calls for the `[csquotes`](https://ctan.org/pkg/csquotes) package, pandoc will detect this automatically and use `\enquote{...}` for quoted text. 

### Inline formatting

#### Emphasis

To _emphasize_ some text, surround it with `*`s or `_`, like this: 

    
    
    This text is _emphasized with underscores_, and this
    is *emphasized with asterisks*.
    

Double `*` or `_` produces **strong emphasis**: 

    
    
    This is **strong emphasis** and __with underscores__.
    

A `*` or `_` character surrounded by spaces, or backslash-escaped, will not trigger emphasis: 

    
    
    This is * not emphasized *, and \*neither is this\*.
    

##### Extension: `intraword_underscores`

Because `_` is sometimes used inside words and identifiers, pandoc does not interpret a `_` surrounded by alphanumeric characters as an emphasis marker. If you want to emphasize just part of a word, use `*`: 

    
    
    feas*ible*, not feas*able*.
    

#### Strikeout

##### Extension: `strikeout`

To strikeout a section of text with a horizontal line, begin and end it with `~~`. Thus, for example, 

    
    
    This ~~is deleted text.~~
    

#### Superscripts and subscripts

##### Extension: `superscript`, `subscript`

Superscripts may be written by surrounding the superscripted text by `^` characters; subscripts may be written by surrounding the subscripted text by `~` characters. Thus, for example, 

    
    
    H~2~O is a liquid.  2^10^ is 1024.
    

If the superscripted or subscripted text contains spaces, these spaces must be escaped with backslashes. (This is to prevent accidental superscripting and subscripting through the ordinary use of `~` and `^`.) Thus, if you want the letter P with âa catâ in subscripts, use `P~a\ cat~`, not `P~a cat~`. 

#### Verbatim

To make a short span of text verbatim, put it inside backticks: 

    
    
    What is the difference between `>>=` and `>>`?
    

If the verbatim text includes a backtick, use double backticks: 

    
    
    Here is a literal backtick `` ` ``.
    

(The spaces after the opening backticks and before the closing backticks will be ignored.) 

The general rule is that a verbatim span starts with a string of consecutive backticks (optionally followed by a space) and ends with a string of the same number of backticks (optionally preceded by a space). 

Note that backslash-escapes (and other markdown constructs) do not work in verbatim contexts: 

    
    
    This is a backslash followed by an asterisk: `\*`.
    

##### Extension: `inline_code_attributes`

Attributes can be attached to verbatim text, just as with [fenced code blocks](pandocs-markdown.html#fenced-code-blocks): 

    
    
    `<$>`{.haskell}
    

#### Small caps

To write small caps, you can use an HTML span tag: 

    
    
    <span style="font-variant:small-caps;">Small caps</span>
    

(The semicolon is optional and there may be space after the colon.) This will work in all output formats that support small caps. 

### Math

#### Extension: `tex_math_dollars`

Anything between two `$` characters will be treated as TeX math. The opening `$` must have a non-space character immediately to its right, while the closing `$` must have a non-space character immediately to its left, and must not be followed immediately by a digit. Thus, `$20,000 and $30,000` wonât parse as math. If for some reason you need to enclose text in literal `$` characters, backslash-escape them and they wonât be treated as math delimiters. 

TeX math will be printed in all output formats. How it is rendered depends on the output format: 

Markdown, LaTeX, Emacs Org mode, ConTeXt 

    

It will appear verbatim between `$` characters. 

reStructuredText 

    

It will be rendered using an [interpreted text role `:math:`](http://docutils.sourceforge.net/docs/ref/rst/roles.html#math). 

AsciiDoc 

    

It will be rendered as `latexmath:[...]`. 

Texinfo 

    

It will be rendered inside a `@math` command. 

groff man 

    

It will be rendered verbatim without `$`âs. 

MediaWiki, DokuWiki 

    

It will be rendered inside `<math>` tags. 

Textile 

    

It will be rendered inside `<span class="math">` tags. 

RTF, OpenDocument, ODT 

    

It will be rendered, if possible, using unicode characters, and will otherwise appear verbatim. 

DocBook 

    

If the `\--mathml` flag is used, it will be rendered using MathML in an `inlineequation` or `informalequation` tag. Otherwise it will be rendered, if possible, using unicode characters. 

Docx 

    

It will be rendered using OMML math markup. 

FictionBook2 

    

If the `\--webtex` option is used, formulas are rendered as images using Google Charts or other compatible web service, downloaded and embedded in the e-book. Otherwise, they will appear verbatim. 

HTML, Slidy, DZSlides, S5, EPUB 

    

The way math is rendered in HTML will depend on the command-line options selected: 

  1. The default is to render TeX math as far as possible using unicode characters, as with RTF, DocBook, and OpenDocument output. Formulas are put inside a `span` with `class="math"`, so that they may be styled differently from the surrounding text if needed. 
  2. If the `\--latexmathml` option is used, TeX math will be displayed between `$` or `$$` characters and put in `<span>` tags with class `LaTeX`. The [LaTeXMathML](http://math.etsu.edu/LaTeXMathML/) script will be used to render it as formulas. (This trick does not work in all browsers, but it works in Firefox. In browsers that do not support LaTeXMathML, TeX math will appear verbatim between `$` characters.) 
  3. If the `\--jsmath` option is used, TeX math will be put inside `<span>` tags (for inline math) or `<div>` tags (for display math) with class `math`. The [jsMath](http://www.math.union.edu/~dpvc/jsmath/) script will be used to render it. 
  4. If the `\--mimetex` option is used, the [mimeTeX](http://www.forkosh.com/mimetex.html) CGI script will be called to generate images for each TeX formula. This should work in all browsers. The `\--mimetex` option takes an optional URL as argument. If no URL is specified, it will be assumed that the mimeTeX CGI script is at `/cgi-bin/mimetex.cgi`. 
  5. If the `\--gladtex` option is used, TeX formulas will be enclosed in `<eq>` tags in the HTML output. The resulting `htex` file may then be processed by [gladTeX](http://ans.hsh.no/home/mgg/gladtex/), which will produce image files for each formula and an HTML file with links to these images. So, the procedure is: 

    
        pandoc -s --gladtex myfile.txt -o myfile.htex
    gladtex -d myfile-images myfile.htex
    # produces myfile.html and images in myfile-images
    

  6. If the `\--webtex` option is used, TeX formulas will be converted to `<img>` tags that link to an external script that converts formulas to images. The formula will be URL-encoded and concatenated with the URL provided. If no URL is specified, the Google Chart API will be used (`http://chart.apis.google.com/chart?cht=tx&chl=`). 
  7. If the `\--mathjax` option is used, TeX math will be displayed between `\\(...\\)` (for inline math) or `\\[...\\]` (for display math) and put in `<span>` tags with class `math`. The [MathJax](https://www.mathjax.org) script will be used to render it as formulas. 

### Raw HTML

#### Extension: `raw_html`

Markdown allows you to insert raw HTML (or DocBook) anywhere in a document (except verbatim contexts, where `<`, `>`, and `&` are interpreted literally). (Technically this is not an extension, since standard markdown allows it, but it has been made an extension so that it can be disabled if desired.) 

The raw HTML is passed through unchanged in HTML, S5, Slidy, Slideous, DZSlides, EPUB, Markdown, and Textile output, and suppressed in other formats. 

#### Extension: `markdown_in_html_blocks`

Standard markdown allows you to include HTML âblocksâ: blocks of HTML between balanced tags that are separated from the surrounding text with blank lines, and start and end at the left margin. Within these blocks, everything is interpreted as HTML, not markdown; so (for example), `*` does not signify emphasis. 

Pandoc behaves this way when the `markdown_strict` format is used; but by default, pandoc interprets material between HTML block tags as markdown. Thus, for example, Pandoc will turn 

    
    
    <table>
    <tr>
    <td>*one*</td>
    <td>[a link](http://google.com)</td>
    </tr>
    </table>
    

into 

    
    
    <table>
    <tr>
    <td><em>one</em></td>
    <td><a href="http://google.com">a link</a></td>
    </tr>
    </table>
    

whereas `Markdown.pl` will preserve it as is. 

There is one exception to this rule: text between `<script>` and `<style>` tags is not interpreted as markdown. 

This departure from standard markdown should make it easier to mix markdown with HTML block elements. For example, one can surround a block of markdown text with `<div>` tags without preventing it from being interpreted as markdown. 

#### Extension: `native_divs`

Use native pandoc `Div` blocks for content inside `<div>` tags. For the most part this should give the same output as `markdown_in_html_blocks`, but it makes it easier to write pandoc filters to manipulate groups of blocks. 

#### Extension: `native_spans`

Use native pandoc `Span` blocks for content inside `<span>` tags. For the most part this should give the same output as `raw_html`, but it makes it easier to write pandoc filters to manipulate groups of inlines. 

### Raw TeX

#### Extension: `raw_tex`

In addition to raw HTML, pandoc allows raw LaTeX, TeX, and ConTeXt to be included in a document. Inline TeX commands will be preserved and passed unchanged to the LaTeX and ConTeXt writers. Thus, for example, you can use LaTeX to include BibTeX citations: 

    
    
    This result was proved in \cite{jones.1967}.
    

Note that in LaTeX environments, like 

    
    
    \begin{tabular}{|l|l|}\hline
    Age & Frequency \\ \hline
    18--25  & 15 \\
    26--35  & 33 \\
    36--45  & 22 \\ \hline
    \end{tabular}
    

the material between the begin and end tags will be interpreted as raw LaTeX, not as markdown. 

Inline LaTeX is ignored in output formats other than Markdown, LaTeX, and ConTeXt. 

### LaTeX macros

#### Extension: `latex_macros`

For output formats other than LaTeX, pandoc will parse LaTeX `\newcommand` and `\renewcommand` definitions and apply the resulting macros to all LaTeX math. So, for example, the following will work in all output formats, not just LaTeX: 

â¨_a_,â_b_,â_c_â© 

In LaTeX output, the `\newcommand` definition will simply be passed unchanged to the output. 

### Links

Markdown allows links to be specified in several ways. 

#### Automatic links

If you enclose a URL or email address in pointy brackets, it will become a link: 

    
    
    <http://google.com>
    <sam@green.eggs.ham>
    

#### Inline links

An inline link consists of the link text in square brackets, followed by the URL in parentheses. (Optionally, the URL can be followed by a link title, in quotes.) 

    
    
    This is an [inline link](/url), and here's [one with
    a title](http://fsf.org "click here for a good time!").
    

There can be no space between the bracketed part and the parenthesized part. The link text can contain formatting (such as emphasis), but the title cannot. 

Email addresses in inline links are not autodetected, so they have to be prefixed with `mailto`: 

    
    
    [Write me!](mailto:sam@green.eggs.ham)
    

#### Reference links

An _explicit_ reference link has two parts, the link itself and the link definition, which may occur elsewhere in the document (either before or after the link). 

The link consists of link text in square brackets, followed by a label in square brackets. (There can be space between the two.) The link definition consists of the bracketed label, followed by a colon and a space, followed by the URL, and optionally (after a space) a link title either in quotes or in parentheses. The label must not be parseable as a citation (assuming the `citations` extension is enabled): citations take precedence over link labels. 

Here are some examples: 

    
    
    [my label 1]: /foo/bar.html  "My title, optional"
    [my label 2]: /foo
    [my label 3]: http://fsf.org (The free software foundation)
    [my label 4]: /bar#special  'A title in single quotes'
    

The URL may optionally be surrounded by angle brackets: 

    
    
    [my label 5]: <http://foo.bar.baz>
    

The title may go on the next line: 

    
    
    [my label 3]: http://fsf.org
      "The free software foundation"
    

Note that link labels are not case sensitive. So, this will work: 

    
    
    Here is [my link][FOO]
    
    [Foo]: /bar/baz
    

In an _implicit_ reference link, the second pair of brackets is empty: 

    
    
    See [my website][].
    
    [my website]: http://foo.bar.baz
    

Note: In `Markdown.pl` and most other markdown implementations, reference link definitions cannot occur in nested constructions such as list items or block quotes. Pandoc lifts this arbitrary seeming restriction. So the following is fine in pandoc, though not in most other implementations: 

    
    
    > My block [quote].
    >
    > [quote]: /foo
    

##### Extension: `shortcut_reference_links`

In a _shortcut_ reference link, the second pair of brackets may be omitted entirely: 

    
    
    See [my website].
    
    [my website]: http://foo.bar.baz
    

#### Internal links

To link to another section of the same document, use the automatically generated identifier (see [Header identifiers](pandocs-markdown.html#header-identifiers)). For example: 

    
    
    See the [Introduction](#introduction).
    

or 

    
    
    See the [Introduction].
    
    [Introduction]: #introduction
    

Internal links are currently supported for HTML formats (including HTML slide shows and EPUB), LaTeX, and ConTeXt. 

### Images

A link immediately preceded by a `!` will be treated as an image. The link text will be used as the imageâs alt text: 

    
    
    ![la lune](lalune.jpg "Voyage to the moon")
    
    ![movie reel]
    
    [movie reel]: movie.gif
    

#### Extension: `implicit_figures`

An image occurring by itself in a paragraph will be rendered as a figure with a caption.[4] (In LaTeX, a figure environment will be used; in HTML, the image will be placed in a `div` with class `figure`, together with a caption in a `p` with class `caption`.) The imageâs alt text will be used as the caption. 

    
    
    ![This is the caption](/url/of/image.png)
    

If you just want a regular inline image, just make sure it is not the only thing in the paragraph. One way to do this is to insert a nonbreaking space after the image: 

    
    
    ![This image won't be a figure](/url/of/image.png)\ 
    

### Footnotes

#### Extension: `footnotes`

Pandocâs markdown allows footnotes, using the following syntax: 

    
    
    Here is a footnote reference,[^1] and another.[^longnote]
    
    [^1]: Here is the footnote.
    
    [^longnote]: Here's one with multiple blocks.
    
        Subsequent paragraphs are indented to show that they
    belong to the previous footnote.
    
            { some.code }
    
        The whole paragraph can be indented, or just the first
        line.  In this way, multi-paragraph footnotes work like
        multi-paragraph list items.
    
    This paragraph won't be part of the note, because it
    isn't indented.
    

The identifiers in footnote references may not contain spaces, tabs, or newlines. These identifiers are used only to correlate the footnote reference with the note itself; in the output, footnotes will be numbered sequentially. 

The footnotes themselves need not be placed at the end of the document. They may appear anywhere except inside other block elements (lists, block quotes, tables, etc.). 

#### Extension: `inline_notes`

Inline footnotes are also allowed (though, unlike regular notes, they cannot contain multiple paragraphs). The syntax is as follows: 

    
    
    Here is an inline note.^[Inlines notes are easier to write, since
    you don't have to pick an identifier and move down to type the
    note.]
    

Inline and regular footnotes may be mixed freely. 

### Citations

#### Extension: `citations`

Using an external filter, `pandoc-citeproc`, pandoc can automatically generate citations and a bibliography in a number of styles. Basic usage is 

    
    
    pandoc --filter pandoc-citeproc myinput.txt
    

In order to use this feature, you will need to specify a bibliography file using the `bibliography` metadata field in a YAML metadata section, or `\--bibliography` command line argument. You can supply multiple `\--bibliography` arguments or set `bibliography` metadata field to YAML array, if you want to use multiple bibliography files. The bibliography may have any of these formats: 

Format  File extension 

BibLaTeX 

.bib 

BibTeX 

.bibtex 

Copac 

.copac 

CSL JSON 

.json 

CSL YAML 

.yaml 

EndNote 

.enl 

EndNote XML 

.xml 

ISI 

.wos 

MEDLINE 

.medline 

MODS 

.mods 

RIS 

.ris 

Note that `.bib` can be used with both BibTeX and BibLaTeX files; use `.bibtex` to force BibTeX. 

Note that `pandoc-citeproc --bib2json` and `pandoc-citeproc --bib2yaml` can produce `.json` and `.yaml` files from any of the supported formats. 

In-field markup: In BibTeX and BibLaTeX databases, pandoc-citeproc parses a subset of LaTeX markup; in CSL YAML databases, pandoc markdown; and in CSL JSON databases, an [HTML-like markup](http://docs.citationstyles.org/en/1.0/release-notes.html#rich-text-markup-within-fields): 

`<i>...</i>`

    

italics 

`<b>...</b>`

    

bold 

`<span style="font-variant:small-caps;">...</span>` or `<sc>...</sc>`

    

small capitals 

`<sub>...</sub>`

    

subscript 

`<sup>...</sup>`

    

superscript 

`<span class="nocase">...</span>`

    

prevent a phrase from being capitalized as title case 

`pandoc-citeproc -j` and `-y` interconvert the CSL JSON and CSL YAML formats as far as possible. 

As an alternative to specifying a bibliography file, you can include the citation data directly in the `references` field of the documentâs YAML metadata. The field should contain an array of YAML-encoded references, for example: 

    
    
    ---
    references:
    - type: article-journal
      id: WatsonCrick1953
      author:
      - family: Watson
        given: J. D.
      - family: Crick
        given: F. H. C.
      issued:
        date-parts:
        - - 1953
          - 4
          - 25
      title: 'Molecular structure of nucleic acids: a structure for deoxyribose
        nucleic acid'
      title-short: Molecular structure of nucleic acids
      container-title: Nature
      volume: 171
      issue: 4356
      page: 737-738
      DOI: 10.1038/171737a0
      URL: http://www.nature.com/nature/journal/v171/n4356/abs/171737a0.html
      language: en-GB
    ...
    

(`pandoc-citeproc --bib2yaml` can produce these from a bibliography file in one of the supported formats.) 

Citations and references can be formatted using any style supported by the [Citation Style Language](http://citationstyles.org), listed in the [Zotero Style Repository](https://www.zotero.org/styles). These files are specified using the `\--csl` option or the `csl` metadata field. By default, `pandoc-citeproc` will use the [Chicago Manual of Style](http://chicagomanualofstyle.org) author-date format. The CSL project provides further information on [finding and editing styles](http://citationstyles.org/styles/). 

Citations go inside square brackets and are separated by semicolons. Each citation must have a key, composed of â@â \+ the citation identifier from the database, and may optionally have a prefix, a locator, and a suffix. The citation key must begin with a letter, digit, or `_`, and may contain alphanumerics, `_`, and internal punctuation characters (`:.#$%&-+?<>~/`). Here are some examples: 

    
    
    Blah blah [see @doe99, pp. 33-35; also @smith04, chap. 1].
    
    Blah blah [@doe99, pp. 33-35, 38-39 and *passim*].
    
    Blah blah [@smith04; @doe99].
    

`pandoc-citeproc` detects locator terms in the [CSL locale files](https://github.com/citation-style-language/locales). Either abbreviated or unabbreviated forms are accepted. In the `en-US` locale, locator terms can be written in either singular or plural forms, as `book`, `bk.`/`bks.`; `chapter`, `chap.`/`chaps.`; `column`, `col.`/`cols.`; `figure`, `fig.`/`figs.`; `folio`, `fol.`/`fols.`; `number`, `no.`/`nos.`; `line`, `l.`/`ll.`; `note`, `n.`/`nn.`; `opus`, `op.`/`opp.`; `page`, `p.`/`pp.`; `paragraph`, `para.`/`paras.`; `part`, `pt.`/`pts.`; `section`, `sec.`/`secs.`; `sub verbo`, `s.v.`/`s.vv.`; `verse`, `v.`/`vv.`; `volume`, `vol.`/`vols.`; `Â¶`/`Â¶Â¶`; `Â§`/`Â§Â§`. If no locator term is used, âpageâ is assumed. 

A minus sign (`-`) before the `@` will suppress mention of the author in the citation. This can be useful when the author is already mentioned in the text: 

    
    
    Smith says blah [-@smith04].
    

You can also write an in-text citation, as follows: 

    
    
    @smith04 says blah.
    
    @smith04 [p. 33] says blah.
    

If the style calls for a list of works cited, it will be placed at the end of the document. Normally, you will want to end your document with an appropriate header: 

    
    
    last paragraph...
    
    # References
    

The bibliography will be inserted after this header. Note that the `unnumbered` class will be added to this header, so that the section will not be numbered. 

If you want to include items in the bibliography without actually citing them in the body text, you can define a dummy `nocite` metadata field and put the citations there: 

    
    
    ---
    nocite: |
      @item1, @item2
    ...
    
    @item3
    

In this example, the document will contain a citation for `item3` only, but the bibliography will contain entries for `item1`, `item2`, and `item3`. 

For LaTeX or PDF output, you can also use `[natbib`](https://ctan.org/pkg/natbib) or `[biblatex`](https://ctan.org/pkg/biblatex) to render bibliography. In order to do so, specify bibliography files as outlined above, and add `\--natbib` or `\--biblatex` argument to `pandoc` invocation. Bear in mind that bibliography files have to be in respective format (either BibTeX or BibLaTeX). 

### Non-pandoc extensions

The following markdown syntax extensions are not enabled by default in pandoc, but may be enabled by adding `+EXTENSION` to the format name, where `EXTENSION` is the name of the extension. Thus, for example, `markdown+hard_line_breaks` is markdown with hard line breaks. 

#### Extension: `lists_without_preceding_blankline`

Allow a list to occur right after a paragraph, with no intervening blank space. 

#### Extension: `hard_line_breaks`

Causes all newlines within a paragraph to be interpreted as hard line breaks instead of spaces. 

#### Extension: `ignore_line_breaks`

Causes newlines within a paragraph to be ignored, rather than being treated as spaces or as hard line breaks. This option is intended for use with East Asian languages where spaces are not used between words, but text is divided into lines for readability. 

#### Extension: `tex_math_single_backslash`

Causes anything between `\\(` and `\\)` to be interpreted as inline TeX math, and anything between `\\[` and `\\]` to be interpreted as display TeX math. Note: a drawback of this extension is that it precludes escaping `(` and `[`. 

#### Extension: `tex_math_double_backslash`

Causes anything between `\\\\(` and `\\\\)` to be interpreted as inline TeX math, and anything between `\\\\[` and `\\\\]` to be interpreted as display TeX math. 

#### Extension: `markdown_attribute`

By default, pandoc interprets material inside block-level tags as markdown. This extension changes the behavior so that markdown is only parsed inside block-level tags if the tags have the attribute `markdown=1`. 

#### Extension: `mmd_title_block`

Enables a [MultiMarkdown](http://fletcherpenney.net/multimarkdown/) style title block at the top of the document, for example: 

    
    
    Title:   My title
    Author:  John Doe
    Date:    September 1, 2008
    Comment: This is a sample mmd title block, with
             a field spanning multiple lines.
    

See the MultiMarkdown documentation for details. If `pandoc_title_block` or `yaml_metadata_block` is enabled, it will take precedence over `mmd_title_block`. 

#### Extension: `abbreviations`

Parses PHP Markdown Extra abbreviation keys, like 

    
    
    *[HTML]: Hypertext Markup Language
    

Note that the pandoc document model does not support abbreviations, so if this extension is enabled, abbreviation keys are simply skipped (as opposed to being parsed as paragraphs). 

#### Extension: `autolink_bare_uris`

Makes all absolute URIs into links, even when not surrounded by pointy braces `<...>`. 

#### Extension: `ascii_identifiers`

Causes the identifiers produced by `auto_identifiers` to be pure ASCII. Accents are stripped off of accented latin letters, and non-latin letters are omitted. 

#### Extension: `link_attributes`

Parses multimarkdown style key-value attributes on link and image references. Note that pandocâs internal document model provides nowhere to put these, so they are presently just ignored. 

#### Extension: `mmd_header_identifiers`

Parses multimarkdown style header identifiers (in square brackets, after the header but before any trailing `#`s in an ATX header). 

#### Extension: `compact_definition_lists`

Activates the definition list syntax of pandoc 1.12.x and earlier. This syntax differs from the one described above under [Definition lists](pandocs-markdown.html#definition-lists) in several respects: 

  * No blank line is required between consecutive items of the definition list. 
  * To get a âtightâ or âcompactâ list, omit space between consecutive items; the space between a term and its definition does not affect anything. 
  * Lazy wrapping of paragraphs is not allowed: the entire definition must be indented four spaces.[5]

### Markdown variants

In addition to pandocâs extended markdown, the following markdown variants are supported: 

`markdown_phpextra` (PHP Markdown Extra) 

    

`footnotes`, `pipe_tables`, `raw_html`, `markdown_attribute`, `fenced_code_blocks`, `definition_lists`, `intraword_underscores`, `header_attributes`, `abbreviations`, `shortcut_reference_links`. 

`markdown_github` (GitHub-Flavored Markdown) 

    

`pipe_tables`, `raw_html`, `tex_math_single_backslash`, `fenced_code_blocks`, `auto_identifiers`, `ascii_identifiers`, `backtick_code_blocks`, `autolink_bare_uris`, `intraword_underscores`, `strikeout`, `hard_line_breaks`, `shortcut_reference_links`. 

`markdown_mmd` (MultiMarkdown) 

    

`pipe_tables` `raw_html`, `markdown_attribute`, `link_attributes`, `raw_tex`, `tex_math_double_backslash`, `intraword_underscores`, `mmd_title_block`, `footnotes`, `definition_lists`, `all_symbols_escapable`, `implicit_header_references`, `auto_identifiers`, `mmd_header_identifiers`, `shortcut_reference_links`. 

`markdown_strict` (Markdown.pl) 

    

`raw_html`

### Extensions with formats other than markdown

Some of the extensions discussed above can be used with formats other than markdown: 

  * `auto_identifiers` can be used with `latex`, `rst`, `mediawiki`, and `textile` input (and is used by default). 
  * `tex_math_dollars`, `tex_math_single_backslash`, and `tex_math_double_backslash` can be used with `html` input. (This is handy for reading web pages formatted using MathJax, for example.) 

  

* * *

[1]  The point of this rule is to ensure that normal paragraphs starting with peopleâs initials, like 

    
    
    B. Russell was an English philosopher.
    

do not get treated as list items. 

This rule will not prevent 

    
    
    (C) 2007 Joe Smith
    

from being interpreted as a list item. In this case, a backslash escape can be used: 

    
    
    (C\) 2007 Joe Smith
    

[2]  I have been influenced by the suggestions of [David Wheeler](http://www.justatheory.com/computers/markup/modest-markdown-proposal.html). 

[3]  This scheme is due to Michel Fortin, who proposed it on the [Markdown discussion list](http://six.pairlist.net/pipermail/markdown-discuss/2005-March/001097.html). 

[4]  This feature is not yet implemented for RTF, OpenDocument, or ODT. In those formats, youâll just get an image in a paragraph by itself, with no caption. 

[5]  To see why laziness is incompatible with relaxing the requirement of a blank line between items, consider the following example: 

    
    
    bar
    :    definition
    foo
    :    definition
    

Is this a single list item with two definitions of âbar,â the first of which is lazily wrapped, or two list items? To remove the ambiguity we must either disallow lazy wrapping or require a blank line between list items. 

* * *
