# Building Secure Systems Checklist

_Captured: 2017-03-16 at 21:24 from [dzone.com](https://dzone.com/articles/building-secure-systems-checklist?edition=283884&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-16)_

Building secure systems is not an easy task. It is a complex problem, that requires software developers to think as hackers and look at the system as a whole, not just review their own code and call it a day.

Here are some of the lessons we have learned while building our Password Manager - [Keepassa](https://keepassa.co/). I will try to keep this blog post platform agonistic as much as possible.

## Guidelines to Build Secure Systems

  1. **Use Encryption **\- Encrypt sensitive data with industry-leading algorithms. You can use AES, Serpent, or Two-Fish. It's best to combine two algorithms, to be sure that recent progress in quantitive computing will not compromise your data.
  2. **Encrypt Your Encryption Keys** \- All the algorithms mentioned above use a key (a random byte sequence) to actually encrypt your data. If the keys get out you are screwed. So encrypt the encryption keys using Public/Private keys, or PGP (Asymmetric Encryption Algorithms). The main idea here is to encrypt the data with your public key and decrypt it with your private key, which you have to secure. Asymmetric encryption's performance is not great so use it only to encrypt your symmetric keys.
  3. **Secure Your Private Keys** \- Don't leave your private keys unencrypted on your computer. It's best to use an HSM device, but that is not always practical. You can use an encrypted flash drive, or an encrypted file, or a specialized database like Java Keystore; but always encrypt your private keys storage.
  4. **Use Full-Disk Encryption **\- Using full-disk encryption protects you from the possibility that someone will physically steal your server.
  5. **Use a Strong Hash Function** when hashing sensitive data like passwords. SHA1 is [compromised](https://security.googleblog.com/2017/02/announcing-first-sha1-collision.html). It's best to use SHA-384 or SHA-512.
  6. **Double Hash Your Sensitive Data** \- For example, use SHA512(SHA384(my_password)). By using such an approach, you can protect your app from rainbow attacks, and use the second hashing function as a salt generator.
  7. **Use Only Open-Source Libraries and Compilers** to build your software. By using popular open-source software that is peer-reviewed you can be sure that security issues will be promptly addressed.
  8. **Use a Separate Build Server **that is not connected to the Internet. Don't release software, that is built on the developer machine. By using a separate build machine you can guarantee that your toolchain is not compromised. As software is built using a variety of tools, linkers, and compilers, it is extremely important that those tools are secured and trusted. Ken Thompson, has an excellent article on the subject of [trusting trust](https://www.ece.cmu.edu/~ganger/712.fall02/papers/p761-thompson.pdf).
  9. **Secure Your Network Communications **\- With free services like [Let's Encrypt](https://letsencrypt.org/), it's pure laziness not to use TLS for critical applications.
  10. **Configure Your Application to Offer Encryption Ciphers **in a specific order. As not all ciphers are created equal, the SSL negotiation process tries them in a specific order. You can control this order while configuring your server. Here is a Jetty example:

For common servers, you can check Mozilla's [SSL Config Generator](https://mozilla.github.io/server-side-tls/ssl-config-generator/). You can test your SSL setup for weaknesses by using SSL Test Labs [app](https://www.ssllabs.com/ssltest/).

Check out Part 2 of this post for additional info on how to build secure systems.
