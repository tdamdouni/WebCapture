# Swift: Create a login app with Parse.com PFUser & Keychain Locksmith

_Captured: 2015-10-17 at 13:12 from [ios-blog.co.uk](http://ios-blog.co.uk/tutorials/swift-create-a-login-app-with-parse-com-pfuser-keychain-locksmith/)_

![parse com logo](http://ios-blog.co.uk/wp-content/uploads/2014/11/parse-logo.jpg)

> _parse com logo_

This tutorial optimising the specialised Parse.com class PFuser to verify login credentials and uses an awesome library called Locksmith Keychain that stores information in the iOS Keychain to remember whether or not the user is currently logged in.

### Download the code

[Jump straight to the download](http://ios-blog.co.uk/tutorials/swift-create-a-login-app-with-parse-com-pfuser-keychain-locksmith/)

### Prerequisites

This tutorial assumes that you have at least a basic understanding of the Swift programming language, the structure of Xcode projects and finally how to create a new single view application in Xcode 6. If you need to be refreshed on any of these head over to our [Swift Tutorials](http://ios-blog.co.uk/swift-tutorials/) page for further reading.

It also assumes that you know how to add the Parse.com iOS SDK to your swift project, creating the bridging header and adding the necessary frameworks. If you do not know this, please check out this tutorial:

Finally, you will also need to head over and download this library: [Locksmith.Keychain](https://github.com/matthewpalmer/Locksmith) created by Matthew Palmer.

### Getting Started

Once you have all the required files and have set up your Parse project you need to Grab two files from the Locksmith project: **Locksmith.swift** and **LocksmithRequest.swift** and add them to your project navigation area.

### Create new view controllers

Click on **Main.Storyboard** and from the Xcode Object library, drag in a new View Controller.

![xcode 6.1 object library view controller](http://ios-blog.co.uk/wp-content/uploads/2014/11/xcode-6.1-object-library-view-controller.png)

> _xcode 6.1 object library view controller_

You now should have two UIViewControllers on your storyboard. I have resized mine to make them smaller and fit on my screen. Now head over to the **Identity Inspector** for that new UIViewController and change the class to: **logInViewController**

![xcode 6.1 identity inspector class](http://ios-blog.co.uk/wp-content/uploads/2014/11/xcode-6.1-identity-inspector-class.png)

> _xcode 6.1 identity inspector class_

We now need to create a new swift file and link this up to our new view. Head over to **File > New > File ** and select swift file. Save the file as: **logInViewController**. That file, once saved should automatically open. If it does not then click on ** logInViewController.swift** in your Project Navigation area.

You should see that there is already some code in there:
    
    
    1  
    2  
    3  
    4  
    5  
    6  
    7  
    8  
    9  
    
    //  
    
    //  logInViewController.swift  
    
    //  swiftLoginAppTutorial  
    
    //  
    
    //  Created by  Mark Petherbridge  on 29/11/2014.  
    
    //  Copyright (c) 2014 iOS-Blog. All rights reserved.  
    
    //  
    
      
    
    import Foundation
    
    
    

The first part is just comments and the second is importing the **Foundation.framework**.

We now need to add in a class. Your new file should look like this:
    
    
    1  
    2  
    3  
    4  
    5  
    6  
    7  
    8  
    9  
    10  
    11  
    12  
    13  
    
    //  
    
    //  logInViewController.swift  
    
    //  swiftLoginAppTutorial  
    
    //  
    
    //  Created by  Mark Petherbridge  on 29/11/2014.  
    
    //  Copyright (c) 2014 iOS-Blog. All rights reserved.  
    
    //  
    
      
    
    import Foundation  
    
      
    
    class logInViewController : UIViewController {  
    
          
    
    }
    
    
    

That has now been linked.

### Create Login UI Elements

Go back to **Main.storyboard** and drag these six UI Elements from your object library onto your view:

  * 2 x UILabel
  * 2 x UITextField
  * 1 x UISwitch
  * 1 x UIButton

I have renamed the labels and the buttons and also added in placeholder text for the UITextFields

![UIViewController Login app elements](http://ios-blog.co.uk/wp-content/uploads/2014/11/UIViewController-Login-app-elements.png)

> _UIViewController Login app elements_

Hopefully you should know how to link these elements to your ViewController so I wont go into detail. However your view controller should now have these lines of code:
    
    
    1  
    2  
    3  
    4  
    5  
    6  
    7  
    8  
    9  
    10  
    
    @IBOutlet var loginInitialLabel: UILabel!  
    
    @IBOutlet var logInSavePassLabel: UILabel!  
    
          
    
    @IBOutlet var loginInUserTextField: UITextField!  
    
    @IBOutlet var logInPassTextField: UITextField!  
    
          
    
    @IBOutlet var logInSavePassSwitch: UISwitch!  
    
          
    
    @IBAction func logInActionButton(sender: AnyObject) {  
    
    }
    
    
    

Now, You should have all the elements linked up.

### Validate and Query the Parse PFUser

The first thing that we need to check is that the UITextfields for Username and Password are not empty. We do this by creating an **If-Else**. We will place this within our **IBAction**:
    
    
    1  
    2  
    3  
    4  
    5  
    6  
    
    if loginInUserTextField.text != "" && logInPassTextField.text != "" {  
    
        // Not Empty, Do something.  
    
    } else {  
    
        // Empty, Notify user  
    
        self.loginInitialLabel.text = "All Fields Required"  
    
    }
    
    
    

The above code will check that both of the UItextFields are not empty. If they are empty then the UILabel: loginInitialLabel will change to say "All Fields Required". Great. So now we know that something has been entered the next thing we need to do is check whether or not the save password switch is **On** or **Off**. We are adding this feature in so that if the user wishes to save their credentials to the iOS Keychain then they can. This requires another If-Else statement like so:
    
    
    1  
    2  
    3  
    4  
    5  
    
    if logInSavePassSwitch.on {  
    
        // If the user has selected YES to saving password  
    
    } else {  
    
       // If the user has selected NO to saving password  
    
    }
    
    
    

Now we get to use **PFUser.logInWithUsernameInBackground** This will make a synchronous request to your Parse.com backend service app and allow us to query the user table for credentials.

Here is the code we need to use within the YES section of the above If-Else statement:
    
    
    1  
    2  
    3  
    4  
    5  
    6  
    7  
    8  
    9  
    
    PFUser.logInWithUsernameInBackground(loginInUserTextField.text, password:logInPassTextField.text) {  
    
        (user: PFUser!, error: NSError!) -> Void in  
    
            if user != nil {  
    
                // Yes, User Exists  
    
                self.loginInitialLabel.text = "User Exists"  
    
            } else {  
    
                // No, User Doesn't Exist  
    
            }  
    
    }
    
    
    

Right, Now you have done this we now need to link up the views.

### Linking the Views

Throughout the development of this project you make have noticed this Warning:

Warning: Unsupported Configuration: Scene is unreachable due to lack of entry points and does not have an identifier for runtime access via -instantiateViewControllerWithIdentifier:.

This is fine as we are about to fix this, it's just Xcode's way of saying Hey! how are you planning to show this view?

Go back to your Main.Storyboard and on your original View Controller, CTRL + Drag from this button to your new View Controller:

![xcode 6.1 view controller link](http://ios-blog.co.uk/wp-content/uploads/2014/11/xcode-6.1-view-controller-link.png)

> _xcode 6.1 view controller link_

You will then be presented with this pop up dialogue:

![xcode 6.1 show view](http://ios-blog.co.uk/wp-content/uploads/2014/11/xcode-6.1-show-view.png)

> _xcode 6.1 show view_

Click show. This will create a Segue between the two views. We now need to name this Segue so we can utilise it later. Click the Segue:

and in the property inspector for that Segue name it to: **logInViewSegue**:

![xcode 6.1 name segue](http://ios-blog.co.uk/wp-content/uploads/2014/11/xcode-6.1-name-segue.png)

> _xcode 6.1 name segue_

That is now done. The next thing we need to do is check whether or not the user is already logged in by querying the Keychain and If not show them the Login View Controller.

### Query Keychain with Locksmith

At the top of your **ViewController.swift** file we need to declare some constants. in-between the class definition add in these lines, so your controller file will look like:
    
    
    1  
    2  
    3  
    4  
    5  
    6  
    7  
    
    class ViewController : UIViewController {  
    
      
    
    let service = "swiftLogin"  
    
    let userAccount = "swiftLoginUser"  
    
    let key = "RandomKey"  
    
      
    
    }
    
    
    

and next, in the **viewDidAppear** function we need to perform a check to see if there is already a keychain item. If there isn't, then the user will need to login - we will then direct them to the other view using **performSegueWithIdentifier**. The **viewDidAppear** function might not be there so you might need to add it all on. Here is that function in full:
    
    
    1  
    2  
    3  
    4  
    5  
    6  
    7  
    8  
    9  
    
    override func viewDidAppear(animated: Bool) {  
    
    let (dictionary, error) = Locksmith.loadData(forKey: key, inService: service, forUserAccount: userAccount)  
    
                  
    
    if let dictionary = dictionary {  
    
        // User is already logged in, Send them to already logged in view.  
    
    } else {  
    
       // Not logged in, send to login view controller  
    
    }  
    
    }
    
    
    

Now, this is where we use the **performSegueWithIdentifier**. In the else part of the above statement we need to add in this line:
    
    
    1  
    
    self.performSegueWithIdentifier("logInViewSegue", sender: self)
    
    
    

That is it, Run your app and check it out.

### Extra Tasks

I have deliberately left a few things out for this app to give you a chance to play around and develop the app further. Give it a go and try these out:

  * Create a new viewController for users to sign up. Hint: There is a tutorial on this here [Swift: Create user sign up based app with Parse.com using PFUser](http://ios-blog.co.uk/tutorials/swift-create-user-sign-up-based-app-with-parse-com-using-pfuser//?utm_source=internalLink&utm_medium=internalLink&utm_term=internalLink&utm_content=internalLink&utm_campaign=internalLink)
  * Save a keychain item when the user has the save password switch selected to on. Hint: use locksmith: Locksmith.saveData(["some key": "\\(NSDate())"], forKey: self.key, inService: self.service, forUserAccount: self.userAccount)
  * Create a new viewController so that when the users do log in, Instead of updating the label they are directed to a new view
  * On the logged In viewController - create a log out button that will delete the keychain item and send the user back to the login view. Hint: Locksmith.deleteData(forKey: key, inService: service, forUserAccount: userAccount) 

### Download

Ok, So I have created this app ready for you and also completed the additional extras (except the signup feature) for those who don't want to mess around and just want the code. Help us out, Like us with one of the social media platforms below and the code will be yours.

I really hoped you liked this tutorial. Any questions, problems and/or comments please post them below and I will respond as soon as I am able to.
