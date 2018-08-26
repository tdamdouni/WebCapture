# Hacking GitHub to Build Your Own Wiki

_Captured: 2018-07-17 at 19:14 from [dzone.com](https://dzone.com/articles/hacking-github-to-build-your-own-wiki?edition=385247&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202018-07-17)_

[Learn how error monitoring with Sentry](https://dzone.com/go?i=299453&u=https%3A%2F%2Fsentry.io%2F_%2Flp%2Ftelephone-game-ebook%2F%3Futm_source%3Dadvertisement%26utm_medium%3Dtext%26utm_content%3Ddzonewebdevzone%26utm_campaign%3Dsponsorship) closes the gap between the product team and your customers. With Sentry, you can focus on what you do best: building and scaling software that makes your users' lives better.

Here at Ably, we have an immense amount of information that needs to be shared among our employees, from the various services we use to the usage of our own system and various company protocols.

Until recently, we've been using the [GitHub Wiki](https://help.github.com/articles/about-github-wikis/) functionality to do the job but lately, we have had a few issues with this. Firstly, there's no form of version control for the wiki available through the GitHub interface. Secondly, we wanted the wiki's content to be easily searchable from the actual page.

![](https://cdn-images-1.medium.com/max/1600/1*gJWkidKhcYg1SC4lN0OVSQ.jpeg)

We considered at first making use of an existing git-based wiki such as [Gollum](https://github.com/gollum/gollum), but soon realized that it wouldn't work for us due to its need to run on a server with the Git repository. In addition, systems such as [Heroku](https://www.heroku.com/) do not support it, making it a poor match for our needs.

Given this, we wanted to convert the GitHub Wiki to one of our own hosted sites. In order to accomplish this, we needed a number of things:

  * A web application framework.
  * A method of presenting our markdown files in a static site.
  * An authentication scheme to keep our wiki private.
  * A place to host this new wiki.
![](https://cdn-images-1.medium.com/max/1600/1*dcF2_ClcpT8Cl-uawtCHLw.png)

> _You can find the base code used to build this tool, in our GitHub Repository._

### **1\. Web Application Framework - Sinatra**

We based our wiki on [Sinatra](http://sinatrarb.com/), a web application library written in Ruby. This is a really simple way to get the foundation of your site running. It comes with some [great tutorials](http://sinatrarb.com/intro.html) on how to get started. With Sinatra we had the infrastructure to present our pages, however, we still needed a way to interpret our markdown files to display them.

### **2\. Presenting Markdown Files - Jekyll**

To convert our markdown pages we settled on [Jekyll](https://jekyllrb.com/). Jekyll will process any markdown, HTML, and CSS and combine it all into a static site, which is exactly what we needed. By creating some CSS files to structure our pages, and storing our markdown pages in a folder, we were able to construct HTML pages with ease. Once the static site has been generated into a folder called **_site**, we were able to have Sinatra use this folder as a basis for presenting pages.

### **3\. Searching Pages - Simple-Jekyll-Search**

![](https://cdn-images-1.medium.com/max/1600/1*P0DlyPIIlc1FJTouJ4TfPA.gif)

Beyond simply hosting and presenting our wiki pages, we wanted to be able to search through them. To do this, we constructed a sidebar containing the titles of each of the searchable pages, and then made use of [Simple-Jekyll-Search](https://github.com/christian-fei/Simple-Jekyll-Search) to easily search through these titles and content of each page. This was just a matter of defining the search structure and results we wanted in a **search.json** file, followed by presenting the results in place of the usual sidebar results.

### **4\. Authentication: Auth0**

As we intended to use this wiki for internal use only, we needed some method of authentication when accessing it. [Auth0](https://auth0.com/) provides a simple API to authenticate throughout the site, abstracting away all the complexities involved with authentication.

### **5\. Deploying: Heroku**

Finally, we needed a way to make our site widely accessible. In order to simplify the process, we made use of [Heroku](https://www.heroku.com/) for hosting our new site. With its easy GitHub integration, this allows us to not only automatically pull new wiki material from our master branch when it gets updated, but also allows access to versioned sites for testing.

## **Conclusion**

By making use of the above tools, it ended up being simple to create our own site to host our old GitHub Wiki. If you want to make your own wiki, check out our [template code](https://github.com/ably/wiki-site) and try making something cool. Give us a shout on [Twitter](https://twitter.com/ablyrealtime) to show off what you built using this template!

[What's the best way to boost the efficiency of your product team](https://dzone.com/go?i=299454&u=https%3A%2F%2Fsentry.io%2F_%2Flp%2Ftelephone-game-ebook%2F%3Futm_source%3Dadvertisement%26utm_medium%3Dtext%26utm_content%3Ddzonewebdevzone%26utm_campaign%3Dsponsorship) and ship with confidence? Check out this [ebook](https://dzone.com/go?i=299454&u=https%3A%2F%2Fsentry.io%2F_%2Flp%2Ftelephone-game-ebook%2F%3Futm_source%3Dadvertisement%26utm_medium%3Dtext%26utm_content%3Ddzonewebdevzone%26utm_campaign%3Dsponsorship) to learn how Sentry's real-time error monitoring helps developers stay in their workflow to fix bugs before the user even knows there's a problem.
