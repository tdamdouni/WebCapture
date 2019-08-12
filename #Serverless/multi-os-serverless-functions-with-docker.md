# Multi-OS Serverless functions with Docker

_Captured: 2017-09-13 at 20:36 from [blog.alexellis.io](https://blog.alexellis.io/multi-os-serverless-cluster/)_

In this post I'll show how you can build and deploy multi-OS Serverless functions with Docker and the [OpenFaaS](https://www.openfaas.com) and why multi-OS clusters are important.

> OpenFaaS is a serverless functions framework for Docker and Kubernetes which is experiencing viral growth and interest.

![](https://blog.alexellis.io/content/images/2017/09/multi.png)

_Windows and Linux play well together with Docker_

### Why do we need multi-OS?

In the container world Linux dominates, but as of last year [Windows Containers](https://blog.alexellis.io/tag/windows/) support became GA and that meant running ad-hoc Docker containers with Windows executables was possible on Windows 2016 Server Core and Windows 2016 Nano Server.

> See also: [Windows Containers on Windows Server](https://docs.microsoft.com/en-us/virtualization/windowscontainers/quick-start/quick-start-windows-server) Companies which have a skill-set based around the Windows operating system or legacy products to support can still benefit from using containers for packaging and running their code. Some companies make use Windows technology like .NET 4.5 alongside back-end services running on Linux such as: Redis, MongoDB or RabbitMQ. 
> 
> Having a multi-OS or hybrid cluster means you can chose how to architect a solution - picking the right OS for each application or back-end.

## Use-case: a hybrid serverless cluster

With Docker Swarm it's now possible to bootstrap a mixed-OS cluster and deploy services to the correct nodes through "placement constraints".

> I'm going to list everything you need to do to deploy [OpenFaaS](https://www.openfaas.com) on a multi-OS Linux and Windows cluster including a tester function for Windows.

### Definitions

**What is a placement constraint?**

A placement constraint specifies things which must be true about a node for Swarm to place your container there.

  * Linux only:
    
    
    docker service create --publish 80:80 --constraint "node.platform.os == linux" nginx  
    

  * Windows only
    
    
    docker service create --publish 80:80 --constraint "node.platform.os == windows" microsoft/sample-nginx  
    

There are other properties of nodes we can use for placement constraints including node labels such as a label for nodes with "SSD" storage, or high network bandwidth.

> Constraints are also available in Kubernetes - [Assigning Pods to Nodes](https://kubernetes.io/docs/concepts/configuration/assign-pod-node/)

### Build your cluster

  * Get Linux

You can provision your Linux host on any developer cloud or via a VM. We'll be using the Linux hosts to run the core [OpenFaaS](https://www.openfaas.com) services.

_Get Windows_

The easiest way to get a Windows 2016 server is to pick the Windows 2016 Datacenter edition from the Azure marketplace. There is also a free alternative in [Play With Docker](http://microsoft.play-with-docker.com) which will give you a temporary VM for 1.5-5 hours.

![](https://blog.alexellis.io/content/images/2017/09/Screen-Shot-2017-09-11-at-23.05.03.png)

Once you have setup two VMs or two hosts on the cloud you can connect them together with two commands:

On the Linux host:
    
    
    $ docker swarm init --advertise-addr=<linux_public_ip_here>
    

On the Windows host:
    
    
    $ docker swarm join <join-token> <linux_public_ip_here> --advertise-addr=<windows_public_ip_here>
    

> Use the join-token from the command above, or type in `docker swarm join-token worker`.

An important step is to include the flag `\--advertise-addr` which is not part of the default output you receive from the Docker CLI.

  * Now verify the hosts are connected:
    
    
    ID                            HOSTNAME            STATUS              AVAILABILITY  
    k9ailx1aj9rrr9l0fb6zlk6bd *   lin-01              Ready               Active  
    tnnccnfrhc296r88ou1q0cuxu     win-01              Ready               Active  
    

> In this example I provisioned both hosts in the same region to reduce latency and data transfer fees.

  * Deploy OpenFaaS

> Functions as a Service (OpenFaaS) - a serverless framework for Docker & Kubernetes is available on [GitHub](https://github.com/alexellis/faas).

On the Linux master deploy [OpenFaaS](https://github.com/alexellis/faas) \- this should take less than 60 seconds.
    
    
    $ git clone https://github.com/alexellis/faas
    $ cd faas
    $ ./deploy_stack.sh
    

> A full deployment [guide is available here for Docker and Kubernetes](https://github.com/alexellis/faas/tree/master/guide)

  * Build a Windows Dockerfile

When I asked a fellow Docker Captain Stefan Scherer what I could run in a Windows Container that wouldn't also run easily in a Linux container he suggested `ipconfig.exe` \- which gives the available IP addresses and adapters on a host or container.

![](https://blog.alexellis.io/content/images/2017/09/output.png)

> _This is a short blog post that you can follow along with while sipping your morning brew. I'll show…_

This is what your Dockerfile looks like for OpenFaaS:
    
    
    FROM microsoft/nanoserver:latest
    
    ADD https://github.com/alexellis/faas/releases/download/0.6.4/fwatchdog.exe fwatchdog.exe
    
    ENV fprocess="ipconfig.exe"
    
    CMD ["./fwatchdog.exe"]  
    

_Dockerfile_

I've already built and pushed a Docker image called `alexellis/windows-ipconfig:nano`.

  * Get the FaaS CLI

Grab the FaaS-CLI from the GitHub releases pages. Download the "faas-cli.exe" and save it within your C:\Windows directory or somewhere in the %PATH% variable.

<https://github.com/alexellis/faas-cli/releases>

Let's create a YAML stack file for the OpenFaaS CLI:
    
    
    provider:  
      name: faas
      gateway: http://localhost:8080
    
    functions:  
      ipconfig:
        image: alexellis/windows-ipconfig:nano
        skip_build: true
        environment:
          suppress_lock: true
        constraints:
          - "node.platform.os == windows"
    

_./ipconfig/stack.yml_

Since we already have an image built out we can now go ahead and deploy the function:
    
    
    > faas-cli.exe deploy -f stack.yml
    Deploying: ipconfig.  
    Removing old service.  
    Deployed.  
    200 OK  
    URL: http://remote_ip:8080/function/ipconfig  
    

You can now navigate to the OpenFaaS UI Portal on your Linux host via port 8080 and invoke the function or do it via the CLI with `faas-cli invoke --help`.

![](https://blog.alexellis.io/content/images/2017/09/Screen-Shot-2017-09-11-at-23.06.18.png)

> The IPv4 address of the container is highlighted in blue.

For an experiment you can scale up the `ipconfig` function to 5 replicas then hit "Invoke" over and over until you see all the IPv4 addresses shown in the command output.

### Wrapping up

So we've taken a look at placement constraints and node OS properties which are built into Docker Swarm. We prepared a hybrid cluster and then deployed a Linux application [OpenFaaS](https://www.openfaas.com) and create a Serverless function for a native Windows binary, then scaled it up.

> Please show support for the Open Source project and **Star** the [GitHub repo](https://github.com/alexellis/faas).

**Find out more about OpenFaaS and Serverless**

> New to Docker? [Get started with Docker here](https://www.docker.com/get-docker)
