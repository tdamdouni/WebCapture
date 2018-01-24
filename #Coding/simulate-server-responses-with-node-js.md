# Simulate Server Responses With Node.js

_Captured: 2017-12-06 at 20:08 from [dzone.com](https://dzone.com/articles/simulate-server-responses-with-nodejs?edition=343098&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-12-06)_

A few days ago, while I was working on the front-end of a new project, I found myself in a situation where I needed to simulate different responses from the backend to check some functionalities and behavior in different browsers. This has encouraged me to write this articles about the **Node.js simulate browser**.

At this point, where a vast amount of companies are placing their bets on [TDD](https://apiumhub.com/blog/advantages-of-test-driven-development/), functional testing is a mere routine for the server side, but tables do turn on when it comes to the front-end development. With some promising tools in the game ([Selenium](http://docs.seleniumhq.org/) comes off the top of my head), developers do prefer to leave some testing to 'humans' to perform. Why does this happen? Due to a lack of solid support community, or an insufficient number of documentation and guides, maybe. But this discussion is not to be held in this post.

Coming back to my original point, it could be an option to do some temporary quick changes in our backend, and that would be it. But what happens if we do not have the control of it? I mean, its development is owned by others, and all we do is work against a REST API. If that's your case, here's a solution that might help: a 'dumb' server whose behavior is controlled from the front-end.

To accomplish that, we will use Node.js with [Express.js](http://expressjs.com/). We are going to build a server, whose response code and headers will be configured from a single POST call. Here's a quick guide you can follow.

### Getting Started With Node.js

The first thing we will need is to get Node.

To install it from the command line, run:

`apt-get install -g nodejs`

Then, from our IDE of choice, create a new Node.js project, and install Express:

`npm install express`

And last, but not least, we will install something that will make our life much easier, bodyParser:

`npm install body-parser`

### Basic Setup

Now we can start with our copycat server. This is a demo code you can find useful:

![1](https://apiumhub.com/wp-content/uploads/2016/01/1-1.png)

As you can see above, we will use 2 variables, to set the response code and headers, with default value: "200 OK" with no headers. Our server will be listening in port 8000.

### Configuration Call

It's about time to put some useful code in it. We will create a POST call that receives and saves the response code and an array of headers it will be answering with for now on. This route will be called from the front-end every time we need to change the behavior of our server.

![2](https://apiumhub.com/wp-content/uploads/2016/01/2-1.png)

In other words, we can set the response we want to get from the server, making a POST request to `127.0.0.1:8000/configure`. Once we have done that, we will proceed with a new call, never mind its method or payload, to which the response will be the one we configured. The body this call expects is in JSON format:

*Note: in the 'code', add the 3 digits code you need. The above lines are just an example.

### Default Routing

Just one thing left: a default route that will use the variables we set in the configuration:

![3](https://apiumhub.com/wp-content/uploads/2016/01/3-1.png)

This function will be executed for any route, as long as it is different from "POST/configure," and the response will be the one stored in our global variables 'code' and 'headers.'

That's all we're going to need. That means it's about time to test it. In this particular case, I will be using Postman, a great Chrome extension, to perform the configuration POST call, and will try to see the default browser's dialog that is displayed during Basic access authentication, displayed when the server's response is '401 Unauthorized,' with a header similar to: 'WWW-Authenticate: Basic realm=something.'

First, we must run our server. Locate the .js file that contains our code and execute it in the command line:

`node ourFileName.js`

Now, in Postman, we select the POST method, set the URL to `127.0.0.1:8000/configure`, add the Content-Type header to `application/json`, and add a body that will be compatible with our copycat server, like so:

Finally, open any browser and go to `http://127.0.0.1:8000/ `

### Results

![4](https://apiumhub.com/wp-content/uploads/2016/01/4.png)

![5](https://apiumhub.com/wp-content/uploads/2016/01/5.png)

> _The server response in the browser's console._

To sum up, in this post we saw an easy way to improve our web development using some popular and well-documented tools, Node.js and Express.js.

We're now able to emulate any server behavior without changing a single line of code in the backend. In order to do so, we created our own server, which has a simple configuration, performed directly from the front-end.
