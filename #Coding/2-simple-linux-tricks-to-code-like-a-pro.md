# 2 Simple Linux Tricks to Code Like a Pro | Make:

_Captured: 2017-11-15 at 13:39 from [makezine.com](https://makezine.com/2017/11/10/2-simple-linux-tricks/)_

Linux is a powerful open source operating system that has been around for many
years and is widely used for running servers and websites. But most students
and makers encounter it for the first time when they are working on projects
with their Raspberry Pi or similar single-board computers (SBCs) such as
BeagleBone Black or Intel Galileo. By gaining a deeper understanding of Linux,
makers can add another useful tool to their kit that will help them build
their projects more easily.

If you are like me, your spelling and typing abilities may be lacking. Too
many times I have spent 20 or 30 seconds typing a long command with lots of
options only to find out after I hit enter that I had something wrong and
needed to start from the beginning again. Not only that, but with all the
possible choices, it can be hard to remember exactly the command you used to
perform a certain task from day to day. Luckily, the Linux shell has some
tools built in that can help with both of these problems.

![](https://i2.wp.com/makezine.com/wp-content/uploads/2017/11/Screen-
Shot-2017-08-17-at-9.50.36-PM-1024x602.png?resize=1024%2C602&ssl=1)<img
class="aligncenter size-large wp-image-534033"
src="https://i2.wp.com/makezine.com/wp-content/uploads/2017/11/Screen-
Shot-2017-08-17-at-9.50.36-PM-1024x602.png?resize=1024%2C602&#038;ssl=1"
alt="" srcset="https://i0.wp.com/makezine.com/wp-content/uploads/2017/11
/Screen-Shot-2017-08-17-at-9.50.36-PM.png?resize=1024%2C602&amp;ssl=1 1024w,
https://i0.wp.com/makezine.com/wp-content/uploads/2017/11/Screen-
Shot-2017-08-17-at-9.50.36-PM.png?resize=620%2C365&amp;ssl=1 620w,
https://i0.wp.com/makezine.com/wp-content/uploads/2017/11/Screen-
Shot-2017-08-17-at-9.50.36-PM.png?resize=768%2C452&amp;ssl=1 768w,
https://i0.wp.com/makezine.com/wp-content/uploads/2017/11/Screen-
Shot-2017-08-17-at-9.50.36-PM.png?resize=90%2C53&amp;ssl=1 90w,
https://i0.wp.com/makezine.com/wp-content/uploads/2017/11/Screen-
Shot-2017-08-17-at-9.50.36-PM.png?resize=300%2C176&amp;ssl=1 300w,
https://i0.wp.com/makezine.com/wp-content/uploads/2017/11/Screen-
Shot-2017-08-17-at-9.50.36-PM.png?w=1600&amp;ssl=1 1600w" sizes="(max-width:
1000px) 100vw, 1000px" data-recalc-dims="1" />

### Auto-complete a command: TAB

You can use the auto-complete feature of the shell by simply pressing the Tab
key on the keyboard. This will auto-complete a command that has been partially
typed and it will also auto-complete a filename based on the context of what
you are typing.

**TIP:** By default, Tab doesn’t always know about the available options for a command, but can auto-complete the name of the command and any associated file names that might be used as part of a command.

For example, if you type “tou” and press the Tab key, the shell will fill in
the rest of the missing letters to make “touch”. If there are multiple options
that start with the letters you have entered, the first time you press Tab
nothing will happen. If you press it again, however, the shell will display a
list of all possible commands or file names that start with the letters you
entered. So, if you type “mkd” and press Tab twice, you will be presented with
two options for commands that start with mkd: `mkdir` and `mkdosfs`:

    
    
    pi@raspberrypi ~ $ mkd
     mkdir mkdosfs
     pi@raspberrypi ~ $ mkd

If you continue to add more characters and then press Tab, you will eventually
rule out all the other options and the shell will complete the rest of the
command or filename when there is only one choice left. This auto-complete
feature is a real time saver with bigger commands and long file names. It also
eliminates spelling errors when you haven’t used a command very often yet.

![](https://i2.wp.com/makezine.com/wp-content/uploads/2017/11/TuxPenguinReal-
884x1024.jpg?resize=844%2C978&ssl=1)<img class="aligncenter wp-image-534034"
src="https://i2.wp.com/makezine.com/wp-content/uploads/2017/11/TuxPenguinReal-
884x1024.jpg?resize=844%2C978&#038;ssl=1" alt=""
srcset="https://i2.wp.com/makezine.com/wp-
content/uploads/2017/11/TuxPenguinReal.jpg?resize=884%2C1024&amp;ssl=1 884w,
https://i2.wp.com/makezine.com/wp-
content/uploads/2017/11/TuxPenguinReal.jpg?resize=620%2C718&amp;ssl=1 620w,
https://i2.wp.com/makezine.com/wp-
content/uploads/2017/11/TuxPenguinReal.jpg?resize=768%2C889&amp;ssl=1 768w,
https://i2.wp.com/makezine.com/wp-
content/uploads/2017/11/TuxPenguinReal.jpg?resize=90%2C104&amp;ssl=1 90w,
https://i2.wp.com/makezine.com/wp-
content/uploads/2017/11/TuxPenguinReal.jpg?resize=300%2C347&amp;ssl=1 300w,
https://i2.wp.com/makezine.com/wp-
content/uploads/2017/11/TuxPenguinReal.jpg?resize=345%2C400&amp;ssl=1 345w,
https://i2.wp.com/makezine.com/wp-
content/uploads/2017/11/TuxPenguinReal.jpg?w=1600&amp;ssl=1 1600w" sizes
="(max-width: 844px) 100vw, 844px" data-recalc-dims="1" />

### Search for a previous command: Up, CTRL-R

Linux keeps a history of all the things you type into the command line. A
simple way to review the commands you have typed is simply to use the Up Arrow
to scroll back through each command starting with the most recent. If the
command you are looking for is further back in your history, you can search
for it by pressing “Ctrl-R” on the command line followed by some characters.
For example, if you wanted to search for the last time you used `nano` to edit
a file you could press “Ctrl-R” followed by “`nano`”.

![](https://i0.wp.com/makezine.com/wp-content/uploads/2017/11/LinuxforMakers-
Cover-1-699x1024.jpg?resize=287%2C420&ssl=1)<img class="wp-image-534035"
src="https://i0.wp.com/makezine.com/wp-content/uploads/2017/11/LinuxforMakers-
Cover-1-699x1024.jpg?resize=287%2C420&#038;ssl=1" alt=""
srcset="https://i0.wp.com/makezine.com/wp-content/uploads/2017/11
/LinuxforMakers-Cover-1.jpg?resize=699%2C1024&amp;ssl=1 699w,
https://i0.wp.com/makezine.com/wp-content/uploads/2017/11/LinuxforMakers-
Cover-1.jpg?resize=620%2C908&amp;ssl=1 620w, https://i0.wp.com/makezine.com
/wp-content/uploads/2017/11/LinuxforMakers-
Cover-1.jpg?resize=768%2C1125&amp;ssl=1 768w, https://i0.wp.com/makezine.com
/wp-content/uploads/2017/11/LinuxforMakers-
Cover-1.jpg?resize=90%2C132&amp;ssl=1 90w, https://i0.wp.com/makezine.com/wp-
content/uploads/2017/11/LinuxforMakers-Cover-1.jpg?resize=300%2C439&amp;ssl=1
300w, https://i0.wp.com/makezine.com/wp-content/uploads/2017/11
/LinuxforMakers-Cover-1.jpg?resize=273%2C400&amp;ssl=1 273w,
https://i0.wp.com/makezine.com/wp-content/uploads/2017/11/LinuxforMakers-
Cover-1.jpg?w=1168&amp;ssl=1 1168w" sizes="(max-width: 287px) 100vw, 287px"
data-recalc-dims="1" />

This is an excerpt from Aaron Newcomb’s book _Linux for Makers_, available [on
Maker Shed](https://www.makershed.com/products/make-linux-for-makers) and fine
book retailers everywhere.

It doesn’t matter if there’s already some information entered at the cursor
when you press Ctrl-R. That text won’t be used for the search, only what you
type after you press Ctrl-R. Notice that the prompt changes to
`(reverse-i-search)` followed by the letters you entered when doing this type
of search through your command history.

    
    
    (reverse-i-search)‘nano’: nano hello.sh

If you press one of the arrow keys, Home, End, or Tab, you will finish the
search and be able to edit the command that you looked up. You can also
continue to search through your history by pressing Ctrl-R multiple times
before you exit out of the search.

Try it for yourself: Change to your home directory and create a file by
typing:

    
    
    cd
     tou <TAB> file1

When you press Tab it should complete the name of the `touch` command. Now
change to your Downloads directory by typing:

cd D <TAB> <TAB>

You should see something similar to this:

    
    
    pi@raspberrypi ~ $ cd D
     Desktop/ Documents/Downloads/
     pi@raspberrypi ~ $ cd D

Add the letters “`ow`” and press Tab again to auto-complete the path we want
and press enter.  
Now let’s create our second file by using the command history. Press Ctrl-R
followed by “`tou`”:

    
    
    pi@raspberrypi ~ $ cd D
     Desktop/ Documents/Downloads/
     pi@raspberrypi ~ $ cd Downloads/
     (reverse-i-search)‘tou’: touch file1

Press the End key and change “`file1`” to “`file2`”. Press enter to complete
the task. Now you have created two files — one in your home directory and one
in the Downloads directory. You have also saved a lot of typing in the
process!
