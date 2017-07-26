# how to reveal hidden users

_Captured: 2017-06-15 at 02:10 from [applehelpwriter.com](http://applehelpwriter.com/2017/05/21/how-to-reveal-hidden-users/?utm_content=bufferd51d9&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

![](https://applehelpwriter.files.wordpress.com/2017/05/screen-shot-2017-05-21-at-17-32-081.png?w=1208&h=928)

**With malware big** in the news again, and evidence that at least [one malware variant that targets macOS creates hidden users](https://www.cybereason.com/cybereason-labs-analysis-the-minds-behind-the-osx-pirrit/) on the victim's system, here's a timely tip on how to check for unwelcome guests.

For this tip, we're going to use the Terminal, which you can find in the /Applications/Utilities folder. If you're not a frequent visitor to the land of the command line, you might want to see my 3-part series "[Learning the Terminal"](http://applehelpwriter.com/2012/03/17/learning-the-terminal-part-one/).

Regardless, the first thing we're going to do in Terminal is about the simplest command you'll ever type: `w`. Yep, type a single 'w' at the prompt and press return.

![](https://applehelpwriter.files.wordpress.com/2017/05/screen-shot-2017-05-21-at-17-20-48.png?w=1206&h=688)

The `w` utility is a very quick way to see who's currently logged on to your system and to ensure that there's no surprises. You should see a couple of entries for yourself: one as 'console' and one as 's***'. The first represents a login through the usual Desktop GUI login window; the second is there because you just logged into Terminal. Anybody else logged in either via the command line (like a potential remote user) or the GUI will show up here. Notice that on my machine, there's another user called 'Developer' who hasn't logged in using the GUI, but is logged in via a command line interface. Note that 'w' returns the full user name, not the short one.

While the `w` utility will tell you if a hidden user is _currently_ logged on, what if there's a hidden user that isn't active at the particular time you check? To look for those, we have a couple of options. First, we can use the `dscl` utility to list all users, and you might be surprised at how many there are:

`dscl . -list /Users`

Look to the end of that list where the names that don't begin with an underscore start. 'Daemon', 'Nobody', 'Root' and 'Guest' are all standard system accounts, as are all those entries that begin with an underscore. Don't worry about those. However, aside from those, you should only see names that you recognise. To make things a little easier, we can add another command to the dscl command to filter that list. Try this

dscl . -list /Users | grep -vE '_|root|nobody|daemon|Guest'

That should now only return the names of real users. There shouldn't be any names in there you don't recognise. In my example, I know the last three, but the first one 'dev' isn't familiar to me. Note that unlike 'w', this command returns short user names, and that 'dev' looks very much like it's the same account as 'Developer' that I saw earlier.

![](https://applehelpwriter.files.wordpress.com/2017/05/screen-shot-2017-05-21-at-17-21-16.png?w=1208&h=468)

However, what we have so far is a list of users, not a list of _hidden_ users. To see specifically if any accounts are hidden, we need a longer command:

`defaults read /Library/Preferences/com.apple.loginwindow`

Normally, when there are no hidden users, this will return the contents of a property list file that may look something like this:

`{  
GuestEnabled = 1;  
OptimizerLastRunForBuild = 31898816;  
OptimizerLastRunForSystem = 168494592;  
SHOWFULLNAME = 1;  
lastUser = loggedIn;  
lastUserName = imackim;  
}`

That tells us that there's no hidden users on this mac. How so? Because if there were it would return something very different, like this:

![](https://applehelpwriter.files.wordpress.com/2017/05/loginwindow-plist1.png)

We can see not only the list of hidden users, but also that the preference for hiding users has been set to '1' (in plist syntax, '1' means true and '0' means false). Note again that unlike the `dscl` command above, this returns the account's full name, not the short user name.

If we'd like to 'unhide' that user, so the account appears in the login window GUI and in System Preferences' 'Users & Groups' pane, we'll need admin privileges. To do that, cut and paste the following into Terminal:

`sudo defaults write /Library/Preferences/com.apple.loginwindow Hide500Users -bool NO`

Supply an admin user password at the prompt and hit 'return', but type slowly as the display doesn't register your key presses, which makes it easy to fat finger your password.

**For the more advanced**  
We can save ourselves some typing by putting much of this into a script so that we can run it whenever we want. If you're not familiar with how to create and use bash scripts, take a look [here](http://stackoverflow.com/questions/8779951/how-do-i-run-a-shell-script-without-using-sh-or-bash-commands).

Our script will basically do the same as all the commands we listed above (except changing the prefs for `Hide500Users`) in one fell swoop, and there's a couple of little twists that I'll leave as an exercise for the reader to figure out. To save on the typing, you can copy the whole script from my pastebin [here](https://pastebin.com/g44U0RAJ).

![](https://applehelpwriter.files.wordpress.com/2017/05/screen-shot-2017-05-21-at-17-45-35.png?w=1208&h=764)

The script's output is illustrated in the shot at the top of this post.

Enjoy!
