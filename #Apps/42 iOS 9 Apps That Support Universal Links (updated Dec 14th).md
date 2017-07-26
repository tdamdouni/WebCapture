# 42 iOS 9 Apps That Support Universal Links (updated Dec 14th)

_Captured: 2015-12-15 at 01:03 from [www.jackivers.me](http://www.jackivers.me/blog/2015/9/17/list-of-universal-link-ios-9-apps)_

[December 14, 2015](/blog/2015/9/17/list-of-universal-link-ios-9-apps) [by Jack Ivers](/?author=54fa4aa8e4b056e8865b8bc7) in [Mobility](/?category=Mobility)

As I describe [here](http://www.jackivers.me/blog/2015/9/16/ios-9-seamlessness), seamlessness is a killer feature of iOS 9, and Universal Links are one of the best experiences of seamlessness: click a simple URL link, in Mail, Messages, Safari, etc.—and BOOM you're looking at the content or feature right inside the native app.

![](http://static1.squarespace.com/static/54fa4aaae4b04430414130c7/t/55fb6591e4b069a5199459f3/1442538898879/)

A long list of apps have already launched that take advantage of two of iOS 9's Search APIs (NSUserActivity and CoreSpotlight). These APIs which expose the apps' content, features, and navigation points when the user searches in iOS 9—not only in Spotlight searches but also within Safari. Examples include IMDB, 1Password, and Dropbox. 

![](http://static1.squarespace.com/static/54fa4aaae4b04430414130c7/t/55fb65bbe4b069a519945a93/1442538940141/)

A growing number of apps are supporting iOS 9's third search API, known as Web Markup, which makes seamless Universal Links possible. For apps whose content is also available on the web (think Airbnb), Universal Links allow standard http / https web URLs to open directly in the app on iOS 9 with no delay and no jarring intermediate steps (like passing through Safari on the way). 

Implementing Web Markup and Universal Links is taking app makers a little longer than other iOS 9 updates, because there are two moving parts instead of just one: both the app and the website need to be updated. On the website side, it's not a massive change—there's no need for wholesale changes to web content—but it does require sysadmin attention, including SSL signing of the "apple-app-site-association" file.

Anyway, I'm excited to see the list keep expanding as more apps roll out their updates. The list below shows what I've found so far, and I'll keep updating this post as I find more.

In the list below, the example Universal Links should, on an iOS 9 device with the associated app installed, open directly in-app. (I recently discovered that there's [apparently an iOS 9 / Universal Links bug](https://openradar.appspot.com/22826286) that can bite if you had an app installed before upgrading to iOS 9—this proved to be the case with my Dropbox installation, where Universal Links began working after I deleted and reinstalled the Dropbox app.)

### Universal-Link-Aware iOS 9 App/Websites as of 14 Dec 2015

  1. Yelp: [app](https://itunes.apple.com/us/app/yelp/id284910350?mt=8), [app-site-association file,](https://www.yelp.com/apple-app-site-association) [example Universal Link](https://www.yelp.com/biz/michael-winnetka)
  2. Amazon: [app](https://itunes.apple.com/us/app/amazon-app-shop.../id297606951?mt=8), [app-site-association file,](https://www.amazon.com/apple-app-site-association) [example Universal Link](http://www.amazon.com/gp/product/B00H1V4EB2?ref_=gbsl_tit_l-1_4822_1b77a67c&smid=A1KWJVS57NX03I)
  3. Pinterest: [app](https://itunes.apple.com/us/app/pinterest/id429047995?mt=8), [app-site-association file,](https://www.pinterest.com/apple-app-site-association) [example Universal Link](https://www.pinterest.com/pin/497366352577351924/)
  4. OpenTable: [app](https://itunes.apple.com/us/app/opentable-restaurant.../id296581815), [app-site-association file,](https://www.opentable.com/apple-app-site-association) [example Universal Link](http://www.opentable.com/restaurant/profile/33160?shareReferrer=ios-share)
  5. The Guardian: [app](https://itunes.apple.com/us/app/the-guardian/id409128287), [app-site-association file,](http://www.theguardian.com/apple-app-site-association) [example Universal Link](http://www.theguardian.com/us-news/2015/sep/18/democratic-candidate-lawrence-lessig-tv-debate-catch-22)
  6. Flipboard: [app](https://itunes.apple.com/us/app/flipboard-your-social.../id358801284), [app-site-association file,](https://flipboard.com/apple-app-site-association) [example Universal Link](https://flipboard.com/section/chicago-tribune-5q3jr8kd93498eib)
  7. Citymapper: [app](https://itunes.apple.com/app/id469463298), [app-site-association file,](https://citymapper.com/apple-app-site-association) [example Universal Link](https://citymapper.com/chicago/d/clybourn)
  8. Resy: [app](https://itunes.apple.com/us/app/resy-restaurant.../id866163372), [app-site-association file,](https://resy.com/apple-app-site-association) [example Universal Link](https://resy.com/cities/ny)
  9. Houzz: [app](https://itunes.apple.com/us/app/houzz-interior-design.../id399563465), [app-site-association file,](http://www.houzz.com/apple-app-site-association) [example Universal Link](http://www.houzz.com/photos/7709199/Craftsman-Exterior-craftsman-exterior-vancouver)
  10. Chairish: [app](https://itunes.apple.com/us/app/chairish-home-decor.../id738192971), [app-site-association file,](https://www.chairish.com/apple-app-site-association) [example Universal Link](https://www.chairish.com/collection/chandeliers)
  11. Foursquare: [app](https://itunes.apple.com/us/app/foursquare-find-places.../id306934924), [app-site-association file,](https://foursquare.com/apple-app-site-association) [example Universal Link](https://foursquare.com/v/trifecta-grill/4f54f50be4b0e14ed9cf52e0)
  12. B&H Photo: [app](https://itunes.apple.com/us/app/b-h-photo-video-pro.../id390928219), [app-site-association file,](https://bhphotovideo.com/apple-app-site-association) [example Universal Link](http://www.bhphotovideo.com/c/product/1121967-REG/vizio_e43_c2_43_1080p_full_array_led.html)
  13. Join.me: [app](https://itunes.apple.com/us/app/join-me/id409811927), [app-site-association file,](https://join.me/apple-app-site-association) [example Universal Link](https://join.me/344-684-243)
  14. Twitter: [app](https://itunes.apple.com/us/app/twitter/id333903271), [app-site-association file,](https://twitter.com/apple-app-site-association) [example Universal Link](https://twitter.com/mchappell51)
  15. Dropbox: [app](https://itunes.apple.com/us/app/dropbox/id327630330), [app-site-association file,](https://www.dropbox.com/apple-app-site-association) [example Universal Link](https://www.dropbox.com/s/oaze4qfl97hksef/IMG_0019%20%281%29.png?dl=0)
  16. Quip: [app](https://itunes.apple.com/us/app/quip-docs-chat-spreadsheets/id647922896), [app-site-association file,](https://quip.com/apple-app-site-association) [example Universal Link](https://quip.com/eGpoAvtgOjUZ)
  17. Estately: [app](https://itunes.apple.com/us/app/estately-homes-for-sale.../id764642939), [app-site-association file,](https://estately.com/apple-app-site-association) [example Universal Link](http://www.estately.com/listings/info/6341-west-henderson-street--1)
  18. Top10: [app](https://itunes.apple.com/us/app/top10-the-best-hotels/id876337397), [app-site-association file,](https://top10.com/apple-app-site-association) [example Universal Link](https://top10.com/san-francisco-hotels?count=20&currency=USD&guests=2&arrival=2015-10-18&departure=2015-10-19)
  19. Airbnb: [app](https://itunes.apple.com/us/app/airbnb/id401626263), [app-site-association file,](https://www.airbnb.com/apple-app-site-association) [example Universal Link](https://www.airbnb.com/rooms/4516626?checkin=10%2F02%2F2015&checkout=10%2F03%2F2015&s=hVefWpV6)
  20. Art Authority: [app](https://itunes.apple.com/us/app/art-authority-for-ipad/id364048834), [app-site-association file,](http://community.artauthority.net/apple-app-site-association) [example Universal Link](http://community.artauthority.net/period.asp?rid=29)
  21. Periscope:  [app](https://itunes.apple.com/us/app/periscope/id972909677), [app-site-association file,](https://periscope.tv/apple-app-site-association) [example Universal Link](https://www.periscope.tv/w/aNqMZzIzNjUzOTJ8MURYeHl3UHpBRFdHTVGUIeGTgD5C26D4qOBVQOtkeGcu3ub17p4cug7qqbn7)
  22. Google Maps: [app](https://itunes.apple.com/us/app/google-maps/id585027354), [app-site-association file,](https://www.google.com/apple-app-site-association) [example Universal Link](https://goo.gl/maps/16rkM3Dz8c12)
  23. Medium: [app](https://itunes.apple.com/us/app/medium/id828256236), [app-site-association file,](https://medium.com/apple-app-site-association) [example Universal Link](https://medium.com/woah-basecamp-3/basecamp-3-adoptional-555e26a4b8b2)
  24. Storehouse: [app](https://itunes.apple.com/us/app/storehouse-photo-video-collages/id791297521), [app-site-association file,](https://storehouse.co/apple-app-site-association) [example Universal Link](https://strh.se/rbqKjbhvPmgz)
  25. Timeline.com: [app](https://itunes.apple.com/us/app/timeline-news-in.../id948867534), [app-site-association file,](https://timeline.com/apple-app-site-association) [example Universal Link](https://www.timeline.com/stories/amy-winehouse)
  26. Overcast: [app](https://itunes.apple.com/us/app/overcast-podcast-player/id888422857), [app-site-association file,](https://overcast.fm/apple-app-site-association) [example Universal Link](https://overcast.fm/+IgzLtibo)
  27. Swarm: [app](https://itunes.apple.com/us/app/swarm-by-foursquare/id870161082), [app-site-association file,](https://swarmapp.com/apple-app-site-association) [example Universal Link](https://www.swarmapp.com/c/bhaSVFbLw6O)
  28. Kayak: [app](https://itunes.apple.com/us/app/kayak-flights-hotels-cars/id305204535), [app-site-association file,](https://kayak.com/apple-app-site-association) [example Universal Link](http://www.kayak.com/flights/BOS-ORD/2015-10-21/2015-10-24)
  29. ibotta: [app](https://itunes.apple.com/us/app/ibotta-cash-back-app.-grocery/id559887125), [app-site-association file,](https://ibotta.com/apple-app-site-association) [example Universal Link](https://ibotta.com/rebates/27574/chobani-oats-greek-yogurt?ref=appshare&friend=wdpnkab)
  30. Yummly: [app](https://itunes.apple.com/us/app/yummly-recipes-grocery-shopping/id589625334), [app-site-association file,](https://yummly.com/apple-app-site-association) [example Universal Link](http://www.yummly.com/recipe/Baked-Herbed-Salmon-1064708)
  31. Flickr: [app](https://itunes.apple.com/us/app/flickr/id328407587), [app-site-association file,](https://flickr.com/apple-app-site-association) [example Universal Link](https://www.flickr.com/photos/psysex/7908800370/in/gallery-flickr-72157660726460751/)
  32. Jet.com: [app](https://itunes.apple.com/us/app/jet-smartest-way-to-shop-save/id950022424), [app-site-association file,](https://jet.com/apple-app-site-association) [example Universal Link](https://jet.com/product/Samsung-UN24H4000AF-LED-TV-24-Class-236-Viewable/ccf73b64e85b418a8098094d6d8d8d04)
  33. Shazam: [app](https://itunes.apple.com/us/app/shazam/id897118787), [app-site-association file,](https://www.shazam.com/apple-app-site-association) [example Universal Link](http://www.shazam.com/track/279248802/hotline-bling)
  34. IMDb: [app](https://itunes.apple.com/us/app/imdb-movies-tv/id342792525), [app-site-association file,](https://www.imdb.com/apple-app-site-association) [example Universal Link](http://www.imdb.com/title/tt3659388/?ref_=nv_sr_1)
  35. NYTimes.com: [app](https://itunes.apple.com/us/app/nytimes-breaking-local-national/id284862083), [app-site-association file,](https://nytimes.com/apple-app-site-association) [example Universal Link](http://www.nytimes.com/2015/12/10/opinion/the-trump-effect-and-how-it-spreads.html?_r=0)
  36. TripAdvisor.com: [app](https://itunes.apple.com/us/app/tripadvisor-hotels-flights/id284876795), [app-site-association file,](https://tripadvisor.com/apple-app-site-association) [example Universal Link](http://www.tripadvisor.com/Hotel_Review-g42758-d1102778-Reviews-Comfort_Inn_Traverse_City-Traverse_City_Grand_Traverse_County_Michigan.html)
  37. LinkedIn: [app](https://itunes.apple.com/us/app/linkedin-connected/id635424128), [app-site-association file,](https://linkedin.com/apple-app-site-association) [example Universal Link](https://www.linkedin.com/in/jackivers)
  38. Spotify: [app](https://itunes.apple.com/us/app/spotify-music/id324684580), [app-site-association file,](https://open.spotify.com/apple-app-site-association) [example Universal Link](https://open.spotify.com/artist/3hv9jJF3adDNsBSIQDqcjp)
  39. SoundCloud: [app](https://itunes.apple.com/us/app/soundcloud-music-audio/id336353151), [app-site-association file,](https://soundcloud.com/apple-app-site-association) [example Universal Link](https://soundcloud.com/jack-soundcloud/the-ballmerator)
  40. Groupon: [app](https://itunes.apple.com/us/app/groupon-deals-coupons-shopping/id352683833), [app-site-association file,](https://groupon.com/apple-app-site-association) [example Universal Link](https://www.groupon.com/deals/navy-pier-inc)
  41. Kickstarter: [app](https://itunes.apple.com/us/app/kickstarter/id596961532), [app-site-association file,](https://kickstarter.com/apple-app-site-association) [example Universal Link](https://www.kickstarter.com/projects/mst3k/bringbackmst3k?ref=discovery)
  42. Songkick: [app](https://itunes.apple.com/us/app/songkick-concerts/id438690886), [app-site-association file,](https://songkick.com/apple-app-site-association) [example Universal Link](http://www.songkick.com/festivals/89286-laneway/id/25028789-laneway-festival-2016)

### Apps That May Support Universal Links Soon

In my quest to find new apps that support Universal Links, I frequently run into the case where app makers have an apple-app-site-association file on their web presence, but the app isn't working yet with Universal Links. In other cases, the developer has announced via release notes, etc. that they support Universal Links but the app doesn't actually work yet (e.g., Zillow, Ticketmaster).

My Universal Link validation process is as follows:

![](http://static1.squarespace.com/static/54fa4aaae4b04430414130c7/t/566af916bfe873e74a301d2d/1449851158925/)

  1. Using Apple's [validation tool,](https://search.developer.apple.com/appsearch-validation-tool) confirm that the app's web presence has an apple-app-site-association file deployed, and check what URL patterns the app should support.
  2. Paste a valid URL into Messages or Notes.
  3. On an iOS device with the app installed, long-press the Universal Link URL and see if the app has correctly registered itself to handle the URL. If so, the popup will show an option to open the link in the app:
  4. Verify that the app correctly opens the Universal Link. I've seen cases where the app immediately forwards the request on to Safari, or fails to open the specified content.

Below is a list of such work-in-process cases, which I'm hoping are apps that should see Universal Link support soon. Unless otherwise noted, the app maker already has an apple-app-site-association file deployed on their web presence but the app isn't working yet.

  * [Netflix](https://netflix.com/apple-app-site-association)
  * Zillow: Announced but not functional.
  * Ticketmaster: Announced but not functional.
  * Instagram
  * Tumblr
  * Shazam
  * Vine
  * Viator
  * BuzzFeed
  * Glassdoor.com: URLs from the website do "open" directly in the app, but instead of opening the linked content, the app simply opens in its prior state, such as the last search run. 
  * RentTheRunway
  * Vimeo
  * Zappos
  * Hotwire.com
  * ebay: Their app-site-association file is clearly in a testing-only mode at this point.

### Built-in Magic Pseudo Universal Link Apps

Some of Apple's own apps, and a few 3rd-party apps, support Universal Linking behavior (open URLs direct in the app) but through iOS-level magic instead of the official Universal Links mechanism. Behavior is slightly different than with real Universal Links: for example, no Open In "[app name]" choice gets displayed in a long-press popover. Among the apps in this category:

  * Apple Maps
  * YouTube
