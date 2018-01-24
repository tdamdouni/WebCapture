# MQTT – Security

_Captured: 2017-12-04 at 13:34 from [www.lucadentella.it](http://www.lucadentella.it/en/2016/11/14/mqtt-sicurezza/)_

In the IoT they often don't give much importance to the **security **aspects of the communcation. Proof of this is that many of the latest [DDOS](https://en.wikipedia.org/wiki/Denial_of_Service) (_Distributed Denial of Service_) attacks [have been launched](http://thehackernews.com/2016/09/ddos-attack-iot.html) by hacked Internet-connected _smart devices_.

In the previous posts, you learned how to configure **mosquitto** to receive messages _published_ by clients and to forward them to all the _subscribers_. Today I'm going to show you how to configure the application security of your MQTT _broker_.

This post is about the **standard** settings mosquitto offers. On the Internet you can find several _plugins_ to extend its functionalities and to implement advanced security settings, like [storing accounts in different backends](https://github.com/jpmens/mosquitto-auth-plug) or using [json web tokens](https://github.com/cyrilcc/mosquitto_auth_plugin_jwt).

#### Authentication

The first step to make our _broker _secure is to require clients who are connecting to authenticate themselves. In this way, only authorized clients can send/receive messages.

Open the **mosquitto.conf** file and, first of all, disable the anonymous access setting to **false **the corresponding parameter.

![mqtt-sec01](http://www.lucadentella.it/blog/wp-content/uploads/2016/11/mqtt-sec01.jpg)

When you change a setting in the file, make sure that the hash (**#**) character is **not** present at the beginning of the line, otherwise the parameter is not considered

The list of the users authorized to connect to the broker is defined in a dedicated file. The name of this file is configured with the **password_file** parameter (in the example below, the file containing users and passwords is named "pwdfile", stored in the same folder of mosquitto):

![mqtt-sec02](http://www.lucadentella.it/blog/wp-content/uploads/2016/11/mqtt-sec02.jpg)

Using the **mosquitto_passwd.exe** command you can create (**-c**) the file and add a new user ("luca"). The command will ask to type the user's password twice:

![mqtt-sec03](http://www.lucadentella.it/blog/wp-content/uploads/2016/11/mqtt-sec03.jpg)

> _If you need to add additional users, you can run the command again, without the -c option:_
    
    
    mosquitto_passwd.exe pwdfile sara

Let's try the new configuration. First run mosquitto specifying the configuration file (**mosquitto.exe -c mosquitto.conf**), then try to publish a message as you learned in the previous tutorials:

![mqtt-sec04](http://www.lucadentella.it/blog/wp-content/uploads/2016/11/mqtt-sec04.jpg)

> _You can see that the connection is refused because of the client is not authorized: we indeed didn't specify any users and anonymous access was disabled._

Try to run the command again, this time specifying the correct user and password and you'll find that the message will be correctly published:
    
    
    mosquitto_pub.exe **-u <utente> -P <password>** -t home/bedroom/temp -m 19

#### Authorization

After having defined **who** can connect to the _broker_, it's now time to define **what **a user can do once connected. Again, the configuration of the ACLs (_access control lists_) is in a dedicated file, whose name is configured with the **acl_file **parameter:

![mqtt-sec05](http://www.lucadentella.it/blog/wp-content/uploads/2016/11/mqtt-sec05.jpg)

> _The ACL file contains blocks with the following structure:_

  * the first line, **user** <nomeutente>, that defines the user the following ACLs are applied to
  * one or more lines, **topic **<read|write|readwrite> <nometopic>, that define which actions the user above can do on the specified topic

Let's see an example, a file in which we define a user (**writeclient**) that can send messages to the secure/data topic and a user (**readclient**) that can read those messages. Both the two users can in addition send an receive messages from all the open/# topic (for an explanation about the use of _wildcards_ read my [previous post](http://www.lucadentella.it/en/2016/11/08/mqtt-topics/)):

![mqtt-sec06](http://www.lucadentella.it/blog/wp-content/uploads/2016/11/mqtt-sec06.jpg)

> _(lines starting with # are comments)_

Let's now try to send a message using the **readclient **user, who's not allowed to do that:

![mqtt-sec07](http://www.lucadentella.it/blog/wp-content/uploads/2016/11/mqtt-sec07.jpg)

The client doesn't get any error message, but in the mosquitto logs you can clearly see that the _publish _command was denied, consistent with the configured ACLs.

If instead the right users are specified, the message is correctly routed from the publishing client to the subscribing one:

![mqtt-sec08](http://www.lucadentella.it/blog/wp-content/uploads/2016/11/mqtt-sec08.jpg)

#### Conclusions

It's very important to secure our _broker_, especially if it's connected to a public network (for example if it's available on the Internet). In today's blog post you learned how to define users and grants in mosquitto.
