# How to Send Emails Using Swift Mailer

_Captured: 2017-03-12 at 00:49 from [dzone.com](https://dzone.com/articles/how-to-send-emails-using-swift-mailer?oid=twitter&utm_content=bufferdc7d3&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

Ever wonder how you can send newsletters, confirmation emails, order details, and other emails to your customers or subscribers using PHP? Given the recent discovery of [security vulnerability in PHPMailer](https://legalhackers.com/advisories/PHPMailer-Exploit-Remote-Code-Exec-CVE-2016-10033-Vuln.html), the PHP development community is on the lookout for alternatives of this extremely useful library.

A very likely option is Swift Mailer, a PHP library created by Chris Corbyn and maintained by [Fabien Potencier](https://twitter.com/fabpot). Swift Mailer is a Symfony component that could also be used independently in PHP projects. In this article, I will introduce Swift Mailer and will highlight a simple use case of the library in which I will send an email using Swift Mailer.

## Why You Shouldn't Use mail()

At this point, you might wonder why I am not talking about the default PHP `mail()` method. `mail()` is an extremely basic method and does not support authentication. Additionally, you cannot send attachments through this method. However, the main problem with the method is that it cannot send emails in a loop because it opens and closes sockets every time an email is sent.

In contrast, Swift Mailer offers:

  * SMTP authentication.

  * HTML emails and attachments.

  * Bulk emails.

  * Read receipts/greeting messages.

  * Ease for integrating and using.

## How To Install Swift Mailer

Composer is a prerequisite for installing Swift Mailer. Thus, you must first get Composer from the official website and install it. In order to avoid all this hassle, I opted for a PHP application hosted on a Cloudways server. Since Composer comes pre-installed on the [Cloudways](https://www.cloudways.com/en/php-cloud-hosting.php) Platform, I could easily skip this step and move on to the next step.

Once this is done, you can install Swift Mailer by simply running the following command:

This will install the latest stable release of Swift Mailer in your project. You can also clone it from GitHub. To do this, first go into your project folder and run this command:

After installing Swift Mailer, you need to load it in your file. I will explain this later on when I make a class and methods for Swift Mailer.

## Create A Simple HTML Form

First of all, I will create a simple form to get the four basic information items (subject, sender's email address, recipient's email address, and message body) about the emails.

For this, I will create an `index.php` file and add a simple form in the body of the HTML.
    
    
    <form class="form-horizontal" action="index.php" method="post" enctype="multipart/form-data">
    
    
      <label class="col-md-4 control-label" for="textinput">Add Subject:</label>  
    
    
      <input id="textinput" name="subject" type="text" placeholder="add subject" class="form-control input-md">
    
    
      <span class="help-block">help</span>  
    
    
      <label class="col-md-4 control-label" for="textinput">Send To:</label>  
    
    
      <input type="email" id="textinput" name="email" type="text" placeholder="add recipient email" class="form-control input-md">
    
    
      <span class="help-block">help</span>  
    
    
      <label class="col-md-4 control-label" for="textarea">Message</label>
    
    
        <textarea class="form-control" id="textarea" name="message">default text</textarea>
    
    
      <label class="col-md-4 control-label" for="filebutton">Attach file</label>
    
    
        <input name="file" class="input-file" type="file">
    
    
      <label class="col-md-4 control-label" for="singlebutton">Click to Send Mail</label>
    
    
        <button type="submit" name="submit" class="btn btn-primary">Send</button>

The form action is set to **index.php** itself and the method must be **post.** The form is very barebones and only collects the essential information from the user. It also contains basic input fields to gather data from the users.

## Create the Swift Mailer Class

The next step is to create a MailClass to get the email response. All the arguments are passed from `index.php`. I will first create the MailClass and then define a sendMail method in the class.

The MailClass contains a simple function with four arguments: $subject, $sendto, $body, $targetpath.

`Swift_SmtpTransport` is used to create a transport instance. `Swift_Message` is the object of email, `setTo()` method holds the recipient email address, `setSubject` holds the subject of the email, `setBody()` contains the whole message of the email, and lastly, `setFrom()` contains the sender email. In the next line, I set a condition to check whether the target path is empty and then attach the files to the email. Finally, the email will be sent by the `send()` method.

Please note that I have set up an optional argument `$targetpath = null` because even if you do not attach files to an email, you will still be able to send it.

## Initialize Swift Mailer and Send The Email

Now, coming back to `index.php` file, I will initialize Swift Mailer by requiring the `autoload.php` file. In addition, I will require `mailclass.php` file. On clicking **Send**, all the values will be passed in PHP variables and the file upload will be handled by defining what extensions are allowed (for instance, PDF, TXT, or PNG). Finally, I will instantiate `MailClass` and pass all the values to `sendMail()` function to send the email.

Simply copy the following code and paste it at the top of **index.php**.

Now open the application in the browser and test it by sending an email with and without attachment. Enter all the details and click the **Send button**.

![Image title](https://dzone.com/storage/temp/4280689-image01.png)

> _Image title_

Swift Mailer keeps track of the number of emails being sent. I have set a condition in the `sendMail()` method that increments the variable `$result`. Simply echo this variable:

This snippet will result in the following result:

![Image title](https://dzone.com/storage/temp/4341792-image00.png)

> _Of course, you should check your inbox to verify that you have, indeed, received the email!_

![Image title](https://dzone.com/storage/temp/4280695-image02.png)

You can test the live application demo [here](http://phpstack-21306-71265-206743.cloudwaysapps.com/).

## SMTP Transport Settings

You can also use other SMTP services, such as Gmail, Hotmail, SendGrid, etc. to send emails from the associated account. You just need to put in SMTP credentials in transport instance.

Try replacing the default transport instance with the following:

### Mandrill

### Gmail

Note: For sending emails from Gmail SMTP, you need to Turn On the access of less secure apps from account settings. Next, go to [this URL](https://accounts.google.com/DisplayUnlockCaptcha) and allow Google to access your application.

### Hotmail

## Conclusion

In this article, I introduced Swift Mailer and created a simple class and methods to send an email. You could easily implement advanced features and automate the process of sending system generated emails. Swiftmailer is a secure email library. I personally recommend that you send emails using Swift Mailer in all your future PHP projects.

If you have a question or would like to contribute to the discussion, do leave a comment below!
