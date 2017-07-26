# How I Do Continuous Delivery With My Personal Jenkins Server

_Captured: 2017-05-09 at 11:23 from [dzone.com](https://dzone.com/articles/how-i-do-continuous-delivery-with-my-personal-jenk?oid=twitter&utm_content=buffere09e5&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

[Download your copy of Continuous Delivery with Jenkins](https://dzone.com/go?i=181130&u=http%3A%2F%2Fjoin.cloudbees.com%2Fl%2F272242%2F2017-01-16%2F3ln26%3Futm_source%3Ddzone%26utm_campaign%3Dpipeline-plugin%26utm_medium%3Dwhitepaper) and learn how you can deliver better, software faster. Brought to you in partnership with [CloudBees](https://dzone.com/go?i=181130&u=http%3A%2F%2Fjoin.cloudbees.com%2Fl%2F272242%2F2017-01-16%2F3ln26%3Futm_source%3Ddzone%26utm_campaign%3Dpipeline-plugin%26utm_medium%3Dwhitepaper).

I suspect I am not alone in having my own personal Jenkins server. In fact, I have a cloud-hosted box on which I run quite a few different services:

  * Jenkins.
  * Jenkins build agents.
  * Nexus.
  * HAProxy with Let's Encrypt.
  * Some personal websites.
  * etc.

I thought it might be interesting to explain how I have set this up to do continuous delivery for my personal websites.

When I first set this up, I ran everything directly as services in the OS. But of course, the different services had different dependency requirements and maintaining it all was just a pain. The solution - for me - was obvious:

![Docker All The Things!](https://cdn.meme.am/instances/250x250/60577565.jpg)

So the base OS runs Docker and all my services are Docker containers.

  * Each Docker container is on an individual locked down virtual network.
  * I forward ports 80 and 443 to the HAProxy Docker container using a firewall rule on the main server.
  * HAProxy routes the requests to the individual Docker containers.
  * Each Docker container is managed by systemd using a custom template systemd script that I developed.

I am sure that there are more fancy setups I could configure, but this is a cloud machine that I am paying for myself _after tax_!

With this setup, however, I have my sweet-spot.

  * I can upgrade the OS and restart, all my applications and services stop and start correctly.
  * Because each application and service is running in a container, they are isolated from dependency changes in the OS.
  * I have a very tight set of firewall rules and the applications themselves are sandboxed.

You may have noticed, however, that Jenkins and my build agents are running as containers. And it probably has not escaped your notice that the applications and services that I use are all Docker containers. So how do I use Jenkins to manage all this from _within its sandboxed container_?

### Put a Hole in the Sandbox

So the first thing I have done is: I put a hole in the sandbox. There is one build agent that has the Docker socket bind mounted:
    
    
     docker run--name jenkins - agent - with - docker - v /
    
    
      var / run / docker.sock: /var/run / docker.sock--rm--net internal - jenkins jenkins - agent

This agent is not permanently on-line, rather it has the availability strategy of Take- this agent online when in demand, and offline when idle. It's not perfect security, if I were using CloudBees Jenkins Enterprise, I could use the [controlled agents](https://go.cloudbees.com/docs/cloudbees-documentation/cje-user-guide/index.html?q=controlled#_configuring_controlled_slaves) functionality to ensure that only those jobs that I explicitly approve can have access to this special build agent, which would give me an extra layer of protection. But I am the only user with permissions on the Jenkins instance, and it only watches the GitHub repositories that I have explicitly configured, so I am not overly concerned!

### Use Pipeline Multi-Branch to Develop Changes

I love multi-branch projects in Jenkins. Of course, since I invented them I would say that!

The basic pipeline looks pretty much like this:
    
    
         withMaven(jdk: 'java-8', maven: 'maven-3', mavenLocalRepo: '.repository') {

As an [Apache Maven](https://maven.apache.org) developer, I tend to use Maven for building Java web applications. There are one or two of my services where it was easier to use Make, but the majority of my applications are using Maven to build. I use [Fabric8's Docker Maven Plugin](https://dmp.fabric8.io/) to build the Docker images, so the important thing is to ensure that the tags are not updated unless we are on the master branch (This is because my systemd scripts always just run the latest tag).

So I can develop my changes using a PR and have Jenkins build and test the application, giving my commits the seal of approval - and I get email notification too. If I want to verify the application locally I can just build and run locally.

When I am ready to deploy, I click the Merge button on GitHub.

  * The changes are applied to master.
  * GitHub sends the webhook notification to Jenkins.
  * Jenkins starts the build.
  * Jenkins launches the agent with Docker.
  * The Docker image gets built and tagged.
  * Because we are on the master branch, we execute the deploy stage.

### The Deployment Secret Sauce

Earlier I said that the services were managed by systemd. In fact, I have a cron task running as root that - as well as tidying up any unused Docker containers - will kill any Docker containers that have been lying around for too long and are not in the "managed" list. This is important as otherwise a build could fail at just the wrong point in time and leave a container running. If that happens too often the system could become overloaded.

One consequence of this, from a deployment perspective, is that the even the build agent with the Docker socket mounted could not deploy the tagged image into production. If the container was restarted using Docker by other than root, the container id would change and it would get killed by the cron task. So we need root to restart the service, however, we don't want to give root access to the build agent.

What I have done instead is set up a special ssh user, called reload. In reload's ~/.ssh/authorized_keys file I have given each application and service their own key and the key will just run a specific command:
    
    
     ssh - rsa AAAAB3NzaC1yc2.....kONZ reload - service - foo command = "touch service-bar"
    
    
     ssh - rsa AAAAB3NzaC1yc2.....eI9p reload - service - bar

The reload user cannot login to a shell, the only thing you can do is login with one of the service-specific keys and that will touch a file and exit. The reload user is also configured to only accept connections from the Jenkins build agent.

The cron task that runs as root now just looks for the service file and if present deletes it and restarts the corresponding service, e.g. something like:
    
    
      if [-f / home / reload / service - $s] then rm - f / home / reload / service - $s systemctl restart docker - service - $s.service fi done

So now we just need the deploy step… which is actually quite simple:

I use the [sshagent](https://jenkins.io/doc/pipeline/steps/ssh-agent/#sshagent-ssh-agent) step to make the SSH key available. For each service, I use the folder scoped credentials store to hold the SSH Key and each time I just use the ID reload.

![](https://www.cloudbees.com/sites/default/files/blog/2017-personal-cd-workflow-folder-scope.png)

Thus each application only has access to its own SSH key and only from the master branch.

### The End Result

Here's a quick unedited real-time demonstration where I updated the copyright year from 2012 to 2017 on one of my personal domains:

[Discover how Docker, Jenkins and DevOps](https://dzone.com/go?i=181131&u=http%3A%2F%2Fjoin.cloudbees.com%2Fl%2F272242%2F2017-01-16%2F3ln1x%3Futm_source%3Ddzone%26utm_campaign%3Ddocker-jenkins%26utm_medium%3Dwhitepaper) are coming together to accelerate innovation. Brought to you in partnership with [CloudBees](https://dzone.com/go?i=181131&u=http%3A%2F%2Fjoin.cloudbees.com%2Fl%2F272242%2F2017-01-16%2F3ln1x%3Futm_source%3Ddzone%26utm_campaign%3Ddocker-jenkins%26utm_medium%3Dwhitepaper).
