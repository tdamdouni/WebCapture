# Converting Markdown to a mind map

_Captured: 2015-09-27 at 15:50 from [brettterpstra.com](http://brettterpstra.com/2013/08/18/markdown-to-mind-map/)_

I'm working on a "Brainstorming workflow" post right now, and in the process I realized I needed a better tool to turn quick Markdown/plain text scribblings into mind maps. I put together a script that will accept a variety of (logical) plain text outline formats and convert them into an indented list in your clipboard. The result is formatted so that pasting it into a mind mapping application will result in a perfect set of topics and nodes for expanding on the outline.

I often start an idea in a text file, whether it's on my iPhone in [Notesy](https://itunes.apple.com/us/app/notesy-for-dropbox/id386095500?mt=8&at=10l4tL&ct=md2mm), or in [nvALT](http://brettterpstra.com/projects/nvalt/) on my Mac. An outline can only go so far for me, though, so I usually end up taking it to a mind mapping application for further expansion. Most mind mapping applications (including [MindNode](https://itunes.apple.com/app/mindnode-pro/id402398561?mt=12&at=10l4tL&ct=md2mm), Mindjet MindManager, [Curio](http://www.zengobi.com/products/curio/), and [MindMeister](http://www.mindmeister.com/)) accept indented text as an "import" option. In the cases of MindManager and MindNode, you can just hit **V** (paste) in a map to create the nodes from the clipboard. In Curio, just right click and choose "Paste as… Mind Map." In MindMeister you have to save to a text file and import it, but it's still a very convenient way to start a map.

I've packaged the script as both a System Service and a [PopClip](http://pilotmoon.com/popclip/) extension. They both do the same thing; it's just two ways to access the script based on your preference.

### Usage

What the script does is take any "logically" formatted outline and turn it into a plain, tab-indented list in your clipboard. The input text can be any combination of Markdown lists, sequential headlines, paragraphs or indented text. Running the Service or PopClip extension on a basic list such as:
    
    
    - Brainstorming
    	- Curio
    	- Mindjet MindManager
    	- MindNode Pro
    	- OmniOutliner
    	- nvALT
    		- Markdown
    		- tab-indented outlines

and then pasting into MindNode produces:

![](http://brettterpstra.com/uploads/2013/08/md2mm-outline@2x.jpg)

You can also use sequential ATX-style headlines (`## headline`) to create topics, and you can mix in plain text and Markdown lists to create additional sub-nodes. The lowest level header becomes the top-level node. Another example with mixed formats:
    
    
    # Brainstorming
    ## Outlining
    ### nvALT
    Markdown
    Plain text lists
    ### OmniOutliner Pro
    ## Mind mapping
    ### Mindjet MindManager
    ### Curio
    - internal mind maps
    	- can convert to outlines
    	- copy as OPML
    - embed maps from other apps
    ### MindNode Pro
    Export OPML

Turns into:

![](http://brettterpstra.com/uploads/2013/08/md2mm-complex@2x.jpg)

Basically, whatever format you outline in, the script should be smart enough to pick up on and convert for you. If you have a system that doesn't work, let me know!

### System Service

To use the script as a Service, download the zip file below, extract it and place it in ~/Library/Services ([more info](http://brettterpstra.com/howtos/install-an-os-x-system-service/)). Then, with outline text selected, right click and choose "Markdown to Mind Map" from the right-click menu.

#### Markdown to MindMap v1.3

### PopClip extension

If you use [PopClip](http://pilotmoon.com/popclip/), download the PopClip extension as part of the "Brett's PopClip Extensions" package and double-click the Markdown2MindMap extension to install it. The source is available on [in the GitHub repository](https://github.com/ttscoff/popclipextensions).

This solves a gap in my workflow nicely, and hopefully it will be of use to others. I'll post a more detailed workflow showing how I use it as part of my brainstorming process soon.
