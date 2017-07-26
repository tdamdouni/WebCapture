# Oauth 2 with React Native

_Captured: 2015-06-12 at 23:17 from [medium.com](https://medium.com/p/c3c7c64cbb6d)_

We're going to be using React Native to make an iPhone app that can interact with a third party API secured by Oauth 2.0.

Initialize the project in the terminal with
    
    
    react-native init OauthExample

The API that we'll be using is the Dropbox Core API. This API allows you to manipulate files and folders in a user's Dropbox account. But first, the user must give us permission. [Dropbox made](https://www.dropbox.com/developers/reference/oauthguide) a pretty good diagram to illustrate the process:

![](https://d262ilb51hltx0.cloudfront.net/max/840/1*IJjMyAfPyxpI7K4NWL1yEw.png)

We'll use React's LinkingIOS library to go to the Oauth2 authorization page and handle the redirect.

But first, we will have to do a bunch of pointing and clicking in Xcode land to enable some of the features we need. We'll need to:

  * Link the LinkingIOS library so that it can be built with our app. Follow [these instructions](https://facebook.github.io/react-native/docs/linking-libraries.html#content).
  * Add this code to your **AppDelegate.m** file, right under **@implementation AppDelegate**. Make sure to add **#import "RCTLinkingManager.h"** to the top of the file.
    
    
    - (BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(NSString *)sourceApplication annotation:(id)annotation {  
      return [RCTLinkingManager application:application openURL:url sourceApplication:sourceApplication annotation:annotation];  
    }

  * Register your app to open on custom URLs using a URL Scheme. Twitter has a [good guide](https://dev.twitter.com/cards/mobile/url-schemes). You can use these settings:
![](https://d262ilb51hltx0.cloudfront.net/max/1400/1*7Q14VPNKrLgmvpamgGaEpQ.png)

Ok, now that we've dealt with that, we can register our app with Dropbox. Go to <https://www.dropbox.com/developers/apps> and click the "Create App" button. Create it with these settings:

![](https://d262ilb51hltx0.cloudfront.net/max/1031/1*I5sVWISAvdRoY1cGMBnUQw.png)

Once the app is created, set up a redirect URI corresponding to the URL scheme you set up for your app. It needs to have something after the **://**.

![](https://d262ilb51hltx0.cloudfront.net/max/1244/1*MBQQv4Zy8AImki14qfcikw.png)

Also, make a file in the root of your React Native project called **config.js**_._ Add the app key from the screen above.
    
    
    module.exports = {  
      app_key: '6unv0yqsyke05qa'  
    }

Ok. Now we can get to the real coding.

We'll need to modify **index.ios.js** to require a few new things.
    
    
    ‘use strict’;
    
    
    var React = require(‘react-native’)  
    var config = require(‘./config.js’)
    
    
    var {  
     AppRegistry,  
     StyleSheet,  
     Text,  
     View,  
     TouchableHighlight,  
     LinkingIOS  
    } = React

Ok, the first thing we need to do for Oauth is to present the user with Dropbox's Oauth approval page on their website. Add this function to **index.ios.js**.
    
    
    function dropboxOauth (app_key) {  
      LinkingIOS.openURL([  
        ‘[https://www.dropbox.com/1/oauth2/authorize'](https://www.dropbox.com/1/oauth2/authorize%27),  
        ‘?response_type=token’,  
        ‘&client_id=’ + app_key,  
        ‘&redirect_uri=oauth2example://foo’  
      ].join(‘’))  
    }

Call it from **componentDidMount**_._
    
    
    componentDidMount: function () {  
      dropboxOauth(config.app_key)  
    }

At this point when the app starts up, it should immediately take you to Dropbox's Oauth page, which will then redirect you back to the app. Now we need to set up a listener using **LinkingIOS** so that we can get the access token that we need to make API calls.

Add this to your **dropboxOauth** function. Notice that we remove the listener after we are done with it.
    
    
    LinkingIOS.addEventListener(‘url’, handleUrl)
    
    
    function handleUrl (event) {  
      console.log(event.url)  
      LinkingIOS.removeEventListener('url', handleUrl)  
    }

Now you should see something like this being logged.
    
    
    oauth2example://foo#access_token=eFEcGxgInLIAAAAAAAAVAe6EIkz8J_kfGNIE0EPSOeuRgjjFYxJDvTH8YOuABe8G&token_type=bearer&uid=27414286

Let's do something useful with this token. We're going to extract the query string from the URL, parse it, and pass it out of **dropboxOauth** with a callback. You will also need to install and require **shitty-qs**.
    
    
    function dropboxOauth (app_key, callback) {  
      LinkingIOS.addEventListener(‘url’, handleUrl)
    
    
      function handleUrl (event) {  
        var [, query_string] = event.url.match(/\#(.*)/)  
        var query = shittyQs(query_string)  
        callback(null, query.access_token, query.uid)  
        LinkingIOS.removeEventListener(‘url’, handleUrl)  
      }
    
    
      LinkingIOS.openURL([  
        ‘[https://www.dropbox.com/1/oauth2/authorize'](https://www.dropbox.com/1/oauth2/authorize%27),  
        ‘?response_type=token’,  
        ‘&client_id=’ + app_key,  
        ‘&redirect_uri=oauth2example://foo’  
      ].join(‘’))  
    }

In **componentDidMount,** we add the callback and have it save the token with **setState. **Let's show the token in the interface so that we know it worked. Add this view to the **render** method.
    
    
    <Text style={styles.instructions}>  
      Access Token: {this.state && this.state.access_token}  
    </Text>

Cool! Now we can actually do something with the API to prove that our authentication works. Add this button below the view you just added.
    
    
    <TouchableHighlight  
      onPress={this.onMakeFolderPressed.bind(this)}>  
      <Text>Make Folder</Text>  
    </TouchableHighlight>

Add an **onMakeFolderPressed** method to your component.
    
    
    onMakeFolderPressed: function () {  
      fetch(  
        ‘[https://api.dropbox.com/1/fileops/create_folder'](https://api.dropbox.com/1/fileops/create_folder%27),  
        {  
          method: ‘POST’,  
          headers: {  
            ‘Authorization’: `Bearer ${this.state && this.state.access_token}`  
          },  
          body: `root=auto&path=${Math.random()}`  
        }  
      )  
    }

We're adding the access token in the header and posting to the **create_folder** endpoint. The option **root** determines where the folder will be created. Dropbox recommends setting it to **auto**. The option **path** we will set to a random number for expedience. You should be able to create folders named after random numbers in your Dropbox.

![](https://d262ilb51hltx0.cloudfront.net/max/1400/1*sWAu9mdADx4aJwK3YgMWnQ.png)

Mission accomplished, right? We can sign into Dropbox and use the API to do file and folder operations.

Not so fast! There's actually a big security issue with this implementation. It might be possible for an attacker to send a URL to our app, containing their access token instead of the user's.
    
    
    oauth2example://foo#access_token=attackers_token_IAAAAAAAAVAe6EIkz8J_kfGNIE0EPSOeuRgjjFYxJDvTH8YOuABe8G&token_type=bearer&uid=27414286

The user might then upload sensitive data to the attacker's account. To mitigate this threat, we need to send something unguessable to Dropbox in the authentication call's **state** parameter. We will then check that the **state** is correct before accepting any access token.
    
    
    function dropboxOauth (app_key, callback) {  
      var state = Math.random() + ‘’
    
    
      LinkingIOS.addEventListener(‘url’, handleUrl)
    
    
      function handleUrl (event) {  
        var [, query_string] = event.url.match(/\#(.*)/)  
        var query = shittyQs(query_string)  
        if (state === query.state) {  
          callback(null, query.access_token, query.uid)  
        } else {  
          callback(new Error(‘Oauth2 security error’))  
        }  
        LinkingIOS.removeEventListener(‘url’, handleUrl)  
      }
    
    
      LinkingIOS.openURL([  
        ‘[https://www.dropbox.com/1/oauth2/authorize'](https://www.dropbox.com/1/oauth2/authorize%27),  
        ‘?response_type=token’,  
        ‘&client_id=’ + app_key,  
        ‘&redirect_uri=oauth2example://foo’  
        `&state=${state}`  
      ].join(‘’))  
    }

Ok, you should now be able to implement and secure Oauth2 API authentication. Other providers will probably be slightly different from Dropbox, but the same concepts should apply.

Here is the finished code: <https://github.com/jtremback/OAuthExample>
