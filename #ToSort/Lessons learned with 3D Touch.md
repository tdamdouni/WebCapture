# Lessons learned with 3D Touch

_Captured: 2015-10-04 at 14:51 from [engineering.instagram.com](http://engineering.instagram.com/posts/465414923641286/lessons-learned-with-3D-touch)_

Last week, Apple released the latest iPhone line, starting with the 6s, which adds a new hardware feature called 3D Touch. As part of the screen, there are new sensors that can tell when you are pressing firmly on the screen and measures precise changes in pressure.

Along with the new hardware, Apple added three APIs that let developers add another dimension of interaction to their apps. Quick Actions let you select up to four context menu items from your app's icon. Another feature lets you "Peek" into content and then "Pop" deeper into it. The last API gives developers details about the depth of a `UITouch` with force and `maximumPossibleForce`.

We had the opportunity to integrate this new technology into Instagram early on and were excited by how natural the shortcuts and peeking on photos and videos felt. The API for adding 3D interactions was seamless to use, and along the way we collected pointers for how to add them to your apps.

## Quick Actions

Quick actions give your users a shortcut to jump to a part of your app by removing any steps in between. For Instagram, we added shortcuts for some of the most commonly used actions in the app: Search, Direct, Activity, and Creation.

![](https://scontent.xx.fbcdn.net/hphotos-xpt1/t39.2365-6/12057001_459445050928434_318754511_n.gif)

Adding shortcuts to the home screen is really simple. All you need to do is create an array of `[UIApplicationShortcutItems](https://www.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.apple.com%2Flibrary%2Fprerelease%2Fios%2Fdocumentation%2FUIKit%2FReference%2FUIApplicationShortcutItem_class%2F&h=vAQEa5zTj&s=1)` and add them to your app's delegate. Each item has a type string and an optional `UIApplicationShortcutIcon`.

In Instagram, we created `UIApplicationShortcutItem` categories to generate our shortcuts:
    
    
      + (instancetype)ig_searchItem {
      NSString *title = NSLocalizedString(@"Search", nil);
      UIApplicationShortcutIcon *icon = [UIApplicationShortcutIcon iconWithTemplateImageName:@"search"];
      UIApplicationShortcutItem *item = [[UIApplicationShortcutItem alloc] initWithType:@"search"
                                                                         localizedTitle:title
                                                                      localizedSubtitle:nil
                                                                                   icon:icon
                                                                               userInfo:nil];
      return item;
    }
      

Depending on if the user is logged in or logged out, we dynamically configure the shortcut items on the app delegate:
    
    
    application.shortcutItems = @[
      [UIApplicationShortcutItem ig_postItem],
      [UIApplicationShortcutItem ig_activityItem],
      [UIApplicationShortcutItem ig_searchItem],
      [UIApplicationShortcutItem ig_directItem]
        ];

Since our architecture already handled actions like app links and push notifications, we ended up using the same routing to handle shortcut actions in `-application:performActionForShortcutItem:completionHandler:`.

## Peek and Pop

Just as you would use a magnifying glass to get a closer look, peeking on content like photos and videos is a way to get a little more info without committing to loading the whole thing.

The simple, first choice for Instagram was to add peeking on smaller images and videos.

The Peek and Pop API has a delegate called [UIViewControllerPreviewingDelegate](https://www.facebook.com/l.php?u=https%3A%2F%2Fdeveloper.apple.com%2Flibrary%2Fprerelease%2Fios%2Fdocumentation%2FUIKit%2FReference%2FUIViewControllerPreviewingDelegate_Protocol%2F&h=EAQFlHUVq&s=1) which is registered to a view. In Instagram, we just register the view of a controller that can receive touches. When a 3D Touch occurs, the delegate decides if there is a peek for whatever item in the view was touched.

![](https://fbcdn-dragon-a.akamaihd.net/hphotos-ak-xtp1/t39.2365-6/12057109_168996173439866_1007264271_n.png)

If the delegate determines that a peek can happen, it is also responsible for two things: set the source rect of the view that is being peeked and return a controller to present.

![](https://scontent.xx.fbcdn.net/hphotos-xta1/t39.2365-6/12056959_1498703093777728_1543774343_n.jpg)

When a 3D touch happens, you are given a context with information about the source view, and the point where the touch occured. Your custom delegates are responsible for mapping the `CGPoint` to a view, and then to corresponding data that gets peeked.

Most of Instagram is built on `UICollectionViews` and `UITableViews`. The classes have excellent APIs for turning data into UI and vice-versa.
    
    
     - (UIViewController *)previewingContext:(id<UIViewControllerPreviewing>)previewingContext viewControllerForLocation:(CGPoint)location {
      UICollectionView *collectionView = (UICollectionView *)[previewingContext sourceView];
      NSIndexPath *indexPath = [collectionView indexPathForItemAtPoint:location];
    
        if (indexPath) {
        IGPostCell *cell = [collectionView cellForItemAtIndexPath:indexPath];
        [previewingContext setSourceRect:cell.frame];
    
        IGPost *post = self.feedController.posts[indexPath.row];
        IGThumbnailPreviewController *controller = [[IGThumbnailPreviewController alloc] initWithPost:post];
          return controller;
      }
    
      // no peek
      return nil;
    }
        

Combining the simple Peek and Pop API with our existing views and infrastructure gave Instagram photo and video peeks with minimal effort!

![](https://scontent.xx.fbcdn.net/hphotos-xaf1/t39.2365-6/10000000_1686332944933747_1140652000_n.gif)

We also added a profile peek for headers or whenever someone is tagged in a comment. The profile-peek delegate works similarly to post-peeks:

  * Find the cell that received a 3D Touch using the location and looking up the `NSIndexPath`
  * Convert the location to a `CGPoint` relative to the text view in the cell
  * Get the attributes for the NSAttributedString at the given `CGPoint`
  * If a username attribute exists, return an IGUserPreviewController

All wired up, the profile peek looks just like this:

![](https://fbcdn-dragon-a.akamaihd.net/hphotos-ak-xta1/t39.2365-6/12056998_1481666338803498_703058534_n.gif)

## Mixing Peeks

The activity feed in Instagram contains both username tags _and_ thumbnails that we wanted to peek. Each of the `UIViewControllerPreviewingDelegate` objects we built for profiles and media were built specifically for those views. We had to somehow combine the work being done in both delegates.

Instead of copy-pasting into a new delegate, we used the **composition pattern** with our profile and post delegates to create a new object that simply forwards touch events:
    
    
    @interface IGUserThumbnailPreviewingHandler : NSObject <UIViewControllerPreviewingDelegate>
    @property (nonatomic, strong) IGUserPreviewingHandler *userDelegate;
    @property (nonatomic, strong) IGFeedThumbnailPreviewingHandler *thumbnailDelegate;
    @end
    
    - (UIViewController *)previewingContext:(idUIViewControllerPreviewing>)previewingContext viewControllerForLocation:(CGPoint)location {
        id controller = [self.thumbnailDelegate previewingContext:previewingContext viewControllerForLocation:location];
        if (!controller) {
            controller = [self.userDelegate previewingContext:previewingContext viewControllerForLocation:location];
        }
        return controller;
    }
        

## Preview Controllers

The controllers returned from a preview delegate are simple `UIViewController` subclasses with a few unique qualities.

For starters, the controllers are completely non-interactive. You can't tap buttons or add any custom gestures. Instead, you can provide an array of `UIPreviewActionItem`-conforming objects. In Instagram we just used `UIPreviewActions`.

These are presented and work similar to `UIAlertController` action items.

![](https://scontent.xx.fbcdn.net/hphotos-xpa1/t39.2365-6/12057023_182232978776192_861894133_n.jpg)

Throughout Instagram, we only load the data that we need at the time and cache it for later. This saves time waiting for the network and doesn't consume our user's bandwidth for data that isn't used.

In some cases, when displaying a profile peek, we don't have all the data we need in order to show latests photos or follower counts in the peek. Peek view controllers still receive `viewDidLoad`, `viewWillAppear:`, and other `UIViewController` events that we use to fetch network resources and update the view.

Lastly, we found out that changing `preferredContentSize` on the controller will resize the peek view, even if it has already been presented. Unfortunately, there isn't a way to animate this property yet.

## Conclusion

For Instagram, 3D Touch is much more than a 2015 version of the "right click". The interaction adds another level of depth and carries a different intent. You aren't yet committed to navigating to the content, but it's clear that you are interested. With this in mind, Peek and Pop gives you a glimpse of what lies ahead and lets you quickly back out to continue browsing.

Quick Actions allow you to jump straight to creating a new post or look at what's been happening in your Instagram without having to wait for everything to load up first. With our focus on keeping things simple, quick actions make it even easier to use Instagram.

_Ryan Nystrom is a software engineer at Instagram. Thanks also to Joshua Dickens, designer at Instagram._
