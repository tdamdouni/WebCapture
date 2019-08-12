# Ghost blog on Docker in 5 mins

_Captured: 2017-08-29 at 10:25 from [blog.alexellis.io](https://blog.alexellis.io/ghost-on-docker-5mins/)_

**Pair Docker and Ghost for the perfect platform to run your blog! Read on, to get up and running in 5 minutes.**

![Ghost blogging platform](https://blog.alexellis.io/content/images/2016/04/ghost_small-2.png)

> [Ghost](https://ghost.org) is an elegant and minimal blogging platform that focus on simplicity. One of its most attractive features is its Markdown editor. It's also fully hackable running on Node.js with the [Handlebars](http://handlebarsjs.com) view-engine.

**Update:** After reading, check out the updated blog post on how to us Docker Volumes to keep upgrading and backing up your blog - hassle free. [Keep Shipping your blog with Docker Volumes](http://blog.alexellis.io/keeping-shipping-your-blog/)

![Raspberry PI](https://blog.alexellis.io/content/images/2016/04/pi_blog_top.jpeg)

I host [blog.alexellis.io](http://blog.alexellis.io) on the Raspberry PI Model 2 pictured above. It has been plugged into my home Internet connection 24/7 for the last 12 months (Sep 15-Sep 16) drawing around 1-2W of energy. It has served up over 82.6K page views (as recorded by Google analytics) to people from all-over the world.

I've put together three `Dockerfile`s for Raspberry PI 2/3, PI B/B+/Zero and regular PCs (x86_64). Get your blog up and running in 5 minutes by pulling a pre-built Docker image straight from the [Docker Hub](https://hub.docker.com/r/alexellis2/ghost-on-docker/).

#### ISP/bandwidth problems?

Don't worry, I've also provided x86_64 Dockerfiles and images which can be used with a cloud provider.

### Benchmarks & Dockerfiles

> Star or fork on Github [alexellis/ghost-on-docker](https://github.com/alexellis/ghost-on-docker) for benchmarks on a cloud instance and Raspberry Pi compared.

### See also:

Enable quick upgrades and constant backups with Docker Volumes which exist outside of the container lifecycle.

  * [Keep Shipping your blog with Docker Volumes](http://blog.alexellis.io/keeping-shipping-your-blog/)

More on self-hosting:
