# How To Build An App Without Interface Builder – Part 6: Show Data

_Captured: 2015-09-01 at 10:55 from [swiftandpainless.com](http://swiftandpainless.com/)_

In [part 5](http://swiftandpainless.com/how-to-build-an-app-without-interface-builder-part-5-data-model/) we have seen how we can add birthdays to the app. But the data was just printed to the debug console.

In this post we want to implement that the birthdays we add are actually shown in the birthday list.

Open BirthdaysListDataProvider and add the following property:

Add the following code outside of the BirthdaysListDataProvider class:

12345 
extensionBirthdaysListDataProvider{funcaddBirthday(birthday:Birthday){birthdays.append(birthday)}}

Replace the code inside of

with this:

Replace the line cell.textLabel?.text="Row: (indexPath.row)" with the following code:

Now add the following code to the end of contactPicker(_:didSelectContact:):

Build and run. Tap the plus button and select John Appleseed. You should see something like this:

![Simulator Screen Shot 30.08.2015 21.43.50](http://swift.eltanin.uberspace.de/wp-content/uploads/2015/08/Simulator-Screen-Shot-30.08.2015-21.43.50-200x300.png)

> _[Simulator Screen Shot 30.08.2015 21.43.50](http://swift.eltanin.uberspace.de/wp-content/uploads/2015/08/Simulator-Screen-Shot-30.08.2015-21.43.50.png)_

Great! Now we need a cell that actually can show the name of the person and his/her birthday. Let's add a first version of a custom table view cell. Remember, later we want to have a nice progress show in the cell behind the name. But for now it is enough to show the name and the birthday.

Select **File / New / File…**, chose **iOS / Source / Cocoa Touch Class**, click **Next**. Put in the name **BirthdayCell**, make it a subclass of **UITableViewCell** and click **Next**. Select the BirthdaysList folder and click **Create**. Open the new created class and remove the two methods from the Xcode template.

Add these two properties:

Xcode will complain that

> Class 'BirthdayCell' has no initializers 

True. But we are going to change that. Add these two initializers:

123456789101112131415161718192021222324252627 
overrideinit(style:UITableViewCellStyle,reuseIdentifier:String?){nameLabel=UILabel()nameLabel.translatesAutoresizingMaskIntoConstraints=falsebirthdayLabel=UILabel()birthdayLabel.translatesAutoresizingMaskIntoConstraints=falsesuper.init(style:style,reuseIdentifier:reuseIdentifier)addSubview(nameLabel)addSubview(birthdayLabel)letviews=["name":nameLabel,"birthday":birthdayLabel]varlayoutConstraints=[NSLayoutConstraint]()layoutConstraints.append(nameLabel.centerXAnchor.constraintEqualToAnchor(centerXAnchor))layoutConstraints.append(nameLabel.centerYAnchor.constraintEqualToAnchor(centerYAnchor))layoutConstraints+=NSLayoutConstraint.constraintsWithVisualFormat("[birthday]-|",options:[],metrics:nil,views:views)layoutConstraints+=NSLayoutConstraint.constraintsWithVisualFormat("V:[birthday]|",options:[],metrics:nil,views:views)NSLayoutConstraint.activateConstraints(layoutConstraints)}required init?(coder aDecoder:NSCoder){fatalError("init(coder:) has not been implemented")}

The constrains in the initializer center the nameLabel and put the birthdayLabel at the bottom right corner. The second initializer is needed because it is a required initializer of UIView and in Swift we need to implement all required initializer as soon as we implement one initializer ourselves.

No let's use our new shiny table view cell. Open **BirthdaysListDataProvider.swift** and replace in registerCellsForTableView(_:) UITableViewCell.self with BirthdayCell.self.

Replace the code in tableView(_:cellForRowAtIndexPath:) with this:

1234567 
letcell=tableView.dequeueReusableCellWithIdentifier(cellIdentifer,forIndexPath:indexPath)as!BirthdayCellletbirthday=birthdays[indexPath.row]cell.nameLabel.text=birthday.firstNamecell.birthdayLabel.text="\\(birthday.birthday.day) \\(birthday.birthday.month)"returncell

Build and run. Add a person to the list. The result should look like this:

![Simulator Screen Shot 31.08.2015 20.50.19](http://swift.eltanin.uberspace.de/wp-content/uploads/2015/08/Simulator-Screen-Shot-31.08.2015-20.50.19-200x300.png)

> _[Simulator Screen Shot 31.08.2015 20.50.19](http://swift.eltanin.uberspace.de/wp-content/uploads/2015/08/Simulator-Screen-Shot-31.08.2015-20.50.19.png)_

That's it for today. Next time we will make the table view cell nicer.

![Screen Shot 2015-08-16 at 09.40.41](http://swift.eltanin.uberspace.de/wp-content/uploads/2015/08/Screen-Shot-2015-08-16-at-09.40.41.png)

> _[Screen Shot 2015-08-16 at 09.40.41](http://swift.eltanin.uberspace.de/wp-content/uploads/2015/08/Screen-Shot-2015-08-16-at-09.40.41.png)_

![Birthdays](http://swift.eltanin.uberspace.de/wp-content/uploads/2015/08/Birthdays.png)

![Screen Shot 2015-07-24 at 17.58.19](http://swift.eltanin.uberspace.de/wp-content/uploads/2015/08/Screen-Shot-2015-07-24-at-17.58.19.png)

> _[Screen Shot 2015-07-24 at 17.58.19](http://swift.eltanin.uberspace.de/wp-content/uploads/2015/08/Screen-Shot-2015-07-24-at-17.58.19.png)_
