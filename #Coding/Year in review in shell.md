# Year in review in shell

_Captured: 2015-12-31 at 21:46 from [leancrew.com](http://leancrew.com/all-this/2015/12/year-in-review-in-shell/)_

This is the traditional time for bloggers to look back over the year and give statistics on pageviews, most popular posts, and things like that. I don't keep track of stuff like that ([this experiment with Piwik](http://leancrew.com/all-this/2015/08/non-google-analytics/) didn't last long), but because ANIAT is a static site organized through a hierarchical folder structure and built from Markdown files, it's easy to summarize the posts themselves though Unix shell tools.

The Markdown source files are kept in a Dropbox directory called `source`, with subdirectories for each year and sub-subdirectories for each month. For example, the source for this post is in a file called
    
    
    ~/Dropbox/Elements/all-this/source/2015/12/year-in-review-in-shell.md

where the tilde is shell-speak for my home directory.

With this organization scheme, I `cd`'d into the `2015` directory and used this command to get the total number of posts for the year, which is 133:
    
    
    ls */* | wc -l

The `ls` command lists all the files that are one subdirectory deep, one per line. These are the Markdown source files. The list is then piped to `wc`, which, when given the `-l` switch, prints out just the number of lines of its input.

This is nice for the total, but it doesn't say much for how the posts were distributed throughout the year. For that, I ran this command:
    
    
    for d in `ls`; do echo -n $d; ls $d | wc -l; done

which looped through all the month directories, got the number of files in each, and printed them out, each month on its own line. The output was this:
    
    
    01      17
    02      11
    03       9
    04       8
    05       9
    06      14
    07      11
    08      20
    09      11
    10       6
    11       5
    12      12

October and November were a real dropoff.

In this command, the backticks around the first `ls` executed that command, which gave a list of the month directories. The `for` command looped through that list, assigning the name of a month directory to the variable `d` each time through the loop. The `echo -n $d` command printed the name of the current month directory, suppressing the newline that `echo` normally adds to the end of what it prints. The `ls $d | wc -l` composite command listed the contents of the current month directory and then printed the line count of the list. The `do` and `done` act as brackets for the commands executed each time through the loop.

Finally, I wanted to know how many words I wrote for the blog. Counting words is the main job of `wc`, and I could string together all the posts via `cat`. The resulting pipeline was very simple:
    
    
    cat */* | wc -w

It gave me an answer of 106,967 words. You could argue that this is a bit of an overestimate, as it includes hidden text, like a few header lines at the top of each post and the URLs of links and images. I don't think it's worth the effort to tease out those differences.

The obvious next step is to figure out how many words I wrote each month. I did that by combining parts of the commands I'd already written:
    
    
    for d in `ls`; do echo -n $d; cat $d/* | wc -w; done

The result was
    
    
    01   13732
    02    9914
    03    6415
    04    6529
    05    8148
    06   10955
    07   10134
    08   16169
    09    7929
    10    4690
    11    4032
    12    8320

I wouldn't say this was a particularly illuminating exercise, but it's nice to keep your shell skills in tune.
