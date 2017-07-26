# About Linux Mail Server

_Captured: 2017-04-10 at 01:07 from [dzone.com](https://dzone.com/articles/linux-mail-server?edition=288887&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-09)_

Learn how API management supports better integration in [Achieving Enterprise Agility with Microservices and API Management](https://dzone.com/go?i=126027&u=http%3A%2F%2Fpages.3scale.net%2Fmicroservices-api-management-dzinteg.html), brought to you in partnership with [3scale](https://dzone.com/go?i=126027&u=https%3A%2F%2Fwww.3scale.net%2F%3Futm_campaign%3Ddzintegration%26utm_source%3Ddzoneint%26utm_content%3Dbumper)

If you want to send or receive an email, you should have a mail server capable of sending and receiving mail across the Internet. In this post, we will discuss the Linux mail server and how SMTP protocol (the standard protocol for mail transport across the internet) works, as well as other mail-related protocols like Post Office Protocol (POP) and Internet Message Access Protocol (IMAP) and the relationship between them.

## Linux SMTP Server

SMTP (Simple Mail Transfer Protocol) defines how mail is sent from one host to another. It does not define how the mail should be stored or how it is displayed. It is also system-independent, which means that the sender and receiver could have different operating systems.

SMTP requires only that a server is able to send straight ASCII text to another server, and this is done by connecting to the server on _port 25_which is the standard SMTP port.

Most Linux distros today are shipped with two of the most common implementation of SMTP: `sendmail` and `postfix`.

Sendmail is a popular open-source mail server implementation used by many Linux distros, but it has a little complex design and less secured. The Postfix took mail server implementation one step further -- it was developed with security in mind.

## Mail Service Components

The mail service on any mail server has three components:

  1. **Mail user agent** (MUA). This is a component that the user sees and interacts with (like Thunderbird and Microsoft Outlook). These user agents are responsible for reading mail and allowing you to compose mail.

  2. **Mail transport agent** (MTA). This component is responsible for getting the mail from one site to another (like Sendmail and Postfix).

  3. **Mail delivery agent** (MDA). This component is responsible for distributing received messages on the local machine to the appropriate user mailbox (like `postfix-maildrop` and Procmail).

## Set Up Email Server

We chose the Postfix mail server, which is a very popular and common between system administrators today. Postfix is the default mail server on most modern Linux distros.

First, check if it is installed on your system or not: `$ rpm -qa | grep postfix`.

If it's not installed, you can install the Postfix mail server on Red Hat-based distros with `$ dnf -y install postfix`.

Then, start the `postfix` service and enable it upon system startup:

On Debian-based distros like Ubuntu, you can install it with `$ apt-get -y install postfix` .

You will be prompted to select your Postfix mail server configuration type during the installation process.

Among the choices of No Configuration, Internet Site, Internet With Smarthost, Satellite System, and Local Only, we will choose the No Configuration option. It will create the necessary user and group accounts that Postfix needs.

## Linux Mail Server Configuration

After installing the Postfix mail server, you will need to configure it. Most of its configuration files can be found under the `/etc/postfix/` directory. You can find the main configuration for Postfix mail server through the `/etc/postfix/main.cf` file.

This file contains a lot of options. We will cover the most important options of them.

### **myhostname**

This option is used for specifying the hostname of the mail system. This is the Internet hostname for which Postfix will be receiving e-mail. Typical examples of mail server hostnames are _mail.example.com_ and _smtp.example.com_.

It is written like this: `myhostname = mail.example.com`.

### **mydomain**

This option is the mail domain that you will be servicing, like _example.com_.

The syntax is like this: `mydomain = example.com`.

### **myorigin**

All e-mails sent from this mail server will look as though they came from this option. You can set this to the `$mydomain` value: `myorigin = $mydomain`.

You can use any option value by placing `$` in front of the variable name.

### **mydestination**

This option lists the domains that the Postfix server will take as its final destination for incoming email. This value is set to the hostname of the server and the domain name, but it can contain other names like this.

`mydestination = $myhostname, localhost.$mydomain, $mydomain,mail.$mydomain,   
www.$mydomain`

### **mail_spool_directory**

There are two modes of delivery that Postfix mail server can use:

  1. Directly to a user's mailbox.
  2. To a central spool directory (this way, the mail will be in `/var/spool/mail` with a file for each user).

Here's the syntax: `mail_spool_directory = /var/spool/mail`.

### **mynetworks**

This variable is an important configuration option. This lets you configure what servers can relay through your Postfix server.

You will usually want to allow relaying from local client machines like mail scripts on your server only. Otherwise, spammers can use your mail server to relay messages.

If you do not set the `mynetworks` variable correctly and spammers begin using your mail server as a relay, it is a fast way to get your mail server blacklisted by a spam control technique like a DNS Blacklist (DNSBL) or Realtime Blackhole List (RBL). Once your server is blacklisted, very few people will be able to receive mail from you.

This option has the following syntax: `mynetworks = 127.0.0.0/8, 192.168.1.0/24`.

### **smtpd_banner**

This variable allows you to return a custom response when a client connects to your mail server

It is better to change the banner to something that doesn't give an indication about the server you are using.

### **inet_protocols**

This variable is used to specify the Internet protocol version that Postfix will use when making a connection: `inet_protocols = ipv4`.

If you change the configuration files for Postfix mail server, you need to reload the service with `$ systemctl reload postfix`.

There are more variables in the Postfix configuration file. You may notice that they are commented. These variables allow you to set security levels, debugging levels, and other variables.

You can check for errors using `$ postfix check`. This tool will help you find exactly the line and the error so you can fix it.

## Checking the Mail Queue

Sometimes the mail queues on your system will fill up. This can be caused by many reasons like network failure or any reason that can delay mail delivery.

To check the mail queue on your Linux mail server, use `$ mailq`.

This command will display all of the messages that are in the Postfix mail queue.

If your queue is fill up and the message takes several hours to be sent, then you should flush the mail queue.

$ postfix flush

Now if you check your mail queue you should find it empty.

## Test Linux Mail Server

After configuring Postfix mail server correctly, you should test your mail server.

The first step in doing this is to use a local mail user agent like `mailx` or `mail`, which is a symlink to `mailx`.

Try to send mail to someone else on the same server. If this works, then send it to a remote site:

Then, try to receive mail from a remote site.

If you have any problems, check the logs. The log file is on Red Hat-based distros in the `/var/log/maillog` file and is on Debian-based distros in the `/var/log/mail.log` file (or as defined in `rsyslogd` configuration).

I recommend you to review the post about [Linux Syslog Server](https://dzone.com/articles/linux-syslog-server-and-log-management) for a detailed explanation about logs and how to configure the `rsyslogd`.

If you still have problems, try checking your DNS settings and check your MX records using [Linux network commands](https://dzone.com/articles/most-useful-linux-command-line-tricks).

## Fight Spam

There are many solutions available that scan mail, searching for certain patterns associated with spam. One of best solutions is SpamAssassin, which is also open source. You can install it like this: `$ dnf -y install spamassassin`:

Then, start the service and enable it at startup

Once you've installed it, you can check the configuration in `/etc/mail/spamassassin/local.cf`.

SpamAssassin determines if an e-mail is spam or not based on the result of the different scripts scores. The higher the score, the higher the possibility of the mail being spam.

In the configuration file, the parameter `required_hits 5` indicates that SpamAssassin will mark an e-mail as spam if its score is 5 or higher.

The `report_safe` option takes the values 0, 1, or 2. If set to 0, this means that e-mail marked as spam is sent as it is, only modifying the headers to show that it is spam. If it takes value 1 or 2, a new report message is generated by SpamAssassin and sent to the recipient.

The difference between the values 1 and 2 is that in the first case, the spam message is coded as content message/rfc822, while in the second case, it will be coded as content text/plain. The text/plain option is safer since some mail clients execute message/rfc822 and could infect the client computer.

Now, we need to integrate it into Postfix. The easiest way to do this is probably by using Procmail.

We'll have to create a file named `/etc/procmailrc` and add the following content:

Then, we edit Postfix configuration file `/etc/postfix/main.cf` and change the `mailbox_command` wit `mailbox_command = /usr/bin/procmail`.

Finally, restart Postfix and SpamAssassin services:

SpamAssassin sometimes does not recognize spam messages, leading to mailboxes filled with spam messages. Fortunately, you can filter messages before they enter Postfix server using Realtime Blackhole Lists (RBLs). These will decrease the load on your mail server and keep your mail server clean.

Open the configuration file of Postfix server `/etc/postfix/main.cf` and change the `smtpd_recipient_restrictions` option. Add the other options like this:

Then, restart your Postfix server: `$ systemctl restart postfix`.

The above RBLs are the common ones. You can find more lists on the web and try them.

## Securing SMTP Connection

It is better to transfer your SMTP traffic over TLS to protect it from being modified in the middle. First, we need to generate the certificate and the key using `openssl` command:
    
    
    $ openssl req -new -key mail.key -out mail.csr
    
    
    $ openssl x509 -req -days 365 -in mail_secure.csr -signkey mail_secure.key -out mail_secure.crt

Then, add the following option to Postfix configuration file `/etc/postfix/main.cf`:

Finally, restart your Postfix service: `$ systemctl restart postfix`.

Now, you have to choose the TLS on your client when connecting to the server. You will receive a warning when you send mail the first time after changing the settings because of the certificate if it's not signed.

## POP3 and IMAP Protocol Basics

So far, we've seen how SMTP mail server sends and receives emails without problems. But consider the following situations:

  * Users need local copies of e-mail for offline viewing.
  * Mail user agents do not support the Mbox file format. The Mbox format is a simple text format that can be read by a number of console mail user agents like `mailx` and `mutt`.
  * Users cannot stay connected to a fast network for file system access for their Mbox file, so they want to grab a local copy to read offline.
  * Security requirements dictate that users not have direct access to the email-gate -- for example, shared mail spool directories are considered unacceptable for security reasons.

To handle these cases, another class of protocols was introduced: mail access protocols.

The two most common and popular mail access protocols are Post Office Protocol (POP) and Internet Message Access Protocol (IMAP).

The idea behind POP is very simple. A central Linux mail server remains online all the time and receives and stores emails for all users. All received emails are queued on the server until a user connects via POP and downloads the queued mail.

When a user wants to send an e-mail, the e-mail client relays it through the central Linux mail server via SMTP normally.

Note that SMTP server and POP server can be on the same system without any problems. Most servers do this today.

Features like keeping a master copy of a user's e-mail on the server with only a cached copy on the client side were missing, which led to the development of IMAP.

By using IMAP, your Linux mail server will support three modes of access:

  1. The online mode is similar to having direct file system access to the Linux mail server.
  2. The offline mode is similar to how POP works; the client is disconnected from the network except when grabbing an e-mail. In this mode, the server normally does not retain a copy of the mail.
  3. The disconnected mode works by allowing users to retain cached copies of their emails and the server retains a copy of the mail.

There are several implementations for IMAP and POP. The most popular one is Dovecot server, which provides both protocols.

The POP3, POP3S, IMAP, and IMAPS listen on ports 110, 995, 143, and 993, respectively.

## Installing Dovecot

Most Linux distros comes with dovecot preinstalled. However, you can install dovecot in Red Hat-based distros like this: `$ dnf -y install dovecot`.

On Debian-based distros IMAP and POP3, functionality is provided in two separate packages. You can install them like this: `$ apt-get -y install dovecot-imapd dovecot-pop3d`.

You will be prompted to create self-signed certificates for using IMAP and POP3 over SSL/TLS. Select **_Yes_** and enter the hostname for your system when prompted.

Then, you can run the service and enable it at startup like this:

## Dovecot Configuration

The main configuration file for Dovecot is the `/etc/dovecot/dovecot.conf` file.

Some Linux distros put the configuration under the `/etc/dovecot/conf.d/` directory and use the `include` directive to include the settings in the files.

The following list is the some of the parameters used to configure Dovecot.

### **Protocols**

These are the protocols you want to support: `protocols = imap pop3 lmtp`.

`lmtp` means local mail transfer protocol.

### **Listen**

IP addresses to listen on `listen = *, ::`.

`*` represents all IPV4 interfaces and `::` represents all IPV6 interfaces.

### **UserDB**

This is the user database for authenticating users:

### **PassDB**

This is the password database for authenticating users:

### **Mail_location**

This entry is in the `/etc/dovecot/conf.d/10-mail.conf` file and written like `mail_location = mbox:~/mail:INBOX=/var/mail/%u`.

Dovecot comes with generic SSL certificates and key files that are used in `/etc/dovecot/conf.d/10-ssl.conf`:

When a user tries to connect to Dovecot server, it will show a warning because the certificates are not signed. You can purchase a certificate from a certificate authority if you want.

Don't forget to open Dovecot server ports in your firewall:

And the SMTP port: `$ iptables -A INPUT -p tcp --dport 25 -j ACCEPT`.

Then, save the rules. You can review my [Linux iptables firewall](https://likegeeks.com/linux-iptables-firewall-examples/) post.

Or, if you are using firewalld, you can do the following:
    
    
    $ firewall-cmd --permanent --add-port=110/tcp --add-port=995
    
    
    $ firewall-cmd --permanent --add-port=143/tcp --add-port=993

And again, for troubleshooting, you check the log files `/var/log/messages`, `/var/log/maillog`, and `/var/log/mail.log` files

Linux mail server is one of the easiest servers to work with especially Postfix mail server.

Unleash the power of your APIs with future-proof API management - [Create your account](https://dzone.com/go?i=126028&u=http%3A%2F%2Fpages.3scale.net%2Ffuture-proof-api-management-dzinteg.html) and start your free trial today, brought to you in partnership with [3scale](https://dzone.com/go?i=126028&u=https%3A%2F%2Fwww.3scale.net%2F%3Futm_campaign%3Ddzintegration%26utm_source%3Ddzoneint%26utm_content%3Dbumper).
