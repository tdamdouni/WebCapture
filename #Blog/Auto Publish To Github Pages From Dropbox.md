# Auto Publish To Github Pages From Dropbox

_Captured: 2016-11-14 at 13:29 from [motyar.github.io](https://motyar.github.io/14/auto_publish_dropbox_github.html)_

## Dropbox integrated FREE static web hosting that supports custom domain.

I am sure you know [How static site can be hosted on Github pages for FREE](http://motyar.github.io/14/free_hosting_on_github.html), and [How to Update Github hosted websites](http://motyar.github.io/14/update_gihub_hosted_website.html).

In this post we are talking about how we can automate the process using Dropbox + A simple bash script + A cron job to Automate the process of updating these sites.

Here are few simple steps:

  * Login to **Dropbox** and setup sync to your machine. You can [register to Dropbox here](https://db.tt/DFVls9JO) (Get 2GB **FREE** storage).

  * [Setup a static site on _Github pages_ for FREE](http://motyar.github.io/14/free_hosting_on_github.html). Skip if you already have one.

  * cd to your Dropbox folder, and clone the repo.
    
        cd ~/Dropbox/  
    git clone git://github.com/usename/site.com.git
    

  * cd into that dir
    
        cd site.com
    

  * Create a new file (named 'update') and put this code into that.
    
        git add -A .
    git commit -m "Updated"
    git push origin gh-pages --force
    

  * Give it the power.
    
        chmod +x update
    

  * Make few changes and test if its working well, by running this command:
    
        ./update
    

  * Setup **cron job**. run
    
        crontab -e
    

  * Add this line
    
        * * * * *  cd /path/to/Dropbox/Dir/site.com && ./update
    

  * All set, Now your site.com folder is in syn with **Dropbox**, The **cron** is looking for changes and pushing to **Github pages**.

Let me know what you think, I am [@motyar](http://twitter.com/motyar) on Twitter.
