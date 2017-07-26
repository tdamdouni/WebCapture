# Updating My Website With Git and iOS

_Captured: 2016-03-15 at 19:12 from [www.jordanmerrick.com](https://www.jordanmerrick.com/posts/website-updates-with-git-ios)_

This website is powered by [Kirby](https://getkirby.com), a file-based CMS, running on a VPS with [Digital Ocean](https://m.do.co/c/4566b58d8638). Instead of the site's content being stored in a database, Kirby uses Markdown-formatted plain text files, so publishing a new blog post is as simple as adding a new text file to the content directory, after which it's immediately available on the site.

For a few years now, I've had Dropbox running on my server to sync the site's content directory so that I can easily publish or edit content on any device[1](https://www.jordanmerrick.com/posts/website-updates-with-git-ios) without needing to directly upload any files to the server. This has been especially useful in the past twelve months as the iPad became my primary computing device, so I was able to use any Dropbox-enabled iOS writing app, such as [1Writer](https://itunes.apple.com/us/app/1writer-note-taking-writing/id680469088?mt=8&at=10l64N), to write and publish blog posts. As soon as I finished a new post, I'd remove the `draft` tag and it would appear on the site.

I've never been fully happy with this workflow, despite it working successfully, because it doesn't easily fit in with how I develop and version control the site's source code, and content[2](https://www.jordanmerrick.com/posts/website-updates-with-git-ios), with Git. But thanks to the iOS Git client [Working Copy](https://itunes.apple.com/us/app/working-copy-powerful-git/id896694807?mt=8&at=10l64N), however, I've been able to use Git on my iPad and iPhone in the same way I would on my Mac and even deploy those changes to my server.

![A clone of my site's repository in Working Copy](https://www.jordanmerrick.com/media/working-copy.jpg)

> _Working Copy_

Working Copy is a fully featured Git client that brings with it a range of supported Git features and makes use of some great features of iOS that are often overlooked, such as Document Provider[3](https://www.jordanmerrick.com/posts/website-updates-with-git-ios).

Just like on my Mac, I've cloned my site's repository (named, unimaginatively, `jordanmerrick.com`) from GitHub to make whatever changes or additions I want (either a new blog post or a tweak to the source code), locally. Once I'm done, I commit and push the changes back to the default remote `origin` repository on GitHub.

###  Automatic Deployment From iOS

Since Working Copy supports many of Git's standard features, I've been able to take advantage of another common use for Git - automatic website deployment. This has eliminated my need for Dropbox syncing and even publishing site changes via SFTP from my Mac, replacing them both with a process that pushes changes to a secondary remote repository - my server.

To set this up, I followed Digital Ocean's guide on [setting up automatic deployment with Git](https://www.digitalocean.com/community/tutorials/how-to-set-up-automatic-deployment-with-git-with-a-vps). In a nutshell, I've configured a remote repository located on my server as a secondary remote for `jordanmerrick.com` within Working Copy, and on my Mac, named `live.`

On the server, a Git Hook[4](https://www.jordanmerrick.com/posts/website-updates-with-git-ios) listens for any changes that are received, which happens when a push has been completed to the `live` remote, and runs script that updates the files in `/var/www/html`. Basically, as soon as I push any changes to `live`, either from my Mac or iOS devices, the site is automatically updated.

Thanks to Working Copy and automatic deployment, whether I'm on my iPad, iPhone or Mac, I perform the same steps to make changes to my website and deploy them:

  1. Fetch and pull any changes from the remote `origin` repository (GitHub).
  2. Make any necessary changes, such as adding a new blog post or editing the site's layout. 
  3. Commit and push the changes back to `origin`.
  4. Push the changes to `live` (my server) so the site is then automatically updated using a Git Hook. 

Finally, Working Copy has a [comprehensive URL scheme](http://workingcopyapp.com/url-schemes.html) and supports `x-callback-url`, making it possible to create powerful workflows and actions with apps like [Workflow](https://itunes.apple.com/us/app/workflow-powerful-automation/id915249334?mt=8&at=10l64N) and [Drafts](https://itunes.apple.com/us/app/drafts-4-quickly-capture-notes/id905337691?mt=8&at=10l64N). The URL scheme is extremely powerful and not only can new files be created or edited, but commits and push actions can be performed as well. I plan on looking into the URL scheme in more detail soon, as I'd like to have a workflow that takes a blog post, creates the necessary text file, then commits and pushes the changes.
