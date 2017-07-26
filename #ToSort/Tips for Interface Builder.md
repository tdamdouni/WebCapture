# Tips for Interface Builder

_Captured: 2015-11-19 at 20:31 from [merowing.info](http://merowing.info/2015/11/tips-for-interface-builder/)_

Young developers are happy when they write a lot of code, they like to brag about that project that has tens of thousands lines of code they wrote.

As we get more experienced, we realize that code is expensive. It's expensive to maintain, debug and reason about.

That's why we should aim to use tools that can help us avoid writing boilerplate code, one of those tools is Interface Builder.

Here are a few of my favourite tips & tricks.

## Storyboards or Xib's

It's pretty clear that Storyboards are what Apple want's us to use as some of the IB features are only available in Storyboard files:

  * Prototype cells
  * Segues
  * Container View Controllers

When it comes to Storyboards, a lot of people complain it's hard to work in teams because of Merge conflicts, this used to be more true in the past, but for a while now we have had a better and easier to understand Storyboard format.

Even so, I don't like merging stuff, fortunately when we divide our Application into Storyboards properly, we can avoid a lot of potential conflicts.

I prefer to create a Storyboard per set of user stories, e.g. from latest app:

  * Onboarding - creating an account and the initial info screens
  * Create Flow - when the user is able to create content
  * Activities - screens related to viewing mentions, activities of myself or other users

iOS 9 brought us [Storyboard References](http://code.tutsplus.com/tutorials/ios-9-staying-organized-with-storyboard-references--cms-24226), this makes it even easier to divide the application into multiple Storyboards.

What about if I need to target older iOS?

### Rolling your own Storyboard, Xib or Class References

If you are not lucky enough to target iOS 9 as min deplyoment target, you can still roll your own implementation, it's a little bit more work but still worth the effort. For years now I've been using a very simple extension to have my own Storyboard, Xib or Class references in interface builder.

Gist of it:

  * Create an Empty UIViewController in a Storyboard
  * Use IBInspectable extension on UIViewController to support custom replacementIdentifier schemas: 
    * storyboard.StoryboardName.ControllerIdentifier
    * storyboard.StoryboardName -> loads the initial vc
    * class.name
    * xib.name
    
    
    @interface UIViewController (KZReplacement)
    
    @property (nonatomic, copy) IBInspectable NSString *replacementIdentifier;
    
    //! Creates new controller if there is a replacementIdentifier set, otherwise returns self
    - (UIViewController *)kz_replacementController;
    
    @end
    

In Interface Builder it looks like this:

![](http://merowing.info/2015/11/replacement.png)

The implementation should be a simple exercise, this is the most 'complex' method:
    
    
    - (UIViewController *)kz_replacementControllerWithIdentifier:(NSString *)identifier;
    {
        NSDictionary *replacementSchemes = @{
                @"class" : [NSValue valueWithPointer:@selector(kz_createControllerWithClassIdentifier:)],
                @"storyboard" : [NSValue valueWithPointer:@selector(kz_loadControllerWithStoryboardIdentifier:)],
                @"xib" : [NSValue valueWithPointer:@selector(kz_loadControllerWithXibIdentifier:)]
        };
    
        __block UIViewController *replacement = nil;
        [replacementSchemes enumerateKeysAndObjectsUsingBlock:^(NSString *scheme, NSValue *selectorValue, BOOL *stop) {
            const struct _NSRange range = [identifier rangeOfString:scheme];
            if (range.location == 0)
            {
                *stop = YES;
                UIViewController *(*objc_msgSendTyped)(id, SEL, NSString *) = (UIViewController *(*)(id, SEL, NSString *))objc_msgSend;
                replacement = objc_msgSendTyped(self, selectorValue.pointerValue, [identifier substringFromIndex:range.length + 1]);
            }
        }];
    
        return replacement;
    }
    

Now you only need your own container to execute this method on each VC, e.g. if your app uses TabBar this would work for your subclass of UITabBarController:
    
    
    - (void)awakeFromNib;
    {
        [super awakeFromNib];
        [super setViewControllers:[self processViewControllersByReplacingMocks:self.viewControllers] animated:NO];
    }
    
    - (void)setViewControllers:(NSArray *)viewControllers animated:(BOOL)animated;
    {
        [super setViewControllers:[self processViewControllersByReplacingMocks:viewControllers] animated:animated];
    }
    
    - (void)setViewControllers:(NSArray *)viewControllers;
    {
        [super setViewControllers:[self processViewControllersByReplacingMocks:viewControllers]];
    }
    
    - (NSArray *)processViewControllersByReplacingMocks:(NSArray *)viewControllersAndMocks;
    {
        NSMutableArray *array = [NSMutableArray new];
        [viewControllersAndMocks enumerateObjectsUsingBlock:^(UIViewController *viewController, NSUInteger idx, BOOL *stop) {
            UIViewController *replacement = [viewController kz_replacementController];
            [array addObject:replacement ?: viewController];
        }];
        return [array copy];
    }
    

## Using Behaviours

If there was one Pattern that I would recommend you use it would without any doubt be Composition, a pattern so great that it leads to other good ones naturally.

Behaviours are composition, only configured with help of Interface Builder.

I've written about it in [objc.io](http://www.objc.io/issue-13/behaviors.html) Architecture Guide.

## Runtime Attributes and @IBInspectable

For years we were able to set custom properties straight from **IB**, yet a lot of people had no idea, they would create a **UIView** in Interface Builder and then configure some of it's properties in code.

With Xcode 6 Runtime Attributes got upgraded to **@IBInspectable**, turning old and fragile:

![](http://merowing.info/2015/11/old_runtime_attributes.png)

into a proper editable property, one that we cannot misspell:

They support any properties of type:

  * Int
  * CGFloat
  * Double
  * String
  * Bool
  * CGPoint
  * CGSize
  * CGRect
  * UIColor
  * UIImage

### Extending UIKit

And you can even extend existing types, like UIKit classes:
    
    
    extension UIView {
        @IBInspectable var kz_borderColor: UIColor? {
            get {
                if let colorRef = layer.borderColor {
                    return UIColor(CGColor: colorRef)
                }
                
                return nil
            }
            set {
                layer.borderColor = newValue?.CGColor
            }
        }
    }
    

Gives each UIView a nice editor for border colors:

![](http://merowing.info/2015/11/border_color.png)

### Driving side-effects

How about adding a identifier to **NSLayoutConstraint**, iOS 7 added **identifier** field that can be used for debuging purpose, but I had a different use case for a custom identifier.

Our application needed to have slightly different designs on each iOS Device, Size Classes unfortunately were not enough for that particular need.

Having to deal with such a requirement, I've created a simple DSL Syntax to describe our values for each device:
    
    
    KZ_SPEC(Create, (@{
      @"create.size.captionTextWidth" : kz_spec(260, 250, 234, 220),
      @"create.size.segmentCollectionView.height" : kz_spec(116, 116, 116, 116).offsetBy(16)
    }))
    

And extended NSLayoutConstraint to allow us to bind specification to actual interface, that way we could avoid writing any boilerplace code in our views:
    
    
    @interface NSLayoutConstraint(KZDesignSpec)
    @property (nonatomic, copy) IBInspectable NSString* kz_specName;
    @end
    
    @implementation NSLayoutConstraint (KZDesignSpe)
    static void const *kDesignSpecKey = &kDesignSpecKey;
    
    - (NSString *)kz_specName;
    {
      return objc_getAssociatedObject(self, kDesignSpecKey);
    }
    
    - (void)setKz_specName:(NSString *)kz_specName;
    {
      objc_setAssociatedObject(self, kDesignSpecKey, kz_specName, OBJC_ASSOCIATION_COPY_NONATOMIC);
      self.constant = kz_floatForSpec(kz_specName);
      self.identifier = kz_specName;
    }
    
    @end
    

## Shortcuts and hidden options

Be sure to know your shortcuts and hidden options of Interface Builder.

I remember when I've used IB for 2 years and then saw someone using Media Tab to drag an Image straight into properly sized UIImageView, I always did it by hand…

There are lots of them, [here are some good ones](http://codesheriff.blogspot.com/2014/03/8-tips-for-working-effectively-with.html)

When working with AutoLayout, be sure to use Option Key when dragging constraints, or Edit menu.

## Conclusion

Interface Builder is far from Perfect, but it's also far from the wretched tool that some Developers consider it to be.

Many application's are not 'too complex for Interface Builder', which is something a lot of people say when I ask them why they don't use IB.

[Foldify](http://foldifyapp.com) and [Storest](http://pixle.pl) both used IB heavily.

Be Pragmatic, in many cases IB will suffice, especially with some smart extensions that I shown you, or the ones you'll write for yourself.

In other cases use Code, it doesn't have to be one or the other.
