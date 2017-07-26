# Markdown table scripts for BBEdit

_Captured: 2015-11-10 at 01:03 from [www.leancrew.com](http://www.leancrew.com/all-this/2012/11/markdown-table-scripts-for-bbedit/)_

The more you customize your editor, the harder it is to switch to another one. This is one of the reasons it took me so long to make the move away from TextMate; in six years of use, I'd accumulated a passel of commands, snippets, and specialty language definitions. The only thing more daunting than the thought of giving them up was the thought of rewriting them for another editor.

So when I switched to BBEdit a few months ago, I decided to make the transition slowly. Not by continuing to use TextMate for some tasks--that's a recipe for never switching at all--but by refusing to rewrite all my customizations right away. Instead, I'd rewrite them as needed, waiting until I ran into a situation that really called out for one of my old scripts. Unsurprisingly, these situations often arose when I was on a deadline and didn't have time to stop and rewrite an old script. This turned out to be good motivation; there's nothing like having to do a repetitive task by hand to inspire you to automate it the first chance you get.

It wasn't until this past week that I found myself wishing I had a couple of scripts from my old [Text Tables bundle](http://www.leancrew.com/all-this/2008/08/tables-for-markdown-and-textmate/). The more complicated of these, the one that [reformats](http://www.leancrew.com/all-this/2012/04/one-more-text-tables-bundle-improvement/) a [MultiMarkdown-style table](https://github.com/fletcher/MultiMarkdown/wiki/MultiMarkdown-Syntax-Guide) that looks like this
    
    
    |Left align|Right align|Center align|
    |:--|--:|:--:|
    |This|This|This|
    |column|column|column|
    |will|will|will|
    |be|be|be|
    |left|right|center|
    |aligned|aligned|aligned|

and turns it into this
    
    
    | Left align | Right align | Center align |
    |:-----------|------------:|:------------:|
    | This       |        This |     This     |
    | column     |      column |    column    |
    | will       |        will |     will     |
    | be         |          be |      be      |
    | left       |       right |    center    |
    | aligned    |     aligned |   aligned    |

was, fortunately, written entirely in Python and had no TextMate-specific features. I just grabbed the script and saved it to
    
    
    ~/Dropbox/Application Support/BBEdit/Text Filters/Normalize Table.py

which put it in BBEdit's **Text▸Apply Text Filter** submenu. Here's the script:
    
    
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
    
    

I've given it a keyboard shortcut of ⌃⌥⌘T, the same shortcut it had in TextMate.

The other script I wanted was the one that turns a table with tab-separated columns--what you get when you paste a table from a spreadsheet into a text editor--into the pipe-separated MultiMarkdown table format. In other words, I wanted to go from this
    
    
    Left align△Right align△Center align
    This△This△This
    column△column△column
    will△will△will
    be△be△be
    left△right△center
    aligned△aligned△aligned

where the triangles represent tab characters, to this
    
    
    |Left align|Right align|Center align|
    |--|--|--|
    |This|This|This|
    |column|column|column|
    |will|will|will|
    |be|be|be|
    |left|right|center|
    |aligned|aligned|aligned|

I rewrote this script from scratch because I knew it would be short and I wanted to add the formatting line, which the TextMate version didn't include. You'll note that the formatting line doesn't have any colons to indicate alignment. Even though I have to add them by hand, that's still faster than adding the whole line by hand. Not sure why I didn't put that in the TextMate version in the first place.

The script is saved in
    
    
    ~/Dropbox/Application Support/BBEdit/Text Filters/Tabs to Markdown Table.pl

and is assigned a keyboard shortcut of ⌃⌥⌘⇥ (that last one is the Tab key). Here it is:
    
    
    1  #!/usr/bin/perl -p
    2  
    3  # For each line...
    4  $n = s/\t/\|/g;       # tabs to pipes, saving the count
    5  s/^/\|/;              # pipe at beginning
    6  s/$/\|/;              # pipe at end
    7  
    8  # Add the formatting line above the second line.
    9  printf "|" . "--|"x($n+1) . "\n" if $. == 2
    
    

I wrote it in Perl because Perl is particularly good at this sort of thing. A Python script would've been longer but no clearer. The `-p` option is one of those time-saving Perlisms that eliminates the need to write a line-reading-and-writing loop.

Looking at the script, I realize that none of the regular expressions are necessary. In fact, if I had written this in Python, I wouldn't have even bothered to import the `re` library. But regular expressions are such a natural part of Perl, and are so easy to write, that I find myself using them more than I have to.

One thing I've noticed recently is that I'm always pasting text into a file and then applying filters to it. That's true not only of tabular material from spreadsheets, but also of code snippets like the ones above. The workflow is

  1. Select and copy from another application or window.
  2. Activate editor window.
  3. Paste
  4. Select the text just pasted.
  5. Apply filter.

I realized that Steps 3 and 4 could be combined with this one-line AppleScript.
    
    
    tell application "BBEdit" to set text of selection to the clipboard

It's saved in
    
    
    ~/Dropbox/Application Support/BBEdit/Scripts/Paste and Select.scpt

and assigned a keyboard shortcut of ⌥⌘V. The `set text of selection` part works even if the "selection" is zero characters long at the blinking cursor. The key side effect of `set text of selection` is that whatever it gets set to stays selected.

This is a lot easier in BBEdit than it would have been in TextMate, because TextMate doesn't have a real AppleScript library. Still, it's surprising that I never even tried to do it before.

This work is licensed under a [Creative Commons Attribution-Share Alike 3.0 Unported License](http://creativecommons.org/licenses/by-sa/3.0/).
