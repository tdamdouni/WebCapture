# Swift: How to send a POST Request to a PHP Script

_Captured: 2015-10-11 at 13:34 from [ios-blog.co.uk](http://ios-blog.co.uk/tutorials/swift-how-to-send-a-post-request-to-a-php-script/)_

![swift post to php](http://ios-blog.co.uk/wp-content/uploads/2014/12/swift-post-php.png)

> _swift post to php_

This tutorial will show you how to send a POST request in Swift to a PHP script on your server.

There are many fantastic advantages to connecting your Swift application to a PHP Web Service. It opens up fantastic opportunities for user registration, database querying and many more.

If you do not have access to a PHP server or just simply cant be bothered to code your own back-end web service then there are some services out there that handle this part for you. The best one I have come across is Parse.com. If you're interested in creating an app with Parse I created a few tutorials a week or so ago to get you started:

### What are HTTP Status Codes?

Hypertext Transfer Protocol (HTTP) response status codes are responses to a request that help determine whether or not the request was successful or not. There are many different status codes for many different reasons and without polluting this article with them all I had a quick Google and found this nifty website: <http://httpstatus.es/> .

In this tutorial we are going to be looking for the Status Code **200** as this is an indication that our connection was successful and then we can proceed.

### Set up your Swift Project

Hopefully you should know how to set up a new project in Xcode 6.1 and also how to add UI Elements. Drag a UI Button onto your Main.storyboard and then link it to your **viewController** as an **IBAction**. It will ask you to give it a name. Call it whatever you like. I have called mine: **postToServerButton**.

We then need to create a function to hold our request so we can call it in the IBAction. I have called my function: **postToServerFunction**. I have added in a quick **println("Button Pressed")** into that function and now when I add **postToServerFunction()** to the **IBAction** it will run and display the 'Button Pressed' line in the console log area.

Your **ViewController.swift** should look like this:
    
    
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
    14  
    15  
    16  
    17  
    18  
    19  
    20  
    21  
    
    import UIKit  
    
      
    
    class ViewController: UIViewController {  
    
        func postToServerFunction() {  
    
            println("Button Pressed")  
    
        }  
    
          
    
        @IBAction func postToServerButton(sender: AnyObject) {  
    
                postToServerFunction()  
    
        }  
    
             
    
        override func viewDidLoad() {  
    
            super.viewDidLoad()  
    
            // Do any additional setup after loading the view, typically from a nib.  
    
        }  
    
      
    
        override func didReceiveMemoryWarning() {  
    
            super.didReceiveMemoryWarning()  
    
            // Dispose of any resources that can be recreated.  
    
        }  
    
    }
    
    
    

### The PHP

I'm not going to go into detail about PHP. I have created a quick script on my server that will check for the POST request and if it exists it will send me an email:
    
    
    1  
    2  
    3  
    4  
    5  
    
    $postVar = $_POST['data'];  
    
      
    
    if (!empty($postVar)) {  
    
        mail("email@email.com","email subject","The POST was set and button was pressed");  
    
    }
    
    
    

**Warning**: If you are attempting to connect to a database or in anyway allow someone access to your server make sure you have set up the correct techniques to stop malicious actions. For database connections the usual rule of thumb is that any variable that is been set by the user (for example Username or Password) must be escaped out. Have a look into [Preventing SQL Injection](http://stackoverflow.com/a/60496/1255945)

### Post to PHP from Swift

First, we need to declare two variables in our function.
    
    
    1  
    2  
    
    var url: NSURL = NSURL(string: "http://url.com/path/to/file.php")!  
    
    var request:NSMutableURLRequest = NSMutableURLRequest(URL:url)
    
    
    

As you can see in the PHP code above I telling the PHP to look for **$_POST['data']**. So now we need to send something in the body to that script, under the above two lines of Swift add this:
    
    
    1  
    
    var bodyData = "data=something"
    
    
    

Then we need to specify what the method we are sending in. As the post suggests (Swift: Post to PHP) we need to specify that the **HTTPMethod** is **POST**. As you might have guessed, we do this like so:
    
    
    1  
    
    request.HTTPMethod = "POST"
    
    
    

The next bit we need to add in is simply encapsulating all that together and then sending it to the server. like so:
    
    
    1  
    2  
    3  
    4  
    5  
    6  
    7  
    
    request.HTTPBody = bodyData.dataUsingEncoding(NSUTF8StringEncoding);  
    
    NSURLConnection.sendAsynchronousRequest(request, queue: NSOperationQueue.mainQueue())  
    
    {  
    
        (response, data, error) in  
    
        println(response)  
    
                     
    
    }
    
    
    

If you run your app now, you will see a response in the console log with the entire response.

### Swift: Get HTTP Status Code

So lets assume that you have an app that if the connection exists and the script runs fine then the user is sent to a new ViewController. If you just run the app above the user will be redirected regardless of whether the script fails or not. So we need to use an If statement here to check for the HTTP Status code. Make sure it is 200 and then do something if it is.

**NSURLConnection.sendAsynchronousRequest** uses **NSURLResponse** in the type signature, but as long as you're connecting over HTTP, the instance is (usually) NSHTTPURLResponse, which has the statusCode.

You can check and cast it this way:
    
    
    1  
    2  
    3  
    4  
    5  
    6  
    7  
    
    if let HTTPResponse = response as? NSHTTPURLResponse {  
    
        let statusCode = HTTPResponse.statusCode  
    
      
    
        if statusCode == 200 {  
    
            // Yes, Do something.   
    
        }  
    
    }
    
    
    

That's it. Run your app. To summarise we have used Swift to POST to a PHP script and have performed a check on the status code that it all went smoothly.

I hope you enjoyed this tutorial. Please comment below and be sure to Like and Share. Happy Coding.
