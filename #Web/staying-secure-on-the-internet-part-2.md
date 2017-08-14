# Staying Secure on the Internet, Part 2

_Captured: 2017-08-08 at 20:30 from [dzone.com](https://dzone.com/articles/staying-secure-on-the-internet-part-2?edition=310393&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-21)_

If you missed the first part of this article, check it out [here](https://dzone.com/articles/staying-secure-on-the-internet).

## Run Router Through TOR

Another 'black box of privacy' option is to configure your router to run all of its traffic through TOR. This is a kind of combination of our previous setup, running TOR as a proxy. What we'll do here is setup a separate machine (or VM) running TOR, and this machine will be our black box in the above diagram. We'll also install DD-WRT on our router, similar to the above step. This time, however, instead of installing a VPN on our router, we'll configure our router to proxy all of its traffic through our TOR machine. We're accomplishing the same feat as the above example, but we don't need the VPN service (which remember, comes at a price).

![](https://www.coveros.com/wp-content/uploads/2017/04/Router-proxied-through-TOR.jpg)

  * The entire network is secure, no need to install anything on any individual system.
  * All traffic is secure.
  * No need to pay for a VPN service.

#### Cons

  * A more complicated initial setup is required.
  * Associated costs with equipment.
  * Slows down internet speeds.

### Setting Up the Machine

In order to build our 'black box of privacy', the first thing we need to do is set up the 'hardware.' Now, at this stage, you have two options; build a physical machine, or build a virtual one. The specs for both the physical and virtual machine will be similar. Ideally, we'll want a machine with 2 cores, and at least 1 gig of RAM. The required hard-drive space should be minimal, but I always suggest having at least 10 gigs, just because operating systems are getting larger, and having more swap file space is always a good idea. Additionally, ensure that you have 2 network adapters for the machine.

I won't go into all of the details of building a physical machine, I'll just assume you have these components assembled into something usable. For a virtual machine, I suggest using VirtualBox, simply because it is open-source and free. There are plenty of other tools you can use, and for a simple setup, VMWare would also work just fine. You'll want to create your base machine with the basic information listed above. To add additional network adapters, instructions can be [found here](https://forums.virtualbox.org/viewtopic.php?f=3&t=36574) for VirtualBox, and [here](https://www.vmware.com/support/ws55/doc/ws_net_configurations_changing_vadapters.html) for VMWare. You should ensure that the configuration setting is for NAT, not Bridged or Host-Only.

Once we have the machine setup properly, we'll want to install our operating system. I would suggest running an open-sourced (read as free) OS like [Ubuntu](https://www.ubuntu.com/download/server) or [CentOS](https://www.centos.org/download/). For these instructions, I will move forward assuming an installation of Ubuntu, but there is no reason that needs to be the case. First, download an image of your chosen OS. I have linked the OSes above to their download links; I always suggest going with the LTS version when available. Once you have downloaded the ISO (or bootable image if installing on a physical machine), run through the basic installer on the machine.

### Configuring the Network

We need to ensure that your machine knows what to do with its two network interfaces. What we desire is for traffic to come in on one interface, and get forwarded to the second (after going through our security measures first). To do this, we just need to set up a few simple rules on our machine. Typically, the network interfaces are named eth0 and eth1. If yours are named differently, make the appropriate changes in the below steps.

First, we want to enable IP forwarding. We can do this in multiple ways, but the simplest is to turn it on within the system processes. To accomplish this, set the value of _/proc/sys/net/ipv4/ip_forward_ to 1. We can do this with the below command

Finally, all we need to do is add our rules indicating that we want to forward traffic from eth0 to eth1.

Ensure you note the address of eth0, as this will be where you want to point all of your network traffic. That's it, we're now ready to start setting up our machine for the specific task, and pointing our router at the machine.

### Passing Router Traffic Through TOR

Now that we have the machine configured, it's time to get our router traffic to run through TOR. First, we need to configure our 'black box of privacy' to be running TOR, and here-forth this machine will be referred to as our 'TOR machine.' We'll need to install TOR on our TOR machine, and we can follow the same instructions as above. If you installed the server version of the operating system, it probably doesn't have a display. If this is the case, then you'll need to set up a virtual display for the browser. You should install Xvfb with the below command to allow our browser to run without an issue.

The last step of our TOR install is to ensure that it is always running so that we can always pass our traffic through TOR via our proxy. To do this, we want to set up a simple service. First, create the below file in _/lib/systemd/system_ and name it _tor.service_.

Replace _/path/to/tor_ with the location where you installed TOR, and only include the _ExecStartPre _command if you needed to install Xvfb in the above steps. To complete our TOR install, we want to enable and start our TOR service with the below commands:

Once that is completed, we'll want to obtain the proxy information to connect through TOR.

Finally, we just need to configure our router to pass all traffic through TOR. If you have already configured your router to run DD-WRT, this is very simple. Navigate to Administration -> Commands, and paste the below code into the text area

You need to replace 127.0.0.1 with the IP of eth0 that you configured earlier in both lines. You also need to replace 3128 with the port that the TOR proxy is listening on. Click the Run Commands button, and finally click the Save Firewall button. That's it. All traffic on your network connecting to your router is being passed through TOR.

## Run Network Through TOR or VPN

You may not have a router that you can install DD-WRT on, and you might not want to spend money on one that you can. That doesn't mean you're out of luck. Rather than using software to route all of your traffic, you can just setup your network so that all outbound traffic from your router passes through another machine (virtual or not) before it hits your modem. In this case, this other machine becomes your 'black box of privacy,' and will need an additional network card (again, maybe it's virtual). Configure your 'black box of privacy' to accept inbound traffic, and then setup TOR as a system proxy, or setup a VPN (see the above instructions) to run on it. This way, all traffic passed from your router to your modem goes through this machine and gets protected.

![](https://www.coveros.com/wp-content/uploads/2017/04/Router-through-TOR2FVPN.jpg)

####   
Pros

  * The entire network is secure, no need to install anything on any individual system.
  * All traffic is secure.
  * Your option to pay for a VPN service or not.
  * No router configuration.
  * A much more complicated initial setup is required.
  * Potential associated costs with equipment and/or VPN provider.
  * Slows down internet speeds (if taking the TOR route).

### TOR

Setup your machine the exact same way as you did for our previous example, and setup the networking the same way as well. Similarly, install TOR like the above to run as a service, and enable it. Rather than using the router to push all traffic through TOR, we'll actually just build the network pipeline to have all traffic move through the TOR machine. In order to accomplish this, we'll want to setup our network to have our router's output connect to our TOR machine, and our TOR machine connect to our modem.

![](https://www.coveros.com/wp-content/uploads/Router-proxied-through-TOR.jpg)

### VPN

This setup isn't too much more complicated than the one given above. Similarly, you'll want to ensure that you have setup your VPN Machine (your 'black box of privacy'), your OS is properly setup, and your network is configured. Once that is completed, you'll want to setup and install your VPN as a service.

When selecting a VPN, ensure that the software supports a Linux machine and that you can run your VPN client from the command line. Once you determine what those steps are, we'll want to setup a service to run the VPN (similar to what we did with TOR), so that the VPN is always running, it runs on startup, and restarts itself on failure. First, create the below file in _/lib/systemd/system_ and name it _vpn.service._

Replace _COMMAND TO RUN VPN_ with the command you determined above to launch your VPN. Finally, to complete our service setup, we want to enable and start our VPN service with the below commands.

Similar to above, again, ensure that your VPN machine is hooked up in between your router and modem, to ensure all traffic passes through it.

![](https://www.coveros.com/wp-content/uploads/Router-through-TOR2FVPN.png)

### Run Network Through pfSense

Setting up a VM to handle traffic like described above is not simple. In addition to the basic machine setup just to get the traffic to work, you need to worry about ensuring your machine (virtual or not) is setup properly and securely. Managing that machine might also be a challenge. Enter [pfSense](https://www.pfsense.org/): an open-sourced operating system designed for secure network traffic. This last configuration is similar to our machine and networking setup in the above option, however, the base OS of the machine would be pfSense. Alternatively, instead of building (physical) or creating (virtual) a machine to run pfSense, you can just buy a small cheap machine, specifically designed for this sort of traffic, with pfSense already installed on it. Many more networking options open up with pfSense, but I'll go into those with a future post. Your last step is to configure pfSense with TOR as a proxy server or configure your VPN service on it. The below steps will detail how to setup pfSense with your VPN, but you can follow similar steps running your router through TOR to pass all traffic through TOR as well.

![](https://www.coveros.com/wp-content/uploads/2017/04/Router-through-pfSense.jpg)

  * The entire network is secure, no need to install anything on any individual system.
  * All traffic is secure.
  * Your option to pay for a VPN service or not.
  * No router configuration.
  * A very complicated initial setup is required.
  * Potential associated costs with equipment and/or VPN provider.
  * Slows down internet speeds (if taking the TOR route).

### Machine Setup

The initial setup for the pfSense machine is a little more complicated. Once we get it going, however, it makes managing your security much simpler. First, download the [latest version of pfSense](https://www.pfsense.org/download/). You'll want to select the _Install_ version, and probably the 64-bit one as well (depending on the hardware you're running it on). Select the CD (ISO) if you're installing on a virtual machine, or a USB if installing on physical hardware.

If installing on a physical machine, ensure you have two network cards installed, and if installing on a virtual machine, ensure you've added two network interfaces. For this setup, it's not required for you to set up traffic forwarding, but ensure you have two adapters enabled: one bridged (for your outbound - WAN - traffic), and one internal (for your local - LAN - traffic). There is no need to change any of the other advanced settings.

### Initial Install

Upon first launching the machine with the ISO (or USB), choose the first option, to Boot pfSense. When prompted (after about 20 seconds), select _I_ to launch the installer. I prefer using the quicker Easy Install, as it'll get our machine setup with all of the expected settings. When prompted, use the default kernel, and then reboot the machine. Unmount the ISO, or remove the USB once prompted.

The machine will then prompt you for some initial setup. I usually skip setting up the VLAN and move onto setting up the network interfaces. I have always allowed pfSense to auto-detect the interfaces. If you are using VirtualBox, your interfaces are emX, and for a physical machine, they should be ethX. Numbering for these interfaces starts at 0. Before you proceed, ensure your network interfaces match up to what you expect and that your WAN (connection to our modem) and LAN (connection back to your network) looks correct.

At this point, a new screen should display showing you options to configure your machine. Note the LAN address of the system. If this address conflicts with another network address (say your modem is on the same IP address), choose option (2) to fix the setup. I personally like to change this just to keep this machine, and everything behind it, on its own subnet. After selecting 2, select (2) for LAN, then enter your new IPV4 address. I went with 192.168.2.1. I set a subnet bit count of 24, and let pfSense handle the DHCP. These are all things you might want to change to your own preferences. Finally, I answer no to using the HTTP web protocol. After this, pfSense told me I could access it by visiting https://192.168.2.1, and that's exactly what I did. I found it much easier to configure via the browser than the command line. This is one of the reasons I really like pfSense.

### VPN Configuration

After you've logged into your web interface (use username _admin,_ password _pfsense_), we can finally look at setting up our VPN. You'll be directed to a setup wizard, and you can accept the provided defaults. This is because we did the critical setup earlier. To setup our VPN, we want to open up our VPN Wizard by navigating to VPN -> OpenVPN in the menu items. From this point on, you'll need the VPN information from your VPN provider. Enter that information and select run for the VPN.

![](https://www.coveros.com/wp-content/uploads/Router-through-pfSense.png)

To check your VPN status, navigate to Status -> OpenVPN and ensure your VPN is running.

*I have gone through the process of setting up each of these options over the past few days. None of them were particularly difficult (_if you know what you are doing_). Most of the instructions I found online, but there were a bunch of bad suggestions/instructions out there. In an attempt to consolidate some good information, many steps I have just linked to; why rewrite the internet?
