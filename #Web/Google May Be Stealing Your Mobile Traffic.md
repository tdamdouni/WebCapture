# Google May Be Stealing Your Mobile Traffic

_Captured: 2016-12-14 at 09:33 from [www.alexkras.com](https://www.alexkras.com/google-may-be-stealing-your-mobile-traffic/)_

**Update 10/17/2016 6:30pm:** You can read a response from the tech lead of the AMP Project for Google, [in the comment area](https://www.alexkras.com/google-may-be-stealing-your-mobile-traffic/#comment-55336).

**Update 11/01/2016 10:40pm:** After learning more about AMP, it became clear that the original title was inaccurate. A better title would have been **You may be losing Your Mobile Traffic**.

**Update 11/03/2016 10:30pm:** I was invited to have lunch with Google AMP team, where I got to discuss some of my concerns. [I've summarized my key takeaways here](https://www.alexkras.com/i-had-lunch-with-google-amp-team/).

I run my blog on WordPress with a custom theme. 6 month ago I've added support for Accelerate Mobile Pages (AMP) in order to provide better user  
experience for mobile devices. I did not research the AMP project well and have made some costly false assumptions that I wanted to share.

Most importantly, I was surprised to find out that instead of redirecting users to an optimized version hosted on my server, Google was actually serving a snapshot of the page from their own cache. To make things worse, Google was injecting a large toolbar at the top of the snapshot encouraging users to get back to Google search results (a functionality already provided by the back button) and making it harder to get to the original site.

To draw a contrast, Google have been keeping snapshots of sites for a very long time, available via a "cache" link right next to search results. The cache link, however, was optional. Clicking on the search result, traditionally, would take the user to the original source. With AMP, Google have turned this equation around.

I do believe that Accelerated Mobile Pages is a great project! At the same time, I find the way Google handles redirects slightly dishonest and very concerning.

## Accelerated Mobile Pages

Accelerated Mobile Pages (AMP) is a newish open source project that Google launched in the February of 2016.

[In their own words](https://www.ampproject.org/learn/about-amp/):

> AMP is a way to build web pages for static content that render fast. AMP in action consists of three different parts:
> 
> **AMP HTML** is HTML with some restrictions for reliable performance and some extensions for building rich content beyond basic HTML. The **AMP JS** library ensures the fast rendering of AMP HTML pages. The Google **AMP Cache** can be used to serve cached AMP HTML pages. 

You can watched [this promotional video](https://www.youtube.com/watch?v=WrpkFROqR0Q) to learn more about the project.

Most Web Developer would recognize the [suggested list of features](https://www.ampproject.org/learn/how-amp-works/) (listed below) as a great thing.

  * Allow only asynchronous scripts
  * Size all resources statically
  * Keep all third-party JavaScript out of the critical path
  * All CSS must be inline and size-bound
  * Font triggering must be efficient
  * Minimize style recalculations
  * Only run GPU-accelerated animations
  * Prioritize resource loading
  * Load pages in an instant

As an added bonus, it was rumored that Google will prioritize AMP optimized pages in their search results, so there was really no downside in giving it a try. Or so I thought.

## AMP In Action

I run my blog on WordPress, so it was really easy to add AMP support via the [AMP plugin](https://wordpress.org/plugins/amp/). I remember bragging that it took less than 5 minutes to set it up, saying "Google wants, Google gets".

I've been running my site with AMP support for over 6 months now.

If you head over to Google and search for "Git Tips" you will see my site with the APM icon next to it.

![1-amp-demo](https://www.alexkras.com/wp-content/uploads/1-amp-demo.png)

Clicking on that link will open up AMP friendly view of the post.

![2-in-amp-close](https://www.alexkras.com/wp-content/uploads/2-in-amp-close.png)

## The Problem

So far everything seems great, with one big problem. The view above is not being served from my site, but rather from Google Cache.

The URL of the page looks as follows:

`https://www.google.com/amp/s/www.alexkras.com/19-git-tips-for-everyday-use/amp/?client=safari`

Essentially, the original link with `www.google.com/amp/s/` added in front of it.

Which is actually a good thing. It reduces load on my site and allows readers to access to the information much faster that my $10 a month server could accommodate.

**So Why in the world am I complaining**, even going as far as to imply that Google might be stealing my mobile traffic?

### Guess what happens when the "close" button is clicked inside the AMP view?

![3-close-button](https://www.alexkras.com/wp-content/uploads/3-close-button.png)

I was expecting it to cause a redirect to the original article. **Instead it redirects back to Google search results.** Say What? How are people supposed to get to my site?

Luckily in my case there is a blue header at the top, clicking on which would redirect to the homepage. I have seen a number of sites, however, that do not have such header. In those cases, I literally had to copy the URL and paste it into my browser to get to the original site. I am afraid that most readers are not willing to go through that trouble.

Also note that even with the header in place, landing on the home page will make it really hard to locate the original article returned via the Google search.

One final nitpick. If Google cares so much about the mobile experience, why cover 15% of the small mobile screen with a fat bar at the top?

## What about the little guy or gal?

If you watched the [AMP promotional video](https://www.youtube.com/watch?v=WrpkFROqR0Q), you've heard them talk about the web as the greatest innovation of our time. Except the user experience was broken on mobile and AMP set out to fix just that.

I think Richard Gingras, Head of News at Google, said it best and I quote: "[Let's make the web great again](https://www.youtube.com/watch?v=WrpkFROqR0Q&feature=youtu.be&t=2m39s)".

_Note: To be fair, Richard Gingras said it way before Donald Trump made it his campaign slogan. Still I couldn't resist to point that coincidence out._

![great-again](https://www.alexkras.com/wp-content/uploads/great-again.png)

Unfortunately, in the process of fixing the Web, Google broke something else. It used to work like this:

  1. Search Google 
  2. Find interesting result 
  3. Go to the site
  4. Explore the site further **OR** hit the back button to go back to Google search results

Now it works like this:

  1. Search Google 
  2. Find interesting result 
  3. Read the content without leaving Google 
  4. Try to explore the original site **AND** get redirected back to Google search results.

The web used to be the place where anybody could publish quality content, help thousands of people, and earn a few dollars along the way. Google Adsense was one of the main products that made this reality possible.

A lot of authors hope that people would find their content useful, stay for a while and come back in the future. None of this will work if readers are not able to get to the site in the first place.

In addition, given the wide spread of Ad Blocking software, mobile platform remains one of few places where ad revenue continues to be a viable option.

**By hijacking the mobile traffic and keeping users from leaving their site, Google gets to benefit from somebody else's content while at the same time displaying their ads.** This cuts further into already narrow margins of independent publishers.

## What can be done?

### Ask Google to give users an easy option to view the original post.

Google could change the close button to take users to the original site. Alternatively, a different button can be added to provide users with such option.

### Make sure your AMP content is optimized for the new deal

I think it is important to point out that Google **is** playing by the AMP rules. My main concern is that a lot of people (like myself a week ago) have yet to realize that AMP search results are being treated differently from other search results.

In other words, Google is playing by the rules, but the rules have changed.

When I installed the AMP plugin, I assumed that all my setting from my main site will carry over. This was not the case.

The AMP plugin extracted the text content and stripped everything else out. I noticed some of it, but did not, for example, realized that it removed my Analytics code. I wasn't too concerned with the changes that I did notice, because I assumed that users will have an easy way to drop back to my original site. As of writing of this article, there is no such option.

That being said, Google allows AMP sites to display whatever content they like, as long as it complies with AMP rules.

### I recommend each AMP enabled side to do the following

  1. Make sure your Analytics tracking code is [properly installed](https://developers.google.com/analytics/devguides/collection/amp-analytics/)
  2. Make sure you have a header that points back to your main site
  3. If your site has a menu, make sure it is visible in the AMP version
  4. Consider adding a link at the top of your AMP page, giving user an option to visit the original post
  5. Make sure your ads and other promotional material is properly integrate into the AMP version 

## Conclusion

I hope I am not being too hard on Google. I get it. Real innovation is hard. It takes courage. No one can get everything right on the first try and it's easy to overlook some details. Since AMP is an open source project, I assume my feedback is welcomed.

That being said, it's the people, millions of authors who take their time to write and billions of readers who take their time to read, comment and share that make the Web great.

Google is improving things for the mobile readers with the AMP project. I only wish they could do so without hurting the content creators.

P.S. This post has generated an interesting [discussion on Hacker News](https://news.ycombinator.com/item?id=12722590), with some good examples both supporting and opposing my arguments.
