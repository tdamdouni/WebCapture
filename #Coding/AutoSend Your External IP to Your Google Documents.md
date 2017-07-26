# AutoSend Your External IP to Your Google Documents

_Captured: 2016-11-20 at 10:42 from [ubuntuforums.org](https://ubuntuforums.org/showthread.php?t=1011105)_

> Dynamic IPs are nice, except that you can never remember what your IP is. This is especially annoying when you are away from home somewhere and you want to SSH or FTP to your home computer. Google documents are a nice place to store information online without having to pay or setup web space. Using this script, you can save your external IP inside the documents section of your gmail account. Then, you will know your home computer's external IP from anywhere just by logging onto gmail and going to the spreadsheet where your IP is stored.  
  
Let's get started!  
  
1) Python will need the google documents api, so go here, download the latest version, unpack and run the install script:  
  
[http://code.google.com/p/gdata-pytho...downloads/list](http://code.google.com/p/gdata-python-client/downloads/list)  
  
(if you're new to linux commands):  

>     
>     
>     wget http://gdata-python-client.googlecode.com/files/gdata.py-1.2.3.tar.gz
>     tar xvf gdata.py-1.2.3.tar.gz
>     cd gdata.py-1.2.3/
>     sudo python setup.py install
> 
> 2) Next, copy this code and paste it into your favorite text editor and save as **googleIP.py**  

>     
>     
>     #!/usr/bin/python
>     #
>     #
>     #  1) Install the google documents python api
>     #  2) Create a spreadsheet in google documents and save it under a name
>     #     that matches SPREADSHEET_NAME
>     #  3) Name the column headings of the google spreadsheet 'ip','date','time'
>     #  4) Edit USERNAME and PASSWD to match your login info
>     #  5) Make this file executable
>     #  6) In a terminal window, type 'crontab -e' and add this script to your
>     #  user's crontab. ex. 56 * * * * /usr/bin/python /path_to_your_script/googleIP.py
>     #
>     
>     import os
>     
>     ## Change These to Match Your Info!
>     
>     SPREADSHEET_NAME = 'MyHomeIP' # google documents spreadsheet name
>     USERNAME = 'your_username_here' # google/gmail login id
>     PASSWD = 'your_password_here' # google/gmail login password
>     BASE_DIR = '/tmp/' # Base Directory to locally save your IP info
>                        # trailing slash required!
>     IP_WEBSITE = 'www.whatismyip.org'
>     #IP_WEBSITE = 'whatismyip.everdot.org/ip' # alternate website
>     
>     ## Function Definitions
>     
>     def StringToDictionary(row_data):
>       result = {}
>       for param in row_data.split():
>         name, value = param.split('=')
>         result[name] = value
>       return result
>     
>     def load():
>       import gdata.spreadsheet.service
>       gd_client = gdata.spreadsheet.service.SpreadsheetsService()
>       gd_client.email = USERNAME
>       gd_client.password = PASSWD
>       gd_client.ProgrammaticLogin()
>       return gd_client
>     
>     def updateIP(ip):
>       import time,string
>       gd_client = load()
>       docs= gd_client.GetSpreadsheetsFeed()
>       spreads = []
>       for i in docs.entry: spreads.append(i.title.text)
>       spread_number = None
>       for i,j in enumerate(spreads):
>         if j == SPREADSHEET_NAME: spread_number = i
>       if spread_number == None:
>         return 0
>     
>       key = docs.entry[spread_number].id.text.rsplit('/', 1)[1]
>       feed = gd_client.GetWorksheetsFeed(key)
>       wksht_id = feed.entry[0].id.text.rsplit('/', 1)[1]
>       feed = gd_client.GetListFeed(key,wksht_id)
>       thetime = time.strftime('%I:%M%p')
>       thedate = time.strftime('%m/%d/%y')
>       entry = gd_client.InsertRow(StringToDictionary('date='+thedate+' time='+thetime+' ip='+ip),key,wksht_id)
>       return 1
>     
>     
>     ## Executed Code
>     
>     if os.path.exists(BASE_DIR+'CheckIP'): os.remove(BASE_DIR+'CheckIP')
>     os.system('wget '+IP_WEBSITE+' -t 2 --output-document='+BASE_DIR+'CheckIP')
>     fh2 = open(BASE_DIR+'CheckIP','r')
>     ip2 = fh2.read()
>     fh2.close()
>     
>     if os.path.exists(BASE_DIR+'CurrentIP'):
>       fh1 = open(BASE_DIR+'CurrentIP','r')
>       ip1 = fh1.read()
>       fh1.close()
>     else:
>       ip1 = ''
>     
>     
>     
>     if ip1 == ip2: pass
>     else:
>       res = updateIP(ip2)
>       if res == 0: raise 'Please Create a Spreadsheet named \''+SPREADSHEET_NAME+'\' in googleDocs.'
>       else:
>         fh = open(BASE_DIR+'CurrentIP','w')
>         fh.write(ip2)
>         fh.close()
> 
> Edit the USERNAME and PASSWD to match your gmail login info.  
This file can be saved to the directory of your choosing, but for this example lets put it in ~/Documents/  
  
Make the file executable.  
3) Log onto your gmail account and create a new **spreadsheet**. If you've never done this before, click on 'Documents' at the top of your gmail account, click 'new > spreadsheet'. In the spreadsheet, the first row is where the names of the colums go. Name cells A1,B1 and C1 'ip','date','time'. They can be placed in any order but use all lower case.  
  
