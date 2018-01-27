# Setting up a Jenkins CI engine for embedded projects

_Captured: 2017-11-07 at 16:20 from [www.thingforward.io](http://www.thingforward.io/techblog/2017-11-03-setting-up-a-jenkins-ci-engine-for-embedded-projects.html)_

Welcome to the sixth part of our "embedded testing" series. From our former blogposts, you are now familiar with [PlatformIO](http://platformio.org) and its powerful features like unit testing, remote controlling and continuous integration. On the fifth embedded testing blogpost, we've been diving into Travis CI in order to automate build and testing processes, deployment of software artifacts to servers. CI tools like [TravisCI](https://travis-ci.org) and Jenkins services can completely automate build and testing processes, as well as deployment of software artifacts to servers ([and embedded, of course](http://www.thingforward.io/techblog/2017-09-18-embedded-testing-with-platformio-part-4-continuous-integration.html)). It would be nice to have something comparable for the world of IoT as well. TravisCI is a cloud solution, meaning it will always build on fresh servers (or better: containers), but remote. Maybe you'd want to have your builds running locally. Today we have chosen [Jenkins](https://jenkins.io/), a well-known CI service that's used often in software development processes, and show how to set it up on a RaspberryPi, in conjunction with [PlatformIO](http://platformio.org)

### Jenkins CI

Jenkins CI is an open source automation server, provides a magnitude of plugins to support building, deploying and automating your project. Easy installation, easy configuration, plugins, extensions and multiple platforms' compatibility makes Jenkins a great choice. And we're going to use it for our embedded projects as well! The physical setup we've been using consists on a RaspberryPi and a NodeMCU that is connected to RPi via USB. The above PlatformIO project is for NodeMCUs firmware, which will be built, uploaded and tested locally from Jenkins CI.

Let's plug in our RPi, login and start with the login to PlatformIO:
    
    
    $ pio account login
    <your login data>

It will be necessary to get & save our PIO Token - `PLATFORMIO_AUTH_TOKEN` flag - in order to authenticate the CI server later:
    
    
    $ pio account token
    <Output>
    PlatformIO Plus (https://pioplus.com) v0.10.11
    Password:
    Personal Authentication Token: xxxxxx11122233444aaabbbcccddee

Copy the token and store it somewhere else for later usage.

For using the Jenkins on RPi board, we need Java JDK-8. Please type this and select JDK-8 by giving the selection number:
    
    
    $ sudo update-alternatives --config java
      Selection      Path                                                   Priority
    ------------------------------------------------------------
       0            /usr/lib/jvm/java-7-openjdk-armhf/jre/bin/java          1063      Automatic
       1            /usr/lib/jvm/java-7-openjdk-armhf/jre/bin/java          1063      Manual
       2            /usr/lib/jvm/java-8-openjdk-armhf/jre/bin/java          1063      Manual
     * 3            /usr/lib/jvm/jdk-8-oracle-arm32-vfp-hflt/jre/bin/java   318       Manual

Now it is time to install Jenkins to our RPi, starting with making a new directory, then install Jenkins:
    
    
    $ mkdir jenkins && cd jenkins
    $ wget -q -O - https://jenkins-ci.org/debian/jenkins-ci.org.key | sudo apt-key add -
    $ sudo sh -c 'echo deb http://pkg.jenkins-ci.org/debian binary/ > /etc/apt/sources.list.d/jenkins.list'
    $ sudo apt-get update
    $ sudo apt-get install Jenkins

Now, Jenkins is installed and should automatically be running. For our demo setup we also place the Git Repository on the RaspberryPi, but this can of course be on GitHub, a hosted GitLab or some other repository server in your network. We put ours in `/opt/git`:
    
    
    $ mkdir /opt/git 
    $ cd /opt/git
    $ mkdir ci-with-platformio && chmod g+rwx ci-with-platformio
    $ ( cd ci-with-platformio; git init --bare --shared )

Now we have an empty, bare repository at `/opt/git/ci-with-platformio`. Since both repository and jenkins instance run on the same server, we're only cloning locally and need to take care of file system access rights to this directory. We'll put both our `pi` and `jenkins` users into the same group and give group rights to the directory. Additionally, we'd like to have jenkins build our project automatically whenever a git push occurs. Let's put a post-receive hook into the repo by:
    
    
    $ cd /opt/git/ci-with-platformio/
    echo '#/bin/bash
    /usr/bin/curl \
    --user <YOUR_USERNAME>:<YOUR_PASS> \ 
    -s \
    http://127.0.0.1:8080/git/notifyCommit?url=/opt/git/ci-with-platformio
    ' >hooks/post-receive
    $ chmod g+rwx hooks/post-receive

Good, now we need some code to work with :-) Let's take the code from the last blog posts about unit testing. It's at [github.com/emirez/ci-with-platformio](https://github.com/emirez/ci-with-platformio.git), and we can simply push this into our local `ci-with-platformio` repo:
    
    
    $ cd ~
    $ git clone https://github.com/emirez/ci-with-platformio.git
    $ cd ci-with-platformio
    $ git remote add local /opt/git/ci-with-platformio
    $ git push local
    $ cd ..
    $ rm -fr ./ci-with-platformio
    $ git clone /opt/git/ci-with-platformio
    $ cd ci-with-platformio
    $ # we can make changes here and push to the local repo (later)

For restarting Jenkins:
    
    
    $ sudo /etc/init.d/jenkins restart

Here is how your project looks like:
    
    
    $ tree
    ├── README.md
    ├── lib
    │   └── mod1
    │       └── src
    │                ├── mod1.cpp
    │                └── mod1.h
    ├── src
    │        └── main.cpp
    ├── platformio.ini
    ├── .travis.yml
    ├──test
    │        └── native
    │        ├── test_first.cpp
    │        ├── nodemcuv2
    └        └── test_main.cpp

By opening our browser and typing the following address, we will see the Jenkins CI interface at `http://<your_device_name_or_ip>:8080`

For our setup, it's `http://tfpi.local:8080`

Hint 1: Jenkins CI interface uses the language of your browser. If you want to change the language of the Jenkins CI, please change your browser language.

![Image 1: Jenkins CI UI](http://www.thingforward.io/fileadmin/user_upload/bp8/1.png)

If you already have an account, please login. Otherwise, please navigate to "Create an Account". After creating your account, you can login and see the next page.

![Image 2: Jenkins CI UI on 8080 Port](http://www.thingforward.io/fileadmin/user_upload/bp8/2.png)

> _To start with a new project, please click on New Item._

![Image 3: Jenkins CI New Item Initiation](http://www.thingforward.io/fileadmin/user_upload/bp8/3.png)

It is the new item page that allows us to select the type of the project that we will build and test automatically. After giving a name, select _Freestyle Project_ and click on OK.

The fine tuning parameters, environment variables, sketches and etc. should be specified now:

  * Type some information about the project under description.
  * Git project and it's path will be written under source code management.
  * Build triggers and build environment can be selected arbitrarily, you can basically set them as you.
  * Build sketches are the commands that you want to automatize. Please see the global environment flag `PLATFORMIO_AUTH_TOKEN`, set it to the token value that you obtained before by `$ pio account token` command.
  * Save and apply.
![Image 4: Jenkins CI Project Settings](http://www.thingforward.io/fileadmin/user_upload/bp8/4.png)

After every push to our local git repository, a new build will be started automatically due to the post-receive hook we set up above:
    
    
    $ cd ci-with-platformio-jenkins
    $ # change something ..
    $ git add .
    $ git commit -m "first Jenkins commit"
    $ git push

In order to see the build console output, please click on the arrow next to the project name:

![Image 6: Project build output on Jenkins](http://www.thingforward.io/fileadmin/user_upload/bp8/6.png)

> _Here is the console output:_

![Image 7: Console Test Output](http://www.thingforward.io/fileadmin/user_upload/bp8/7.png)

> _You can always build the project by clicking on Build now in the context menu of a project:_

![Image 8: Build now on context menu](http://www.thingforward.io/fileadmin/user_upload/bp8/8.png)

The weather icon shows the condition about your last builds. If it is rainy, that means there are some fails at your last 5 builds. If your last 5 builds are successful, then you will see the sun. Hint 2: Probably you see the blue ball whenever your builds are successful. You can paint it green by installing an extension to the Jenkins. To do so, please navigate to **Manage Jenkins > Manage Plugins** and install the **Green Balls** extension. Restart your Jenkins and see them in green color.

**Finalising today:** So what did we actually achieve? Using our PlatformIO's project template, we're able to automatise all the build & testing process, including the installation of Jenkins CI. However, devices can still be connected locally, i.e. a notebook or as in our setup, a RPi simulation our IoT integration farm. Remote function of PIO would be also used in order to reach the integration farm remotely. The goal of this topic is to getting deeper into Agile Embedded process. Every code push triggers a build and testing process, and ideally flashes firmware to some test devices, and runs on-device test processes as well. So every team member is able to inspect the current build and test status on a dashboard and see where the team stands in terms of delivery. This concludes the sixth part of these series, and we're evolving from testing into running a complete IoT Toolchain. Stay tuned for the upcoming parts, where we'll be looking under the hood of PlatformIO's build system and see how to integrate special actions.

Eren

Andreas
