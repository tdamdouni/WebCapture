# Configuring local Jekyll webserver on WIFI network

_Captured: 2016-12-22 at 16:15 from [saifmulla.com](http://saifmulla.com/jekyll/2015/11/configuring-local-jekyll-webserver-on-wifi-network.html)_

It has been over a year I moved my blog to [GitHub.com](http://github.com) and [Jekyll](http://jekyllrb.com). Jekyll is a static site generator built particularly for blogging or static websites moreover it is the primary engine behind [GitHub pages](http://pages.github.com). GitHub pages is a free static website hosting service by GitHub powered by Jekyll where the contents could be fed from raw text files with [Markdown](https://en.wikipedia.org/wiki/Markdown) syntax. This post covers a simple guide to setting up and running a local webserver accessible over Wifi network.

#### Problem

Gone are the days when development and testing of website was done simply for desktops and laptop browsers, apparently browser compatibility issues is a exhaustive discussion in itself. Nowadays most websites are developed with responsive nature, meaning the same design must be compatible with various size of devices, ranging from large screen monitors, normal screen monitors, Tablets and Mobile phone etc. Correspondingly it must have similar look and feel or adapt to various screen sizes, therefore this requires testing your website design and content changes on various screen sizes.

Normally I simply use Jekyll to maintain my blog, which also includes my very own designed theme. So the development comprises configuring remote access on my mac and then accessing local Jekyll website on mobile and Ipad using Ip address of host. However eversince upgrading my Mac to El Capitan I have struggled with HTTP access. I had to quickly resolve this issue so ended up with some a simple setup.

#### Configuration

Typically after starting Jekyll server with default configuration it starts on **localhost** with port number 4000, localhost resolves to the local IP address 127.0.0.1 so the complete accesss url looks like **127.0.0.1:4000**. Although this address is accessible on the browser of the local machine, basically the host machine's browser but simply accessing the host server from another device using host's Ip address does not works, therefore when accessed using `<hostipaddress>:4000` results in message _cannot find server_.

Fortunately the solution to resolve this issues is configuring jekyll to start on Host 0.0.0.0 Ip address. For curious minds! here is the wikipedia definition for this IP address.

> _In the context of servers, 0.0.0.0 means "all IPv4 addresses on the local machine". If a host has two IP addresses, 192.168.1.1 and 10.1.2.1, and a server running on the host listens on 0.0.0.0, it will be reachable at both of those IPs._

The command to Jekyll serve will look like this `jekyll serve --host 0.0.0.0` on success it will print the following information along with informatio log.

`Server address: http://0.0.0.0:4000/`

Accordingly the url to access the local server will be similar to following
    
    
    127.0.0.1:4000 or localhost:4000 - for local on device access  
    192.168.0.10:4000 - for other devices on wifi network (assume 192.168.0.10 as host Ip)  
    

Moreover if you are keen to eliminate port number in url, such as simply using Ip then you could also configure Jekyll server to start on port number 80. It is a default port number for responding to HTTP requests, notably you must ensure if your http port isn't configured to another web server on your host or there is no existing webserver running or using port number 80. Moreover this requires Jekyll to be started with super user priviledges. Below is complete command to start Jekyll with required configuration.

`sudo jekyll serve --host 0.0.0.0 --port 80`   
`Jeykll server starts with the following configuration`   
`Server address: http://0.0.0.0:80/`

Subsequently the access url could now be requested without port number for all devices on the network, hopefully this post helps someone to resolve similar issue I faced, although similar setup could be used to resolve issues on Linux Host as well. Happy Blogging!!!
