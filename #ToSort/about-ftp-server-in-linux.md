# About FTP Server in Linux

_Captured: 2017-04-06 at 20:14 from [dzone.com](https://dzone.com/articles/ftp-server-in-linux?edition=288884&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-06)_

Build APIs from SQL and NoSQL or Salesforce data sources in seconds.[ Read the Creating REST APIs white paper](https://dzone.com/go?i=142024&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309714743%3B137084581%3Bk), brought to you in partnership with [CA Technologies](https://dzone.com/go?i=142024&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309714743%3B137084581%3Bk).

File transfer protocol (FTP) is a network protocol used to transfer files between computers. One acts as a client and the other acts as a server. In this post, we will talk about FTP server in Linux systems, specifically the very secure FTP daemon (vsftpd).

The vsftpd program is a very popular FTP server that is being used by many servers today.

## How FTP Server Works

FTP server works with client-server architecture to communicate and transfer files.

FTP is a stateful protocol, meaning that connections between clients and servers are created and kept open during an FTP session.

To send or receive files from an FTP server, you use FTP commands. These commands are executed consecutively. It is like a queue, one by one.

There are two types of FTP connections initiated:

  1. Control connection (also called a command connection).
  2. Data connection.

When you establish an FTP connection, a single control connection is established by default using the TCP port 21. This connection is used for the authentication process.

A data connection is established only when a file needs to be transferred.

There are two types of data connections:

  1. Passive mode.
  2. Active mode.

Active connections are initiated by the remote server, and the client listens for the connection.

Passive connections use the PASV command; the client initiates the connection to the remote server, and the server listens for the data connections.

When the FTP client starts a transfer, it tells the server what type of connection it wants to make.

### Active Mode

In active mode, the client connects from a random source port in the ephemeral port range to the FTP control port 21.

You can check your ephemeral port range using `$ cat /proc/sys/net/ipv4/ip_local_port_range`.

When you actually want to transfer a file, the remote FTP server will initiate a connection from the FTP data port 20 on the server system back to a destination port in the ephemeral port range on the client

Active mode connections often have issues with firewalls. Also, you need to have the TCP ports 20 and 21 open on your firewall.

Because of these problems with firewalls in active mode, passive mode was introduced.

If you are using the iptables firewall, I recommend you to review my [Linux iptables firewall](https://likegeeks.com/linux-iptables-firewall-examples/) post to know how to allow ports.

### Passive Mode

In passive mode, the client initiates the control connection from a random ephemeral port on the client to the destination port of 21 on the remote server. When it needs to make a data connection, the client will issue the PASV FTP command. The server will respond by opening a random ephemeral port on the server and passing this port number back to the client via the control connection.

The client will then open a random ephemeral source port on the client and initiate a connection between that port and the destination remote port provided by the FTP server.

That's why they said that the FTP is connection-hungry -- because every time you make a data connection (like transfer a file), the server will do the above process, and this is done with all clients connected to the server.

In passive mode, the client initiates both the control and data connections. Thus, firewalls see the outgoing FTP data connection as part of an established connection.

You need to have ephemeral ports open on the server and client side of the connection, but firewalls would disallow the connections that originate from the Internet that are destined for ephemeral ports.

Many firewalls implement application-level proxies (mean that they look deeply into packets for analysis) for FTP, which keeps track of FTP requests and opens up those high ports when they're needed to receive data from a remote site.

## Vsftpd FTP Server Features

There are several FTP servers available for you to use, both commercial and open source.

Vsftpd has some great security features like:

  * Can run as a non-privileged user with privilege separation.
  * Supports SSL/TLS FTP connections.
  * Can chroot users into their home directories.
  * Can limit the FTP commands that a user can execute.
  * Reduces the risk of DoS attacks with connection limits.

## FTP Server Setup

Some Linux distros shipped with vsftpd, if you want to install it on Red Hat-based systems, you can use `$ sudo dnf -y vsftpd`.

On Debian-based distros like Ubuntu, you can use the `$ sudo apt-get install vsftpd`.

Once you've installed the package, you can run the service and enable it to run at boot time.

The configuration file for the vsftpd FTP server is `/etc/vsftpd/vsftpd.conf`. In Debian-based distros, you can find it at `/etc/vsftpd.conf`.

Actually, the FTP server in Linux is one of the easiest servers that you can work with.

There are two types of accessing the FTP server:

  * **Anonymous FTP access**: Anyone can login with the username _anonymous_ without a password.
  * **Local user login**: All valid users on `/etc/passwd` are allowed to access the FTP server using their usernames and passwords.

You can allow or prevent anonymous access to the FTP server from the configuration in `/etc/vsftpd/vsftpd.conf` and enable `anonymous_enable=YES` if it is not enabled and reload your service.

Now, you can try to connect to the FTP server using any FTP client. I will use the simple FTP command. You can install it if it is not on your system with `$ dnf -y install ftp`.

Now you can access your FTP server with `$ ftp localhost`.

Then type the username anonymous and with no password, just press **_enter_**.

You will be presented with the FTP prompt.

Now, you can type any FTP command to interact with the FTP server.

### Connect as Local User

Since there is an option on the setting for allowing local users to access FTP server (`local_enable=YES`), let's try to access the FTP server using a local user: `$ ftp localhost`.

Then, type your local username and the password for that user and you will see a "Login successful" message.

## Set Up FTP Server as Anonymous Only

This type of FTP server is useful for large sites that have files that should be available to the public via FTP without any passwords or login.

You need to configure vsftpd to allow anonymous users only.

Open `/etc/vsftpd/vsftpd.conf` and change the following options with the corresponding values:

Then, we need to create a non-privileged system account that is used especially for anonymous FTP-type access: `$ useradd -c " FTP User" -d /var/ftp -r -s /sbin/nologin ftp` .

This user has no privileges on the system, so it is safer to use it when accessing the FTP server.

Don't forget to restart your FTP server after you modify the configuration file.

You can access the FTP server from the browser -- just type _ftp://youdomain/_.

## FTP Server Security

We can configure vsftpd to use TLS so the transferred files over the network a bit more secure.

First, we generate a certificate request using `$ openssl genrsa -des3 -out FTP.key`.

Then we generate a certificate request with `$ openssl req -new -key FTP.key -out certificate.csr`.

Now, we remove the password associated with the key file.

Finally, we generate our certificate
    
    
    $ openssl x509 -req -days 365 -in certificate.csr -signkey ftp.key -outmycertificate.crt

Now, we copy both the key and the certificate file to `/etc/pki/tls/certs`.

Now, all we need to do is configure vsftpd to support secure connections. Open the `/etc/vsftpd/vsftpd.conf` file and add the following lines:

Restart your service to reflect these changes.

And that's it!

Try to connect to your FTP server from any client on any system like Windows and choose the secured connection or FTPS, and you will successfully see your folders.

## SFTP vs. FTPS

In the last example, we saw the FTP-over-SSL layer (FTPS) and we've successfully connected to the FTP server, however, with the tightly secured firewall, it is difficult to manage this kind of connection since FTPS uses multiple port numbers.

The best solution is to use SFTP (FTP-over-SSH). SFTP only needs a single port number, which is port 22. This port is used for all connections during FTP sessions.

Briefly, SFTP and FTPS are both very secure -- but SFTP is much easier to port through firewalls.

## Jailing FTP Users

You can secure your FTP server by jailing your FTP users in their homes directories and allow only specific users to access the service.

Open `/etc/vsftpd/vsftpd.conf` and uncomment the following options:

The file `/etc/vsftpd.chroot_list` contains the list of jailed users -- one per line.

Save the files and restart your service with `$ systemctl restart vsftpd`.

## Linux FTP Server Commands

You can use any GUI client to upload and download your files, but you need to know some FTP server commands, as well.

`ftp> pwd`
Print the current working directory (you will see your home folder).

`ftp> ls`  

List files.

`ftp> cd /`  

Change the working directory. 

`ftp> bye`  

Exit your FTP session.

`ftp> lcd`  

Display the local folder instead of the FTP folder.

`ftp> lcd /home`  

Change the local directory.

`ftp> get mysfile`  

Download a file.

`ftp> mget file1 file2`  

Download multiple files.

`ftp> delete filename`  

Delete a file from the server.

`ftp> mput file1 file2`  

Upload multiple files.

`ftp> mkdir dirName`  

Create a directory.

`ftp> rmdir dirName`  

Delete a directory.

There are two modes for file transfer when using FTP server: ASCII mode and binary mode. You can change it like this:

FTP server is one of the easiest servers in Linux to work with and configure.

The Integration Zone is brought to you in partnership with [CA Technologies](https://dzone.com/go?i=142025&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309714699%3B137084580%3Bt). Use CA Live API Creator to quickly [create complete application backends, with secure APIs and robust application logic](https://dzone.com/go?i=142025&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Fclk%2F309714699%3B137084580%3Bt), in an easy to use interface.
