# Show and Hide the Master View Button

_Captured: 2016-02-06 at 00:08 from [developer.xamarin.com](https://developer.xamarin.com/recipes/ios/content_controls/split_view/show_and_hide_the_master_view_button/)_

# Recipe

The UISplitViewController can help display a button & popover for the master view controller when it is hidden. This recipe shows how to add a toolbar to the detail view and implement the popover button.

[ ![](https://developer.xamarin.com/recipes/ios/content_controls/split_view/show_and_hide_the_master_view_button/Images/SplitViewController2.png)](https://developer.xamarin.com/recipes/ios/content_controls/split_view/show_and_hide_the_master_view_button/Images/SplitViewController2.png)

To show and hide the master view:

  1. Start with an existing implementation of `UISplitViewController`, such as the [Using a Split View to Show Two Controllers](/recipes/ios/content_controls/split_view/use_split_view_to_show_two_controllers) recipe.
  1. Add a toolbar the `DetailViewController` so that there is a host for the popover button (when it is required):
    
    
    // add a toolbar to host the master view popover (when it is required, in portrait)
    toolbar = new UIToolbar(new CGRect(0, 0, View.Frame.Width, 30));
    toolbar.AutoresizingMask = UIViewAutoresizing.FlexibleWidth;
    View.AddSubview(toolbar);

  1. Implement two methods on the `DetailViewController` that will be used to show and hide the button.
    
    
    /// <summary>
    /// Shows the button that allows access to the master view popover
    /// </summary>
    public void AddContentsButton (UIBarButtonItem button)
    {
        button.Title = "Contents";
        toolbar.SetItems (new UIBarButtonItem[] { button }, false );
    }
    /// <summary>
    /// Hides the button that allows access to the master view popover
    /// </summary>
    public void RemoveContentsButton ()
    {
        toolbar.SetItems (new UIBarButtonItem[0], false);
    }

  1. Implement a `UISplitViewControllerDelegate` the `SplitViewController` to control when the button is shown or hidden:
    
    
    public class SplitViewDelegate : UISplitViewControllerDelegate {
        public override bool ShouldHideViewController (UISplitViewController svc, UIViewController viewController, UIInterfaceOrientation inOrientation)
        {
            return inOrientation == UIInterfaceOrientation.Portrait
                || inOrientation == UIInterfaceOrientation.PortraitUpsideDown;
        }
        public override void WillHideViewController (UISplitViewController svc, UIViewController aViewController, UIBarButtonItem barButtonItem, UIPopoverController pc)
        {
            DetailViewController detailView = svc.ViewControllers[1] as DetailViewController;
            detailView.AddContentsButton (barButtonItem);
        }
        public override void WillShowViewController (UISplitViewController svc, UIViewController aViewController, UIBarButtonItem button)
        {
            DetailViewController detailView = svc.ViewControllers[1] as DetailViewController;
            detailView.RemoveContentsButton ();
        }
    }

  1. Set the `Delegate` in the `SplitViewController's` constructor:
    
    
    Delegate = new SplitViewDelegate();

# Additional Information

The example above does not include any interaction between the views. See the [Communicating Between Detail and Master Controllers](https://developer.xamarin.com/recipes/ios/content_controls/split_view/communicate_between_master_and_detail_controllers) recipe.

You can change the behavior of the `SplitViewController` to always show the master view (or always show the button & popover) by returning `false` or `true` respectively from `ShouldHideViewController`.
