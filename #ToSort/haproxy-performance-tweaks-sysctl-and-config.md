# HAProxy Performance Tweaks: sysctl and config

_Captured: 2017-05-08 at 16:19 from [dzone.com](https://dzone.com/articles/haproxy-performance-tweaks-sysctl-and-config?oid=twitter&utm_content=buffer5aa1e&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Download](https://dzone.com/go?i=212221&u=http%3A%2F%2Fresources.apicasystem.com%2Fguides%2Fintro-to-api-performance-testing%3Futm_source%3Ddzone%26utm_medium%3Dadvertising%26utm_campaign%3Darticle-asm) our Introduction to API Performance Testing and learn why testing your API is just as important as testing your website, and how to start today.

If you're running a high-performance HAProxy setup, there are many tweaks and settings that you can benefit from. Some of these can be complex, but there are many that can quite easily increase your performance. We'll give you some tips here to get that extra bit of performance you need!

Warning: These are mostly kernel changes and can cause unknown issues. Please Google any changes you are unsure of, or ask us!

## Sysctl.conf Changes

sysctl is a program used to tweak kernel settings on your OS. These can allow you to optimize specifically the way your kernel is handling things -- specifically, networking. If you are using Snapt, for HAProxy you can navigate to the **Setup** > **Configuration** > **Performance** menu. Alternatively, you can manually edit the `/etc/sysctl.conf` file.

These are specifically designed to optimize your Linux installation `forhaproxy`, allowing it to perform better under peak loads and allowing you to get more requests per second.

You can apply our selected tweaks by pasting the below into your `/etc/sysctl.conf` file, and then running `sysctl -p`" to apply the changes.

If any give you an error it may be because of a kernel version or anything else, just remove the relevant line. Remember to reboot or run `sysctl -p`" to apply this.

## Haproxy.cfg Config Changes

![](https://www.snapt.net/wp-content/uploads/2017/04/mode-300x202.jpg)

Below are several tips to keep in mind when creating or adjusting your `haproxy.cfg` file.

### Mode Selection

TCP mode groups are much less load than HTTP. Check your "mode" setting under a listen, frontend, or backend section of the config. If you don't need to do any HTTP level adjustments then TCP mode will be much faster.

### HTTP Tweaks

There are a lot of configuration changes that effect performance, but there are (as always) some easy tweaks to get more out of your server farm. Firstly, consider adding`option httpclose` to all your HTTP groups. In Snapt, this is called "Force HTTP Close." This will stop keepalives, but that will be to your advantage. Also, add `option abortonclose` - this will close aborted requests.

### Maxconn Setting

HAProxy limits connections on a global level as well as a frontend/listen level to the `maxconn` setting. It restricts the maximum number of connections HAProxy will accept (at a time), so make sure it's high enough. You can use this in groups as well as globally. In Snapt, this is called "Maximum Connections."

Make sure you don't have it set high in the "global" section of the config, but not high enough in the "listen" or "frontend" section!

### Balance Method

Only use what you require when choosing a balance method. Remember that `roundrobin` is going to be much faster, so if there is no requirement for a more advanced method don't use it (in performance sensitive situations).

### Compression

HTTP compression uses a lot of CPU, and if you are in a high-performance environment, you will want to disable it. This obviously has pluses and minuses.

Find scaling and performance issues before your customers do with our Introduction to [High-Capacity Load Testing guide](https://dzone.com/go?i=212222&u=http%3A%2F%2Fresources.apicasystem.com%2Fguides%2Fintro-to-high-capacity-load-testing%3Futm_source%3Ddzone%26utm_medium%3Dadvertising%26utm_campaign%3Darticle-alt).
