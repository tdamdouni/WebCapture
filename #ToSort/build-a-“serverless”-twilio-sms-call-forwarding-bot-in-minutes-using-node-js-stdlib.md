# Build a “Serverless” Twilio SMS + Call Forwarding Bot in 7 Minutes using Node.js + StdLib

_Captured: 2017-06-15 at 01:12 from [hackernoon.com](https://hackernoon.com/build-a-serverless-twilio-sms-call-forwarding-bot-in-7-minutes-using-node-js-stdlib-411697c3cc1b?source=userActivityShare-c79006fee040-1497485531)_

Since 2009, [Twilio](https://twilio.com/) has enabled developers to seamlessly build SMS and Voice technology into their apps, handling everything from basic user notifications, connecting drivers and passengers in apps like Uber and Lyft, to conference calling and more. If you haven't had a chance to incorporate Twilio's services into your product yet, here's your chance to start! We're happy to team up with Twilio's functionality to show you how to bring Voice + SMS into your product or company in only a couple of minutes with StdLib!

![](https://cdn-images-1.medium.com/max/800/1*DRxMoUVu1SXHL6BCpR8xpQ.jpeg)

Maybe you've used Twilio before, or maybe you haven't but you're extremely interested in playing with programmable telephony and bringing it to your team or company. With the past success of our "Build" articles (like [Build a Slack Bot in 9 Minutes](https://medium.com/slack-developer-blog/build-a-serverless-slack-bot-in-9-minutes-with-node-js-and-stdlib-b993cfa15358)), we're excited to share StdLib's quickest article yet -- we're happy to introduce how you can build a Twilio Messaging Hub in only 7 Minutes with StdLib!

If you haven't used StdLib before you're in for a treat -- [StdLib is the fastest way to ship business value via code](https://stdlib.com/). It's effectively a package manager for APIs that's built upon new "serverless" architecture, meaning you never have to worry about managing servers or allocating resources for scale. Write a function, deploy, and you're ready to go! We also have a growing ecosystem of integrations contributed by other developers that are extremely easy to plug in to.

Once you've created your StdLib service in **Minute 4**, you'll get a `README.md`file that shows you how to hack your Twilio + StdLib Messaging Hub to your own needs.

### What You'll Need Beforehand

### Minute 1: Create Your Twilio Phone Number

The first thing you'll want to do to get your Stdlib + Twilio messaging hub operational is grab a new phone number for your Twilio Account. First, make sure you're logged in to your Twilio Account at <https://www.twilio.com/login>.

> _Log In to Twilio_

From here, you'll be at your [Twilio Console](https://www.twilio.com/console). If this is your first time with Twilio, you'll see a screen that looks like this (below). On the left menu, hit the button with the circle and ellipsis "**(…)**" inside:

> _You want to select "All Products and Services" on the grey bar on the left_

From here, a slider menu will pop out. You want to select _Phone Numbers_ under the _Super Network_ heading:

> _Click "# Phone Numbers"_

To add your first phone number, hit "**Get Started**":

And then "**Get Your First Twilio Phone Number**":

You'll see a popup suggesting a random number for your geolocation, in this case, 415 is San Francisco. Click "**Choose this Number**" to continue quickly. (You can buy other numbers later.)

You'll be greeted with a success message. Awesome!

### Minute 2: StdLib Account Setup

In order to create a robust messaging hub, you'll next need to set up your [StdLib](https://stdlib.com/) Account. You'll use StdLib to host your Twilio Hub using infinitely scalable "serverless" architecture from a single, maintainable codebase, and to hook into other integrations on StdLib (for example, using [utils.image](https://stdlib.com/utils/image) to format images you receive via MMS or using [devin.income-predictor](https://stdlib.com/devin/income-predictor) to see income ranges for the zip code associated with an incoming phone number). Simply visit <https://stdlib.com> and click "Sign Up Free" to create your account.

> _Click "Sign Up" to Create an Account_

### Minute 3: Create a StdLib Workspace

[StdLib natively runs Node.js 8.0.0 (yes, the newest version)](https://medium.com/stdlibhq/stdlib-updates-node-8-0-0-platform-support-new-faaslang-function-definitions-b33ffe5633b8) so to ensure there are no compatibility issues you'll likely want to run it (though Node 6 and 7 will work for this example). You can install the latest version of Node from the [Official Node.js Website](https://nodejs.org). Once complete, open up your Terminal or Command Line and install the [StdLib Command Line Tools](https://github.com/stdlib/lib) with the following:
    
    
    $ npm install lib.cli -g

This gives you access to the `lib` command for service management and execution. Next, create a `stdlib` directory for your StdLib services.
    
    
    $ mkdir stdlib  
    $ cd stdlib  
    $ lib init

Log in using the credentials you created in the previous step. That's it!

### Minute 4: StdLib Service Creation

Next you'll create your StdLib service from the command line. We've created a special `twilio` template to allow you to ship a prototype of your own Twilio Hub in only a few seconds.
    
    
    $ lib create -t twilio

You'll be asked to enter a `Service Name`, we recommend `twilio-hub` for the purposes of this tutorial. You'll see some NPM packages being installed locally and your service directory being created:

Once complete, you'll be told to enter your service directory. Do so with the command:
    
    
    $ cd user/twilio-hub

Where `user` is, of course, your StdLib username. (In my case, it's `keith`.)

From here, you can try running some SMS commands (these will be the responses for _"more"_ or _"whoami"_ sent to your Twilio number) with:

And see the result:

![](https://cdn-images-1.medium.com/max/800/1*v-gwA2hKYp2WJ8OM0lGH3Q.png)

> _The SMS response to people who message your number with the text "more."_

Or, alternatively, turn on debug mode with `-d` to see what's going on behind the scenes:

Since this isn't actually being triggered by Twilio's webhook, execution information (zipcode, city) reads as `undefined`, so this is expected.

### **Minute 5: Configure Your StdLib Environment**

As a next step, we'll want to make sure StdLib knows all of our Twilio Account details. To set this up properly, first open up `env.json` in the StdLib service directory you just created, `user/twilio-hub/env.json` where, again, `user` is your username.

You can see three different environments: `local`, `dev` and `release`. These are intended for different execution contexts -- when running locally, the environment variables in `local` are used, you can deploy to a `dev` environment in the cloud, or a production `release` environment. We generally recommend at least using a different phone number.

**Make sure, for the purposes of this tutorial, you fill in the **`**dev**`** and **`**local**`** variables with the same values.**

To fill in `"STDLIB_TOKEN"` visit <https://dashboard.stdlib.com/dashboard/>, log in, click **Library Tokens** on the left, then **Show Token** to reveal your token. Copy and paste it into your environment variables.

> _Click "Show Token" to reveal your token, then copy it._

Next, `"TWILIO_ACCOUNT_SID"`, `"TWILIO_AUTH_TOKEN"`, and `"TWILIO_NUMBER"` -- these are all available from your Twilio Console at <https://www.twilio.com/console>. Copy your **ACCOUNT SID** directly, and click the eyeball beside your **AUTH TOKEN** to reveal it and copy it as well.

> _Copy your Account SID and your Twilio Auth Token into your Environment Variables_

To find your Twilio Phone Number you previously created, visit <https://www.twilio.com/console/phone-numbers/incoming>. Click on the red, highlighted number you created in **Minute 1**.

> _Click on the Red Text to Configure Your Number_

From the next screen, copy and paste the **PHONE NUMBER** value in the format `+1234567890` to your `"TWILIO_NUMBER"` value.

> _Copy the "PHONE NUMBER" value_

**Finally**, the `"CALL_FORWARD_NUMBER"` value can be filled in with **any phone number of your choosing, it is the number that your Twilio Hub will automatically redirect incoming calls to**. Use the format `+1234567890` again (make sure it's in quotes). Best bet is to use a personal phone number for demonstration purposes.

### Minute 6: Deploy and Configure Webhooks

You're almost done! The very last step is to deploy your StdLib Twilio Hub (with the appropriate environment variables set above) and then configure Twilio Webhooks to point to StdLib.

To deploy your StdLib Twilio Hub in a `dev` environment, simply open up your command line in your service directory and type:

You'll see the progress of your service deploying to a development environment, and be greeted with a list of available HTTP endpoints corresponding to everything in your `functions/` directory.

Now that your service is live, go back to the Twilio Manage Numbers dashboard <https://www.twilio.com/console/phone-numbers/incoming> and select your phone number again. Scroll down to **Voice & Fax** first:

> _Enter in your "voice" endpoint to Voice & Fax_

On this form, beside **A CALL COMES IN**, make sure **Webhook** is selected in the dropdown and use the value `https://<user>.lib.id/twilio-hub@dev/voice/` (where `<user>` is of course, your username). Note that the hostname `lib.id` is our functions gateway, where all of your services and functions will be deployed to.

Next, scroll down to **Messaging** and enter in `https://<user>.lib.id/twilio-hub@dev/messaging/` in the **A MESSAGE COMES IN** Webhook handler.

> _Enter in your Messaging Handler details, and hit **Save**_

Finally, hit **Save** in the bottom left.

### Minute 7: Add Verified Phone Numbers

If this is your first time signing up with Twilio, you'll be using a trial account. Trial accounts have limitations on numbers they can send messages to or forward calls from. To make sure your Twilio Messaging Hub on StdLib works as you expect it, use the **verified phone numbers** list to add any phone numbers that you want to forward calls or send messages to.

By default, the phone number you registered your account with should already be listed here.

Your Twilio Messaging Hub on StdLib is live! You can now send SMS messages to your Twilio Number to receive an automated response and make calls to your number to have them forwarded. **If you're using a Twilio trial account, make sure you've added verified numbers in Minute 7. **Otherwise, you're good to go!

> _A Twilio Bot Interaction using StdLib_

You can modify the behavior of your SMS Bot by visiting the `/functions/messaging/` directory in your StdLib service. The default responses are are to "whoami" and "more." This messaging hub also handles MMS (media, picture) uploads.

If at any point you lose track of your StdLib username or what your webhook callbacks should be, they're listed when you deploy a service with `$ lib up dev`.

If you're not getting the expected responses when you play, Twilio has an amazing debugger at <https://www.twilio.com/console/dev-tools/debugger>.

To ship a bot / messaging hub to production, we recommend using a different phone number. Configure your `release` environment variables in `env.json` to the appropriate settings, set your `version` in `package.json` to `1.0.0` (or whatever you'd like, really), ship a release with `$ lib release` and then you can use `https://<user>.lib.id/twilio-hub@1.0.0/voice/` and `https://<user>.lib.id/twilio-hub@1.0.0/messaging/` as your voice and messaging endpoints for your production phone number.
