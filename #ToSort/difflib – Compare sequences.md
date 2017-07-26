# difflib – Compare sequences

_Captured: 2016-01-22 at 21:44 from [pymotw.com](https://pymotw.com/2/difflib/)_

The [difflib](https://pymotw.com/2/difflib/) module contains tools for computing and working with differences between sequences. It is especially useful for comparing text, and includes functions that produce reports using several common difference formats.

The examples below will all use this common test data in the difflib_data.py module:
    
    
    text1 = """Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Integer
    eu lacus accumsan arcu fermentum euismod. Donec pulvinar porttitor
    tellus. Aliquam venenatis. Donec facilisis pharetra tortor.  In nec
    mauris eget magna consequat convallis. Nam sed sem vitae odio
    pellentesque interdum. Sed consequat viverra nisl. Suspendisse arcu
    metus, blandit quis, rhoncus ac, pharetra eget, velit. Mauris
    urna. Morbi nonummy molestie orci. Praesent nisi elit, fringilla ac,
    suscipit non, tristique vel, mauris. Curabitur vel lorem id nisl porta
    adipiscing. Suspendisse eu lectus. In nunc. Duis vulputate tristique
    enim. Donec quis lectus a justo imperdiet tempus."""
    text1_lines = text1.splitlines()
    
    text2 = """Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Integer
    eu lacus accumsan arcu fermentum euismod. Donec pulvinar, porttitor
    tellus. Aliquam venenatis. Donec facilisis pharetra tortor. In nec
    mauris eget magna consequat convallis. Nam cras vitae mi vitae odio
    pellentesque interdum. Sed consequat viverra nisl. Suspendisse arcu
    metus, blandit quis, rhoncus ac, pharetra eget, velit. Mauris
    urna. Morbi nonummy molestie orci. Praesent nisi elit, fringilla ac,
    suscipit non, tristique vel, mauris. Curabitur vel lorem id nisl porta
    adipiscing. Duis vulputate tristique enim. Donec quis lectus a justo
    imperdiet tempus. Suspendisse eu lectus. In nunc. """
    text2_lines = text2.splitlines()
    

## Comparing Bodies of Text

The Differ class works on sequences of text lines and produces human-readable _deltas_, or change instructions, including differences within individual lines.

The default output produced by Differ is similar to the **diff** command line tool is simple with the Differ class. It includes the original input values from both lists, including common values, and markup data to indicate what changes were made.

  * Lines prefixed with - indicate that they were in the first sequence, but not the second.
  * Lines prefixed with + were in the second sequence, but not the first.
  * If a line has an incremental difference between versions, an extra line prefixed with ? is used to highlight the change within the new version.
  * If a line has not changed, it is printed with an extra blank space on the left column so that it it lines up with the other lines that may have differences.

To compare text, break it up into a sequence of individual lines and pass the sequences to compare().
    
    
    import difflib
    from difflib_data import *
    
    d = difflib.Differ()
    diff = d.compare(text1_lines, text2_lines)
    print '\n'.join(diff)
    

The beginning of both text segments in the sample data is the same, so the first line is printed without any extra annotation.
    
    
    1:   Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Integer
    

The second line of the data has been changed to include a comma in the modified text. Both versions of the line are printed, with the extra information on line 4 showing the column where the text was modified, including the fact that the , character was added.
    
    
    2: - eu lacus accumsan arcu fermentum euismod. Donec pulvinar porttitor
    3: + eu lacus accumsan arcu fermentum euismod. Donec pulvinar, porttitor
    4: ?                                                         +
    5:
    

Lines 6-9 of the output shows where an extra space was removed.
    
    
    6: - tellus. Aliquam venenatis. Donec facilisis pharetra tortor.  In nec
    7: ?                                                             -
    8:
    9: + tellus. Aliquam venenatis. Donec facilisis pharetra tortor. In nec
    

Next a more complex change was made, replacing several words in a phrase.
    
    
    10: - mauris eget magna consequat convallis. Nam sed sem vitae odio
    11: ?                                              - --
    12:
    13: + mauris eget magna consequat convallis. Nam cras vitae mi vitae odio
    14: ?                                            +++ +++++   +
    15:
    

The last sentence in the paragraph was changed significantly, so the difference is represented by simply removing the old version and adding the new (lines 20-23).
    
    
    16:   pellentesque interdum. Sed consequat viverra nisl. Suspendisse arcu
    17:   metus, blandit quis, rhoncus ac, pharetra eget, velit. Mauris
    18:   urna. Morbi nonummy molestie orci. Praesent nisi elit, fringilla ac,
    19:   suscipit non, tristique vel, mauris. Curabitur vel lorem id nisl porta
    20: - adipiscing. Suspendisse eu lectus. In nunc. Duis vulputate tristique
    21: - enim. Donec quis lectus a justo imperdiet tempus.
    22: + adipiscing. Duis vulputate tristique enim. Donec quis lectus a justo
    23: + imperdiet tempus. Suspendisse eu lectus. In nunc.
    

The ndiff() function produces essentially the same output.
    
    
    import difflib
    from difflib_data import *
    
    diff = difflib.ndiff(text1_lines, text2_lines)
    print '\n'.join(list(diff))
    

The processing is specifically tailored for working with text data and eliminating "noise" in the input.
    
    
    $ python difflib_ndiff.py
    
      Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Integer
    - eu lacus accumsan arcu fermentum euismod. Donec pulvinar porttitor
    + eu lacus accumsan arcu fermentum euismod. Donec pulvinar, porttitor
    ?                                                         +
    
    - tellus. Aliquam venenatis. Donec facilisis pharetra tortor.  In nec
    ?                                                             -
    
    + tellus. Aliquam venenatis. Donec facilisis pharetra tortor. In nec
    - mauris eget magna consequat convallis. Nam sed sem vitae odio
    ?                                             ------
    
    + mauris eget magna consequat convallis. Nam cras vitae mi vitae odio
    ?                                            +++        +++++++++
    
      pellentesque interdum. Sed consequat viverra nisl. Suspendisse arcu
      metus, blandit quis, rhoncus ac, pharetra eget, velit. Mauris
      urna. Morbi nonummy molestie orci. Praesent nisi elit, fringilla ac,
      suscipit non, tristique vel, mauris. Curabitur vel lorem id nisl porta
    - adipiscing. Suspendisse eu lectus. In nunc. Duis vulputate tristique
    - enim. Donec quis lectus a justo imperdiet tempus.
    + adipiscing. Duis vulputate tristique enim. Donec quis lectus a justo
    + imperdiet tempus. Suspendisse eu lectus. In nunc.
    

### Other Output Formats

While the Differ class shows all of the input lines, a _unified diff_ only includes modified lines and a bit of context. In Python 2.3, the unified_diff() function was added to produce this sort of output:
    
    
    import difflib
    from difflib_data import *
    
    diff = difflib.unified_diff(text1_lines, text2_lines, lineterm='')
    print '\n'.join(list(diff))
    

The output should look familiar to users of subversion or other version control tools:
    
    
    $ python difflib_unified.py
    
    ---
    +++
    @@ -1,10 +1,10 @@
     Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Integer
    -eu lacus accumsan arcu fermentum euismod. Donec pulvinar porttitor
    -tellus. Aliquam venenatis. Donec facilisis pharetra tortor.  In nec
    -mauris eget magna consequat convallis. Nam sed sem vitae odio
    +eu lacus accumsan arcu fermentum euismod. Donec pulvinar, porttitor
    +tellus. Aliquam venenatis. Donec facilisis pharetra tortor. In nec
    +mauris eget magna consequat convallis. Nam cras vitae mi vitae odio
     pellentesque interdum. Sed consequat viverra nisl. Suspendisse arcu
     metus, blandit quis, rhoncus ac, pharetra eget, velit. Mauris
     urna. Morbi nonummy molestie orci. Praesent nisi elit, fringilla ac,
     suscipit non, tristique vel, mauris. Curabitur vel lorem id nisl porta
    -adipiscing. Suspendisse eu lectus. In nunc. Duis vulputate tristique
    -enim. Donec quis lectus a justo imperdiet tempus.
    +adipiscing. Duis vulputate tristique enim. Donec quis lectus a justo
    +imperdiet tempus. Suspendisse eu lectus. In nunc.
    

Using context_diff() produces similar readable output:
    
    
    $ python difflib_context.py
    
    ***
    ---
    ***************
    *** 1,10 ****
      Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Integer
    ! eu lacus accumsan arcu fermentum euismod. Donec pulvinar porttitor
    ! tellus. Aliquam venenatis. Donec facilisis pharetra tortor.  In nec
    ! mauris eget magna consequat convallis. Nam sed sem vitae odio
      pellentesque interdum. Sed consequat viverra nisl. Suspendisse arcu
      metus, blandit quis, rhoncus ac, pharetra eget, velit. Mauris
      urna. Morbi nonummy molestie orci. Praesent nisi elit, fringilla ac,
      suscipit non, tristique vel, mauris. Curabitur vel lorem id nisl porta
    ! adipiscing. Suspendisse eu lectus. In nunc. Duis vulputate tristique
    ! enim. Donec quis lectus a justo imperdiet tempus.
    --- 1,10 ----
      Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Integer
    ! eu lacus accumsan arcu fermentum euismod. Donec pulvinar, porttitor
    ! tellus. Aliquam venenatis. Donec facilisis pharetra tortor. In nec
    ! mauris eget magna consequat convallis. Nam cras vitae mi vitae odio
      pellentesque interdum. Sed consequat viverra nisl. Suspendisse arcu
      metus, blandit quis, rhoncus ac, pharetra eget, velit. Mauris
      urna. Morbi nonummy molestie orci. Praesent nisi elit, fringilla ac,
      suscipit non, tristique vel, mauris. Curabitur vel lorem id nisl porta
    ! adipiscing. Duis vulputate tristique enim. Donec quis lectus a justo
    ! imperdiet tempus. Suspendisse eu lectus. In nunc.
    

### HTML Output

HtmlDiff produces HTML output with the same information as Diff.
    
    
    import difflib
    from difflib_data import *
    
    d = difflib.HtmlDiff()
    print d.make_table(text1_lines, text2_lines)
    

This example uses make_table(), which only returns the table tag containing the difference information. The make_file() method produces a fully-formed HTML file as output.

## Junk Data

All of the functions that produce difference sequences accept arguments to indicate which lines should be ignored, and which characters within a line should be ignored. These parameters can be used to skip over markup or whitespace changes in two versions of a file, for example.
    
    
    # This example is taken from the source for difflib.py.
    
    from difflib import SequenceMatcher
    
    A = " abcd"
    B = "abcd abcd"
    
    print 'A = %r' % A
    print 'B = %r' % B
    
    print '\nWithout junk detection:'
    
    s = SequenceMatcher(None, A, B)
    i, j, k = s.find_longest_match(0, 5, 0, 9)
    print '  i = %d' % i
    print '  j = %d' % j
    print '  k = %d' % k
    print '  A[i:i+k] = %r' % A[i:i+k]
    print '  B[j:j+k] = %r' % B[j:j+k]
    
    print '\nTreat spaces as junk:'
    
    s = SequenceMatcher(lambda x: x==" ", A, B)
    i, j, k = s.find_longest_match(0, 5, 0, 9)
    print '  i = %d' % i
    print '  j = %d' % j
    print '  k = %d' % k
    print '  A[i:i+k] = %r' % A[i:i+k]
    print '  B[j:j+k] = %r' % B[j:j+k]
    

The default for Differ is to not ignore any lines or characters explicitly, but to rely on the ability of SequenceMatcher to detect noise. The default for ndiff() is to ignore space and tab characters.
    
    
    $ python difflib_junk.py
    
    A = ' abcd'
    B = 'abcd abcd'
    
    Without junk detection:
      i = 0
      j = 4
      k = 5
      A[i:i+k] = ' abcd'
      B[j:j+k] = ' abcd'
    
    Treat spaces as junk:
      i = 1
      j = 0
      k = 4
      A[i:i+k] = 'abcd'
      B[j:j+k] = 'abcd'
    

## Comparing Arbitrary Types

The SequenceMatcher class compares two sequences of any types, as long as the values are hashable. It uses an algorithm to identify the longest contiguous matching blocks from the sequences, eliminating "junk" values that do not contribute to the real data.
    
    
    import difflib
    from difflib_data import *
    
    s1 = [ 1, 2, 3, 5, 6, 4 ]
    s2 = [ 2, 3, 5, 4, 6, 1 ]
    
    print 'Initial data:'
    print 's1 =', s1
    print 's2 =', s2
    print 's1 == s2:', s1==s2
    print
    
    matcher = difflib.SequenceMatcher(None, s1, s2)
    for tag, i1, i2, j1, j2 in reversed(matcher.get_opcodes()):
    
        if tag == 'delete':
            print 'Remove %s from positions [%d:%d]' % (s1[i1:i2], i1, i2)
            del s1[i1:i2]
    
        elif tag == 'equal':
            print 'The sections [%d:%d] of s1 and [%d:%d] of s2 are the same' % \
                (i1, i2, j1, j2)
    
        elif tag == 'insert':
            print 'Insert %s from [%d:%d] of s2 into s1 at %d' % \
                (s2[j1:j2], j1, j2, i1)
            s1[i1:i2] = s2[j1:j2]
    
        elif tag == 'replace':
            print 'Replace %s from [%d:%d] of s1 with %s from [%d:%d] of s2' % (
                s1[i1:i2], i1, i2, s2[j1:j2], j1, j2)
            s1[i1:i2] = s2[j1:j2]
    
        print 's1 =', s1
        print 's2 =', s2
        print
    
    print 's1 == s2:', s1==s2
    

This example compares two lists of integers and uses get_opcodes() to derive the instructions for converting the original list into the newer version. The modifications are applied in reverse order so that the list indexes remain accurate after items are added and removed.
    
    
    $ python difflib_seq.py
    
    Initial data:
    s1 = [1, 2, 3, 5, 6, 4]
    s2 = [2, 3, 5, 4, 6, 1]
    s1 == s2: False
    
    Replace [4] from [5:6] of s1 with [1] from [5:6] of s2
    s1 = [1, 2, 3, 5, 6, 1]
    s2 = [2, 3, 5, 4, 6, 1]
    
    The sections [4:5] of s1 and [4:5] of s2 are the same
    s1 = [1, 2, 3, 5, 6, 1]
    s2 = [2, 3, 5, 4, 6, 1]
    
    Insert [4] from [3:4] of s2 into s1 at 4
    s1 = [1, 2, 3, 5, 4, 6, 1]
    s2 = [2, 3, 5, 4, 6, 1]
    
    The sections [1:4] of s1 and [0:3] of s2 are the same
    s1 = [1, 2, 3, 5, 4, 6, 1]
    s2 = [2, 3, 5, 4, 6, 1]
    
    Remove [1] from positions [0:1]
    s1 = [2, 3, 5, 4, 6, 1]
    s2 = [2, 3, 5, 4, 6, 1]
    
    s1 == s2: True
    

SequenceMatcher works with custom classes, as well as built-in types, as long as they are hashable.
