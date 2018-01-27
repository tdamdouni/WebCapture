# Add an IP Address and OS Version Display to the OS X Login Page

_Captured: 2015-11-24 at 01:44 from [lifehacker.com](http://lifehacker.com/add-an-ip-address-and-os-version-display-to-the-os-x-lo-1744245268?sidebar_promotions_icons=testingoff&utm_expid=66866090-67.e9PWeE2DSnKObFD7vNEoqg.1&utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+lifehacker%2Ffull+%28Lifehacker%29)_

![Add an IP Address and OS Version Display to the OS X Login Page](http://i.kinja-img.com/gawker-media/image/upload/s--Fld8MtnY--/1532023363086450727.jpg)

The login screen on a Mac is purposefully devoid of information, but if you'd like to add just a little more info, MacIssues shows you how to with Terminal command.

Once you run this command, you'll be able to click on the clock in the menubar to cycle between the computer's IP address, OS version, and system name. The IP address is pretty handy if you need to SSH into you Mac for any reason and don't feel like logging in. Regardless of your reason, enabling this just requires one setting to get tweaked in the command line. Open up Terminal (Applications > Utilities) and type in:
    
    
    sudo defaults write /Library/Preferences/com.ap\ ple.loginwindow AdminHostInfo HostName  
    

That's it, now you can quickly cycle through info on the login screen.

[How to view system identification at the OS X login window](http://www.macissues.com/2015/11/19/how-to-view-system-identification-at-the-os-x-login-window/#more-4014) | MacIssues