The top should look like this:  
Save the spreadsheet as '**MyHomeIP**'. (again case matters, this can be changed easily to something different if you want to change SPREADSHEET_NAME in the python script).  
  
At this point you can test that the script works by running  
If you look in /tmp you should see the files CurrentIP and CheckIP. Also you can look at your google documents file and see if it sent the information.  
  
4) Now that you know the script is working, make a cron job to check if your IP has changed.  
  
Add this line to the file  

>     
>     
>     # m h  dom mon dow   command
>     59 * * * * /usr/bin/python /home/your_username/Documents/googleIP.py
> 
> This will check at the 59th minute of every hour if your IP has changed. If you want to set it to check less frequently, setting the second * to a number 0-23 will cause it to update daily.  
  
I hope this works for you as it has been very useful to me. 

  


##  Re: HOW TO: Change your GL Text Screensaver 

> I see this has come up several times so I will post my changes. This displays the time on the screen in the format:  
  
First I changed to the screensaver directory:  
  
cd /usr/share/applications/screensavers   
  
Then I copied the text screen saver  
sudo cp gltext.desktop gltime.desktop  
  
Then I edited the time screen saver, deleting everything and replacing it with the text below.  
sudo nano gltime.desktop   
  

>     
>     
>     [Desktop Entry]
>     Encoding=UTF-8
>     Name=GLTime
>     Comment=Displays a few lines of text spinning around in a solid 3D font. The text can use strftime() escape codes to display the current date and time. Written by Jamie Zawinski; 2001.
>     TryExec=gltext
>     Exec=gltext -root -front -text '%A%n%d %b %Y%n%l:%M:%S %p'
>     StartupNotify=false
>     Terminal=false
>     Type=Application
>     Categories=Screensaver;
>     OnlyShowIn=GNOME;
>     Name[en_US]=xxGLTime.txt
> 
> Control-O to save and Control-X to exit out of the editor. Then go to Preferences->screensaver->GLtime should be listed.  
  
For more options you can type  
man gltext  
":q" to exit out of that.  
  
Still very disappointed with the lack of a simple screen saver in Linux. Even the xscreensaver package has a ton of great choices but nothing simple. I have seen several requests for the Windows marque type of screen saver. I just want something that displays the time or some text and moves it in different positions on the screen. This bounces it all over the place. ("-no-spin" didn't seem to help) Even after following these directions to the letter I haven't been able to get things working. It's quite strange. I agree that a simple marque type screen saver is a somewhat simple oversight, but would be so helpful, when I was still working in Windows I often used it to keep a long-term to-do list so I would keep it memorized from constantly reading it whenever I wasn't using my laptop. 

  


Hi,   
I wanted to customize Gltext screen saver to display the Rhythmbox current song infos.  
Thanks for the help I got from this forum, it helped me much to findout how to do it.

I simply copied the /usr/share/applications/screensavers/gltext.desktop to /usr/share/applications/screensavers/glrb.desktop, edited it and now it's ok.  
Here are the commands :

sudo cp /usr/share/applications/screensavers/gltext.desktop /usr/share/applications/screensavers/glrb.desktop  
sudo gedit /usr/share/applications/screensavers/glrb.desktop

#I modified the line starting with "Name"  
Name=GlRb   
#I modified the line starting with "Exec" :  
Exec=/usr/lib/xscreensaver/gltext -root -program "rhythmbox-client --print-playing-format '%ta - %at\n%tt\n(%ag)'|iconv -fUTF-8 -tISO8859-15"

#Save and go to your screensavers settings panel. It should work fine!

You can check the rhythmbox-client man page for formats if you want to display some other infos. My format displays :  
Artist - Album  
Title  
(Genre)

I have piped the output of rhythmbox-client to iconv as I'm french and have a lot of unicode chars in my id3 tags. Maybe you'll have to adapt to your own language.

Hope it will help someone

  


> If you are afraid of the command line, then you can try a little different track to get virtually the same result.   
1\. Navigate to your filesystem (Click on your home screen and then the left arrow next to your user name near the top. Do it until it says file system or just click on it in the left hand list)  
2\. Now click on view "Show hidden items"  
3\. Now click on "usr" and then "share" and then "applications" and then "screensavers"  
4\. Right click on GLText and select copy to desk top.  
5\. Minimize the window.  
6\. on the desktop, right click and rename the file to GLTime.  
7\. Right click on GLTime and select properties.  
8\. delete everything in the "command" line  
9\. copy and paste this into the command line: gltext -root -front -text '%A%n%d %b %Y%n%l:%M:%S %p'  
10\. delete everything in the "Comment" line  
11\. Paste the following into the Comment line: Displays a few lines of text spinning around in a solid 3D font. The text can use strftime() escape codes to display the current date and time. Written by Jamie Zawinski; 2001.  
12\. Click on "Close"  
13\. Cut the GLTime file and paste it in the screen saver folder.  
14\. it should appear in the list of screen savers.  
  
Warning: The Preceding directions are for recovering Windows users. Long term Linux users should not attempt to follow them. Ok.. that sounded all NICE until we got to the ' user , share , application - Screen saver.. then PICK GL Text , RIGHT CLICK. which mine does not allow. I get the same pop up after clicking on Screen saver as I do if I just used the ICON for screen saver. the LIST of Screen Savers but no ability to Right Click anything. 
