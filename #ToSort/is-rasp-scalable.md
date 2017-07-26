# Is RASP Scalable?

_Captured: 2017-02-23 at 09:52 from [dzone.com](https://dzone.com/articles/is-rasp-scalable?oid=twitter&utm_content=buffer60a8b&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

The short answer is: Yes. RASP is scalable when it is implemented correctly.

## What is RASP?

Runtime application self-protection (RASP) is not a single technology. It is a concept -- that protecting the application from within is the most efficient and effective way to provide true security for web applications. Different vendors interpret it in different ways and with sometimes vastly different approaches.

In general, the most promising and the most effective approach to RASP technology to ensure scalability is an in-process agent approach--the protection agent is embedded as a library inside the main application process.

## Why is RASP Scalable?

There are three main reasons RASP in-process, agent based technology is scalable.

  1. Granular control of monitoring and protection. A fully encapsulated, agent approach monitors and controls the behavior of the application. It does not monitor and control the syntax of the incoming requests like web application firewalls (WAF) or some of the unsophisticated, non-agent based RASP solutions. The benefit of this approach is less impact on application performance and better handling of a large volume of requests.
  2. Individual agents for applications. Modern web applications are deployed in a virtualized environment, either in a public or private cloud with elasticity achieved through instances of new virtual machines and containers. Each of the applications contains a RASP agent and each agent contributes a small overhead across each virtual machine or container. The benefit of this is that the RASP solution can scale together with the application that it protects.
  3. Designed for speed. The in-process RASP approach is designed for production environment. Other security testing technologies, such as interactive application security testing (IAST), are designed to find as many vulnerabilities as possible before deployment in production. RASP, on the other hand, is designed specifically to prevent exploitation in product environment. Because of that, it must adhere to much more stringent security, performance, service availability and scalability requirements.

To be able to keep your web application secure, no matter how they grow, look for a vendor with an in-process, agent based approach. That is the best RASP technology to ensure a system is secure and scalable, and will perform up to speed.
