# Simplify Writing with Markdown

_Captured: 2015-11-20 at 12:37 from [techstreams.github.io](http://techstreams.github.io/2015/09/21/simplify-writing-with-markdown/)_

It occurred to me recently that I use **_markdown_** to simplify most of my writing/publishing workflows, so I thought it would be a good idea to share a quick tutorial for others who might be interested.

![Markdown](http://techstreams.github.io/images/2015-09-21-markdown.png)

**_Before I begin though, a quick introduction..._**

### What is markdown?

Markdown converts easily to formatted [HTML](https://en.wikipedia.org/wiki/HTML) which makes it a great tool for writing and publishing.

In addition to the original version, there are several markdown variations. Examples include:

  * [MultiMarkdown (MMD)](https://github.com/fletcher/MultiMarkdown/wiki/MultiMarkdown-Syntax-Guide)
  * [Github Flavored Markdown (GFM)](https://help.github.com/articles/github-flavored-markdown/)

### What are the benefits of markdown?

  * It's **_easy_** to learn
  * **_Significantly speeds up_** writing/publishing workflows
  * Can be created, edited and stored on a variety of platforms and devices because it's **_just plain text_**
  * Is a **_supported format_** on an increasing number of writing tools and services 

### Markdown workflow examples?

I use markdown to:

  * Write all posts for this blog
  * Create, send and reuse emails from [Google Docs](https://www.google.com/docs/about/) with my [TSMarkMail Google Doc Add-on](http://techstreams.github.io/2015/03/27/tsmarkmail-overview/)
  * Initiate many of my [Drafts app workflows](http://techstreams.github.io/2015/09/03/ios-automation-with-drafts/)
  * Initiate many of my [Workflow app workflows](http://techstreams.github.io/2015/04/06/ios-automation-with-workflow/)
  * Write documentation for my [Github projects](https://github.com/techstreams)
  * Write ebooks and documentation with [Gitbook](https://www.gitbook.com/)

_I plan to share some of my favorite writing/publishing workflow details in upcoming posts._

**_Now for the tutorial..._**

In the interest of time, I'll only be highlighting markdown elements I use most frequently:

  * Paragraph 
  * Text Emphasis
  * Headings
  * Blockquote
  * List
  * Horizontal Rule
  * Link
  * Image
  * Table 
  * Code

## Paragraph

  * Begin markdown paragraph text at the left margin.

  * Separate paragraphs from other markdown elements _(including other paragraphs)_ with one or more blank lines.

  * _Lines of text within a paragraph are continuous. To separate lines within the same paragraph, add **two space characters** to the end of the previous line._

**Paragraph Markdown Example:**
    
    
    This is a paragraph.
    
    Here is another paragraph.
    

**Converts to:**

This is a paragraph.

Here is another paragraph.

## Text Emphasis

  * Markdown text emphasis can be inserted _inline_ and does not need to begin at the left margin.

  * Create emphasis by surrounding text with special symbols.

  * To display text as **Bold**, surround text in:

    * two consecutive asterisks `**`
    * two consecutive underscores `__`
  * To display text as _Italics_, surround text in:

    * a single asterisk `*`
    * a single underscore `_`
  * To display text in **_Bold Italics_**, surround text in:

    * three consecutive asterisks `***`
    * three consecutive underscores `___`
  * To display text as Strikethrough, surround text in:

    * two consecutive tildas `~~`

**Text Emphasis Markdown Example:**
    
    
    Here is **Bold Text**. 
    
    Here is *Italic Text*. 
    
    Here is ***Bold Italic Text***.  
    
    Here is ~~Strikethrough Text~~. 
    

**Converts to:**

Here is **Bold Text**.

Here is _Italic Text_.

Here is **_Bold Italic Text_**.

Here is Strikethrough Text.

## Headings

  * There are **six levels** of headings possible in markdown. 

  * Begin markdown headings at the left margin.

  * Create a heading by entering the `#` symbol followed by a space character and the heading text. 

  * Enter the number of `#` symbols per heading level.

**Heading Markdown Example:**
    
    
    # I Am a Level 1 Heading
    
    ## I Am a Level 2 Heading
    
    ### I Am a Level 3 Heading
    
    #### I Am a Level 4 Heading
    
    ##### I Am a Level 5 Heading
    
    ###### I Am a Level 6 Heading
    

**Converts to:**

# I Am a Level 1 Heading

## I Am a Level 2 Heading

### I Am a Level 3 Heading

#### I Am a Level 4 Heading

## Blockquote

  * Begin markdown blockquotes at the left margin.

  * Create a blockquote by entering a `>` symbol followed by a space character and the blockquote text. 

  * Blockquotes can also be nested by entering consecutive `>` symbols.

## List

Markdown supplies both **_Ordered_** and **_Unordered_** lists.

  * **Ordered List:**

    * Begin a markdown list item at the left margin.
    * Enter the list item number followed by a `.` symbol followed by a space character and the item text. 
    * _Each list item can also be numbered with `1.`and the correct list number will be displayed._
    * Lists can be **_nested_** by including a **_two space character indention_**.
  * **Unordered List:**

    * Begin a markdown list item at the left margin.
    * Type a `*`, `-` or `+` symbol followed by a space character and the item text. 
    * Lists can be **_nested_** by including a **_two space character indention_**.

## Horizontal Rule

  * Begin a markdown horizontal rule at the left margin.

  * Create a horizontal rule (line break) by entering:

    * three consecutive underscores `___`
    * three consecutive dashes `\---`
    * three consecutive asterisks `***`

## Link

  * Markdown links can be inserted _inline_ and do not need to begin at the left margin.

  * Add links by entering **_link text_** enclosed in `[]` symbols followed by the **_full link url_** enclosed in `()` symbols.

    * Example: `[Link Text](http://someurl)`
    * Example _with link title_: `[Link Text](http://someurl "Link Title")`

## Image

  * Markdown images can be inserted _inline_ and do not need to begin at the left margin.

  * Add images by entering a `!` symbol followed by the **_image alt text_** enclosed in `[]` symbols followed by the **_full url of the image_** enclosed in `()` symbols.

    * Example: `![Image Alt Text](http://someimageurl)`
![TSMarkMail](https://camo.githubusercontent.com/fe25f153e40d825f9c888cfd91e814190d06d660/687474703a2f2f7465636873747265616d732e6769746875622e696f2f74736d61726b6d61696c2f696d616765732f74732e706e67)

## Table

  * Begin a markdown table at the left margin.

  * Tables can be created by adding pipe dividers (`|` symbol) between each **_table cell_**.

    * **Table Header vs Table Body** \- separate the table _header row_ from _table body rows_ by adding a row of cells containing dashes
    * **Text Alignment Within Table Column** \- include colon `:` symbols within the dash row to define _left-aligned, right-aligned, or center-aligned_ text in table body cells
    * **Inline Markdown** \- table cell text can include _inline markdown_ such as Links and Text Empahsis _(see corresponding elements above)_

Column 1 Column 2

row 1
some text

row 2
some more text

row 3
some additional text

Left Align Center Align Right Align

row 1
some text
$600

row 2
some more text
$500

row 3
some additional text
$400

Left Align Center Align Right Align

row 1
**some bold text**
$600

row 2
_some italic text_
$500

row 3
some strikethrough text
$400

## Code

  * Code snippets can be included in markdown. 
    * **Inline Code** \- wrap inline code with backtick ``` symbols
    * **Indented Code** \- indent code blocks with **_4 space characters_**
    * **Fenced Code Blocks** \- wrap code with backtick ````` symbols to create a **_multi-line block of code_**
