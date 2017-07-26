# Storing Secrets in Linux

_Captured: 2017-05-10 at 00:41 from [dzone.com](https://dzone.com/articles/storing-secrets-in-linux?edition=298034&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-09)_

Discover how to [protect your applications](https://dzone.com/go?i=176121&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fzero-day-defense%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dprerolltextad%26utm_content%3Dzeroday) from known and unknown vulnerabilities.

We need to store an encryption key on Linux and Windows. On Windows, the decision is pretty much trivial, you throw that into [DPAPI](https://msdn.microsoft.com/en-us/library/ms229741\(v=vs.110\).aspx), and can rely on the operating system to handle that for us. In particular, it is very easy to analyze key scenarios such as "someone stole the hard disk" and say that either the thief wouldn't be able to get the plain text key, or we can blame Microsoft for that.

On Linux, the situation seems to be much more chaotic. There is [libsecret](https://lwn.net/Articles/490518/), which seems to be much wider in scope than DPAPI. Whereas DPAPI has 2 methods (protect and unprotect), libsecret has a _[lot of moving pieces](https://people.gnome.org/~stefw/libsecret-docs/libsecret-Password-storage.html), _which is quite scary. That is leaving aside the issue of having no managed implementation and having to dance around Gnome specific data types in the API (need to pass GCancellable and GError into it) which increase the complexity.

Other options include using some sort of hardware/software security modules (such as [HashiCorp Vault](https://www.vaultproject.io/)), which is great in theory, but requires us to either take a dependency on something that might not be there, or try to support a wide variety of options (Keywhiz, Chef, Puppet, CloudHSM, etc). That isn't a really good alternative from our point of view.

Looking into how Mono implemented the DPAPI on Linux, they did it by writing a master key to an XML file and relied on file system ACLs to prevent anyone from seeing that information. This end up being this:

> chmod(path, (S_IRUSR | S_IWUSR | S_IXUSR) );

Which has the benefit of only allowing that user to access it, but given that I've gotten the physical disk, I'm able to easily mount that on the machine that I control as root and access anything that I like. On Windows, by the way, the way this is prevented is that the user must have logged in, and a key that is derived from their password is used to decrypt all protected data as needed, so without the user logging in, you cannot decrypt anything. For that matter, even the administrator on the machine can't recover the data if they want to, because resetting the user's password will cause all such information to be lost.

There is the [Gnome.Keyring](https://github.com/mono/gnome-keyring-sharp) project as well, which hasn't been updated in 7 years, and obviously doesn't support the kwallet (which libsecret does). [OWASP](https://www.owasp.org/index.php/Securing_tomcat#Cleartext_Passwords_in_CATALINA_HOME.2Fconf.2Fserver.xml) seems to be throwing in the towel there and just recommend that you rely on the file system ACL.

The Linux Kernel [has a Key Retention API](https://lwn.net/Articles/210502/), but it seems to be targeted primarily toward giving file systems access to the secrets they need, and it looks like it isn't going to survive reboots (it is primarily a caching mechanism, it looks like?).

So after all this research, I can say that I don't _like_ libsecret, it seems too cumbersome and will need users to jump through some hoops in some cases (install additional packages, setup access, etc).

Setting up the permissions via the ACL seems to be the common way to handle this scenario, but it doesn't sit well with me.

Any recommendations?

Find out how [Waratek's](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect) award-winning virtualization platform can [improve your web application security](https://dzone.com/go?i=176122&u=http%3A%2F%2Fwww.waratek.com%2Fsolutions%2Fapplication-protection%2F%3Futm_source%3DDZone%26utm_campaign%3Dba%26utm_medium%3Dpostrolltextad%26utm_content%3Dappprotect), development and operations without false positives, code changes or slowing your application.
