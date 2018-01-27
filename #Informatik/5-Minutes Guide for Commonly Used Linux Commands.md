# 5-Minutes Guide for Commonly Used Linux Commands

_Captured: 2015-11-22 at 13:24 from [www.programcreek.com](http://www.programcreek.com/2013/03/my-commonly-used-linux-commands-in-ubuntu/)_

I'm not a serious Linux user, but sometimes I need to use Linux. In a long time, I frequently searched a limited number of Linux commands. So I think it is a good idea to list those frequently-used ones and remember them finally. This definitely improved my work effectiveness.

Here is my list.

**1\. cp/scp**

cp all files with ".extention" as extension to the garget directory.
    
    
    cp *.extension /target/directory
    

scp a remote directory to local:
    
    
    scp -r user@your.server.com:/path/to/foo /home/user/dir
    

**2\. grep**

Search 'keyword' in file
    
    
    grep   keyword file
    grep  'keyword' file
    grep  "keyword" file
    

Find environment variables that contain 'keyword".
    
    
    env | grep 'keyword'
    

Recursively search "keyword" in current directory.
    
    
    grep -r "keyword" *
    

Recursively search "keyword" in a target directory.
    
    
    grep -r "keyword" /a/target/directory/
    

Match only those lines that do NOT contain "keyword":
    
    
    grep -v "keyword" /path/to/file
    

Match only .php files:
    
    
    grep -r --include=*.php "keyword" ./
    

**3\. find**

Find the Main.java file in current directory (including all sub-directories).
    
    
    find * -name "Main.java"
    

**4\. zip/unzip**

zip all files under current directory.
    
    
    zip abc.zip *
    

Unzip all files to current directory.
    
    
    unzip abc.zip 
    

Extract a tar using gzip
    
    
    tar -xzf file.tar.gz
    

Create a tar using gzip. For example if you are in directory /var/www/html/, and want to zip a directory under /var/www/hmtl, you can use the following command:
    
    
    tar -czf directory_name.tar.gz directory_name
    

**5\. Environment Variable**

Set environment variable.
    
    
    export PROJECT_PATH=/home/name/project/
    

If a variable already exists, you can connect it with the new value.
    
    
    export PATH=$PATH:/home/name/project/
    

If you don't have root access to a machine, you can not change environment variable permanently. You can put all the variables you want to set in a file. And then run "source".
    
    
    source file
    

**6\. LAMP Related**

Start apache server
    
    
    sudo /usr/sbin/apache2ctl start
    

Actually, here I need to remember the apache2ctl. I can use the following to find out where it is:
    
    
    which apache2ctl
    

Restart Apache2 on Ubuntu 14
    
    
    sudo service apache2 restart
    

Start MySQL
    
    
    sudo service mysql start
    

**7\. Java Development**

Install Java: http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html  
Install Eclipse: http://colinrrobinson.com/technology/install-eclipse-ubuntu/ (Note: last step is to drag the icon to launcher!)

Open GUI file browser via command line
    
    
    nautilus . &
    
