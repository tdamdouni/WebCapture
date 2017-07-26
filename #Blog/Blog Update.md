# Blog Update

_Captured: 2016-12-20 at 17:26 from [www.philweber.com](http://www.philweber.com/2016/12/blog_update/?utm_content=bufferb1d60&utm_medium=social&utm_source=twitter.com&utm_campaign=buffer)_

It all started with a tweet.

![The tweet that started it all](http://www.philweber.com/images/wordpress-tweet-thumb.png)

Last summer, a colleague asked for recommendations of WordPress alternatives; I replied with a link to [this article](http://sixrevisions.com/wordpress/wordpress-alternatives/). At the time, I had been running this site on [Movable Type](https://en.wikipedia.org/wiki/Movable_Type) for over 10 years; the article piqued my interest: Did I really need a full-fledged content-management system? Did I need to keep shelling out $10 a month for a web host with a database server?

I decided to give [Jekyll](http://jekyllrb.com) a try. The Jekyll documentation includes a [handy script](http://import.jekyllrb.com/docs/mt/) for importing posts from Movable Type. I found a [Bootstrap](http://getbootstrap.com)-based, [Medium](https://medium.com)-esque [theme](https://startbootstrap.com/template-overviews/clean-blog/) that I liked, and [Manuel Gruber](http://manuelgruber.com/) (no relation to [Hans](https://en.wikipedia.org/wiki/List_of_Die_Hard_characters#Hans_Gruber)) has an [awesome post](http://manuelgruber.com/2014/jekyll-bitbucket-to-aws-s3/) explaining how to have [Wercker](http://www.wercker.com) (a free continuous integration service) rebuild my site and deploy it to [Amazon S3](https://aws.amazon.com/s3/) whenever I check in a change.

Within a few hours, I had a fast, good-looking site running on modern software, and my hosting bill from Amazon is less than a dollar a month. I recently upgraded to [Jekyll version 3](https://jekyllrb.com/news/2015/10/26/jekyll-3-0-released/); at the same time, I added an [archive](http://www.philweber.com/archive/) page to surface older content on the site.

### Authoring on the iPad

Now that I can create a post simply by editing a [Markdown](https://en.wikipedia.org/wiki/Markdown) file and committing it to a Github repository, I wondered if it's practical to post from my iPad. (You may recall that I [struggled with this](http://www.philweber.com/2010/05/traveling_with_the_ipad/) several years ago.) This post is evidence that it is indeed: I authored it almost entirely on my 9.7-inch iPad Air 2 (I cheated a bit and created the image thumbnails on a Mac).

There are several capable Github clients in the App Store; I chose [Git2Go](http://git2go.com/) because of its attractive UI and reasonably-priced ability to access private repos. My first step in writing a new post is to create a _draft_ branch and clone it to the iPad.

![Git2Go](http://www.philweber.com/images/git2go-thumb.png)

[Textastic](https://www.textasticapp.com/) gets rave reviews and integrates nicely with Git2Go: I can create a new file in Textastic and export it to my local repo, or create an empty file in the repo and open it in Textastic for editing.

![Editing this post in Textastic](http://www.philweber.com/images/textastic-thumb.png)

My one complaint is that my (older) version of Textastic doesn't support [Split View](https://support.apple.com/en-us/HT202070) in iOS. It's a bit tedious to have to switch to a separate app to look up a link (or use the anemic Slide Over mode), but I'm not sure it's worth an additional $10 to upgrade to the latest version.

### What about QA?

At this point, I could commit my changes and merge the _draft_ branch with _master_; my Wercker process would kick off and automatically publish the post to my site. But I'd prefer to preview the post in a browser and correct any issues before I push it to production. I have several options:

  * [Manuel Gruber](http://manuelgruber.com/2014/jekyll-bitbucket-to-aws-s3) uses two S3 buckets, one for QA and one for Production. When he commits to his _draft_ branch, Wercker publishes his site to the QA bucket, which is accessible at a secret URL. I considered this approach, but Wercker takes several seconds to publish the site; that would quickly become annoying if I wanted to make several changes;

  * [Aerobatic](https://www.aerobatic.com/blog/automated-continuous-deployment-of-jekyll-sites) offers automated continuous deployment of Jekyll sites. It works with [Bitbucket](https://www.atlassian.com/software/bitbucket), where I host my code (free private repos!), and it will host up to two sites free of charge. But the free tier only allows five deployments a day; I can see myself easily blowing through that trying to fine-tune some CSS;

  * What I really want is the same experience I get while working on my laptop: open a Terminal and execute `jekyll serve`, then point my browser at `localhost:4000` and preview the site. I thought I had found the perfect solution: [Codeanywhere](https://codeanywhere.com/) spins up a container and runs your code in the cloud; the container is accessible via SSH. But alas, it chooses a random SSH port each time it starts a container; there's no way to see what that port is in their mobile app, and their web application doesn't work correctly in mobile browsers. ☹

I was ready to resign myself to merely _writing_ on the iPad and waiting to publish until I got back to my desk, or using RDP to launch Codeanywhere on my home computer and finding the secret SSH port. But then it hit me: _AWS!_

If I set up an EC2 instance with Git and Jekyll, can I start it from my iPad, pull the latest code from my repo, and use an SSH client to run `jekyll serve`? Yes!

![Previewing my Jekyll site on an AWS EC2 instance](http://www.philweber.com/images/aws-shell-thumb.png)

Then I can point my iPad browser at _[ec2-instance-name]_:4000 to preview the post:

![Voilà!](http://www.philweber.com/images/preview-post-thumb.jpg)

Now I can write, preview, and publish posts wherever I am when inspiration strikes…as long as I have my iPad with me. And an external keyboard. After writing this post on the iPad, I've learned that trying to do real work makes that 9.7-inch screen feel _really_ small; maybe I need to upgrade to the large model. 😉

[Leave a comment](mailto:blog@philweber.com?subject=Comment%20on-2016-12-blog_update)
