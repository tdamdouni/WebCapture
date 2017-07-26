# Facebook Messenger Bot

_Captured: 2017-05-21 at 12:39 from [dzone.com](https://dzone.com/articles/facebook-messenger-bot-1?edition=299092&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-20)_

[Learn how to build modern digital experience apps](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) with Crafter CMS. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190130&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).

Very recently when I visited the JS Channel conference sometimes later on July, 2016 and it started with something called '**bots'** in their Keynote followed by a pretty cool demonstration of how does it work and what is it. Kind of gave me a boost to learn it. I came back home and started researching on what are bots and how can we thrive its benefits.

So I started looking into Facebook which provides pretty good developer handy tools to get your job done in no time. There I came up with something known as Facebook messenger bot. So let me take you on a ride into the world of bots. The agenda of this blog would be to give you some idea about what bots are and how a bot functions.

So an internet bot, also known as a web robot, or simply a bot, is a software application that runs automated tasks over the internet. Typically bots perform tasks that are both simple and structurally repetitive without any human intervention. Nowadays, bots play a major role in any kind of web interaction or deployment. It reduces human effort in repetitive tasks.

So let us try creating a weather bot which will let you know the forecast for given a place. So let's start off by creating a Facebook messenger bot.

Make a git clone of this [repository.](https://github.com/Corefinder89/JavaScript) You should have npm (node package manager) and Node.js installed on your machine. Once you clone the repository, visit the directory **_Facebook_Bot2_**. Now do _npm install_. This will install all the dependencies related to express that we will be needing to make a GET and a POST request. Once all your required modules get installed, you need to run the command `npm run dev`. This will basically run your Node.js server. Next, we will need a tool called _**ngrok. **_This would basically tunnel your localhost to the internet. You can also deploy your application on cloud services, for example, Heroku, and use the URL provided by the service for a callback URL in webhook. To run ngrok in your system, just type in your terminal_ `npm run ngrok`._Your terminal will look something like this:

![ngrok.png](https://soumyajit2016.files.wordpress.com/2016/09/ngrok.png)

As you can see, our localhost is running on port 5000 which is now available as a domain with the help of ngrok. Keep the URL with HTTPS in handy. We will be needing it later on.

Next, login to Facebook and create a page of your own. Once that is done, create a Facebook app. To create a Facebook app, login to your Facebook account. In the extreme bottom left you will find the Developer section. Under _**Developer**_ section, you will find the option **_'manage your apps.' _**Click on it.

![f5b79890-462c-440b-4791-9e1a73f0746b](https://soumyajit2016.files.wordpress.com/2016/09/f5b79890-462c-440b-4791-9e1a73f0746b.png)

This will take you the developers page in Facebook, which would look something like this:

![Developers_Facebook.png](https://soumyajit2016.files.wordpress.com/2016/09/developers_facebook.png)

Over here you need to click on the option **Add a New App** as shown in the image below:

![b0f45cf0-2cd1-46b1-5bf4-82033bf87ddb.png](https://soumyajit2016.files.wordpress.com/2016/09/b0f45cf0-2cd1-46b1-5bf4-82033bf87ddb.png)

When you click on **_'Add a New App' _**you will be asked to enter the name of the application and your email address. You will also be asked to choose a **_category_** for which I have chosen **_'Apps for pages.' _**

![Create_App.png](https://soumyajit2016.files.wordpress.com/2016/09/create_app.png)

![1e4ffa4d-75ee-45ab-4956-8c1c39faa3c3.png](https://soumyajit2016.files.wordpress.com/2016/09/1e4ffa4d-75ee-45ab-4956-8c1c39faa3c3.png)

Then click on **_'Create App ID' _**once you are done with entering all the information. When the app is created, you need to add a feature to your application. You can do this by clicking the **_'Add Product'_** button present on the left side of the screen. Next, click on the **_'Get Started' _**button to start with your messenger bot application.

![b342da42-9317-4aa1-53f2-0e1f37417f35.png](https://soumyajit2016.files.wordpress.com/2016/09/b342da42-9317-4aa1-53f2-0e1f37417f35.png)

So once you get started in the Facebook messenger page, you will be asked to select a page and a **_page access token_** will be generated for you. A page token is needed to start using the APIs. This page token will have messenger permissions even if your app is not approved to use them, though in this case, you will only be able to message the app admins. Follow the corresponding screenshots to generate the page access token:

![17e61c1d-24f6-41fd-4feb-40100a0c4d51.png](https://soumyajit2016.files.wordpress.com/2016/09/17e61c1d-24f6-41fd-4feb-40100a0c4d51.png)

![permission.png](https://soumyajit2016.files.wordpress.com/2016/09/permission.png)

![permission2.png](https://soumyajit2016.files.wordpress.com/2016/09/permission2.png)

![64eb02ad-c508-4cd6-58a0-8f0c4d529a74.png](https://soumyajit2016.files.wordpress.com/2016/09/64eb02ad-c508-4cd6-58a0-8f0c4d529a74.png)

Keep the page access token in handy. You will need this to authorize your page messenger bot to carry out requests and responses. Next up, we will be setting the Webhooks. Now, this plays a crucial part in your application. We will be needing the webhook so that messages and other events can be received from the users. For this, we would need to integrate a webhook with the corresponding app.

Before plunging into setting webhooks, I would like to quickly talk about the concept of webhooks first. Webhooks are user-defined callbacks. They are usually triggered by some event such as pushing a code to a repository. When the event occurs, the source site makes an HTTP request to the URI configured for the webhook. Users can configure them to cause events on one site to invoke behavior of another. Since it is an HTTP callback, it can be integrated into any web service without adding any added infrastructure.

So, you can create a webhook by clicking on the **_'Setup Webhooks' _**button.

![010baa8a-c607-41e9-73d9-e8faa6dcd75b.png](https://soumyajit2016.files.wordpress.com/2016/09/010baa8a-c607-41e9-73d9-e8faa6dcd75b.png)

![WebHookURL.png](https://soumyajit2016.files.wordpress.com/2016/09/webhookurl.png)

Now, in the callback URL, insert the forwarding URL that is given by ngrok in the terminal with an endpoint **_'Webhook,'_**, followed by the name of the token. Verify and save the settings of the webhook.

Next, subscribe the webhook to your page.

![WebHookPage.png](https://soumyajit2016.files.wordpress.com/2016/09/webhookpage.png)

Next, you'll need to attach your bot to the page you set up. This allows you to communicate with the bot by visiting the page and clicking "Message." In Token Generation, generate a page access token by selecting the page you created. In the terminal, execute the following command, replacing the access token with the page token:

Also, update your index.js file (on line 53) with this page token so you can send messages back:

At this point, your bot is subscribed to updates for the page, which means that when someone messages the bot from the page, you'll get the notification.

When you send a message to WeatherBot, you'll see WeatherBot echo it back. The server will also indicate that it received the message.

The relevant code that's handling the message receiving is here:
    
    
    app.post('/webhook/', function (req, res) {
    
    
      var messaging_events = req.body.entry[0].messaging;
    
    
      for (i = 0; i < messaging_events.length; i++) {
    
    
        var event = req.body.entry[0].messaging[i];
    
    
        var sender = event.sender.id;
    
    
        if (event.message && event.message.text) {
    
    
          var text = event.message.text;

Sending a text message looks like this:
    
    
    var request = require('request');
    
    
      }, function(error, response, body) {
    
    
        } else if (response.body.error) {
    
    
          console.log('Error: ', response.body.error);

Now let us make our bot do something more.

## Weatherbot

The bot should respond with the current weather in a particular location. We'll use [Yahoo weather](https://developer.yahoo.com/weather/) as our API. The endpoint we'll be using is this gnarly-looking URL:
    
    
    var weatherEndpoint = ‘https://query.yahooapis.com/v1/public/yql?
    
    
    q=select%20*%20from%20weather.forecast%20where%20woeid%20in%20(select%20
    
    
    woeid%20from%20geo.places(1)%20where%20text%3D%22' + location + ‘%22)&
    
    
    format=json&env=store%3A%2F%2Fdatatables.org%2Falltableswithkeys’;

Replace the POST response (the /webhook listener) with this:
    
    
    app.post('/webhook/', function (req, res) {
    
    
      var messaging_events = req.body.entry[0].messaging;
    
    
      for (i = 0; i < messaging_events.length; i++) {
    
    
        var event = req.body.entry[0].messaging[i];
    
    
        var sender = event.sender.id;
    
    
        if (event.message && event.message.text) {
    
    
          var location = event.message.text;
    
    
    ?q=select%20*%20from%20weather.forecast%20where%20woeid%20in%20(select%
    
    
    20woeid%20from%20geo.places(1)%20where%20text%3D%22' + location + '%22)&
    
    
    format=json&env=store%3A%2F%2Fdatatables.org%2Falltableswithkeys';
    
    
          }, function(error, response, body) {
    
    
              var condition = body.query.results.channel.item.condition;
    
    
    + condition.text + " in " + location);

This code initiates a call to Yahoo's servers with the incoming message and returns the current weather for that location.

So now the bot will respond to your query. You enter the name of a region or a place, like Boston or Los Angeles, for example, and the bot will give you the forecast of that place.

![1-Xdsf-EBXxGx5D8bXwTZoVQ.png](https://soumyajit2016.files.wordpress.com/2016/09/1-xdsf-ebxxgx5d8bxwtzovq.png)

This is what I have been experimenting with for the past few days. I would like to make it more intelligent by using the NLP (Natural Language Processing) API also called [wit.ai](https://wit.ai/). That helps in recognizing text patterns entered by the user, and it makes the bot more intelligent and user-friendly.

Crafter is a [modern CMS platform for building modern websites](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb) and content-rich digital experiences. Download this eBook now. Brought to you in partnership with [Crafter Software](https://dzone.com/go?i=190131&u=http%3A%2F%2Fwww.craftersoftware.com%2Fresources%2Flp%3Fid%3D%2Fmodern-web-dev-with-java%26t%3Deb).
