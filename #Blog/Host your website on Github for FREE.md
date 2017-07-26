# Host your website on Github for FREE

_Captured: 2016-11-14 at 13:30 from [motyar.github.io](https://motyar.github.io/14/free_hosting_on_github.html)_

## Any static site can be hosted on Github pages for FREE

Here are few steps to setup a website in one hour:-

  * Get a domain name (With 10% off on [BigRock](http://www.bigrock.in/?coupon=lobi.mobi)).
  * GoTo **DNS Managment** and add two A records. 
    
        www.domain.com   192.30.252.153 
    domain.com       192.30.252.154
    

  * Login to github.com and [create a new](http://github.com/new) **Repository** (Let's say named domain.com )

  * Clone that repo, using
    
        git clone git@github.com:username/domain.com.git
    

  * cd into that directory.
    
        cd domain.com
    

  * Create a branch named 'gh-pages'.
    
        git checkout --orphan gh-pages
    

  * Create the _CNAME_ file.
    
        echo 'domain.com'>CNAME
    

  * Create index.html file.
    
        echo 'Hello Pooh'>index.html
    

  * Push this file to github using:
    
        git add -A .
    git commit -m 'First commit'
    git push origin gh-pages
    

  * Test it by opening **http://username.github.io/domain.com**
  * If everything went well, your site should be live on **http://domain.com**

Need a dynamic website? Register on [DigitalOcean](https://www.digitalocean.com/?refcode=34a8a2d54244) FREE VPS.
