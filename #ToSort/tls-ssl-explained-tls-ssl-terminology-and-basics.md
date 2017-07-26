# TLS/SSL Explained: TLS/SSL Terminology and Basics

_Captured: 2017-05-05 at 23:50 from [dzone.com](https://dzone.com/articles/tlsssl-terminology-and-basics?utm_source=Top%205&utm_medium=email&utm_campaign=top5%202017-05-05)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

In Part 1 this series we asked, _[What is TLS/SSL?](https://dzone.com/articles/tls-security-tlsssl-explained)_ In this part in the series, we will be describing some of the TLS/SSL terminologies.

Before diving deeper into TLS, let's first have a look at the very basics of SSL/TLS. Understanding the following will help you gain a better understanding of the topics discussed and analyzed later on.

## Encryption

Encryption is the process in which a human-readable message (plaintext) is converted into an encrypted, non-human-readable, format (ciphertext). The main purpose of encryption is to ensure that only an authorized receiver will be able to decrypt and read the original message. When unencrypted data is exchanged between two parties, using any medium, a third-party can intercept and read the communication exchanged.

If the exchange contains sensitive information, that implies a loss of **confidentiality**. Furthermore, if the third-party can intercept and read the messages, they might as well tamper with the data which means they can change the information being exchanged thus compromising the **integrity** of the message.

Imagine sending a payment over an unencrypted channel. The payment includes your bank account details as well as the amount that you authorized. An attacker could use a man-in-the-middle attack to tamper the information and change the amount from $100 to $10,000. The bank receives the tampered data from the third-party instead of you which means that there is no **authenticity**. By using encryption, an attacker might still be able to intercept the traffic but they will not be able to read or tamper the data.

![TLS SSL 1](https://www.acunetix.com/wp-content/uploads/2017/01/image21.png)

## Symmetric Encryption

Symmetric encryption is the process in which the same key is used for encrypting and decrypting data.

If Thomas wants to send information to Bob, he will use a shared key to encrypt the data and Bob will decrypt the data using the same key.

![Symetric encryption](https://www.acunetix.com/wp-content/uploads/2017/01/image27.png)

The biggest problem with symmetric key encryption is that the data exchanged must be encrypted and decrypted with the same key. That means that all of the parties exchanging data must have the shared key.

The major drawback in this is that if the shared key is exposed, an attacker would be able to decrypt all the communication encrypted with that key. That is why the shared key distribution between the parties must be done over an **already established** secure encrypted communication channel. Another disadvantage is that you cannot authenticate the sender of a message, which compromises authenticity.

#### **Advantages of Symmetric Encryption**

  * Fast, low resource usage.
  * Simple operation.
  * Secure.

#### **Disadvantages **of Symmetric Encryption****

  * Same key used for encryption/decryption.
  * Key distribution must be done over an already established, secure channel.
  * A different key is needed for different parties - key management/distribution.
  * Cannot authenticate users.

## Asymmetric Encryption

Unlike symmetric key encryption, asymmetric encryption (also referred to as Public Key Cryptography) uses a pair of keys, a **public key**, and a **private key**. These cryptographic keys are uniquely related which means that whatever is encrypted with one key, can be decrypted with the other. The public key, as the name implies, can be shared with anyone. The **private key must be known only to the server**.

![asymetric encryption](https://www.acunetix.com/wp-content/uploads/2017/01/image01-1.png)

Asymmetric encryption can be used for authentication of the sender. If Bob signs and encrypts a message using his private key, whoever decrypts it with Bob's public key can be sure that Bob is the sender.

**This is why keeping a private key secure is critical.**

#### **Advantages of Asymmetric Encryption**

  * Key distribution is easy.
  * Authenticity.
  * Integrity.
  * Secure.

#### **Disadvantages **of Asymmetric Encryption****

  * Slower than symmetric encryption.
  * Needs more resources.

## Ciphers

Ciphers are methods/algorithms used to encrypt and decrypt data.

### Block Ciphers

In this method, data is split into fixed-length blocks and then encrypted (e.g. 64-bit or 128-bit blocks). If the last block of the data is less than the specified block length, padding will be used to fill the "empty" space. Popular Block Ciphers include **AES, Blowfish, 3DES, DES,** and **RC5**.

### Padding

Block ciphers have a specified fixed length and most of them require that the input data is a multiple of their size. It is common that the last block contains data that does not meet this requirement. In this case, padding (usually random data) is used to bring it to the required block length.

### Initialization Vector (IV)

An Initialization Vector is a random (or pseudorandom) fixed-size input used in encryption methods. If this input is not repetitive on each message, then, it is also called as a nonce, which means that it can only be used once.

The main purpose of an IV is to start off an encryption method. In Cipher Modes, like Cipher Block Chaining (CBC), where each block is XORed with the previous block, in the first block there is no previous block to XOR with, so an Initialization Vector is used as an input to the first block to start off the process.

A nonce is also used to prevent attackers from decrypting all messages by guessing the IV. A nonce, which should be random and unpredictable, allows the same message to be encrypted with the same key and yet have a different result (ciphertext).

### XOR (Exclusive Or)

XOR is an easy to implement logical function which is used in cryptography (among its many other uses). XOR takes two-bit patterns and it returns true only if the two inputs are **different**.

Input 1 Input 2 OUTPUT

0
0
0

1
0
1

0
1
1

1
1
0

The following is an example of an XOR **encrypt** operation.

Message
Hello!
01001000 01000101 01001100 01001100 01001111 00100001

Key
S3CR3T
01010011 00110011 01000011 01010010 00110011 01010100

Ciphertext
00011011 01110110 00001111 00011110 01111100 01110101

The following is an example of an XOR **decrypt** operation.

Ciphertext
00011011 01110110 00001111 00011110 01111100 01110101

Key
S3CR3T
01010011 00110011 01000011 01010010 00110011 01010100

Message
Hello!
01001000 01000101 01001100 01001100 01001111 00100001

### Block Cipher Algorithms

#### **Electronic Code Book (ECB)**

Each block of data is encrypted separately and concatenated at the end. A major drawback of ECB is that if the same block of data is encrypted, it will always generate the same ciphertext. Parallel processing is possible since blocks do not depend on one another.

![Electronic Code Book \(ECB\)](https://www.acunetix.com/wp-content/uploads/2017/01/image28.png)

#### **Cipher Block Chaining (CBC)**

Each block is XORed with the previous ciphertext before encryption. An Initialization Vector is needed for the first plaintext block encryption to happen. Parallel processing is not possible since the blocks are chained.

![Cipher Block Chaining \(CBC\)](https://www.acunetix.com/wp-content/uploads/2017/01/image20.png)

#### **Cipher Feedback (CFB)**

Turns a block cipher into stream cipher by selecting a number of bits to XOR on each iteration.

![Cipher Feedback \(CFB\)](https://www.acunetix.com/wp-content/uploads/2017/01/image13.png)

#### **Output Feedback (OFB)**

Similar to CFB, but instead of the result of XOR, the result of crypto goes to the next iteration.

![Output feedback](https://www.acunetix.com/wp-content/uploads/2017/01/image05-1.png)

#### **Counter Mode (CTR)**

Each block has a nonce and an iteration counter which is first encrypted and then XORed with a plaintext block. Then the nonce changes and the counter increments on each iteration.

![Counter Mode \(CTR\)](https://www.acunetix.com/wp-content/uploads/2017/01/image33.png)

### Stream Ciphers

Stream ciphers are ciphers that use a method of encryption that encrypts data one bit or byte at a time. Each bit is encrypted with a different key. While stream ciphers are not used much in modern cryptography, a popular example of a stream cipher is the **RC4** cipher.

### Message Authentication Code (MAC)

Message Authentication Code (or Cryptographic Checksum) is a method which is used to check the authenticity as well as the integrity of a message. It accepts two input parameters, a secret key and a message of arbitrary length, and the result is called a **tag**.

![Message Authentication Code \(MAC\)](https://www.acunetix.com/wp-content/uploads/2017/01/image03-1.png)

If the MAC tag of the sender and the calculated MAC tag of the receiver match, that means that the message has **not** been tampered with. If they** do not** match that means that the message has been altered during the transmission.

### Hash-Based Message Authentication Code (HMAC)

HMAC is a type of MAC which uses a hash function. It accepts two input parameters, a secret key, and a message of arbitrary length.

The following is an example of HMAC function using the SHA256 hash algorithm.

The following illustration shows how the HMAC function works.

![Image title](https://www.acunetix.com/wp-content/uploads/2017/01/image17.png)

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.
