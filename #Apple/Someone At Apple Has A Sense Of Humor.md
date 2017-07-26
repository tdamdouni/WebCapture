# Someone At Apple Has A Sense Of Humor

_Captured: 2016-01-16 at 13:13 from [techcrunch.com](http://techcrunch.com/2009/07/09/someone-at-apple-has-a-sense-of-humor/)_

![iphone](http://old.mobilecrunch.com/wp-content/uploads/2009/07/iphone.jpg)

No one likes limitations. Though Apple has been opening up more and more of their API with each software update, a good chunk of the functionality is still off limits to anyone outside of their own team of developers. Be it because they're unstable, unproven, or just outright blacklisted, a number of methods exist that no one but Apple is supposed to use.

Of course, people try to use them anyway. Some ([like Google](http://www.crunchgear.com/2008/11/26/google-drops-truth-bomb-over-iphone-api/)) succeed. Others [don't](http://www.crunchgear.com/2009/06/22/interview-jared-brown-iphone-developer-about-having-his-app-rejected/). The practice of playing with verboten methods is heavily frowned upon - but if a newly discovered private method is any indication, Apple's at least got a sense of humor about it.

A bit of background, first: As with any good SDK, the iPhone OS has a big huge bundle of documents that outlines every method available to developers - well, besides the secret ones. If no one is supposed to be using them, why tease their existence?

That doesn't mean that they can't be found, however. Developers can run a tool called "classdump" while running an application, and it'll spill the beans on any private methods being used in the application. When [Erica Sadun](http://ericasadun.com/) ran a dump on the iPhone 3.0 OS, this little gem popped up:

> 00009 @interface UIViewController (UIViewControllerClassDumpWarning)  
00010 - (void)attentionClassDumpUser:(id)fp8 yesItsUsAgain:(id)fp12 althoughSwizzlingAndOverridingPrivateMethodsIsFun:(id)fp16 itWasntMuchFunWhenYourAppStoppedWorking:(id)fp20 pleaseRefrainFromDoingSoInTheFutureOkayThanksBye:(id)fp24;  
00011 @end

`[x for x in dir(ObjCClass('PAMoveFilesViewController').alloc().init()) if x.startswith('at')]`

Sans all the extraneous characters, that method reads, "Yes, it's us again. Although swizzling and overriding private methods is fun, it wasn't much fun when your app stopped working. Please refrain from doing so in the future. Okay thanks bye."

Yeah, it's silly - but it's a little easter-egg shout out to anyone looking for the next hush-hush way to give their app that little extra (and totally unauthorized) sparkle. 5 e-points to anyone who manages to work this method into an App-Store-Approved app.

Photo by: [2493™](http://www.flickr.com/photos/2493/434778868/) on Flickr
