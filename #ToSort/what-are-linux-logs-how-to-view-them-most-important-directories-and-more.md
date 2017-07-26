# What Are Linux Logs? How to View Them, Most Important Directories, and More

_Captured: 2017-06-27 at 20:50 from [dzone.com](https://dzone.com/articles/what-are-linux-logs-how-to-view-them-most-importan?edition=305152&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-26)_

Logging is a must for today's developers, and it's important to understand Linux logs, how to view them, and which logs are most important to your work. We wrote this mini-guide to give you all the need-to-know essentials in an easily digestible format. It won't take up your entire lunch break - promise!

### A Definition of Linux Logs

Linux logs provide a timeline of events for the Linux operating system, applications, and system, and are a valuable troubleshooting tool when you encounter issues. Essentially, analyzing log files is the first thing an administrator needs to do when an issue is discovered.

For desktop app-specific issues, log files are written to different locations. For example, Chrome writes crash reports to '~/.chrome/Crash Reports'). Where a desktop application writes logs depends on the developer, and if the app allows for custom log configuration.

Files are stored in plain-text and can be found in the **/var/log** directory and subdirectory. There are Linux logs for everything: system, kernel, package managers, boot processes, Xorg, Apache, MySQL. In this article, the topic will focus specifically on Linux system logs.

You can change to this directory using the **cd** command. You'll need to be the root user to view or access log files on Linux or Unix-like operating systems.

### How to View Linux Logs

Use the following [commands to see log files](https://www.linux.com/learn/sysadmin/viewing-linux-logs-command-line):

Linux logs can be viewed with the command **cd/var/log**, then by typing the command** ls **to see the logs stored under this directory. One of the most important logs to view is the _syslog_, which logs everything but auth-related messages.

Issue the command **var/log/syslog **to view everything under the syslog, but zooming in on a specific issue will take a while, since this file tends to be long. You can use _Shift+G_ to get to the end of the file, denoted by "END."

You can also view logs via **dmesg, **which prints the kernel ring buffer. It prints everything and sends you to the end of the file. From there, you can use the command **dmesg | less **to scroll through the output. If you want to view log entries for the user facility, you need to issue the command **dmesg -facility=user.**

Lastly, you can use the **tail **command to view log files. It is one of the handiest tools you can use, since it only shows the last part of the logs, where the problem usually lies. For this, use the command **tail /var/log/syslog **or** tail** **-f /var/log/syslog. **_tail_ will continue watching the log file, and print out the next line written to the file, allowing you to follow what is written to syslog as it happens. Check out [20 ways to tail a log file](https://stackify.com/13-ways-to-tail-a-log-file-on-windows-unix/) post.

For a specific number of lines (example, the last 5 lines) key in **tail** **-f -n 5 /var/log/syslog**, which prints the most recent 5 lines. Once a new line comes, the old one gets removed. To escape the tail command, press Ctrl+X.

### Most Important Linux Logs

Most directories can be grouped into one of four categories:

  * Application Logs
  * Event Logs
  * Service Logs
  * System Logs

Monitoring every log is a monumental task, making tools like [Retrace](https://stackify.com/retrace/), which combines APM with centralized [log management](https://stackify.com/log-management/) - enabling you to collect all of your log data in one place - essential for developers. The logs that you monitor may depend on your goals or other variables, but there is some consensus about some of the most critical, [must-monitor logs](https://www.eurovps.com/blog/important-linux-log-files-you-must-be-monitoring), such as:

  * **/var/log/syslog **or **/var/log/messages**: general messages, as well as system-related information. Essentially, this log stores all activity data across the global system. Note that activity for Redhat-based systems, such as CentOS or Rhel, are stored in messages, while Ubuntu and other Debian-based systems are stored in Syslog.
  * **/var/log/auth.log **or **/var/log/secure**: store authentication logs, including both successful and failed logins and authentication methods. Again, the system type dictates where authentication logs are stored; Debian/Ubuntu information is stored in /var/log/auth.log, while Redhat/CentrOS is stored in /var/log/secure.
  * **/var/log/boot.log**: a repository of all information related to booting and any messages logged during startup.
  * **/var/log/maillog or var/log/mail.log:** stores all logs related to mail servers, useful when you need information about postfix, smtpd, or any email-related services running on your server.
  * **/var/log/kern**: stores Kernel logs and warning data. This log is valuable for troubleshooting custom kernels as well.
  * **/var/log/dmesg**: messages relating to device drivers. The command **dmesg** can be used to view messages in this file.
  * **/var/log/faillog:** contains information all failed login attempts, which is useful for gaining insights on attempted security breaches, such as those attempting to hack login credentials as well as brute-force attacks.
  * **/var/log/cron**: stores all Crond-related messages (cron jobs), such as when the cron daemon initiated a job, related failure messages, etc.
  * **/var/log/yum.log:** if you install packages using the** yum** command, this log stores all related information, which can be useful in determining whether a package and all components were correctly installed.
  * **/var/log/httpd/**: a directory containing error_log and access_log files of the Apache httpd daemon. The **error_log** contains all errors encountered by httpd. These errors include memory issues and other system-related errors. **access_log** contains a record of all requests received over HTTP.
  * **/var/log/mysqld.log **or** /var/log/mysql.log **: MySQL log file that logs all debug, failure and success messages. Contains information about the starting, stopping and restarting of MySQL daemon mysqld. This is another instance where the system dictates the directory; RedHat, CentOS, Fedora, and other RedHat-based systems use /var/log/mysqld.log, while Debian/Ubuntu use the /var/log/mysql.log directory.

What does the output look like? Here's an example of a [Crontab edited by root](https://ossec-docs.readthedocs.io/en/latest/log_samples/linux/cron.html) log:
    
    
    Sep 11 09:46:33 sys1 crontab[20601]: (root) BEGIN EDIT (root)
    
    
    Sep 11 09:46:39 sys1 crontab[20601]: (root) REPLACE (root)
    
    
    Sep 11 09:46:39 sys1 crontab[20601]: (root) END EDIT (root)

And here's a case of [Syslogd on Ubuntu](https://ossec-docs.readthedocs.io/en/latest/log_samples/linux/syslogd.html) (exiting and restarting):

And [system shutdown](https://ossec-docs.readthedocs.io/en/latest/log_samples/linux/kernel.html) from the Linux kernel:

A few other directories and their uses include:

  * **/var/log/daemon.log:** tracks services running in the background that perform important tasks, but has no graphical output.
  * **/var/log/btmp**: recordings of failed login attempts.
  * **/var/log/utmp**: current login state, by user.
  * **/var/log/wtmp**: login/logout history.
  * **/var/log/lastlog**: information about the last logins for all users. This binary file can be read by command **lastlog**.
  * **/var/log/pureftp.log**: runs the pureftp process that listens for FTP connections. All connections, FTP logins, and authentication failures get logged here.
  * **/var/log/spooler**: rarely used and often empty. When used, it contains messages from USENET.
  * **/var/log/xferlog**: contains all FTP file transfer sessions, including information about the file name and user initiating FTP transfers.

Understanding the usefulness and limitations of Linux logging is important for any professional working with them. What Linux logs do you consider most important to monitor? Leave your thoughts in the comments below.

## Additional Resources and Tutorials on Linux Logs
