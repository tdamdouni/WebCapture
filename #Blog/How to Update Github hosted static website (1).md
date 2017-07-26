# How to Update Github hosted static website

_Captured: 2016-11-14 at 13:29 from [motyar.github.io](https://motyar.github.io/14/update_gihub_hosted_website.html)_

## By just typing a single command

I have moved few of my websites to **Github Pages**. Check the [blog post about it](http://motyar.github.io/14/free_hosting_on_github.html).

In this post we are talking about **how to update** these sites.

Here are few steps:

  * You need to clone the repo, only the gh-pages branch.
    
        git clone git@github.com:username/domain.com.git -b gh-pages
    

  * Edit, Remove or Add files and data you want to.

  * Create a new file named 'update' with these contents
    
        git add -A . 
    git commit -m "Updated" 
    git push origin gh-pages
    

  * Give it permissions by runing this command
    
        chmod +x update
    

  * Run this script
    
        ./update
    

  * Done, Updated!!
