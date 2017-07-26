# Markdown Parsers in Python

_Captured: 2015-06-09 at 21:52 from [lepture.com](http://lepture.com/en/2014/markdown-parsers-in-python)_

There are many markdown parsers in Python. Misaka was my favorite one. However, misaka is deprecated now, and the successor which is called hoedown still has issues to solve. That's why it is a **was**. But I still love it.

Here is a list of markdown parsers for Python in my knowledge:

  * Misaka: A python binding for Sundown. (CPython required)
  * Hoedown: A python binding for Hoedown, successor of Misaka.
  * Discount: A python binding for Discount. (CPython required)
  * cMarkdown: Markdown for Python, accelerated by C. (CPython required)
  * Markdown: A pure markdown parser, the very first implementation.
  * Markdown2: Another pure markdown parser.

And I've just released another pure markdown parser too, which is called **[mistune](https://github.com/lepture/mistune)**.

## Misaka

[Misaka](https://github.com/FSX/misaka) was my favorite markdown parser. It is a python binding of Sundown, which means that it has all the features that Sundown provides.

It is super fast! Actually, it is the top one in my benchmarks. Since it is a binding of a C library, no wonder that it is this fast. If speed is what you want, you should try misaka, and as well as other bindings of a C library.

But misaka is more than speed. It is the custom renderer feature that catches my heart. I am so fond of it, that's why I implement the custom renderer feature in my own markdown parser **mistune**.

A quick and very useful sample is [code highlighting](http://misaka.61924.nl/manual/#toc_15).

However, it is a binding of a C libary. It requires CPython, if you prefer PyPy, you have no access to it. Some App Engines have a limitation on compiling C libraries too, you can't use misaka in this case. And even if you are using CPython, it is still difficult to install it on a Windows OS.

> Visual Studio's support for C is not optimal and most VS compilers are missing stdint.h, which is needed to compile Misaka.

If you are on a Windows, may god helps you. I don't care it a shit.

Footnote feature is missing in Misaka. Maybe many of you don't need such a thing, in this case, misaka has nothing bad. It is stable, efficient, and has many GFM features.

The only trouble is Sundown is deprecated.[1](http://lepture.com/en/2014/markdown-parsers-in-python)

## Hoedown

Because the Sundown library is deprecated, here comes hoedown[2](http://lepture.com/en/2014/markdown-parsers-in-python), which is the fork of the original Sundown. It has a Python binding also called as hoedown.

Since Hoedown is the successor of Sundown, and [python-hoedown](https://github.com/hhatto/python-hoedown) is the successor of Misaka, all features that misaka has, python-hoedown has them too. But python-hoedown is more than that.

  1. It is PyPy compatible.
  2. It has footnote feature.

It looks promissing, and even misaka's author recommends it. I've tried it, but failed with one issue, [a magic error](https://github.com/hhatto/python-hoedown/issues/5) that I can't do anything:
    
    
    terminated by signal SIGSEGV (Address boundary error)

This isssue is not fixed yet. Once it does, hoedown would be a good choice for non-AE users.

_Updated at Jun 23, 2014_: you can use [Hoep](https://github.com/Anomareh/Hoep) as the Python Binding.

## cMarkdown & Discount

[cMarkdown](https://github.com/paulsmith/cMarkdown) is much like Misaka, except that it is based on upskirt[3](http://lepture.com/en/2014/markdown-parsers-in-python) rather than sundown. The history is very interesting, sundown is a fork of upskirt, hoedown is a fork of sundown. And now, sundown is deprecated, upskirt is missing. The new markdown parser that vmg promised is still not available.

cMarkdown has all the disadvantages of Misaka, and it is a little slower than Misaka. This means you really should use misaka instead of cMarkdown.

Discount is a joke for me, I can't even install it successfully! There is not much to say. But I do know that Discount is slower than Sundown.

## Markdown & Markdown2

[Python-Markdown](https://github.com/waylan/Python-Markdown) is the very first markdown parser in pure Python. It is good, except the documentation. However, I miss the renderer feature in misaka, which is not in Python-Markdown.

Python-Markdown is not that slow as I expected, since Python-Markdown2 calls itself as:

> A fast and complete implementation of Markdown in Python.

But it is not true. Python-Markdown2 is much slower than Python-Markdown. I have no idea why it says itself fast. All features that 2 has, the older one has too.

The benchmark shows that Python-Markdown2 is almost twice slower than Python-Markdown. No wonder it is 2.

## Mistune

[Mistune](https://github.com/lepture/mistune) is a new (just released) markdown parser. It is the **fastest** one in all pure Python implementations. Almost **4 times faster**[4](http://lepture.com/en/2014/markdown-parsers-in-python) than Python-Markdown in pure Python environment, almost **5 times faster** with Cython's help.

I didn't expect it to be so fast when I wrote it. I know it would be a fast one, but I didn't know that it would be 4 times faster and even 5 times faster.

I have never thought of creating a Markdown parser my own. But it has been months since I reported the issue to Hoedown. The issue is still there, not solved a bit. Because it is a C binding, I am not able to do any help, the only thing I can do is waiting.

I don't use Python-Markdown or Python-Markdown2, because they have no renderer feature, and they are slow.

I have [introduced renderer feature to marked](http://lepture.com/en/2013/unpleasant-open-source), which is finally merged. And now I am trying to add the [footnote feature](https://github.com/chjj/marked/pull/351). It occured to me that I can port marked to Python, since I know marked well, and I know it is the fastest in all pure JavaScript implementations. It would be fast in Python too, and it really does.

If you are looking for a fast, full featured[5](http://lepture.com/en/2014/markdown-parsers-in-python) and pure Python implementation, Mistune is a good choice. It also has renderer feature just like Misaka. You can always influnce the rendering results with custom renderers.
    
    
    import mistune
    from pygments import highlight
    from pygments.lexers import get_lexer_by_name
    from pygments.formatters import HtmlFormatter
    
    class MyRenderer(mistune.Renderer):
        def block_code(self, code, lang):
            if not lang:
                return '\n<pre><code>%s</code></pre>\n' % \
                    mistune.escape(code.strip())
            lexer = get_lexer_by_name(lang, stripall=True)
            formatter = HtmlFormatter()
            return highlight(code, lexer, formatter)
    
    renderer = MyRenderer()
    md = mistune.Markdown(renderer=renderer)
    print(md.render('Some Markdown text.'))
    

## Additional Notes

I did a benchmark on my MacBook Air, [view the results](https://github.com/lepture/mistune/issues/1). You can run the benchmark script yourself: [bench.py](https://github.com/lepture/mistune/blob/master/tests/bench.py)
    
    
    Parsing the Markdown Syntax document 1000 times...
    Mistune: 12.7255s
    Mistune (with Cython): 9.74075s
    Misaka: 0.550502s
    Markdown: 46.4342s
    Markdown2: 78.2267s
    cMarkdown: 0.664128s
    Discount is not available

Mistune can be compiled with Cython if you have Cython installed already.
    
    
    $ pip install cython mistune

The magic happens in the `setup.py` script. I'd like to introduce this part another time.

**mistune is used by many great projects such as IPython, Rodeo and crossbar.**

*This post and all posts in markdown format on this site are rendered with mistune.*

  1. Sundown is deprecated a year ago with a [commit](https://github.com/vmg/sundown/commit/37728fb2d7137ff7c37d0a474cb827a8d6d846d8) by vmg, but the new markdown parser is still missing.[↩](http://lepture.com/en/2014/markdown-parsers-in-python)

  2. Hoedown is a fork of Sundown, it is a C library. It reverted the [deprecated message](https://github.com/hoedown/hoedown/commit/aa43a77283c613662033039eddb477f2e0fd3d63) 5 months ago.[↩](http://lepture.com/en/2014/markdown-parsers-in-python)

  3. Links about upskirt are missing now, they are all 404.[↩](http://lepture.com/en/2014/markdown-parsers-in-python)

  4. I've did a benchmark on all markdown parsers I know. [Checkout the Benchmarks](https://github.com/lepture/mistune/issues/1).[↩](http://lepture.com/en/2014/markdown-parsers-in-python)

  5. Mistune is full featured, it has autolink, strikethrough, table, fenced code, footnotes. And you can't disable them. I believe that it is a good design to enable all these features, since they are the standards in the real world now.[↩](http://lepture.com/en/2014/markdown-parsers-in-python)
