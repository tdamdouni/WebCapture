# TLS/SSL Explained: TLS/SSL Certificates, Part 3

_Captured: 2017-05-05 at 23:52 from [dzone.com](https://dzone.com/articles/tlsssl-certificates-part-4)_

In parts 1 and 2 of this series, we looked at _[What is TLS/SSL?](https://dzone.com/articles/tls-security-tlsssl-explained) _and_ [TLS/SSL terminology and basics](https://dzone.com/articles/tlsssl-terminology-and-basics)._ In this, the third part in the series, we will be describing TLS/SSL certificates and their use.

As we have already seen, a secure connection can be used to encrypt data and protect our data from being exposed to third parties.

In order for the encryption to occur, the server needs a TLS/SSL certificate to be used. A TLS/SSL certificate essentially binds an identity to a pair of keys which are then used by the server to encrypt as well as sign the data.

## Certificate Authority (CA)

A Certificate Authority is an entity which issues TLS/SSL or Digital certificates. These authorities have their own certificate for which they use their **private key** to sign the issued TLS/SSL or Digital Certificate. This certificate is known as the Root Certificate.

The CA's Root Certificate, and therefore, **public key**, is installed and** trusted** by default in browsers such as Chrome, Firefox, and Edge. This is necessary to validate that the certificate of a website visited was signed by the CA's private key. Popular CA authorities include Comodo, GlobalSign, DigiCert, GeoTrust, Thawte, and Symantec.

## Types of TLS/SSL Certificates

TLS/SSL Certificates are available in different types, grouped by either Validation Level or Domain setup.

### Single-Domain

This type of certificate is used to secure only one hostname (or Fully Qualified Domain Name FQDN) or subdomain. For example, you may get a certificate for _www.example.com_ or _my.example.com_. In either case, however, _**mail**.example.com_ will not be secured. Nor will any other subdomain. The certificate will only be valid for the hostname you specify during the registration.

### Wildcard

This type of certificate is used to secure an entire domain with all its subdomains. For example, _*.example.com_ is used in the registration which means all _mail.example.com_, _**secret**.example.com_, _**admin**.example.com_ will be secured (as well as any other subdomain). Keep in mind that each domain could be pointed to a different server. The same certificate can be used on multiple servers as long as the domain is the same.

### Multi-Domain

This type of certificate is used to secure several different domain names.

## TLS/SSL Certificate Validation

### Domain Validation

It will only validate that the person who applies for a certificate is the owner of the domain name (or at least has some sort of access to do so). This kind of validation usually takes only a few minutes, but can take up to a few hours.

### Organization Validation

The Certification Authority (CA) not only validates the domain's ownership but also the owner's identity. This means that an owner might be asked to provide personal identification documents which prove their identity. It may take several days for the validation to be completed and the certificate to be issued.

### Extended Validation (EV)

This is the highest level of validation and it includes validation of domain ownership, owner identity, as well as a business's legal registration proof.

## Certificate Generation

For a Certificate Authority to issue a certificate, it first needs to have our server's CSR, which stands for Certificate Signing Request. We first create a private key which will be used to decrypt our certificate and then we generate a CSR.

While generating the CSR, we will be asked to specify the domain name as well as details about our organization like name, country, and email. The following example shows a CSR:

The CSR is then submitted to the CA in order to create our certificate. When the certificate is ready, it will be sent to our email in `*.crt` format and it must then be installed on the server.

![CSR](https://www.acunetix.com/wp-content/uploads/2017/01/image31.png)

### Secure Browsing

Identifying whether a website has a valid certificate and that you are on a secure connection is very easy. All you have to do is look at the status of the URL bar on the top left of our screen (it is similar across all major browsers).

![SSL secure browsing](https://www.acunetix.com/wp-content/uploads/2017/01/image09.png)

The green lock with the https:// protocol indicates that the connection to the web server is encrypted and secure.

### Insecure Browsing

Identifying a non-secure website is just as easy. There is no green lock and there is no mention of HTTPS.

![SSL Insecure browsing](https://www.acunetix.com/wp-content/uploads/2017/01/image18.png)

However, identifying an insecure website which is using HTTPS can be tricky if you are a non-experienced user. The reason is that even though the website is using an SSL/TLS certificate and HTTPS is being used, some parts of the content are delivered via HTTP.

In that case, depending on the browser we will see either of the following:

![SSL/TLS delivered via HTTP](https://www.acunetix.com/wp-content/uploads/2017/01/image19.png)

![connection not secure](https://www.acunetix.com/wp-content/uploads/2017/01/image26.png)

This is what we refer to as Mixed Content. **Mixed content** vulnerabilities defeat the purpose of a secure connection, especially since when requesting files from a website to which we are logged in, the browser will automatically send our authentication cookies along the request.

Therefore, if a resource, such as an image, is loaded using HTTP, our request is sent over HTTP which is un-encrypted; meaning that an attacker sniffing the network will be able to see this request in plaintext. This compromises the security of a "secure" session since an attacker can now use the cookie to login to the website and impersonate a victim.
