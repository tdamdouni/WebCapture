# The (in)security of iCloud Backup

_Captured: 2016-02-19 at 12:45 from [medium.com](https://medium.com/@nweaver/the-in-security-of-icloud-backup-41b980977653#.5egxj3gxi)_

I'm currently working on developing a guide to securing iOS devices in a hostile environment (basically, "iPads for activists"). Although iOS is solid, iCloud backup is dangerously insecure, and must be avoided at all costs. Worse, it is enabled by default!

With iCloud backup, most of the contents of an iPhone are continuously backed up to Apple's cloud services. This includes pictures, contacts, messages, and other valuable content. If the iPhone encrypted this backup, it would be a useful service. Unfortunately it doesn't, and there is **_no meaningful protection_** for this data.

I conducted a simple test to verify the lack of protection:

  1. I configured a new iPad with a new Apple ID
  2. I generated some test data, and then forced a backup with iCloud backup
  3. I changed the password on the Apple ID account using the password recovery mechanism.
  4. I took a second iPad, performed a complete reset, and then had it "restore from backup" using the changed password.

The resulting second iPad contained the bulk of the information from the original iPad, notably including photographs and previously sent messages. Its only some items in the more secure store, notably the email and WiFi passwords, that weren't present on the new iPad.

This is horrifically insecure, and a major root cause behind "[the Fappening](https://en.wikipedia.org/wiki/2014_celebrity_photo_hack)": the attackers were able to compromise celebrities iCloud accounts and obtain the iCloud backups.

Apple could make iCloud backup substantially stronger. A good default would be to encrypt the backup with both the Apple ID password and the device password. Someone could restore from backup if they know one of the two passwords, but someone who doesn't have access to either password (such as a government subpoena, a corrupt Apple employee, or a [hacker exploiting the weaknesses in password recovery](https://www.theverge.com/a/anatomy-of-a-hack)) is unable to access the content.

An even better option would be to enable encryption with a single password, for those who want to explicitly secure their backup, although that can plainly not be the default without imposing significant usability problems.

Unfortunately, Apple doesn't seem to care about securing the backups themselves. They are improving the security for iCloud itself: adding **_optional_** phone verification and two-factor authentication. But such security doesn't change the fundamental problem: iCloud backups have **_no meaningful protection against attackers who can compromise a target's iCloud account_**.

Apple's approach of improving iCloud's authentication is akin to switching from hiding a doorkey under the mat to hiding it under a fake rock in a flowerpot.

If you want to back up your iPhone (and you should), use iTunes on your computer. And everyone should disable iCloud Backup (Settings->iCloud->Backup) and delete old backups. They represent a substantial security hole in an otherwise solid device.
