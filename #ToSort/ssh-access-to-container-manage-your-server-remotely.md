# SSH Access to Container: Manage Your Server Remotely

_Captured: 2018-07-11 at 07:59 from [dzone.com](https://dzone.com/articles/ssh-access-to-container-manage-your-server-remotel?edition=385217&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=cloud%202018-07-10)_

See why enterprise app developers love Cloud Foundry. [Download](https://dzone.com/go?i=295426&u=https%3A%2F%2Fwww.cloudfoundry.org%2Fcf-user-report-2018%2F%3Futm_source%3Ddzone%26utm_medium%3Dpaid%26utm_campaign%3Dleadgen) the 2018 User Survey for a snapshot of Cloud Foundry users' deployments and productivity.

The Jelastic Platform allows establishing to any container on your account. In this guide, we'll provide some of the most common commands that can come in handy when managing your server via SSH terminal.

There are two ways to connect your server inside Jelastic PaaS over SSH:

  * **Web SSH - **click on the same-named option next to the required environment layer or particular container to quickly access and start managing it online directly through your browser, via the automatically opened terminal tab at the bottom of Jelastic dashboard ![](https://jelastic.com/blog/wp-content/uploads/2018/06/connect-server-web-ssh.png)

  * **SSH Gate** \- alternatively, you can connect to your server via any preferred local SSH client basing on preliminary [generated ](https://docs.jelastic.com/ssh-generate-key?utm_source=blog-ssh-to-container) SSH keys pair (where the public key should be [added ](https://docs.jelastic.com/ssh-add-key?utm_source=blog-ssh-to-container) to your Account Settings, and the corresponding private key - being handled at your local machine) ![](https://jelastic.com/blog/wp-content/uploads/2018/06/connect-server-ssh-gate.png)

Once all the requirements are fulfilled, you can [establish an SSH connection](https://docs.jelastic.com/ssh-local-client?utm_source=blog-ssh-to-container) by means of the corresponding command line (circled above) from the same-named tab of your account settings.

For the sake of simplicity and quick access, in this article we'll leverage the inbuilt Web SSH tool; however, the described below commands can be used when working via remote local client absolutely similar.

**Tips:**

  * Within the majority of servers within Jelastic PaaS (including [custom Docker containers](https://docs.jelastic.com/dockers-management?utm_source=blog-ssh-to-container)), you are automatically granted full root permissions while connected via SSH. For the rest, mostly legacy nodes, which were created upon Jelastic-managed certified stack templates, the sufficient level of controllability is ensured with a set of additional intentionally allowed commands.
  * The full [list of terminal commands ](http://www.linfo.org/command_index.html)with all the appropriate options description you can find at the dedicated websites, similar to the linked above. In this guide, we'll consider a number of the most common commands to give you insights on the basics of operating with containers via the SSH protocol.

## Navigation through Remote Container File System

This section is rather for newbies than for an average developer, so the majority of you could probably skip it and proceed to more complex operations - however, we believe this is still worth to mention before proceeding further.

Once you've entered the required container via console, you get to the server home directory by default, which is commonly dedicated for storing your custom data and configs. For navigation between the folders, the **_cd _**command is used, with the following available arguments:

  * _**{directory_path}** - _either name of the nested folder (where several slash-separated nesting levels can be specified) or a full path to the required directory relatively to the container root

  * **..** - to navigate one level up within the file tree
  * **~** - to instantly switch to your working (server home) directory from any location
  * **/** - to instantly switch to the container root directory
![](https://jelastic.com/blog/wp-content/uploads/2018/06/Tomcat-ssh-connection-cofigurations.png)

As a result, the violet string next to the container hostname will change, indicating your current location.

**Tip: **If you are new to a stack runtime that your instance runs, most likely you'd like to explore its inner structure first (i.e. tree of files & directories, available configuration files, etc). The most convenient way to accomplish this is to use the inbuilt Jelastic [File Manager ](https://docs.jelastic.com/configuration-file-manager?utm_source=blog-ssh-to-container) GUI, available by clicking on the **Config **button next to the required server at your developer's panel:

![](https://jelastic.com/blog/wp-content/uploads/2018/06/manage-ssh-access.png)

> _The appropriate file tree will be shown in a dedicated tab below._

1\. To create a new file or folder, execute the next commands:

_where _

**_{file}_** and **_{dir}_** \- the preferred file or folder name (if being created in the current directory)

**_[path-to/] _**\- optional parameter for the case this new item should be placed in a different location.

![](https://jelastic.com/blog/wp-content/uploads/2018/06/ssh-connection-tomcat-server.png)

2\. To make sure that the file and folder we've specified above have been actually created, let's get the list of comprised files and directories at the current location with the next command:

**_ls_**

![](https://jelastic.com/blog/wp-content/uploads/2018/06/check-created-tomcat-ssh.png)

3\. Among the rest of most common commands that are intended for file management, are:

  * **_[cat_**](http://www.linfo.org/cat.html) - is used to operate with text files; depending on stated args, allows to view, merge and duplicate file content
  * **_[locate_**](http://www.linfo.org/locate.html) - to find the required file or directory within a server by its name (or part of it)

Now, let's consider the default shell possibilities to monitor and manage your node's metrics, its resource consumption, running inside processes, etc.

## Commands to View Server System Information

![](https://jelastic.com/blog/wp-content/uploads/2018/06/view-ssh-server-information.png)

1\. To get a short summary on the current container state and make sure that, for example, no malefactor affects its performance and/or operability, use the **_w_** command:

The received output will provide you with some general system information in a header (namely - current system timestamp, instance uptime, number of logged users and average amount of active processes for the last 1/5/15 minutes) and details on connected users below (their names, terminal type, source connection IP, login time, stats on the last activity and name of the currently active process(es), run on behalf).

**Tip: **Due to the native shell implementation specifics, the **_w_** command output does not include information on users, connected via terminal emulator.

2\. All statistics on server RAM usage is stored within the **_/proc/meminfo_** file. To review its content, use the mentioned above **_cat_** command:

`cat/proc/meminfo`

![](https://jelastic.com/blog/wp-content/uploads/2018/06/view-Tomcat-server-RAM-usage.png)

`uname -a`

![](https://jelastic.com/blog/wp-content/uploads/2018/06/Linux-Node-SSH.png)

3\. In order to display the basic software and hardware container data, execute the following line:

Here you can see info on a server kernel (name, version, release date), node hostname, CPU type, OS, etc.

## How to Manage Container Processes Remotely via Terminal

![](https://jelastic.com/blog/wp-content/uploads/2018/06/Web-SSH-Tasks.png)

1\. While connected over SSH, you can monitor all running processes inside a container with the `top` command:

Herewith, information is constantly updated in a real-time mode, displaying info on all user's processes (including system ones).

Press _Ctrl + C_ to terminate the command execution and return to the console input mode.

![](https://jelastic.com/blog/wp-content/uploads/2018/06/Web-SSH-Tomcat.png)

> _2. To display only your user's active processes, type in ps and run this command:_

`kill {pid}`

![](https://jelastic.com/blog/wp-content/uploads/2018/06/terminate-running-tomcat-process.png)

3\. Another useful command is `kill` , which allows terminating any running process, designated by its `{pid}` as an argument (the required process identifier can be found in the previous command's output)_:_

As you can see, the process, shown on the screen within the 2nd step of this section, was stopped since it's not listed among the active ones for now.

## Operating Application Archives via SSH Console

You are able to fetch the necessary files from Internet (for example, your application archive) directly through the console, to store and/or subsequently deploy them within your server.

![](https://jelastic.com/blog/wp-content/uploads/2018/06/operate-archives-ssh-console.png)

> _1. The wget command allows to download files by the specified {link}:_

2\. Then, you can `unzip` the downloaded archive with the same-named command:

![](https://jelastic.com/blog/wp-content/uploads/2018/06/unzip-tomcat-archive-ssh.png)

> _where {archive} is a path to your compressed package._

As a result, all extracted files will be placed to a same-named (after the archive) folder inside the current directory.

## Setting Custom Server Variables via SSH

![](https://jelastic.com/blog/wp-content/uploads/2018/06/setting-custom-tomcat-variables-ssh.png)

1\. The list of default environment variables for any container can be viewed within the **_.bash_profile_** file, which is located in the container's home directory. So to check them, make sure you've got to the proper container directory and execute the next command:

![](https://jelastic.com/blog/wp-content/uploads/2018/06/set-custom-variables-via-ssh.png)

2\. The **_.bash_profile _**file is not editable, so in case you need to additionally set your own variables, write them down to the **_.bashrc_** file within the same folder (just create it, if missing). To accomplish this, use any preferable text editor (for example, **_vi_**):

`export {VAR_NAME}={VAR_VALUE}`

![](https://jelastic.com/blog/wp-content/uploads/2018/06/export-tomcat-variables-via-ssh.png)

> _3. Here, new variables should be defined in the following format:_

**Note:** The **_.bashrc_** file is read during the bash initiation so the changes will be automatically applied when starting all further user session. But in case you need to apply the made changes immediately, run the `bash` command to restart the shell.

![](https://jelastic.com/blog/wp-content/uploads/2018/06/check-custom-tomcat-variables-via-ssh.png)

4\. To check whether your custom variable was successfully applied, execute the following command:

## Specifics of Certified Jelastic Containers Remote Management

At Jelastic PaaS, there are 2 types of [software stack ](https://docs.jelastic.com/software-stacks-versions?utm_source=blog-ssh-to-container) templates, which are used as a base when creating each of containers:

  * **_dockerized_** \- unified template model based on [native Docker standard support ](https://docs.jelastic.com/dockers-overview?utm_source=blog-ssh-to-container) with the generality of container management principles and functionality for all server types (i.e. regardless of whether it computes node, or database server, or caching instance, etc). When connecting to such server via SSH, you automatically get full control over the instance with root privileges granted and can perform any required operations inside a container.
  * **_certified_** software templates are based on native stack implementation, adapted by our team according to platform specifics.

Upon entering such server via SSH, you are logged in as a default server user. To provide enough possibilities for effective container management, we've made some additional options available to be executed under a regular user account:

  * **_sudo sbin/service {service_name} {start|stop|restart|condrestart|status|reload|upgrade|help} _**\- a set of commands to operate the main server process, defined with the _{service_name} _placeholder (where, depending on a server used, the possible values are: _jetty, mysql, tomcat, memcached, mongod, postgresql, couchdb, glassfish-domain1, nginx, php-fpm _and _httpd_)
  * **_sudo usr/bin/jem firewall {fwstart|fwstop} _**\- to run/stop container firewall respectively
  * **_sudo usr/bin/jem nscd _**\- to control the [name-service caching ](https://linux.die.net/man/8/nscd) daemon, which stores records for the most common name server requests (like _passwd, hosts, group _, etc)
  * **_sudo sbin/service rpcbind.service_** \- to operate with the service, used to map user-readable names to program numbers that handle incoming RPC calls

Any of the commands above, despite being run in a mode, does not require entering a server admin root password. This allows you to take advantage of all the required container functionality, essential for your application proper work, even with regular account permissions.

Now, as you know all the required basics to manage your containers via console, you can leverage even more PaaS flexibility while running your applications. [Get started with Jelastic Multi-Cloud ](https://jelastic.cloud/?utm_source=blog-ssh-to-container) at one of the certified service providers worldwide.

Cloud Foundry saves app developers $100K and 10 weeks on average per development cycle. [Download](https://dzone.com/go?i=295427&u=https%3A%2F%2Fwww.cloudfoundry.org%2Fcf-user-report-2018%2F%3Futm_source%3Ddzone%26utm_medium%3Dpaid%26utm_campaign%3Dleadgen) the 2018 User Survey for a snapshot of Cloud Foundry users' deployments and productivity. Find out what people love about the industry standard cloud application platform.

Topics:

ssh into server ,ssh command ,free ssh server ,ssh run remote command ,ssh command example ,ssh server ,ssh command line ,ssh key management ,ssh terminal commands ,ssh execute remote command
