# How to Use the .htaccess File Effectively

_Captured: 2018-08-28 at 14:41 from [dzone.com](https://dzone.com/articles/how-use-htaccess-file?edition=387231&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-08-27)_

The .htaccess file is the configuration file for web servers running the Apache Web Server. It is very useful for configuring and redirecting the Apache Web Server file system.

Keep in mind that the .htaccess file will be in a hidden format. No one can see it directly via the URL.

There are many uses for the .htaccess files. Here, I will discuss creating them and their uses.

## **Creating an .htaccess File**

Open any text editor and save the file with name `.htaccess`. Enable the `mod_rewrite` extension in the php.ini file in the Apache Web Server Configurations.

## **Uses for .htaccess**

### **1\. Disable Directory Listings**

Include the following code if you want to disable the folder files listings.

### **2\. Error Pages**

You can set error pages for the particular error.

Example :

**If you want to turn on Rewrite Rules in the Apache Server, you have to write:**

`RewriteEngine on `

If you want to turn off this rule, change the value to off.

### **3\. Domain Redirection**

To permanently redirect yourdomain.com to www.yourdomain.com, add the following code:

### **4\. Subdomain Redirection**

You can also perform subdomain redirection mapping to the folder. Here www.yourdomain.com is connecting to the `website_folder` folder.

Here subdomain.yourdomain.com is connecting to the `subdomain_folder` folder.

### **5\. Old Domain Redirection**

The .htaccess code for redirecting an old domain (old.com) to a new domain (new.com).

### **6\. Friendly URLs**

Friendly and informative URLs help in search engine rankings. URLs are a very important part of the search engine optimization process.

### **Profile URL**

_http://gurutechnolabs.com/profile.php?username=test_

into

_http:// gurutechnolabs.com/test_

### **Friends URL **

_http://gurutechnolabs.com__/friends.php?username=test_  
to  
_http://gurutechnolabs.com/friends/test_

### **Friends URL With Two Parameters **

_http://gurutechnolabs.com/friends.php?username=test&page=2_

to

_http://gurutechnolabs.com/friends/test/2_

### **7\. Hiding File Extension**

Say you don't want to display an extension a web page.

Example :

_http://www.yourdomain.com/index.html_

to

_http://www.yourdomain.com/index_

Just add the following code :

## **Use of .htaccess for Improving Website Speed and Performance**

### **1\. Enable Compression:**

Compression is very useful for reducing the size of web pages.

There are two compression options :

  * Deflate: Very easy to set up.
  * GZIP: More powerful, You can pre-compress the content.

To enable Deflate mode, add following code in your .htaccess

Enable GZIP compression mode

### **2\. Add Expire Headers: Enable Browser Caching **

The Expire header is used to cache data from the browser. It is helpful to speed up webpage because webpage can retrieve data from the browser so no need to get it from the server that reduces HTTP requests.

### **3\. Enable Keep-Alive to Decrease HTTP Requests**

By enabling Keep-Alive, your web server is telling the web browser that there is no need to make a separate request for each file it retrieves on a site. Also, make sure to code it in such way that it will reduce HTTP requests.

### **4\. Prevent Spam Bots From Crawling Your Website**

Sometimes the page load speed of your website can be reduced by the bandwidth you have available on your hosting plan. Sometimes spam boats take most of your bandwidth and your website becomes slowly.

So, it's helpful to prevent spambots.

So, we can use the .htaccess file for many purposes.

**Happy coding!**
