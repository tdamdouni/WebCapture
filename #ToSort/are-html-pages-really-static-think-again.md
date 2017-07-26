# Are HTML Pages Really Static? Think Again!

_Captured: 2017-02-07 at 20:38 from [dzone.com](https://dzone.com/articles/is-html-page-really-static-think-again?edition=267885&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-02-07)_

[Start coding today](https://dzone.com/go?i=155124&u=http%3A%2F%2Fplayground.qlik.com%2Fhome) to experience the powerful engine that drives data application's development, brought to you in partnership with [Qlik](https://dzone.com/go?i=155124&u=http%3A%2F%2Fplayground.qlik.com%2Fhome).

According to the definition of a static page, it shows information exactly as it is stored. So if you are building a page that shows information from the database (dynamic), then you will use a server side page like .php/.aspx/.cshtml.

As a web developer, I have heard quite often that, "An HTML page is a static page, so it cannot be used to show dynamic contents." This sounds fair but it is not totally correct. So let's discuss why an HTML page is not really a static one.

## A Simple Dynamic Operation With an HTML Page

Let's make a simple yet powerful operation with an HTML page. Here we have to make a feature through which a user is able to subscribe to a blog. This feature is quite common on the internet!

You will have an "input" and a "button." The user will enter his/her email and click the button. Upon clicking the button, his/her email should be inserted into the database table and he/she should get a thank you message.

**The HTML Page Code:**
    
    
    <div id="message"></div>

Note: The final message is inside the "message" div.

## Making the HTML Page Dynamic

Now, the problem we face is how to insert the email in the database and show the thank you message. The answer is through a [jQuery AJAX](http://www.yogihosting.com/jquery-ajax/) Method.

This is the main catch here! With jQuery AJAX, we can send the email value to a PHP page and this PHP page will insert it to the database and return the thank you message.

We will call the jQuery AJAX method in the button click event and simply post the email value to the PHP page.

**Below is our jQuery AJAX code**:
    
    
    $("#submit").click(function (e) {    
    
    
            data: '{"email":"' + $("#email").val() + '"}',
    
    
            error: function (req, status, error) {
    
    
                alert(req + " " + status + " " + error);

**Explanation**: In the above jQuery AJAX method code, we pass the "result.php" to the "url" key. This is the PHP page which will get the email value.

The "data" key will pass the email input value.

The "success" key defines the function that will be called when the AJAX request is called. Inside this function, we receive the returned value from the PHP page and put it in the "message" div.

The "error" key defines the function which will be called in case there is some error during the AJAX call.

**Finally the PHP Page...**

The PHP page just gets the email values, inserts it into the database, and sends back the thank you message.

Now if any web developer tells you that an HTML page cannot be used to show dynamic contents. Tell that person politely, "You are wrong, there is another way!"

With jQuery AJAX an HTML page can work like a server page. You can use it, to make any sort of database application right from the HTML page.

Happy Coding!

[Create data driven applications](https://dzone.com/go?i=155123&u=http%3A%2F%2Fplayground.qlik.com%2Fhome) in Qlik's free and easy to use coding environment, brought to you in partnership with [Qlik](https://dzone.com/go?i=155123&u=http%3A%2F%2Fplayground.qlik.com%2Fhome).

Opinions expressed by DZone contributors are their own.
