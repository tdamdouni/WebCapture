# Top 10 Security Risks in Serverless Architectures

_Captured: 2018-08-25 at 10:13 from [dzone.com](https://dzone.com/articles/top-10-security-risks-in-serverless?edition=387227&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-08-24)_

Protect your applications against [today's increasingly sophisticated threat landscape.](https://dzone.com/go?i=299500&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D25669356%26PluID%3D0%26ord%3D%25255Btimestamp%25255D)

Serverless architectures (Function as a Service or FaaS) are architectures on which applications, once built and deployed, can self-scale according to the cloud workload flow. From a development standpoint, serverless architectures are largely focused on the core **functionality** and disregard all underlying constraints, such as OS, runtime environment, storage, etc.

The serverless architecture allows developers to focus solely on business logic and not on complex server infrastructures.

## **Benefits of Going Serverless**

  * **Zero administration -- **In serverless, a developer's job is to deploy code without provisioning compute instances, operating systems, etc. The Ops (Infra Operations) aren't to be bothered with either.
  * **Auto-scaling -- **As alluded to earlier, the serverless application can be scaled dynamically according to cloud workloads.
  * **Pay-per-use -- **Function-as-a-service (FaaS) computes and manages services that are charged upon usage as opposed to pre-provisioned capacity.

## **Great, so What About Security?**

When you go serverless, it is the serverless provider (eg.AWS lambda, Google Cloud Functions, etc) that is responsible for securing all the cloud components, such as the data center, network, servers, operating systems, and its configurations.

![](https://lh4.googleusercontent.com/Ik9LhaI1pXKLSqESIgrLf2nPQHbLtJxd7Y91cyVY-yStjRKSkYEUGJ1AFP-bNFnn0vvF5hV9877PFvF0NU5N6Jtp7xFXd-SdcjUOZcVHLK_yBUtUt-RmlHmTTgdjmVfDItHEcwgB)

> _Figure 1: The Shared Security Responsibilities Model for Serverless Architectures_

However, this merely reduces the security burden shouldered by the developer and doesn't negate it. From the application side of things, the application developer is still responsible for application logic, code, data, and application-layer configurations, making it is a shared security responsibility as illustrated in **Figure 1**.

### **New Attack Vectors Introduced in Serverless **

A new work dynamic brings with it new perspectives and new vulnerabilities. I've enlisted most of them here:

  * **Increased attack surface: **As serverless functions consume data from multiple event sources, such as HTTP APIs, message queues, cloud storage, and IoT device communications, the attack surface induces protocols and complex message structures, which are hard to inspect by a typical web application firewall.
  * **Attack surface complexity: **Right off the bat, the attack surface of the architecture is quite new, hence it could be a bit of a hassle to adapt and scale for the developers; the probability of misconfiguration is very high.
  * **Overall system complexity: **It is very difficult to visualize and monitor applications developed with serverless architectures as it is not a typical software environment. Hence, proper logging of events and functions are crucial for timely troubleshooting and to respond to security events.
  * **Inadequate security testing: **Security testing on applications built on serverless architectures are far more complex when compared to standard applications. This is why automated scanning tools have not adapted to scan applications developed on serverless architectures just yet.

## **Top 10 Critical Risks in Serverless Architectures**

  * (SAS-1) -- Function Event Data Injection
  * (SAS-2) -- Broken Authentication
  * (SAS-3) -- Insecure Serverless Deployment Configuration
  * (SAS-4) -- Over-Privileged Function Permissions and Roles
  * (SAS-5) -- Inadequate Function Monitoring and Logging
  * (SAS-6) -- Insecure 3rd Party Dependencies
  * (SAS-7) -- Insecure Application Secrets Storage
  * (SAS-8) -- Denial of Service and Financial Resource Exhaustion
  * (SAS-9) -- Serverless Function Execution Flow Manipulation
  * (SAS-10) -- Improper Exception Handling and Verbose Error Messages

### **(SAS-1) -- Function Event-Data Injection **

No wonder injection flaws are topping the OWASP Top 10 list as the most devastating flaw there is. Injection flaws occur when an untrusted input is passed directly to an interpreter and gets executed or evaluated.

Most serverless architectures provide a multitude of event sources, which can trigger the execution of a serverless function.

This abundant set of event sources increases the potential attack surface and introduces complexities when attempting to protect serverless functions against event-data injections, especially since serverless architectures are not nearly as well-understood as web environments where developers know which message parts shouldn't be trusted (e.g. GET/POST parameters, HTTP headers, and so forth).

#### **Some Examples Include:**

  * Cloud storage events (e.g. AWS S3, Azure Blob Storage, Google Cloud Storage)
  * NoSQL database events (e.g. AWS DynamoDB, Azure cosmos DB)
  * SQL database events
  * Stream processing events (e.g. AWS Kinesis)
  * Code changes and new repository code commits
  * HTTP API calls
  * IoT device telemetry signals
  * Message queue events
  * SMS message notifications, PUSH notifications, emails, etc.

#### **Most Common Types of Injection Flaws in Serverless Architectures Are:**

  * Operating System (OS) command injection
  * Function runtime code injection (e.g. Node.js/JavaScript, Python, Java, C#, Golang)
  * SQL injection
  * NoSQL injection
  * Pub/Sub Message Data Tampering (e.g. MQTT data injection)
  * Object deserialization attacks
  * XML External Entity (XXE)
  * Server-Side Request Forgery (SSRF)

### **(SAS-2) -- Broken Authentication**

Serverless applications being architected in the microservices-like system design would often contain hundreds of distinct serverless functions with its own purpose. Some may expose public web APIs, while others may serve as a proxy to different functions or processes.

It is mandatory to apply robust authentication schemes, which provides proper access control and protection to every relevant function, event type, and trigger.

An example of such an attack would be "Exposing Unauthenticated Entry Point via S3 Bucket with Public Access:"

![](https://lh6.googleusercontent.com/SQqM0ZNTfFxtGUYIIkkscrF6GvdFZyRhsLQajhiiEuJHXNy7bvqWn9HEEedZgKL1-1tHX3KLjXNOLQP7BdIH_A8beWCVv4CBKVnQMh9MUb8CKdm3mCXxhgXtlmfQjc-tmjNjXsGc)

> _(SAS-3) -- Insecure Serverless Deployment Configuration_

As serverless architecture is new and provides different customization and configuration settings for any specific need, task, and environment, the probability of misconfiguring critical configuration settings are quite high and can lead to catastrophic data losses. It is vital to make functions stateless while designing serverless architectures and also to make sure that sensitive data is not exposed to any unauthorized personnel. It is also recommended to properly make use of cloud hardening methods and proper ACL configurations.

### **(SAS-4) -- Over-Privileged Function Permissions and Roles **

It is always wise to follow the principle of "Least Privilege." Technically this means serverless functions should only be given necessary privileges to perform the intended logic. Provisioning over privileges to a serverless function could end up being abused to perform unintended operations, such as 'Executing System Functions.'

### **(SAS-5) -- Inadequate Function Monitoring and Logging **

From a security standpoint, it is critical to log and monitors security-related events in real-time as it would help in detecting an intruder's action and containing the situation much effectively. It will also help prevent cyber breaches in real-time. One of the key aspects of serverless architectures is the fact that "Monitoring and Logging" reside in a cloud environment, outside the organizational data center perimeter.

It's true that many serverless architecture vendors provide extremely capable logging facilities. These logs -- in their basic/out-of-the-box configuration -- are not always suitable for the purpose of providing a full security event audit trail.

In order to achieve adequate real-time security event monitoring with the proper audit trail, serverless developers and their DevOps teams are required to stitch together logging logic that will fit their organizational needs, like:

● Collecting real-time logs from different serverless functions and cloud services

● Pushing these logs to a remote security information and event management (SIEM) system.

This will oftentimes require you to store the logs in an intermediary cloud storage service. The SANS six categories of critical log information paper recommend that the following log reports be collected:

  * Authentication and authorization reports
  * Change reports
  * Network activity reports
  * Resource access reports
  * Malware activity reports
  * Critical errors and failures reports

### **(SAS-6) -- Insecure 3rd Party Dependencies **

Technically, a serverless function should be a small piece of code that performs a single discrete task. At times, in order to perform this task, the serverless function will be required to depend on third-party software packages, open source libraries, and even consume 3rd party remote web services through API calls. It is wise to look at 3rd party dependencies before importing their code as they could be vulnerable and can make the serverless application susceptible to cyber attacks.

### **(SAS-7) -- Insecure Application Secrets Storage **

As applications are growing in scale and complexity, the need for storing and maintaining application secrets are critical, such as :

  * API keys
  * Database credentials
  * Encryption keys
  * Sensitive configuration settings

One of the most frequently committed mistakes is storing application secrets in plain text within configuration files, database configurations, etc. Any user with "Read" permissions can gain access to these secrets.

It is always advisable to encrypt or not to store plain text secrets containing API private keys, passwords, environment variables, etc. Environment variables are a useful way to persist data across serverless function executions, in certain cases, such variables could leak data to unauthorized entities.

### **(SAS-8) -- Denial of Service and Financial Resource Exhaustion**

Denial of Service attacks can also be targeted within serverless architectures as they are pay-per function based model. Denial of service attacks on a serverless application can cause financial and resource unavailability disasters. To avoid such financial disasters and server downtime, it is vital for the application developer to properly define execution limits while deploying the serverless application in the cloud. Some resources to be limited are:

  * Per-execution memory allocation
  * Per-execution ephemeral disk capacity
  * Per-execution number of processes and threads
  * Maximum execution duration per function
  * Maximum payload size
  * Per-account concurrent execution limit
  * Per-function concurrent execution limit

#### Some Attack Vectors Are:

  * **AWS VPC IP address depletion:** Organizations that deploy AWS Lambda functions in VPC (Virtual Private Cloud) environments should also pay attention to the potential exhaustion of IP addresses in the VPC subnet. An attacker might cause a denial of service scenario by forcing more and more function instances to execute and deplete the VPC subnet from available IP addresses.
  * **Financial Resource Exhaustion: **An attacker may push the serverless application to "over-execute" for long periods of time, essentially inflating the monthly bill and inflicting a financial loss for the target organization.

### **(SAS-9) -- Functions Execution Flow Manipulation **

Manipulating an application's flow will help an attacker to subvert the application logic in bypassing access controls, elevating user privileges or even cause Denial of Service attacks.

Application flow manipulation is not uncommon to serverless architectures. It is a common problem is multiple types of software. However, as serverless applications are unique, they often follow a microservices design paradigm containing discrete functions, coupled together in a specific order, which implements the overall application's logic.

As functions are chained, invoking a specific function may invoke another function. The order of invocation is critical for achieving the desired logic.

### **(SAS-10) -- Improper Exception Handling and Verbose Error Messages**

In all, serverless applications that perform line-by-line debugging is more complicated and limited when compared to standard applications. However, the above factor forces developers to adopt the use of verbose error messages, enabling debugging environment variables and, eventually, forgetting to clean the code when moving it to the production environment.

Verbose error messages, such as stack traces or syntax errors, expose internal logic of the serverless function, revealing potential weakness, flaws, or sensitive data.

[Rapidly detect security vulnerabilities in your web, mobile and desktop applications](https://dzone.com/go?i=299501&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D25669352%26PluID%3D0%26ord%3D%25255Btimestamp%25255D) with IBM Application Security on Cloud. [Register Now](https://dzone.com/go?i=299501&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D25669352%26PluID%3D0%26ord%3D%25255Btimestamp%25255D)
