# Building owncloud client for Raspberry pi's raspbian

_Captured: 2017-05-23 at 18:52 from [wiki.sgripon.net](https://wiki.sgripon.net/doku.php?id=building_owncloud_client_for_raspberry_pi)_

I use my Raspberry pi as an owncloud client to synchronize my NAS and my server. Unfortunately, the official package is not up-to-date so I have to build it by myself.

**Update!**: this page has been updated for client 2.3.2.

**DISCLAIMER ** Tested on raspbian jessie on raspi 1 and 3. Feedback welcome on twitter.

**Note:** if you need a newer version of the client, just tweet me [@sgripon](https://twitter.com/sgripon).

If you don't want to compile by yourself, you can get the debian package installer from <http://pub.sgripon.net/owncloud-client/rpi/> (tested on raspberry pi 1) or <http://pub.sgripon.net/owncloud-client/rpi3/> (tested on raspberry pi 3).

To install:
    
    
    sudo dpkg -i owncloud-client-2.3.2_armhf.deb

If there are missing dependencies, this command should automatically install all:
    
    
    sudo apt-get install -f

If not, you should be able to install manually missing packages with apt-get.

I also experiment ppa. You can try it by adding my ppa to the source.list. Add line:
    
    
    deb http://pub.sgripon.net ppa/

to /etc/apt/sources.list

Then:
    
    
    sudo apt-get update
    sudo apt-get install owncloud-client

I use raspberry pi emulator to build owncloud. See [Raspberry pi emulator](https://wiki.sgripon.net/doku.php/raspberry_pi_emulator). This is to avoid too much writing on SD card and breaking it too quickly.

Most of the build instructions are from owncloud official website (<http://doc.owncloud.org/desktop/2.2/building.html>) with some adjustments for RPI.

Get owncloud client sources from official web site here: <https://download.owncloud.com/desktop/stable/owncloudclient-2.3.2.tar.xz>.

This tutorial assumes that the work is done on raspbian in folder /home/pi/dev/owncloud-client. If not, change all paths.

On your pi:
    
    
      cd /home/pi/dev/owncloud-client

Some dependencies are necessary to build the two packages.
    
    
      sudo apt-get install libssl-dev
      sudo apt-get install libsqlite3-dev
      sudo apt-get install libqt4-dev libqtkeychain0 qtkeychain-dev libqt4-sql-sqlite

You will need to install cmake if not already done to build both:
    
    
      sudo apt-get install cmake

The following script downloads and builds the source code (remove download command (_wget_) if already done). The script must be invoked with the desired client version:
    
    
    ./oc-build.sh 2.3.2

The script should work for future versions unless ownlcoud changes files naming.

[oc-build.sh](https://wiki.sgripon.net/doku.php/building_owncloud_client_for_raspberry_pi?do=export_code&codeblock=3)
    
    
    
    #!/bin/sh
     
    # Download and extract source from official website
    if [ ! -f owncloudclient-$1.tar.xz ]; then
      wget https://download.owncloud.com/desktop/stable/owncloudclient-$1.tar.xz
    fi
     
    tar -xf owncloudclient-$1.tar.xz
     
    # Build
    mkdir client-build 
    cd client-build
    cmake -DWITH_DOC=TRUE -DCMAKE_BUILD_TYPE="Release" ../owncloudclient-$1
    make

Then, installation. The following script must be run as root:
    
    
    sudo ./oc-install.sh 2.3.2

[oc-install.sh](https://wiki.sgripon.net/doku.php/building_owncloud_client_for_raspberry_pi?do=export_code&codeblock=5)
    
    
    
    #!/bin/sh
     
    cd client-build
     
    # Prepare a redistribuable package
    make package
     
    make install
     
    # It seems that libocsync and libowncloudsync shared libraries must be installed manually:
    cp csync/src/libocsync.so.$1 /usr/local/lib
    cp src/libsync/libowncloudsync.so.$1 /usr/local/lib
    ldconfig

In /home/pi/dev/owncloud-client, create a deb folder:
    
    
    cd /home/pi/dev/owncloud-client
    mkdir -p deb/owncloud-client

First thing is to copy all needed files to this new folder. We are lucky, the "make install" command has produced a file with all files installed, so it can be used with rsync:
    
    
    cd deb/owncloud-client
    rsync  --files-from /home/pi/dev/owncloud-client/client-build/install_manifest.txt / .

Add also libraries installed manually:
    
    
    cp /usr/local/lib/libocsync.so.2.3.2 usr/local/lib
    cp /usr/local/lib/libowncloudsync.so.2.3.2 usr/local/lib

The full script to build the debian package:

[oc-build-deb.sh](https://wiki.sgripon.net/doku.php/building_owncloud_client_for_raspberry_pi?do=export_code&codeblock=6)
    
    
    
    #!/bin/sh
     
    DIR=`pwd`
     
    mkdir -p deb/owncloud-client
    cd deb/owncloud-client
     
    rsync --files-from $DIR/client-build/install_manifest.txt / .
     
    cp /usr/local/lib/libocsync.so.$1 usr/local/lib
    cp /usr/local/lib/libowncloudsync.so.$1 usr/local/lib
     
    mkdir DEBIAN
     
    cat <<EOT>> DEBIAN/control
    Package: owncloud-client
    Version: $1+debian+rpi1
    Homepage: https://wiki.sgripon.net/doku.php?id=building_owncloud_client_for_raspberry_pi
    Depends: libc6 (>= 2.13-28), libgcc1 (>= 1:4.4.0), libqt4-network (>= 4:4.7.0~beta1), libqt4-test (>= 4:4.5.3), libqt4-xml (>= 4:4.5.3), libqtcore4 (>= 4:4.8.0), libqtgui4 (>= 4:4.7.0~beta1), libqtkeychain0 (>= 0.1.0), libstdc++6 (>= 4.4.0), libqtwebkit4, libqt4-xmlpatterns, libqt4-sql-sqlite
    Priority: optional
    Section: net
    Architecture: armhf
    Essential: no
    Installed-Size: 1024
    Maintainer: Sebastien Gripon <oc-rpi-deb@sgripon.net>
    Description: GUI app to sync a folder to ownCloud
     Specify one ore more directories on the local machine to sync your ownCloud
     server, and always have your latest files wherever you are. Make a change to
     the files on one computer, it will flow across the others using these desktop
     sync clients.
    EOT
     
    cat <<EOT>> DEBIAN/postinst
    #!/bin/sh
    set -e
     
    echo "Postinst running ..."
    ldconfig
    echo "Done"
    EOT
     
    chmod 0755 DEBIAN/postinst
     
    # Build package
    cd $DIR/deb
    dpkg-deb --build owncloud-client
     
    # Rename package
    mv owncloud-client.deb owncloud-client-$1_armhf.deb

Must be invoked as sudo with version number as argument:
    
    
    sudo ./oc-build-deb.sh 2.3.2

If you want to launch owncloud client automatically at startup, just add this line:
    
    
    @owncloud

at the end of _/etc/xdg/lxsession/LXDE/autostart_

Note that owncloud client needs a graphical session to be launched so if you want to launch the client at raspi boot, it must be configured to start X automatically.
