# Use a Raspberry Pi running Raspian OS behind a proxy server

_Captured: 2017-05-21 at 10:54 from [www.jeffgeerling.com](https://www.jeffgeerling.com/blogs/jeff-geerling/use-raspberry-pi-running)_

I've been working on figuring out some interesting ways to use my revision A Raspberry Pi, and one of the things I'm doing with it requires it to work correctly behind a corporate proxy server. If you're in a similar situation, and need your Pi to work with a proxy server, it's simple to get set up:

You need to edit the `~/.profile` file (where `~` is your home folder, e.g. `/home/jeffgeerling`, adding the following lines to the bottom of the file:

`# Proxy server (example: http://username:password@10.0.0.1:8080). User/pass optional.  
export http_proxy=http://[user]:[pass]@[proxy_server_address]:[port]  
  
# Proxy exclusions (don't use the proxy server for these hostnames and IP addresses).  
export no_proxy=localhost,127.0.0.0/8`

If you'd also like the proxy to apply when running `sudo` commands and when using your Pi as the root user, you need to add the same configuration to `/root/.profile` (this would be helpful if you need to use `sudo apt-get` to install or update software packages).

After you edit and save the file, you can either enter `source ~/.profile` to get the new proxy settings to stick for your current session, or log out and log back in.

One caveat: proxy support varies widely by browser--Midori is configured to use the proxy you set up by default, but [doesn't honor the no_proxy environment variable](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=540308). I tend to use Chromium instead, so it's not an issue for me.
