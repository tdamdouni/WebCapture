# Docker Security: It's a Layered Approach

_Captured: 2017-12-10 at 20:40 from [dzone.com](https://dzone.com/articles/docker-security-its-a-layered-approach?edition=343111&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-10)_

Discover an in-depth knowledge about the different kinds of [iOS hacking tools](https://dzone.com/go?i=222228&u=https%3A%2F%2Fweb.securityinnovation.com%2Fhacking-ios-applications-dzone%3Futm_campaign%3DDZONE-Sponsorship-June-2017%26utm_source%3DAdvertising%26utm_medium%3Dhacking-ios-applications) and techniques with the [free](https://dzone.com/go?i=222228&u=https%3A%2F%2Fweb.securityinnovation.com%2Fhacking-ios-applications-dzone%3Futm_campaign%3DDZONE-Sponsorship-June-2017%26utm_source%3DAdvertising%26utm_medium%3Dhacking-ios-applications) iOS Hacking Guide from Security Innovation.

![](https://logz.io/wp-content/uploads/2017/11/docker_security_1_720.jpg)

It's no secret that containers (specifically Docker) are taking the industry by storm, and for several good reasons. They standardize deployment, allow developers to choose whichever library/framework best suits them, and scale out well with proper [orchestration](https://kubernetes.io/). Container technologies provide these benefits through the way in which they relate to the host system, by isolating processes while sharing a single kernel.

![](https://logz.io/wp-content/uploads/2017/11/image1-2-335x300.png)

Different containers may have their own CPU, memory, and IO constraints, but they all interface with the same kernel. The [image](https://www.docker.com/what-container) above illustrates this. Contrast this with virtual machines, where each machine uses its own dedicated kernel and other features that are separate from the host system.

While the container runtime (Docker for example) owns the security between processes in the container and the kernel itself, achieving robust security also requires that developers protect against any exploitation of the container process that could allow [escape from the container](https://blog.paranoidsoftware.com/dirty-cow-cve-2016-5195-docker-container-escape/) and the granting of privileged access to the host system.

In the past, security concerns were largely focused on kernel exploits and Docker's integration with the kernel, since this is where most exploits happen. These concerns were well warranted, especially since many people run container processes as root.

Yet container adoption hasn't halted or even slowed down. On the contrary, containers are becoming more widespread, secure, and useful. Adopting containers requires you to think differently about security, although existing best practices still apply. Let's take a look at some historical common vulnerabilities and exposures (CVEs) before discussing how to secure your stack.

## Past Issues

There are two noteworthy, relevant types of CVEs: [Linux kernel-specific issues](https://www.cvedetails.com/vulnerability-list/vendor_id-13134/Linuxcontainers.html) that apply to any container runtime (such as Docker or run-c) and [runtime-specific issues](https://www.docker.com/docker-cve-database) (this article focuses on Docker).

A quick skim through these issues reveals that the majority target privilege escalation. These issues are only resolved by patching the kernel or the runtime. Lower layers may be exploited by the process itself. [Equifax was hacked](https://www.theregister.co.uk/2017/09/20/equifax_vulnerability_could_be_widespread/) in September 2017 through a [remote command injection bug](https://blog.blackducksoftware.com/cve-2017-5638-anatomy-apache-struts-vulnerability) in Apache Struts. The vulnerability exposed private identity information of nearly half the US population. Attacks may use this type of vulnerability to escape the container as well as to access private information.

Other exploits are possible as we move up the stack from the kernel to the libraries and applications. [Heartbleed](http://heartbleed.com/) exploited the OpenSSL library to gain access to private information.

This particular issue is not container specific, but it is important because each image has a unique copy of all libraries. Thus, each container may be open to a different set of exploits, depending on the language/framework/libraries involved. The point is that containers are not a panacea for all security threats. They cannot guard against all possible attack vectors. However, they do provide strong security when setup correctly.

## Stay Vigilant

Attacks that achieve escape from the container are the most serious and require the most attention. Luckily, preventing escape is easy enough in the majority of cases, so long as you're aware of CVEs, and patches/updates accordingly. Bear in mind that the underlying kernel technologies are much older than modern container technologies (such as Docker). Container runtimes are changing much faster than the kernel, so new exploits may be found across a range of kernel versions. Prepare an emergency kernel or Docker upgrade playbook and test it out with your team.

This is the first step in securing the Docker hosts themselves. Docker, Inc. provides the [Docker bench for security](https://github.com/docker/docker-bench-security), which is a script that checks for dozens of common best practices around deploying Docker containers in production. These (and similar types of checks) may be integrated with your infrastructure as code tooling to verify that each change meets your security requirements. This is an efficient way of safeguarding against common mistakes such as allowing unprivileged users access to the Docker daemon. You may also decide to add an extra layer of safety by enabling AppArmor, SELinux, GRSEC, or whatever your favorite hardening solution happens to be.

## Docker Security Scanning

Now we can move up the stack, from the Docker host to the containers themselves.

All containers start from an image, which includes all the libraries, files, and dependencies required to run the process in the container. To highlight the relevance of threats to this layer, Aqua Security conducted [a survey](https://info.aquasec.com/container-security-enterprise-survey) of 512 attendees at DockerCon 2016, 53% of whom considered image vulnerabilities a key focus area.

Luckily, it's possible to eliminate such vulnerabilities with image scanning. While Docker, Inc. offers a [first-party solution](https://docs.docker.com/docker-cloud/builds/image-scan/), third parties such as Aqua Security and Twist Lock also offer similar products. Security scanning identifies packages within an image that have known vulnerabilities (like Heartbleed or the Struts issue). This practice is especially important since most teams use a shared base image. This approach saves time and energy, but it also increases the attack service. Security scanning is a fantastic way to ensure your base images are free from known package exploits. It should be done as part of the CI/CD pipeline before deploying to production, and even in development environments if possible.

Security scanning is not limited to checking for exploited packages. These tools may also detect secrets (such as an API token or a database password) in images. Teams should implement these checks as early as possible in the SDLC, as they help inform developers that the often simple and straightforward practice of including secrets in images is unacceptable. This also guides the team into defining and implementing a secure secret management process. The practice has a knock-on effect of improving security knowledge throughout the organization, and yet another benefit is that it also prevents attackers from exploiting your production environment using static artifacts.

## Best Practices

There are also some recommendations that apply to all containers-regardless of application or environment.

First, mitigate against privileged access, both inside and outside the container. Processes in containers should not run as root. Dockerfiles should include a USER instruction, specifying what user to apply when the container is started.

Pair this practice with container capability enforcement such as mounting volumes, socket access, kernel module loading, and others. Docker grants the minimum capabilities by default, which is great. The [Docker security guide](https://docs.docker.com/engine/security/security/) explains the connection: "_This means that even if an intruder manages to escalate to root within a container, it will be much harder to do serious damage, or to escalate to the host._"

## Summing it Up

The practices outlined above will help you secure your stack, but be warned-security is not a one-time concern. It requires constant vigilance to stay up-to-date with CVEs and patch software. Security scanning prevents compromised images from entering production, but what can you do about container escapes and other anomalies on your Docker hosts? Centralized logging and tripwires work well here.

We've discussed container capabilities and privileged containers. Most applications don't require privileged containers, so it would be strange if one were to start somewhere in your network, right? Centralized logging plus text-matching alerts can notify you in such cases, and here's how it would work: Connect the Docker daemon logs (and other useful information sources) up to a centralized logging system. Create an alert that pings the security team when "privileged container" shows up in the log, and then investigate. You can leverage the same approach for detecting other undesirable traits, like containers running as the root user or having strange capabilities.

Security will always be an issue. The steps outlined will guard you against known attack vectors, test for best practices, and alert you to anomalies, so that it will be _less_ of an issue. Check out the Docker security guide and [Docker security whitepaper](https://www.docker.com/sites/default/files/WP_IntrotoContainerSecurity_08.19.2016.pdf) for more information and the rationale behind these recommendations. Also, consider adopting [DevSecOps](http://www.devsecops.org/) principles by integrating security and operational concerns into your SDLC to increase production security and security knowledge amongst team members.

Learn about the importance of a strong culture of cybersecurity, and [examine](https://dzone.com/go?i=232227&u=https%3A%2F%2Fweb.securityinnovation.com%2Fbuilding-a-culture-of-cybersecurity-adv%3Futm_campaign%3DDZONE-Sponsorship-June-2017%26utm_source%3DAdvertising%26utm_medium%3Dbuilding-a-culture-of-cybersecurity) key activities for building - or improving - that culture within your organization.
