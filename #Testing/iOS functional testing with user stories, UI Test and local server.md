# iOS functional testing with user stories, UI Test and local server

_Captured: 2015-10-30 at 10:55 from [www.thinkandbuild.it](http://www.thinkandbuild.it/ios-functional-testing-with-user-stories-uitest-and-local-server/)_

In my projects I've been mostly focused on Unit Testing but I was always interested in performing some tests on the navigation flow of the application, being then able to verify something like this: "When a user inserts valid credentials and taps the Sign In button, then he moves to the next view". I know that at a first sight it might sound extremely obvious… you have written the navigation flow, so you know that it is going to behave like this. Sure. Trust me (but you already know that), things happen, your so-obvious flow may suddenly brake and things work differently from your expectations. Yes, I know, it's a terrible prospect :/ that's why writing some functional tests is a good idea!

### Functional tests and something about User Stories 

A functional test is a good way to verify an implemented [user story](http://www.extremeprogramming.org/rules/userstories.html). A story is essentially a well-defined task; In extreme programming (but also in some less strict-environment), you use stories to describe all the possible **user cases** that might be encountered in a project. You (or your PM) use a list of stories to split the project's scenarios, in little, specific, logical parts.  
Take something similar to the sentence that we have previously introduced:

**_"Given I'm in the sign in view,  
when I insert valid credentials,  
and I tap the 'Sign In' button,  
then I move to the list view"._**

This is a good example of a story that gives you information about a really specific task. A really important thing to understand when implementing a story, is that you have to be focused only on that story. As example, if you are implementing the previous one you don't want to implement the logic needed for invalid credentials too (like showing an error message), just the one described by the current story, for sure there is another story to verify the "invalid credentials" behaviour.

That been said, a functional test can be considered as the automation of a flow, and to be "green" (succeed) it has to run from the start to the end respecting the logics described by the story.

### The Example project 

The project is extremely simple. We want to create an application that gives to a user the ability to sign in into a restricted area, see a list of his robots and a details view for each of them (For the sake of simplicity we skip the user registration).

These are some useful stories to describe the project:

**Sign in with Invalid credentials **  
`"Given I'm a user,  
and I'm in the Sign In View,  
when I enter invalid credential,  
and I tap the Sign In button,  
then nothing happen" `

**Sign in with valid credentials **  
`"Given I'm a user,  
and I'm in the Sign In View,  
when I enter valid credential,  
and I tap the Sign In button,  
then I see the Robot List"`

**Robot list with Robots**  
`"Given I'm a logged in user,  
and I'm in the Robot List view,  
and I own some robots,  
then I see all my robot"`

**Robot list without Robots**  
`"Given I'm a logged in user,  
and I'm in the Robot List view,  
and I don't own any robot,  
then I don't see robots in the list" `

**Robot details**  
`"Given I'm a logged in user,  
and I'm in the Robot Detail view,  
then I see robot name, id and charge level"`

**Logout**  
`"Given I'm a logged in user,  
and I'm in the Robot List view,  
when I press the Logout button,  
Then I see the logout page and  
I'm logged out" `

### Let's code

Before continuing with the article I suggest you to download the code for this project. There you can find all these stories already implemented in a simple application.

####  Injecting fake data

A really common way to perform tests is faking the server responses, heading the application towards a predefined flow. As example, when I want to simulate a valid login, I can inject a server response with a 200 or 201 status code that contains an auth token, while if I want to simulate an invalid credentials response I can set the status to 403 or 401 and return an error code. Then the application will continue its flow in different ways depending on the fake data. So we can implement tests to verify the behaviour of the application is correct for all the flows that we can generate with fake data.

When working with Unit Tests you can fake server responses in differente ways. You can stub the HTTP responses intercepting the HTTP calls (the [OHTTPStubs](http://www.thinkandbuild.it/ios-functional-testing-with-user-stories-uitest-and-local-server/“https://github.com/AliSoftware/OHHTTPStubs”) library is a really good choice to implement this solution) or you can mock your network library to return fake data (this topic is worth a dedicated article).

The new Xcode UI test target works in a different way: tests and application run as different instances, that means you don't have a way to inject data directly from tests code. A really common solution to be able to inject somehow data during UI testing is launching the application instance with dedicated **launch arguments** and generating a different data flow when the App is running in "testing mode".

If you open the **TB_UITestingUITests.swift** file you will find out that in the **setUp** function the application instance is launched with the **UI_TESTING_MODE** argument:

123
`let` `app = XCUIApplication()``app.launchArguments = ["``UI_TESTING_MODE``"]``app.launch()`

This information is then retrieved from the application thanks to the **NSProcessInfo** class. In the **Helper.swift** file, the **endPoint** function is responsible to return the server url. This is a good point to injecting fake information pointing the application to a different server, in this case **localhost:4567**, the url where our fake server responds generating data for the tests.

12345678
`func` `endPoint()->``NSURL` `{``if` `(``NSProcessInfo``.processInfo().arguments.contains("``UI_TESTING_MODE``")) {``return` `NSURL``(string: "http:``//localhost:4567")!``}``else``{``return` `NSURL``(string: "http:``//www.example.com/api/")!``}``}`

If you don't want to use a fake server you might also fake data directly inside the application. Personally, I don't like this method since the application code requires to much adjustments. With the previous example we get to the point changing just a single function, all the needed information will be handled outside the application code.

#### Network requests and the fake Sinatra server

In this article I'm using Sinatra since it's extremely simple to write and explain the needed code. Obviously we might substitute this solution with Node.js, PHP or whatever you like the most.

Just to be consistent with the previous examples let's focus on the sing-in call. Here is the code of the Application responsible for it:

12345678910111213141516171819202122232425262728293031
`…``let` `API = APIService(endPoint: endPoint())``…``@IBAction` `func` `signIn(){``// Verify User Input``guard ``let` `username = username_textfield.text,``let` `password = password_textfield.text ``else` `{``// Error handling here…``return``}``// Create the Call``var` `signInCall = APICall(path: "session", method: Method.POST)``signInCall.parameters = ["username":username, "password":password]``// Handle the Response``API.request(signInCall) {``(code, JSON) -> Void in``switch` `code {``case` `StatusCode.Created:``if` `let` `token = JSON?["access_token"] as? ``String``{``NSUserDefaults``.accessToken = token``let` `vc = instantiateViewController("RobotList")``self``.showViewController(vc, sender: ``self``)``}``case` `StatusCode.Forbidden:``print("Login failed")``default``:``print("Other error")``}``}``}`

In has been organized in 3 main parts:  
It verifies user input, then it creates the call and finally it handles the response.

I've written some simple API classes that should be really easy to read (do not use it on real projects please it's not the state-of-the-art code). The **APICall** instance receives the API path and the HTTP method, in this case "session" and "POST", and sets username and password as call parameters that internally are transformed into JSON data.

The **APIService** class is responsible to send an API call request and handle the response through callbacks.

In the previous example an instance of this class is initialized with an end point defined at launch time then it starts the sing-in call previously defined and it handles the response through a simple switch, focusing on the response status code.  
If the session has been correctly created then we store the auth token and we move to the next view controller, otherwise nothing happens exactly as per the previous dedicated stories.

All the other API calls for this Application have been handled in a really similar way, creating an instance of the call and handling the response inside a callback that addresses different code depending on the response status.

It is time to take a look at the server code (bear with me, my Ruby skills are limited -.- )

Writing a simple Sinatra server is extremely easy. Some predefined blocks are named after HTTP methods and you can route the requests with a super simple and readable syntax :

1234
`<httpMethod> '<route>' ``do``status <response_status_code>    ``…your code``end`

Here is the full code for the "session" call.

123456789101112131415161718
`post '/session' ``do``data = ``JSON``.parse request.body.read``username = data["username"]``password = data["password"] ``# not used in this example…``case` `username``when` `"user_with_robots"``status ``201``JSON``.generate( ``:access_token` `=> "``1234``" )``when` `"user_without_robots"``status ``201``JSON``.generate( ``:access_token` `=> "``5678``" )``else``status ``403``JSON``.generate( ``:error` `=> "invalid_credentials" )``end``end`

We obtain username and password that come from the request, then, depending on the username, we decide what kind of response to create. I found this solution extremely useful, as you will see later we can write tests that will be addressed to different responses depending on predefined data. Here for the "session" call, you know that passing as username "user_with_robots" or "user_without_robots" you obtain valid tokens, otherwise, this code simulates invalid credentials, with a 403 response and an error code. As you can imagine the token received will be useful to define the Robot list later, generating an empty or a full list depending on the username. Neat.

You can have a look at all the other Server responses defined by the file **TestServer/server.rb**, the logics behind those call are exactly the same described for the "session" call.

You can launch the server just executing the ruby script (you might need to install the Sinatra gem ).

Forcing the application endPoint to "localhost:4567" you can try the server, try to perform a login with "user_with_robots" as username and whatever password 

#### Implementing UI Tests 

Great, now we have a working application and a test server. We can simulate whatever application flow we need!  
My suggestion is to start from the stories previously listed and just write tests that verify those stories.  
We can keep our focus on the the sign-in process, let's implement the "sign-in with valid credential" test.

To generate a valid signed in user we might use one of the accepted usernames, let's choose the "user_with_robots" one and write a really readable function. I think that the Ruby function naming style (name_of_the_function) is perfect to achieve good readability, so all the functions that you see inside the TB_UITestingUITests.swift file have been written with this approach. Let's put our focus on the **test_login_when_credentials_are_valid** function.

12345678910111213141516171819
`func` `test_login_when_credentials_are_valid(){``let` `app = XCUIApplication()``performLogin(app, username:"user_with_robots")``XCTAssert(!app.buttons["signin"].exists)``}``func` `performLogin(app:XCUIApplication, username:``String``){``let` `usernameTextField = app.textFields["Username"]``usernameTextField.tap()``usernameTextField.typeText(username)``let` `passwordSecureTextField = app.secureTextFields["Password"]``passwordSecureTextField.tap()``passwordSecureTextField.typeText("mypassword")``app.buttons["signin"].tap()``}`

This function should be straightforward, it keeps a reference to the app, simulates the username and password textfield completion and taps the sign in button through the **performLogin** method. Then finally it verify the current view is changed checking that the **signin** button no longer exists.

### Conclusions 

Even if I can count on a QA team, I've found this process extremely useful during the development of my current project. Performing automated test with a fake server is extremely useful and if adopted in conjunction with good Unit tests you achieve a great coverage! There are many other different ways to do what is explained in this article, so I'd like to hear your opinion and your suggestion on [twitter](http://www.twitter.com/bitwaker)!

[Follow @bitwaker](https://twitter.com/bitwaker)
