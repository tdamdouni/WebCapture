# iThoughts can be 'driven' by other apps using a technique called x-callback-url

_Captured: 2015-09-21 at 21:56 from [toketaware.com](http://toketaware.com/ithoughts-howto-x-callback-url/)_

(see [here](http://x-callback-url.com) for the techie details.) This enables apps such as 'Editorial' and 'Drafts' to send text (or Markdown) over into iThoughts and have it converted into a mind map. It also enables apps such as 'Launch Center Pro' to provide 'quick access' to features such as adding new topics to specific locations in existing maps.

## Turn Markdown/Text into a mind map 

You can send Markdown/text from one app (e.g. Editorial, Drafts etc.) and have it turned into a new mind map.

The basic URL to CREATE a map is as follows:

**ithoughts://x-callback-url/makeMap**

Then the following parameters are supported:

**text**=<text to convert - if [[clipboard]] then contents of clipboard are used>

**note**=<text appended to the notes field of the _first topic_ created by this call>

**link**=<text appended to the link field of the _first topic_ created by this call>

**format**=<md or text - will attempt to auto detect if not supplied>

**path**=<path to map - will generate one if not supplied - will OVERWRITE existing map>

**style**=<name of style to use when creating map - will use system default if not supplied>

NB: Assume everything is case sensitive and remember to '[percent encode](http://en.wikipedia.org/wiki/Percent-encoding)' the parameters.

Below you can see some Markdown text in Editorial which has been selected and the 'Send to iThoughts' workflow tapped. The workflow sends the text over into iThoughts to be converted into a map. Notice how (in addition to the text) the path to the map and the style settings are passed as parameters.

![](http://static1.squarespace.com/static/5065b792c4aac831ab26e463/t/53f221fee4b0af31b6eb761f/1408377360139/?format=300w)

![](http://static1.squarespace.com/static/5065b792c4aac831ab26e463/t/53f21d8de4b08ee76485786f/1408376219682/?format=300w)

![](http://static1.squarespace.com/static/5065b792c4aac831ab26e463/t/53f21d25e4b01c5e39214fa8/1408376115622/?format=300w)

_Click to expand_

## Amending an existing map

It is also possible to amend an existing map. This requires the original app to supply a path to an existing map and a 'target' to identify where (under which topic) the amendment should apply.

The basic URL to AMEND a map is as follows:

**ithoughts://x-callback-url/amendMap**

Then the following parameters are supported:

**text**=<text to convert - if [[clipboard]] then contents of clipboard are used>

**note**=<text appended to the notes field of the _first topic_ created by this call>

**link**=<text appended to the link field of the _first topic_ created by this call>

**format**=<md or text - will attempt to auto detect if not supplied>

**path**=<path to map - must exist already>

**target**=<string to match - first topic with this substring will be used - can be a regex>

**edit**=<YES or NO - YES will select the new topic and edit it>

A good use for this is to create a shortcut in 'Launch Center Pro' to add a new topic to a '/tasks' map under the 'newtasks' topic. Notice how (in the following example) we don't even pass in any text - thus we get a new blank topic.

![](http://static1.squarespace.com/static/5065b792c4aac831ab26e463/t/53f5d713e4b0da8664b0f73a/1408620310192/?format=300w)

NB: You can also send a link to the current page from Safari using a Bookmarklet - see [here](http://toketaware.com/ithoughts-howto-bookmarklet)
