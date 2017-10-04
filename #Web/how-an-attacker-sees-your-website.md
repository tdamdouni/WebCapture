# How an Attacker Sees Your Website

_Captured: 2017-09-21 at 19:34 from [dzone.com](https://dzone.com/articles/how-an-attacker-sees-your-website?edition=326503&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-09-21)_

Discover an in-depth knowledge about the different kinds of [iOS hacking tools](https://dzone.com/go?i=222228&u=https%3A%2F%2Fweb.securityinnovation.com%2Fhacking-ios-applications-dzone%3Futm_campaign%3DDZONE-Sponsorship-June-2017%26utm_source%3DAdvertising%26utm_medium%3Dhacking-ios-applications) and techniques with the [free](https://dzone.com/go?i=222228&u=https%3A%2F%2Fweb.securityinnovation.com%2Fhacking-ios-applications-dzone%3Futm_campaign%3DDZONE-Sponsorship-June-2017%26utm_source%3DAdvertising%26utm_medium%3Dhacking-ios-applications) iOS Hacking Guide from Security Innovation.

You don't have to try very hard to [hear about](https://smashingboxes.com/blog/attacker-sees-website/) the latest cyber attack. Sony, Yahoo, LinkedIn are just a few of the recent victims. However, it's not only large companies that are getting hit. In fact, the number of attacks against small businesses has been dramatically increasing since 2011. According to [Symantec's 2016 Internet Security Threat Report](https://www.symantec.com/security-center/threat-report), 43% of attacks are now directed at small businesses.

One of the most frequent ways these attacks happen is through the company's website. Normally, it's best practice to keep network resources walled off from the rest of the world, but in the case of a website, its whole purpose is to be a publicly available portal. It wasn't so bad back when a website was nothing more than a few static HTML files (there were, of course, other problems then, but I digress), but with the database-backed, dynamic applications we have now, there are many places where things can go wrong.

So, let's talk about what a real attack looks like. This won't be an in-depth _how to hack_ tutorial, but rather a demonstration of how information is gathered and used to exploit the application.

### Finding a Target

Since picking an unsuspecting website to run attacks on is unfriendly (and also quite illegal), I'll instead opt to demonstrate using a practice app known as Hacme Casino. Hacme Casino is an intentionally vulnerable web application written in Rails 1. Though the tech may be a bit dated, the same vulnerabilities are still prevalent in modern apps and the attack methodology remains the same.

Hacme Casino may be downloaded from [McAfee (Windows only)](http://www.mcafee.com/apps/free-tools/termsofuse.aspx?url=/us/downloads/free-tools/hacme-casino.aspx)

OR

As part of the [Maven Security Dojo VM](https://www.mavensecurity.com/resources/web-security-dojo/)

### Attack Methodology

Every (good) attack follows the methodology: Reconnaissance, Exploit, Payload, Loot.

**Reconnaissance.** Understand your target. What ports are open? What services are running? What is it built with? How is data passed? The better you can understand your target, the more successful you will be in later steps

**Exploit.** Find the weak points. Can you cause 500 errors with arbitrary data? Does any of the software have known CVEs (Common Vulnerabilities and Exposures)?

**Payload.** Find the specific data needed to accomplish your goal. Are you trying to extract passwords with SQL injection? Compromise sessions with XSS? Gain shell access via file upload?

**Loot.** Reap the benefits of your efforts. Exfiltrate user or account data. Compromise the server. Shut it all down.

### Spoiler Warning

If you plan on practicing with Hacme Casino, you may want to come back to this post to compare your results. Below this point, I will be spoiling many of the issues. You've been warned.

## Beginning the Attack

### Step 1. Reconnaissance

Let's explore together. When we load up Hacme Casino, we're presented with this page:

![](https://smashingboxes.com/app/uploads/2016/11/main_page_image-1024x786.png)

Here, it's good to just look around the site and see what pages and features are available. Burp Suite can be used here to passively spider the site while you browse.

Not much can be done without an account, so one of the first things we should do is sign up for a new account. Every field here is a potential attack vector, but for now, we're just observing.

Once we're logged in, we see some games we could play if only we had chips. On the account page, we can transfer chips to other players or simply cash out. Looking at the transfer select box, we can see that there are already a few other accounts. Inspecting this box with the Chrome dev tools, we can grab those users' account names.

By poking around a bit more, I was able to glean the following:

### Step 2. Exploit

Alright, now that we have some information about the server, let's start finding some exploits. There are a number of CVEs published for the Ruby/Rails versions being used, but let's focus on the app itself for now.

We'll focus on the login form to start. Hacme Casino does a good job here of giving a message that doesn't specify if the username or password was wrong. It also gives the same message if an account exists or not. This is important because just like in the court of law, everything you say can and will be used against you.

There is a flaw here, though. By typing in `'` for the `Login` or `Password`, we get a message that says `An error occured during login.`. Though it's hard to get any other useful information from this form manually, it's enough to confirm that SQL Injection is possible. At this point, a tool like SQLMap could be used to extract data.

![](https://smashingboxes.com/app/uploads/2016/11/login_failure.png)

![](https://smashingboxes.com/app/uploads/2016/11/login_error.png)

Since we're not getting much information from the login form, let's move over to the other user-related form, the signup form.

![](https://smashingboxes.com/app/uploads/2016/11/signup_form.png)

We need to type at least three characters into the `Desired login` field, since that is verified on the backend. Entering `'''` (any odd number of `'` will also work) in this field and filling out the rest of the form normally yields an interesting result indeed.

![](https://smashingboxes.com/app/uploads/2016/11/stacktrace-1024x297.png)

There is a lot of great information on this page. If your website exposes information like this in production, please go fix it now!

The part we are most interested in for the moment is this

What can we gather from this line? The database is SQLite3, the entire SQL query used for login, and it appears passwords are being stored in unsalted SHA1. Let's look at the query for now.

### Step 3. Payload

What if we were to transform this some. By using SQL injection, we can remove the check for the password. We need to close the quote, the parentheses, and end the query. To do that, we can select a user and append `');--` to their name. If we enter `user');--`, that would make the query:

Everything after `\--` is ignored, so the query that runs is

Since we already have a list of usernames, let's give one a try:

![](https://smashingboxes.com/app/uploads/2016/11/sql_injection_string.png)

![](https://smashingboxes.com/app/uploads/2016/11/sql_injection_access.png)

### Step 4. Loot

From here we now have access to every account on the site. We can transfer the chips from another player to our account. We can extract the SHA1 passwords for later offline cracking. There's even a way to generate unlimited money.

![](https://smashingboxes.com/app/uploads/2016/11/lots_of_chips.png)

### Summary

So this is great for us as attackers, but what if we were another user, or even worse, the owner of this site?

Well, as another user, there's not always a lot that can be done. General good practices like strong passwords will make it harder to crack the stolen password hashes, but won't prevent access to the account in the first place.

### What Can We, as Professionals, Do?

#### 1\. Think of Security as a Mindset

We need to understand that security is a mindset. It's not a tool that we set and forget. It's not a one-time code decision. It needs to be in the forefront of our minds during our daily work.

#### 2\. Apps Will Be Used in Ways That Were Not Intended

We need to understand that our products may be used in ways that we did not intend. Attackers are looking to cheat the system. They do so by sending strange inputs, calling resources directly, and watching how the data flows.

One of the most important questions to ask as an insider is, 'If I wanted to break this, what would I do?'

#### 3\. All Input Is Potentially Dangerous

This one is simple to understand but easy to forget. **Any** information that comes from the client is under the client's control and should not be implicitly trusted. This includes, but is not limited to: form input, headers, cookies, request methods, parameters, and so on.

Sometimes it's easy to tell. A string like `"> <img src=d onerror=alert(document.cookie)` looks rather suspicious, but receiving a request whose origin says 'google.com' may or may not actually be coming from Google. In this case, how do we tell if it's malicious or not? Many times we can't, and that's why we need to have other protections in place.

#### 4\. Security by Obscurity Does Not Work!

Security by obscurity simply means that since no one knows about a site or resource and there are no links to it, that it must be secure. This does not work. It has never worked. Sure, it may take a long time to uncover manually, but those of us in software especially should know that for time-consuming tasks we use scripts. Well, hackers have scripts too. Someone will find your alternate domain, someone will find that undocumented endpoint. A business is not safe from attacks just because it's not a household name. As I mentioned at the start of the article, attacks against small businesses are on the rise.

#### 5\. Remember to Breathe

Reading the news about all the latest threats, attacks, and breaches can get overwhelming. It's true that attackers are at work every day trying to exploit others for gain. It's easy to get pulled under by the never-ending waves of bad news. By being proactive and addressing security from the start, we can help to prevent it from becoming a problem in the first place. However, we can't think clearly and make proper decisions if we're too stressed out. So, when things start to feel overwhelming, just remember to breathe.

Learn about the importance of a strong culture of cybersecurity, and [examine](https://dzone.com/go?i=232227&u=https%3A%2F%2Fweb.securityinnovation.com%2Fbuilding-a-culture-of-cybersecurity-adv%3Futm_campaign%3DDZONE-Sponsorship-June-2017%26utm_source%3DAdvertising%26utm_medium%3Dbuilding-a-culture-of-cybersecurity) key activities for building - or improving - that culture within your organization.
