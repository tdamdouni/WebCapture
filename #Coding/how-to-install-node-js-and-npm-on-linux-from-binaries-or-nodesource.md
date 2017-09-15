# How to Install Node.js and NPM on Linux from Binaries or NodeSource

_Captured: 2017-09-01 at 12:25 from [www.thegeekstuff.com](http://www.thegeekstuff.com/2015/10/install-nodejs-npm-linux)_

![Node.js Logo](http://static.thegeekstuff.com/wp-content/uploads/2015/10/nodejs.png)

Node.js framework is very lightweight and does not use threads.

Node.js is an event driven framework. It is also asynchronous.

Using Node.js developers can write scalable application without having to worry about writing logic to take care of thread related tasks.

This article explains two methods to Install Node.js on your Linux system.

## I. Install from Linux Binaries

First method is to install nodejs from Linux Binaries that are available from [nodejs.org downloads](https://nodejs.org/en/download/).

When you install using this method, you'll always get the latest node.js version. The latest stable current version is 4.2.1

### Download Node.js Binaries

In this example, I downloaded the "Linux Binaries (.tar.gz)" 64-bit file. Download this to your downloads directory.
    
    
    cd /downloads
    wget https://nodejs.org/dist/v4.2.1/node-v4.2.1-linux-x64.tar.gz
    

Note: If you get "ERROR: certificate common name `*.nodejs.org' doesn't match requested host name `nodejs.org', then use the following to skip the certificate check.
    
    
    wget --no-check-certificate https://nodejs.org/dist/v4.2.1/node-v4.2.1-linux-x64.tar.gz
    

### Install it under /usr/local

Next, do the following to install it under /usr/local/bin. This will untar all Node.js related binaries into the appropriate directories under /usr/local.
    
    
    cd /usr/local
    tar --strip-components 1 -xzf /usr/save/node-v4.2.1-linux-x64.tar.gz
    

### Verify Node.js installation

Verify that the Node.js is successfully installed.
    
    
    # node -v
    v4.2.1
    

### Verify NPM installation

This will also install NPM. You can install additional packages to Node.js using npm.

NPM stands for Node Package Manager.

Verify that the npm is installed properly.
    
    
    # npm version
    { npm: '2.14.7',
      ares: '1.10.1-DEV',
      http_parser: '2.5.0',
      icu: '56.1',
      modules: '46',
      node: '4.2.1',
      openssl: '1.0.2d',
      uv: '1.7.5',
      v8: '4.5.103.35',
      zlib: '1.2.8' }
    

As you see below, currently node.js does not have any modules installed. You
    
    
    # npm ls
    /usr/local
    +-- (empty)
    

### Install Node Module using NPM

To install an module, use npm install command as shown below. In this example, we are installing MongoDB module to Node.js.
    
    
    # npm install mongodb
    

Verify that the mongodb Node.js module is installed successfully.
    
    
    # npm ls
    /usr/local
    +-- mongodb@2.0.46
      +-- es6-promise@2.1.1
      +-- mongodb-core@1.2.19
      ¦ +-- bson@0.4.19
      ¦ +-- kerberos@0.0.15
      ¦   +-- nan@2.0.9
      +-- readable-stream@1.0.31
        +-- core-util-is@1.0.1
        +-- inherits@2.0.1
        +-- isarray@0.0.1
        +-- string_decoder@0.10.31
    

## II. Install Node From NodeSource

You can also install node manager using [yum](http://www.thegeekstuff.com/2011/08/yum-command-examples/) on RedHat or CentOS as explained in this section.

For this, we need to use add nodesource distribution to our yum repository.

If you are using an older version of RedHat or CentOS, then you should make sure [EPEL is enabled](http://www.thegeekstuff.com/2012/06/enable-epel-repository/) on your server.

### System Verification and Nodesource Setup

The following was done on a CentOS 7 server.

First, execute the following setup script from nodesource, which will check to make sure your server is supported to install Node.js.

Next, if your system is supported, it will also install nodesource package, which is used to install the node.js using yum.
    
    
    # curl --silent --location https://rpm.nodesource.com/setup | bash -
    

The following is the output of the above curl command. As you see below, this first checks to make sure CentOS7 X86 is supported for Node.js. If supported, it then downloads the nodesource rpm file, and installs the rpm file automatically.
    
    
    ## Inspecting system...
    + rpm -q --whatprovides redhat-release || rpm -q --whatprovides centos-release || rpm -q --whatprovides cloudlinux-release
    + uname -m
    ## Confirming "el7-x86_64" is supported...
    + curl -sLf -o /dev/null 'https://rpm.nodesource.com/pub/el/7/x86_64/nodesource-release-el7-1.noarch.rpm'
    ## Downloading release setup RPM...
    + mktemp
    + curl -sL -o '/tmp/tmp.IJM36kruJO' 'https://rpm.nodesource.com/pub/el/7/x86_64/nodesource-release-el7-1.noarch.rpm'
    ## Installing release setup RPM...
    + rpm -i --nosignature --force '/tmp/tmp.IJM36kruJO'
    ## Cleaning up...
    + rm -f '/tmp/tmp.IJM36kruJO'
    ## Checking for existing installations...
    + rpm -qa 'node|npm' | grep -v nodesource
    ## Run `yum install -y nodejs` (as root) to install Node.js and npm.
    ## You may also need development tools to build native addons:
    ##   `yum install -y gcc-c++ make`
    

### Nodesoruce Warning Message on Unsupported System

If your system is not supported for Node.JS install using nodesource, you'll get the following error message:

In this example, I tried to install it on CentOS 6 and got the following warning message:
    
    
    # curl --silent --location https://rpm.nodesource.com/setup | bash -
    
    
    
    ## Inspecting system...
    + rpm -q --whatprovides redhat-release || rpm -q --whatprovides centos-release || rpm -q --whatprovides cloudlinux-release
    + uname -m
    ## Confirming "el6-x86_64" is supported...
    + curl -sLf -o /dev/null 'https://rpm.nodesource.com/pub/el/6/x86_64/nodesource-release-el6-1.noarch.rpm'
    ## Your distribution, identified as "centos-release-6-4.el6.centos.10.x86_64", is not currently supported, please contact NodeSource at https://github.com/nodesource/distributions/issues if you think this is incorrect or would like your distribution to be considered for support
    

Note: While doing the check, if you get the following SSL connect error, then go to this URL <https://rpm.nodesource.com/setup> from your browser, copy the content and paste it to nodesetup file on your local server, and execute it manually as shown below.
    
    
    # curl --location https://rpm.nodesource.com/setup | bash -
    curl: (35) SSL connect error
    
    # vi nodesetup
    
    # /bin/bash nodesetup
    

### Search for Node.JS Package using Yum

Now, when you search for nodejs using yum, you'll see it in the output. As you see below, it is also searching in the "nodesource" repository.
    
    
    # yum search node
    Loaded plugins: fastestmirror
    base             | 3.6 kB     00:00
    extras           | 3.4 kB     00:00
    nodesource       | 2.5 kB     00:00
    updates          | 3.4 kB     00:00
    ============================== N/S matched: nodejs ===========
    nodejs-debuginfo.x86_64 : Debug information for package nodejs
    nodejs-docs.noarch : Node.js API documentation
    nodejs.x86_64 : JavaScript runtime
    nodejs-devel.x86_64 : JavaScript runtime - development headers
    

### Install Node.js using Yum

Install the Node.js using yum as shown below. This will also ask you to reivew and accept the Nodesource GPG key before installing nodejs.
    
    
    # yum install nodejs
    ...
    ...
    Public key for nodejs-0.10.40-1nodesource.el7.centos.x86_64.rpm is not installed
    nodejs-0.10.40-1nodesource.el7.centos.x86_64.rpm           | 4.5 MB   00:01
    Retrieving key from file:///etc/pki/rpm-gpg/NODESOURCE-GPG-SIGNING-KEY-EL
    Importing GPG key 0x34FA74DD:
     Userid     : "NodeSource <gpg-rpm@nodesource.com>"
     Fingerprint: 2e55 207a 95d9 944b 0cc9 3261 5ddb e8d4 34fa 74dd
     Package    : nodesource-release-el7-1.noarch (installed)
     From       : /etc/pki/rpm-gpg/NODESOURCE-GPG-SIGNING-KEY-EL
    Is this ok [y/N]: y
    ..
    ..
    Installing : nodejs-0.10.40-1nodesource.el7.centos.x86_64
    Complete!
    

### Verify Node.js Installation

Verify that the node.js and npm are successfully installed.
    
    
    # node -v
    v0.10.40
    
    # npm version
    { http_parser: '1.0',
      node: '0.10.40',
      v8: '3.14.5.9',
      ares: '1.9.0-DEV',
      uv: '0.10.36',
      zlib: '1.2.8',
      modules: '11',
      openssl: '1.0.1p',
      npm: '1.4.28' }
    

In this method, you'll see that node and npm executable are installed under /usr/bin directory.
    
    
    # whereis node
    node: /usr/bin/node /usr/share/node /usr/share/man/man1/node.1.gz
    
    # whereis npm
    npm: /usr/bin/npm
    

### If you enjoyed this article, you might also like..
