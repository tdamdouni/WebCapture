# iPhone Applications in Python

_Captured: 2015-10-14 at 10:32 from [www.saurik.com](http://www.saurik.com/id/5)_

# [The Realm of the Avatar](http://www.saurik.com)

Writing iPhone applications is easy. Well, if you are willing to wait until Apple provides the ability to run their SDK-based applications on actual hardware. Until then, you are forced to go through [a quite long list of steps](http://code.google.com/p/iphone-dev/wiki/Building). While I've [updated this process somewhat](http://www.saurik.com/id/4), it's still anything but "easy".

Even then, when you get the whole thing working, you still have to know Objective-C. To some extent there is no getting around that without someone writing a giant abstraction for you: Apple's frameworks are all written in Objective-C, and their APIs are documented in it. However, that doesn't mean you really need to also learn all the quirks of C syntax or be forced to use Objective-C libraries to solve all of your problems when you are already deep into something else.

This same issue came up on the desktop, and spawned a number of projects that connect Objective-C with other languages. This is an area I have recently gotten into, writing JocStrap, which unifies Java and Objective-C's object models, allowing one to, for instance, develop for the iPhone in Java. Having done this then put me in the perfect frame of mind to try to get other languages over, and the #1 request was Python, which already has an amazing project behind it: [PyObjC](http://pyobjc.sourceforge.net/).

The effort for porting this turned out to be [minimal](http://svn.telesphoreo.org/trunk/data/pyobjc/), and the maintainer of the project (Ronald Oussoren) has contacted me about merging my changes, which means that its support that is likely to stay around for quite a while. To get it, one need only [install Cydia Packager](http://www.saurik.com/id/1) (which contains a bootstrap of the [Telesphoreo](http://www.telesphoreo.org/) project), and install the PyObjC package under the Python section (or apt-get install pyobjc).

### A Sample Application

In addition to this, however, I have included a sample program called HelloPython that performs the same function (with almost identical code) to my existing HelloJava and HelloScript (JavaScript) programs: use SQLite3 to access your contact information, and display a nice iPhone UITable with the results. Great thanks goes out to Dave Arter for this, who did much of the implementation of this sample application (I being quite busy and not even knowing Python, which luckily was not needed to port PyObjC).

To get this program, and its source code, install the package iPhone/Python from the Python section (or apt-get install iphone-python). This will install all required dependencies (including PyObjC) and place HelloPython.app in /Applications, inside which is the source code (which is an "of course" given that it's Python). The [complete source code](http://svn.saurik.com/repos/menes/trunk/uicaboodle.py/HelloPython.py) for this may also be seen online from my Subversion repository.

### A Quick Introduction

In order to help users who are new to PyObjC be able to use this bridge effectively, I think it useful to quickly go through a few points of this file. I am not going to attempt to replace the PyObjC manual, but do think that people who are already familiar with Apple's SDK (and who already know Python) should be able to jump into this almost immediately given just a few pointers.

> import objc from _uicaboodle import UIApplicationMain from objc import YES, NO, NULL from sqlite3 import dbapi2 as sqlite 

To start with, we see the block of import statements. The last one is from Python's included SQLite3 support, but the first three are new. In Objective-C, boolean values are specified using single-byte 0/1 values represented by the constants YES/NO. In order to make certain to use the correct ABI, PyObjC therefore provides YES/NO constants to use in these cases. (Note that I'm actually not certain that it does this for ABI purposes, but if it doesn't then it should.)

The weirdest part, though, is NULL. This is there because Python doesn't really have a null value: it's None is just another object that an object may choose to refer to. Isn't that enough? If you pass None to an Objective-C message, PyObjC will pass NULL. Unfortunately, there is another case: messages that take a pointer to an object. These come up a lot with error handling (where the message will fill in the pointer to point to a description of the problem).

This form of API is mapped to Python byref argument passing by PyObjC... which makes passing None not helpful if you really want to pass a NULL pointer (to disable error handling, which might be useful). Therefore, we get another constant NULL that disables the byref behavior.

Finally there is the line importing UIApplicationMain from _uicaboodle. This is probably temporary, and might get better addressed by the author of PyObjC as he merges in this support. UIApplicationMain, the first function called by an Objective-C iPhone Application, is itself exported as a C API, which means it can't be automatically discovered by PyObjC.

Functions like this would normally be supported, I believe, by a system known as [BridgeSupport](http://trac.macosforge.org/projects/BridgeSupport), but I didn't have enough time to figure out how. (Besides, the equivalent desktop function NSApplicationMain doesn't use BridgeSupport anyway, so maybe it isn't even encouraged.) We can see it used at the very bottom of the file.

> UIApplicationMain(["HelloPython"], PYApplication) 

This function takes first the set of arguments passed to the program, with the first argument being the name of the project. I've obviously cheated here, so if anyone can tell me how to get the arguments that were passed to the program (and maybe even verify that doing so works out alright), I will happily modify the program. The second argument s a class that derives from UIApplication that will be instantiated and provide the actual functionality of the program.

To get at classes such as UIApplication, we have to have PyObjC parse the Objective-C frameworks. This is done using objc.loadBundle, which takes both the name of the framework and its path. Here I bring in both Celestial (which has the AV* classes for multimedia support) and UIKit.

> objc.loadBundle("Celestial", globals(), "/System/Library/Frameworks/Celestial.framework") objc.loadBundle("UIKit", globals(), "/System/Library/Frameworks/UIKit.framework") 

After this, you generally can just directly use an Objective-C class by name as if it were a Python class object, calling static methods on it to send messages to its metaclass. As a simple example we see getting the default size of a navigation bar.

> navsize = UINavigationBar.defaultSize() navrect = ((0, 0), (inner[1][0], navsize[1])) 

This function returns a struct of two elements (a width/height), which we can see on the next line is accessed using array syntax. PyObjC does not attempt to provide access to the names of the elements as this information is usually not provided in the binary frameworks. If you have nested structs (such as a rectangle, which consists of a point and a size) then they are represented as nested arrays.

While this is all well and good for no-argument or even one-argument messages, in Objective-C multiple arguments are provided using an infix keyword notation that Python does not itself support. PyObjC therefore has to translate this functionality, and chooses to convert all the :'s in a raw selector to _'s. Something that used to be written [a does:b to:c] thereby gets converted to a.does_to_(b, c).

> col = UITableColumn.alloc().initWithTitle_identifier_width_("Name", "name", 320) 

This example also demonstrates another difference: how objects are instantiated. In Objective-C, to allocate an object, you normally send the message alloc to the metaclass object you wish to obtain an instance of. This, however, isn't the only way to get a new object as you could also call allocWithZone, and technically it is only a convention as a message named connectToServer could also serve this function. PyObjC directly maps this mechanism to Python.

The last thing we have to look at is how to provide messages back to Objective-C. This is done quite easily by providing a method with the appropriately mangled name, but there's a catch: in Objective-C the receiver is expected to know how to parse the arguments that it is passed, whereas the sender is allowed to be ignorant. This functionality comes up while connecting to remote proxy objects, or when attempting to reflect a message to determine its arguments.

This causes Python a greater challenge than some other languages as it doesn't use declared argument types. While it is important to Objective-C whether a message takes a double or a pointer, to Python there is no difference. When overriding an existing message PyObjC can just follow the inheritence hierarchy to figure it out, but barring that case the signature needs to be specified somewhere.

In PyObjC, you specify this with a special annotation objc.signature, which takes the Objective-C type signature of the method. This signature is made up of a number of different characters that represent the type. A [complete list](http://developer.apple.com/documentation/Cocoa/Conceptual/ObjectiveC/Articles/chapter_13_section_9.html#//apple_ref/doc/uid/TP30001163-CH9-TPXREF165) of these signature elements can be found in Apple's developer documentation.

> @objc.signature("i@:@i") def sectionList_rowForSection_(self, list, section): 

To exemplify this, this method takes two non-self arguments: an object (list) and an integer (section). It also returns an integer. Now, much in the same way that Python represents the self argument explicitely, in Objective-C the type signature also represents a couple hidden arguments. One of them is self, and the other is the name of the message that is being called in the form of a "selector" (which is really just an intern'd string pointer). These arguments, in that order, come before the other arguments that are defined.

Putting all of that together, we get the signature integer, object, selector, object, integer, or i@:@i. This may seem irritating, and it is: normally this sort of thing might be handled via BridgeSupport, with a list of the standard callbacks that an object might receive and their standard signatures. If someone knows more about BridgeSupport and would like to help with this, their contribution would be quite useful (although now that the maintainer of PyObjC is involved, that might be handled pretty quickly, and all we need is a good list).

### Any Questions?

After all of that, I hope everything just works for you, but if you'd like to find other people working on iPhone applications in Python, I encourage you to join [the iPhone/Python mailing list](http://www.telesphoreo.org/cgi-bin/mailman/listinfo/iphone-python), hosted at the [Telesphoreo](http://www.telesphoreo.org/) project.

Good luck!
