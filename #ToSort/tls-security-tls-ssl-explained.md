# TLS Security: TLS/SSL Explained

_Captured: 2017-05-05 at 23:51 from [dzone.com](https://dzone.com/articles/tls-security-tlsssl-explained)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

In this series on TLS security, we will focus on two widely known and used protocols in computer security, **SSL** and **TLS**. We will first start off with SSL, which stands for **Secure Socket Layer** and then we will talk about its successor, TLS, which stands for **Transport Layer Security**.

Many people, quite often use these terms but do not really understand the underlying technology and mechanics behind these protocols. The reason is simple. Behind these protocols, there is a complicated network of cryptographic functions, algorithms, and structures.

Having established that understanding how SSL/TLS works can be a challenge, so we will try to give a simple yet comprehensive overview of it.

## What Is TLS/SSL?

The Transport Layer Security (TLS), and Secure Socket Layer (SSL) protocols' main purpose is to provide: privacy and integrity; identification; and perfect forward secrecy.

### Privacy and Integrity

It allows the connection between two mediums (client-server) to be encrypted. By encrypting the communication, we ensure that no third-party is able to read or tamper with the data that is being exchanged on our connection with the server. An unencrypted communication could and would expose sensitive data such as usernames, passwords, credit card numbers, and generally anything that is being sent back and forth during the connection.

Using a normal - unencrypted - connection, if a third party intercepted our connection with the server, they would be able to see information exchanged in plaintext (human readable format). If, for example, we access our website's administration panel without SSL and someone is sniffing the local network's traffic, they would be able to see the following:

![TLS Security ](https://www.acunetix.com/wp-content/uploads/2017/01/image32.png)

The cookie which we use to authenticate on our website is now sent in plain text and anyone intercepting the connection can see it. This means that an attacker can use this information to log in to our website's administration panel. From then on the attacker's options expand dramatically for data leak or further exploitation.

However, if we access our website using SSL/TLS, they would see something quite different.

![TLS/SSL ](https://www.acunetix.com/wp-content/uploads/2017/01/image04-1.png)

> _In this case, the information is useless to the attacker._

### Identification

With the use of Public Key Cryptography, SSL/TLS provides identification between the communicating parties. This means that one (most commonly the server), or both parties, know who they are communicating with. This is crucial, especially in the event of online transactions, as we need to ensure we are transferring money to the person or company who are who they claim to be.

When a secure connection is established, the server will send its SSL certificate to the client. The certificate will then be checked by the client against a trusted Certificate Authority, essentially validating the server's identity. We will see how an SSL certificate is created later on in this series.

### Perfect Forward Secrecy

Simply put, PFS's primary job is to make sure that in the event of the private key of a server being compromised, an attacker will not be able to decrypt any previous TLS communications. Perfect Forward Secrecy is possible by using the Diffie-Hellman ephemeral key exchange, which provides new keys for every session and is valid as long as the session is active.

## Application

SSL/TLS protocols can be used in different services such as the web, mail, FTP, VoIP, and VPN. Typically, when a service uses a secure connection the letter S is appended to the service's protocol name. For example: HTTP**S**, SMTP**S**, FTP**S**, SIP**S**.

Tune in next time for the history of SSL/TLS!

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.
