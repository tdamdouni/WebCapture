# Staying Secure on the Internet, Part 1

_Captured: 2017-07-13 at 11:07 from [dzone.com](https://dzone.com/articles/staying-secure-on-the-internet?edition=308191&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-12)_

With the passing of S.J.Res.34 and H.J.Res.86, and now that the bill is signed, many people are panicking about their privacy. Now, I have [read](https://www.theregister.co.uk/2017/03/28/congress_approves_sale_of_internet_histories/) [all](https://arstechnica.com/tech-policy/2017/03/for-sale-your-private-browsing-history/) [sorts](http://www.theverge.com/2017/3/29/15115382/buy-congress-web-history-gop-fake-internet-privacy) of [things](http://www.theverge.com/2017/3/31/15138526/isp-privacy-bill-vote-trump-marsha-blackburn-internet-browsing-history) about changes we will or won't see as a result of this bill, but either way, you should take this as a wake-up call. As we always see in the software security realm, unfortunately, security is never a concern until it is too late. Well, I have no idea if this counts as 'too late' or not, but I decided to take this as a good reason to finally implement securing my home network traffic (something I have put off for almost 4 years now). Below are a few ideas for keeping your internet traffic private, with some analysis of each. A big thanks to my buddy [Tim](https://www.linkedin.com/in/tim-strackbein-pmp-ceh-1726b638/) (he's a nerd for hire), for letting me bounce some ideas off of him, and pointing me in a direction or two.

Before we dive into anything, I think it's pertinent to talk about what the issue is, and what we're looking at accomplishing. Based on those articles I pointed out, and [many](http://www.npr.org/sections/alltechconsidered/2017/03/28/521813464/as-congress-repeals-internet-privacy-rules-putting-your-options-in-perspective) [many](https://xkcd.com/504/) [others](http://www.gameinformer.com/b/features/archive/2017/03/25/what-potential-changes-to-internet-privacy-laws-could-mean-for-you.aspx), we want to ensure our web traffic can't be viewed by anyone. As has been pointed out [numerous](https://www.howtogeek.com/117776/htg-explains-how-private-browsing-works-and-why-it-doesnt-offer-complete-privacy/) [times](https://xkcd.com/1820/), using something like incognito mode in your browser keeps data from being saved locally, it doesn't obfuscate that traffic from anyone else: your Internet Service Provider (ISP), network sniffers, etc. What we want, is to ensure the traffic you are generating can't be read, so we need something more.

## SSL

When you visit a secure site (one using HTTPS), all of the data passed between you and the site is encrypted (assuming the site was setup properly). This is a major step to ensuring your personal data is safe. This means, ensure your email, Facebook, banks, etc., are all being visited over HTTPS. Depending on the browser, you should verify that a little (sometimes green) lock is present to the left of the URL. So, this sets us in the direction of what we're looking for, keeping our data safe from prying eyes. But it doesn't do everything.

#### Pros

  * You shouldn't need to change much.
  * Simple.
  * Completely Free.
  * Supported on any browser, any OS, any device without any additional work.

#### Cons

  * Only works for browser traffic.
  * Not all sites have HTTPS as an option.
  * ISPs can still see what sites you are visiting (they just can't see the content you are viewing on them).

As using SSL is a good start, be sure to check out plugins that can for additional SSL traffic. Tools like [HTTPS Everywhere](https://chrome.google.com/webstore/detail/https-everywhere/gcbommkclmclpchllfjekcdonpmejbdp?hl=en) for Firefox and Chrome can ensure all of your traffic is encrypted.

## TOR

So, let's dive in a little deeper. For just a little added setup, we can ensure all of the data we're browsing through gets hidden from our ISP. Do you watch _House of Cards_? Do you remember them mentioning the 'dark web.' Maybe you've seen _Mr. Robot_. They more directly (and more accurately) represent this 'secret' side of the internet that hackers hang out in. Well, it's not necessarily a dark nasty corner of the web. The Onion Router, or TOR (originally developed by the Navy), is simply a way to [browse the web anonymously](http://lifehacker.com/what-is-tor-and-should-i-use-it-1527891029). Yes, there are private servers within the network you'll want to avoid, but our goal here is anonymity, not treachery. What does that mean for us? If you don't want your ISP to know what sites you are visiting, or you want to visit a site that doesn't support HTTP, ensure you [install TOR](https://www.torproject.org/projects/torbrowser.html.en) and make that your new browser. You can even run TOR on your [mobile device](https://www.torproject.org/docs/android.html.en).

  * Relatively simple.
  * Free.
  * Supported on most devices.

#### Cons

  * Limited to TOR browser.
  * Difficult to get working on iOS.
  * Slows down internet speeds (because you are bounced from server to server to provide anonymity, this slows down your connection speed).
  * Only works for browser traffic.
  * Install needs to be made on every machine you want to use.

## TOR as a Proxy

We're moving in the correct direction, so let's dive even deeper. In our previous example, we've ensured all of our browser traffic is secure. To get additional security, you can configure your TOR browser as a proxy, which means we can pass any internet traffic through it. This means not only can we gain security and still use any browser we want, but also our actions outside our browsers (such as backups, messaging, or email clients) are also secure. Here are some relatively simple instructions to gather the [information needed from TOR](http://www.wikihow.com/Route-All-Network-Traffic-Through-the-Tor-Network), and how to setup your [Windows](https://www.howtogeek.com/tips/how-to-set-your-proxy-settings-in-windows-8.1/), [Mac](https://kb.netgear.com/25191/Configuring-TCP-IP-and-Proxy-Settings-on-Mac-OSX?cid=wmt_netgear_organic), [Linux](https://www.cyberciti.biz/faq/linux-unix-set-proxy-environment-variable/), or [Android](http://stackoverflow.com/questions/21068905/how-to-change-proxy-settings-in-android-especially-in-chrome) machine to route all it's traffic through TOR.

I'd like to put a note at this point about streaming services. Services like Hulu, Netflix, Prime, and many others require that you run outside a VPN. It's part of their ToS. This means that if you wanted to watch Netflix on your machine, in our previous scenario, you just wouldn't use the TOR browser. If ALL of your traffic is setup to run through TOR, you need to turn this off in order to use these streaming services.

  * Free.
  * All traffic can be secure (other than that over cellular networks).
  * More complicated setup.
  * Setup needs to be repeated each time machine is rebooted (or TOR is launched).
  * Setup needs to be repeated on each machine you want to secure.
  * Slows down traffic.
  * Can't run streaming services.

## VPN

As we can see from the above, using TOR is becoming more and more complicated. If we want to get back into a simple realm, we need to start talking VPNs. The purpose of a VPN is the same as we were looking for with TOR. It should encrypt your connection and provide you with an anonymous IP to protect your privacy. This, however, switches us from the free realm, into the paid one. Now, while there are plenty of free VPNs, you want to be very careful about which VPN you choose. You need to consider WHY a VPN service would be free. They have hardware they are using and maintaining, software to setup, and people to pay. How are they making money? Many of them will do exactly what you're trying to avoid; sell your information, inject ads, or worse, [use your bandwidth](https://www.cactusvpn.com/vpn/what-is-the-problem-with-free-vpn-providers/).

When selecting a VPN service, I happen to like [this site](https://thatoneprivacysite.net/vpn-section/) for comparing. TorrentFreak also has some [good reviews](https://torrentfreak.com/vpn-anonymous-review-160220/) on VPN services, and _thebestvpn_ has recently published a great [VPN vs. TOR guide](https://thebestvpn.com/tor-vs-vpn/). Some of the things I look for when selecting a VPN service are OS options (can it run on Linux, and Android (for me at least)), available simultaneous connections, price (kind of obvious), speed, and privacy policy. Once you choose a VPN, install it on your machine(s), and set it up to run at startup. Most services I've been interested in have great instructions and even provide good technical support. As a reminder from above, if you want to stream video, you'll probably need to turn your VPN off (much simpler than turning off TOR as a proxy for your system). Alternatively, some VPNs are set up to allow you to run a split tunnel. If you do this, you can ensure streaming services run directly to the internet, but that all other traffic goes through the VPN; this is typically very complicated to setup, and depending on the service you choose, their technical support might or might not be able to assist with it.

  * Simple to setup.
  * Simple multiple machine support.
  * No speed reduction.
  * All traffic is secure.
  * Not free.
  * Setup needs to be repeated on each machine you want to secure.
  * More difficult to run streaming services.

## Verifying You Are Secure

Before we dive much further, I believe it's worthwhile discussing a few ways you can verify that you've secured your data. First off, head over to [https://whatismyipaddress.com](https://whatismyipaddress.com/) and take note of what it says; I'll be referring to this as your personal IP address. Once you connect securely, using any of the above methods, there are a few ways to verify you have truly secured yourself.

  1. Navigate to <https://www.xmyip.com/>
    1. Verify that is not your personal IP address.
    2. Click the Additional Details button.
    3. Check that is not your actual location.
    4. Confirm that is not your ISP.
  2. Navigate to <https://whoer.net/#extended>
    1. Verify that is not your personal IP address.
    2. Check that is not your actual location.
    3. Confirm that is not your ISP.
    4. If you're running TOR, it will indicate so.
    5. Run the interactive detection to ensure no data is being leaked.
  3. Navigate to <https://dnsleaktest.com/>
    1. Verify that is not your personal IP address.
    2. Click the Extended Test button.
    3. Verify that none of the hostnames contain your personal IP address.
    4. Confirm that none of the ISPs match your ISP.

These next few suggestions all ramp up the complications. The idea is to run all of your network traffic through one device that can provide a secure connection. A typical home setup might look like this:

![](https://www.coveros.com/wp-content/uploads/2017/04/Typical-Network-2.jpg)

Obviously, yours may vary, but above are two pretty typical network setups. In order to ensure that all of our network traffic runs through TOR or our VPN, we need to inject TOR or our VPN between our machines and our modem. We'll get into specifics about how to do that below, but we would be looking at a new network setup which looks like this:

![](https://www.coveros.com/wp-content/uploads/2017/04/Network-w2F-TOR2FVPN.jpg)

Now, this definitely adds to the complexity of the setup, as you're starting to inject some additional hardware. Notice I put in a black box labeled _privacy_. This just means, at this point, we don't care what it is, we just want it in place to route all our traffic through. It can be a physical machine, a VM, or even some specialized hardware. Additionally, it could be running TOR or a VPN. At this point in our decision making, we're more concerned at the high level of where it is, and what its purpose is - to secure our data.

In our first setup, I added a switch to route traffic to multiple machines, but our mobile devices now can't connect to this system, since there is nothing wireless behind our privacy box. Our mobile device can only connect directly to the modem with the router, which doesn't keep its data secure. We could replace the switch with a router, but that adds more cost to our setup.

Now, based on this setup, we can cause some problems. As I mentioned above, sometimes you need some traffic to run outside your private network. For this reason, I always like to have 2 connection points, one inside your private network, and one outside. This way, if there is anything you need to access directly (Netflix, Alexa, work VPN), you have another access point. While this might add some additional cost to your home network setup, it should increase your capabilities.

![](https://www.coveros.com/wp-content/uploads/2017/04/Full-Network-w2F-TOR2FVPN.jpg)

> _Below, I will dive into some ways to implement our 'black box of privacy.'_

## Setup VPN on Router

One of the simplest ways to setup our above 'black box of privacy' is actually to combine your router with our secure connection. The same VPN service you might have selected above will work just fine for this step. The idea here is to actually have your router run your VPN, thereby eliminating the need for any additional hardware. Most routers out there by default don't support this, but luckily, 'by default' is not what we're looking at here. At their core, routers are hardware that runs software. What we're interested in here is modifying the software that the router is running, so that it will support running our VPN service. There is a great piece of open-source (free) firmware (software for specific hardware) called [DD-WRT](https://www.dd-wrt.com/) which runs on a slew of [different routers](http://www.dd-wrt.com/site/support/router-database). Among other capabilities, DD-WRT allows you to run a VPN directly on your router. There is other software out there that can accomplish the same thing, but DD-WRT seems to be the simplest, with the most community support.

![](https://www.coveros.com/wp-content/uploads/2017/04/VPN-on-Router.jpg)

  * The entire network is secure, no need to install anything on any individual system.
  * All traffic is secure.
  * Some initial setup is required.
  * Associated costs with equipment and VPN provider.
  * May notice some speed reduction (router may not have the capacity to encrypt and decrypt as fast as desired).

### Router Setup

Getting started with this setup is relatively simple:

  1. Determine if your current router (not your main internet connection or modem) is compatible with DD-WRT. 
    1. If it is not, you may need to get one that is.
  2. Ensure your network configuration matches the below diagram.
  3. Install DD-WRT on your router. 
    1. Locate your router from the above router-database link.
    2. Download the 'Webflash image for first installation' bin file.
    3. Log in to your router.
    4. Select upgrade firmware.
    5. Provide this file for the upgrade.
    6. Restart your router.
  4. Configure your VPN - these steps may differ depending on your VPN. 
    1. Log in to your router.
    2. Select the Services tab.
    3. Click the VPN sub-tab.
    4. Select 'enable' under OpenVPN Client.
    5. Enter in your VPN information.
    6. Restart your router.
  5. Verify your VPN. 
    1. Log in to your router.
    2. Select the Status tab.
    3. Click the OpenVPN sub-tab.
    4. Verify the state shows successAlternatively, you could use any of the above verification methods.

These instructions are a little generic but are the correct overall process to follow. Whichever router you choose to go with, it might be worth your time Googling some instructions on how to install DD-WRT on that specific router. Additionally, check with your VPN provider, and see if they have more detailed instructions on running with DD-WRT - many of them do.

Tomorrow we'll dive into the nitty gritty of setting up your secure network, and show you all the commands and configurations you'll need to know.
