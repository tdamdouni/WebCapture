# Apprentice Blog of the Week: SSH Over the Internet!

_Captured: 2015-10-17 at 22:15 from [blog.8thlight.com](http://blog.8thlight.com/andrew-spalding/2014/07/29/ssh-over-the-internet.html)_

One of my hobbies is Linux. My home server is a Raspberry Pi running [Debian](https://www.debian.org/). It currently hosts a local [gitlist](http://gitlist.org/) instance over Nginx and SSH. This past week I decided to secure my SSH connection so I could open a port to the external Internet. In addition to the Raspberry Pi, I have a router that has an open source Linux-based firmware. The router handles a variety of Dynamic DNS services.

As a security habit, I haven't had a public-facing server in my home for quite some time now. SSH servers are a frequent target for people looking to exploit insecure computers. It is advised that you do not allow password logins or the root user to log in over SSH. However, I still desired to have those settings while on my local network. In accordance, I set up my `sshd_config` to use a match rule. That rule is as follows:
    
    
    1 Match Address *,!192.168.1.0/24
    2 PasswordAuthentication no
    3 PermitRootLogin no
    4 MaxAuthTries 2

In plain English, the rule says that if your address lies outside my local subnet (192.168.1.X), then you cannot simply log in with a password. Logging in as root is not allowed, and you only get two shots. With password authentification disabled, a public key/private key is required to log on. To generate these I utilized `ssh-keygen` and `ssh-copy-id`.

Another hurdle when opening up to the rest of the Internet is that most of our Internet providers do not give us a static public IP address. To deal with this, I've signed up for [freedns](http://freedns.afraid.org/). The firmware I installed on my router lets it talk directly to this service. When my IP address changes, my router tells the DDNS provider. When everything is ready to go, check your port configuration, create an entry pointing to the static ip address you've given your server, and enable TCP port 22.

Checking the tail log, you can see failed attempts. The behavior below seems to reflect a script trying common user name possibilities (a postgres user, for example, may be a common user name, as many people rely on the postgres database).
    
    
     1 $ tail /var/log/auth.log -n 100
     2 Jul 26 23:14:25 piserver sshd[2053]: Invalid user zabbix from 210.211.99.244
     3 Jul 26 23:14:25 piserver sshd[2053]: input_userauth_request: invalid user zabbix [preauth]
     4 Jul 26 23:14:25 piserver sshd[2053]: Received disconnect from 210.211.99.244: 11: Bye Bye [preauth]
     5 Jul 26 23:14:32 piserver sshd[2058]: Invalid user postgres from 210.211.99.244
     6 Jul 26 23:14:32 piserver sshd[2058]: input_userauth_request: invalid user postgres [preauth]
     7 Jul 26 23:14:33 piserver sshd[2058]: Received disconnect from 210.211.99.244: 11: Bye Bye [preauth]
     8 
     9 $ cat /var/log/auth.log | grep "Accepted"
    10 Jul 24 04:17:09 piserver sshd[30576]: Accepted password for pi from 192.168.1.113 port 63580 ssh2
    11 Jul 24 14:18:37 piserver sshd[31235]: Accepted publickey for andrew-8thlight from x.x.x.x port 49825 ssh2
    12 Jul 25 20:58:29 piserver sshd[688]: Accepted publickey for andrew-8thlight from x.x.x.x port 5541 ssh2

Listed above are successful log-ins. The IP addresses that have been crossed out reflect my work addresses. You can see that passwords are still being accepted on my local subnet, and both successful logins from an external IP have a public key. I'll be keeping an eye on these logs for a couple weeks, but my server should be sheltered from the majority of attacks!
