# Editorial – First Impressions, and a Workflow

_Captured: 2015-11-27 at 22:42 from [www.devwithimagination.com](http://www.devwithimagination.com/2013/10/03/editorial-first-impressions-and-a-workflow/)_

I have been playing with [Editorial](http://omz-software.com/editorial/index.html) for a couple of days now and had my first experiment with the workflow features. I must say, I do like it a lot!

![Image](http://www.devwithimagination.com/images/editorial_first_look/appIcon.jpg)

> _[Editorial Icon](https://itunes.apple.com/gb/app/editorial/id673907758?mt=8&uo=4&at=10lsY7)_

When Editorial was first released there was a lot of hype for the application by the tech community (at least from the people I follow on Twitter). There is a true monster of a review for this application (and a must read to discover the true power of it) that I was only part way through when I decided I would just spend the £2.99 and try it for myself. it definitely lives up to the hype. The review In question is by Federico Viticci of Macstories and is available here: [Reinventing iOS Automation: Editorial Review](http://www.macstories.net/stories/editorial-for-ipad-review/). He has produced an extended version of this review along with more example workflows which is [available as an iBook](https://itunes.apple.com/us/book/writing-on-ipad-text-automation/id697865620?mt=11&uo=4&at=10l6nh&ct=ms_editorial_announcement). I am still to finish reading this, as I keep taking breaks to try out the application and come up with my own workflows based on the ideas presented in the book. It is definitely worth reading if you want/need more than just a basic text editor to write. I am not even going to try going in to any depth of the features available, everything you could ever need to know about the application is contained in the above links.

I have came across a few minor issues to do with selecting text and auto closing of brackets, but it does appear to be a very stable application for a 1.0 release.

## Current Setup

My previous iOS writing app of choice has been [iA Writer](http://www.iawriter.com/ipad/). I own both the iOS and Mac versions, and have been very happy with them for writing simple documents which required very little formatting. It is designed, and billed, to be a distraction free editor that allows you to focus just on the text of the document. It supports markdown, and allows the final formatted text to be exported in a variety of formats. The latest update for the Mac version now supports two way conversion with the DOCX format, I'm still to try this but it could be a great feature if it works reliably. This is going to remain my app of choice on the Mac, I love the distraction free interface (especially when using the app fullscreen).

On the iPad however, Editorial has me converted. The markdown editor in iA Writer works well when the formatting is simple headers, emphasis and lists, but can be hard to work with when writing a post that contains a lot of links. I think that I find this an issue as the first category of items use markdown that only uses a few successive characters, and the marks themselves add the effect (with varying levels of accuracy) to the text. I find the way that Editorial renders markdown while in the editor less distracting, and it has options to change how these are formatted. It allows the opacity of the formatting characters to be reduced, but also allows the inline formatting to be disabled completely if that is preferred. The reduced opacity of the markdown syntax makes it easier to skim over the formatting characters when reading in the editor. It does have a preview screen that shows the document with the markdown formatting applied, but I only really use this as a final step when I think the document is finished and requires proof reading, while actively working I will read in the editor.

## Workflows

Editorial is a very capable text editor, but it's true power lies in it's workflow functionality.

In a [previous post](/2013/08/06/a-blogging-workflow/ "A Blogging Workflow
Dev With Imagination") I had written about using the Zemanta service for automatically generating the keywords that were relevant to a post for SEO purposes, with a pretty high level of accuracy (the code for this had came from a [post by Brett Terpstra](http://brettterpstra.com/2013/03/23/auto-tagging-jekyll-posts-with-zemanta/)). As a first attempt to do something with the Workflows feature of Editorial I have migrated this part of my workflow to Editorial.

This required using the "Run Python Script" action to call the Zemanta API. I have never written anything in Python before but with the help of a quick start tutorial, the Zemanta [code snippet](http://developer.zemanta.com/wiki/helloworld/python/) and [API documentation](http://developer.zemanta.com/docs/suggest/) I was able to pick up the basics required for this simple task. The bit I actually found most difficult was getting the regex right that is used to determine the range of the document to replace! This workflow works by identifying the YAML front matter at the start of the document, loading the keyword suggestions for the body of the document, then updating the YAML header with this information.

Editorial allows you to share workflows that you have created, so this is available [here](http://editorial-app.appspot.com/workflow/5136686396735488/zgbeHU5QcX8). As I said, I'm only just starting with Python and workflows so it may not be the optimal way to achieve the task, but it is working for me. **Note:** this requires an API key that is freely available from [their developer site](http://developer.zemanta.com/docs/) to be added as the value to the first parameter in the workflow. I've added a conditional to warn if this is missing.

**Update:** I have noticed this will mess up any Unicode characters in the front mater, turning them in to their respective codes. Not sure at this point how to resolve this issue. [Tweet me](https://twitter.com/davidhutchison) suggestions!

The workflow that I'm using the most just now is from the review/book above. It deals with inserting a markdown formatted link for the current selected text, using the web page that is currently open in Editorial's web browser. It is available [here](http://editorial-app.appspot.com/workflow/6258007868440576/-PjiU8b7VOw).

## Going Forwards

This workflow is a good first step in the direction of being able to publish posts from my iPad, but it only forms one step of the process involved between writing and posting. The main step that I am still missing is a way to commit finished post files to GitHub. Once I have a solution to this there will be nothing I need to do on the computer to create and publish a new post. At the moment a copy of my Git repository for the site is held in my Dropbox so I can access it in Editorial, and this is synced back to the computer prior to doing a commit.

This should not be as impossible as it sounds, the Python engine in this application appears to very functionally similar to the Author's other application: [Pythonista.](http://omz-software.com/pythonista/) There exists [sample code](http://omz-software.com/pythonista/forums/discussion/30/access-your-github-account-from-pythonista/p1) that shows how to access files in Github from Pythonista. I have tried this in Editorial and got as far as a file listing, I should just need to figure out how to perform a commit using this Python Github API. if I get this working it will be the subject of a future post, in the mean time I will be trying it on a dummy repository that doesn't rebuild my site on commit!
