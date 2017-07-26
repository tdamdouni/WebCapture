# iPad Coding for Web Development

_Captured: 2015-12-03 at 10:19 from [aaron.vegh.ca](http://aaron.vegh.ca/2014/01/ipad-coding-for-web-development/)_

![Photo](http://aaron.vegh.ca/wp-content/uploads/2014/01/photo.jpg)

On the [most recent episode](http://5by5.tv/amplified/85) of _Amplified_ (starting at about minute 37), Dan talked about how he does web development on an iPad. While clearly not his first choice of platform for development, the iPad is great for making touch-ups to existing sites. He outlined his process like so:

  * Symlink a Git repository to Dropbox
  * Use [Textastic](http://www.textasticapp.com) to edit the site, owing to the app's ability to edit files in Dropbox
  * If he wants to commit and push the Git repo to Github, for example, he'll use [Prompt](http://panic.com/prompt/) to shell into a remote Linux machine, also running Dropbox, and commit and push from there.

For the past year I've had a more-complete solution, using just one app on the iPad, which, in my opinion, is far more elegant than Dan's solution.

I give you [Diet Coda](http://panic.com/dietcoda/).

I can't believe I don't hear more people talking about this miraculous app. I [wrote about it in May 2012](http://aaron.vegh.ca/2012/05/coda-2-the-ipad-and-the-future-of-computing/), and it clearly bears repeating: if you do web development of any kind, Diet Coda should be on your iPad.

My piece from 2012 still stands. By taking advantage of Git's **distributed versioning system**, you can readily run multiple copies of your source code in different locations, merging them to the master repo. Which means you don't need Dropbox to edit your sites anywhere. You just need a system that can run Git. Here are the instructions that I wrote in the earlier article, to save you a click:

>   * Rather than point Diet Coda at my production server's live directory, I've created a Git clone in a home directory, and point DC there. I can therefore use Diet Coda to edit files remotely, but it's on a development branch of my application's code.
>   * When I've completed my edits, I switch to the Terminal, shell into that repository, and add/commit my changes to the repo. I can then push to the master branch.
>   * Again, from the home directory clone, I can issue a "cap deploy" and push my changes live. Essentially, I'm copying the development repo to the master repo on the same machine. But with Git goodness.

Because Diet Coda includes both a file system browser, text editor and Terminal application in one, you can remote into a Linux host, edit a development branch of your application, **in place on the server**, and then commit, push and deploy.

All from a single, gorgeous iPad app.

Having taken the time to re-read my piece from back in '12, I'm saddened that the shortcomings I discovered in Diet Coda haven't been addressed. At all. (I can even add another feature: the ability to sync site bookmarks between Mac and iPad versions!) I know Panic is a company that takes its time with development, preferring correctness over speed. And it's also quite possible that Diet Coda was nowhere near the success that it so richly deserves, making additional development hard to justify.

So let me do my bit and help send Panic a message: Dan Benjamin, get Diet Coda, and give the developers a chance to make it great.
