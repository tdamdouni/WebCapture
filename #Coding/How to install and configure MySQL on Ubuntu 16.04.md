# How to install and configure MySQL on Ubuntu 16.04

_Captured: 2016-12-03 at 22:36 from [tutorials.technology](https://tutorials.technology/tutorials/12-installing-mysql-on-ubuntu-16-04.html)_

# Introduction

MySQL is a very popular open-source database. Most of PHP application uses a MySQL database and even some python apps use it. It became more popular since facebook is using this database for their production environment, they have a [custom branch of this database](https://github.com/facebook/mysql-5.6).

# Step 1: Install MySQL from ubuntu repositories
    
    
    sudo apt-get update
    sudo apt-get install mysql-server
    

During the installation you will be asked for a root password. Try to use a secure and a new password for this high privilege user.

# Step 2: MySQL secure installation

After installing MySQL execute the mysql_secure_installation wizrd:
    
    
    sudo mysql_secure_installation
    

Since you need root MySQL permissions for running the wizard, enter the password that you used in the previous step. For most of this steps, you can accept everything but read it carefully.

## Bind address to localhost only

Now we are going to edit the my.cnf to improve configuration default, open with your favorite editor the file:
    
    
    sudo vim /etc/mysql/my.cnf
    

Since we assume that you are running a small application, .ake sure the the config _bind-address_ is set to _127.0.0.1_.We usually don't want to expose mysql port to outside except when we are using multiple database backends. If you need to share mysql, we recommend to use other setups like vpns or ssh tunnels.

## Disable unsecure function

Set the value of _local-infile_ to local-infile=0. This will disable file system access for users without file privileges to the database.

## MySQL Users Recommendations

Always avoid using root in your applications, since this user has a lot more privielegs than neccesary. You should create an user for each application and with restricted access to the database queries or tables.

As an example we are going to create a user for the tutorialstechnology database:
    
    
    create database tutorialstechnology;
    CREATE USER 'tutorials'@'localhost' IDENTIFIED BY 'securerandomandlongpassword';
    GRANT SELECT,UPDATE, INSERT ON tutorialstechnology.* TO 'tutorials'@'localhost';
    FLUSH PRIVILEGES;
    

Last commands are for creating an user called _tutorials_ with SELECT and UPDATE permission to the database _tutorialstechnology_. We don't give DELETE permission since out application uses logical deletes. If your application has a sqlinyection security bug, having a user without DELETE permission will avoid future headaches. Of course that with the update some user could do harm, but we need that in order to update values.

We don't recommend to execute the following, DON'T DO IT:
    
    
    GRANT ALL ON testDB.* TO 'tutorials'@'localhost';
    

With GRANT ALL a user could drop tables for example, we want to avoid that scenario.

For checking user permission execute:
    
    
    show grants for 'tutorials'@'localhost';
    

Some people recommend to change the root username, since it's a well know username that most of hacking tools will target.

# Step 3: Data directory initialization

For Ubunru 16.04 it's not required to initialize any directory if we did the step 1. However for other linux distributions we need to execute:

  * mysql_install_db for versions before 5.7.6
  * mysqld --initialize for 5.7.6 and later

# Step 4: Checking everything is working as expected
    
    
    sudo service mysql-server status
    

You should see the following after the _status_ execution:
