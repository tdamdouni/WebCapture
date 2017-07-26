# Exposing Business Logic as REST API

_Captured: 2017-05-21 at 12:37 from [dzone.com](https://dzone.com/articles/exposing-business-logic-as-rest-api?edition=299092&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-20)_

[Start coding today](https://dzone.com/go?i=155124&u=https%3A%2F%2Fgoo.gl%2FmNOkDt) to experience the powerful engine that drives data application's development, brought to you in partnership with [Qlik](https://dzone.com/go?i=155124&u=https%3A%2F%2Fgoo.gl%2FmNOkDt).

In this article, I would explain to my fellow readers a simple way to expose business logic as a REST API.

The pre-requisites are:

  1. An IDE (it can be NetBeans or Eclipse). If you are using Eclipse, please download the enterprise version of Eclipse, or if you choose to work with the normal Eclipse version then you have to separately set up Eclipse for an enterprise project.
  2. Maven, as I will be using Maven to build the project.
  3. Apache Tomcat. I have used Apache tomcat 7.
  4. The jars for jersey-core, jersey-server, and jersey-build.

To my readers who will be using the normal Eclipse version, I will first explain how you can set up your Eclipse for a web application. I have used **_Eclipse Mars 4.5.1_ **version.

**Step 1**: First go to `Help -> Install new software`. It looks something like this:

![screenshot-1](https://soumyajit2016.files.wordpress.com/2016/04/screenshot-1.png?w=1140)

**Step 2**: Click on `Check for updates`. As soon as you click here, it will load the next screen where you have to specify your Eclipse's version release. Check the screenshot:

![screenshot-2](https://soumyajit2016.files.wordpress.com/2016/04/screenshot-21.png?w=1140)

  1. Select your version of Eclipse from the `Work with` drop down. Once the version is selected, Eclipse will list the components within the release.
  2. Select what component of the version you want to install.
  3. Then click on `Next`. Once you do that, it will take some time to install the components. Once the installation finishes, your Eclipse is ready to create web applications.

**Step 3**: Click on `File -> New -> Java Project`. Please check the following screenshot:

![screenshot-3](https://soumyajit2016.files.wordpress.com/2016/04/screenshot-3.png?w=1140)

> _Step 4: Create a Dynamic Web Project from here:_

![screenshot-4](https://soumyajit2016.files.wordpress.com/2016/04/screenshot-4.png?w=1140)

  1. Under new project, go to the `Web` section.
  2. Click on`Dynamic Web Project`.
  3. Click on _Finish_.

The following web directory structure will look something like this:

![Screenshot-5.png](https://soumyajit2016.files.wordpress.com/2016/04/screenshot-5.png?w=1140)

**Step 5**: Download your choice of application server. I have used Tomcat 7.0 for this application. You can download it from [Apache Tomcat version 7.0](http://tomcat.apache.org/download-70.cgi). Once downloaded, just copy all the content into the Library directory. Not a necessary step but I prefer to do it this way. Use the following command to perform this task for Linux and Unix systems: _`sudo cp -r Downloads/Tomcat/ Library`_. For Windows, you can copy it into any folder.

**Step 6**: Next click on _'Preferences.'_

![Screenshot-6](https://soumyajit2016.files.wordpress.com/2016/04/screenshot-6.png?w=1140)

Once you've clicked _Preferences, _Eclipse will open up the preferences dialog box from where you can go to the server section. Under the server section, you will get the option to set up the server when you click on the runtime environments.

![screenshot-7](https://soumyajit2016.files.wordpress.com/2016/04/screenshot-7.png?w=1140)

Click on **add** to configure a server. I already have Tomcat configured in the Eclipse system.

![screenshot-8](https://soumyajit2016.files.wordpress.com/2016/04/screenshot-8.png?w=1140)

![Screenshot-9](https://soumyajit2016.files.wordpress.com/2016/04/screenshot-9.png?w=1140)

> _Select your specific Apache Tomcat version._

  1. Enter the correct path for Apache Tomcat.
  2. Click on Finish.
  3. After the installation of the Tomcat server is done there will be a directory created in the Eclipse system for the servers. It will look something like this:
![Screen Shot 2016-04-19 at 3.49.32 pm](https://soumyajit2016.files.wordpress.com/2016/04/screen-shot-2016-04-19-at-3-49-32-pm.png?w=1140)

Click on Tomcat v7.0 Server at localhost.server. It will look something like this:

![Screen Shot 2016-04-19 at 3.51.05 pm](https://soumyajit2016.files.wordpress.com/2016/04/screen-shot-2016-04-19-at-3-51-05-pm1.png?w=1140)

By default the option would be set to **_"Use workspace metadata (does not modify Tomcat installation)" _**to **_"Use Tomcat installation (takes control of Tomcat installation)."_**

So your Tomcat is set up in your Eclipse. So if you start Tomcat on port 8080 you will have an option to login to the manager app to handle your applications from the server itself. It provides a portal for that by default. But you will not have access. For that you have to specifically define the roles, the username, and the password which you need to allocate it to the specific manager role. You can define the roles and the username and password for that in the tomcat-users.xml file under the server section in Eclipse. The following needs to be scripted down in the XML file:
    
    
     <user username="admin" password="admin" roles="manager-gui,manager-script,manager-jmx,manager-status,admin-gui,admin-script"/>

So the next time you open the manager-app UI, you just need to provide the username admin and password admin and you are in! The list of the applications will be listed infront of you.

Now you have the dynamic web project ready to be implemented.

**Step 7**: Now, since I am using Maven to build my project, you need to upgrade your project to a Maven project. For that you need to right click on_ project -> Maven -> Update Project _

![Screenshot-10](https://soumyajit2016.files.wordpress.com/2016/04/screenshot-10.png?w=1140)

Once it is updated, you can add the following dependencies in the _pom.xml_. You have to declare dependencies for:

  1. Jersey-core
  2. Jersey-server
  3. Jersey-bundle
  4. asm
  5. JSON

So, **_Jersey_** implementation provides a library to implement Restful web services in a Java servlet container and _**ASM**_ is an all purpose Java byte code manipulation and analysis framework. It can be used to modify existing classes or dynamically generate classes directly in binary form. Besides using these libraries, you also need to have the JSON library to parse the desired output in JSON format.

Here is how my pom.xml looks:
    
    
    <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    
    
           <artifactId>maven-compiler-pluginartifactId>
    
    
           <artifactId>maven-war-pluginartifactId>

You can get the dependency XML structure for the following jars from [here](http://mvnrepository.com/). It looks like the following:

![Screenshot-11](https://soumyajit2016.files.wordpress.com/2016/04/screenshot-11.png?w=1140)

I would prefer using dependency structures from here because you will understand the following versions of the jar that are currently compatible with Maven and the packages assigned to the following libraries. So you just need to pick up the dependency structure from here and paste it in the pom.xml.

So, now you have:

  1. Updated your Eclipse to support "Dynamic web projects."
  2. You have configured Apache Tomcat with Eclipse.
  3. You have updated your project into a Maven project.
  4. You have updated your pom.xml structure with all the dependencies so that you are ready to build your project.

So, once these are all done, I will start writing my servlets under the src directory under a package container.

![Screenshot-12](https://soumyajit2016.files.wordpress.com/2016/04/screenshot-12.png?w=1140)

So, as I mentioned in my last blog on REST APIs, you can access the following resources of an API over a URL.So let's get to talking about how can you implement REST services.

As I said, I have been using the Jersey implementation. The Jersey implementation makes it much easier to implement a REST API service. I have followed the _Agnostic application deployment model._ So JAX-RS provides a deployment agnostic abstract class Application for declaring the root resource and the provider classes. A web service may extend this class to declare a root resource and provider classes. So the Root Resource will be the point of contact or communication with the rest of the provider classes. The structure will look somewhat like this:

![Screenshot-13](https://soumyajit2016.files.wordpress.com/2016/04/screenshot-13.png?w=1140)

I have used the class _MyApplication_ as the root class. The MyApplication class extends to the _Application_ class.

So the _@ApplicationPath_ annotation allows you to access the root class as a URL. Now, as you can see, the `get class()` method returns the set of provider classes to the calling function. You can add as many provider classes inside the `get classes()`method as you need. The agnostic application jersey implementation helps deployment at class level, i.e. you can deploy the application without the servlets declared within the web.xml.

The implementation of the root class looks like the following:
    
    
         Set<Class<?>> set = new HashSet<>();

So, as you can see, there are two provider classes that I have declared in the CtoFService class and the FtoCService class. So in the two classes, I have implemented both ways that you can: 1) produce the API service in an XML format and as well as a JSON format; 2) implement in such a way so that I can use a query as well as a query parameter to access the REST API service. Here is an example of how you can do it:
    
    
         celsius = (fahrenheit - 32)*5/9;
    
    
         return Response.status(200).entity(result).build();
    
    
       return Response.status(200).entity(result).build();

For more details you can use my git hub [REST-API](https://github.com/Corefinder89/REST-APIs) link to get a better over view of how these REST APIs are functioning.

[Create data driven applications](https://dzone.com/go?i=155123&u=https%3A%2F%2Fgoo.gl%2FWwzwij) in Qlik's free and easy to use coding environment, brought to you in partnership with [Qlik](https://dzone.com/go?i=155123&u=https%3A%2F%2Fgoo.gl%2FWwzwij).
