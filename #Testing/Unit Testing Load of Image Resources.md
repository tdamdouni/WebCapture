# Unit Testing Load of Image Resources

_Captured: 2015-12-06 at 01:16 from [www.infinite-loop.dk](http://www.infinite-loop.dk/blog/2012/06/unit-testing-load-of-image-resources/)_

I recently decided to try out the Test Driven Development approach for a new utility iPhone App which I'm currently working on. My goal was (and still is) to perform TDD in every possible corner of the design and implementation of the App. As it happened the project was kicked off about the same time as "[Test-Driven iOS Development](http://www.amazon.co.uk/Test-Driven-iOS-Development-Developers-Library/dp/0321774183?SubscriptionId=AKIAI6JHVCNWPJEGDMTA&tag=infiniteloop-21)" by Graham Lee was released. This book shows how to develop an iOS App from scratch using TDD throughout the entire process - including design and test of the UI aspects. Graham's book is one of the first (if not the first) I have seen which also covers the UI parts - most other sources I have seen tend to just write this off as not practically possible. The techniques described below are heavily inspired by some of the examples and methods described in the book. Anyway, if you haven't purchased it yet, I can highly recommend you do so - it's a great book.

One of the tasks of my new iPhone App is to display a small icon for indication of battery status for a connected UPS (Uninterruptible Power Supply). The icon will just be loaded from the bundle resources depending on the status of the power supply. It's fairly straightforward to write a bunch of tests to verify that the correct image is selected for the various states, e.g.:
    
    
    - (void)testImageNameForUpsNotPresent {
      UPSStatus *status = [[UPSStatus alloc] initWithStatus:notPresentTestData];
      assertThat([status imageName], equalTo(@"UPS_NotPresent"));
    }
     
    - (void)testCanLoadImageForUpsNotPresent {
      UPSStatus *status = [[UPSStatus alloc] initWithStatus:notPresentTestData];
      assertThat([status image], notNilValue());
    }

[AdSense - blog banner]  
It's also fairly straightforward to implement some code in the `UPSStatus` class that satisfies these tests, e.g.:
    
    
    - ([NSString](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSString_Class/)*)imageName {
      if(status == kUPSNotPresentStatus) {
        return @"UPS_NotPresent";
      }
      ...
    }
     
    - (UIImage*)image {
      return [UIImage imageNamed:[self imageName]];
    }

That code is so simple it couldn't possibly fail. Or could it? Looking into the [documentation](http://developer.apple.com/library/ios/documentation/UIKit/Reference/UIImage_Class/Reference/Reference.html#//apple_ref/occ/clm/UIImage/imageNamed:) for `+[UIImage imageNamed:]` there are different behaviors whether you are running on an older iPhone or on one with Retina display:

> On a device running iOS 4 or later, the behavior is identical if the device's screen has a scale of 1.0. If the screen has a scale of 2.0, this method first searches for an image file with the same filename with an @2x suffix appended to it. For example, if the file's name is button, it first searches for button@2x. If it finds a 2x, it loads that image and sets the scale property of the returned UIImage object to 2.0. Otherwise, it loads the unmodified filename and sets the scale property to 1.0.

Unfortunately this mean that we'll have to somehow force `UIImage` to load the image with a specific resolution so that we can test that both image files are loaded correctly. There are no public accessors for this, so we'll need to resort to a technique called method swizzling. This allows us to replace the standard `imageNamed:` method with our own specialized test version:
    
    
    static const char *imageLocKey = "TestSizeImageNamedLocalizationKey";
    static const char *imageSizeKey = "TestSizeImageNamedSizeModifierKey";
     
    @implementation UIImage(TestOverrideAutomaticSize)
     
    + (UIImage*)testOverrideAutomaticSize_ImageNamed:([NSString](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSString_Class/) *)name {
      UIImage *image = nil;
      [NSString](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSString_Class/) *loc = objc_getAssociatedObject([UIImage class], imageLocKey);
      [NSArray](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSArray_Class/) *paths = [[[NSBundle](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSBundle_Class/) mainBundle] pathsForResourcesOfType:nil
                                                          inDirectory:nil
                                                      forLocalization:loc ?: @"en"];
     
      [NSString](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSString_Class/) *sizeModifier = objc_getAssociatedObject([UIImage class], imageSizeKey);
      if(sizeModifier) {
        name = [name stringByAppendingString:sizeModifier];
      }
      for([NSString](http://developer.apple.com/documentation/Cocoa/Reference/Foundation/Classes/NSString_Class/) *path in paths) {
        if([[[path lastPathComponent] stringByDeletingPathExtension] isEqualToString:name]){
          image = [UIImage imageWithContentsOfFile:path];
          break;
        }
      }
     
      return image;
    }
     
    @end

This code will search the localized and global bundle directory for a file name that matches the supplied name exactly (minus the extension) and return an `UIImage` instance using that file. This behavior should be close enough to the original `imageNamed:` method for the purpose of detecting if any image files are missing in the bundle. The behavior of the code is controlled by using associated objects. That way the same code can be used for loading images in 1x and 2x resolutions as well as searching for different localized versions if that should be needed.  
In order to use our test code we'll need to replace the standard implementation of `imageNamed:` as shown below:
    
    
    @implementation UPSStatusTest {
      SEL realImageNamed, testImageNamed;
      BOOL hasSwappedImageNamedImpl;
    }
     
    - (void)tearDown {
      [self resetImageNamedImpl];
    }
     
    - (void)swapClassMethodsForClass:(Class)cls selector:(SEL)sel1 withSelector:(SEL)sel2 {
      Method method1 = class_getClassMethod(cls, sel1);
      Method method2 = class_getClassMethod(cls, sel2);
      method_exchangeImplementations(method1, method2);
    }
     
    - (void)resetImageNamedImpl {
      if(hasSwappedImageNamedImpl) {
        [self swapClassMethodsForClass:[UIImage class]
                              selector:testImageNamed 
                          withSelector:realImageNamed];
        hasSwappedImageNamedImpl = NO;
        objc_setAssociatedObject([UIImage class], imageSizeKey, nil, OBJC_ASSOCIATION_RETAIN);
      }
    }
     
    - (void)setTestImageNamedImpl {
      if(!hasSwappedImageNamedImpl) {
        realImageNamed = @selector(imageNamed:);
        testImageNamed = @selector(testOverrideAutomaticSize_ImageNamed:);
        [self swapClassMethodsForClass:[UIImage class]
                              selector:realImageNamed 
                          withSelector:testImageNamed];
        hasSwappedImageNamedImpl = YES;
      }
    }
     
    - (void)setLoadImageNamed1x {
      [self setTestImageNamedImpl];
      objc_setAssociatedObject([UIImage class], imageSizeKey, nil, OBJC_ASSOCIATION_RETAIN);
    }
     
    - (void)setLoadImageNamed2x {
      [self setTestImageNamedImpl];
      objc_setAssociatedObject([UIImage class], imageSizeKey, @"@2x", OBJC_ASSOCIATION_RETAIN);
    }

To choose if we want to test for loading the 1x images or the 2x images we'll just have to call `setLoadImageNamed1x` or `setLoadImageNamed2x` prior to executing the code under test. We will therefore need to modify the original test from above and use these two test methods instead:
    
    
    - (void)testCanLoadImage1xForUpsNotPresent {
      [self setLoadImageNamed1x];
      UPSStatus *status = [[UPSStatus alloc] initWithStatus:notPresentTestData];
      assertThat([status image], notNilValue());
    }
     
    - (void)testCanLoadImage2xForUpsNotPresent {
      [self setLoadImageNamed2x];
      UPSStatus *status = [[UPSStatus alloc] initWithStatus:notPresentTestData];
      assertThat([status image], notNilValue());
    }

Using the above technique it's possible to ensure that all the image assets are present in you app for both older devices as well as new devices fitted with a Retina screen.
