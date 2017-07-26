# Moving to GitHub Pages without F❤cking Up Email

_Captured: 2016-12-11 at 17:37 from [imakewebthings.com](http://imakewebthings.com/blog/github-pages-email)_

Things look different around here. Two weeks ago I moved this site from a self-hosted WordPress install to [Jekyll](https://github.com/mojombo/jekyll/wiki) running on [GitHub Pages](http://pages.github.com). But this isn't about the redesign or the hosting move, it's about the three days I spent silently bouncing email afterwards.

The `imakewebthings.com` domain is registered through and was previously hosted on [A Small Orange](http://asmallorange.com), which uses the cPanel site management software. My email for the site is also hosted there as part of the package. The root cause is my idiocy, but hopefully this page can provide clarity to the passing frustrated user hopelessly searching Google for answers. Here's how it went down.

## How to Move to GitHub Pages

Enough has been written on this topic over the years, so I won't get into the details. It breaks down to:

  1. Create [a repository](https://github.com/imakewebthings/imakewebthings.github.com) on GitHub with the name of `username.github.com`. Put your Jekyll powered site in this repository. Once you push the site will be viewable at `http://username.github.com`.
  2. Add [a file](https://github.com/imakewebthings/imakewebthings.github.com/blob/master/CNAME) named `CNAME` to the root directory of this repository. It is a text file that just contains one line, the domain name you wish to use. In my case, `imakewebthings.com`.
  3. Change the DNS settings for your domain to point to GitHub's servers.

We're concerned with the last step. Here are [the instructions](http://pages.github.com/#custom_domains) on the GitHub Pages site (emphasis mine):

> Next, you'll need to visit your domain registrar or DNS host and add a record for your domain name. For a sub-domain like `www.example.com` you would simply create a CNAME record pointing at `charlie.github.com`. If you are using a top-level domain like `example.com`, you must use an A record pointing to `207.97.227.245`. **Do not use a CNAME record with a top-level domain, it can have adverse side effects on other services like email.** Many DNS services will let you set a CNAME on a TLD, even though you shouldn't. Remember that it may take up to a full day for DNS changes to propagate, so be patient.

Sweet. I opened up cPanel to change the DNS records.

![cPanel domain section, including Simple and Advanced DNS Zone Editor buttons](http://s3.amazonaws.com/imakewebthings-blog/cpanel-domains.png)

The simple DNS editor doesn't show the A record for top-level domains, so I went to the advanced editor. The first DNS entry was an A record for the top-level pointing at my shared server IP. I changed it to point to the GitHub IP address. Several hours later the record change had started propogating and the site worked as expected. So far, perfect.

Three days later I received a Twitter DM that my email address was returning to sender with a warning, or worse, failing silently.

## What Went Wrong?

The GitHub instructions don't tell the whole story, nor should they, about all the things that could go wrong when making DNS changes. The immediate lesson: It's perfectly possible to screw up email on a domain without switching the TLD record to a CNAME **if the MX record for that domain also points to the top-level record**.

_Hold on,_ you say, _What are all these different record types?_

Great question, voice in my head. If you've managed DNS records before this is all 101 material. For folks like myself who until recently relied on other team members to deal with these matters, it's foreign. To summarize:

  * **A Record**: The basic core of DNS. It maps a nice, pretty URL to a messy IP address behind the scenes.
  * **CNAME**: A "Canonical Name" record. It acts as an alias, redirecting lookups to another record. A common one is `www.tld.com` pointing to `tld.com`. If a user navigates to `www.tld.com` the DNS server will say, "Hey, go here instead."
  * **MX Record**: This record describes where to route SMTP mail traffic. It should point to wherever your email is hosted.

If you haven't already guessed, my MX record for the `imakewebthings.com` domain was pointed to `imakewebthings.com` which was now resolving to the GitHub IP address instead of my old shared server that hosts the email. Other hosts may point to a separate A record specifically for this purpose, but it's worth checking. If you're wondering why you don't see the MX record listed, it's because in cPanel **MX records are not listed in the Advanced DNS Zone Editor.** They're in a separate page under the Mail section.

![cPanel email section, including the MX Entry button](http://s3.amazonaws.com/imakewebthings-blog/cpanel-mail.png)

## How to Fix It

  1. Keep the top level A record pointing to GitHub's server.
  2. Create a new A record for `mail.yourdomainhere.com`. If you already have a CNAME record for the mail subdomain, change it to an A record. Point this record to your old host IP. If you don't know it, look in the left sidebar of cPanel and click "expand stats." It's listed under Shared IP Address.
  3. Change the MX entry to point to `mail.yourdomainhere.com`.

Give it some time to propagate. Several hours later you should start to see a steady stream of backed up messages. Congratulations. Now stop reading your email and get back to work.
