# Hiding empty table view rows

_Captured: 2016-02-15 at 16:58 from [useyourloaf.com](http://useyourloaf.com/blog/hiding-empty-table-view-rows/)_

_A quick tip for an annoying problem that I see asked enough to suspect it is worth sharing._

You have a **plain style table view with insufficient rows to fill the screen**. In that situation UIKit fills the space below the rows in the table with empty rows. Here is what it looks like with the cell separator in red to make them more visible:

![Extra table view rows](http://useyourloaf.com/assets/images/2016/2016-02-14-001.png)

**How do you get rid of those ugly extra rows?** It is not obvious but it is easy once you know how.

### Removing the separator

One quick solution is just to get rid of the separator. Setting the separator style to none in the viewDidLoad method of the table view controller will do that:
    
    
    // Objective-C
    self.tableView.separatorStyle = UITableViewCellSeparatorStyleNone;
    
    // Swift
    tableView.separatorStyle = .None
    

You can do the same in Interface Builder:

![No Separator](http://useyourloaf.com/assets/images/2016/2016-02-14-005.png)

This is not a solution if we want the separator for our real cells. A better approach is to **add a footer view to the table**.

### Adding a Footer View

UIKit does not create the empty rows when the table has a footer view displayed below the table cells. I don't want a footer in this case but we can still add one with zero height so it is not visible to the user. In the viewDidLoad method of our table view controller **create a new UIView with a zero rect frame** and use it to set the **tableFooterView** property of the table view:
    
    
    // Objective-C
    self.tableView.tableFooterView = [[UIView alloc]
        initWithFrame:CGRectZero];
    
    // Swift
    tableView.tableFooterView = UIView(frame: .zero)
    

This fixes the problem without removing the separators for the real cells:

![Extra separators removed](http://useyourloaf.com/assets/images/2016/2016-02-14-004.png)

### Adding a Footer View in Interface Builder

It is not obvious how you add a footer (or header) view to a table with Interface Builder. The code solution is so easy you could ask why bother? Well perhaps you have a static table view created in a Storyboard that does not need a custom table view controller subclass. Creating one just to fix this problem seems a waste.

The solution is to drop a UIView into the table view **just below** the table view cells. In the screenshot below I have made it green so you can see it. You can set a table view header in a similar way by dropping a view just above the cells.

![Footer view](http://useyourloaf.com/assets/images/2016/2016-02-14-002.png)

You can then set the height of the view to zero in the inspector:

### Not seeing the separators in the simulator?

One final bonus tip that catches me out from time to time. If you are using the simulator and not seeing the separators check the **simulator scale setting**. On my screen the **separator lines are not visible** for larger devices like the iPhone 6 if the **scale factor is not 100%**. This caused me some confusion during the iOS 9 betas when a bug was causing the separators to show even if you set the style to none.
