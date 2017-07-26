# Creating Better, Faster And More Optimized WordPress Websites

_Captured: 2017-06-07 at 12:16 from [www.smashingmagazine.com](https://www.smashingmagazine.com/2017/06/better-faster-optimized-wordpress-websites/)_

Today, too many websites are still inaccessible. In our new book _Inclusive Design Patterns_, we explore how to craft **flexible front-end design patterns** and make **future-proof and accessible interfaces without extra effort**. Hardcover, 312 pages. [Get the book now!](https://shop.smashingmagazine.com/products/inclusive-design-patterns?utm_source=magazine&utm_campaign=inclusive-design-patterns&utm_medium=html-ad-content-1)

Consumers typically have their own experiences when it comes to web hosting and their own opinions. If you search Google for reviews for any web hosting provider you'll find dozens of results. Usually, there are a lot more negative reviews than there are positive ones. I thought I would flip that around and share some WordPress hosting challenges **from the perspective of the WordPress host** and how I frequently solve them.

I have compiled a list of bad web practices and recommendations on what not to do on your site, based on thousands of hours of customer interactions, support tickets, and troubleshooting I experience on a daily basis. Some of these range from beginner mistakes to more complex issues. A lot of these can be the difference between having a successful WordPress site and a failure. Picking the right web host is very important. But your decision also goes hand-in-hand with educating yourself on how to best optimize your WordPress site.

![Optimizing WordPress sites.](https://www.smashingmagazine.com/wp-content/uploads/2017/05/wordpress-host-800w-opt.png)[1](https://www.smashingmagazine.com/2017/06/better-faster-optimized-wordpress-websites/)

> _Optimizing WordPress sites. (_

I often observe that even seasoned developers focus on what they are good at, which is building solutions and sometimes neglect or don't have time to learn the latest optimization practices. Whether you are a WordPress user just getting started or an experienced developer, the following tips will help you create better, faster and more optimized WordPress sites.

One of the most important things people need to realize is that switching hosts doesn't automatically fix certain problems. If your WordPress site is having code issues or compatibility problems with specific plugins, this is still going to occur no matter where you host your site.

![Code Issues.](https://www.smashingmagazine.com/wp-content/uploads/2017/05/code-800w-opt.png)[7](https://www.smashingmagazine.com/2017/06/better-faster-optimized-wordpress-websites/)

> _Coding issues aren't magically fixed. (_

A managed host will provide as much assistance as they can, but won't debug an issue with a bad plugin or code for you. It is not the WordPress host's responsibility to write PHP code, create or edit custom functions for plugins or themes, integrate or fix external services or performing website content updates. This is where you would **need the assistance of a seasoned WordPress developer** to dig into it and make a determination as to what the issue is. There are many places to find WordPress specific developers, such as [Codeable](https://codeable.io/) or [toptal](https://www.toptal.com/wordpress).

Many hosts also have third-party agency partners and developers they can refer you to for solving these problems. If there is an issue with a specific plugin, you should also reach out to the developer yourself.

I could say this a thousand times. **Never use production (live) sites for development work!** Nearly all of the major managed WordPress hosts now have staging/development environments and this is certainly for good reason. It prevents critical downtime caused by users breaking things while testing on their live site. This is typically the scenario that causes what some call the [white screen of death](https://codex.wordpress.org/Common_WordPress_Errors#The_White_Screen_of_Death).

If you don't want to use a staging environment you can always test and [develop locally](https://developer.wordpress.org/themes/getting-started/setting-up-a-development-environment/) using what some call a LAMP or LEMP stack. These stand for Linux, Apache/Nginx (sounds like Engine-X), MySQL, and PHP. Tools like WAMP and [MAMP](http://www.smashingmagazine.com/2011/09/28/developing-wordpress-locally-with-mamp/) all make configurations for local development quite easy.

These tools have all improved and evolved over time, but there are also other challenges and problems that arise with local development, such as the environment not exactly mimicking your live site. First of all, you have to figure out how to push your changes from local back to production without overwriting existing data or breaking your site. Depending on your setup this process might even add another layer of complexity. Other complications could also include having to mess with conflicting ports or errors from a different version of MySQL are all things that could pop up.

To avoid some of these complications, I recommend using tools like [DesktopServer](https://serverpress.com/) and [Local](https://local.getflywheel.com/), which are both built solely for the purpose of speeding up your workflow when working locally with WordPress. These include streamlined ways to push things back to production and even have additional tools and features such as WP-CLI and multisite support built right in. Having multisite support alone can be priceless as working with large local installations can sometimes be downright tricky.

![LEMP Stack](https://www.smashingmagazine.com/wp-content/uploads/2017/05/lemp-stack-800w-opt.png)[16](https://www.smashingmagazine.com/2017/06/better-faster-optimized-wordpress-websites/)

> _LEMP stack. (View large version)_

Staging and local testing environments can help you find problems before they break your site.

People that are either unfamiliar with WordPress or don't know the basics of how code works should not be editing files. One of the most common reasons that WordPress sites go down (or see that "white screen of death") is someone editing a PHP file directly from the appearance editor in the dashboard. Also, you shouldn't be editing your live site to begin with as we mentioned earlier.

![WordPress appearance editor.](https://www.smashingmagazine.com/wp-content/uploads/2017/05/wordpress-appearance-editor-800w-opt.png)[18](https://www.smashingmagazine.com/2017/06/better-faster-optimized-wordpress-websites/)

> _Editing code in the WordPress Appearance editor. (_

A good administrative recommendation is to place the following code in your wp-config.php file, removing the `edit_themes`, `edit_plugins`, and `edit_files` capabilities for all users. This can help prevent users from breaking the site by hacking away at the code.
    
    
    define('DISALLOW_FILE_EDIT', true);

Taking this process one step further, remove the functionality for clients to update themes or install plugins. Place the following code in your wp-config.php file to restrict these capabilities.
    
    
    define('DISALLOW_FILE_MODS', true);

**Note**: _The above code will also disable the plugin and theme file editor, so you don't need both if you want to disable everything mentioned above. See [WordPress Codex](https://codex.wordpress.org/Editing_wp-config.php#Disable_Plugin_and_Theme_Update_and_Installation) for more information._

It's understandable that you are trying to save a few bucks or cut corners, but don't do it with your themes and plugins. WordPress might be the foundation of your site, but the themes and plugins are the glue that holds it all together. Try to **stick with reputable developers** when choosing plugins and look through the ratings and reviews beforehand. Look for a history of the developer providing good product support. With over 50,000 plugins in the [repository](https://wordpress.org/plugins/), this can sometimes be an overwhelming task, so do your research beforehand.

![WordPress plugin repository.](https://www.smashingmagazine.com/wp-content/uploads/2017/05/wordpress-plugin-repository-800w-opt.jpg)[22](https://www.smashingmagazine.com/2017/06/better-faster-optimized-wordpress-websites/)

> _Finding a plugin in the WordPress repository. (Image credit: WordPress.org) (View large version)_

It is very common for outdated and bad themes/plugins to more easily get infected with malware, inject bad links on your site, pharma, etc. According to recently published [research by WP Loop](https://wploop.com/old-outdated-wordpress-plugins/), nearly 50% of the plugins in the repository haven't been updated in over 2 years. That is both shocking and frightening!

![Out of date plugins.](https://www.smashingmagazine.com/wp-content/uploads/2017/05/wordpress-plugins-not-updated-800w-opt.png)[26](https://www.smashingmagazine.com/2017/06/better-faster-optimized-wordpress-websites/)

> _Statistics on plugins that haven't been updated. (Image credit: WP Loop) (View large version)_

Another thing to be on the lookout for is a third-party source that is bundling up premium plugins into one low bundled price. If you purchase these, first off, you aren't supporting the developer, so shame on you. Second, you are relying on the 3rd party to grab the latest updates for you which is not good.

Relying on updates for a bundled plugin is actually a huge problem for WordPress users who purchase things via online marketplaces such as ThemeForest. Many theme developers bundle additional plugins like Revolution Slider or Visual Composer. The problem is that when [vulnerabilities are discovered](https://www.themepunch.com/products/old-revolution-slider-pre-4-2-vulnerabilty-explained/), the consumer is left waiting for an update from the theme developer, even though the plugin might have been patched the next day. This leaves a lot of sites wide open for hackers and site owners extremely vulnerable.

Watch out for multiple [Admin AJAX](https://kinsta.com/blog/admin-ajax/) calls from your WordPress site and plugins that may utilize AJAX. For example, the WordPress Heartbeat API uses `/wp-admin/admin-ajax.php` to run AJAX calls from the web-browser. A lot of times these are un-cachable requests. High usage of this file sometimes occurs during traffic spikes, CPU load, and can bring your site to a crawl. It is almost like you are launching a distributed denial-of-service (DDoS) attack against yourself!

![Admin AJAX calls](https://www.smashingmagazine.com/wp-content/uploads/2017/05/high-admin-ajax-usage-800w-opt.png)[31](https://www.smashingmagazine.com/2017/06/better-faster-optimized-wordpress-websites/)

> _High admin-ajax.php usage. (Image credit: Pingdom) (View large version)_

If there are 3rd party plugins that utilize admin-ajax.php, make certain they are doing it in the correct way. You can usually **look at the HTTP POST request action** and quickly determine, based on the name, what plugin might be causing it. For example, one I have seen is, `get_shares_count`. Which turned out to be a popular social media sharing plugin which was hammering admin-ajax.php. These simply multiply on high-traffic sites.

However, AJAX does load after the page loads. So just because you see this in a speed test, doesn't necessarily always mean it is a bad thing. It is also an interesting comparison to note the [performance differences](https://deliciousbrains.com/comparing-wordpress-rest-api-performance-admin-ajax-php/) between admin-ajax.php and the WordPress REST API.

Most high-traffic websites rely on advertising for their income. Removing 3rd party advertisements altogether is not an option. However, it is important to keep the number of 3rd party networks to a minimum and realize just how much load some of these tack onto your website.

Here's a quick comparison of how ad networks can affect your WordPress site.

Test Parameters: I added three 300×250 Google Adsense ads on a development/staging site running the default twenty sixteen theme and tested the speed before and after.

  * First view: 1.372s load time
  * Repeat view: 1.013s load time

Here is the content breakdown by connections:

![Before AdSense.](https://www.smashingmagazine.com/wp-content/uploads/2017/05/content-breakdown-800w-opt.jpg)[36](https://www.smashingmagazine.com/2017/06/better-faster-optimized-wordpress-websites/)

> _Content breakdown before running Google AdSense. (Image credit: WebPageTest) (View large version)_

  * First view: 4.103s load time
  * Repeat view: 3.712s load time

Here is the content breakdown by connections:

![After AdSense.](https://www.smashingmagazine.com/wp-content/uploads/2017/05/ad-network-content-breakdown-2-800w-opt.jpg)[40](https://www.smashingmagazine.com/2017/06/better-faster-optimized-wordpress-websites/)

> _Content breakdown after adding Google AdSense. (Image credit: WebPageTest) (View large version)_

By simply adding 3 Google AdSense ads, 6 additional connections were instantly added. **The WordPress site with ads is 2.7x slower than the one without.** This is mainly due to extra DNS lookup times and much heavier use of JavaScript on the page. This gives you a small picture of what can happen when large-scale sites simply embeds 10 ads on a single page. No matter how fast your WordPress host is, it won't fix delays from 3rd party ad network connections.

Here is another example below taken from New Relic monitoring on a site with a massive amount of HTTP requests to external ad networks, causing a heavy load on the WordPress site.

![Ad Heavy.](https://www.smashingmagazine.com/wp-content/uploads/2017/05/external-ad-network-1-800w-opt.png)[43](https://www.smashingmagazine.com/2017/06/better-faster-optimized-wordpress-websites/)

> _Heavy load due to advertising network. (_

There were so many requests that the app server failed to load at all. The site was simply unavailable trying to load all the external requests.

![App Server.](https://www.smashingmagazine.com/wp-content/uploads/2017/05/external-ad-network-2-800w-opt.png)[45](https://www.smashingmagazine.com/2017/06/better-faster-optimized-wordpress-websites/)

> _Web transactions time on app server. (_

Another good example of this is with [Huffington Post's](http://www.huffingtonpost.com/) website. If you run a speed test on their website you will see massive amounts of HTTP requests to ad networks. This graph shows what I saw in a quick test. ([speed test](https://www.webpagetest.org/result/161208_H7_61C7/)). They had a load time of over 13 seconds!

  * First view: 15.908s load time / Total HTTP requests: 221
  * Repeat view: 13.957s load time / Total HTTP requests: 66

However, simply removing advertisements might not be a realistic solution. Many sites rely on them for their income and livelihood. In this case, it's important to dive deeper into your scripts and ensure they are loading in the most optimal way. You can use [async](https://www.keycdn.com/support/prefer-async-resources/) or defer on your scripts to help prevent them from interrupting the rendering of your page loads. When it comes to performance there is always a balancing act of [perceived performance](https://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/) vs. that of actual performance.
    
    
    src="example.js" async
    
    
    src="example.js" defer

Patrick Sexton also has another popular method for [deferring JavaScript](https://varvy.com/pagespeed/defer-loading-javascript.html). WordPress version 4.1 and higher has a [filter](http://matthewhorne.me/defer-async-wordpress-scripts/) in which you can more easily add async and defer attributes to your scripts.

As a general rule, if you are relying on external services you will also want to cache the responses. Why? Because issues like the white screen of death can occur if you don't. Every external service you add to your WordPress site should be from a trusted and reliable source. After all, if they go down, it is then affecting your entire site or business operations. If you use vanity URLs generated from your WordPress site and use them in social networks, those will cease to function as well.

There are thousands of articles around the web that give "tips" on how to speed up and optimize your WordPress site. But an even **worse scenario is when users over optimize their websites.** Yes, this happens a lot more frequently than you might think. It is common for WordPress site owners to think that by adding more of something it will double their speed.

Below I've listed a few problem scenarios that I see on a regular basis:

Unlike typical VPS or standalone servers, a lot of managed WordPress host providers have their own caching, which is done at a server-level (like Redis or Memcache). Most providers do not allow caching plugins because this can cause all types of issues, most commonly 502 gateway errors. Trying to "cache the cache" as I call it is never a good idea.

![Bad optimizations.](https://www.smashingmagazine.com/wp-content/uploads/2017/05/facepalm-800w-opt.png)[53](https://www.smashingmagazine.com/2017/06/better-faster-optimized-wordpress-websites/)

> _Bad optimizations which makes things worse. (_

Plugins like WP Rocket and Cache Enabler are great, but they are designed for servers which need additional assistance speeding up your site. Read more about [object caching](https://www.scalewp.io/object-caching/), which is a popular form of server-level caching used by many today.

[Content Delivery Networks](https://www.incapsula.com/cdn-guide/what-is-cdn-how-it-works.html) (CDN) have been shown to greatly decrease load times and latency when serving up content across different geographical regions, but only when setup correctly. One of the most popular providers is Cloudflare. Cloudflare is technically a fully proxy service and is slightly different than a normal CDN provider as you are pointing your entire DNS over to them, not just your assets.

Typically I see users add CloudFlare, and then they go add KeyCDN or MaxCDN along with it. This is usually because they read blog posts from someone recommending that they should go install this new service right away, and they simply go do it. They don't think about their existing setup. While this combination can work in certain scenarios, typically this ends up in a giant mess. In most cases it is better to either use CloudFlare or use a 3rd party CDN provider, each of which have their own advantages and disadvantages.

You want to dominate search engine ranking positions (SERPs) right? Well, adding 3 SEO plugins won't help you accomplish that goal. In fact, there are a lot of compatibility issues that popup when trying to run All In One SEO, Yoast, and other SEO plugins together. Such as outputting [duplicate meta tags](https://wordpress.org/support/topic/can-one-use-both-all-in-one-seo-and-yoast-plugin-at-the-same-time/). Adding more plugins doesn't mean it will improve your current SEO situation.

Even if you aren't an advanced WordPress expert, common performance issues are fairly easy to diagnose. I recommend using [WebPageTest](https://www.webpagetest.org/) for seasoned WordPress users as it supports the latest protocols such as HTTP/2. However, for those that aren't as webperf savvy, then [Pingdom](https://tools.pingdom.com/) does a good job. A simple [waterfall analysis](https://kinsta.com/blog/pingdom-speed-test/) can tell you quite a bit, such as learning if you have unnecessary redirects, missing files, too many DNS lookups or if a certain script or 3rd party ad network is bogging your site down.

Take a quick glance at the performance insights and response codes and you can see where to start addressing these performance issues on your WordPress site.

![Pingdom Insights.](https://www.smashingmagazine.com/wp-content/uploads/2017/05/pingdom-insights-800w-opt.jpg)[61](https://www.smashingmagazine.com/2017/06/better-faster-optimized-wordpress-websites/)

> _Pingdom performance insights. (Image credit: Pingdom) (View large version)_

Plain and simple, modifying WordPress core files to make some of your code work is [simply a bad idea](http://websynthesis.com/dont-hack-wordpress-core/), especially on a live production site. Doing this can open up your WordPress site to security vulnerabilities. Unless you have an active update procedure in place (which many don't) you will lose your modifications with each new version of WordPress that is released. Instead, you should take advantage of WordPress tools and features such as well-developed 3rd party plugins, child themes, custom post types and hooks.

PHP 7 and HHVM have been shown to be incredibly fast when it comes to [boosting WordPress performance](https://make.wordpress.org/core/2015/09/10/wordpress-and-php7/). And of course it's always satisfying to be using the latest and greatest, but first you need to make sure your site is compatible before simply hopping on the bandwagon. For example, If you are upgrading from PHP 5.6 to 7, you should test all functionalities of your WordPress site in a staging environment or locally to ensure there aren't any compatibility issues. One out of date plugin you rely on that doesn't work with PHP 7 could mean that you should wait before moving.

One of the easiest ways for a large WordPress site to slow down is when the database hasn't been optimized. Simple tasks like cleaning up old WordPress revisions or cleaning up unused tables, can help prevent some of this slowdown. However, I've found that a lot of older sites are still using the MyISAM storage engine in their database. Recently InnoDB has shown to [perform better](http://dimitrik.free.fr/blog/archives/2015/12/mysql-performance-revisiting-innodb-vs-myisam-with-mysql-57.html) and be more reliable. A big reason is to use InnoDB over MyISAM is the lack of table locking. This allows your queries to process faster.

![Database performance.](https://www.smashingmagazine.com/wp-content/uploads/2017/05/database-800w-opt.png)[67](https://www.smashingmagazine.com/2017/06/better-faster-optimized-wordpress-websites/)

> _Database performance. (_

You can convert your tables with just a few simple steps. Ensure you are running MySQL 5.6.4 or higher and that you always take a backup as a precautionary measure before making changes to your database. This example is using the `wp_comments` table. Simply run the ALTER command to convert it to InnoDB storage engine.
    
    
    ALTER TABLE wp_comments ENGINE=InnoDB;

If you are running on a newer version of phpMyAdmin you can also click on a table, click into the "Operations" tab and change the storage engine manually.

![InnoDB.](https://www.smashingmagazine.com/wp-content/uploads/2017/05/innodb-800w-opt.png)[69](https://www.smashingmagazine.com/2017/06/better-faster-optimized-wordpress-websites/)

> _Changing from MyISAM to InnoDB. (_

Another easy optimization technique is to **disable or modify the number of revisions** you keep in your database. You can add the following to your wp-config.php to disable them completely.
    
    
    define('WP_POST_REVISIONS', false );

Or simply modify the number of revisions that are kept per post/page:
    
    
    define('WP_POST_REVISIONS', 3);

I've seen many sites with over 200 revisions per post, which adds up very fast across large sites. Unless your host has an internal optimization in place, the default in WordPress is to store unlimited revisions. This is why it's so important to check and verify the settings with your own eyes.

If your current site has a lot of revisions already, you can run the following query in phpMyAdmin to clean them up:
    
    
    DELETE FROM wp_posts WHERE post_type = "revision";

If you aren't comfortable running a query, use plugins such as WP-Optimize to help you cleanup the revisions.

There is a huge problem I see within the WordPress community. People go out and buy a multipurpose theme and then only utilize 1% of the theme's features or none at all. Many see fancy sliders and attractive portfolio pages on the demos that entices them to make the purchase. But in reality, these might be things they never actually use. They could have purchased a more minimal theme and saved a ton of time on digging through confusing options and their site would be a lot faster from the onset. Many of these additional features add load time.

I'm not saying all multipurpose themes are bad, in fact with a lot of customization they can sometimes run fast. Here is an example of an Avada theme that clocks in under 700ms. ([speed test](https://tools.pingdom.com/#!/eaL5Ny/http://arizonamri.com))

![Fast WordPress theme after optimization.](https://www.smashingmagazine.com/wp-content/uploads/2017/05/avada-theme-fast-800w-opt.jpg)[72](https://www.smashingmagazine.com/2017/06/better-faster-optimized-wordpress-websites/)

> _Optimized multipurpose WordPress theme. (Image credit: Pingdom) (View large version)_

However, that requires a lot of knowledge and time to optimize the existing theme. For basic WordPress users, if they aren't utilizing a lot of features a more minimal theme is the way to go. Don't let all the shiny bells and whistles fool you. In most scenarios, fancy sliders and visual editors just slow your site down.

If you know your way around your WordPress files and the wp-config.php file, then the error log is your friend. By checking it on a regular basis you can save yourself a lot of headaches and probably learn a thing too. Not many users even bother checking this before reaching out to their host for help. With a few simple tweaks in your wp-config.php file you can enable logging, which by default is saved to /wp-content/debug.log.

![Log file.](https://www.smashingmagazine.com/wp-content/uploads/2017/05/log-file-800w-opt.png)[75](https://www.smashingmagazine.com/2017/06/better-faster-optimized-wordpress-websites/)

> _Error log is your friend. (View large version)_
    
    
    define( 'WP_DEBUG_LOG', true );
    
    
    define( 'WP_DEBUG_DISPLAY', true );

You would think this is common sense by now, but Google is here for a reason folks. Don't be afraid to Google your answer. The internet is full of solutions and tips. Within a few minutes of searching you can easily solve a majority of your issues. Typically questions like "how to change your GoDaddy DNS" or "how to use SFTP" are things that can be easily found on Google.

There are great resources available online such as <http://wordpress.stackexchange.com/> and the [WordPress Codex](https://codex.wordpress.org/). Not to mention the hundreds of blogs with tutorials on just about any WordPress scenario that exists.

But not all of this is squarely on the shoulders of the user either. A responsible WordPress host should have an in-depth knowledge base with a good UI. Not only to cut down on their own support tickets but to help the user as well.

SpashData compiles a list of the most widely used leaked passwords (over 2 million) every year. Not surprisingly, in 2015 the [most popular password](https://www.teamsid.com/worst-passwords-2015/) still being used was "123456 (the same as 2014)." This can be very frustrating for web hosting providers, as the bad practice of using easy to guess passwords puts the client's WordPress site in a state of "always one step away from being hacked." While storing passwords locally in a tool like KeePass is probably one of the safest routes, encouraging users to use services like LastPass or Passpack will at least help harden their passwords, even if they are stored in the cloud. A hashed and secured password in the cloud is always much more secure than using "123456."

Unfortunately, unlike a static website which you have more control over, when it comes to WordPress many are at the mercy of the plugin and theme developers. Let's be honest, not all developers care about performance. There are a lot of plugins that simply load their scripts on all pages even though it might only be used on one. If you multiply this by 35+ plugins you can end up with a lot of unnecessary bloat that slows down your site.

One example of this can be seen with the popular Contact Form 7 WordPress plugin. As shown below, it is loading it's CSS file on the homepage of our dev site, as well as it's JavaScript file. Even though I'm not utilizing any contact form.

![Script loading sitewide.](https://www.smashingmagazine.com/wp-content/uploads/2017/05/contact-form-7-loading-sitewide-800w-opt.png)[81](https://www.smashingmagazine.com/2017/06/better-faster-optimized-wordpress-websites/)

> _Script loading sitewide. (View large version)_

There are a few easy ways to get around this. The first is to utilize a function which was introduced in WordPress 3.1 called [wp_dequeue_script()](https://codex.wordpress.org/Function_Reference/wp_dequeue_script). This allows you to remove an enqueued script from your site. Here is an example of [how to utilize the function](http://orbitingweb.com/blog/prevent-cf7-from-loading-css-js/) with Contact Form 7. The Contact Form 7 developer also has some documentation on how to [load the JavaScript and CSS only when necessary](https://contactform7.com/loading-javascript-and-stylesheet-only-when-it-is-necessary/).

Another easy way to prevent certain scripts from loading on specific pages and posts is to utilize a WordPress plugin like [Gonzalez](https://tomasz-dobrzynski.com/wordpress-gonzales) or [Plugin Organizer](https://wordpress.org/plugins/plugin-organizer/). Here is an example below on our dev site with the Gonzalez plugin. There are easy one-click options to disable the Contact Form 7 CSS and JavaScript files sitewide, per page/post, or only enable in a specific place. Generally, only loading Contact Form 7 on your "Contact Us" page would be the best for performance.

![Disable scripts per page.](https://www.smashingmagazine.com/wp-content/uploads/2017/05/disable-scripts-per-page-800w-opt.png)[88](https://www.smashingmagazine.com/2017/06/better-faster-optimized-wordpress-websites/)

> _Disable scripts per page. (View large version)_

There is a reason why WordPress is used by over [28% of all websites](https://w3techs.com/technologies/details/cm-wordpress/all/all) on the internet. And that is because it's a very robust, easy to use and feature rich content management system (CMS). Everyone from stay at home bloggers to fortune 500 companies rely on it every day. Just like with most platforms, if it isn't properly used or optimized it can turn into a big headache very quickly.

By correcting some of the common issues and mistakes I've seen from WordPress users above you can ensure happier visitors, better conversion rates, lower bounce rate and even improved search engine rankings. It is important for the WordPress community as a whole to **help educate each other on better performance and development practices** as the web continues to evolve.

_(mc, vf, ms, il)_
