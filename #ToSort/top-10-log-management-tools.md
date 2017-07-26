# Top 10 Log Management Tools

_Captured: 2017-06-25 at 19:22 from [dzone.com](https://dzone.com/articles/top-10-log-management-tools-1?edition=305136&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-25)_

[Evolve your approach to Application Performance Monitoring](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html) by adopting five best practices that are outlined and explored in this [e-book](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html), brought to you in partnership with [BMC](https://dzone.com/go?i=161135&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-APM-BMCcom-FY17-eBook-Form.html).

Programs have generated logs for as long as they have existed. But with the advent of modern server and application software, [logging](https://dzone.com/articles/top-7-log-management-cloud-tools) has become a part of the IT management and monitoring process. Servers and applications can generate log data on a variety of processes, from a simple announcement on a health check to detailed information on running processes.

It'd be interesting to look at these tools from a developer's point of view. In this article, we'll review 10 most popular logging management systems of today -- listed in a random order, not in the order of performance or capabilities.

## 1\. Splunk

There are few products that [Splunk](http://www.splunk.com/) provides: Enterprise, Light, Cloud, and Hunk. Splunk Enterprise helps you gain valuable Operational Intelligence from your machine-generated data. And with a full range of powerful search, visualization, and pre-packaged content for use-cases, any user can quickly discover and share insights. Splunk also has built-in reporting capabilities with advanced charts and dashboards and a pivot interface to generating visual reports with drag-and-drop ease.

### Pros

  * Built-in alerting and reporting.

  * Configurable charts and dashboards.

  * SaaS solution.

  * Scale from a single server to multiple data centers.

  * Real-time search, analysis, and visualization.

### Cons

  * Not easy to set up and add new sources. Each source must be added manually.

  * Limit of 500MB/day is not enough to use it for free, whereas 1GB/day will cost 2.700$ per year.

## 2\. LogPacker

[LogPacker](https://logpacker.com/) provides you with two solutions: Standalone and Cloud. Standalone version illustrates network with Agents and Servers in Cluster, there can be any amount of servers in this network. Agents can be installed or integrated into various platforms such as Unix, Windows, Android, iOs, WP, and even into website's JS. While Server accepts logs from all Agents and saves them into any storage. The main advantage is that LogPacker works just from the box and can find and send to the Cluster all possible logs on the server, grouped and aggregated.

Cloud version (SaaS) provides a full web interface with dashboards and search functions and has disk-based limits.

All LogPacker services are written in Go and created for high performance. The Agent instance usually spends around 30-40 MB of memory on default server installation.

### Pros

  * Built-in support for more than 100 log sources types.

  * Multiple storage providers.

  * Alerting and reporting system by Email, Slack or SMS.

  * Easy installation from packages.

  * Reliable clusterization.

  * Wide platform support: Unix, Windows, Mobile, JS.

  * REST API to build custom solutions based on saved data.

  * Events aggregation and security.

  * High performance.

  * Disk-based Cloud dashboard.

### Cons

  * Standalone version has no built-in web interface.

  * The free version has a limit up to 5 servers in Cluster.

## 3\. LogRhythm

In [LogRhythm](https://logrhythm.com/), log management and event management are distinct processes. That means purchasing and managing two separate tools, while LogRhythm combines both into a single centralized platform to streamline not only log management but log analysis, event management, and reporting. However, LogRhythm also provides an Agent that can be installed on a network server. The Agent collects computer's log data and sends it to the Log Manager.

### Pros

  * Intelligent search in real-time.

  * Collects data from all log sources, including applications and databases. ~700 log sources.

  * Real-time monitoring and flexible, role-based alerts.

  * One-click correlation from any search.

  * The console enables users to quickly correlate, search and pivot through their data rapidly.

### Cons

  * Big initial cost.

  * Not transparent user guide and documentation.

## 4\. Logentries

[Logentries](https://logentries.com/) automatically collects and centralizes all of your log data in any format into one secure location where you can search, aggregate, and visualize log data to get answers to your questions, in seconds. Logentries offers options for both agent and agentless collection of logs. When problems occur, Logentries provides an aggregated live tail view to see what is happening across your logs in real-time. As your environment dynamically scales, new instances can be easily configured to send all log data in real-time to Logentries.

### Pros

  * Works with multiple PaaS and IaaS.

  * Aggregated live tail search.

  * Custom tags of logs.

  * SQL-Like Query Language (LEQL) for searching.

  * Email reports.

  * Supports a diverse set of programming languages.

  * Free up to 5 GB.

  * Excellent documentation.

### Cons

  * Manual installation and manual log sources management.

  * Can't track the source of errors in 3rd party libraries.

  * There's a limit of 100 logs per server.

  * Insufficiently secure web client logger.

  * No specialized reporting for JavaScript.

## 5\. Logscape

[Logscape](http://logscape.com/) is an Enterprise ready big-data analytics tool built for time-series data visualization of machine data. Whether it is data generated by your systems or extracted from an external source - any form of machine generated data can easily be Searched, Filtered and placed onto Interactive Dashboards.

### Pros

  * 5GB daily data limit.

  * LDAP for user and role-based access control.

  * Custom dashboards, workspaces, and reports.

  * Indexers: In place processing on remote files.

  * Scale on existing or dedicated infrastructure.

### Cons

  * Not customizable.

  * Supports only data from network input or syslog.

## 6\. Loggly

[Loggly](https://www.loggly.com/) is a robust log analyzer, focusing on simplicity and ease of use for a DevOps audience. It's targeted for developers and DevOps -- making it less enterprise-focused. When to use it: Primary use cases are for troubleshooting and customer support scenarios. It's a good tool for a DevOps team.

### Pros

  * Unlimited custom dashboards based on any search.

  * Full-system RESTful API to integrate with other applications.

  * Text-based logs from any source.

  * Adaptable interface with multiple views, pages and workspaces.

  * Free lite version.

### Cons

  * Not transparent configuration and sources configuration.

  * Not good in cloud infrastructures.

  * Not secure.

## 7\. Fluentd

[Fluentd](http://www.fluentd.org/) is an open-source data collector, which lets you unify the data collection and consumption for a better use and understanding of data. Fluentd's performance has been proven in the field -- its largest user currently collects logs from 5000+ servers, 5 TB of daily data, handling 50,000 messages/sec at peak time. Yes, the main reason for using it is performance. Fluentd has a flexible plugin system that allows the community to extend its functionality.

Pros:

  * Apache 2.0 License project.

  * More than 300 community-contributed plugins.

  * Requires very little system resource.

  * Built-in reliability.

  * Store data in multiple systems.

### Cons

  * No Windows version is available.

  * Doesn't provide any built-in visualizations.

## 8\. Graylog

[Graylog](https://www.graylog.org/) is an open-source package that claims to perform the same functions as Splunk. Graylog is written in Java and its web interface is written in Ruby on Rails. Graylog does not have the ability to read directly from syslog files; instead, you need to send your messages directly to Graylog and it's less convenient. You can perform searches of your data just as in Splunk and with similar search functions. Alerting is also a possibility in Graylog, but the alert emails were less than informative on their own, providing only a reference to search results contained on Graylog's web interface.

### Pros

  * Free and open source.

  * Streams allow identifying events in real-time and perform actions.

  * Easy setup.

  * Server-side functionality can be extended via plug-ins.

  * REST API.

  * Intuitive search interface.

### Cons

  * Graylog only has support for syslog and GELF.

## 9\. Scalyr

[Scalyr](https://www.scalyr.com/) is a server monitoring tool built by ex-Google engineers. It brings together log data, system metrics, website monitoring, and alerting. It just doesn't scale at all; you must have that data in one place. But the interesting point here is that they're also trying to bring in the monitoring components. Other log management tools focus on the logs and gloss over the other parts of application monitoring.

### Pros

  * Easy set-up Agent or API.

  * Security and reliability.

  * Import logs from Heroku, Amazon RDS, or Amazon CloudTrail.

  * Customizable graphs.

### Cons

  * Doesn't have a free version.

  * No Cloud solution.

## 10\. Papertrail

[Papertrail](https://papertrailapp.com/) can aggregate data from text log files and syslog. It has a flexible team-wide access in web interface. Papertrail is installed easily in 45 seconds, can be distributed to multiple servers and has a simple clean interface. Unfortunately, compared with other competitors, their free plan comes with only 100MB/month.

### Pros

  * Real-time functionality from browser, command line, or API.

  * Custom alerts on any event configuration.

  * Backup feature to S3 bucket or MapReduce.

  * Integration with Slack, Email and Librato.

### Cons

  * Free plan comes with only 100MB/month.

  * Papertrail can integrate with Librato Metrics and StatHat to graph event occurrence count over time, but there's no built-in way to visualize data.

## Conclusion

All these tools and services are different. Some solutions are a component of a larger SIEM platform, providing even more sophisticated analytics capabilities, long-term storage, and data encryption, while others can be used with any SIEM solution or even as stand-alone appliances. Depending on your business, you can choose a suitable log management system for your purposes.

Learn tips and best practices for optimizing your capacity management strategy with the [Market Guide for Capacity Management](https://dzone.com/go?i=161136&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-BCO-GartnerMarketGuide-CapMgmtTools-AR.html), brought to you in partnership with [BMC](https://dzone.com/go?i=161136&u=http%3A%2F%2Fwww.bmc.com%2Fforms%2FPA-BCO-GartnerMarketGuide-CapMgmtTools-AR.html).

Opinions expressed by DZone contributors are their own.
