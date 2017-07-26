# How to implement Deep copy for the Class in UIKit?

up vote 2 down vote favorite

**2**

I have an object imageView1. I want to create another object to keep the deep copy of imageView1. Like this,
    
    
    UIImageView *imageView1 = [[UIImageView alloc] initWithImage:[UIImage imageNamed:@"background.png"]];
    UIImageView *imageView2 = [imageView1 copy];
    

I know it does't work, because UIImageView doesn't conform to NSCopying. But how should i do?

[iphone](/questions/tagged/iphone) [objective-c](/questions/tagged/objective-c) [ios](/questions/tagged/ios) [deep-copy](/questions/tagged/deep-copy)

[share](/q/10188387)|[improve this question](/posts/10188387/edit)

[edited Apr 17 '12 at 10:33](/posts/10188387/revisions)

![](https://www.gravatar.com/avatar/37f4524cd7e14422a7cb0cbe3cf3e24c?s=32&d=identicon&r=PG)

[Mayur Birari](/users/304839/mayur-birari)

4,64972555

asked Apr 17 '12 at 9:14

![](https://www.gravatar.com/avatar/78b63cc56394a8a7dd86a702624a9ab4?s=32&d=identicon&r=PG)

[tzzzoz](/users/412786/tzzzoz)

9619

  
 

Copying UI components is not a good idea in any architecture. - [Sulthan](/users/669586/sulthan) Apr 17 '12 at 10:55

  
 

@Sulthan I understand what you mean. But, I really need UIImageView to save some Data about Model. Certainly, it works to storage CGRect, fileName and so on. I think it's complex than using UIImageView directly. Thanks for your experience. I will take care of this. - [tzzzoz](/users/412786/tzzzoz) Apr 17 '12 at 11:55

  
 

You should be able to create UI from your model, not make UI part of your model. - [Sulthan](/users/669586/sulthan) Apr 17 '12 at 12:29

add a comment | 

##  2 Answers 2

[ active](/questions/10188387/how-to-implement-deep-copy-for-the-class-in-uikit?answertab=active#tab-top) [ oldest](/questions/10188387/how-to-implement-deep-copy-for-the-class-in-uikit?answertab=oldest#tab-top) [ votes](/questions/10188387/how-to-implement-deep-copy-for-the-class-in-uikit?answertab=votes#tab-top)

up vote 4 down vote accepted

To create a deep copy of UIImageView object you need to archive it using NSKeyedArchiver and then unarchive it with NSKeyedUnarchiver, but there is a problem with this approach because UIImage does not conform to the NSCoding protocol. What you need to do first is to extend the UIImage class to support NSCoding.

Add a new category with name `NSCoding` on `UIImage` and place the following code:

**UIImage+NSCoder.h**
    
    
    #import <UIKit/UIKit.h>
    
    @interface UIImage (NSCoding)
    - (id)initWithCoder:(NSCoder *)decoder;
    - (void)encodeWithCoder:(NSCoder *)encoder;
    @end
    

**UIImage+NSCoder.m**
    
    
    #import "UIImage+NSCoder.h"
    
    @implementation UIImage (NSCoding)
    - (id)initWithCoder:(NSCoder *)decoder {
        NSData *pngData = [decoder decodeObjectForKey:@"PNGRepresentation"];
        [self autorelease];
        self = [[UIImage alloc] initWithData:pngData];
        return self;
    }
    - (void)encodeWithCoder:(NSCoder *)encoder {
        [encoder encodeObject:UIImagePNGRepresentation(self) forKey:@"PNGRepresentation"];
    }
    
    @end
    

Then add a new category with name `DeepCopy` (for ex.) on UIImageView and the following code:

**UIImageView+DeepCopy.h**
    
    
    #import <UIKit/UIKit.h>
    
    @interface UIImageView (DeepCopy)
    -(UIImageView *)deepCopy;
    @end
    

**UIImageView+DeepCopy.m**
    
    
    #import "UIImageView+DeepCopy.h"
    #import "UIImage+NSCoder.h"
    
    @implementation UIImageView (DeepCopy)
    
    -(UIImageView *)deepCopy
    {
        NSMutableData *data = [[NSMutableData alloc] init];
        NSKeyedArchiver *archiver = [[NSKeyedArchiver alloc] initForWritingWithMutableData:data];
        [archiver encodeObject:self forKey:@"imageViewDeepCopy"];
        [archiver finishEncoding];
        [archiver release];
    
        NSKeyedUnarchiver *unarchiver = [[NSKeyedUnarchiver alloc] initForReadingWithData:data];
        UIImageView *imgView = [unarchiver decodeObjectForKey:@"imageViewDeepCopy"];
        [unarchiver release];
        [data release];
    
        return imgView;
    }
    
    @end
    

Usage: Import your UIImageView+DeepCopy.h
    
    
    UIImageView *imgView1 = [[UIImageView alloc] initWithImage:[UIImage imageNamed:@"picture.jpg"]];
    UIImageView *imageView2 = [imgView1 deepCopy];
    

[share](/a/10189676)|[improve this answer](/posts/10189676/edit)

[edited Apr 17 '12 at 11:10](/posts/10189676/revisions)

answered Apr 17 '12 at 10:43

![](https://i.stack.imgur.com/CRg8T.jpg?s=32&g=1)

[graver](/users/1228534/graver)

12.2k22849

  
 

It's very smart! But, if I have some sub imageViews in imageView1. How to modify this method? - [tzzzoz](/users/412786/tzzzoz) Apr 17 '12 at 12:20

  
 

This approach will copy the whole object graph, so you don't need to change anything. UIImageView *imgView1 = [[UIImageView alloc] initWithImage:[UIImage imageNamed:@"picture.jpg"]]; UIImageView *imgView2 = [[UIImageView alloc] initWithImage:[UIImage imageNamed:@"picture2.jpg"]]; [imgView1 addSubView:imgView2]; UIImageView *copiedResult = [imgView1 deepCopy]; - [graver](/users/1228534/graver) Apr 17 '12 at 12:28

  
 

Ok, I will try it. Thanks! - [tzzzoz](/users/412786/tzzzoz) Apr 17 '12 at 12:34

1
 

It works for me! Thanks again! - [tzzzoz](/users/412786/tzzzoz) Apr 17 '12 at 12:57

add a comment | 

up vote 4 down vote

**Shallow copy**  
One method of copying an object is the shallow copy. In this process, B is attached to the same memory block as A. This is otherwise known as address copy. This results in a situation in which same data is shared between A and B, thus modifying the one will alter the other. The original memory block of B is now no longer referred to from anywhere. If the language does not have automatic garbage collection the original memory block of B has probably been leaked. The advantage of shallow copies is that their execution speed is fast and does not depend on the size of the data. Bitwise copies of objects which are not made up of a monolithic block are shallow copies.   
  
**Deep copy**  
An alternative is a deep copy. Here the data is actually copied over. The result is different from the result a shallow copy gives. The advantage is that A and B do not depend on each other but at the cost of a slower more expensive copy.  
  
![enter image description here](http://i.stack.imgur.com/bGIlI.png)   
So following snippet will work for you to do deep copy.
    
    
    UIImageView *imageView1 = [[UIImageView alloc] initWithImage:[UIImage imageNamed:@"background.png"]];
    UIImageView *imageView2 = [[UIImageView alloc] initWithImage:imageView1.image];
    

[share](/a/10189719)|[improve this answer](/posts/10189719/edit)

answered Apr 17 '12 at 10:45

![](https://www.gravatar.com/avatar/37f4524cd7e14422a7cb0cbe3cf3e24c?s=32&d=identicon&r=PG)

[Mayur Birari](/users/304839/mayur-birari)

4,64972555

  
 

I have try it. But, I find imageView2.image is a reference of imageView1.image. Both of these image have the same memory address. Besides, imageView1 may have some subviews. - [tzzzoz](/users/412786/tzzzoz) Apr 17 '12 at 12:13

  
 

@tzzzoz, so the code does not do a deep copy, right? - [gabbler](/users/4016786/gabbler) Oct 6 '14 at 6:23

  
 

For these UIImage objects, I thought it doesn't do a deep copy. You can try it and see if these two UIImage objects have the same memory address. - [tzzzoz](/users/412786/tzzzoz) Oct 8 '14 at 11:05

add a comment | 


