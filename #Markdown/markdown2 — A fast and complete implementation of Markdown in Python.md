# markdown2 — A fast and complete implementation of Markdown in Python

_Captured: 2015-06-09 at 21:59 from [omz-software.com](http://omz-software.com/editorial/docs/ios/markdown2.html)_

Note

The documentation for this module is an excerpt of the documentation available on the [markdown2 project page on GitHub](https://github.com/trentm/python-markdown2). Minor edits have been made to make the documentation fit on one page and to remove passages that are not relevant on iOS. Also, only a summary of available extras is included here, for more information on individual extras, please refer to the project page wiki.
    
    
    >>> import markdown2
    >>> markdown2.markdown("*boo!*")  # or use `html = markdown_path(PATH)`
    u'<p><em>boo!</em></p>\n'
    
    >>> markdowner = Markdown()
    >>> markdowner.convert("*boo!*")
    u'<p><em>boo!</em></p>\n'
    >>> markdowner.convert("**boom!**")
    u'<p><strong>boom!</strong></p>\n'
    

## Extras

By default [markdown2](http://omz-software.com/editorial/docs/ios/markdown2.html)'s processing attempts to produce output exactly as defined by <http://daringfireball.net/projects/markdown/syntax> - the "Markdown core." However, a few optional extras are also provided.

### Implemented Extras

  * **code-friendly:** Disable _ and __ for em and strong.
  * **code-color:** (**DEPRECATED** Use fenced-code-blocks extra instead.) Pygments-based syntax coloring of <code> sections.
  * **cuddled-lists:** Allow lists to be cuddled to the preceding paragraph.
  * **fenced-code-blocks:** Allows a code block to not have to be indented by fencing it with '```' on a line before and after. Based on <http://github.github.com/github-flavored-markdown/> with support for syntax highlighting.
  * **footnotes:** support footnotes as in use on daringfireball.net and implemented in other Markdown processors (tho not in Markdown.pl v1.0.1).
  * **header-ids:** Adds "id" attributes to headers. The id value is a slug of the header text.
  * **html-classes:** Takes a dict mapping html tag names (lowercase) to a string to use for a "class" tag attribute. Currently only supports "pre" and "code" tags. Add an issue if you require this for other tags.
  * **link-patterns:** Auto-link given regex patterns in text (e.g. bug number references, revision number references).
  * **markdown-in-html:** Allow the use of markdown="1" in a block HTML tag to have markdown processing be done on its contents. Similar to <http://michelf.com/projects/php-markdown/extra/#markdown-attr> but with some limitations.
  * **metadata:** Extract metadata from a leading '--'-fenced block.
  * **nofollow:** Add rel="nofollow" to add <a> tags with an href. See <http://en.wikipedia.org/wiki/Nofollow>.
  * **pyshell:** Treats unindented Python interactive shell sessions as <code> blocks.
  * **smarty-pants:** Fancy quote, em-dash and ellipsis handling similar to <http://daringfireball.net/projects/smartypants/>. See old issue 42 for discussion.
  * **toc:** The returned HTML string gets a new "toc_html" attribute which is a Table of Contents for the document. (experimental)
  * **wiki-tables:** Google Code Wiki table syntax support.
  * **xml:** Passes one-liner processing instructions and namespaced XML tags.

### How to turn on extras

Extras are all off by default and turned on as follows:
    
    
    >>> import markdown2
    >>> html = markdown2.markdown_path(path, ..., extras=["name1", "name2"])
    >>> html = markdown2.markdown("some markdown", ..., extras=["name1", "name2"])
    
    >>> markdowner = Markdown(..., extras=["name1", "name2"])
    >>> markdowner.convert("*boo!*")
    <em>boo!</em>
    

(New in v1.0.1.2) You can also now specify extras via the "markdown-extras" emacs-style local variable in the markdown text:
    
    
    <!-- markdown-extras: code-friendly, footnotes -->
    This markdown text will be converted with the "code-friendly" and "footnotes"
    extras enabled.

## Functions

markdown2.markdown(_text_, _html4tags=False_, _tab_width=DEFAULT_TAB_WIDTH_, _safe_mode=None_, _extras=None_, _link_patterns=None_, _use_file_vars=False_)
    

Convert the markdown-formatted text to html with the given options.

markdown2.markdown_path(_path_, _encoding="utf-8"_, _html4tags=False_, _tab_width=DEFAULT_TAB_WIDTH_, _safe_mode=None_, _extras=None_, _link_patterns=None_, _use_file_vars=False_)
    

Same as [markdown()](http://omz-software.com/editorial/docs/ios/markdown.html), but use the text in a given file as input.
