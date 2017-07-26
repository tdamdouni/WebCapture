# discovering how Dropbox hacks your mac

_Captured: 2016-11-07 at 10:28 from [applehelpwriter.com](http://applehelpwriter.com/2016/08/29/discovering-how-dropbox-hacks-your-mac/)_

![Screen Shot 2016-08-26 at 23.05.27](https://applehelpwriter.files.wordpress.com/2016/08/screen-shot-2016-08-26-at-23-05-27.png?w=604&h=420)

> _Update: Dropbox hack blocked by Apple in Sierra_

**Following my post **[revealing Dropbox's Dirty Little Security Hack](http://applehelpwriter.com/2016/07/28/revealing-dropboxs-dirty-little-security-hack/) a few weeks ago, I thought I'd look deeper into how Dropbox was getting around Apple's security.

After a little digging around in Apple's vast documentation, it occurred to me to check the authorization database and see if that had been tampered with. According to [the docs](https://developer.apple.com/library/mac/documentation/Security/Conceptual/authorization_concepts/02authconcepts/authconcepts.html):

> In a policy-based system, a user requests authorization--the act of granting a right or privilege--to perform a privileged operation. Authorization is performed through an agent so the user doesn't have to trust the application with a password. The agent is the user interface-- operating on behalf of the Security Server--used to obtain the user's password or other form of identification, which also ensures consistency between applications. The Security Server--a Core Services daemon in OS X that deals with authorization and authentication--determines whether no one, everyone, or only certain users may perform a privileged operation.

The list of authorization "rights" used by the system to manage this "policy based system" is held in `/var/db/auth.db` database, and a backup or default copy is retained in /System/Library/Security/authorization.plist.

Looking at the default with

`defaults read /System/Library/Security/authorization.plist `

we can find that there is an authorization right for System Preferences' Accessibility list, which says:

> ` "system.preferences.accessibility" = {  
class = user;  
comment = "Checked when making changes to the Accessibility Preferences.";  
group = admin;  
shared = 0;  
timeout = 0;  
`

That file's comments also state that "The `allow-root` property specifies whether a right should be allowed automatically if the requesting process is running with uid == 0. This defaults to false if not specified."

In other words, if allow-root isn't explicitly set, the default is that even a process with root user privileges does not have the right to perform that operation. Since that's not specified in the default shown above, then even root couldn't add Dropbox to the list of apps in Accessibility preferences. Is it possible then, that Dropbox had overriden this setting in the auth.db? Let's go and check!

To see what the current policies are, you have to actually read the sql database in /var/db/auth.db. There's various ways of doing that, but the easiest for me was to access auth.db through the command line using the security tool. Issuing the following command in Terminal will return us the currently active policy for Accessibility:

`security authorization read system.preferences.accessibility`

On my machine, this returned:

![Screen Shot 2016-08-26 at 20.57.12](https://applehelpwriter.files.wordpress.com/2016/08/screen-shot-2016-08-26-at-20-57-12.png?w=300&h=135)

Root wasn't allowed to override Accessibility, and authenticate was on, so it couldn't be this way that Dropbox was hacking my mac.

Security on OS X is a complex beast, however, and there are other authorization protocols at work. One that I already knew of is tccutil. If you issue `man tccutil` in Terminal, you'll see this:

> tccutil(1) BSD General Commands Manual tccutil(1)
> 
> NAME  
tccutil -- manage the privacy database
> 
> SYNOPSIS  
tccutil command service
> 
> DESCRIPTION  
The tccutil command manages the privacy database, which stores decisions the user has made about  
whether apps may access personal data.
> 
> One command is current supported:
> 
> reset Reset all decisions for the specified service, causing apps to prompt again the next time  
they access the service.
> 
> EXAMPLES  
To reset all decisions about whether apps may access the address book:
> 
> tccutil reset AddressBook
> 
> Darwin April 3, 2012 Darwin  
(END)

I had heard of a hack of this utility that was related directly to adding apps to Accessibility list over a year ago when I stumbled across this [stackexchange page](http://apple.stackexchange.com/questions/111903/allow-application-to-control-computer-assistive-devices-on-mavericks-via-termi). In short, what that hack suggests is that you modify `tcc` directly by inserting an entry into the sql database located here `/Library/Application Support/com.apple.TCC/TCC.db`.

You can read the current list with the command:

`sudo sqlite3 /Library/Application\ Support/com.apple.TCC/TCC.db 'select * from access'`.

To insert an app in the list, you grab it's bundle identifier (in the case of Dropbox, that's com.getdropbox.dropbox), and issue:

sudo sqlite3 /Library/Application\ Support/com.apple.TCC/TCC.db "REPLACE INTO access VALUES('kTCCServiceAccessibility','com.getdropbox.dropbox',0,1,1,NULL, NULL);"

(*note the code given on the stackexchange page isn't quite correct for the latest builds of the mac operating system, in which the access table now has 7 columns and so requires and extra "NULL" on the end as shown above).

I tested this with several of my own apps and found it worked reliably. It'll even work while System Preferences is open, which is exactly [the behaviour I saw with Dropbox](https://www.youtube.com/watch?v=9ZOrDPC8mfw).

It remained to prove, though, that this was indeed the hack that Dropbox was using, and so I started to look at what exactly Dropbox did after being given an admin password on installation or launch. Using [DetectX](http://sqwarq.com/detectx), I was able to see that Dropbox added a new folder to my /Library folder after the password was entered:

![Screen Shot 2016-08-26 at 21.36.35](https://applehelpwriter.files.wordpress.com/2016/08/screen-shot-2016-08-26-at-21-36-35.png?w=300&h=195)

![Screen Shot 2016-08-26 at 21.37.09](https://applehelpwriter.files.wordpress.com/2016/08/screen-shot-2016-08-26-at-21-37-09.png?w=300&h=213)

As can be seen, instead of adding something to the PrivilegedHelperTools folder as is standard behaviour for apps on the mac that need elevated privileges for one or two specialist operations, Dropbox installs its own folder containing these interesting items:

![Screen Shot 2016-08-26 at 21.40.45](https://applehelpwriter.files.wordpress.com/2016/08/screen-shot-2016-08-26-at-21-40-45.png?w=300&h=193)

Not one, but three binaries! I wonder what they do? The first thing I did on each was to run the `strings` command on them. I still haven't determined what that 1.5MB _DropboxHelperInstaller_ binary is doing (that's pretty big for a binary for a helper app), but its jam-packed with strings relating to file compression and encryption. The string output for _dbfseventsd_ binary didn't reveal anything much interesting, but with the deliciously named _dbaccessperm_ file, we finally hit gold and the exact proof I was looking for that Dropbox was using a sql attack on the tcc database to circumvent Apple's authorization policy:

This is all the more telling when we look at what Dropbox themselves say when queried about why their app is in the list of Accessibility apps [here](https://www.dropboxforum.com/hc/en-us/community/posts/204505875-MacOS-X-Security-Is-it-normal-to-allow-Dropbox-app-to-control-your-computer-). After a great deal of obfuscation, misdirection and irrelevance in which they mention everything about permissions in general and nothing about Accessibility in particular, or that they're hacking their way into the user's Accessibility list rather than going through the supported channel of presenting the user with a dialog box and asking for permission, comes this line:

> we need to request all the permissions we need or** even may need in the future**.  
(my emphasis)

Ostensibly, that's in the context of Drobpox on mobile apps, but since the question isn't related to mobile apps at all, I think interpreting anything said there as being honest is naive at best. What I do suspect, especially in light of the fact that there just doesn't seem to be any need for Dropbox to have Accessibility permissions, is that it's in there just in case they want that access in the future. If that's right, it suggests that Dropbox simply want to have access to anything and everything on your mac, whether it's needed or not.

The upshot for me was that I learned a few things about how security and authorisation work on the mac that I didn't know before investigating what Dropbox was up to. But most of all, I learned that I don't trust Dropbox _at all_. Unnecessary privileges and backdooring are what I call untrustworthy behaviour and a clear breach of user trust. With Apple's recent stance against the FBI and their commitment to privacy in general, I feel moving over to iCloud and [dropping Dropbox](http://www.drop-dropbox.com) is a far more sensible way to go for me. For those of you who are stuck with Dropbox but don't want to allow it access to Accessibility features, you can thwart Dropbox's hack by following [my procedure here](http://applehelpwriter.com/2016/07/28/revealing-dropboxs-dirty-little-security-hack/#comment-27348).

**Further Reading:**
