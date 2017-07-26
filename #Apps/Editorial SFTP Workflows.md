# Editorial SFTP Workflows

_Captured: 2015-06-14 at 14:24 from [www.macdrifter.com](http://www.macdrifter.com/2013/08/editorial-sftp-workflows.html)_

I'm back from vacation and so is this site. To get the life juices flowing, I'm sharing my SFTP workflows for Editorial.[1](http://www.macdrifter.com/2013/08/editorial-sftp-workflows.html)

I use [this first one to edit posts](http://editorial-app.appspot.com/workflow/5294595164340224/ZNR1UkLlJDs) I've already uploaded to my host. It reads the first 20 text files in my Pelican raw text file directory and shows them sorted by modification time stamp. Tapping one in the list downloads it to the Editorial local file storage for editing.

![](http://www.macdrifter.com/uploads/2013/08/2013-08-25%20085046_600px.png)

[This next one](http://editorial-app.appspot.com/workflow/5764017909923840/swIKe94JsZ0) can then upload the file to my server over SFTP. I posted [my workflow](http://www.macdrifter.com/2013/08/ftp-upload-with-editorial.html) for simple FTP upload but a couple of you jackals wanted SFTP uploads instead. This new workflow uses the Python Paramiko module to do just that. It overwrites any file with the same name, which is what I want to do.[2](http://www.macdrifter.com/2013/08/editorial-sftp-workflows.html)

This combination of workflows gives me the ability to edit files remotely on my web server. Pretty nice for a little iOS text editor.

  1. Here's a quick tip: If you are not into Editorial for iPad, then this site will be pretty boring over the next few weeks. If you are into Editorial, then we should probably exchange friendship-bracelets. [↩](http://www.macdrifter.com/2013/08/editorial-sftp-workflows.html)

  2. As with most everything that's free on the Internet, these workflows come with no serious support. If the problem is interesting or something that I might use, I'll take a stab at it. But really, you're on your own. That's the great thing about Editorial. You can actually mess with it. [↩](http://www.macdrifter.com/2013/08/editorial-sftp-workflows.html)
