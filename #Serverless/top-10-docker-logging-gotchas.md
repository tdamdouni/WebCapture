# Top 10 Docker Logging Gotchas

_Captured: 2018-01-23 at 14:16 from [dzone.com](https://dzone.com/articles/top-10-docker-logging-gotchas?edition=355120&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202018-01-23)_

Docker changed not only how applications are deployed, it also changed the workflow for log management. Instead of writing logs to files, containers write logs to the console (stdout/stderr) and [Docker Logging Drivers](https://docs.docker.com/engine/admin/logging/overview/) forward logs to their destination. A check against Docker [GitHub issues](https://github.com/moby/moby/labels/area%2Flogging) quickly shows that users have various problems when dealing with Docker logs. Managing logs with Docker seems to be tricky and needs a deeper knowledge of Docker Logging Driver implementations and alternatives to overcome issues that people report.

## So What Are the Top 10 Docker Logging Gotchas?

First, let's start with an overview of Docker Logging Drivers and options to ship logs to centralized Log Management solutions such as Elastic Stack (former ELK Stack) or [Sematext Cloud](https://sematext.com/cloud/).

![top 10 docker logging gatchas sematext](https://sematext.com/wp-content/uploads/2018/01/top-10-docker-logging-gatchas-sematext.png)

In the early days of Docker, container logs were only available via Docker remote API, i.e. via "docker logs" command and a few advanced log shippers. Later on, Docker introduced logging drivers as plugins, to open Docker for integrations with various log management tools. These logging drivers are implemented as binary plugins in the docker daemon. Recently, the plugin architecture got extended to run logging drivers as external processes, which could register as plugins and retrieve logs via Unix socket. Currently, logging drivers shipped with docker binaries are binary plugins, but this might change in the near future.

Docker Logging Drivers receive container logs and forward them to remote destinations or files. The default logging driver is "json-file". It stores container logs in JSON format on local disk. Docker has a plugin architecture for logging drivers, so there are plugins for open source tools and commercial tools available:

  * Journald - storing container logs in the system journal
  * Syslog Driver - supporting UDP, TCP, TLS
  * Fluentd - supporting TCP or Unix socket connections to fluentd
  * Splunk - HTTP/HTTPS forwarding to Splunk server
  * Gelf - UDP log forwarding to Graylog2

For a complete log management solution additional tools need to be involved:

  * Log parser to structure logs, typically part of log shippers ([fluentd](https://www.fluentd.org/), [rsyslog](http://www.rsyslog.com/), [logstash](https://github.com/elastic/logstash), [logagent](https://sematext.com/docs/logagent/), …)
  * Log indexing, visualization and alerting: 
    * [Elasticsearch ](http://www.elastic.co)and Kibana (Elastic Stack, also known as ELK stack),
    * and many more …

To ship logs to one of the backends you might need to select a logging driver or logging tool that supports your Log Management solution of choice. If your tool needs Syslog input, you might choose the Syslog driver.

## Top 10 Docker Logging Gotchas

### 1\. Docker Logs Command Works Only With json-file Logging Driver

The default Logging driver "json-file" writes logs to the local disk, and the json-file driver is the only one that works in parallel to "docker logs" command. As soon one uses alternative logging drivers, such as Syslog, Gelf or Splunk, the Docker logs API calls start failing, and the "docker logs" command shows an error reporting the limitations instead of displaying the logs on the console. Not only does the docker log command fail, but many other tools using the Docker API for logs, such as Docker user interfaces like Portainer or log collection containers like Logspout are not able to show the container logs in this situation.

See <https://github.com/moby/moby/issues/30887>

### 2\. Docker Syslog Driver Can Block Container Deployment

Using Docker Syslog driver with TCP or TLS is a reliable way to deliver logs. However, the Syslog logging driver requires an established TCP connection to the Syslog server when a container starts up. If this connection can't be established at container start time, the container start fails with an error message like

This means a temporary network problem or high network latency could block the deployment of containers. In addition, a restart of the Syslog server could tear down all containers logging via TCP/TS to a central Syslog server, which is definitely the situation to avoid.

See: <https://github.com/docker/docker/issues/21966>

### 3\. Docker Syslog Driver Loses Logs When Destination Is Down

Similar to the issue #2 above, causing a loss of logs is the missing ability of Docker logging drivers to buffer logs on disk when they can't be delivered to remote destinations.

An interesting issue to watch: <https://github.com/moby/moby/issues/30979>

### 4\. Docker Logging Drivers Don't Support Multi-Line Logs Like Error Stack Traces

When we think about logs, most people think of simple single-line logs, say like Nginx or Apache logs. However, logs can also span multiple lines. For example, exception traces typically span multiple lines, so to help Logstash users we've shared how to [handle stack traces with Logstash](https://sematext.com/blog/2015/05/26/handling-stack-traces-with-logstash/). Things are no better in the world of containers, where things get even more complicated because logs from all apps running in containers get emitted to the same output - stdout. No wonder seeing [issue #22920 ](https://github.com/moby/moby/issues/22920)closed with "Closed. Don't care." disappointed so many people. Luckily, there are tools like Sematext[ Docker Agent](https://github.com/sematext/sematext-agent-docker) that can parse multi-line logs out of the box, as well as apply custom multi-line patterns.

### 5\. Docker Service Logs Command Hangs With non-JSON Logging Driver

While the json-files driver seems robust, other log drivers could unfortunately still cause trouble with Docker Swarm mode.

See Github Issue: <https://github.com/docker/docker/issues/28793>

### 6\. Docker Daemon Crashes If fluentd Daemon Is Gone and Buffer Is Full

Another scenario where a logging driver causes trouble when the remote destination is not reachable - in this [particular case](https://github.com/moby/moby/issues/32567) the logging drivers throws exceptions that cause Docker daemon to crash.

### 7\. Docker Container Gets Stuck in Created State on Splunk Driver Failure

If the Splunk server returns a 504 on container start, the container is actually started, but Docker reports the container has failed to start. Once in this state, the container no longer appears under docker ps, and the container process cannot be stopped with docker kill. The only way to stop the process is to manually kill it.

Github: <https://github.com/moby/moby/issues/24376>

### 8\. Docker Logs Skipping/Missing Application Logs (journald Driver)

It turns out that this issue is caused by journald rate limits, which needs to be increased as Docker creates logs for all running applications and journald might skip some logs due to its rate limitation settings. So be aware of your journald settings when you connect Docker to it.

### **9\. Gelf Driver Issues**

The Gelf logging driver is missing a TCP or TLS option and supports only UDP, which could be risky to lose log messages when UDP packets get dropped. Some issues report a problem of DNS resolution/caching with GELF drivers so your logs might be sent to "Nirvana" when your Graylog server IP changes - and this could happen quickly using container deployments.

### **10\. Docker Does Not Support Multiple Log Drivers**

It would be nice to have logs stored locally on the server and the possibility to ship them to remote servers. Currently, Docker does not support multiple log drivers, so users are forced to pick a single log driver. Not an easy decision knowing various issues listed in this post.
