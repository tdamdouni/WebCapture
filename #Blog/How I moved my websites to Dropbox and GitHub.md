# How I moved my websites to Dropbox and GitHub

_Captured: 2016-11-14 at 13:25 from [alexcican.com](https://alexcican.com/post/guide-hosting-website-dropbox-github/)_

A few months ago I cancelled my hosting and server accounts and moved all my websites to the cloud. I tried it **as an experiment**; never for a second I thought it would work this well. I did the switch out of impulse: I was pissed. I was pissed at the hosting companies charging so much, having such crappy support, and much downtime. I'm very glad I switched.

## Why I switched

Prior to the cloud, I was hosting my websites on a **VPS (Virtual Private Server) with a company called [Linode](http://linode.com)**. This company gives you a server _as is_ and you have to install the OS by yourself, maintain it, improve its performance, etc. I busted my chops trying to configure a fast server. After I was done, the server was running **CentOS + nginx + PHP-fpm + MySQL**, hosting my websites and Wordpress blogs.

The drop that spilled the cup came one day of February 2012, when all my websites (folders) **were deleted** somehow. Because I considered paying $20 per month for simply hosting my files was enough, I didn't enable the backup option (it was an extra $2 per month, if I remember correctly). So that day came, and I went straight to their support ticketing system. The dude that was assigned to me was not helpful at all and said there was nothing to be done. My last backup of the websites was in December 2011.

Pissed off, I **cancelled my account**, got my refund and didn't think back (or forward). Having been left only with my domain names, I had to do something (for _AlexCican.com_ alone, I was averaging around 700 unique visitors per day). That's when I made the decision to use the cloud.

## Why I switched to Dropbox and GitHub

I switched to these two services for a couple of reasons:

  1. **Free**. It's free and your account is created immediately. Free 2GB space for Dropbox and unlimited public repos for GitHub.

  2. **Easy to use**. Just drag-n-drop the file inside your Dropbox folder. The file is accessible anytime from anywhere (Dropbox website, desktop, laptop, mobile, tablet). Uploading to GitHub (known as _pushing_), is very simple: `commit`, add your message and `push` the changes.

  3. **Plenty of space**. I didn't need 20GB for my websites. The free 2GB of space offered by Dropbox was more than enough.

  4. **Backup**. Your files won't get lost/deleted. The extra layer of pushing the files to GitHub as well, offered double protection.

  5. **Restore**. In case you screwed up something, you can restore the file (as well as previous versions of it) and revert the changes. At no extra cost.

  6. **Uptime**. Previously, with my VPS, and going back even more, with my shared hosting, the uptime was good but I would experience downtime. Switching to the cloud, made my websites online with an uptime of [99.991%](http://37signals.com/svn/posts/3099-benchmarking-basecamps-uptime-against-five-other-web-apps).

  7. **Speed**. My websites are blazing fast. Dropbox and GitHub servers are optimised "out of the box" to be fast and reliable (pages are compressed and deflated).

  8. **Security**. In my effort to improve the performance of my server, who knows what vulnerabilities I uncovered, making my server hackable (maybe that's what happened on that day). I don't have to worry about this again. Both services come with SSL and free support included.

Let's get into **how I did** it.

## The specifics of Dropbox

If you want your files to be accessible by anyone, you have to move them into your "Public" folder. If you're using absolute paths for your website, I suggest you change it to relative paths. So from this:
    
    
    <a href="https://alexcican.com/web/file.html"></a>
    

change them to this:
    
    
    <a href="./web/file.html"></a>
    

Doing it this way, you can still access the website without having the domain name of the website pointing to the correct folder.

Next step is to **change the DNS** to point to the Dropbox folder (skip this if you're gonna use GitHub to host your online version of the site).

If you're using GoDaddy, login to _"Your account"_ and launch the _"Domains"_. Then, click on the domain name you want to edit and from the toolbar, select the _forward_ icon. Click _"Forward Domain"_ and insert in the popup input, the complete URL of the `index.html` from inside the Dropbox folder (to get the link: _right click on the file>Dropbox>Copy public link_).

![godaddy forward domain](https://alexcican.com/images/blog/assets/godaddy-forward-domain.jpg)

Wait a few hours and you should be able to access the website hosted on Dropbox via your domain name!

## Downsides of Dropbox

The big downside of hosting your website on Dropbox is that you can only **host static assets** (HTML, CSS, JS, images). No PHP. A solution to that was to use another service called [PHPFog](http://phpfog.com). I won't go into details in this tutorial about PHP.

The other downside I found was the **URL system**. On Dropbox, the URL of a file is something like:
    
    
    https://dl.dropbox.com/u/212143/public/website/file.html
    

This means that the Dropbox URL would be visible when navigating the website. I couldn't have something like:
    
    
    https://alexcican.com/file.html
    

unless I did a URL forwarding with masking from my DNS settings. This was not optimal because whichever page of the website I'd browse, it would show up only as:
    
    
    alexcican.com
    

To do this URL masking on GoDaddy, repeat the steps above for pointing the DNS record to Dropbox, but in the popup click on _"Advanced Options"_ and select the second option: _"Forward with Masking"_.

Lastly, if you have a large website, with many pages, you will find it difficult when you want to update the copyright of the page, for example. Because of the website being static, you would have to edit every single page of your website. Whereas with a dynamic website, you edit once (the `header.php` for example) and you're done.

## Specifics of GitHub

Searching for solutions to this issue I came across GitHub. On GitHub, you can host static websites with the option of adding your custom domain name (hence custom URLs) as well. There are two ways to do this:

1) You [create a repository](http://help.github.com/create-a-repo/) with your username and add `.github.com` at the end of the name. For example, if your username is _"sican"_ you create a repo:
    
    
    sican.github.com
    

2) or within an existing repo, you [create a new branch](http://learn.github.com/p/branching.html) called `gh-pages` and push the HTML files of your website in there.

To enable **custom domain names**, you just have to create a file named `CNAME`, in the root of the repo or branch, open the file with a text editor and add your domain name inside:
    
    
    alexcican.com
    

GitHub pages also supports **custom error pages**. Simply push a `404.html` file with your message in the root of the repo or branch.

Now it's time to change the **DNS settings** from GoDaddy to point to our GitHub page. Login to your account, launch the domains and click on the domain name you want to change. From that page (see screenshot above), go down and find the _"DNS Manager"_ section. Click on _"Launch"_.

You have to decide what domain name you'll be using. For a sub-domain like `http://www.alexcican.com` or `http://blog.alexcican.com` you would simply create a `CNAME` record pointing to `charlie.github.com`. If you are using a top-level domain like `https://alexcican.com`, you must use an `A (Host)` record pointing to `192.30.252.153` and another one to `192.30.252.154`. There's no need to add a `CNAME` record for top-level domains. [Read more in the documentation](https://help.github.com/articles/tips-for-configuring-an-a-record-with-your-dns-provider/).

## Downsides of GitHub

The first downside is that you need **special software** for interacting (gracefully) with your repositories. The best software to install if you're on a Mac is **[Git Tower](http://www.git-tower.com/)** and if you're on Windows you shoud be using **[SmartGit](http://www.syntevo.com/smartgit/index.html)**.

The other downside to GitHub is that unless you're a software geek, it **takes time** to _get it_. It's not intuitive and it's not drag-n-drop. After you went through the [help documents](http://help.github.com/) and learned how to setup stuff (repositories, branches, trees), it's very easy to use.

Lastly, the same with Dropbox, GitHub only **supports static assets** (HTML, CSS, JS, images).

## Liberation begins

> _"FTP-ing is so 1999"_ - everyone

Found an error on the website but you're on the move without your laptop? Edit the page that's hosted on Dropbox from your iPhone/iPad, save it and you're done. If you're on GitHub, `commit` the changes and `push` them to the repository. Job done!

_"Hold your horses, Johnny"_. There's a catch: a Git version control app for the iPhone/iPad **doesn't exist yet**, so you can't update your repository on those devices. [Textastic](http://www.textasticapp.com/) has it planned but I don't see it being completed any time soon.

There is a way around this but it involves Jailbreaking your iPhone/iPad and a great deal of hacking via the command line. Check out this [great tutorial](http://kreeger.posterous.com/textastic-git-a-match-made-in-jailbreaker-ner) showing you how to do it.

## Conclusion

There are some disadvantages to both systems:

  * **Dropbox:** **1)** doesn't support custom URLs **2)** can host only static files (HTML, CSS, JS) and **3)** making changes to a website with many pages is tedious

  * **GitHub:** **1)** requires special software and takes time to learn **2)** pushing changes difficult via mobile/tablet and **3)** can host only static files (HTML, CSS, JS)

But for me it works. For me, the **advantages outweigh the disadvantages**. I like my websites more (since they load faster and stay online longer), I feel more relaxed and I also sleep better at night (secure servers, backups exist). Lastly, I feel liberated since I can access my files anytime from anywhere (and edit them, almost from any device).

Next article I have scheduled, is a continuation of this one: _"[How I moved my blog to Dropbox"_](https://alexcican.com/post/blog-dropbox-scriptogram). Make sure you [grab the RSS feed](http://feeds.feedburner.com/alexcican) and you [follow me on Twitter](http://twitter.com/alexcican).

## [The lost art of Pricing and Negotiating](https://alexcican.com/post/pricing-negotiating/)
