# Feature: org-mode support

_Captured: 2016-02-07 at 23:09 from [forum.omz-software.com](https://forum.omz-software.com/topic/2023/feature-org-mode-support/8)_

I wrote some org (<http://orgmode.org>) related functions as a proof of concept. You can check out my screencast for more info (<https://youtu.be/JclQcwc2iJs>). They work well for my needs. Still, please back up your work before using as I make no guarantees. Perhaps they'll work for you or get the ball rolling. I'm sure there are better programmers out there who can bring this to the next level. The functions are:

** Set status to TODO  
<http://www.editorial-workflows.com/workflow/5868157243752448/iHmicbjCGnQ>  
** Set priority to A to E or none  
<http://www.editorial-workflows.com/workflow/5867376096575488/XFtytC5Exlc>  
** Set status to DONE  
<http://www.editorial-workflows.com/workflow/5801748996292608/_FdUYKZc8ok>  
** Sort by status and priority  
<http://www.editorial-workflows.com/workflow/5812294751617024/gupP4BzwlAU>  
** Set folding level  
<http://www.editorial-workflows.com/workflow/5903220819886080/TWOVI5goxlQ>

** They require 2 helper functions  
*** regexpcore1  
<http://www.editorial-workflows.com/workflow/5843896315674624/uHU7TbwvYpQ>  
*** tagline1  
<http://www.editorial-workflows.com/workflow/5842528100155392/M7MkV9-ttEA>  
*** Select line is also pretty handy:  
<http://www.editorial-workflows.com/workflow/5826771207323648/Ff1vStBebbE>

I also wrote some functions to convert between org and markdown. One simply replaces each * with # (up to 3 deep). The other creates a hybrid format with * becoming #_, ** to ##_*, etc. All my functions work with md, org, and hybrid styles for the moment.

** Org to md:  
<http://www.editorial-workflows.com/workflow/5340270866464768/kF8RXChZOD4>  
** Md to org:  
<http://www.editorial-workflows.com/workflow/5878952644050944/NGqQ3s08GTs>  
** Org to md-hybrid * to #*  
<http://www.editorial-workflows.com/workflow/5840025744834560/ngt2H9QcOo8>  
** Md-Hybrid to org #* to *  
<http://www.editorial-workflows.com/workflow/5839157624569856/7pzDbe4W2Zs>
