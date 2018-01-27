# screen: Keep Your Processes Running Despite A Dropped Connection

_Captured: 2017-11-09 at 23:30 from [www.howtoforge.com](https://www.howtoforge.com/linux_screen)_

Version 1.0

I guess you all know this: you are connected to your server with SSH and in the middle of compiling some software (e.g. a new kernel) or doing some other task which takes lots of time, and suddenly your connection drops for some reason, and you lose your labour. This can be very annoying, but fortunately there is a small utility called screen which lets you reattach to a previous session so that you can finish your task. This short tutorial shows how to use screen for just this purpose.

### 1 Installing screen

The installation of screen is very easy. On Debian and Ubuntu, you just run

apt-get install screen

I guess that for Fedora, CentOS, SuSE, and Mandriva there are also screen packages that you can install with yum/yast/urpmi/...

### 2 Using screen

With screen you can create one or more sessions in your current SSH terminal. Just run

screen

to start it. This creates a screen session or window (although you don't see it as such) in your current SSH terminal:

![](https://www.howtoforge.com/images/linux_screen/1.png)

Press Space or Return to get to the command prompt:

![](https://www.howtoforge.com/images/linux_screen/2.png)

Looks like your normal SSH terminal, doesn't it?

Now I'm going to describe the most important screen commands that you need to control screen. These commands begin with CTRL a to distinguish them from normal shell commands.

  * Ctrl a c - Creates a new screen session so that you can use more than one screen session at once.
  * Ctrl a n - Switches to the **n**ext screen session (if you use more than one). 
  * Ctrl a p - Switches to the **p**revious screen session (if you use more than one).
  * Ctrl a d - Detaches a screen session (without killing the processes in it - they continue). 

To close a screen session where all tasks are finished you can type

exit

Now let's play around with it a little bit. In our screen window we run the command

top

This should look like this:

![](https://www.howtoforge.com/images/linux_screen/3.png)

Now let's create another screen session by typing

Ctrl a c

A new, blank screen session opens, and there we run

tail -f /var/log/mail.log

to have an ongoing look at our mail log:

![](https://www.howtoforge.com/images/linux_screen/4.png)

Now you can browse your two screen sessions by running

Ctrl a n

or

Ctrl a p

To detach a screen session and return to your normal SSH terminal, type

Ctrl a d

Back on your normal SSH terminal, you can run

screen -ls

to get a list of your current screen sessions:

There are screens on:  
2477.pts-0.server1 (Detached)  
2522.pts-0.server1 (Detached)  
2 Sockets in /var/run/screen/S-root.

To reconnect to one of these sessions, run

screen -r 2477.pts-0.server1

where 2477.pts-0.server1 is the name of one of the sessions from the screen -ls output.

To leave and finish a screen session, finish all current tasks in it (top can be finished by typing q, tail -f /var/log/mail.log can be finished by typing CTRL c) and then type

exit

You will then fall back to another screen session (if you use more than one) or to the normal SSH terminal, if no more screen sessions are open.

If you want to learn more about screen, run

man screen

### 3 My Connection Dropped - What Can I Do?

Now let's assume you compile a kernel in a screen session, something which normally takes a long time, and suddenly your connection drops. Thanks to screen your work isn't lost. Once your connection is back up, log in to your system with SSH again and run

screen -ls

as shown in chapter 2. From the results pick one session (e.g. 2477.pts-0.server1) and reattach to it:

screen -r 2477.pts-0.server1

If you picked the right session, you should find your kernel still compiling (if it hasn't finished in the meantime) so that you can continue your work.

### 4 Links

  * screen: [http://www.gnu.org/software/screen](http://www.gnu.org/software/screen/)
