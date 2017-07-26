# 42 of the Most Useful Raspberry Pi Commands

_Captured: 2017-01-28 at 11:58 from [www.circuitbasics.com](http://www.circuitbasics.com/useful-raspberry-pi-commands/)_

![42 of the Most Useful Raspberry Pi Commands](https://i0.wp.com/www.circuitbasics.com/wp-content/uploads/2015/02/lcd-sudo-su.png?resize=672%2C423)

Sometimes it's difficult to keep track of all the useful [Raspberry Pi](http://buy.geni.us/Proxy.ashx?TSID=13213&GR_URL=http%3A%2F%2Fwww.amazon.com%2Fgp%2Fproduct%2FB00T2U7R7I%2Fref%3Das_li_qf_sp_asin_il_tl%3Fie%3DUTF8%26camp%3D1789%26creative%3D9325%26creativeASIN%3DB00T2U7R7I%26linkCode%3Das2%26tag%3Dcircbasi-20%26linkId%3DDIWIYTYYNRK362TG) commands you use, so I created a list of some of the most common and important ones that will make using Linux on the Raspberry Pi a lot easier.

There are two user "modes" you can work with in Linux. One is a user mode with basic access privileges, and the other is a mode with administrator access privileges (AKA super user, or root). Some tasks cannot be performed with basic privileges and you will need to enter into root mode to perform them. You will frequently see the prefix sudo before commands, which means that you are telling the computer to operate the command with super user privileges. Another way is to access the _root command prompt_, which operates all commands with super user privileges. Access root mode by entering sudo su at the command prompt. After entering sudo su, you will see the root@raspberrypi:/home/pi# command prompt, and all subsequent commands can be entered without the sudo prefix and still have super user privileges.

Most of the commands below have a lot of other useful options that I have not explained. To see a list of all the other available options for a command, enter the command, followed by -help.

## 42 of the Most Useful Raspberry Pi Commands:

_General Commands_

  * apt-get update: Updates your version of Raspbian.
  * apt-get upgrade: Upgrades all of the software packages you have installed.
  * clear: Clears the terminal screen of previously run commands and text.
  * date: Prints the current date.
  * find / -name example.txt: Searches the whole system for the file example.txt and outputs a list of all directories that contain the file.
  * nano example.txt: Opens the file example.txt in "Nano", the Linux text editor.
  * poweroff: To shutdown immediately.
  * raspi-config: Opens the configuration settings menu.
  * reboot: To reboot immediately.
  * shutdown -h now: To shutdown immediately.
  * shutdown -h 01:22: To shutdown at 1:22 AM.
  * startx: Opens the GUI (Graphical User Interface).

_File/Directory Commands_

  * cat example.txt: Displays the contents of the file example.txt.
  * cd /abc/xyz: Changes the current directory to the /abc/xyz directory.
  * cp XXX: Copies the file or directory XXX and pastes it to a specified location; i.e. cp examplefile.txt /home/pi/office/ copies examplefile.txt in the current directory and pastes it into the /home/pi/ directory. If the file is not in the current directory, add the path of the file's location (i.e. cp /home/pi/documents/examplefile.txt /home/pi/office/ copies the file from the documents directory to the office directory).
  * ls -l: Lists files in the current directory, along with file size, date modified, and permissions.
  * mkdir example_directory: Creates a new directory named example_directory inside the current directory.
  * mv XXX: Moves the file or directory named XXX to a specified location. For example, mv examplefile.txt /home/pi/office/ moves examplefile.txt in the current directory to the /home/pi/office directory. If the file is not in the current directory, add the path of the file's location (i.e. cp /home/pi/documents/examplefile.txt /home/pi/office/ moves the file from the documents directory to the office directory). This command can also be used to rename files (but only within the same directory). For example, mv examplefile.txt newfile.txt renames examplefile.txt to newfile.txt, and keeps it in the same directory.
  * rm example.txt: Deletes the file example.txt.
  * rmdir example_directory: Deletes the directory example_directory (only if it is empty).
  * scp user@10.0.0.32:/some/path/file.txt: Copies a file over SSH. Can be used to download a file from a desktop/laptop to the Raspberry Pi. _user@10.0.0.32_ is the username and local IP address of the desktop/laptop and _/some/path/file.txt_ is the path and file name of the file on the desktop/laptop.
  * touch: Creates a new, empty file in the current directory.

_Networking/Internet Commands_

  * ifconfig: To check the status of the wireless connection you are using (to see if wlan0 has acquired an IP address).
  * iwconfig: To check which network the wireless adapter is using.
  * iwlist wlan0 scan: Prints a list of the currently available wireless networks.
  * iwlist wlan0 scan | grep ESSID: Use grep along with the name of a field to list only the fields you need (for example to just list the ESSIDs).
  * nmap: Scans your network and lists connected devices, port number, protocol, state (open or closed) operating system, MAC addresses, and other information.
  * ping: Tests connectivity between two devices connected on a network. For example, ping 10.0.0.32 will send a packet to the device at IP 10.0.0.32 and wait for a response. It also works with website addresses.
  * wget http://www.website.com/example.txt: Downloads the file example.txt from the web and saves it to the current directory.

_System Information Commands_

  * cat /proc/meminfo: Shows details about your memory.
  * cat /proc/partitions: Shows the size and number of partitions on your SD card or hard drive.
  * cat /proc/version: Shows you which version of the Raspberry Pi you are using.
  * df -h: Shows information about the available disk space.
  * df /: Shows how much free disk space is available.
  * dpkg -get-selections | grep XXX: Shows all of the installed packages that are related to XXX.
  * dpkg -get-selections: Shows all of your installed packages.
  * free: Shows how much free memory is available.
  * hostname -I: Shows the IP address of your Raspberry Pi.
  * lsusb: Lists USB hardware connected to your Raspberry Pi.
  * UP key: Pressing the UP key will enter the last command entered into the command prompt. This is a quick way to correct commands that were made in error.
  * vcgencmd measure_temp: Shows the temperature of the CPU.
  * vcgencmd get_mem arm && vcgencmd get_mem gpu: Shows the memory split between the CPU and GPU.

Hopefully this list of commands will make navigating Linux on your Raspberry Pi more efficient and enjoyable. If you feel that I have left anything out, please leave a comment below and I'll add it to the list.
