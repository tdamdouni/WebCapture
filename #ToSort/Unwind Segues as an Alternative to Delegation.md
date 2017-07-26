# Unwind Segues as an Alternative to Delegation

_Captured: 2015-11-06 at 09:39 from [useyourloaf.com](http://useyourloaf.com/blog/unwind-segues-as-an-alternative-to-delegation.html)_

I have never been sure why and when I should use an unwind segue in a Storyboard. One use I am seeing more often is to replace the use of a delegate protocol to dismiss a presented view controller and pass data back to the presenting view controller. Let's compare the two approaches.

### Using Delegation

It is common practise to use a delegate protocol to pass data from the presented view controller back to the presenting view controller. The presenting view controller, after retrieving the data, dismisses the presented view controller. Consider the situation where I have some property in a master view controller that I want to display and change in a detail view controller.

In the detail view controller, I can define the delegate protocol that our presenting view controller will adopt to dismiss the detail view controller:
    
    
    protocol DetailViewControllerDelegate {
      func didDismissDetail(sender: DetailViewController)
    }
    

I will also need an optional delegate property as part of the public interface of the view controller:
    
    
    var delegate:DetailViewControllerDelegate? = nil
    

Now in the action for the control that should dismiss the view controller check for and call the delegate passing self as the sender:
    
    
    @IBAction private func doneAction(sender: UIBarButtonItem) {
      if let delegate = self.delegate {
        delegate.didDismissDetail(self)
      }
    }
    

In the presenting view controller, adopt the protocol and implement the delegate to retrieve the data and dismiss the detail view controller:
    
    
    extension ViewController: DetailViewControllerDelegate {
      func didDismissDetail(sender: DetailViewController) {
        status = sender.status
        dismissViewControllerAnimated(true, completion: nil)
        configureView()
      }
    }
    

Also remember to set the delegate when presenting the detail view controller. This could be in the prepareForSegue method:
    
    
     // Pass data into the view controller and set
     // ourselves as the delegate
     detailViewController.status = status
     detailViewController.delegate = self
    

This is a lot of typing but the intent is clear for all to see.

### What is an unwind segue

An unwind segue allows us to go back one or more steps to a view controller already in our navigation hierarchy. You create unwind segues in Interface Builder but unlike normal segues you do not specify the destination view controller. Instead the segue searches at runtime for the nearest view controller in the view hierarchy that implements the specified unwind action.

An unwind action has only two properties:

  * A return type of IBAction
  * A single parameter of type UIStoryboardSegue

Note that when configuring an unwind segue in Interface Builder it shows all available unwind actions so you need to make the method name unique and meaningful. To add the unwind action to our master view controller:
    
    
    @IBAction func unwindToMainViewController(sender: UIStoryboardSegue) {
      if let sourceViewController = sender.sourceViewController
                                    as? DetailViewController {
        status = sourceViewController.status
        configureView()
      }
    }
    

The UIStoryboardSegue parameter gives us access to the presented view controller in the sourceViewController property. This provides a simple mechanism, similar to the delegate protocol, to pass data back to the presenting view controller before dismissing the presented view controller.

To add the unwind segue to the Storyboard control-drag from the Done button in the detail view controller to the orange Exit icon in the scene menu bar:

![](http://useyourloaf.com/assets/images/2015/2015-10-31-001.png)

Interface Builder shows all the unwind actions it knows about. In this case we have only the one we created in the master view controller:

![](http://useyourloaf.com/assets/images/2015/2015-10-31-002.png)

If you have the unwind segue setup you should see it listed in the outline for the scene:

![](http://useyourloaf.com/assets/images/2015/2015-10-31-003.png)

The "Done" button now triggers the unwind segue which takes care of dismissing the view controller and finding the unwindToMainViewController method in the presenting view controller.

Compared to the delegate approach this is less code but is it any better? It needs storyboards which I know is a non-starter for some. However not having to create the delegate protocol is a big time saver. What do you think, do you use unwind segues and if so when?

### Further Reading

  * [Technical Note TN2298 Using Unwind Segues](https://developer.apple.com/library/ios/technotes/tn2298/_index.html)
