# Communicate Between Master and Detail Controllers

_Captured: 2016-02-06 at 00:08 from [developer.xamarin.com](https://developer.xamarin.com/recipes/ios/content_controls/split_view/communicate_between_master_and_detail_controllers/)_

# Recipe

When a selection is made in the master view the detail view should be updated accordingly (and if the master view is in a popover, the popover should be automatically dismissed). This recipe shows how to communicate between the master and detail views to make that happen.

To get row selection in the master view to change the detail view:

  1. Start with an existing implementation of `UISplitViewController` (such as the [Using a Split View to Show Two Controllers](http://developer.xamarin.com/recipes/ios/content_controls/split_view/use_split_view_to_show_two_controllers/) recipe).
  1. Add an event handler and an `EventArgs` subclass to the `MasterViewController` which will be used to communicate with the detail view:
    
    
    public event EventHandler<RowClickedEventArgs> RowClicked;
    public class RowClickedEventArgs : EventArgs
    {
           public int Item { get; set; }
           public RowClickedEventArgs(int item) : base()
           { this.Item = item; }
    }

  1. Add a delegate to each row in the `MasterViewController` constructor, when clicked it will call the `RowClicked` event handler passing a new `RowClickedEventArgs` containing information about the row that was clicked.
    
    
    Root = new RootElement ("Items") {
        new Section () {
            from num in Enumerable.Range (1, 10)
            select (Element) new MonoTouch.Dialog.StringElement("Item " + num,
            delegate {
                if (RowClicked != null)
                    RowClicked (this, new RowClickedEventArgs(num));
            })
        }
    };}

  1. Add a public property `Popover` to the `DetailViewController` so that we can track when it is showing and hide it when a selection is made:
    
    
    public UIPopoverController Popover {get;set;}

  1. Create an `Update()` method in the `DetailViewController` which will be called when a new selection is made in the master view:
    
    
    public void Update (string text) {
           label.Text = String.Format (content, text);
           // dismiss the popover if currently visible
           if (Popover != null)
                  Popover.Dismiss (true);
    }

  1. Attach a handler to the `RowClicked` event to the `MasterViewController` in the `SplitViewController`. This lets the `SplitViewController` act as the go-between, listening for `RowClicked` events that happen in the master view, and calling the `Update()` method in the detail view:
    
    
    masterView.RowClicked += (object sender, MasterViewController.RowClickedEventArgs e) => {
        detailView.Update (e.Item);
    };

  1. Finally, set the new `DetailViewController` `Popover` property whenever the `SplitViewController` shows or hides the popover. This will allow the `DetailViewController` to dismiss the popover when a selection is made: 
    
    
    WillHideViewController += (object sender, UISplitViewHideEventArgs e) => {
           detailView.Popover = e.Pc;
           detailView.AddContentsButton(e.BarButtonItem);
    };
    WillShowViewController += (object sender, UISplitViewShowEventArgs e) => {
           detailView.Popover = null;
           detailView.RemoveContentsButton ();
    };

# Additional Information

In this example we just pass an `int` value from the selected row to the detail view, however you can modify the `RowClickedEventArgs` to pass whatever information you need.
