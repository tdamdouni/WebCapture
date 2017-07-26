# Markdown Cheatsheet

_Captured: 2016-06-11 at 10:40 from [www.keycdn.com](https://www.keycdn.com/support/markdown-cheatsheet/?utm_content=buffer14b6c&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

![markdown cheatsheet](https://cdn.keycdn.com/support/wp-content/uploads/2016/03/markdown-cheatsheet.png)

## What Is Markdown?

Markdown is a markup language used to convert plain text format syntax to various other formats including HTML. This format is often used in readme documentation files (using the .md extension) or even online discussion forums. The primary goal of markdown is to allow the text to be as readable as possible in plain-text syntax without the addition of tags and other formatting tags.

The following markdown cheatsheet provides an overview of the formatting rules available for writing plain text with markdown syntax.

## Markdown Cheatsheet Index:

  1. [Headers](https://www.keycdn.com/support/markdown-cheatsheet/?utm_content=buffer14b6c&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)
  2. [Images](https://www.keycdn.com/support/markdown-cheatsheet/?utm_content=buffer14b6c&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)

## Headers

Markdown header sizes are defined by the number of # characters placed before the text. Therefore, for an H1 header this corresponds to # while H6 corresponds to ######.

**Markdown Syntax**
    
    
    # H1
    ## H2
    ### H3
    #### H4
    ##### H5
    ###### H6

**HTML Equivalent**
    
    
    <h1>H1</h1>
    <h2>H2</h2>
    <h3>H3</h3>
    <h4>H4</h4>
    <h5>H5</h5>
    <h6>H6</h6>

**Browser View**

# H1

## H2

### H3

### H4

##### H5

H6

## Italics, Bold, and Strikethrough

There are a couple of different ways to achieve both italics and bold text styles in markdown.

**Markdown Syntax**

  * To style text with **italics**, this can be achieved either by using `*sometext*` or `_sometext_`.
  * To style text with **bold**, this can be achieved either by using `**sometext**` or `__sometext__`.
  * To use a **strikethrough**, this can be achieved by using two tildes on either site of the text ~~sometext~~.

**HTML Equivalent**
    
    
    ## Italics
    <em>sometext</em>
    
    ## Bold
    <strong>sometext</strong>
    
    ## Strikethrough
    <del>sometext</del>

**Browser View**

  * _sometext_
  * **sometext**
  * sometext

## Lists

Creating lists in markdown is very easy. The following will go through the creation of both ordered and unordered lists.

### Ordered List

**Markdown Syntax**
    
    
    1. First ordered list item
    2. Second ordered list item
    3. Third ordered list item

**HTML Equivalent**
    
    
    <ol>
     <li>First ordered list item</li>
     <li>Second ordered list item</li>
     <li>Third ordered list item</li>
    </ol>

**Browser View**

  1. First ordered list item
  2. Second ordered list item
  3. Third ordered list item

### Unordered List

There are a few bullet point options for unordered lists when using markdown. The following characters are all valid bullet point options: *, -, +.

**Markdown Syntax**
    
    
    + First unordered list item
    + Second unordered list item
        - First sub-unordered list item
        - Second sub-unordered list item
    + Third unordered list item

**HTML Equivalent**
    
    
    <ul>
      <li>First unordered list item</li>
      <li>Second unordered list item
        <ul>
          <li>First sub-unordered list item</li>
          <li>Second sub-unordered list item</li>
        </ul>  
      </li>
      <li>Third unordered list item</li>
    </ul>

**Browser View**

  * First unordered list item
  * Second unordered list item 
    * First sub-unordered list item
    * Second sub-unordered list item
  * Third unordered list item

## Code

Inline code as well as code blocks can be represented using the following methods.

**Markdown Syntax**

  * **Inline code** is defined by using back ticks such as `code example`.
  * For **multiple lines of code**, three back ticks can be used. 
    
        ```
    code example 1
    code example 2
    code example 3
    ```

  * Code can also be **indented** by four spaces. 
    
            code example 1
        code example 2
        code example 3

**HTML Equivalent**

  * Inline code 
    
        <code>code example</code>

  * Code block 
    
        <pre>
    code example 1
    code example 2
    code example 3
    </pre>

**Browser View**

  * Inline code: `code example`
  * Code block 
    
        code example 1
    code example 2
    code example 3

## Links

There are a few options available when linking in markdown. However, a basic link accompanied by a title can be defined with the following.

**Markdown Syntax**
    
    
    [KeyCDN](https://www.keycdn.com/ "KeyCDN Homepage")

**HTML Equivalent**
    
    
    <a href="https://www.keycdn.com/" title="KeyCDN Homepage">KeyCDN</a>

**Browser View**

[KeyCDN](https://www.keycdn.com/)

## Images

The markdown syntax for images is quite similar to that of links with the difference being that images begin with a exclamation point.

**Markdown Syntax**
    
    
    ![logo](https://cdn.keycdn.com/support/wp-content/uploads/2015/11/keycdn-logo-sm.svg "KeyCDN logo")

**HTML Equivalent**
    
    
    <img src="https://cdn.keycdn.com/support/wp-content/uploads/2015/11/keycdn-logo-sm.svg" alt="logo" title="KeyCDN logo">

**Browser View**

## Tables

Tables are created with markdown syntax by using pipes and dashes. Dashes separate the header section from the other cells and pipes separate the columns.

**Markdown Syntax**
    
    
    | Header 1 | Header 2 | Header 3 |
    | -------- | -------- | ---------|
    | Cell 1A | Cell 1B | Cell 1C |
    | Cell 2A | Cell 2B | Cell 2C |

**HTML Equivalent**
    
    
    <table>
     <tr>
     <th>Header 1</th>
     <th>Header 2</th>
     <th>Header 3</th>
     </tr>
     <tr>
     <td>Cell 1A</td>
     <td>Cell 1B</td>
     <td>Cell 1C</td>
     </tr>
     <tr>
     <td>Cell 2A</td>
     <td>Cell 2B</td>
     <td>Cell 2C</td>
     </tr>
    </table>

**Browser View**

Header 1 Header 2 Header 3

Cell 1A
Cell 1B
Cell 1C

Cell 2A
Cell 2B
Cell 2C

This markdown cheatsheet aims to give a broad overview of what's possible with markdown formatting. If you're creating a markdown file and want to see the HTML preview in real-time, use a tool such as [dillinger.io](http://dillinger.io/) which allows you to preview your changes and export the file in various formats when done editing.
