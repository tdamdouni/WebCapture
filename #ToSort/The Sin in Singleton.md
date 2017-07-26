# The Sin in Singleton

_Captured: 2015-11-13 at 09:45 from [sandofsky.com](https://sandofsky.com/blog/singletons.html)_

Singletons are not an anti-pattern, but they are an abused pattern. They're popular among beginners because they're convenient. Down the line they add complexity and cause maddening bugs.

Let's start with the positive. Every so often, you have an object that should be represented with one and only one instance. Consider `UIApplication`:
    
    
    UIApplication.sharedApplication.applicationIconBadgeNumber = 0
    UIApplication.sharedApplication.applicationIconBadgeNumber = 1

That makes a lot more sense than:
    
    
    let firstInstance = UIApplication()
    firstInstance.applicationIconBadgeNumber = 0
    
    let secondInstance = UIApplication()
    secondInstance.applicationIconBadgeNumber = 1

Shouldn't `firstInstance == secondInstance` always return true? When we update one, does it update the other?

Singletons _may_ be an appropriate metaphor when it represents an omnipresent object, one that will never change out from under you, like the current application, the device's accelerometer, or your god.

Rarely, you need to share a single service throughout your app. `NSNotificationCenter` only works if there's a single broadcaster across all boundaries, hence the 'center' in its name.[1](https://sandofsky.com/blog/singletons.html)

Everywhere else, don't use singletons.

### An Inappropriate Model

Sometimes I see the currently logged-in user represented by `User.currentUser` or `Account.sharedAccount`. I don't blame you. It's so convenient.
    
    
    class NewsFeedController:UIViewController {
      func didPullToRefresh(sender:AnyObject){
        Account.currentAccount.newsFeed.loadNewer()
      }
    }

But **accounts are not singletons.** Users log out of accounts. Many apps represent a Logged-Out Experience through a special type of account. Services grow to support multiple simultaneous accounts. Accounts are volatile, and a singleton is a lie.

If accounts were a true singleton, this wouldn't be a problem:
    
    
    Account.currentAccount.networkAPI.validatePhoto(photo) {
      newPhoto, errorOrNil in
      guard errorOrNil == nil else { return }
      Account.currentAccount.networkAPI.updatePhoto(newPhoto)
    }

What if that photo takes minutes to validate on a slow network, and in the interim the user switches accounts? The wrong account gets the photo profile.

'Singleton' is a fancy word for 'global variable.' Sometimes-- _rarely_-- globals are necessary, but you should make every effort to avoid them. State is hard, and shared state is very, very hard.
    
    
    class HomeViewController:UIViewController {
      override func viewWillAppear(animated:Bool){
        super.viewWillAppear(animated)
        Analytics.sharedAnalytics.currentViewController = self
      }
      
      func didTapLike(sender:AnyObject) {
        Analytics.sharedAnalytics.recordEvent(.TappedLike)
      }
    }
    
    // An Alert Modal that can pop up any time
    class IncomingMessagePrompt:UIViewController {
      override func viewWillAppear(animated:Bool){
        super.viewWillAppear(animated)
        Analytics.sharedAnalytics.currentViewController = self
      }
    
      func didTapReply(sender:AnyObject) {
        Analytics.sharedAnalytics.recordEvent(.TappedReply)
      }
    }

Custom container view controllers make `viewWillAppear` less predictable. Even vanilla navigation has edge cases: if you start a bezel swipe to go back, change your mind, and cancel it, you will get a false `viewWillAppear`, and you'll log events from the wrong view controller.

This is better:
    
    
    func didTapReply(sender:AnyObject) {
      Analytics.sharedAnalytics.recordEvent(.TappedReply, fromViewController:self)
    }

But the real world often requires state. Maybe your analytics team found duplicate taps, so they've asked you to only log `.TappedReply` once per view controller instance.
    
    
    class IncomingMessagePrompt:UIViewController {
      lazy var analytics:Analytics = { Analytics(controller:self) }()
      func didTapReply(sender:AnyObject){
        analytics.recordEvent(.TappedReply)
      }
    }

In the real world, maybe you want to keep all of your analytics requests in a single queue, so you can throttle them. _Maybe_ a singleton would be acceptable. At least reduce its scope:
    
    
    Analytics(controller:self, queue:AnalyticsQueue.sharedQueue)

### Singletons Cross Boundaries

Here's a fun bug I hit while refactoring:
    
    
    class Account:NSObject {
      static sharedAccount = Account()
      var homeTimeline:Timeline()
      var preferences:AccountPreference
      init(){
          preferences = AccountPreference.loadFromDisk()
          homeTimeline = Timeline()
          super.init()
      }
    }
    
    class Timeline:NSObject {
      init(){
        self.orderPreference = Account.sharedAccount.preferences.timelineOrder
        super.init()
      }
    }

This code fails during initialization, because the `Timeline` object accesses the account singleton while we're in the middle of initializing it. Imagine this faux pas buried deeper in the object graph.

What if we want to unit test `Timeline`? We have to mock the `Account` object, and return a mock preferences object. Ugh.

If anyone can get ahold of an object, any object in your app can be tangled with hidden dependencies.

Let's refactor:
    
    
    init(){
      preferences = AccountPreference.loadFromDisk()
      homeTimeline = Timeline(order:preferences.timelineOrder)
      super.init()
    }

This clarifies ownership. `Account` configures its child, `Timeline`. It happens to pull that configuration from preferences, but we could assign any value we want in tests.[2](https://sandofsky.com/blog/singletons.html)

It's trivial to decouple view controllers with the Account singleton. Compare before:
    
    
    let news = NewsFeedController()
    self.showViewController(news)

…with after:
    
    
    let news = NewsFeedController(account:self.account)
    self.showViewController(news)

### On Best Practices

For very simple apps, you'll never run into problems with singletons. When you're first building an app, best practices can seem like overkill. "You aren't going to need it," someone says. "You can always refactor!"

In my experience, it's significantly harder to pay down technical debt than to do things right the first time. When you paint yourself into a corner, and your product manager asks for a change that _should_ be quick, there's a lot of pressure to slap on _just one hack_.

This isn't about designing around imaginary features, like supporting multiple accounts. It's about having no idea what tomorrow brings. It's worth a little extra work to retain flexibility.
