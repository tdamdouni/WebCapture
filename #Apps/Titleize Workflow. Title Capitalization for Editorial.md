# Titleize Workflow. Title Capitalization for Editorial

_Captured: 2015-09-26 at 21:27 from [www.movingelectrons.net](http://www.movingelectrons.net/blog/2014/06/23/title-capitalization-workflow-editorial-for-ios.html)_

## General

This is a quick and dirty workflow for capitalizing title lines in [Editorial for iOS](https://itunes.apple.com/us/app/editorial/id673907758?mt=8&uo=4&at=11lqkH). There are several ways to accomplish this, some people do it by calling other Apps through URL schemes, but I find this method quicker and more accurate. Additionally, you have more control over what's happening behind the scenes.

Rules for capitalization vary widely, so I used the guidelines described [in this article](http://grammar.yourdictionary.com/capitalization/rules-for-capitalization-in-titles.html) which are inline with what is recommended by [The U.S. Government Printing Office Style Manual](http://www.gpo.gov/fdsys/search/pagedetails.action?granuleId=&packageId=GPO-STYLEMANUAL-2008&fromBrowse=true) and [this other site](http://titlecapitalization.com/#).

## How Does it Work?

The workflow selects the line the cursor is currently on (i.e. no need to make a selection) and sends it to a small python script, which is the one doing all the heavy lifting. The script processes the text and sends it back to the workflow, which in turn replaces the line with the capitalized title. Here is the Python code:
    
    
    #coding: utf-8
    import workflow
    import re
    
    exception_list = ['a','an','the','at','by','for','in','of','on','to','up','and','as','but','it', 'or','nor', 'from']
    
    title = workflow.get_input()
    
    word_list = re.split(' ', title)
    final = [word_list[0].capitalize()] # First word is always capitalized
    
    for word in word_list[1:]:
    
        if word in exception_list:
            tmp = word
        else:
            tmp = word.capitalize()
    
        final.append(tmp)
    
    final[-1]=final[-1].capitalize() # Last word is always capitalized
    output=" ".join(final)
    
    workflow.set_output(output)
    

I could have optimized the code a little bit more to make it shorter, but wanted to be as clear as possible so it can easily be revised down the road.

Once the line of text is passed to it, the script parses the words and puts them in a list (`re.split(' '.title)`). It capitalizes the first word and then iterates over the list checking each word against a list of _exceptions_. If a word is matched, then it's not capitalized, otherwise it's capitalized. In the end, the last word is capitalized regardless of wether it's in the list of exceptions or not.

Editorial runs the Workflow nicely and really fast as you can see below:

You can view and install the Workflow [here](http://www.editorial-workflows.com/workflow/6282806338519040/Ftd5tmiLYfw).

## Resources
