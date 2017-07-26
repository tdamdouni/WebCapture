# LyX export to markdown

_Captured: 2015-12-03 at 14:55 from [www.lemmster.de](http://www.lemmster.de/lyx-export-to-markdown.html)_

Command line (Lyx > Markdown)
    
    
    lyx --export latex file.lyx
    pandoc --no-wrap -f latex -t markdown file.tex > file.md
    

Command line (Markdown > Lyx)
    
    
    pandoc --no-wrap -f markdown -t latex file.md > file.tex && tex2lyx
    file.tex && lyx file.lyx
    

(--no-wrap makes sure we don't screw up e.g. \hrefs by spanning them over multiple lines)
    
    
    sudo apt-get install pandoc lyx
    

![FileFormats](http://www.lemmster.de/uploads/FileFormats-300x234.png)
    
    
    pandoc --no-wrap -f latex -t markdown -o $$o $$i
    

(might need extra whitespace at end)

![Converters](http://www.lemmster.de/uploads/Converters-300x234.png)

Want to comment? Send me an email to blog-comments at lemmster dot de and I'll paste it here (I won't publish your address). Why don't you use an external comment service like disqus, you ask? Well, I like to keep this site under my control, comments included. You can use markdown to format your comment.

## Comment by Markus Alexander Kuppe | 2013/06/23 at 11:52:37

Using:
    
    
    “pandoc –no-wrap -f markdown -t latex $$i > /tmp/mdtmp.tex && tex2lyx -f /tmp/mdtmp.tex $$o”
    

as a Markdown > LyX importer causes LyX to crash with a BO during import.

## Comment by Stephane Mourey | 2015/02/12 at 22:31:37

You should try [Multimarkdown](http://fletcherpenney.net/multimarkdown/) which works well for me with the command
    
    
     `multimarkdown -t lyx $$i > $$o`
    

as Markdown -> LyX converter.
