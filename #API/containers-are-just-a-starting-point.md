# Containers Are Just a Starting Point

_Captured: 2017-08-04 at 23:50 from [dzone.com](https://dzone.com/articles/containers-are-just-a-starting-point?oid=twitter&utm_content=buffera02b7&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Site24x7](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227232&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

Containers, Docker, Kubernetes have been around for four years now. Some people are even starting to refer to this technology as mature! I would strongly argue, however, that the implementation of containers infrastructure is still very much in its growth stage.

This blog post will focus on the other parts of the container infrastructure. Everything else but the containers. They are just a starting point.

## Containers Recap

### What Is Docker?

Docker revolutionized the software technology in 2013, by simplifying the existing concept of microservices. It is best described as a tool that can package any application and its dependencies in a virtual container.

Read the conversation between web developer and container consultant to get a [better idea on containers implementation](http://blog.cloud66.com/cloud66-now-supports-docker/).

### What Is Kubernetes?

Kubernetes is an open source tool developed by Google to manage containerized apps in a clustered environment. It was essentially created to manage Docker and to address the disconnect between the way that modern, clustered infrastructure is designed.

So which one should you use?

In my opinion, use both for your production environment. Kubernetes orchestration compliment Docker and work together very well.

Kubernetes is the current market leader and has a large community for support. This is an opinionated tool, which is great as developers are on the same page and can follow the same guidelines, but it gives them less flexibility. It has a huge potential to become a standard in the container industry.

On the other hand, Docker Swarm (aka Docker Compose++) are really designed with development in mind; therefore they are easier to debug in the development environment. Not as powerful in production.

Also, it is worth remembering that all of the technologies above are open source. It is also important to understand a true value of open source. Read more on [the open source containerization conundrum](http://blog.cloud66.com/the-open-source-containerization-conundrum/).

## Infrastructure Besides the Containers

Starting from 'hello world' to running your containerized application is a long steep learning curve. Once you master the containers and learn your way around all the gotchas out there, you are ready to move to the next level, deploy, and maintain your app in production.

So, what developers have to consider to run their containerized infrastructure. The decisions for the containers strategy will positively or negatively impact the customers.

### Database

You can host your database in containers without worrying about I/O performance in a development environment. There is a lot more to consider in the production environment.

You need to think about the database storage components, backups, and replications. To run modern web app or mobile API scale the database to handle increase I/O base on demand, together with high availability and a reliable backup/restore strategy.

### Cloud Provider

Choose the right [cloud provider](http://blog.cloud66.com/part-2-comparing-the-speed-of-vm-creation-and-ssh-access-on-aws-digitalocean-linode-vexxhost-google-cloud-rackspace-packet-cloud-a-and-microsoft-azure/) for you, whether it is a bare metal, public cloud, or hybrid cloud. Investigate if your cloud provider can provide high availability within a region.

Lastly, look for flexible solutions as the container deployment process differs across cloud providers, and you don't want to end up locked up with one provider.

### Deployment Workflow Management

The aim is to achieve deployment without any downtime (a blue-green deployment). It can be designed by starting a cluster of replicas running the new version, while all the old replicas are still serving all the live requests.

It is important to choose the right set of tools, as the deployment management tools will vary considerably from development to production environment, as mentioned above with the Docker Compose case. Moving to the multi-host environment will increase the complexity, make sure you think ahead about the details of moving from a simple single-container application to a complex set of container images, where each image with multiple instances is connected to the load balancer for distributing workloads.

### Load Balancer & Service Discovery

Moving from a single container service to multiple containers across one or more hosts requires a load balancer to distribute incoming requests.

To deliver a seamless end-user experience a container apps need to communicate with each other and be able to deploy on any server or any containers cluster.

Tools, like Nginx or HAProxy are the popular choice for microservices load balancer. The trick is to keep their configuration up to date, bearing in mind the different versions that need to run at the same time. Developers face the networking challenges with the service discovery, which contributes to slower container adoption process.

### Security

Containers cannot be treated as small virtual machines, as they are 'snippets of the code with the shared kernel that runs independently of one another'. Quick adaptation of the containers requires a new security strategy. In productions, all container processes run on a single host, isolated from the risk of network intrusion and various attack vectors.

Make sure you apply firewall rules for your container stacks and protect them against denial of service and brute-force attacks. Also, discover tools like [Habitus.io](http://www.habitus.io/) a build flow tool for Docker can help you remove and manage the layers with secrets during the build process.

### Monitoring & Logs

Investigate the available options for the full stack container monitoring strategies to ensure that users can perform necessary functions with the application. Check that the current and the future loads don't cause a slow performance or outages and lastly bear in mind the troubleshooting and error handling.

Additionally, set up the log management to collect and aggregate log entries for one or more log servers. Think about the ways how to view and search your logs to support troubleshooting.

[Site24x7](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty) \- Full stack It Infrastructure Monitoring from the cloud. [Sign up for free trial.](https://dzone.com/go?i=227233&u=https%3A%2F%2Fwww.site24x7.com%2Ffeatures.html%3Futm_source%3DDzone-text%26utm_medium%3Dthirdparty)

### Like This Article? Read More From DZone
