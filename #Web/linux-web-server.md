# Linux Web Server

_Captured: 2017-04-05 at 23:46 from [dzone.com](https://dzone.com/articles/linux-web-server?edition=288883&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-05)_

The DevOps Zone is brought to you in partnership with Sonatype Nexus. The [Nexus Suite](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016) helps scale your DevOps delivery with continuous component intelligence integrated into development tools, including Eclipse, IntelliJ, Jenkins, Bamboo, SonarQube and more. [Schedule a demo today](https://dzone.com/go?i=146021&u=https%3A%2F%2Fwww.sonatype.com%2Fnexus-lifecycle%3Futm_source%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Nexus%2520Lifecycle%2520-%2520September%25202016).

A web server is a system that processes requests via HTTP protocol. You request a file from the server and it responds with the requested file, which might give you an idea that web servers are only used for the web -- but actually, they can also be found embedded in devices such as printers and routers. When you open your router configuration page, this is a web server behind it. When you open the printer configuration page, there is also a web server behind it serving your requests. Web servers are important today. In this post, we will talk about Linux web server and how to install one and configure it to serve your content to others.

## How a Web Server Works

Your browser establishes a connection with the web server and requests a document on the server. The server decodes the request and maps the virtual path to a real one, which should match an existing file on the server. The server sends the file to the browser with some information such as its MIME type, the length of the content, and some other useful information.

Sometimes, the requested file is a static page like HTML pages or dynamic pages like PHP, Java, Perl, or any other server-side language. For example, when you type _www.google.com_, the browser queries the DNS about the IP address of the computer: _www.google.com_. Once the browser gets the answer from the DNS, it establishes a TCP connection using _port 80_ and requests the default web page. The Google server will send the page to the browser in HTML format.

I recommend you review this [Linux DNS server](https://likegeeks.com/linux-dns-server/) post to know how DNS servers work.

## Linux Web Server Implementations

There are many Linux web servers available for you to use:

  * Apache server.
  * Nginx.
  * Lighttpd.
  * Apache Tomcat.
  * Monkey HTTP Daemon (used especially for embedded systems).

There are more Linux web servers, but this list is the most-used web servers, the most frequently used being Apache and Nginx. Nginx doesn't support the ability to execute scripts in the same way that Apache does, but it can be used in conjunction with application servers that can execute scripts.

In this post, we will use the Apache server for several reasons:

  * It is stable.
  * It is extremely flexible.
  * It has proved to be secure.

We'll walk through the process of installing and configuring the Apache server on Linux server. But before we get into the steps, let's review some of the basics of HTTP as well as some of the internals of Apache.

## Understanding HTTP

When a web client connects to a web server, the client contacts the server's TCP _port 80_. Once connected, the web server says nothing. It's up to the client to issue HTTP commands (also methods) for its requests to the server. Along with each command comes a request header that includes information about the client.

To view these request headers, in Chrome, open Chrome dev tools. Then, open the network panel and visit _google.com_ and check the request headers. You should see something like this:

![Linux Web Server Request Header](https://likegeeks.com/wp-content/uploads/2017/03/01-Linux-Web-Server.png)

As you can see, the HTTP `GET` command asks the server to fetch a file. The other information tells the server about the client, the kind of file formats the client will accept, and so on.

Along with the request header, additional headers may be sent. For example, when a client uses a hyperlink to get to the site, a header entry showing the client's originating site will also appear in the header.

When it receives a blank line, the server knows that the request header is complete. Once the request header is received, it responds with the requested content, prefixed by a server header.

The server header provides information about the server like the amount of data the client is about to receive, the type of data, and other information.

![Linux Web Server response header](https://likegeeks.com/wp-content/uploads/2017/03/02-Linux-Web-Server-response-header.png)

> _You can check the response headers from the browser network panel._

## Install Apache Webserver

You can install apache server on Red Hat based distros using the following command:

Or, if you are using a Debian-based distro, you can install it like this:

The Apache web server service is called HTTPD on Red Hat-based distros like CentOS, while it is called apache2 in Debian-based distros. As the firewall probably will be filtering out the traffic, we'll have to add a rule to permit HTTP traffic _port 80_:

Or, if you are using firewalld, you can use the following command:

You can make changes to firewall permanent, as we discussed in this [Linux iptables firewall](https://likegeeks.com/linux-iptables-firewall-examples/) post.

Start your service and enable it on boot, you can check if your service is running or not using the following command:

Now, open your browser and visit _http://localhost_ or_ http://[::1]_/ if you are using IP v6. If your installation goes well, you should see your HTML home page.

## Configuring Apache Webserver

You can start adding files to Apache right away in the _/var/www/html_ directory for top-level pages. Just remember to make sure that any files or directories placed in that directory are world-readable.

The Apache default web page is _index.html_. Try to change the content of this page and see the results on your browser. The configuration files for Apache are located in the _/etc/httpd/conf/_ directory. On Debian-based systems, the main configuration file for Apache is at the _/etc/apache2/apache2.conf _file.

We can't discuss every option for apache on a single post, but we will discuss the most important options. You can call them options or directives- it's up to you.

### ServerRoot Option

This is used for specifying the configuration directory for the web server. On Red Hat-based distros, the ServerRoot option is the _/etc/httpd/_directory. On Debian distros, the ServerRoot option is _/etc/apache2/: ServerRoot /etc/httpd_.

### Listen Option

This is the port(s) on which the server listens for connection requests. The default value for this option is _80 _for non-secure connections. The Listen option can also be used to specify the particular IP addresses over which the web server accepts connections.

You can specify a different port other than _80_ that is not in use by another service. This is one of the techniques for running multiple web servers or sites on the same server.

When a site runs a web server on a non-standard port such as port _8080_, it will require the port number to be explicitly stated like this:

### ServerName Option

This option defines the hostname and port that the server uses to identify itself. This option allows you to specify what you want Apache to return as the hostname of the web server to visitors:

### DocumentRoot Option

This defines the directory on the web server from which HTML files will be served to requesting clients, which is _/var/www/html_ in our file: _DocumentRoot /var/www/html_.

### MaxRequestWorkers Option

This sets a limit on the number of simultaneous requests that the web server will serve.

### LoadModule Option

This is used for adding other modules into Apache's running configuration. Apache comes with many modules by default and automatically includes them in the default installation.

There are a lot of Apache modules like those:

  * `mod_cgid`: Allows the execution of CGI scripts on the web server.

  * `mod_ssl`: Provides strong cryptography for the Apache web server via SSL and TLS protocols.

  * `mod_userdir`: Allows user content to be served from user-specific directories.

If you want to disable loading a specific module, you can comment the load module line that contains that module.

If you use Debian-based distros like Ubuntu, you can use `$ a2enmod modulename` to enable the module and `$ a2dismod modulename` to disable the module.

All these commands do is create symlink under the _/etc/apache2/mods-enabled_ directory with the file that contains the module you want to enable. All files under this directory are included in Apache configuration by default, so any file will exist in this directory will include what's inside it.

If you use `a2dismod`, the symlink will be removed.

If you enable or disable a module, you have to reload or restart Apache web server: `LoadModule mod_cgid.so`.

### Include Option

This option allows you to include other configuration files. You can store all the configuration for different virtual domains in appropriately named files, and Apache will automatically know to include them at runtime: Include filePath.

### UserDir Option

This option defines the subdirectory within each user's home directory, where can place your content that they want to make accessible via the web server. This directory is usually named `public_html`.

For example, if you have user Adam who wants to make web content available via web browser, first, we make a `public_html` folder under his home directory. Then, set the permission for public_html folder: `$ chmod 644 public_html`.

Now, if you put `index.html` file, it will be accessible via the browser like this:

### Alias Option

The alias option allows web content to be stored in any other location on the file system that is different from the location specified by the `DocumentRoot` directive.

Like you have files outside `DocumentRoot` and you want them to be available to the visitors: `Alias URL_Path Actual_Path`.

### ErrorLog Option

This defines the location where errors from the web server will be logged: `ErrorLog /var/log/httpd/error_log.`

### VirtualHost Option

This option makes it possible for a single web server to host multiple websites.

It works by allowing the web server to provide different content based on the hostname, port number, or IP address that is being requested by the client.

For example, if you want to set up a virtual host for a host named _www.example.com_. First, create the `VirtualHost` option in _/etc/httpd/conf/httpd.conf _file. Specify the `DocumentRoot` and `ServerName` like this:

Keep in mind that the value of the `ServerName` option in the `VirtualHost` container must be resolvable via DNS.

These are the most-used Apache options. There are two types of virtual hosts you can define in Apache web server:

  1. Name-based virtual hosts.
  2. IP-based virtual hosts.

The `NameVirtualHost` directive defines which addresses can be virtual hosts; the asterisk (*) means any name or address this server. You can write them like this

If you have more than one IP address or you want to use SSL certificate, the website must be on a dedicated IP address. You can write IIP-based virtual hosts like this:

## Apache Process Ownership

We know from this [Linux process management](https://likegeeks.com/linux-process-management/) post that each process has an owner and that owner has specific rights on the system, and we know that every process inherits its permissions of its parent process. Also, we know from that post that there is an exception in Linux for that rule.

The exception is that all programs configured with the SetUID bit do not inherit rights from their parent process, but rather start with the rights specified by the owner of the file itself, like _/bin/su_ program which is owned by root and has SetUID bit set. If a user Adam runs this program, it does not inherit the permission from Adam but it acts as a root user running it.

Apache web server must start with root permissions because it needs to bind itself to _port 80_, and only the root can do this. Once it does this, Apache can give up its rights and run as a non-root user.

Based on the Linux distro you use, the user could be one of the following: nobody, www, apache, www-data, or daemon. Apache can read only the files that the user has permissions to read. As user nobody, the scripts and processes don't have access to the same key files that root can access.

I delayed introducing two more options for Apache until reaching this point.

### User Option

This specifies the user ID with which the web server will answer requests. The user should have enough privileges to access files and directories that supposed to be available to visitors.

User www-data

### Group Option

This specifies the group name of the Apache web server process.

Group www-data

Security is very important for sites that use executable scripts such as CGI or PHP scripts. The user that you will use will have permission to read and write the content of all sites on the server. We want to ensure that only the members of a particular site can read their own site only. This is very important because if a site of theirs were compromised by an evil user from one of the other sites, the user will be able to read all files since the Apache user has permission to do that.

So, how do we solve this problem?

## Suexec Support

A popular method is to use suEXEC. suEXEC is a program that runs with root permissions and makes CGI programs run as the user and group IDs of a specific user, not the user and group running the Apache server.

You can specify the user on each virtual host like this:

It's just that simple.

## Apache Authentication

You may want to restrict some parts to specific visitors, like a password protected directory.

In Apache, you can store authentication information file called an _._htpasswd file.

You can use htpasswd command to do that.

First, create the.htpasswd file using htpasswd command.

The -c option is needed the first time you run htpasswd, but when you need to add more users you shouldn't use -c because it will overwrite the file.

Then create.htaccess file in the public_html folder and write the following

AuthName is required; you can use any string you want.

AuthType Basic means we're using an htpasswd style user file.

AuthUserFile points to the file that contains the generated password from htpasswd command.

The Order directive says that Apache should deny access by default, and allow access only when specified in the user file.

The require directive means any user in the.htpasswd file is allowed.

## Troubleshooting Apache Webserver

If you modify the httpd.conf file and restart or reload apache web server and it does not work, then you have typed the wrong configuration. However, this is not the only case where you need to troubleshoot Apache; you may look at Apache logs to see how the service works so you can diagnose the problem and solve it.

The two main log files for apache are** error_log** and **access_log** files.

You can find those files in /var/log/httpd/ directory in Red Hat-based distros, or in /var/log/apache2/ directory if you are using Debian-based distros.

The access_log file contains every request to Apache web server with the details about clients who requested that resource.

The error_log file contains all of the errors that occur in Apache.

You can use tail command to watch the log file:

I recommend you to review [Linux syslog server](https://likegeeks.com/linux-syslog-server-log-management/) post to know more about logging.

On the upcoming posts, we will talk about Apache security tricks and tweaking.

I hope you find working with the Linux Web Server easy and interesting.

Thank you.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. Use the [Nexus Suite](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016) to automate your software supply chain and ensure you're using the highest quality open source components at every step of the development lifecycle. [Get Nexus today](https://dzone.com/go?i=146022&u=https%3A%2F%2Fwww.sonatype.com%2Fget-nexus-sonatype%3Futm_source%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_medium%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016%26utm_campaign%3DDZONE%2520-%2520Get%2520Nexus%2520-%2520September%25202016).
