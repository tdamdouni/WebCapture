# How to Install HTTPS on Your WordPress Site – The Easy Way

_Captured: 2017-08-03 at 18:08 from [dzone.com](https://dzone.com/articles/how-to-install-https-on-your-wordpress-site-the-ea?oid=twitter&utm_content=buffera590b&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

HTTPS (HTTP + SSL) is a transfer protocol that ensures a secured connection between the client and the server. This article shows how to easily add HTTPS support to any WordPress website in order to make visitors more secure and enhance the average quality of your website.

## 1\. Get Your SSL Certificate From Your Host

The first thing to do is to get in touch with your hosting company and ask them to install SSL on your site. Most hosts will ask you to pay an annual fee for it, ranging from $19 to $99 a year.

Good news if your website is hosted on [Vidahost](https://catswhocode.com/go/vidahost.html), [SiteGround](https://catswhocode.com/go/siteground.html), [WPEngine](https://catswhocode.com/go/wpengine.html) or [DreamHost](https://catswhocode.com/go/dreamhost.html), they can provide you an SSL certificate for free, and assist you with the whole process of going secure.

Further reading: [Characteristics of quality WordPress hosting](https://www.catswhocode.com/blog/quality-wordpress-hosting)

## 2\. Update WordPress URL

Once your host has added SSL on your account, your website should be accessed through the URL `https://yourwebsite.com`. If you can access your site through this address, it's time for you to start setting up WordPress for HTTPS.

The first step to do so is super easy. Just log into your WordPress dashboard and visit the _Settings > General_ section.

![](https://www.catswhocode.com/blog/wp-content/uploads/2017/06/https-wordpress1.jpg)

Simply update the **WordPress Address (URL)** and **Site Address (URL)** to HTTPS, as shown in the image below. Save the settings and you'll be logged out of your WordPress dashboard.

## 3\. Force SSL Admin in wpconfig.php

Use your FTP to edit the `wp-config.php` file, located at the root of your WordPress install. Append the following:

This constant easily enables and enforces WordPress administration over SSL, adding extra security to your WordPress dashboard.

## 4\. Redirect HTTP to HTTPS

At this stage, HTTPS is already working on your website. But there are a few things left to do. The first one is to redirect the `http` traffic to `https`.

Over the years, many websites have linked to your site using `http://`, so there are gonna be a lot of people still accessing the `http` version of your site.

So what you have to do is to redirect all the traffic to the secure, https site. This is done by using the `.htaccess` file, located at the root of your WordPress install. Open the file and add the following in between the `<IfModule mod_rewrite.c>` tag:

Please note that `.htaccess` redirects can be a bit tricky, and sometimes will work perfectly on one host and not on another.

If the code above doesn't function properly, simply revert the changes and get in touch with your hosting provider support. They'll be happy to provide you the correct `.htaccess` redirect that works on their servers.

## 5\. Make All Your Links HTTPS

Alright, now we have HTTPS properly set up, and the HTTP traffic is automatically redirected to the HTTPS site. But there's one more thing to do before we can call it a day: replacing all HTTP links on your site with their HTTPS equivalent. This is done in two distinct parts:

### Hardcoded Links in Theme Files

Let's start with your theme. If you're using a [WordPress theme](http://catswhocode.com/go/themeforest.html) from the WP repository, from [ElegantThemes](http://catswhocode.com/go/elegantthemes.html) or any other free/premium theme shop and haven't made any changes to it, you have nothing to do. However, if you're using a custom theme or a theme that you modified yourself, there might be some HTTP links hard coded somewhere.

Have a look in your theme files (especially `header.php` and `footer.php`) and update each internal hardcoded HTTP link to its HTTPS version.

### Internal Links in Database

When writing posts or pages, there is a strong chance that you inserted HTTP internal links. In order to update your links, you can edit each post and page, but this will be a very time-consuming task.

Instead of dealing with so much hassle, there's a super simple and fast solution to update all internal links in your database: use SQL queries.

Further reading: [Using SQL to manage WordPress: The definitive guide](https://www.catswhocode.com/blog/using-sql-to-manage-wordpress-the-definitive-guide)

There are several ways to run SQL queries. Most of you probably have a cPanel installed on your server. This is the case if your host is [Vidahost](http://catswhocode.com/go/vidahost.html), [HostGator](http://catswhocode.com/go/hostgator.html) or [InMotion Hosting](http://catswhocode.com/go/inmotionhosting.html), for example.

To access phpMyAdmin from cPanel, simply log into cPanel and click the **phpMyAdmin** icon in the **Databases** section.

Make sure to backup your database, in case something goes wrong. Once done, run the following two queries:

Here you go. The queries have updated all your internal links from HTTP to HTTPS. Now, your WordPress site is fully SSL compliant and you should see a green padlock in your address bar, showing your visitors that your site is fully secure.
