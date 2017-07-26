# Linux Kernel Capabilities Explained

_Captured: 2017-07-10 at 19:53 from [dzone.com](https://dzone.com/articles/linux-kernel-capabilities-explained?edition=306243&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-07-10)_

Traditionally, Linux Kernel distinguishes its processes with the following [two categories](https://unix.stackexchange.com/questions/258503/what-happens-when-a-non-root-user-sends-signals-to-root-users-process):

  * Privileged Processes: These processes allow the user to bypass all Kernel permission checks.

  * Unprivileged Processes: These processes are subject to full permission checks, such as the effective UID, GID, and supplementary group list.

Granting full privileged access to a user process might induce system abuse, like unauthorized changes of data, backdoors, changing ACL, etc.

Linux 2.2 shipped with a solution called Capabilities. Capabilities allows the developer to grant binaries/files specific permissions.

### **Example**

Let's say we want to start a Simple HTTP Server module of Python on port 80 with a non-privileged user. If we try to start the process without granting any capabilities, we will get the following error:

Let's add the `CAP_NET_BIND_SERVICE` capability to our Python binary.

The above command states that we are adding the `CAP_NET_BIND_SERVICE ` capability to our `/usr/bin/python2.7` file. `+ep` indicates that the file is Effective and Permitted ( `"-" ` would remove it).

Now let's try to run the Python Simple HTTP Server module again on port 80:

We are now able to serve traffic over privileged port 80 with a non-privileged user.

At the time of writing this article, there are over 40 capabilities which can be assigned per requirement.

There are 3 modes for [Capabilities](https://www.insecure.ws/linux/getcap_setcap.html):

  * ** e: Effective -** This indicates that the capability is "activated."

  * **p: Permitted -** This indicates that the capability can be used.

  * **i: Inherited -** This indicates that the capability is inherited by child elements/subprocesses.

Capabilities provide a concise and efficient way to assign privileged permissions to non-privileged users.
