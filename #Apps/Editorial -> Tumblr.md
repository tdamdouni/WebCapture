# Editorial -> Tumblr

_Captured: 2015-09-26 at 17:06 from [jeffmueller.net](http://jeffmueller.net/post/65440171874/editorial-tumblr)_

As you might have noticed from the little branded buttons at the top of the page, my blog runs on [Tumblr](http://www.tumblr.com).

I've been using [Byword](http://bywordapp.com) and the official Tumblr iOS app to publish new posts, which has been working great.

Last night, though, I noticed a small hiccup. A post I made through the Tumblr iPad app didn't auto-tweet the headline to my blog's Twitter account. That's a small problem, but my brain wouldn't let it go.

So, after a bit of fiddling, I can now post to Tumblr directly from Editorial, and my headlines get syndicated properly to Twitter.

Setting this up isn't trivial, so if you want to use it, you'll need to be comfortable with downloading scripts, working with the command line, screwing with API keys, and more. Also, this is only for creating text posts. Tumblr supports several other post types (photo, link, quote, etc.), but supporting those is outside the scope of this post.

### Getting Tumblr API Access

First, you'll need an OAuth key, which you can get by [registering an application](http://www.tumblr.com/oauth/apps) with Tumblr. Fill out the form and click **Register**. Here's how I filled out mine; you can do something similar:

![Form](http://674b7cd13acc6f89120f-67e41eba13667dee44e3f35da8964e2a.r70.cf5.rackcdn.com/image-1383063796.jpeg)

Now that you have an OAuth consumer key and secret, you'll need an access token. To get that, download [this script](https://gist.github.com/codingjester/2296339) (here's a link to the [raw text](https://gist.github.com/codingjester/2296339/raw/116139d24e6a3226be36eb6a95729cd614cd5163/oauth_tumblr.py)). Copy the text, and save it in a plain text file somewhere. Name it something like `tumblr.py`. Add your consumer key and consumer secret by replacing the values on lines 4 and 5.
    
    
    consumer_key = 'consumer_key'
    consumer_secret = 'consumer_secret'
    

Launch Terminal.app.

Navigate to the directory where you saved the `tumblr.py` script. If you dropped it into your Downloads folder, then you would enter `cd ~/Downloads` and press _Return_. Now, type `python tumblr.py` and press _Return_. Follow the prompts on the screen; it will ask you to paste a URL into your browser. When you do, you'll see a screen asking for access to your account. It will look like this:

![Auth Screen](http://674b7cd13acc6f89120f-67e41eba13667dee44e3f35da8964e2a.r70.cf5.rackcdn.com/image-1383063854.jpeg)

> _Click Allow. If you're using Safari, you'll see an error page. Don't panic; that's expected._

Go back to Terminal, type `y`, and press _Return_. You'll be asked for the `OAuth Verifier`. Go back to Safari, and look at the URL. You'll see a section that mentions `oauth_verifier`.

Select everything between the `=` and the `#` and copy it. Go back to Terminal, paste it in, and press _Return_. If you've completed these steps successfully, the script will spit out your access token and access secret. Huzzah!

### Setting Up Editorial

Before you can use the Tumblr API through Editorial, you'll need to install the official Tumblr Python client, [PyTumblr](https://github.com/tumblr/pytumblr). You can do so using [this workflow](http://editorial-app.appspot.com/workflow/6132822456664064/uY0MaqRPsW4), which I adapted from [Ole Zorn's workflow](https://gist.github.com/9c54a36c619261067225) for installing Rackspace's Cloudfiles client. Install the workflow and run it; you can delete the workflow after it runs.

Install the [Post to Tumblr workflow](http://editorial-app.appspot.com/workflow/5790693951799296/NdsP5TZ25wQ) in Editorial, then edit it. Tap the action titled **Post it**, and scroll the source code to line 7. Change the value of `BLOG_NAME` to your Tumblr blog's address (if you're using a custom domain, use the original `.tumblr.com` domain, not the domain you registered).

Replace the values on lines 17 through 20 with the consumer key, consumer secret, access key, and access secret you generated above.

Tap **Done** to save your changes.

### Using the Workflow

When you run the workflow, you'll be presented with a pop-up that asks for a title. It defaults to the file name of the current document. After entering a title, it'll ask you for tags. You can leave this blank, or you can enter a comma-separated list.

Now go write something and stop fiddling with your text editor!
