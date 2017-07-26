# Establishing a TLS Connection, Part 4

_Captured: 2017-05-05 at 23:53 from [dzone.com](https://dzone.com/articles/establishing-a-tls-connection-part-4)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

In Parts 1, 2, and 3 of this series we looked at _[What is TLS/SSL?](https://dzone.com/articles/tls-security-tlsssl-explained),__ [TLS/SSL terminology and basics](https://dzone.com/articles/tlsssl-terminology-and-basics) _and _[TLS/SSL Certificates](https://dzone.com/articles/tlsssl-certificates-part-4)_. In this, the fourth, part in the series, we will be looking at establishing a TLS connection.

To get a better understanding of the TLS protocol, we will now see what exactly takes place for a secure connection to be established.

The most important process of the connection establishment is the so-called "**Handshake**". During the Handshake, the server and client will exchange important information regarding the properties under which the connection will be established.

During the Handshake, we will see how a hybrid of asymmetric and symmetric encryption is used in order to ensure security.

For this article, we will refer to a browser as the Client. In the following example, Diffie-Hellman is used for the key exchange.

## Client Hello

A standard negotiation between client-server (the handshake) starts off with a Client Hello message.

The client sends a **Client Hello** to the server and includes the following.

![Client hello](https://www.acunetix.com/wp-content/uploads/2017/01/image15.png)

### client_version

The client will send a list of all the SSL/TLS protocol versions it supports, with the preferred one being first on the list. The preferred one is usually **and should be**, the latest available version.

### random

A 32-byte piece of random data of which 4 bytes represent the client's current datetime (in epoch format) and the remaining 28 bytes, a randomly generated number. The Client's random and the Server's random will later be used to generate the key with which the data will be encrypted.

### session_id

This is the session id which will be used for the connection. If the session_id is **not** empty, the server will search for previously cached sessions and resume that session if a match is found.

### compression_methods

This is the method that is going to be used for compressing the SSL packets. By using compression, we can achieve lower bandwidth usage and therefore, faster transfer speeds. Later on this article, we will see why using compression is risky.

### cipher_suites

Cipher suites are a combination of cryptographic algorithms which are used to define the overall security of the connection to be established. Typically, each cipher suite contains one cryptographic algorithm for each of the following: Key Exchange, Authentication, Bulk (data) Encryption, and Message Authentication.

The following is a sample cipher suit:  
**TLS_ECDHE_ECDSA_**WITH**_AES_128_GCM_SHA256**

Let's break this down so that it makes more sense.

  * **TLS** is the protocol being used.
  * **ECDHE** is the key exchange algorithm **(Elliptic curve Diffie-Hellman).**
  * **ECDSA** is the authentication algorithm **(Elliptic Curve Digital Signature Algorithm).**
  * **AES_128_GCM** is the data encryption algorithm **(Advanced Encryption Standard 128 bit Galois/Counter Mode).**
  * **SHA256** is the Message Authentication Code (MAC) algorithm **(Secure Hash Algorithm 256 bit).**

Here's what an actual Client Hello looks like in a Wireshark capture:

![Wireshark capture](https://www.acunetix.com/wp-content/uploads/2017/01/image35.png)

The client can request additional functionality for the connection and this can be done via "**extensions**." If the server cannot provide the additional functionality, then the client can abort the handshake if needed.

## Server Hello

![Server Hello](https://www.acunetix.com/wp-content/uploads/2017/01/image23.png)

After the server receives the Client Hello, the second step will be to reply with a Server Hello. If it finds an acceptable set of algorithms in the Client's request, it will respond by accepting those options and provide its certificate. If the server does not meet the requirements of the Client it will respond with a handshake failure message.

The server sends a **Server Hello** to the client and includes the following.

### server_version

The server will (not blindly) select the Client's preferred version of SSL/TLS protocol.

### random

32 bytes of random data, out of which 4 bytes represent the server's current datetime (in epoch format), and the rest of the 28 bytes are a randomly generated number that will be sent to the client. The Server's random and the Client's random will, later on, be used to generate the key with which the data will be encrypted.

### session_id

This is the session id which will be used for the connection. If the session_id sent by the Client is not empty, the server will search for previously cached sessions and if a match is found, that session id will be used, thus resuming. If the session_id is empty, a new session will be created for the connection.

### compression_methods

If supported, the server will agree on the Client's preferred compression method.

### cipher_suites

If supported, the server will agree on the Client's preferred cipher suite.

### certificate

The signed certificate of the server which proves it's identity to the client. It also contains the public key of the server.

### Client Certificate (Optional)

Not often, the server may require the client to be authenticated with a Client Certificate as well. In cases like this, the client will provide its signed certificate to the server.

### Server Key Exchange

The server key exchange message is sent only if the certificate provided by the server is not sufficient to allow the client to exchange a pre-master secret. (This is true for **DHE_DSS, DHE_RSA,** and **DH_anon**)

### Server Hello Done

This is sent to the client as a confirmation that the Server Hello message is completed.

The following is what a Server Hello looks like in a Wireshark capture:

![server hello wireshark capture](https://www.acunetix.com/wp-content/uploads/2017/01/image16.png)

![SSL TLS](https://www.acunetix.com/wp-content/uploads/2017/01/image25.png)

## Client Key Exchange

![Key Exchange](https://www.acunetix.com/wp-content/uploads/2017/01/image22.png)

The** Client Key Exchange** message is sent right after the Server Hello Done is received from the server. If the server requests a Client Certificate, the Client Key Exchange will be sent after that.

During this stage, the client will create a pre-master key.

### Pre-Master Secret

The pre-master secret is created by the client (the method of creation depends on the cipher suite that will be used) and then it is shared with the server.

Before sending the pre-master secret to the server, the client encrypts it using the server's public key which was extracted from the certificate provided by the server. This means that only the server can decrypt the message since **asymmetric encryption** is being used for the pre-master secret exchange.

The following is what the key-exchange looks like in a Wireshark capture (using DH):

![key exchange](https://www.acunetix.com/wp-content/uploads/2017/01/image06-1.png)

### Master Secret

After the server receives the pre-master secret key, it uses its private key to decrypt it. Now both client and server will compute the master-secret key based on the random values exchanged earlier (**ClientRandom** and **ServerRandom**) using a Pseudorandom Function (PRF). A PRF is a function used to generate arbitrary amounts of pseudorandom data.
    
    
    master_secret = PRF(pre_master_secret, "master secret", ClientHello.random + ServerHello.random) [0..47];

The master-secret key, which is 48 bytes in length, will then be used by both client and server to symmetrically encrypt the data for the rest of the communication.

Each of the parties (Client and Server), will create 3 sets of keys.

  * client_write_MAC_key - Authentication and Integrity check.
  * server_write_MAC_key - Authentication and Integrity check.
  * client_write_key - Message encryption using a symmetric key.
  * server_write_key - Message encryption using a symmetric key.
  * client_write_IV - Initialization Vector used by some AHEAD ciphers.
  * server_write_IV - Initialization Vector used by some AHEAD ciphers.

Both the Client and the Server will use the master secret to generate the sessions keys which will be able to encrypt/decrypt the data.

## Change Cipher-Spec

![Change Cypher Spec](https://www.acunetix.com/wp-content/uploads/2017/01/image00-3.png)

![Change Cypher Spec](https://www.acunetix.com/wp-content/uploads/2017/01/image30.png)

At this point, both the Client and the Server are ready to switch to a secure, encrypted environment. The Change Cipher Spec protocol is used to change the encryption being used by the client and server. Any data being exchanged between the two parties will now be encrypted with the symmetrical shared key they have.

This is what the Change Cipher Spec looks like in a Wireshark capture:

![ Change Cipher Spec Protocol](https://www.acunetix.com/wp-content/uploads/2017/01/image12.png)

## Finished

The last message of the handshake process and first encrypted one in the secure connection is **Finished**, which is exchanged by both parties.

### Application Data

![Application Data](https://www.acunetix.com/wp-content/uploads/2017/01/image11.png)

> _To recap, the following illustrates a typical handshake._

![Image title](https://www.acunetix.com/wp-content/uploads/2017/01/image34.png)

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.
