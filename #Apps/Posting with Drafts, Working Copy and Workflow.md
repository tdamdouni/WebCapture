# Posting with Drafts, Working Copy and Workflow

_Captured: 2016-03-23 at 22:06 from [www.matteocappadonna.org](http://www.matteocappadonna.org/Posting-with-Drafts,-Working-Copy-and-Workflow/)_

Finally, after the switch to the [new blog platform](http://www.matteocappadonna.org/New-blog-platform/), I searched a way to publish articles and drafts to my new blog using iOS.

First I've thinked about what I need:

  * A GIT client for iOS with all the basic functions (pull, push, commit, etc.)
  * A text editor which is fast and, possibly, configurable, and which can open files from the GIT repository
  * Some helper applications for generate quick posts from Safari link, or uploading images and screenshots from iOS to my GIT repository

And, all those applications must implement a way to talk each other, which basically mean [x-callback-url](http://x-callback-url.com/) support.

Fortunately, I've found exactly what I need:

  * [Working Copy](https://appsto.re/it/xONC1.i) : A complete GIT client with full x-callback-url support and editing via iOS Document Picker. A little price (€9.99) unlocks all features.
  * [Drafts4](https://appsto.re/it/BTL91.i): a really cool iOS text editor, really light and fast, extremely configurable, and with x-callback-support. Do you need more?
  * [Workflow](https://appsto.re/it/2IzJ2.i): the definitive application if you need to automatize things easily on iOS. I use this as a glue for different things.

#Working Copy

![Posting-with-Drafts-Working-Copy-and-Workflow-1](http://www.matteocappadonna.org/images/2015/05/Posting-with-Drafts-Working-Copy-and-Workflow-1.png)

After configuring my [GitHub](https://github.com/) account and pulled my blog repository, I've enabled the x-callback-url support and saved the provided key:

![Posting-with-Drafts-Working-Copy-and-Workflow-2](http://www.matteocappadonna.org/images/2015/05/Posting-with-Drafts-Working-Copy-and-Workflow-2.png)

Also, I've renamed my local repository checkout name "Blog", so it's more convenient and readable in the vary x-callback-url I'm going to build.

#Workflow

Despite the power of the Workflow app (which I use for, really, a lot of thing), some of workflows I created are launched by Drafts actions. This to avoid some limitations of Drafts, for example the impossibility to opening documents from Document Picker.

Here the workflows I've set up:

## [Copy as MD Link](http://www.matteocappadonna.org/files/2015/05/Copy-as-MD-Link.wflow)

This is an Action Extensions which accept URLs (generally from Safari or AppStore) and generate a link in Markdown style, copy that string in the Clipboard then open Drafts.

## [Upload to Blog](http://www.matteocappadonna.org/files/2015/05/Upload-to-Blog.wflow)

Another Action Extensions workflow for uploading images to the blog. I usually call this from Drafts in order to extract the filename from the draft itself (we'll talk about this in the Draft section).

## [Get image link](http://www.matteocappadonna.org/files/2015/05/Get-image-link.wflow)

This workflow, launched from Drafts, present the Document Picker and ask you to select a file. Then build a Markdown style link to that file and append to the Drafts I'm working on.

## [Get file link](http://www.matteocappadonna.org/files/2015/05/Get-file-link.wflow)

Works in the same way as the "Get image link" workflow, but for files. And yes, all those workflow download links are generated with this action :D

## [New Post From Clipboard](http://www.matteocappadonna.org/files/2015/05/New-Post-From-Clipboard.wflow)

This pick up the content of the Clipboard, and generate the structure for a new link post on this blog.

## [Edit Post](http://www.matteocappadonna.org/files/2015/05/Edit-Post.wflow)

Last, but not least, the workflow can permit to pick up a file from the GIT repository and continue editing on Drafts.

# Drafts 4

Finally, I've set up Drafts with some blog-related actions. I've put those in a new action group named "Blog". Here a screenshot:

![Posting-with-Drafts-Working-Copy-and-Workflow-3](http://www.matteocappadonna.org/images/2015/05/Posting-with-Drafts-Working-Copy-and-Workflow-3.png)

From the top, here a list with a brief description (we see them in detail later):

  * _New draft_: pick the current draft and save it in the _drafts directory on the repository. The draft name is generated from the note itself
  * _New post_: pick the current draft and reformat it to match the [Jekyll](http://jekyllrb.com/) post format. Then save it in the _posts directory. The draft name are generated from the current date (YYYY-MM-DD) and the note itself.
  * _New link post_: this action acts like the "New post" one, but consider the link post format for reformatting the draft itself before loading to GIT
  * _New link post from Clipboard_: this action run the "New Post From Clipboard" workflow.
  * _Upload image for article_: this action generate the file name from the draft and save it on the clipboard. Then launch the iOS Photos app.
  * _Add image link_: extract the current draft UUID and pass it to the "Get image link" workflow. This will append to the current draft a Markdown style link to a blog image.
  * _Add file link_: like the image one, this make the same things but for downloadable file.
  * _Edit Post_: this action runs the "Edit Post" workflow.

Then I put some actions useful for managing GIT repository with Working Copy directly from Drafts, so I don't have to manually switch to the application and come back (I know, I'm a little lazy :D)

  * _Open Repository_: this will simple open the Working Copy app
  * _Pull Repository_: open Working Copy, execute a pull, then come back
  * _Commit changes_: this action will get the current draft and consider it a commit message, then commit the changes to the repository
  * _Push to remote_: finally, a quick action for pushing changes from Working Copy to the remote GitHub repository.

## Draft structure The Jekyll syntax is really simple, but need some chars which can be a little tediously to type on mobile devices. On iOS I usually don't write long posts, but just simple ones, and some link posts.

I wrote this post on iOS (some on my iPhone 6 , some on my iPad mini), but I thinks this is an exception, and I made this choice just for testing my iOS posting environment.

So I defined draft structure that can be quick to type in mobility, and easy parsable with Drafts4 and javascript (Drafts4 provide a lot of tags for extracting parts from the draft, and can run javascript code as action step).

At this time, two types of posts are managed by Drafts: the basic posts and the link posts (you can read more about those types on [this article](http://www.matteocappadonna.org/Posting-on-Postachio-from-iOS/)). I think to implement also the video post type, but for now isn't necessary.

So I defined the following structure:

  * _First line_: the post title. This will also be used for generating the post file name and the base name for image and file uploading.
  * _Second line_: list of tags (separated by spaces).
  * _Third line_: if the post will be a link post, this line must contain the linked URL.
  * _Other content_: this become the post content.

So, using this convention, the first lines of this blog post are formatted in this way:

The cool thing of this method was that the title of the draft in the Drafts4 app will be the same of the post title: easy to recognize :D

Now, come to see how Drafts actions are build! For every action step I describe how to configure that.

## New draft

Used for saving the current draft as a new blog draft; the first line will be used for generate the draft name (with the blank spaces replaced with the '-' symbol), and the extension will be .md

It's composed by three actions steps:

  * _Clipboard_: pick up the first line and save it in the system clipboard
    
    
    Template
      [[line|1]]
    

  * _Script_: this will replace the blank spaces on the file name, and define a new tag named 'filename'
    
    
    var filename = getClipboard().replace(/\ /g, '-');
    draft.defineTag("filename", filename);
    

  * _URL_: this will launch Working Copy and save the file in the _drafts directory. The file structure remain unchanged, so you can easly pick up and edit again the file. You must provide your Working Copy key (for x-callback-url security) and the callback URI must be encoded manually
    
    
    working-copy://x-callback-url/write/?x-success=drafts4%3A%2F%2F&key=YOUR_WC_KEY&repo=Blog&path=_drafts/[[filename]].md&text=[[draft]]
    

## New post

Used for saving the current draft as a new blog post; this mean that we re-elaborate the draft content in order to match the Jekyll post structure. The filename will be the first line of the draft (with spaces replaced by character '-') prefixed by the date in the form YYYY-MM-DD.

It's composed by 8 action steps:

  * _Clipboard_: pick up the first line and save it in the system clipboard
    
    
    Template
      [[line|1]]
    

  * _Script_: save the first line a new tag named 'title', and generate the 'filename' tag
    
    
    var title = getClipboard();
    draft.defineTag("title", title);
    var filename = title.replace(/\ /g, "-");
    draft.defineTag("filename", filename);
    

  * _Clipboard_: then pick up the tag list (second line in the draft), and put it in the clipboard
    
    
    Template
      [[line|2]]
    

  * _Script_: save the content of the clipboard in a new tag named 'tags'
    
    
    draft.defineTag("tags", getClipboard());
    

  * _Clipboard_: then pick up the lines from the fourth to the end of the drafts, and put it in the clipboard
    
    
    Template
      [[line|4..]]
    

  * _Script_: save the content of the clipboard in a new tag named 'content'
    
    
    draft.defineTag("content", getClipboard());
    

  * _Script_: this generate the new draft content, compliant with the Jekyll post structure
    
    
    var post = "";
    
    post += "---\n";
    post += "layout: post\n";
    post += "title: " + draft.getTag("title") + "\n";
    post += "tags: " + draft.getTag("tags") + "\n";
    post += "---\n";
    post += "\n";
    post += draft.getTag("content");
    
    draft.content = post;
    commit(draft);
    

  * _URL_: finally we have all what we need to create the new post via Working Copy x-callback-url
    
    
    working-copy://x-callback-url/write/?x-success=drafts4%3A%2F%2F&key=YOUR_WC_KEY&repo=Blog&path=_posts/[[date]]-[[filename]].md&text=[[draft]]
    

## New link post

Used for saving the current draft as a new blog link post; this mean that we re-elaborate the draft content in order to match the Jekyll post structure. The filename will be the first line of the draft (with spaces replaced by character '-') prefixed by the date in the form YYYY-MM-DD.

It's composed by 10 action steps:

  * _Clipboard_: pick up the first line and save it in the system clipboard
    
    
    Template
      [[line|1]]
    

  * _Script_: save the first line a new tag named 'title', and generate the 'filename' tag
    
    
    var title = getClipboard();
    draft.defineTag("title", title);
    var filename = title.replace(/\ /g, "-");
    draft.defineTag("filename", filename);
    

  * _Clipboard_: then pick up the tag list (second line in the draft), and put it in the clipboard
    
    
    Template
      [[line|2]]
    

  * _Script_: save the content of the clipboard in a new tag named 'tags'
    
    
    draft.defineTag("tags", getClipboard());
    

  * _Clipboard_: then pick up the post link (third line in the draft), and put it in the clipboard
    
    
    Template
      [[line|3]]
    

  * _Script_: save the content of the clipboard in a new tag named 'link'
    
    
    draft.defineTag("link", getClipboard());
    

  * _Clipboard_: then pick up the lines from the fifth to the end of the drafts, and put it in the clipboard
    
    
    Template
      [[line|5..]]
    

  * _Script_: save the content of the clipboard in a new tag named 'content'
    
    
    draft.defineTag("content", getClipboard());
    

  * _Script_: this generate the new draft content, compliant with the Jekyll post structure
    
    
    var post = "";
    
    post  = "---\n";
    post  = "layout: post\n";
    post  = "title: "   draft.getTag("title")   "\n";
    post  = "link: "   draft.getTag("link")   "\n";
    post  = "tags: "   draft.getTag("tags")   "\n";
    post  = "---\n";
    post  = "\n";
    post  = draft.getTag("content");
    
    draft.content = post;
    commit(draft);
    

  * _URL_: finally we have all what we need to create the new post via Working Copy x-callback-url
    
    
    working-copy://x-callback-url/write/?x-success=drafts4%3A%2F%2F&key=YOUR_WC_KEY&repo=Blog&path=_posts/[[date]]-[[filename]].md&text=[[draft]]
    

## Upload image for article

It's pretty useful launching this action from here, because we can put in the clipboard the file name based from the form title. I use it for quickly have a link between the post and the images used.

Three steps for this:

  * _Clipboard_: pick up the first line and save it in the system clipboard
    
    
    Template
      [[line|1]]
    

  * _Script_: pick up the clipboard, replace spaces with '-', then save the result in the clipboard again
    
    
    var title = getClipboard().replace(/\ /g, "-");
    setClipboard(title);
    

  * _URL_: this will launch the default iOS Photos app. You can upload from that app running the 'Upload to Blog' workflow. Do you need a filename? Do you remember what we've put in the clipboard?
    
    
    photos-redirect://
    

## Add image link

This is useful for adding uploaded images to the post, directly in Markdown format. Unfortunately, Working Copy doesn't return the correct filename when you upload things, so this action needs to be saparated from the Upload one.

Two easy steps:

  * _Clipboard_: I save the UUID in the clipboard, so Workflow can pick it for adding the generated link to the current note
    
    
    Template
      [[uuid]]
    

  * _Run Workflow_: I run the 'Get image link' workflow. The input template wasn't used.
    
    
    Workflow
      Get image link
    

## Add file link

Like the image one, this action execute a workflow for picking up a saved file and generate the Markdown link. We need two different actions because the final URL (which is statically embedded in the workflow itself) is different for images and files.

  * _Clipboard_: I save the UUID in the clipboard, so Workflow can pick it for adding the generated link to the current note
    
    
    Template
      [[uuid]]
    

  * _Run Workflow_: I run the 'Get file link' workflow. The input template wasn't used.
    
    
    Workflow
      Get file link
    

## Edit Post

This action just run a workflow which present you the system Document Picker, open the file, and add its content to a new draft.

Just one step.

  * _Run Workflow_: run the 'Edit Post' workflow. Input template wasn't used.
    
    
    Workflow
      Edit Post
    

## Open Repository

Another simple one: just launch the Working Copy app (it's really convenient to do this without leaving the editor)

  * _URL_: this will launch Working Copy. Done
    
    
    working-copy://
    

## Pull repository

This action opens the Working Copy application, perform a pull from the repository master, then come back to Drafts. Usefull for ensuring to have the updated repository before starting the 'dirty work'

  * _URL_: this will launch Working Copy, perform the pull, and come back indipendently than if the operation are done
    
    
    working-copy://x-callback-url/pull/?x-callback-success=drafts4%3A%2F%2F&x-error=drafts4%3A%2F%2F&x-cancel=drafts4%3A%2F%2F&key=YOUR_WC_KEY&repo=Blog
    

## Commit changes

With this, you can commit some changes (like new posts or updated drafts). The draft content will be used as commit message, so this action will check if something was written in the draft.

  * _Script_: check if draft contain something, otherwise display an alert
    
    
    if (draft.content == "") {
      alert("You must provide a commit description.");
      stopAction();
    }
    

  * _URL_: launch Working Copy and perform the commit. Then come back
    
    
    working-copy://x-callback-url/commit/?x-callback-success=drafts4%3A%2F%2F&x-error=drafts4%3A%2F%2F&x-cancel=drafts4%3A%2F%2F&key=YOUR_WC_KEY&repo=Blog&path=&limit=999&message=[[draft]]
    

## Push to remote

This action complete the working habit: pick up what we have committed on our blog (repository), and send all changes to the master, putting our article online.

Just one step:

  * _URL_: executing the push on Working Copy, then come back
    
    
    working-copy://x-callback-url/push/?x-callback-success=drafts4%3A%2F%2F&x-error=drafts4%3A%2F%2F&x-cancel=drafts4%3A%2F%2F&key=YOUR_WC_KEY&repo=Blog
    

# Conclusion

So, finally a cool way of create new blog post in mobility.

I want to say thanks to all actors involved: [Agile Tortoise](http://agiletortoise.com) for giving us the great editor Drafts, [Workflow.is](https://workflow.is) for the awesome Workflow app and [Anders Borum](http://workingcopyapp.com) for the complete Working Copy app!

You must try those applications and services, are really great and usefull apps, also if you don't want to

![automate all the things](http://www.matteocappadonna.org/images/2015/05/Posting-with-Drafts-Working-Copy-and-Workflow-5.png)

like me :)
