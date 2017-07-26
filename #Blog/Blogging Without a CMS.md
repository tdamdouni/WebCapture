# Blogging Without a CMS

_Captured: 2015-11-24 at 23:41 from [jeffreykishner.com](http://jeffreykishner.com/posts/blogging-without-cms-md.html)_

If you have read my blog long enough, you'll see that I change subdomains and/or directories on *.jeffreykishner.com fairly frequently, and the change in stylesheets is nearly as frequent. Perhaps I'm just fickle. For my personal blog, I've used the following content management systems:

Also for a while I was just using the markdown editor [StackEdit](https://stackedit.io) to write my entries and post them via SSH.

Since I've learned of [Markdeep](http://casual-effects.com/markdeep/) I've been won over by the ease of use. It's basically an on-the-fly markdown-to-HTML script, so I can upload a markdown file to my server (including one piece of javascript) and a reader will see the HTML instead of the text file.

Of course, the problem without using a content management system is that I've had to manually update my home page and RSS feed. For many months, I've just added a new line to index.html in a text editor via an FTP program like Cyberduck. And I was using a script I wrote to generate a new RSS `<item>` and then I manually added that text to an XML file.

I'm still doing this while using Markdeep, but I'm not bothering to include a `<description>` in the RSS feed. I know this is an inconvenience for subscribers, but currently it feels like too much work to convert the markdown to HTML and then do xhtml substitutions for some characters so that the feed doesn't break.

I kinda like the simplicity of the system, even though it requires more work. On the other hand, I am not reliant on a CMS and all the headaches that can come with one. Everything's just static html.

The only downside I can see is that I have no consistent look (or _braaand_). But I'm not selling anything (even myself), and I hope that the content alone will suffice.
