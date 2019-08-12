# Integrating Docker Solutions Into Your CI/CD Pipeline

_Captured: 2018-04-27 at 15:55 from [dzone.com](https://dzone.com/articles/integrating-docker-solutions-into-your-cicd-pipeli?edition=376213&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=devops%202018-04-27)_

## **Docker Image Security**

Docker. It seems like in this day and age, you are either using Docker containers or you are going to use Docker containers. If you haven't jumped on the bandwagon yet, check out a previous article, _[Docker: The New Ordinary](https://blog.sonatype.com/docker-devops-new-ordinary)_. If you are on the wagon or are thinking about it but have concerns about their security, it's time to read on.

[Jose Manuel Ortega](http://about.me/jmortegac) ([jmortega.github.io](https://github.com/jmortega)) is a software engineer and security researcher in Spain. I recently watched his presentation online entitled, _Testing Docker Images Security_. He gave an overview of typical Docker deployments, explained the attack surface and threats, presented how to detect vulnerabilities, and outlined a couple of best practices. In short, his advice will help you learn how to better secure your Docker containers.

[New to Docker? Read this paragraph; all others skip ahead.] If you aren't sure what Docker is, Jose offers this explanation, "Docker containers wrap a piece of software in a complete file system that contains everything it needs to run: code, runtime, system tools, system libraries - anything you can install on a server, regardless of the environment it is running in."

That is, containers are isolated but share an operating system and, where appropriate, binaries and libraries. Docker provides an additional layer of isolation, making your infrastructure safer by default. This makes the application lifecycle faster and easier to configure, reducing risks in your applications.

For starters, Jose lays out Docker's default mechanisms for security:

  * Linux kernel namespaces
  * Linux Control Groups (cgroups)
  * The Docker daemon
  * Linux capabilities (libcap)
  * Linux security mechanisms like AppArmor or SELinux
![Screen Shot 2018-04-08 at 7.17.58 AM](https://blog.sonatype.com/hs-fs/hubfs/Screen%20Shot%202018-04-08%20at%207.17.58%20AM.png?t=1524088760827&width=1059&height=1278&name=Screen%20Shot%202018-04-08%20at%207.17.58%20AM.png)

Jose walks through others tools, add-ons, best practices, etc. to increase Docker container security. I will cover most of them here.

**Docker Inspect Tool. **The Docker Inspect Tool is built into Docker. It provides information about the host name, the ID of the image, etc. and it comes up when you start Docker.

**Docker Content Trust**. It protects against untrusted images. It can enable signing checks on every managed host, guarantee integrity of your images when pulled, and provide trust from publisher to consumer.

![Screen Shot 2018-04-08 at 7.19.01 AM](https://blog.sonatype.com/hs-fs/hubfs/Screen%20Shot%202018-04-08%20at%207.19.01%20AM.png?t=1524088760827&width=4800&height=2490&name=Screen%20Shot%202018-04-08%20at%207.19.01%20AM.png)

**Docker File Security. **Docker files build Docker containers. They should not write secrets, such as users and passwords. You should remove unnecessary setuid and setgid permissions, download packages securely using GPG and certificates, and try to restrict an image or container to one service.

**Container Security**. Docker security is about limiting and controlling the attack surface on the kernel. Don't run your applications as root in containers, and create specific users for testing and policing the Docker image. Run filesystems as read-only so attackers can not overwrite data or save malicious scripts to the image.

Jose provided a useful checklist to check the security of a Docker container, but it's not a short one. Remember, if you are going to deploy hundreds or thousands of these containers, you'll want to ensure consistent handling of security concerns to keep the hackers at bay:

  * Do not write secrets to Docker files
  * Create a user
  * Follow version pinning for base images, packages, etc.
  * Remove unnecessary setuid, setgid permissions
  * Do not write any kind of update instructions alone in a Docker file
  * Download packages securely
  * Do not download unnecessary packages
  * Use COPY instead of ADD
  * Use the HEALTHCHECK command
  * Use gosu instead of sudo whenever possible
  * Use-no-cache (if applicable) when building
  * Enable Docker Content Trust
  * Ensure images are free from known vulnerabilities
  * Ensure images are scanned frequently throughout your DevOps pipeline
  * Ensure your images, packages are up-to-date
  * Use file monitoring solutions for image layers (if required)

**Auditing Docker Images. **You can scan your images for known vulnerabilities with a wide variety of commercial and open source tools such as:

  * Docker's native Security Scanning

All of these solutions can be integrated into one element of your CI/CD pipelines -- some can be integrated in multiple places.

Jose explored these solutions and best practices in more detail and offered up technical implementation tips in his full talk, available for free [here](https://youtu.be/nluTVEjycF0). If you are working on or interested in Docker security, his talk is worth your time.

Thirsty for more DevOps discussions led by practitioners (not vendors)? You too can binge watch 99 other talks from the All Day DevOps conference [here](https://www.alldaydevops.com/all-day-devops-2017-recordings?__hstc=31049440.e9fd034d652f4ba995fdbbc43f7ead80.1490111084079.1522939419125.1524145960687.77&__hssc=31049440.1.1524145960687&__hsfp=908707084).
