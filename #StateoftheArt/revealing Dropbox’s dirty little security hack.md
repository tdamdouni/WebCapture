# revealing Dropbox’s dirty little security hack

_Captured: 2016-11-07 at 10:29 from [applehelpwriter.com](http://applehelpwriter.com/2016/07/28/revealing-dropboxs-dirty-little-security-hack/)_

![Screen Shot 2016-07-28 at 14.54.30](https://applehelpwriter.files.wordpress.com/2016/07/screen-shot-2016-07-28-at-14-54-30.png?w=604&h=506)

> _Update: also see Discovering how Dropbox hacks your mac_

If you have Dropbox installed, take a look at `System Preferences > Security & Privacy > Accessibility` tab (see screenshot above). Notice something? Ever wondered how it got in there? Do you think you might have put that in there yourself after Dropbox asked you for permission to control the computer?

No, I can assure you that your memory isn't faulty. You don't remember doing that because Dropbox never presented this dialog to you, as it should have:

![AskForPermission](https://applehelpwriter.files.wordpress.com/2016/07/askforpermission.png?w=604&h=303)

That's the only officially supported way that apps are allowed to appear in that list, but Dropbox never asked you for that permission. I'll get to why that's important in a moment, but if you have the time, try this fascinating experiment: _try and remove it_.

Ok, you say, no problem. We all know how to do that - open the padlock, un-click the checkbox. Click the '-' button to remove it from the list. Simple, right? Look there it goes, no more Dropbox in the the Preferences panel, right?

Wrong…like a bad penny it'll be back again before you know it. Either log out and log back in again or quit Dropbox and restart it. Dropbox will surreptitiously insert itself back in to that list AND the checkbox will be checked. That's the magic of Dropbox for you. If you don't want to try it for yourself, watch me do it:

That leaves a couple of questions. First, why does it matter, and second, is there any way to keep using Dropbox but stop it having access to control your computer?

There's at least three reasons why it matters. It matters first and foremost because Dropbox didn't ask for permission to take control of your computer. What does 'take control' mean here? It means to literally do what you can do in the desktop: click buttons, menus, launch apps, delete files… . There's a reason why apps in that list have to ask for permission and why it takes a password and explicit user permission to get in there: it's a security risk.

> **Interlude:** Contrary to Dropbox's completely spurious "explanation"/obfuscation [here](https://www.dropboxforum.com/hc/en-us/community/posts/204505875-MacOS-X-Security-Is-it-normal-to-allow-Dropbox-app-to-control-your-computer-), Accessibility has nothing at all to do with granting permissions to files. [Accessibility frameworks](https://developer.apple.com/library/mac/documentation/Accessibility/Conceptual/AccessibilityMacOSX/index.html#//apple_ref/doc/uid/TP40001078-CH254-SW1) were first introduced in Mac OS X 10.2 and expanded in 10.3 to allow control of user interface items via System Events and the Processes suite. As anyone can readily see, what that allows is [GUI control](http://www.macosxautomation.com/applescript/uiscripting/index.html) just as if the program or script was clicking buttons and menu items.

But perhaps you implicitly trust Dropbox to not do anything untoward. After all, they're a big name company who wouldn't want to upset their customers, right?

There's two flaws in reasoning that way. One: the bigger the name, the less effect customer dissatisfaction has. Let's face it. If a 1000 people read this post and stop using Dropbox because of it, it's not going to make much difference to Dropbox. So assuming you can trust a "big name" company not to "[feck you off](https://www.youtube.com/watch?v=eNwcXtWFWic)' because they might lose your business is not "smart computing", even less smart if they figure that you're a customer on a free plan anyway… :p ([See this](http://arstechnica.com/security/2016/07/dark-patterns-are-designed-to-trick-you-and-theyre-all-over-the-web/) for more reasons why big companies in general don't pay much attention to ethical values). Two, and more importantly, you already have hard proof that Dropbox can't be trusted. It just overrode your and Apple's security preferences without asking you, and - as you've seen if you tried to remove it and noticed its magic reappearance act - it disregards your choices and re-inserts itself even after you've explicitly removed it (we'll sort this naughty behaviour out in a minute).

It matters for another reason, too. Let's assume for the sake of argument that Dropbox never does any evil on your computer. It remains the fact that the Dropbox process has that ability. And that means, if Dropbox itself has a bug in it, it's possible an attacker could take control of your computer by hijacking flaws in Dropbox's code. Of course, that's entirely theoretical, but all security risks are until someone exploits them. The essence of good computer security and indeed the very reason why OSX has these kinds of safeguards in place to begin with is that apps should not have permissions greater than those that they need to do their job.

Which is the third reason why it matters: Dropbox doesn't appear to need to have access to Accessibility features in order to work properly ([update](http://applehelpwriter.com/2016/08/29/discovering-how-dropbox-hacks-your-mac/#comment-27468)). I figured out what Dropbox was up to in October 2015. Why has it taken me this long to write about it? First, because after having reported it to Apple Product Security at that time, I wanted to see if they would force Dropbox to change this behaviour (they haven't…[yet](http://www.apple.com/macos/sierra/) ;)). Second, because the only way I could be sure that DB didn't need to be in the list of apps with Accessibility privileges was to test it over a period of time. I use Dropbox across 3 different macs and an iPhone. I haven't experienced any issues using it _whatsoever_ while denying it access to Accessibility. _Caveat:_ I haven't tested Dropbox against _all_ of OSX's Accessibility features, but certainly for a 'standard' set up of OS X, it is not needed - and, let me repeat, even if it were needed for some particular feature to work, Dropbox should have _explicitly asked for this permission_, like every other app, and obeyed the user's decision to revoke that permission when removing it from the list of allowed apps.

There really isn't any excuse for Dropbox to ride roughshod over users' security and preference choices. So that leaves us with just one last question: how to get Dropbox out of there? The short answer is that you first quit Dropbox, then remove it from the Accessibility pane, then delete the DropboxHelperTools folder (see [my procedure here](http://applehelpwriter.com/2016/07/28/revealing-dropboxs-dirty-little-security-hack/#comment-27348)). Relaunch Dropbox, but now you hit 'Cancel' when it asks you for an admin password:

![Stop! Choose 'Cancel' !!!](https://applehelpwriter.files.wordpress.com/2016/07/dropbox-asks.png?w=604)

> _Stop! Choose 'Cancel' !!!_

The dialog box _apparently_ lies (again, still trusting this big name firm?) when it says Dropbox won't work properly and _clearly_ deceives because this is NOT the dialog box that Dropbox should be showing you to get access into Accessibility. Indeed, even with your admin password, it still shouldn't be able to get into Accessibility. Clearly Dropbox's coders have been doing some OS X hacking on company time.

Now, there's a slight catch. So long as you never give Dropbox your admin password, it won't be able to install itself in Accessibility and you can keep on using Dropbox just as you have done before. However, it will throw up this dialog box on every restart of the machine or relaunch of Dropbox. So the catch is that you have to actually notice what's asking you for your password and not just blindly throw your password into the box without looking. :O

But you shouldn't be doing that anyway, of course, cos that's not good security practice… , but given that the dialog box looks _just like***_ an authentic password request from the OS itself, that may be a habit you have to train yourself into.

Slightly annoying, but not as annoying as having an app hack your mac (of course, if you forget, you'll have to go uninstall Dropbox again, remove it from Accessibility, then reinstall it).

***But not "like" enough - note the 'Type your password…' sentence is both misaligned and is spaced into a separate paragraph, unlike genuine authentication requests from OS X. The phrasing of the first sentence "your computer password" is also very "un-OS X".

Last edit: 21 Sept, 21:35 ICT.
