# Use Split View to Show two Controllers

_Captured: 2016-02-06 at 00:06 from [developer.xamarin.com](https://developer.xamarin.com/recipes/ios/content_controls/split_view/use_split_view_to_show_two_controllers/)_

# Recipe

There are three components required to make a split view work: the master view, the detail view and the split view that encapsulates them both.

[ ![](https://developer.xamarin.com/recipes/ios/content_controls/split_view/use_split_view_to_show_two_controllers/Images/Picture_1.png)](https://developer.xamarin.com/recipes/ios/content_controls/split_view/use_split_view_to_show_two_controllers/Images/Picture_1.png)

To create these views and wire them up:

  1. Create a subclass of `DialogViewController` for the master view:
    
    
    public class MasterViewController : DialogViewController {
        public MasterViewController () : base (null)
        {
           Root = new RootElement ("Items") {
              new Section () {
                 from num in Enumerable.Range (1, 10)
                 select (Element) new StringElement("Item " + num)
              }  
           };
        }
        public override bool ShouldAutorotateToInterfaceOrientation
          (UIInterfaceOrientation toInterfaceOrientation)
        {
           return true;
        }
    }

  1. Create a subclass of `UIViewController` for the detail view:
    
    
    public class DetailViewController : UIViewController
    {
        UILabel label;
        public DetailViewController () : base()
        {
            View.BackgroundColor = UIColor.White;
            label = new UILabel(new CGRect(100,100,300,50));
            label.Text = "This is the detail view";
            View.AddSubview (label);
        }
        public override bool ShouldAutorotateToInterfaceOrientation (UIInterfaceOrientation toInterfaceOrientation)
        {
            return true;
        }
    }

  1. Create a subclass of `UISplitViewController`, and assign the master and detail classes to its `ViewControllers` property.
    
    
    public class SplitViewContoller : UISplitViewController
    {
        UIViewController masterView, detailView;
        public SplitViewContoller () : base()
        {
            // create our master and detail views
            masterView = new MasterViewController ();
            detailView = new DetailViewController ();
            // create an array of controllers from them and then
            // assign it to the controllers property
            ViewControllers = new UIViewController[]
                    { masterView, detailView }; // order is important
        }
        public override bool ShouldAutorotateToInterfaceOrientation
            (UIInterfaceOrientation toInterfaceOrientation)
        {
            return true;
        }
    }

  1. Finally create and assign the `SplitViewController` in the `AppDelegate`:
    
    
    splitView = new SplitViewContoller();
    window.RootViewController = splitView;

# Additional Information

The example above does not include any interaction between the views. See the [Communicating Between Detail and Master Controllers] recipe. It also does not allow you to view the master view in portrait orientation, which is explained in the [Showing and Hiding the Master View Button (SplitView)] recipe.

You can also force the master view to appear in portrait orientation, by implementing the following delegate in the `SplitViewController`:
    
    
    ShouldHideViewController = (svc, viewController, inOrientation) => {
        return false; // default behaviour is true
    };
