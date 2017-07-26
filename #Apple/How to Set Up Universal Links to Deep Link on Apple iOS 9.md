# How to Set Up Universal Links to Deep Link on Apple iOS 9

_Captured: 2015-09-23 at 23:45 from [blog.branch.io](https://blog.branch.io/how-to-setup-universal-links-to-deep-link-on-apple-ios-9)_

_This was originally posted on July 24th, 2015 but has since been updated with the latest iOS 9 information. Enjoy!_

At Branch, we eat, breathe and sleep mobile deep linking. We created a single link that you can use everywhere: every platform, every device and every app store to drive users to your app. It's a single link, fully configured to link to your app off of every channel (Facebook, Twitter, Gmail, etc) and be listed in every search portal (Google App Indexing, Bing search, Apple Spotlight).

It just works. In fact, we've already written blog posts about [How to Set Up Google App Indexing](https://blog.branch.io/how-to-setup-google-app-indexing-with-deep-links) and [How to Deep Link on Facebook](https://blog.branch.io/how-to-deep-link-on-facebook), check them out.

![Slide1](http://cdn2.hubspot.net/hub/480264/hubfs/Slide1.jpg?t=1443043558099&width=250)

When Apple announced "Universal Links" in the latest WWDC pitch, we were excited to incorporate it into the Branch deep linking platform. Little did we know how complicated it would be to get it working. After spending far too much time on it and given how poor the documentation is, we thought we'd share a guide on how to do it in order to save everyone else.

# How Do Universal Links Work in iOS9?

Before Universal Links, the primary mechanism to open up an app when it was installed was by trying to redirect to an app's URI scheme (registered in the app's PLIST [like so](https://dev.branch.io/recipes/quickstart_guide/ios/#configure-for-deep-linking)) in Safari. This put the routing logic in Safari, but there was no way to check if the app was installed or not. This meant that developers would try to call the URI scheme 100% of the time, in the off chance that the app was installed, then fallback gracefully to the App Store when not by using a timer.

iOS 9 Universal Links were intended to fix this. Instead of opening up Safari first when a link is clicked, iOS will check if a Universal Link has been registered for the domain associated with the link, then check if the corresponding app is installed. If the app is currently installed, it will be opened. If it's not, Safari will open and the http(s) link will load.

Functionally, it allows you have a single link that will either open your app or open your mobile site.

## Universal Link Integration Guide

Here are the high-level steps to get Universal Links working for your app:

## 1\. Configure your app to register approved domains

i. Registered your app at developers.apple.com

ii. Enable 'Associated Domains' on your app identifier

iii. Enable 'Associated Domain' on in your Xcode project

iv. Add the proper domain entitlement

v. Make sure the entitlements file is included at build

**If you use Branch, you can stop here. Otherwise, continue to section two.**

## 2\. Configure your website to host the 'apple-app-site-association' file

i. Buy a domain name or pick from your existing

ii. Acquire SSL certification for the domain name

iii. Create structured 'apple-app-site-association' JSON file

iv. Sign the JSON file with the SSL certification

v. Configure the file server

If you use the Branch service, we'll save you all of the complexity of creating SSL certs and signing and hosting your server's JSON file, so you only need to modify your app's code to leverage it. We'll introduce this at the bottom of the post.

## Section 1: Configuring your app entitlements

In order to register your Xcode project for Universal Links, you need to create an App ID in the Apple developer portal and enable the proper entitlements. This is very similar to the configuration required for in-app purchases.

You cannot use a wildcard app identifier for Universal Links

### Register your app on developers.apple.com

First, head to developers.apple.com and login. Then click on "Certificate, Identifiers & Profiles", and then click on "Identifiers".

![Apple Developer Portal for Universal Links](http://cdn2.hubspot.net/hub/480264/hubfs/Screen_Shot_2015-07-24_at_10.56.24_AM.png?t=1443043558099&width=497)

> _Apple Developer Portal for Universal Links_

If you don't have a registered App Identifier already, you'll need to create one by clicking the + sign. If you do have one, skip ahead to the next section.

You need to fill out 2 fields here: name and bundle ID. For name, you basically enter whatever you want. For bundle ID, you'll fill in the value of the bundle

![Explicit App ID for Universal Links](https://lh5.googleusercontent.com/nhNhLYzrRspX13h2S8kHUi5cjcwzFz-MnceDgGzcCS84Lj74BHVAEho5iW229vxWEUmx_ZPdeBIq2lO-1NswRbB1ManLLOKZ1iaylzwn02jeDaBOZWflQ528vhayBSh8HSmmWqg)

> _Explicit App ID for Universal Links_

You can retrieve this by looking at the General tab of your Xcode project for the proper build target.

![Setting up Universal Links in xcode](https://lh5.googleusercontent.com/SmZ_B_HQoLM_bD4MVh5cdKiUfdmHXLZKzw_BpIE_U9MVfAD1753ppBi3K9GPX3waSWEYC0TXVjlHyX8zdbRqb98xvT9ue3lfOdX4VvPj49CQErjpxp32SKCkuKK3_zo5gBsBP8A)

> _Setting up Universal Links in xcode_

### Enable 'Associated Domains' in your app identifier on developers.apple.com

For your pre-existing or work-in-progress App Identifier, scroll down to the last section and check the 'Associated Domains' services.

![Setting up App ID for Universal Links](https://lh5.googleusercontent.com/QWnGKkPM6O4R-CKHBnwZucRhryfFBuaPWCOr2WTHjsgBZgNsIzHjPsoQQkbN2y0xMqcrPR-AGTnMVEpbd7mA0WrIALsbR7ziHeagXo_sw82I4ZM3b8JqN97Y2Q3S0aI48Hfwx-0)

> _Setting up App ID for Universal Links_

Scroll down and click 'Save'.

### Enable 'Associated Domains' in your Xcode project

Now, you'll want to enable the 'Associated Domains' entitlement within your Xcode project. First, make sure that your Xcode project has the same Team selected as where you just registered your App Identifier. Then go to the Capabilities tab of your project file.

![Universal Links in xcode](https://lh4.googleusercontent.com/e0JS11RiJJK9yiLtbBJrYNJ5XyhZA5lRi5r4JO8uqDWTPHcUvYnrUhedf0r7_BknfY7lZekRsP4aNmsjQaJaDL3y3zDf6ZQWZ6nJ48qFfVdHgt-Pj-nwx-KIHoV8y_n3ihBaVfI)

> _Scroll down and enable 'Associated Domains' so that the accordion expands._

![setting up associated domain for Universal Links](https://lh5.googleusercontent.com/RGmRvtiKCHRZpcJtOkLrMr2ooQOjPuvOSSkhXsuUcBU6AzG7JzvTYKzihOKmhIuCixQS_3bXM_4Efhm4PG0V7UbDtmbMcuLyONDrCo5pl_CQOxtVEwDpNgPxtDlp2Wwv6HsqpqI)

> _If you see an error like this, check:_

  * that you have the right team selected

  * your Bundle Identifier of your Xcode project matches the one used to register the App Identifier

### Add the domain entitlement

In the domains section, add the appropriate domain tag. You must prefix it with "applinks:". In this case, you can see we added "applinks:yourdomain.com".

![App Links and your domain ](https://lh3.googleusercontent.com/pAM7dC9WPnCmZoGLJCwaSWyUAk2soRWR8pJ_X4CvDVjaYYhg61Oh0_0R7qQ1N8rmWvrEWpvhh2ziGXAoG__d0VQc6KGkdse3VoreO9M5UUqpiF_4aeuKXw5FreUnagKwlstsWdc)

> _Make sure the entitlements file is included at build_

Lastly, for some reason, Xcode 7 did not include my entitlements file in my build. In the project browser, make sure that your new entitlements file is selected for membership to the right targets so that it's built.

![Configuring xcode for universal links](https://lh3.googleusercontent.com/YPEKvz5Yps7L8HEG3xcRl6XssT4KnAZn-scB2YgO1SbLti33Nr3m3kxidLiBxmYzPSh1bmD7SScaLA98JyWH35VWNmS7SS6IVTGjJbA1m-Y074krw60MUuroPmJ8i20JZWrvAmQ)

> _Configuring xcode for universal links_

**If you use Branch links, you can stop here! If not, keep reading or use the button below to start integrating.**

If you want to save yourself hours of headache, you can **avoid all the JSON hosting and SSL cert work**and just use Branch links to host it for you.

However, if you're a control freak and glutton for punishment, by all means continue.

## Section 2: Configuring your apple-app-site-association file

Universal Links turn your website URL into an app link, so you need be running a web server in order to leverage them.

### Pick a domain

First, identify the domain that you'd like to use for your Universal Links. You can register a new one or use an existing. If registering a new one, we prefer to use a clean, non-spammy registrar like ghandi.net.

### Acquire SSL certification

You need to acquire SSL certification files for the domain you'll use to host the Universal Links. In order to do this, you'll need to use a third party service to register your domain for SSL, and create the files you need. After looking around, we've chosen Digicert to handle branch.io and associated subdomains.

Here are the steps to create your SSL certification:

1\. Visit <https://www.digicert.com/easy-csr/openssl.htm> and fill out the form at the top to generate an openSSL command. Keep this window open

2\. Login to your remote server

3\. Execute the openSSL command to generate a certificate signing request (.csr) and certification file (.cert)

4\. Pay for your SSL certification at <https://www.digicert.com/welcome/ssl-plus.htm>

5\. Wait for Digicert to approve and send you the final files

6\. In the end, move yourdomain.com.cert, yourdomain.com.key and digicertintermediate.cert into the same directory on your remote server

### Create your apple-app-site-association JSON

There is a pretty standard structure of this JSON file, so you can basically just copy this version and edit it to fit your needs. I'll breakdown where to get the correct values below.
    
    
    {  
       "applinks": {  
           "apps": [ ],  
           "details": {  
               "T5TQ36Q2SQ.com.branch.sdk.TestBed": {  
                   "paths": [  
                       "*"  
                   ]  
               }  
           }  
       }

The only fields you need to change are associated with: "T5TQ36Q2SQ.com.branch.sdk.TestBed". This is actually two values joined together with a period. Both values are found on developer.apple.com in the Identifiers -> App IDs section. Just click on the corresponding registered App ID as shown below.

![Configuring Apple ID for Universal Links](https://lh5.googleusercontent.com/B4QzQ80F7W1hGm9uewCo6kPwNcoKPPR_dZWBgwhcxOOFgMyxKkZj1KU3d_SKkfL6uRRjJBKZqqHR4S9tcBz2jCtK0g3JCL3NbA_rjLd3gcfP0xveEBqhfIt1yv8lehLPHrfAMm8)

> _Configuring Apple ID for Universal Links_

In this example, connect the Prefix and the ID together with a period so that it looks like so: `"T5TQ36Q2SQ.com.branch.sdk.TestBed"`.

Save this JSON file as apple-app-site-association-unsigned.

### Sign the JSON file with your SSL certificates

Upload the apple-app-site-association-unsigned file to your server into the same directory as the certification and key files from the previous steps. Using the command line, change directory into that folder and issue the following command:

`cat apple-app-site-association-unsigned | openssl smime -sign -inkey yourdomain.com.key -signer yourdomain.com.cert -certfile digicertintermediate.cert -noattr -nodetach -outform DER > apple-app-site-association`

This will generate the file apple-app-site-association

### Configure your file server

Alright! So you have your signed apple-app-site-association file. Now you just need to configure your file server to host this for you. There are a few caveats:

  1. It must be sent with the header 'application/pkcs7-mime'

  2. It must be sent from the endpoint youdomain.com/apple-app-site-association

  3. It must return a 200 http code.

We setup the one for all Branch integrated apps using our Node+Express link servers. Here's the code we used in case that's helpful:

`var aasa = fs.readFileSync(__dirname + '/static/apple-app-site-association');  
app.get('/apple-app-site-association', function(req, res, next) {`  
`     res.set('Content-Type', 'application/pkcs7-mime');`  
`     res.status(200).send(aasa);`  
`});`

## Branch and Universal Link Integration Guide

Again, you can **avoid all the JSON hosting and SSL cert work**and just use Branch links to host it for you.

Happy Linking!

[Learn more](https://branch.io/team/) about this author.

Branch helps mobile apps grow with [deep links](https://branch.io/features/) that power referral systems, sharing links, invites and marketing links with full attribution and analytics. The best teams in mobile use Branch links. [Find out who](https://branch.io/partners/) and [get started](https://dashboard.branch.io/) today.
