# Microservices Architectures: 3 Overlooked Considerations

_Captured: 2017-06-11 at 02:02 from [dzone.com](https://dzone.com/articles/microservices-architectures-3-overlooked-considera?edition=304168&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-10)_

Find your next Integration job at [DZone Jobs](https://dzone.com/go?i=219251&u=https%3A%2F%2Fjobs.dzone.com%2Fjobs%2Fsearch%3Futf8%3D%25E2%259C%2593%26q%3DIntegration). See [jobs focused on integration](https://dzone.com/go?i=219251&u=https%3A%2F%2Fjobs.dzone.com%2Fjobs%2Fsearch%3Futf8%3D%25E2%259C%2593%26q%3DIntegration), or [create your profile](https://dzone.com/go?i=219251&u=https%3A%2F%2Fjobs.dzone.com%2Fprofiles%2Fsign_up) and have the employers come to you!

Microservices architectures have become a ubiquitous industry trend because of their promise of speed, agility, and scale. Just like any major paradigm shift, microservices adoption introduces many changes at the architectural, technical, and organizational levels. It is not uncommon to overlook some considerations in pursuit of microservices-based applications. While containers, orchestrations, automation, and service definition take up the majority of the mindshare, here we have identified three often-overlooked but critical considerations based on our customer conversations.

An overarching takeaway is that in a microservices architecture, complexity is shifting from being code-based to network-based. Therefore, service interactions become a much richer source of information for the health, performance, and security of microservices applications. [Netsil](https://netsil.com/) has leveraged this key insight and built the [Application Operations Center](https://github.com/netsil/manifests) (AOC) using service interactions as the source of truth. As we explore the considerations mentioned below, we will highlight how the AOC benefits SREs and operations teams in improving reliability and delivering service-level objectives (SLOs) for their microservices-based applications.

### Addressing the Common Requirements of Service Interactions

In microservices architectures, services interact heavily with each other to fulfill transactions. Each of these service interactions requires a subset of these common functionalities:

  * Connection pooling to avoid expensive overhead of creating a new connection for every request.
  * Automatic timeouts and retries for idempotent requests.
  * Ability to dynamically shift interaction to another replica of a service when initial target is experiencing latency. Unlike simple pulse-based load balancing, this goes further into leveraging more metrics to identify the right instance of a service.
  * Ability to flexibly route traffic among multiple instances of services. This is useful for blue-green and canary release management.
  * Leverage modern microservices glue protocols such as [gRPC](http://www.grpc.io/), [Thrift](https://thrift.apache.org/), etc. that are more efficient to transmit on the wire, offer request multiplexing and pipelining than HTTP.
  * Automatic or manual dependency modeling/mapping for documentation and quick incident response purposes.
  * Build, expose and maintain good APIs and contracts. Also, constantly address forward and backward compatibility.

One option is to build all these functionalities into each service interaction. A more efficient option is to employ lightweight proxy services such as [linkerd](https://github.com/linkerd/linkerd), [Envoy](https://github.com/lyft/envoy), or [Traefik](https://github.com/containous/traefik). From the perspective of operations teams, these additional components are critical dependencies that they should be able to visualize and monitor. The AOC has the strong advantage of automatically discovering all service interactions with such intermediate components without requiring any code change! Operations teams will see these components and their dependencies on a real-time map along with all the key performance indicators such as latency, throughput and error rates. The below picture shows the Kubernetes L7-Proxy as an example of the AOC's complete visibility into the hard-to-instrument intermediate services.

![Fig 1: Kubernetes Pods Shown on a Application Topology](https://d1miwa46wjqrlu.cloudfront.net/wp-content/uploads/2017/05/Screen-Shot-2017-05-02-at-21.47.11.png?x40029)

> _[Fig 1: Kubernetes Pods Shown on a Application Topology](https://d1miwa46wjqrlu.cloudfront.net/wp-content/uploads/2017/05/Screen-Shot-2017-05-02-at-21.47.11.png?x40029)_

### Think Shared Services, Not Shared Libraries

In any microservices application, many services will have a need for some common functions. Cache, key-value stores, distributed lock managers, and service discovery are good examples of such common functions used by multiple services. In the monolithic world, multiple components could simply use shared libraries for such common functions. And with handy techniques such as Docker or Packer, it might be tempting to bundle the shared libraries with all the services that use them. But continuing down the path of shared libraries becomes detrimental for at least two reasons:

  * Managing multiple copies of shared libraries and their dependencies would soon become a nightmare. Also, this runs afoul of the core principles of microservices, i.e. bounded context of services.
  * The situation becomes unsustainable when dev teams start using multiple programming languages and frameworks. Then it would be absolute waste to build and maintain multiple copies of shared libraries in different languages

The paradigm of building and using shared services can be seen in Netflix [EVcache](https://github.com/Netflix/EVCache), the popularity of redis and [etcd](https://github.com/coreos/etcd) for key-value stores, and growing use of products such as Consul for service discovery.

While it is important to realize and build shared services, it is equally important to ensure their health, availability, and performance. We've come across both providers and consumers of such shared services which may be from same or different teams. If you are a consumer team then quite often you don't know the details of the service itself but are concerned about its latency, throughput, and error rates. If you are a provider of shared services, you have additional concerns regarding saturation and capacity of these services.

All of these "[golden signals](https://netsil.com/blog/4-golden-signals-api-health-performance/)" are available to Netsil users irrespective of whether they own the services or are merely consuming them. Since Netsil leverages service-interactions as source of truth, it can monitor and present latency, throughput, error rates, and saturation without requiring any code instrumentation of these services. As an example, the picture below captures the golden signals for a shared Memcached service.

![Fig 2: Golden Signals for a Memcached Service](https://d1miwa46wjqrlu.cloudfront.net/wp-content/uploads/2017/05/Screen-Shot-2017-05-02-at-21.30.06.png?x40029)

> _[Fig 2: Golden Signals for a Memcached Service](https://d1miwa46wjqrlu.cloudfront.net/wp-content/uploads/2017/05/Screen-Shot-2017-05-02-at-21.30.06.png?x40029)_

### Don't Forget the Circuit Breakers

Failure is inevitable in a distributed system. The role of circuit breakers is to contain the failure and avoid propagating isolated failures to the entire application.

Let's say service A calls service B which in turn calls service C to fulfill a particular transaction. If downstream service C starts experiencing errors and experiences a time-out then service B and eventually service A will both start failing. In real world scenarios when such failures are left unchecked it can have disastrous effect impacting transaction integrity, causing data inconsistency and resulting in widespread outages of multiple services. Instead, if service B implements a circuit breaker paradigm, then the circuit breaker will monitor for failure of service C and when failures exceed specified thresholds it can invoke graceful error handling.

While it is important for development teams to implement circuit breakers for their services, it is equally important for the operations team to be alerted of "circuit break" incidents. Netsil provides multiple important features for handling such incidents:

  * A real-time auto-discovered map of the entire microservices application. Using this map, operations teams can quickly visualize and understand service dependencies.
  * Operations teams can define and monitor KPIs at the service level rather than worrying about individual instances. They get alerted when services start experiencing issues potentially even before a circuit break kicks in.
  * Commonly, circuit breakers are implemented using wrapper functions such as Netflix [Hystrix](https://github.com/Netflix/Hystrix). Netsil supports gathering metrics from circuit breaker functions using the standard statsd protocol. Circuit breaker functions can simply send incident metrics using statsd and Netsil will enable the analytics and alerting workflows on the metrics.
![Fig3: Netsil Enables Service-level Monitoring to Alert on Circuit Break Conditions](https://d1miwa46wjqrlu.cloudfront.net/wp-content/uploads/2017/05/Screen-Shot-2017-05-02-at-21.58.02.png?x40029)

> _[Fig3: Netsil Enables Service-level Monitoring to Alert on Circuit Break Conditions](https://d1miwa46wjqrlu.cloudfront.net/wp-content/uploads/2017/05/Screen-Shot-2017-05-02-at-21.58.02.png?x40029)_

Microservices bring a lot of value and a lot of changes. We hope this post has put the spotlight on the considerations that you will take into account. Based on your experience, if you have other important considerations then do share them in the comments section below.

Find your next Integration job at [DZone Jobs](https://dzone.com/go?i=219252&u=https%3A%2F%2Fjobs.dzone.com%2Fjobs%2Fsearch%3Futf8%3D%25E2%259C%2593%26q%3DIntegration). See [jobs focused on integration](https://dzone.com/go?i=219252&u=https%3A%2F%2Fjobs.dzone.com%2Fjobs%2Fsearch%3Futf8%3D%25E2%259C%2593%26q%3DIntegration), or [create your profile](https://dzone.com/go?i=219252&u=https%3A%2F%2Fjobs.dzone.com%2Fprofiles%2Fsign_up) and have the employers come to you!
