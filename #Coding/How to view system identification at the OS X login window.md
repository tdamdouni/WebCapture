# How to view system identification at the OS X login window

_Captured: 2015-11-24 at 01:43 from [www.macissues.com](http://www.macissues.com/2015/11/19/how-to-view-system-identification-at-the-os-x-login-window/#more-4014)_

![FinderIconYosemiteX](http://i0.wp.com/www.macissues.com/wp-content/uploads/2014/10/FinderIconYosemiteX.png?resize=150%2C150)

When logging into a Mac you generally see your list of usernames that you can click, followed by a password entry field. While you can enable other features such as a the shutdown and restart buttons, as well as the system's input menu, these are fairly static functions that offer utility but no additional information about the system. However, being able to identify a system at the login window may be useful, and in OS X there are two ways to accomplish this.

First is to create a login window message, by opening the Terminal and running the following command. Note the command shown here has two lines to it (formatted this way to prevent the software running this blog from breaking the command's syntax with automatic line breaks), but you can remove the back-slash on the first line to continue it all on one line. For instance, here just continue "com.apple.loginwindow…" when you type, as opposed to typing "com.ap\" followed by a return to a new line before continuing the command. However, either approach will do just fine.
    
    
    sudo defaults write /Library/Preferences/com.ap\
    ple.loginwindow LoginwindowText "TEXT GOES HERE"

In this command, replace "TEXT GOES HERE" with your desired phrase, and press Enter to execute the command. This will append the text message to the login window, which you should see by returning to it (log out or use Fast User Switching). This is useful for adding a phone number, email address, or other details more unique to you or your organization.

You can re-un the command to change the phrase, or run the following command to remove the text altogether:
    
    
    sudo defaults delete /Library/Preferences/com.ap\
    ple.loginwindow LoginwindowText

You can use the login window text to show system information such as IP address, OS X version, and computer name; however, these are more dynamic settings for your Mac, and may change if your network setup is altered in any way, or if someone performs administrative tasks on your Mac. Because of this, it may be best to use the login window's separate ability to show this information, which can be enabled by running the following commands:
    
    
    sudo defaults write /Library/Preferences/com.ap\
    ple.loginwindow AdminHostInfo HostName

With this command entered, return to the login window and you will the OS version appear where other menu extras are shown. Now click the system to the far left, and you will see the OS version switch to the machine name and then to the current IP address.

![loginwindow host information and custom message](http://i2.wp.com/www.macissues.com/wp-content/uploads/2015/11/LoginWindowInfo.png?resize=625%2C391)

> _The login window message shows under your list of accounts, and the host information shows in the toolbar (click the current system time to switch the host information between IP address, OS version, and system name)._

As with all "defaults" commands, this one for displaying host information can be removed by re-running the command using the "delete" flag and then only providing the defaults key, as follows:
    
    
    sudo defaults delete /Library/Preferences/com.ap\
    ple.loginwindow AdminHostInfo
