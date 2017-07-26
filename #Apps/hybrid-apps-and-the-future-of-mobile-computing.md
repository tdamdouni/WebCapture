# Hybrid Apps and the Future of Mobile Computing

_Captured: 2017-04-16 at 10:28 from [dzone.com](https://dzone.com/articles/hybrid-apps-and-the-future-of-mobile-computing?edition=290923&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-15)_

Discover [how to focus on operators for Reactive Programming](https://dzone.com/go?i=190139&u=https%3A%2F%2Fblog.wakanda.io%2Freactive-programming-operators%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how they are essential to react to data in your application. Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190139&u=https%3A%2F%2Fwww.wakanda.io%2F).

The jury is out on which type of mobile app is the future of mobile computing. The stats point to native being the dominant app type in use. Most of the top 100 apps in the app stores are native, and [comScore](http://www.comscore.com/Insights/Blog/Smartphone-Apps-Are-Now-50-of-All-US-Digital-Media-Time-Spent) reports that 50% of all time spent digitally is spent on mobile apps (though it doesn't give a split between native and hybrid), and just 7% is spent on mobile web apps.

![Digital Time Spent in July 2016](https://az184419.vo.msecnd.net/sauce-labs/blog-images/digital-time-spent-0716.png)

Source: comScore

While native apps are great for engagement, mobile websites still draw a majority of traffic. [Applause](https://arc.applause.com/2016/09/13/native-apps-versus-mobile-web-decision/) accurately says, "The Web Gets Eyeballs, Apps Keep Them."

![Top 1k Mobile Apps v Top 1k Mobile Web Properties](https://az184419.vo.msecnd.net/sauce-labs/blog-images/top-1000.png)

Source: comScore

Clearly, relying on native mobile apps is not enough. For this reason, [Bloomberg](https://www.emarketer.com/Article/Forget-Mobile-Web-vs-AppsWhy-Bloomberg-Needs-Both-Growth/1015082) and many large mobile app publishers use both web and native mobile apps, not wanting to miss out on either. However, this is far from efficient. What we need is to build and ship mobile apps much like web apps--Deploy once, and it works across all platforms. Fortunately, there are exciting developments on this front.

There are two strong currents in mobile app development bound to intersect in the near future. On one side, there are many app development frameworks that help you build hybrid apps with native-like functionality. These include frameworks like [React native](http://www.reactnative.com/), [Cordova](https://cordova.apache.org/), [NativeScript](https://www.nativescript.org/), and [Ionic](https://ionicframework.com/). They promise the best of both worlds- use HTML, JavaScript and CSS to build mobile apps, and let those apps access native device functionality.

On the other side, the two major mobile platforms, iOS and Android, are taking steps to make mobile web apps function like native apps, allowing web apps to place their icons on the homescreen or app drawer, send notifications, and even leverage device functionality. Google's [Progressive Web Apps](https://developers.google.com/web/progressive-web-apps/) are the most recent development in this regard, and there are already numerous examples of apps that have gone progressive.

As these two trends converge in the future, they will lead to a shift from native mobile apps to hybrid apps. There are a couple of reasons why hybrid apps are set to trump native apps in the near future:

## **App Store Limitations**

Today, releasing a native mobile app involves packaging the code, submitting it to the app store, and waiting for it to be approved. The entire process can take anywhere from two to seven days. This is an eternity in the mobile world. Mobile app developers (especially those that already practice DevOps for their web apps) want to be able to update their mobile apps like their web apps, multiple times a day if necessary. This is not possible with the limitations of app stores, and hybrid apps are the way out.

## **Code Reuse**

As most apps have an iOS and an Android version, they are developed using each platform's preferred programming language- Objective-C or Swift for iOS, and Java for Android. Hybrid apps, on the other hand, let you build mobile apps with the same languages your developers are already familiar with- HTML, JavaScript, and CSS. You can write code once, and deploy it across all your mobile platforms. Mobile app testing equally benefits because you don't need to write unique test scripts for each app type. Testing against a single codebase also reduces the testing infrastructure you need and simplifies the QA process. With the increasing fragmentation in device types and OS versions, this is becoming a necessity for mobile development.

## **The Rising Talent Gap**

[Code.org](https://code.org/files/Code.orgOverview.pdf) estimates there will be 1.4 million computing jobs available by 2020, and only 400,000 computer science students. This is also true for mobile development. Truly great iOS and Android developers are a rare find. It's a better strategy to make the best use of the existing talent you have than to leave your mobile development at the mercy of scarcely available new talent.

## **Faster Time to Market**

The popularity of mobile apps rises and falls faster than their web counterparts. Ratings, reviews, installs, daily active users and churn rate all add up to decide the fate of a mobile app. In this fast-paced world, hybrid moves you faster from idea to app than native.

## **DevOps for Mobile**

Finally, hybrid apps let you extend DevOps to your mobile apps, too. They let you go from mammoth quarterly app updates to a bi-weekly cycle, and eventually let you update as frequently as your web app- which is close to impossible with native apps today. To update at this frequency, you'll need to automate the two key parts of your continuous integration (CI) process: builds and tests. This is where tools like Git, Jenkins, and Appium have a key role to play. When well-integrated, they can let you focus exclusively on developing and testing your app, rather than worrying about mobile platforms' norms. This gives you the confidence to release multiple times a day, and take ownership of your mobile development process.

This post will sound too one-sided if I ignore the fact that as of today, native apps deliver a much better and faster UI than hybrid apps. This is the single biggest reason they're so popular with developers and users alike. However, hybrid apps are fast approaching native-like functionality. All of the reasons above add up to show why native apps, though the de facto choice for many today, can't hold that position for too long.

The mobile ecosystem changes faster than we'd like to believe. And it won't be long before we look back at how primitive our mobile app development was in the era of app stores and their policing of native apps. Hybrid apps are the future of mobile computing.

[Learn how divergent branches can appear in your repository](https://dzone.com/go?i=190140&u=https%3A%2F%2Fblog.wakanda.io%2Fanimated-git-4-understand-divergent-branches-appear-fetching-remote-repository%2F%3Futm_source%3Ddzone%26utm_campaign%3Dblog-article%26utm_medium%3Dreferral) and how to better understand why they are called "branches". Brought to you in partnership with [Wakanda](https://dzone.com/go?i=190140&u=https%3A%2F%2Fwww.wakanda.io%2F).
