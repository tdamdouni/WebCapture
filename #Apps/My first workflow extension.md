# My first workflow extension

_Captured: 2015-06-12 at 22:46 from [medium.com](https://medium.com/p/15626afd4a77)_

![](https://d262ilb51hltx0.cloudfront.net/max/500/1*pBKggf3dCoTuIel2L8px2Q.jpeg)

### Automation with Workflow app on iOS

#### iOS and automation

It's been three years since I've discovered a new area on iOS : **automation **and **markdown. **I would like to thank Federico Viticci on [macstories.net](http://www.macstories.net/) for that. Before I didn't know anything about automation or markdown on iOS. My iPad was just for games and Internet although i wanted to use it for more things like writing notes. But you know, that iPad is not like your PC or Mac and when you need to format your text and apply bold, italic or anything else it can be really uncomfortable.

Things have changed now, my iPad is also good for my personal productivity (writing notes, writing codes, automating tasks). You can find a bunch of app about automation on the appstore.

I'm already use :

  1. **Pythonista**
  2. **Editorial**
  3. **Drafts**
  4. **Launch Center Pro**

All these apps are good. But since two weeks we can make things more incredible and in some way more simple with a new app call [Workflow](https://appsto.re/fr/2IzJ2.i). This app tends to be for normal person with no coding skills or knowledge about url scheme.

By using drag and drop you can build strong workflow like :

  * download file from a url on the clipboard
  * Make gif with selected images
  * Make PDF from Web pages

It is possible to combine Workflow with another app like Drafts or Pythonista. Workflow is genuinely powerful and we are going to see why. I made an example using the Tweets from Marvel.

#### Save tweet elements from Twitter

I follow the [Marvel](https://mobile.twitter.com/Marvel) account on Twitter and often you can see a tweet like this :

![](https://d262ilb51hltx0.cloudfront.net/max/748/1*YIDmwP8BT6hyvw9ejLgsBA.jpeg)

Before Workflow, I use to do the same process below :

  1. select the picture and copy it
  2. open Evernote
  3. create a new note and paste the marvel picture
  4. Come back in Twitter and copy url about the marvel character
  5. Come back to my previous note and paste the selected url
  6. Write title and tag for my note

This is a long process : tap screen, write text, copy and paste. Thanks to workflow you can do the same with less effort.

**There is my new process :**

  1. On tweetbot, select the **share **option and choose "**copy link" **then tap "**Run Workflow"**
![](https://d262ilb51hltx0.cloudfront.net/max/700/1*XaJts_eGK5pHav3VnwylNQ.jpeg)

2\. On Workflow, Choose the task to run

![](https://d262ilb51hltx0.cloudfront.net/max/700/1*GKj8VBk7JqmETXttbjMT-Q.png)

### Now this is how my workflow works.

  1. Set a variable with text in clipboard
  2. Launch a python script (I'm using Pythonista app). This script read the clipboard text and make readable data for workflow (a json style string).
![](https://d262ilb51hltx0.cloudfront.net/max/700/1*O-u_L6DG9fHX7jboxl0I2Q.png)

_my script sample from pythonista _:

![](https://d262ilb51hltx0.cloudfront.net/max/1303/1*V85WofyizDHaJ9KK0zH34Q.jpeg)

3\. Set two new variables with the previous data. This data will be useful for **Evernote**.

![](https://d262ilb51hltx0.cloudfront.net/max/800/1*UI-dx-YazDlhPp4ur2UmEg.png)

![](https://d262ilb51hltx0.cloudfront.net/max/800/1*6URc6V-6PtQ6CcJ-5ZQCTw.png)

4\. Find the right image from the original twitter link

![](https://d262ilb51hltx0.cloudfront.net/max/800/1*LhS8sySA40fDVEd6CQRrnQ.png)

5\. Insert the image in a new note

![](https://d262ilb51hltx0.cloudfront.net/max/800/1*yPr3sZ_9XPhR88XGQdn1EA.png)

6\. Update the note with Marvel's url

![](https://d262ilb51hltx0.cloudfront.net/max/800/1*dpCpx5vGbRtEk72yo4-58w.png)

And now you can see the result in evernote :

![](https://d262ilb51hltx0.cloudfront.net/max/800/1*X_Dbqf8auOb5v5euIb-HlQ.png)

Watch all the process in YouTube :

This is just an example, If you want to know more about **Workflow **read the long review by Federico Viticci [here](http://www.macstories.net/reviews/workflow-review-integrated-automation-for-ios-8/).
