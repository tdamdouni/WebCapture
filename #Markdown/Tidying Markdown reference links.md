# Tidying Markdown reference links

_Captured: 2015-11-10 at 01:04 from [www.leancrew.com](http://www.leancrew.com/all-this/2012/09/tidying-markdown-reference-links/)_

Oscar Wilde--who would have been great on Twitter--[said](http://www.gutenberg.org/dirs/etext97/lwfan10h.htm) "I couldn't help it. I can resist everything except temptation." That's my excuse for this post.

Several days ago I got an email from a reader, asking if I knew of a script that would tidy up [Markdown reference links](http://daringfireball.net/projects/markdown/syntax#link) in a document. She wanted them reordered and renumbered at the end of the document to match the order in which they appear in the body of the text. I didn't know of one and suggested she write it herself and let me know when it's done. I've been getting progress reports, but her script isn't finished yet.

There's certainly no need to tidy the links up that way. Markdown doesn't care what order the reference links appear in or the labels that are assigned to them. I've written dozens of posts in which the order of the references at the end of the Markdown source were way off from the order of the links in body. But…

But there _is_ an attraction to putting everything in apple pie order, even when no one but me will ever see it. Last night I succumbed and wrote a script to tidy up the links. Sorry, Phaedra.

Here's an example of a short Markdown document with out-of-order reference links:
    
    
    Species and their hybrids, How simply are these facts! How
    strange that the pollen of each But we may thus have
    [succeeded][2] in selecting so many exceptions to this rule.
    but the species would not all the same species living on the
    White Mountains, in the arctic regions of that large island.
    The exceptions which are now large, and triumphant, and
    which are known to every naturalist: scarcely a single
    [character][4] in the descendants of the Glacial period,
    would have been of use to the plants, have been accumulated
    and if, in both regions.
    
    Supposed to be extinct and unknown, form. We have seen that
    it yields readily, when subjected as [under confinement][3],
    to new and improved varieties will have been much
    compressed, we may assume that the species, which are
    already present in the ordinary spines serve as a prehensile
    or snapping apparatus. Thus every gradation, from animals
    with true lungs are descended from a marsupial form), "and
    if so, there can be followed by which viscid matter, such as
    that of making [slaves][1]. Let it be remembered that
    selection may be extended--to the stigma of.
    
    [1]: http://daringfireball.net/markdown/
    [2]: http://www.google.com/
    [3]: http://docs.python.org/library/index.html
    [4]: http://www.kungfugrippe.com/

Note that the references are numbered 1, 2, 3, 4 at the bottom of the document, but that they appear in the body in the order 2, 4, 3, 1. The purpose of the script is to change the document to
    
    
    Species and their hybrids, How simply are these facts! How
    strange that the pollen of each But we may thus have
    [succeeded][1] in selecting so many exceptions to this rule.
    but the species would not all the same species living on the
    White Mountains, in the arctic regions of that large island.
    The exceptions which are now large, and triumphant, and
    which are known to every naturalist: scarcely a single
    [character][2] in the descendants of the Glacial period,
    would have been of use to the plants, have been accumulated
    and if, in both regions.
    
    Supposed to be extinct and unknown, form. We have seen that
    it yields readily, when subjected as [under confinement][3],
    to new and improved varieties will have been much
    compressed, we may assume that the species, which are
    already present in the ordinary spines serve as a prehensile
    or snapping apparatus. Thus every gradation, from animals
    with true lungs are descended from a marsupial form), "and
    if so, there can be followed by which viscid matter, such as
    that of making [slaves][4]. Let it be remembered that
    selection may be extended--to the stigma of.
    
    
    [1]: http://www.google.com/
    [2]: http://docs.python.org/library/index.html
    [3]: http://www.kungfugrippe.com/
    [4]: http://daringfireball.net/markdown/

Now the links are numbered 1, 2, 3, 4 in both the text and the end references. The HTML produced when this document is run through a Markdown processor will be the same as the previous one--the links will still go to the right places--but the Markdown source looks better.

Here's the script that does it:
    
    
     1  #!/usr/bin/python
     2  
     3  import sys
     4  import re
     5  
     6  '''Read a Markdown file via standard input and tidy its
     7  reference links. The reference links will be numbered in
     8  the order they appear in the text and placed at the bottom
     9  of the file.'''
    10  
    11  # The regex for finding reference links in the text. Don't find
    12  # footnotes by mistake.
    13  link = re.compile(r'\[([^\]]+)\]\[([^^\]]+)\]')
    14  
    15  # The regex for finding the label. Again, don't find footnotes
    16  # by mistake.
    17  label = re.compile(r'^\[([^^\]]+)\]:\s+(.+)$', re.MULTILINE)
    18  
    19  def refrepl(m):
    20    'Rewrite reference links with the reordered link numbers.'
    21    return '[%s][%d]' % (m.group(1), order.index(m.group(2)) + 1)
    22  
    23  # Read in the file and find all the links and references.
    24  text = sys.stdin.read()
    25  links = link.findall(text)
    26  labels = dict(label.findall(text))
    27  
    28  # Determine the order of the links in the text. If a link is used
    29  # more than once, its order is its first position.
    30  order = []
    31  for i in links:
    32    if order.count(i[1]) == 0:
    33      order.append(i[1])
    34  
    35  # Make a list of the references in order of appearance.
    36  newlabels = [ '[%d]: %s' % (i + 1, labels[j]) for (i, j) in enumerate(order) ]
    37  
    38  # Remove the old references and put the new ones at the end of the text.
    39  text = label.sub('', text).rstrip() + '\n'*3 + '\n'.join(newlabels)
    40  
    41  # Rewrite the links with the new reference numbers.
    42  text = link.sub(refrepl, text)
    43  
    44  print text
    
    

The regular expressions in Lines 13 and 17 are fairly easy to understand. The first one looks for the links in the body of the text and the second looks for the labels.

The key to the script are the four data structures: `links`, `labels`, `order`, and `newlabels`. For our example document, `links` is the list of tuples
    
    
    [('succeeded', '2'),
     ('single character', '4'),
     ('under confinement', '3'),
     ('slaves', '1')]

`labels` is the dictionary
    
    
    {'1': 'http://daringfireball.net/markdown/',
     '3': 'http://docs.python.org/library/index.html',
     '2': 'http://www.google.com/',
     '4': 'http://www.kungfugrippe.com/'}

`order` is the list
    
    
    ['2', '4', '3', '1']

and `newlabels` is the list of strings
    
    
    ['[1]: http://www.google.com/',
     '[2]: http://docs.python.org/library/index.html',
     '[3]: http://www.kungfugrippe.com/',
     '[4]: http://daringfireball.net/markdown/']

`links` and `labels` are built via the regex `findall` method in Lines 25-26. `links` is the direct output of the method and maintains the order in which the links appear in the text. `labels` is that same output, but converted to a dictionary. Its order, which we don't care about, is lost in the conversion, but it can be used to easily access the URL from the link label.

`order` is the order in which the link labels first appear in the text. The `if` statement in Line 32 ensures that repeated links don't overwrite each other.

`newlabels` is built from `labels` and `order` in Line 36. It's the list of labels after the renumbering. Line 39 deletes the original label lines and puts the new ones at the end of the document.

Finally, Line 42 replaces all the link labels in the body of the text with the new values. Rather than a replacement string, it uses a simple replacement function defined in Lines 19-21 to do so.

Barring any bugs I haven't found yet, this script (or filter) will work on any Markdown document and can be used either directly from the command line or through whatever system your text editor uses to call external scripts. I have it stored in BBEdit's Text Filters folder under the name "Tidy Markdown Reference Links.py," so I can call it from the **Text ‣ Apply Text Filter** submenu.

I should mention that although this script is fairly compact and simple, it didn't spring from my head fully formed. There were starts and stops as I figured out which data structures were needed and how they could be built. Each little subsection of the script was tested as I went along. The `order` list was originally a list of tuples; it wasn't until I had a working version of the entire script that I realized that it could be simplified down to a list of link labels. That change shortened the script by five lines or so and, more importantly, clarified its logic.

Despite these improvements, the script is hardly foolproof. The Markdown source of this very post confuses the hell out it. Not only does it think there are links in the sample document (which you'd probably guess), it also thinks the `[%s][%d]` in Line 21 of the script is a link (and the one in this sentence, too). And why wouldn't it? To distinguish between real links and things that look like links in embedded source code, the script would have to be able to parse Markdown, not just match a couple of short regular expressions. This is a variant on what Hamish Sanderson said in the comments on [an earlier post](http://www.leancrew.com/all-this/2012/09/applescript-syntax-highlighting-finally/).

At the moment, I'm not willing to sacrifice the simplicity of the Tidy script to get it to handle weird posts like this one. But if I find that it fails often with the kind of input I commonly give it, I'll have to revisit that decision.

As Wilde also said, "Experience is the name everyone gives to their mistakes."

This work is licensed under a [Creative Commons Attribution-Share Alike 3.0 Unported License](http://creativecommons.org/licenses/by-sa/3.0/).
