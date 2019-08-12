# Security Through Blockchain

_Captured: 2018-09-20 at 09:22 from [dzone.com](https://dzone.com/articles/security-through-blockchain?edition=399199&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-09-19)_

Discover how to provide [active runtime protection](https://dzone.com/go?i=255346&u=https%3A%2F%2Fwww.waratek.com%2Fruntime-application-self-protection-rasp%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Drasp) for your web applications from [known and unknown vulnerabilities](https://dzone.com/go?i=255346&u=https%3A%2F%2Fwww.waratek.com%2Fruntime-application-self-protection-rasp%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Drasp) including Remote Code Execution Attacks.

_This article is featured in the new [DZone Guide to Security: Defending Your Code](https://dzone.com/guides/security-defending-your-code). Get your free copy for more insightful articles, industry statistics, and more!_

Since its inception in 2008 by Satoshi Nakamoto, blockchain technology has spread across the globe at an astonishing pace and is positioned to be one of the greatest technological advancements in decades. From cashless digital currencies to food supply chains, blockchains are helping to radically change the way the world thinks and operates. Foremost among its benefits is the intrinsic security forged in its openness, immutability, and distributed topology, which places trust in a network of participants rather than a central authority.

Amid the whirlwind of excitement and flourishing of blockchain-based cryptocurrencies, such as Bitcoin, a great deal of conflation and misconception has arisen about what blockchain technology is and how it can be used to solve practical problems. In order to understand how it can be useful for securing applications -- and how so many people and companies have placed their trust in this emerging technology -- it is essential to take a detailed look at the embedded security of blockchains and how they are used in practice, beginning with what constitutes a blockchain

## What Is a Blockchain?

Blockchain technology often gets confused with its specific implementations (such as Bitcoin) but there are certain concepts all blockchains share apart from cryptocurrencies. The name blockchain is derived from the data structure that sits at the heart of this technology, consisting of an arbitrary number of blocks cryptographically chained together. A block is composed of three principal parts: (1) data, (2) a cryptographic hash of the previous block, and (3) a cryptographic hash of both the data and the hash of the previous block. Doing so not only creates an ordered dependency between subsequent blocks but it also institutes a data dependency between blocks.

![Image title](https://dzone.com/storage/temp/10248655-screen-shot-2018-09-17-at-11930-pm.png)

If the data contained in any block is changed, the corresponding hash of that block will change, which in turn invalidates the hashes of the subsequent blocks in the chain that depend on it. For example, if the data in block i is changed, the hash of block i will need to be updated, as well. Updating the hash of i results in in a change to the hash of block i + 1 (since the hash of i is an input to the hash of i + 1), which in turn results in a change to the hash of i + 2, and so on.

![Image title](https://dzone.com/storage/temp/10248656-screen-shot-2018-09-17-at-12124-pm.png)

If a node wishes to add a new block to the chain, it must broadcast the new block to all of the other nodes in the network -- creating an open network where any node can see the entirety of the blockchain at any given time. Using a predetermined consensus protocol, each of the nodes either accepts or rejects the new block. If the new block is accepted, it is added to the front of the chain of each node. Given enough time, all of the nodes in the network will reach consensus, having a copy of the same chain as all of the other nodes in the network.

Generally, the protocol is based on the acceptance of the longest chain in the network and therefore, for a bad actor to change an existing block, it must recompute the hash for the changed block and all subsequent blocks and submit it to the network. Using a Proof of Work (PoW) or Proof of Stake (PoS)scheme, this becomes exponentially more difficult the further into the chain a block is altered. For example, in Bitcoin, gaining a controlling stake in the network requires an infeasible level of computing power.

This combination of fixed blocks and network consensus differs from existing technology in a few fundamental ways: It is open, immutable, and does not rely on a central authority. At any given time, any node can verify for itself the integrity of the data in the chain. The distributed nature of the consensus mechanism, combined with verifiability, ensures that no single node (or the plurality of nodes) can feasibly dictate to other nodes the correct state of the chain. Although security is built into the core of blockchain technology, a blockchain, and its associated network are only as secure as the underlying technologies used.

> This combination of fixed blocks and network consensus differs from existing technology in a few fundamental ways: It is open, immutable, and does not rely on a central authority. 

## Is a Blockchain Secure?

The security of blockchain technology hinges on a few crucial assumptions. The data structure of a blockchain is secure so long as the cryptographic hashing algorithm used for chaining blocks is sufficiently secure. In many cases, the Secure Hash Algorithm(SHA) 256 is used, which is accepted by nearly all institutions, including the National Security Agency (NSA).

A more challenging criterion is the security of a blockchain network, which consists of nodes which cannot be trusted outright. In order to provide a sufficient level of security in a blockchain network, a consensus protocol must be devised such that it is statistically infeasible to gain a controlling stake in the network. The specifics will vary by application but as we will see shortly, the protocols devised for practical blockchain applications are secure enough for major financial institutions and companies to place their trust in them.

## What Do Blockchains Look Like in Practice?

While blockchain technology is theoretically secure, there is no greater testament to the security of blockchains than their widespread use in critical applications and the trust they have earned by some of the largest financial institutions, originating with cryptocurrencies.

### Bitcoin and Cryptocurrency

In terms of both scale and notoriety, Bitcoin is the most recognizable blockchain system, with over 22 million Bitcoin wallets created as of July 2018 and nearly 210 million transactions per day at the time of writing. Bitcoin and other cryptocurrencies take the concept of a blockchain and propel it to an entirely different level of practicality*, allowing users to electronically transfer money without any trusted third party, such as a bank or financial clearinghouse).

This technological leap is made possible through the use of more sophisticated cryptographic tools, such as asymmetric encryption and digital signatures. Instead of storing arbitrary data in each block, the Bitcoin blockchain stores transactions, which are digitally signed by their originators and thus reflect the authenticity of the transaction. This stringency is made in an effort to thwart the possibility of a bad actor double-spending his or her coins.

With cryptocurrencies, the consensus protocol involves a node proving to the rest of the network it has a sufficient stake in the network (i.e. PoS) or that it has performed a sufficient level of work (i.e. PoW) to submit a new node to the blockchain. In order to solve the double-spend problem while quickly accepting transactions, a balance must be struck between the time required for a transaction to be considered valid and the burden that is placed on an attacker to succeed in fraudulently spending his or her money.

With the creation of innovative companies such as Bakkt (created by the Intercontinental Exchange, ICE, the owner of theNew York Stock Exchange -- in partnership with Microsoft and Starbucks), many of the largest financial institutions in the world are starting to solidify their trust not only in cryptocurrencies like Bitcoin but also in the integrity of the blockchain technology that underpins them.

### Smart Contracts

A second breakthrough thanks to blockchain technology (first conceived in 1994) is the smart contract. A smart contract is a cryptographically signed an agreement between an arbitrary number of parties. This contract is then publically submitted as a block in a blockchain network, ensuring that all of the nodes recognize the validity and obligation of the parties involved. Some contracts may involve the exchange of payment for some good or service, while others may require the forfeiture of assets if the contract is breached.

Numerous cryptocurrencies, including Bitcoin and Ethereum, allow users to embed contracts within a transaction. This enables a user to release funds when an objective, the codified condition is satisfied. Improvements, such as the Bitcoin Lightning Network, utilize these underlying smart contracts to great advantage. Regardless of the specific criteria, smart contracts are starting to change the legal landscape in many countries around the world and at its current pace, will likely drastically change the way we deal with binding contracts in the future.

## Food Supply Chain

Along with financial and legal breakthroughs, blockchains are helping to improve the way we bring food from the farm to the market. IBM -- partnered with Walmart, Dole, Nestle, and a host of other major food companies -- have created a permissioned blockchain (data is shared only to those entities given permission by the chain owner) called IBM Food Trust to help trace the origin and state of food from the farm to the shelf.

Although this product is in its infancy, its acceptance has been accelerated by the support of many of the largest growers, suppliers, and regulators in the United States. While there are many secure alternatives to blockchain currently available, these major partners have placed enough trust in blockchain technology to trace the complex journey of our daily food products. It will be interesting to watch how similar permissioned blockchains can enable security while still maintaining control over sensitive data.

## Conclusion

Blockchain technology is poised on becoming one of the most creatively disruptive inventions in recent decades and its combination of openness, immutability, and distributed network makes it a very promising technology for securing a host of applications. Regardless of the application, blockchain has cemented its place in the world of software security and can enable countless advancements, some of which have not been fully conceived.

_This article is featured in the new [DZone Guide to Security: Defending Your Code](https://dzone.com/guides/security-defending-your-code). Get your free copy for more insightful articles, industry statistics, and more!_

Find out how Waratek's award-winning [application security platform](https://dzone.com/go?i=255347&u=https%3A%2F%2Fwww.waratek.com%2Fapplication-security-platform%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappsecplatform) can improve the security of your [new and legacy applications and platforms](https://dzone.com/go?i=255347&u=https%3A%2F%2Fwww.waratek.com%2Fsolutions%2Flegacy-platforms%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dlegacy) with no false positives, code changes or slowing your application.
