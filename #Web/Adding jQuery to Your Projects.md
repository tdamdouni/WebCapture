# Adding jQuery to Your Projects

_Captured: 2015-12-11 at 16:17 from [www.granneman.com](http://www.granneman.com/index.php?cID=775)_

  1. What's a CDN? Wikipedia to the rescue!

> A content delivery network or content distribution network (CDN) is a system of computers containing copies of data placed at various nodes of a network.
> 
> When properly designed and implemented, a CDN can improve access to the data it caches by increasing access bandwidth and redundancy and reducing access latency.

Basically, it's a collection of servers located all over the world. Companies hire CDNs to keep copies of software & content on those servers; the idea is that when people request that software or content, it's delivered to them from the server closest to them, thereby speeding up the delivery. [↩](http://www.granneman.com/index.php)

  2. There are actually many different versions of jQuery, each with a different purpose & intended use. For the full list, take a look at <http://code.jquery.com>. [↩](http://www.granneman.com/index.php)

  3. Is it a good idea to use a CDN to host jQuery & just link to it? Absolutely! For reinforcement, check out "[3 reasons why you should let Google host jQuery for you](http://encosia.com/3-reasons-why-you-should-let-google-host-jquery-for-you/)". That settles it, as far as I'm concerned. [↩](http://www.granneman.com/index.php)

  4. You'll notice that you have two choices when you download jQuery: Minified & Uncompressed. Take a look at both. You'll notice that the Uncompressed version is far more human readable, but is hundreds of lines long, while the Minified version isn't human readable at all, but is less than 5 lines long (although each line itself stretches on forevvvvvvverrrrrrrr).

The Minified versions have been minified (duh!); all unnecessary whitespace has been removed so that it's a much smaller file that web browsers & computers can still happily read & use, but humans can no longer parse it. But so what? Use the Minified version! [↩](http://www.granneman.com/index.php)
