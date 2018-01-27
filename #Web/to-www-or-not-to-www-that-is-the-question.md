# To www or Not to www — That is the Question

_Captured: 2017-12-15 at 20:28 from [www.sitepoint.com](https://www.sitepoint.com/domain-www-or-no-www/)_

In the dim and distant days at the dawn of the web, those publishing a URL on offline media would add the 'www' prefix. It informed everyone you'd moved into the twenty-first century and owned a piece of prime real estate on the World Wide Web.

Fast forward to 2012. Everyone knows what the web is -- few organizations publish their URL with a preceding www. People understand that Google.com, Facebook.com, Twitter.com and SitePoint.com are websites.

Before we take this discussion further, your site **must** work with or without the www. For the sake of SEO and canonical/duplicate content issues, you should choose one domain option and redirect when the other is used. If you prefer naked domains, redirect to it when a visitor requests the fully-dressed www version. It's not difficult -- a three line Apache .htaccess file will suffice:
    
    
    RewriteEngine on
    RewriteCond %{HTTP_HOST} !^mydomain.com [NC]
    RewriteRule ^/?(.*)$ http://mydomain.com/$1 [L,R=301]
    

The question is: _which should you choose?_

Those in the pro-www camp point out that 'www' has not been deprecated. It's unambiguous, technically accurate and distinguishes the address from similar URLs for FTP, mail or other data types.

The anti-www camp point out that it's simply not necessary. No one's confused. URLs are shorter, easier to read and quicker to type.

"Ahh", says the pro-www lobby, "you're just being vain".  
"Well", responds the anti-group, "you're being finicky and my website looks far better than yours".  
"Does not", shouts pro, "Your site smells."  
And so on.

My opinion: _it doesn't matter_. Pick one and stick with it. Some word combinations look better with the www, some look better without. Ultimately, it's your personal branding preference and few people will notice or care.

Just remember that your site should load regardless of the URL and redirect when necessary. If you're breaking that rule, go and stand in the naughty corner and consider the consequences of your actions.

_Comments on this article are closed. Have a question about domains? Why not ask it on our [forums](http://www.sitepoint.com/forums/forumdisplay.php?140-General-Web-Development-amp-Application-Design-Issues?utm_source=sitepoint&utm_medium=link&utm_campaign=forumlink)?_

Craig is a freelance UK web consultant who built his first page for IE2.0 in 1995. Since that time he's been advocating standards, accessibility, and best-practice HTML5 techniques. He's written more than 1,000 articles for SitePoint and you can find him [@craigbuckler](http://twitter.com/craigbuckler)
