# First impressions: Docker for Mac with Kubernetes

_Captured: 2018-02-06 at 10:14 from [blog.alexellis.io](https://blog.alexellis.io/docker-for-mac-with-kubernetes/)_

I'm excited to say that [Docker for Mac](https://www.docker.com/docker-mac) is now shipping with support for both Docker Swarm and Kubernetes built-in. Let's take a look at what this means, a brief history of developer tooling and then cover my first impressions as I kick the tyres.

## Why does this matter to developers?

Docker CE (nee. Docker) is a piece of software which has brought the benefits of containers to the people (democratisation) and made them extremely easy to use and valuable (commoditisation). This has been a journey and we didn't start day one with Kubernetes support in Docker for Mac, so let's look at the context:

Containers (which normally means Linux containers) were not available on Windows or Mac when Docker began its story as a spin-out from DotCloud.

## Docker tooling - a brief history

Here's a a brief history of developer tools and how they brought Linux containers to Mac and Windows users:

### Virtual machines - version 1

Before any of this tooling someone on a Mac or Linux computer who wanted to access Linux container would have needed to have installed a Virtual Machine host such as VirtualBox or VMWare Workstation/Player. They would need to install a Linux host manually and then set up shared folders. Sometimes people also use [vagrant from Hashicorp](https://www.vagrantup.com) to provide a consistent CLI between VM host software.

**Use when:** none of the following options work for you. This option is not recommended.

### Docker Machine

Docker Machine was the next step in the tooling evolution. Docker Machine automated the setup of a virtual machine on a local or remote environment and made use of standard ISO images (`boot2docker`) plus a writeable disk area. This also meant upgrading from one version to another was easy.

Once the VM was running SSL certificates were generated and then the Docker client accessed the remote or local VM over TCP/IP. It could support multiple-concurrent Docker versions or hosts at the same time for clustering.

Pros:

  * multiple Docker back-ends even on the same computer
  * works on Linux
  * uses simple distribution `boot2docker`
  * pluggable architecture - with plugins for major cloud providers / distros

Cons:

  * CLI-driven
  * Less "native" integration on Windows / Mac 

**Use when:** you're on Windows 7 or Windows 10 Home or need a cluster of machines on your local computer. Or you're creating/managing a remote cloud cluster.

### Docker for Mac/Windows

The problem with Docker Machine was that it involved too many manual steps (`docker-machine env` etc) and configuration sometimes needed to be regenerated for TLS. Docker for Mac/Windows or DfM was pitched as a "native" integration which meant it came with a UI and a menu-bar that was hugely popular. The initial release of DfM was through a limited beta and there was a big demand on Twitter for it.

Pros:

  * 1-click install
  * Command-line is automatically configured
  * Configuration through UI for proxies / registries etc
  * Can be started/stopped with a single click

Cons:

  * DfM has had performance issues with shared volumes
  * High CPU usage is reported by `hyperkit` resulting in low battery life
  * Only available on Windows 10 pro or enterprise

**Use when:** it's available to you and you need Docker Swarm or Kubernetes support for local development.

### Minikube

Minikube has a very similar user-experience to `docker-machine` and also relies on `boot2docker`. Its primary purpose is to create a single-node Kubernetes cluster which also includes a Docker host that can be used for development.

![](https://blog.alexellis.io/content/images/2018/01/Screen-Shot-2018-01-07-at-10.25.36.png)

Example output of starting up `minikube` on my Mac:
    
    
    $ minikube start
    Starting local Kubernetes v1.8.0 cluster...  
    Starting VM...  
    Getting VM IP address...  
    Moving files into cluster...  
    Setting up certs...  
    Connecting to cluster...  
    Setting up kubeconfig...  
    Starting cluster components...  
    Kubectl is now configured to use the cluster.  
    Loading cached images from config file.  
    

Pros:

  * Easy access to Kubernetes for local development
  * It works

Cons:

  * Kubernetes uses a significant amount of battery at idle
  * Docker integration feels similar to `docker-machine`
  * Docker version lags behind significantly (i.e. no multi-stage builds until recently)
  * Some features hard to access or not officially supported such as RBAC (role-based authentication control)
  * Should use `minikube start/stop`

**Use when:** you need a local Kubernetes environment but don't mind if the Docker version is older.

To summarise the tooling there are pros and cons to each option. Let's move onto my first impressions of Kubernetes on Docker for Mac.

## First impressions

Here are my first impressions through getting hold of the update, kicking the tyres with an application and seeing what the Docker "stack" integration is like..

### Getting it

You currently need to be on the "edge" track of Docker CE in 17.12 or greater to get Kubernetes support. The support is then downloaded via a UI option and this can take several minutes.

![](https://blog.alexellis.io/content/images/2018/01/Screen-Shot-2018-01-07-at-09.39.57.png)

### Contexts and namespaces

If you've ever installed `minikube` then you'll have to switch out of that context into the DfM context otherwise `kubectl` will hang.
    
    
    kubectl config use-context docker-for-desktop  
    

> If you find that too verbose to type in then the Kubernetes community has a tool called [kubectx](https://github.com/ahmetb/kubectx) that make that shorter.

One of the other key differences between Docker Swarm and Kubernetes is the support for namespaces. By default parts of the Kubernetes ecosystem run as containers in a hidden namespace called system.

To view all containers running type in `kubectl get all --all-namespaces`:

![](https://blog.alexellis.io/content/images/2018/01/Screen-Shot-2018-01-07-at-09.47.28.png)

You'll see that a lot of services are running by default. This is in effect the same as what is running for Docker Swarm, but it's hidden from you and baked into a few fixed binaries rather than being split out to this degree.

Let's check which version got shipped?
    
    
    $ kubectl version
    Client Version: version.Info{Major:"1", Minor:"8", GitVersion:"v1.8.2", GitCommit:"bdaeafa71f6c7c04636251031f93464384d54963", GitTreeState:"clean", BuildDate:"2017-10-24T19:48:57Z", GoVersion:"go1.8.3", Compiler:"gc", Platform:"darwin/amd64"}  
    Server Version: version.Info{Major:"1", Minor:"8", GitVersion:"v1.8.2", GitCommit:"bdaeafa71f6c7c04636251031f93464384d54963", GitTreeState:"clean", BuildDate:"2017-10-24T19:38:10Z", GoVersion:"go1.8.3", Compiler:"gc", Platform:"linux/amd64"}  
    

Looks like we get 1.8.2 which is not the latest but does include all the most important features.

### Docker's integration

Docker is attempting to make Kubernetes easy to use for Docker Swarm users by creating an integration between Docker stacks (as seen in Swarm) and Kubernetes native deployments/services.

Kubernetes is by nature extensible and Docker are using [Custom Resource Definitions (CRDs)](https://kubernetes.io/docs/concepts/api-extension/custom-resources/) which add a "stack" concept. It means you can do this:
    
    
    $ kubectl get stacks
    No resources found.
    
    $ kubectl get crd
    NAME                        AGE  
    stacks.compose.docker.com   24d  
    

Let's try a Docker compose file I have and see what happens:
    
    
    $ docker stack deploy prometheus -c ./docker-compose.yml 
    Stack prometheus was created  
    Waiting for the stack to be stable and running...  
     - Service exporter has one container running
     - Service grafana has one container running
     - Service prom has one container running
    Stack prometheus is stable and running  
    

Here's the CRD:
    
    
    $ kubectl get stacks
    NAME         AGE  
    prometheus   1m  
    

And it appears to have created some Pods:
    
    
    kubectl get pods  
    NAME                        READY     STATUS             RESTARTS   AGE  
    exporter-66c7bbfcc6-r5sq4   1/1       Running            0          2m  
    grafana-7c5f5f6b75-rfgzp    1/1       Running            0          2m  
    prom-76b4f584f7-qckc9       0/1       CrashLoopBackOff   4          2m  
    

Prometheus has an issue that I can debug by typing in: `kubectl logs pod/prom-76b4f584f7-qckc9`.

Take away - if you're still using `docker-compose` for development or production - you can probably move straight to Kubernetes and enjoy the benefits of clustering.

### Native workflow

So for a native workflow we'd expect a few things:

  * `kubectl apply` with YAML works
  * `helm` works
  * `RBAC` is enabled

Let's try to deploy OpenFaaS - Serverless Functions Made Simple for Docker and Kubernetes.
    
    
    $ mkdir -p go/src/github.com/openfaas/ && \
     cd go/src/github.com/openfaas/ && \
     git clone https://github.com/openfaas/faas-netes && \
     cd faas-netes && \
     kubectl apply -f ./yaml
    

> If you run into an error about namespaces then type in `kubectl apply -f ./namespaces.yml` in the `faas-netes` folder and try again.

This is a good test because OpenFaaS will display a UI at localhost:31112 and also uses both RBAC and two namespaces (openfaas / openfaas-fn).

We see no errors:
    
    
    service "alertmanager" created  
    deployment "alertmanager" created  
    configmap "alertmanager-config" configured  
    service "faas-netesd" created  
    deployment "faas-netesd" created  
    deployment "gateway" created  
    service "gateway" created  
    service "nats" created  
    deployment "nats" created  
    service "prometheus" created  
    deployment "prometheus" created  
    configmap "prometheus-config" configured  
    deployment "queue-worker" created  
    serviceaccount "faas-controller" configured  
    role "faas-controller" configured  
    rolebinding "faas-controller-fn" configured  
    

The services are created too. See them by typing in:
    
    
    $ kubectl get all --namespace openfaas
    

Now open the UI and deploy a function using the store:

<http://localhost:31112>

![](https://blog.alexellis.io/content/images/2018/01/Screen-Shot-2018-01-07-at-10.00.37.png)

Then select Figlet - figlet is a Linux binary that can generate ASCII text-logos.

![](https://blog.alexellis.io/content/images/2018/01/Screen-Shot-2018-01-07-at-10.00.51.png)

You'll see the Function/Pod created here:
    
    
    $ kubectl get all --namespace openfaas-fn
    NAME            DESIRED   CURRENT   UP-TO-DATE   AVAILABLE   AGE  
    deploy/figlet   1         1         1            1           8m
    
    NAME                   DESIRED   CURRENT   READY     AGE  
    rs/figlet-676c995d66   1         1         1         8m
    
    NAME            DESIRED   CURRENT   UP-TO-DATE   AVAILABLE   AGE  
    deploy/figlet   1         1         1            1           8m
    
    NAME                   DESIRED   CURRENT   READY     AGE  
    rs/figlet-676c995d66   1         1         1         8m
    
    NAME                         READY     STATUS    RESTARTS   AGE  
    po/figlet-676c995d66-rqjpn   1/1       Running   0          8m
    
    NAME         TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)    AGE  
    svc/figlet   ClusterIP   10.101.45.157   <none>        8080/TCP   8m  
    

> Kubernetes uses more primitive objects to make up a "service" than Docker Swarm. Find out more about Kubernetes fundamentals below.

Now invoke the function and see the result:

![](https://blog.alexellis.io/content/images/2018/01/Screen-Shot-2018-01-07-at-10.14.33.png)

It works very well and was really easy to deploy. This will help the community maintain and build the Kubernetes integration for OpenFaaS.

I said we'd need `helm` to work too, which is a package manager for distributing software like OpenFaaS, Minio or similar. The equivalent doesn't exist for Docker Swarm.

I saw this Tweet before writing the post so it looks like `helm` also works out the box:

> Just setup [#kubernetes](https://twitter.com/hashtag/kubernetes?src=hash&ref_src=twsrc%5Etfw) on the [@Docker](https://twitter.com/Docker?ref_src=twsrc%5Etfw) for Mac beta and did a [#helm](https://twitter.com/hashtag/helm?src=hash&ref_src=twsrc%5Etfw) install... this is so so great!!
> 
> -- Adnan Abdulhussein (@prydonius) [December 15, 2017](https://twitter.com/prydonius/status/941615338726281216?ref_src=twsrc%5Etfw)

One of the key advantages of having this new support in Docker for Mac is not the stacks integration - it's the simplicity, speed and ease of use over existing tools. I believe a portion of existing Docker Swarm users will make use of the stacks integration and it could be a useful upgrade path for them if they decide to move to Kubernetes.

> Is Docker Swarm dead? I don't have any inside information as a member of the Docker Captains group, but what I've been told generally is that while there is a customer-base for Docker Swarm it will continue to be supported. For example the original Swarm that ran as individual containers is still supported by [Docker's UCP product](https://docs.docker.com/datacenter/ucp/2.2/guides/).

If you read the [developer reactions on Hacker News](https://news.ycombinator.com/item?id=16084243)   
you'll see Swarm still has its fans and if Kubernetes wants to convert them then my impression is that installation/maintenance for on-prem installations needs to improve.

So as for my first impressions - it's great and everything I was expecting to work does. I'm really impressed with what Docker has done with Docker for Mac and the internal components that make it up like LinuxKit.

**Follow and share**

Follow me and share this post on Twitter to help me get to 10k followers:

> First impressions: Docker for Mac with Kubernetes and a brief history of developer tooling - <https://t.co/XVlTaW8tgz> [@docker](https://twitter.com/Docker?ref_src=twsrc%5Etfw) [@kubernetesio](https://twitter.com/kubernetesio?ref_src=twsrc%5Etfw) [pic.twitter.com/YrftDCEwEa](https://t.co/YrftDCEwEa)
> 
> -- Alex Ellis (@alexellisuk) [January 7, 2018](https://twitter.com/alexellisuk/status/949953728924266498?ref_src=twsrc%5Etfw)

### See also:

I highly recommend reading the differences between Docker Swarm and Kubernetes - even if you're a Kubernetes veteran, this blog post may be useful for your colleagues and friends:

  * Star: Award-winning [OpenFaaS - serverless functions](https://github.com/openfaas/faas/) you can run yourself on Kubernetes or Docker Swarm

> "Docker Captains are experts and leaders in their communities who demonstrate a commitment to sharing their Docker knowledge with others."

Alex Ellis is a [Docker Captain](https://www.docker.com/community/docker-captains) and the author of the [OpenFaaS project](https://www.openfaas.com/)
