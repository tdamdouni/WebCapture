# Cross-Site Scripting for Fun and Profit

_Captured: 2017-04-23 at 21:56 from [dzone.com](https://dzone.com/articles/cross-site-scripting-for-fun-and-profit?edition=292909&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-23)_

Discover [how to focus on operators for Reactive Programming](https://dzone.com/go?i=190137&u=https%3A%2F%2Fblog.wakanda.io%2Freactive-programming-operators%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how they are essential to react to data in your application. Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190137&u=https%3A%2F%2Fwww.wakanda.io%2F).

Still one of the most common vulnerabilities in web applications, XSS (cross-site scripting) still serves as a useful point of attack for hackers. If you are a web developer, knowing how to properly protect your application from these attacks is a must.

![](https://safecontrols.files.wordpress.com/2017/04/img_20160905_085644.jpg?w=739)

> _ Don't leave your app open to attack - injection vulnerabilities are not nice. _

Cross-site scripting vulnerabilities exist when the user input in web forms or in API calls are not properly escaped and sanitized before it is used. Directly reflecting user input back to the browser can be a sketchy practice. If the user inputs JavaScript into a form input field, and that script executes, then you have a vulnerability that hackers can take advantage of.

There are two ways users can give input to a web page: through web forms, and through URL parameters (usually by clicking links on the page). Both input types are interesting injection points for someone looking to exploit your page.

Modern web applications seek to filter out this type of input. OWASP has put together a large selection of attack vectors for XSS exploits that try to bypass these filters. You can see the list [here](https://www.owasp.org/index.php/XSS_Filter_Evasion_Cheat_Sheet).

To manually test your own applications you can try the following input strings:

  * <script>alert()</script>: usually, doesn't work. 
  * <img src=x onerror=alert()>: this is typically stored as an XSS exploit, typically in the comment functionality, etc. If code pops up an alert when you reload the page, you have successfully injected JavaScript into the page that will be used by others too. Now you can just go ahead and change the alert with a more evil kind of thing, like a redirect to your phishing site of choice (don't do it, it really is evil - and illegal).
  * In URL parameters: data:html,alert() or data:text/JavaScript,alert(); or JavaScript:alert()

The URL manipulation is typically used in links supplied in scam emails, etc. It makes your code execute within the context of the web application, and is often used to steal session data.

## Avoiding XSS as a Developer

There are several things you can do as a developer to avoid these vulnerabilities. The best way is to use a framework/templating system that auto-escapes dangerous inputs for you. Most modern web frameworks will do this for you, as long as you enable the right middleware!

You should also test for vulnerabilities, including XSS. You can do this manually by trying to inject strings like the ones above, and you can use a vulnerability scanner. Allow someone else to look at your code to try and find weaknesses - it is harder to see errors when you have made them yourself! You should use multiple test methods when available, and also consider including security tests in unit testing for your code.

Some takeaways:

  * Also, big league players have XSS vulns on their sites. See this [Register ](http://www.theregister.co.uk/2014/11/24/worst_wordpress_hole_for_five_years_affects_86_of_sites/)story from 2014 on a plugin bug for WordPress, affecting most of the platform (2014).
  * XSS will allow hackers to attack your users. You are partially to blame if this was possible due to neglect on your behalf. Right? And your customers would get angry.
  * Web application frameworks deal with this in a good way. It is very hard to write context-aware escaping manually, so stick with a framework!

[Learn how divergent branches can appear in your repository](https://dzone.com/go?i=190138&u=https%3A%2F%2Fblog.wakanda.io%2Fanimated-git-4-understand-divergent-branches-appear-fetching-remote-repository%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how to better understand why they are called "branches". Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190138&u=https%3A%2F%2Fwww.wakanda.io%2F).
