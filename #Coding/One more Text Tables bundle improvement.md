# One more Text Tables bundle improvement

_Captured: 2016-05-29 at 12:28 from [www.leancrew.com](http://www.leancrew.com/all-this/2012/04/one-more-text-tables-bundle-improvement/)_

Last month, I presented [an improvement](http://www.leancrew.com/all-this/2012/03/improved-markdown-table-commands-for-textmate/) to my old [Text Tables bundle](http://www.leancrew.com/all-this/2008/08/tables-for-markdown-and-textmate/) for TextMate. The bundle supplies a few commands for reformatting [MultiMarkdown](http://fletcherpenney.net/multimarkdown/)-style tables. This post adds one more improvement to properly handle empty cells. If you just want the bundle and don't care about its internals, you can just download [the zipped bundle](http://www.leancrew.com/all-this/downloads/text-tables.zip), unzip it, and drag it into TextMate to install it.

OK, now that the riffraff are gone, let's talk about the coding. The updated bundle solves a problem in the Normalize Table command. Normalize Table takes a quickly written table like this,
    
    
    |Left align|Right align|Center align|
    |:---------|----------:|:----------:|
    |This|This|This|
    |column|column|column|
    |will|will|will|
    |be|be|be|
    |left|right|center|
    |aligned|aligned|aligned|

and turns it into one that looks like this,
    
    
    | Left align | Right align | Center align |
    |:-----------|------------:|:------------:|
    | This       |        This |     This     |
    | column     |      column |    column    |
    | will       |        will |     will     |
    | be         |          be |      be      |
    | left       |       right |    center    |
    | aligned    |     aligned |   aligned    |

I should stress that this has no effect on the Markdown processing; it just makes the table easier to read in TextMate. You could also, I'm sure, take the code and turn it into a command that would work in BBEdit or vim, but I leave that as an exercise for the reader.

In [a comment](http://www.leancrew.com/all-this/2012/03/improved-markdown-table-commands-for-textmate/#comment-20032) to [last month's post](http://www.leancrew.com/all-this/2012/03/improved-markdown-table-commands-for-textmate/) reader BZH Geek pointed out an important bug associated with empty cells. When given a table written like this,
    
    
    |Left align|Right align|Center align|
    |:-|-:|:-:|
    |1|2|3|
    ||1|2|
    |||1|

the Normalize Table command would turn it into this,
    
    
    | Left align | Right align | Center align |
    |:-----------|------------:|:------------:|
    | 1          |           2 |      3       |
    | 1          |           2 |              |
    | 1          |             |              |

which put the empty cells in the wrong places. This bug bit only when empty cells were at the beginning of a row; trailing and internal empty cells were handled correctly.

The culprit was my use of `strip('| ')` to get rid of leading and trailing spaces and pipes before breaking a row up, via `split('|')`, into a list of cells. My intention was to get rid of any and all inadvertent leading and trailing spaces and also to eliminate the single leading and trailing pipe characters that define the boundaries of the row. The problem was that `strip('| ')` eliminated _all_ the leading and trailing pipes, not just the first and the last. This left rows that had repeated pipes with fewer cells than they were supposed to have, and Normalize Table would deal with that by putting as many empty cells as needed at the end of the row.

The solution was to treat spaces and pipes separately. Normalize Table still uses `strip` to get rid of all leading and trailing spaces, but it's more careful with pipes, deleting only the first and last. Here's the new script:
    
    
     1  #!/usr/bin/python
     2  
     3  import sys
     4  
     5  def just(string, type, n):
     6      "Justify a string to length n according to type."
     7      
     8      if type == '::':
     9          return string.center(n)
    10      elif type == '-:':
    11          return string.rjust(n)
    12      elif type == ':-':
    13          return string.ljust(n)
    14      else:
    15          return string
    16  
    17  
    18  def normtable(text):
    19      "Aligns the vertical bars in a text table."
    20      
    21      # Start by turning the text into a list of lines.
    22      lines = text.splitlines()
    23      rows = len(lines)
    24      
    25      # Figure out the cell formatting.
    26      # First, find the separator line.
    27      for i in range(rows):
    28          if set(lines[i]).issubset('|:.-'):
    29              formatline = lines[i]
    30              formatrow = i
    31              break
    32      
    33      # Delete the separator line from the content.
    34      del lines[formatrow]
    35      
    36      # Determine how each column is to be justified.
    37      formatline = formatline.strip(' ')
    38      if formatline[0] == '|': formatline = formatline[1:]
    39      if formatline[-1] == '|': formatline = formatline[:-1]
    40      fstrings = formatline.split('|')
    41      justify = []
    42      for cell in fstrings:
    43          ends = cell[0] + cell[-1]
    44          if ends == '::':
    45              justify.append('::')
    46          elif ends == '-:':
    47              justify.append('-:')
    48          else:
    49              justify.append(':-')
    50      
    51      # Assume the number of columns in the separator line is the number
    52      # for the entire table.
    53      columns = len(justify)
    54      
    55      # Extract the content into a matrix.
    56      content = []
    57      for line in lines:
    58          line = line.strip(' ')
    59          if line[0] == '|': line = line[1:]
    60          if line[-1] == '|': line = line[:-1]
    61          cells = line.split('|')
    62          # Put exactly one space at each end as "bumpers."
    63          linecontent = [ ' ' + x.strip() + ' ' for x in cells ]
    64          content.append(linecontent)
    65      
    66      # Append cells to rows that don't have enough.
    67      rows = len(content)
    68      for i in range(rows):
    69          while len(content[i]) < columns:
    70              content[i].append('')
    71      
    72      # Get the width of the content in each column. The minimum width will
    73      # be 2, because that's the shortest length of a formatting string and
    74      # because that matches an empty column with "bumper" spaces.
    75      widths = [2] * columns
    76      for row in content:
    77          for i in range(columns):
    78              widths[i] = max(len(row[i]), widths[i])
    79      
    80      # Add whitespace to make all the columns the same width and 
    81      formatted = []
    82      for row in content:
    83          formatted.append('|' + '|'.join([ just(s, t, n) for (s, t, n) in zip(row, justify, widths) ]) + '|')
    84      
    85      # Recreate the format line with the appropriate column widths.
    86      formatline = '|' + '|'.join([ s[0] + '-'*(n-2) + s[-1] for (s, n) in zip(justify, widths) ]) + '|'
    87      
    88      # Insert the formatline back into the table.
    89      formatted.insert(formatrow, formatline)
    90      
    91      # Return the formatted table.
    92      return '\n'.join(formatted)
    93  
    94          
    95  # Read the input, process, and print.
    96  unformatted = sys.stdin.read()   
    97  print normtable(unformatted)
    
    

The improvements are in Lines 37-40 and Lines 58-61. To make it easier to see, here are 58-61 all by themselves.
    
    
    58          line = line.strip(' ')
    59          if line[0] == '|': line = line[1:]
    60          if line[-1] == '|': line = line[:-1]
    61          cells = line.split('|')
    
    

As you can see, Line 58 deletes the line's leading and trailing spaces. Line 59 then deletes the first pipe (if there is one), and Line 60 deletes that last pipe (if there is one). Finally, Line 61 splits the line into cells, as before.

Now Normalize Table takes BZH Geek's example table and produces
    
    
    | Left align | Right align | Center align |
    |:-----------|------------:|:------------:|
    | 1          |           2 |      3       |
    |            |           1 |      2       |
    |            |             |      1       |

as it should.

Two additional notes:

First, rows with an empty cell at the beginning must have a leading pipe to avoid ambiguity. In table defined like this,
    
    
    |Left align|Right align|Center align|
    |:-|-:|:-:|
    |1|2|3|
    ||1|2|
    |1|2|

there's no way to know whether the user intended the last row to have an empty cell at the beginning or at the end. Normalize Table will always put the empty at the end.

Finally, MultiMarkdown tables have a provision for multicolumn spans, which are designated by consecutive pipes, like this:
    
    
    | Left align | Right align | Center align |
    |:-----------|------------:|:------------:|
    | 1          |           2 |      3       |
    |            |           1 |      2       |
    | span 2 columns          ||      1       |

Although I said in [my response to BZH Geek](http://www.leancrew.com/all-this/2012/03/improved-markdown-table-commands-for-textmate/#comment-20036) that I wanted Normalize Table to handle multicolumn spans, I've since decided against it. Distinguishing between empty cells and multicolumn spans would involve either

  1. requiring empty cells to be designated by a space, which I didn't want to do; or
  2. complex logic, which I'd probably screw up.

Also, PHP Markdown Extra doesn't have a provision for multicolumn spans, so even if I got the script working right, it would be of no use to me for any of my writing here on the blog. So I'm keeping Normalize Column simple and forgoing the multicolumn span feature.
