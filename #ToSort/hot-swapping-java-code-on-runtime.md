# Hot Swapping Java Code on Runtime

_Captured: 2017-04-14 at 20:41 from [dzone.com](https://dzone.com/articles/hot-swap-java-bytecode-on-runtime?edition=290908&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-14)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943538%26PluID%3D0%26ord%3D%255Btimestamp%255D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943538%26PluID%3D0%26ord%3D%255Btimestamp%255D).

If you are a Java enterprise application developer, you must know the pain of **redeploying** your code changes on your local server running inside your IDE (or externally) after making some smaller changes. You cannot always take the luxury to redeploy every change you make once in a while to see the output in your APIs, since redeployment requires your server to restart or reloading your whole enterprise application. And every redeployment takes around **4 to 9 mins** on an average, depending on the size of your application and the infrastructure of your machine. It is even more devastating to see a web developer next to you writing and redeploying his/her changes just in few seconds to see the output in the browser instantly. And you can't do the same with your Java stack, eh!!

Well, on a serious note, consider that there are **10 developers** working in your organization. Each developer is working **8 hours** a day, their average annual wage is **₹500,000** and he/she does **4 redeployments per hour** on an average, and the average time taken by the system is **5 mins per redeployment**. Interestingly, each developer is wasting **2.67 hours** a day just in redeployments, which is costing the organization around **₹16,70,400 **annually for all 10 developers for doing nothing worthy of his/her time.

Well, there are ways to save this time and invest it in other, more productive work. There is a tool available in the market called [JRebel](https://zeroturnaround.com/software/jrebel/). It is a good commercial tool if one can afford. However, if you are an open-sourcist, there is a promising alternative to JRebel, which is **[DCEVM](https://dcevm.github.io/)** (_Dynamic Code Evolution Virtual Machine_) along with **[HotswapAgent](https://github.com/HotswapProjects/HotswapAgent/releases)**. And we are going to see hotswapping of Java code on runtime using these two tools.

DCEVM is a _modified Java HotSpot,_ which allows you to _redefine the classes at runtime_ in your JVM. Hence, we need to _patch_ this modified Java HotSpot version to our existing JVM on our system.

## Install DCEVM

Download the latest **[release](https://dcevm.github.io/)** of DCEVM and patch your current JVM installed in your system. For reference, I am using Java 8. DCEVM also supports Java 7.

Once you download the JAR file, run the following command to start the installer:

`java -jar DCEVM-light-8u112-installer.jar`

The installer will automatically detect your JVM directory. If not, then select your Java installation directory and click the "**Install DCEVM as altjvm**" and "**Replace by DCEVM**" buttons.

![DCEVM Installer](https://dzone.com/storage/temp/4853400-4-hs.png)

> _And you're done! This will patch your JVM with DCEVM._

To validate the installation, run:

`java -version`

It should output something like:

Note that there is `Dynamic Code Evolution 64-bit Server VM` instead of `Java HostSpot(TM)` on the last line. This means you have successfully patched DCEVM in your JVM.

Next, we are going to download and configure HotswapAgent. HotswapAgent is responsible for reloading resources and framework configurations. In the other words, it supports the reloading of classeses/Spring bean definitions after changes occur to them.

## **Download HotswapAgent**

Download the latest **[release](https://github.com/HotswapProjects/HotswapAgent/releases)** of HotswapAgent and put _hotswap-agent*.jar_ in **any location** on your disk.

## Run Configurations

Now that we have both tools in place, we need to configure the location of _hotswap-agent*.jar_ as _javaagent_ and DCEVM as _altjvm_ in the VM arguments to the JVM in our Run Configurations. For reference, I am using STS (Spring Suit Tools) Eclipse. It supports any IDE/Server or command line.

You need to configure following line in VM arguments to the JVM in Run Configurations:

Here, note that path of **hotswap-agent*.jar** on my system is **/home/cybercode/tools/hotswap-agent-1.1.0-SNAPSHOT.jar**. _Replace the path where you have saved this JAR file_.

To open Run Configurations in Eclipse, go to _Run > Run Configurations. _If you are running your Java application with embedded Tomcat, you can configure the VM arguments here.

![Tomcat Run Configurations](https://dzone.com/storage/temp/4853610-6-hs.png)

> _Tomcat Run Configurations_

And if you are running your Java application as Spring Boot application, then you can select your Spring Boot app and pass the VM arguments in the same place.

![Spring Boot App](https://dzone.com/storage/temp/4853628-7-hs.png)

> _Spring Boot App_

That's it. All the setup is done. Now, it's time to run the application and test the configurations.

## Run Your Application to Hot Swap Java Code

Now that we have done all the configurations, let's start the server and change some code and see the changes instantly.

For reference, I am running my application on an embedded Tomcat Server in my STS (Eclipse) IDE. Once you run the server, you can observe from the logs in the console to see that the `HOTSWAP AGENT` plugin is loaded in the Tomcat container.

![Hotswap Agent log](https://dzone.com/storage/temp/4853661-screenshot-from-2017-04-03-21-59-58.png)

> _Hotswap Agent log_

Once the server starts. I am calling an API where in my code I have printed `Calling my API...` on the console.

![Image title](https://dzone.com/storage/temp/4853676-1-hs.png)

Next, I have modified the print statement to `Calling my API again after some changes!!` and saved and built my code. There it goes. You can observe in the following snapshot that, instead of redeploying the whole application, the DCEVM hot swapped the affected classes in the JVM just within **1 to 3 seconds**. And you can see the modified output on the console as following.

![Classes hot swapped.](https://dzone.com/storage/temp/4853682-2-hs.png)

> _Classes hot swapped._

So, that's it. It has hotswapped my Java code just in **1 to 3 seconds**. Overall, a very useful and promising tool.

_**TIP**: _Uncheck the 'Build Automatically' option in the Project Menu in Eclipse. After making changes in your code, to hotswap classes, press Ctrl+B to build the project. After the build event, it will automatically hotswap the classes. But if you keep the 'Build Automatically' option checked, it will hotswap on every save event.

## An Alternative: Spring Loaded

As an alternative, I have also given [Spring Loaded](https://github.com/spring-projects/spring-loaded) a try. It's an open source tool that does the same job. It worked fine with my smaller Spring Boot application, however, it could not hold up when faced with the larger enterprise application. If you also want to give it a try, you can download the latest [release](https://repo.spring.io/list/libs-snapshot-local/org/springframework/springloaded/1.2.6.BUILD-SNAPSHOT/) of the Spring Loaded JAR and place it in your favorite location. Then, pass the following VM arguments to the Run Configurations and follow the same steps as above.

This would work the same way as DCEVM and HotswapAgent. However, I found DCEVM and HotswapAgent to be more convenient over Spring Loaded due to their stability. What do you think? Let me know in the comments below.

And if you find this post helpful, do share it with others.

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943536%26PluID%3D0%26ord%3D%255Btimestamp%255D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943536%26PluID%3D0%26ord%3D%255Btimestamp%255D).

Opinions expressed by DZone contributors are their own.
