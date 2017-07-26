# Push / Pop modal SFSafariViewController (Hacking swipe from edge gesture)

_Captured: 2015-10-16 at 10:23 from [www.stringcode.co.uk](http://www.stringcode.co.uk/push-pop-modal-sfsafariviewcontroller-hacking-swipe-from-edge-gesture/)_

In iOS 9 Apple introduced SFSafariViewController. In a nutshell it pretty much runs full Safari in your app. This is great as user gets all Keychain passwords, Safari extensions access, cookies, session data, etc. All of that done securely as the SFSafariViewController spins up a separate process, so that the app does not have access to SFSafariViewController's content (More info [here](https://developer.apple.com/videos/play/wwdc2015-504/)).

That's all great, however there is problem. Result of pushing SFSafariViewController in UINavigationsController is loss of default bar behaviour, which looks pretty bad. So really, only option is to present it modally. This has is own drawbacks. Apple has made unfortunate choice of placing the done button to top right corner. This makes it very difficult to dismiss when using the phone one handed. Although, I don't really think positioning it anywhere else would solve the problem. Now standard swipe from the edge of the screen gesture really is the way to go.

My solution to this problem is to trade swiping from the edge to go back in browsing history for dismissing view view controller. I create a subclass of SFSafariViewController and add a 5 points wide UIView to it. View covers its entire height. Background colour of the view is imperceptibly transparent white. Right thing to do would be to override `hitTest:` and have it entirely transparent, but this is quick and dirty hack :-). This view is in app's process and therefore accessible to us.
    
    
    import UIKit
    import SafariServices
    
    class SCSafariViewController: SFSafariViewController {
        var edgeView: UIView? {
            get {
                if (_edgeView == nil && isViewLoaded()) {
                    _edgeView = UIView()
                    _edgeView?.translatesAutoresizingMaskIntoConstraints = false
                    view.addSubview(_edgeView!)
                    _edgeView?.backgroundColor = UIColor(white: 1.0, alpha: 0.005)
                    let bindings = ["edgeView": _edgeView!]
                    let options = NSLayoutFormatOptions(rawValue: 0)
                    let hConstraints = NSLayoutConstraint.constraintsWithVisualFormat("|-0-[edgeView(5)]", options: options, metrics: nil, views: bindings)
                    let vConstraints = NSLayoutConstraint.constraintsWithVisualFormat("V:|-0-[edgeView]-0-|", options: options, metrics: nil, views: bindings)
                    view?.addConstraints(hConstraints)
                    view?.addConstraints(vConstraints)
                }
                return _edgeView
            }
        }
        private var _edgeView: UIView? 
    }
    

In presentation completion handle I add UIScreenEdgePanGestureRecognizer to our edge view.
    
    
        @IBAction func showSafariViewController(sender: AnyObject){
            let safariViewController = SCSafariViewController(URL: NSURL(string: "http://www.stringcode.co.uk")!)
            safariViewController.delegate = self;
            safariViewController.transitioningDelegate = self
            self.presentViewController(safariViewController, animated: true) { () -> Void in
                let recognizer = UIScreenEdgePanGestureRecognizer(target: self, action: "handleGesture:")
                recognizer.edges = UIRectEdge.Left
                safariViewController.edgeView?.addGestureRecognizer(recognizer)
            }
        }
    

Then it's a simple matter of creating custom transition animation. It's a standard boiler plate. I also add shadow when transitioning views, to mimic UINavigation's controller push and pop animations. Included in [sample code](https://github.com/stringcode86/SCSafariViewController). I really think this is the least bad trade off. In reality swipe from the edge to go to previous page in SFSafariViewController still works. You have to swipe from very close to the edge, but not quite. No one will know about this, so it's useless. Sample project can be found [here](https://github.com/stringcode86/SCSafariViewController). Repo currently only contains Swift sample. As I need it for my ObjC only app, I will add ObjC sample as well soon. For questions or suggestions Im [@stringcode](https://twitter.com/stringcode). Thank you for reading!
