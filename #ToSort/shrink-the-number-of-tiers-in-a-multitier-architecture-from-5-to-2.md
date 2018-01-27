# Shrink the Number of Tiers in a Multitier Architecture From 5 to 2

_Captured: 2017-12-04 at 01:37 from [dzone.com](https://dzone.com/articles/shrink-the-number-of-tiers-in-a-multitier-architec?edition=343092&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-03)_

![Image title](https://dzone.com/storage/temp/7364216-header.jpg)

I am a contributor to many open-source projects, but one day, I decided to make my life easier by writing some open-source software for a task I needed to personally accomplish. So, I developed an upstream module for NGINX that helped me eliminate a thick bunch of tiers in a multitier architecture. It was such a fun experience that I've decided to share my results and publish them here.

## Introduction and Theory

![Image title](https://dzone.com/storage/temp/7364222-image1.jpg)

This is what the typical architecture of a microservice looks like. User requests come in through NGINX onto an application server. There is business logic running on the application server that the users interact with.

The application server does not hold any state, so you need to store states somewhere. You can use a database for that. Also, there is a cache to decrease latency and to ensure faster content delivery.

Let's give definitions to the tiers that are commonly present in an individual microservice:

  1. **Tier 1**: NGINX

  2. **Tier 2**: Application server

  3. **Tier 3**: Cache

  4. **Tier 4**: Database proxy (you need a proxy in order to secure the fault tolerance of your database and to persist connections to it)

  5. **Tier 5**: Database server

So, as I mentioned, I was thinking about the five tiers and it occurred to me that I should eliminate some of them.

Why eliminate tiers? I prefer keeping things simple and not having to maintain many different systems in production. Also, fewer tiers mean fewer failure points.

So, I created my Tarantool NGINX upstream module, which helped me reduce the number of tiers down to two.

![Image title](https://dzone.com/storage/temp/7364224-image2.jpg)

Tier 1 is NGINX, and Tiers 2, 3, and 5 are now replaced by Tarantool. Tier 4, the database proxy, is inside NGINX now.

The trick is that Tarantool is a database, a cache, _and_ an application server -- all in one. My upstream module is the glue that sticks NGINX and Tarantool together and lets them work without the other three tiers.

![Image title](https://dzone.com/storage/temp/7364227-image3.jpg)

This is what our new microservice looks like. A user sends REST or JSON RPC requests to NGINX with the Tarantool upstream module. This module connects directly to Tarantool, or it can balance the workload among many Tarantool instances. I use a super efficient protocol between NGINX and Tarantool based on [MessagePack](http://msgpack.org/index.html). You can find more information in this [article](https://medium.com/@vasiliysoshnikov/building-nginx-and-tarantool-based-services-c92492fc34c6) of mine.

Let's pause for a minute so you can install everything. I would advise you to install via packages or to use a Docker image (`docker pull tarantool/tarantool-nginx`).

### Docker Images

### Sources

### Documentation

## How to Use the Technologies

Here is an example of an `nginx.conf` file. As you can see, it uses a regular NGINX upstream parameter. We add a `tnt_pass` directive telling NGINX that there is a Tarantool upstream in a specified location.

`**nginx-tnt.conf**`:

So we've connected NGINX with Tarantool. What's the next step? We need to write a function and store it in a file. I'll call the file `app.lua`.
    
    
     box.schema.user.grant('guest', 'read,write,execute', 'universe')
    
    
     return 'first', 2, { str .. 'world!' }, http_request.args

Taking a closer look at the Lua code we can see:

  * `**box.cfg {}**`: This is telling Tarantool to start listening on port 3301 (it can also take other parameters).

  * `**box.once**`: This is telling Tarantool to execute a function provided that it has not been executed before.

  * `**function api()**`: This is our function, which I'm going to call soon. It is pretty simple, it takes an HTTP request as the first argument and it returns an array of values.

As mentioned, I store the code in a file named `app.lua`. I can execute it just by starting a Tarantool binary:

Let's call our function by using an HTTP `GET` request. I use `wget` for this. By default, `wget` puts the result into a file. So, I use `cat` to extract the contents of the file.

## Benchmarks

The following benchmarks are running with production data.

Input data for the benchmark is a large JSON object. Each object has an average size of 2 KB.

A single server with a 4-core CPU, 90GB RAM, and an OS of Ubuntu 14.04.1 LTS was used.

For this test, we used only one NGINX worker, a round-robin balancer. The worker is balancing the workload for two Tarantool instances and the instances are tied via sharding.

The following charts show us the number of reads per second. The top chart shows latencies (in ms).

![Image title](https://dzone.com/storage/temp/7364229-image4.jpg)

The next group of charts shows the number of writes per second. The top chart shows latencies (in ms).

![Image title](https://dzone.com/storage/temp/7364231-image5.jpg)

Impressive, right?

I hope that you will experiment with Tarantool and my module in order to simplify the architecture of your application. Please visit my module's [GitHub](https://github.com/tarantool/nginx_upstream_module) page or the Tarantool [Google Group](https://groups.google.com/forum/#!forum/tarantool) to share your experiences with it.
