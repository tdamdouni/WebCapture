# What Is Path Traversal?

_Captured: 2017-12-19 at 04:47 from [dzone.com](https://dzone.com/articles/what-is-path-traversal?edition=345100&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-18)_

Discover how to provide [active runtime protection](https://dzone.com/go?i=255346&u=https%3A%2F%2Fwww.waratek.com%2Fruntime-application-self-protection-rasp%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Drasp) for your web applications from [known and unknown vulnerabilities](https://dzone.com/go?i=255346&u=https%3A%2F%2Fwww.waratek.com%2Fruntime-application-self-protection-rasp%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Drasp) including Remote Code Execution Attacks.

Path Traversal, or, as it is otherwise known, [Directory Traversal](https://www.acunetix.com/websitesecurity/directory-traversal/), refers to an attack through which an attacker may trick a web application into reading and subsequently divulging the contents of files outside of the root directory of the application, or the web server. Path Traversal attacks typically manipulate web application inputs by using the dot-dot-slash (../) sequences, or similar variations. `../` is a cross-platform convention to 'go up' (traverse) a directory (folder).

Typically, Path Traversal attacks are used in order to gain access to sensitive information stored within files either within other areas of a web application, as well as other parts of the filesystem which the web server can read. Since files containing sensitive information may contain secrets such as passwords, access tokens or backups, a successful Path Traversal attack may allow an attacker to take their reconnaissance further, or exploit other vulnerabilities within the web application.

**Note -** While Path Traversal may seem similar to Local File Inclusion (LFI) and Remote File Inclusion (RFI), Path Traversal only allows an attacker to **read** a file, while LFI and RFI may also allow an attacker to execute code.

The following is an example in PHP that is vulnerable to Path Traversal.

In the above example, an attacker could make the following request to trick the application into divulging the contents of the `/etc/passwd` system file.

In the above example, an attacker could have used Path Traversal to obtain the contents of the `/etc/passwd` file, which contains a list of users on the server. Similarly, an attacker may leverage the Path Traversal vulnerability to gain access to credentials, logs, and other sensitive information that may help advance an attack.

Path Traversal is certainly not limited to accessing the `/etc/passwd` file. Since 'everything' in Linux-based systems is a file, an attacker can gain a wealth of information about a vulnerable application just by reading the right files on a system. The following are just a couple of examples of how Path Traversal can be used to glean information about the system the vulnerable application is running on.

The `/proc/version` file contains the version of the Linux kernel running on the system. This information can be used by an attacker to determine the operating system version and determine if any security updated could be missing.

The `/proc/mounts` file provides a list of file systems which are mounted and can be used by an attacker to learn where potentially interesting and sensitive files may be located.

The `/proc/net/arp` file lists the system's Address Resolution Protocol (ARP) table which could provide a very easy way for an attacker to discover other internal, connected systems.

The `/proc/net/tcp` and `/proc/net/udp` files can provide an attacker with a list of active connections. This information can be used to determine what ports are listening on the server, and, therefore, what services the server is likely running.

## Preventing Path Traversal Vulnerabilities

The best way to eliminate Path Traversal vulnerabilities is to avoid dynamically reading files based on user input. If this is not possible, the application should maintain a whitelist of files that can be included in order to limit the attacker's control over what gets included.

Find out how Waratek's award-winning [application security platform](https://dzone.com/go?i=255347&u=https%3A%2F%2Fwww.waratek.com%2Fapplication-security-platform%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappsecplatform) can improve the security of your [new and legacy applications and platforms](https://dzone.com/go?i=255347&u=https%3A%2F%2Fwww.waratek.com%2Fsolutions%2Flegacy-platforms%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dlegacy) with no false positives, code changes or slowing your application.
