# Deep linking & search in iOS 9 will change everything

_Captured: 2015-09-24 at 00:50 from [medium.com](https://medium.com/ios-os-x-development/deep-linking-search-in-ios-9-will-change-everything-feab0bb7e189)_

The holy grail for any investor is to discover the next Google and [deep linking](http://en.wikipedia.org/wiki/Deep_linking) has been a pathway largely because the iOS app world has been incredibly fragmented -- both in search & app-to-app communication. There are a flurry of startups trying to solve this problem. There's [URX](http://www.urx.com), which lets an application developer search and display relevant deep links on her application. There is also [Button](http://www.usebutton.com) which allows an application developer to embed deep actions to other third party apps. Another is [Parse](http://www.parse.com). Now, these startups have a powerful platform player in the game, Apple.

Just this week, Apple unveiled iOS 9 with a slew of new features from news to multi-tasking to intelligence. However, one foundational piece of functionality was somewhat glanced over during the keynote --universal deep linking. In iOS 9, apps are cohesively linked together via deep links and the experience feels magical.

### How deep linking works in iOS 9

Say one of your friends tweets a Foursquare link to her favorite restaurant. Before, when you tapped the link on Twitter for iOS, it simply launched the web view as it does for millions of other links -- even if you had the Foursquare app installed.

This is because Twitter has no idea how to link you to that restaurant inside of the Foursquare app. Wouldn't it be great if iOS knew that I had Foursquare installed? Wouldn't it be great if it routed me appropriately to that restaurant inside of the Foursquare app? That's exactly what happens in iOS 9.

Now when you tap that Foursquare link, iOS 9 intelligently routes you to that exact place inside of the Foursquare app bypassing Safari altogether. On top of that, it throws in a handy back link so you can go back to your Twitter timeline with just one tap.

The experience is exactly what you would expect when two apps work seamlessly together. One caveat is that all of this only works if Foursquare creates the URL path mappings between its web and native experience (as specified in the iOS developer docs) but there is no reason why Foursquare wouldn't do so.

Another simple example: let's say you're in the ESPN app reading about the Warriors. The ESPN app could place a buy button on the page for the next Warriors home game linked to a StubHub web link. In the previous world, this link would kick you to Safari or open a web view but now since StubHub would have registered this link in iOS 9, the StubHub app opens and you're magically into the purchase flow inside of the app.

In iOS 9, navigating between apps feels extremely fluid. The app content loads quickly. And a back link in the status bar is added to help you go back to the previous app. For the first time ever on iOS, there is a fluid system in place to help you navigate between apps.

Apple calls this Universal Deep Linking. It will have a profound impact on the iOS ecosystem and more importantly on mobile search.

### Search

While it's great that apps can link to each other in a way that we're all used to, via web links, what's more important is the implication of deep linking on mobile search. At the moment, any blue link you tap, whether on Google Search App for iOS or Google.com, is mostly web content that Google has crawled. But we live in an age where a large chunk of interesting content also lives inside of apps, completely inaccessible to Google or anyone else for that matter.

This week, Apple laid out a set of powerful APIs that are intended to solve this problem. The first API lets an application developer tell iOS about her content. The developer specifies the content, the keywords associated with that content, and a deep link to that content. Once she does that, iOS indexes the content and gets it ready for a potential search by a user.

For example, say you're searching for a Baklava recipe on iOS search. The developer of Yummly has already told iOS that she has an incredible recipe for Baklava and other users have also tapped on her deep link (more on this later). The Yummly link is ranked as number one for Baklava and when tapped takes you directly to the Baklava recipe inside the Yummly app. In addition, a back link is added to the top left to get you back to search incase you want to browse other search results.

Similarly, when searching for "Maui", Kayak can offer up a deep link inside of its app for flights from your origin city to Maui.

A second API allows application developers to specify any web content iOS should index via Apple web crawlers --indicating Apple will also index web content for search. This allows for iOS to display search content for apps that the user doesn't have installed. When tapping these links, iOS prompts the user to download the app first or sends them to the app's web experience via Safari.

Finally, a third API allows for any activity type to get indexed (e.g. steps inside of the health app). As Apple specifies:

> For example, the Health app indexes its sections to make them available to all users. When a user searches for "steps," Search lists an item that displays the user's current steps; tapping the result automatically opens the Steps area of the Health Dashboard. Because "steps" is marked as a publicly searchable item, users who have never tracked their steps in the Health app also receive a link to the Steps area when they search for "steps."

#### New PageRank

PageRank is the ranking algorithm that originally powered Google Search. In this new world, it's unclear how any of this newly indexed content inside of apps will be ranked, e.g. which result will show up first. Apple will have to develop a new PageRank algorithm to avoid spam, irrelevant results, and overall user frustration just as Google did. Apple gives this guideline to developers which indicates that it is indeed working on ranking:

> Be sure to avoid over-indexing your app content or adding unrelated keywords and attributes in an attempt to improve the ranking of your results. Because iOS measures the level of user engagement with search results, items that users don't find useful are quickly identified and can eventually stop showing up in results.

#### Google

While there is little doubt that Apple is slowly but surely pushing Google out of its default platform one iOS release at a time, the real question becomes: when does the Apple search experience actually become powerful enough? Apple pulled the trigger on Apple Maps way too early and it won't make that same mistake again.

Unlike Maps, Apple's strategy to lessen the dependency on Google Search seems to be three pronged: 1) building a primary search interface using app content 2) using third party data providers such as Yelp and 3) using another search engine as a fallback for the long-tail -- probably Bing. This strategy will take time but the foundational pieces are now firmly in place.

Publicly available data suggests a non-trivial percentage of search volume for Google comes from iPhones and iPads, as do a large amount of transactional searches -- crucial to Google's core business. The biggest hedge Google has ever made in its existence is Android and the battle lines are now pretty clearly drawn -- Android & Google Search vs. iOS & Apple Search (Siri).

### Change

The mobile era has already caused a sea of change. There is another major shift coming to iOS and that's how you'll search.
