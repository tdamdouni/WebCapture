# Little Stuff about Markdown I Always Forget and have to Google

_Captured: 2017-04-11 at 10:58 from [css-tricks.com](https://css-tricks.com/little-stuff-markdown-always-forget-google/)_

This is mostly for me. These are the little things that sometimes confuse me about Markdown and I find myself having to search the web for. So I'll write them down. Blogging as memory extension.

Know that your mileage may vary on this stuff, as there are [many varietals of Markdown](https://css-tricks.com/choosing-right-markdown-parser/).

There is no concept of a `<div>` in Markdown syntax (or most other structural HTML elements), except that Markdown supports HTML so you can just use a `<div>` if you want to. But as soon as you do, nothing nested inside of it can be Markdown.
    
    
    ### Header
    
    <div class="special-class">
    1. Nope
    1. Not 
    1. Happening
    </div>

Except it can! In many (most?) varietals of Markdown, you can put `<div markdown="1">` on the element and it will allow Markdown inside of it.
    
    
    ### Header
    
    <div class="special-class" markdown="1">
    1. All
    1. Fixed 
    1. Up
    </div>

If a list item need multiple paragraphs in it, you can't just break multiple lines and keep going. The next paragraph needs to be indented for it to be considered part of the same list item. Otherwise the list ends and new one starts.
    
    
    1. one paragraph
    
        more for 1st list item :)
    
    1. another paragraph

Blockquotes are similar:
    
    
    > First bit.
    > Second bit.

There will be no line break there. Those two bits will be inside the same `<p>` inside the `<blockquote>`. To make them multiple paragraphs, you'll need a blank line in between.
    
    
    > First bit.
    
    > Second bit.

If you wanted them to be entirely separate `<blockquote>`s, without any other text in between, I'm not sure what'd you do.

Certain characters have meaning in markdown, like how `*asterisks*` make text italic. But what if you want to actually display an asterisk? You escape it with a backslash, like `\\*`.

You can even escape the backslash itself, meaning `\\\` is `\`.

Markdown supports HTML, so if you need any special attributes on elements, you can just use HTML. But it's nice to not have to.

Different varietals of Markdown handle it in different ways.

A somewhat common way is to allow them on headers like this:
    
    
    ### Custom IDs {#custom-id}

Some varietals simply add an ID on all headings for you automatically.

This is also [doable client side](https://blog.codepen.io/2016/11/17/anchor-links-post-headers/).

It's the same as the link syntax `[link text](url)` except it starts with a bang.
    
    
    ![alt text](http://example.com/image.jpg)

Slightly trickier still is nesting it to be a link:
    
    
    [![alt text](image.jpg)](https://css-tricks.com)

The language comes right after the first set of backticks.
    
    
    ```css
    body {
      background: red;
    }
    ```

You basically draw them like ASCII art. Note the dashes to denote the header row, and the colons for alignment:
    
    
    | header | header | header |
    |--------|:------:|-------:|
    | a      |    b   |      c |
    | 1      |    2   |      3 |
    | foo    |   bar  |    baz |

![](https://cdn.css-tricks.com/wp-content/uploads/2017/04/table-generator.png)

Here's quite [a thread of what other folks forget](https://twitter.com/chriscoyier/status/849616181853995010).
