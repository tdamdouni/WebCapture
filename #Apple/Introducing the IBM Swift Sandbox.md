# Introducing the IBM Swift Sandbox

_Captured: 2015-12-04 at 19:22 from [developer.ibm.com](https://developer.ibm.com/swift/2015/12/03/introducing-the-ibm-swift-sandbox/)_

Hi, I'm John Petitto, one of IBM's Swift developers located at IBM's Mobile Innovation Lab in Austin. We love Swift here and thought you would too so we are making our [IBM Swift Sandbox available](http://swiftlang.ng.bluemix.net/?cm_mmc=developerWorks-_-dWdevcenter-_-swift-_-lp) to developers on developerWorks.

The IBM Swift Sandbox is an interactive website that lets you write Swift code and execute it in a server environment - on top of Linux! Each sandbox runs on IBM Cloud in a Docker container. In addition, both the latest versions of Swift and its standard library are available for you to use.

![IBM Swift Sandbox](http://developer.ibm.com/swift/wp-content/uploads/sites/69/2015/12/Screen-Shot-2015-12-04-at-7.26.25-AM-1024x391.png)

> _[IBM Swift Sandbox](http://swiftlang.ng.bluemix.net/?cm_mmc=developerWorks-_-dWdevcenter-_-swift-_-lp)_

We know you're as excited as we are to start using this tool, so please bear with us during the initial launch of the sandbox. With that in mind, let's get started!

## Hello Swift!

To begin, let's write a simple Swift program together. In the left window labeled **source code**, enter the following line of code:

`print("Hello Swift!")`

_New to Swift? Check out the [official language guide](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/Swift_Programming_Language/TheBasics.html)._

Hit the blue **run** button located at the top to execute the program. If everything was entered correctly, "Hello Swift!" should appear under **output** in the results window.

If we edit the previous example and omit the closing parenthesis at the end of the line, an error should get flagged by the editor. Hover over the red marker that appears next to the line number to examine the error message. Error messages are also listed in the output.

## Swift Meets Linux

We've provided a collection of sample programs for you to experiment with. Click **Source Samples** in the upper left corner to see the list of available sample programs. For instance, select **filestat.swift** and run the program. The output generated should be similar to what's seen below:

`/bin/bash is 1037464 bytes`

If we try changing the value of `filename` on line 12 from "/bin/bash" to "/tmp", we should see a different number of bytes printed.

You may have noticed that this program is calling `stat` from [glibc](https://www.gnu.org/software/libc/) (The GNU C Library). Since the sandbox runs on top of Linux, we can write Swift code that interacts directly with the system. Take a look at some of the other samples for more examples of using glibc.

## What's Next

With the movement of Swift to open source, we're opening the doors on what we are working on at IBM with Swift. The IBM Swift Sandbox barely scratches the surface of what's possible. To stay up to date with the open source efforts around Swift, head on over to [Swift @ IBM](https://developer.ibm.com/swift/).
