# Most Useful Linux Command Line Tricks

_Captured: 2017-02-21 at 20:25 from [dzone.com](https://dzone.com/articles/most-useful-linux-command-line-tricks?edition=272882&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-21)_

### It's easy to forget what we've learned in the past when we don't practice. This happens often when we work with the same Linux command lines.

[Discover how to optimize your DevOps workflows](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) with our cloud-based automated testing infrastructure, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161129&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).

We use many [Linux command lines](https://likegeeks.com/main-linux-commands-easy-guide/) every day. We know some tricks from the web, but if we don't practice them, we may forget them. I've decided to make a list of tips and tricks that you may have forgotten or that may be entirely new to you.

## Display Output as a Table

Sometimes, when you see the output of a command, it can be overwhelming to identify the output due to overcrowded strings (for example, the output of the mount command). How about viewing it like a table? This is easy to do!

`mount | column -t`:

![mount table view](https://likegeeks.com/wp-content/uploads/2017/02/01-mount-table-view-1024x578.png)

In this example, the output is well-formatted because of the spaces. What if the separators were something else, like colons? (For example, in the output of `cat /etc/passwd`.)

Just specify the separator with an `-s` parameter, like below.

`cat /etc/passwd | column -t -s`:

![users tabular view](https://likegeeks.com/wp-content/uploads/2017/02/02-users-tabular-view-1024x578.png)

## Repeat a Command Until It Runs Successfully

If you search Google about this feature, you will find that a lot of people have asked how to repeat the command until it returns successfully and runs correctly. Suggestions include pinging the server until it becomes live, checking if a file with a specific extension is uploaded from a specific directory, checking if a specific URL has come into existence, etc.

You can use the `while true` loop to achieve that:

![repeat till success](https://likegeeks.com/wp-content/uploads/2017/02/03-repeat-till-success.png)

In this example, `>/dev/null 2>&1` redirects the output of your program to `/dev/null`. Include both the `Standard Error` and `Standard Out`.

This is one of coolest Linux command line tricks to me.

## Sort Processes by Memory Usage

`ps aux | sort -rnk 4`:

![sort by memory usage](https://likegeeks.com/wp-content/uploads/2017/02/04-sort-by-memory-usage.png)

## Sort Processes by CPU Usage

`ps aux | sort -nk 3`:

![sort by cpu usage](https://likegeeks.com/wp-content/uploads/2017/02/05-sort-by-cpu-usage.png)

> _To check your architecture, perform getconf LONG_BIT ._

## Watch Multiple Log Files at the Same Time

You may use tail commands to watch your logs without problems, but sometimes, you may want to watch multiple log files. Using multi-tail commands supports text highlighting, filtering, and many more features that you may need:

![multitail command](https://likegeeks.com/wp-content/uploads/2017/02/06-multitail.png)

> _You can install it if it is not found on your system with apt-get install multitail ._

## Return to Your Previous Directory

just type `cd -` and you will return back to the previous directory.

## Make a Non-Interactive Shell Session Interactive

To do this, change the settings from `~/.bashrc` to `~/.bash_profile`.

## Monitor Command Output at Regular Intervals

Using the watch command (`watch df -h`), you can watch any output of any command. For example, you can watch the free space and how it is growing.

You can imagine what you can do with variant data by using the watch command.

## Run Program After Session Killing

When you run any program in the background and close you, it will be killed by your shell. How can you continue running the program after closing the shell?

This can be done using a nohup command -- which stands for no hang-up:

`nohup wget site.com/file.zip`

This command is one of the most forgotten Linux command line tricks because many of us use another command-like screen:

![nohup command](https://likegeeks.com/wp-content/uploads/2017/02/07-nohup-command.png)

A file will be generated in the same directory with the name `nohup.out`, which contains the output of the running program:

![nohup output](https://likegeeks.com/wp-content/uploads/2017/02/08-nohup-output.png)

Cool command, right?

## Automatically Answer Yes or No to Any Command

If you want to automate the process that requires user to say yes

That can be done using yes command: `yes | apt-get update`.

Maybe you want to automate saying "no" instead. This can be done using `yes no | command`.

![yes command](https://likegeeks.com/wp-content/uploads/2017/02/09-yes-command.png)

## Create File With a Specific Size

You can create a file with a specific size using the `dd` command: `dd if=/dev/zero of=out.txt bs=1M count=10`.

This will create a file of 10 megabytes filled with zeros:

![dd command](https://likegeeks.com/wp-content/uploads/2017/02/10-dd-command.png)

## Run Your Last Command as Root

Sometimes, you forget to type `sudo` before your command that requires root privileges. You don't have to rewrite it; just type `sudo`!

![sudo command](https://likegeeks.com/wp-content/uploads/2017/02/11-sudo.png)

## Record Your Command Line Session

If you want to record what you've typed on your shell screen, you can use script command to save all of your typings to a file named `typescript` : `script`.

Once you type exit, all of your commands will be written to that file so you can review it later.

## Replace Spaces With Tabs

You can replace any character with any other using the `tr` command, which is very handy: `cat geeks.txt | tr ':[space]:' '\t' > out.txt`.

![tr command](https://likegeeks.com/wp-content/uploads/2017/02/12-tr-command.png)

## Convert a File to Upper or Lower Case

You can do this using: `cat myfile | tr a-z A-Z > output.txt`.

## Powerful Xargs Command

The `xargs` command is one of the most important Linux command line tricks. You can use this command to pass the output of a command to another command as an argument. For example, you may search for PNGpng files and compress them or do anything with them:

`find. -name *.png -type f -print | xargs tar -cvzf images.tar.gz`

Or, maybe you have a list of URLs in a file and you want to download them or process them in a different way:

`cat urls.txt | xargs wget`

![xargs command](https://likegeeks.com/wp-content/uploads/2017/02/13-xargs-command.png)

Keep in mind that the output of the first command passed at the end of the `xargs` command.

What if your command needs the output in the middle? Easy!

Just use `{}` combined with the `-i` parameter, like below, to replace arguments in the place where the output of the first command should go:

`ls /etc/*.conf | xargs -i cp {} /home/likegeeks/Desktop/out`

This is only a few Linux command line tricks. There are some more geeky things that you can do using other commands, like the `awk` command and the `sed` command!

If you know any other geeky commands that I did not mention, feel free to comment.

[Download "The DevOps Journey - From Waterfall to Continuous Delivery"](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle) to learn learn about the importance of integrating automated testing into the DevOps workflow, brought to you in partnership with [Sauce Labs](https://dzone.com/go?i=161130&u=http%3A%2F%2Finfo.saucelabs.com%2Fpaper-the-devops-journey.html%3Futm_campaign%3Ddevopsjourney%2Bwp%26utm_medium%3Dtextlink%26utm_source%3Ddzone-devops%26utm_content%3Darticle).
