# Avoid Using Same SSH Private Key For All Your Servers

_Captured: 2017-04-18 at 19:48 from [dzone.com](https://dzone.com/articles/avoid-using-same-ssh-private-key-for-all-your-serv?edition=293881&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-18)_

The more projects you handle, the more servers you manage. But when you use SSH to servers of different projects, are you using **the same private key**?

**And how secure do you feel about this?** Let's imagine. One day, your powerful private key gets compromised somehow. Boom! All your servers and all your projects are in danger.

Check out this post, and get improved security for all your projects, in just five minutes!

![Avoid Using Same SSH Private Key For All Your Servers](http://www.dennyzhang.com/wp-content/uploads/denny/ssh_private_key.png)

## **Step 1: Generate Different SSH Key Pairs For Different Projects**

Using ssh-keygen, we can easily generate as many SSH key pairs as we need. Let's say we already have two key pairs for two projects: project1_id_rsa and project2_id_rsa.

## **Step 2: Use Different Private Keys Selectively but in an Easy Way!**

**Version 1.0:** We need to manually specify a private key when we send an SSH to different servers.

It works, but typing those extra characters thousands of times is not fun. And it's pointless.

**Version 2.0:** Create an alias in ~/.ssh/config, then use SSH with that alias.

Using SSH with an alias is quite easy and straightforward. Here's how to do it:

So are we good now? Hang on, my friend. Not yet.

Let's say you have tens of, or hundreds of, servers. You don't want to configure them one by one, right?

**Version 3.0: **Update ~/.ssh/config to load all SSH private keys.

Now you can use SSH like you normally would: "ssh user1@server1".

**SSH will try to use all your private keys one by one**. To confirm this, use SSH with the -vvv option.

You can argue it will waste some time on the retry. Yes, it does. But it's fast enough to get the job done before we can even notice the difference.

And SSH tries the keys from top to bottom. So, if we put frequently used keys at the top it will speed things up a little bit.

## **Step 3: [Optional] Secure Your SSH Private Key With Passphrase**

To make it better, add passphrase protection for your SSH private keys. Check this article on the topic: [Manage SSH Key File With Passphrase](https://dzone.com/articles/manage-ssh-key-file-with-passphrase).

So now, go have a try at using SSH with the tips shared in this post!

Please leave me comments, if you have any questions or feedback.

And don't forget to share this post, if you find it might be useful for your friends or colleagues.
