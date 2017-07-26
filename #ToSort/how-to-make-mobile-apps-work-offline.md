# How to Make Mobile Apps Work Offline

_Captured: 2017-06-18 at 21:37 from [dzone.com](https://dzone.com/articles/how-to-make-mobile-app-work-offline?edition=305103&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-06-17)_

[Launching an app doesn't need to be daunting.](https://dzone.com/go?i=204132&u=http%3A%2F%2Finfo.perfectomobile.com%2Febook-mobile-app-testing-best-practices.html%3Futm_source%3Dbgm-dzonespon) Whether you're just getting started or need a refresher on mobile app testing best practices, [this guide is your resource!](https://dzone.com/go?i=204132&u=http%3A%2F%2Finfo.perfectomobile.com%2Febook-mobile-app-testing-best-practices.html%3Futm_source%3Dbgm-dzonespon) Brought to you in partnership with [Perfecto](https://dzone.com/go?i=204132&u=http%3A%2F%2Finfo.perfectomobile.com%2Febook-mobile-app-testing-best-practices.html%3Futm_source%3Dbgm-dzonespon).

_This article was originally published [here](https://www.romexsoft.com/blog/make-app-work-offline/)._

To understand how to build a mobile app with an offline mode which is resilient to different network scenarios, it is useful to know the key technologies that allow you to make an app work offline. Mobile apps can be built with two core capabilities:

  * Local storage/ database.

  * Data synchronization.

Let's take a closer look at all the possible challenges that you can deal with during offline mobile app development and explain each capability in more depth.

## Offline Data Storage and Access

While making your app work offline, you will often need to store data directly on the client's device. This allows your application to work effectively even when there is no connection. There are several different methods or levels of offline data storage that make an app run offline. It can be different for different mobile platforms (iOS, Android, Windows phone, and others) and we'll go through each of them.

### Local Caching and Cookies

When you use web technologies for building a mobile app it is possible to use browser application caching or cookies. Normally, when you visit a certain URL, your browser makes a request to a server to return the appropriate page, but when the server is offline, the browser can fail to show you the requested page. Here, you will need a cache manifest which is just a simple list of essential files. Setting up an app cache manifest tells the browser how it can use pages that have been already downloaded rather than just immediately display an error when there is no longer a network connection.

**Cache Manifest:**
    
    
    jquery-3.2.1.min.js

It should be served with a text/cache-manifest MIME-type and linked to HTML pages with the following tag:

When a browser loads the file, it will ask whether you permit data to be cached on your device. Such an approach allows web-based mobile apps to work even if the user loses their Internet connection. For example, peers will be able to read the news or email messages even if they don't find a WI-FI hotspot.

Another approach that could be used to retain local web based app data (even when the browser is shut down) is browser cookies. This is the most basic approach and is very limited due to the condition that cookies tend to store around 4KB of data. One of the disadvantages of this method is that cookies are re-sent to the server with each HTTP request, which results in a waste of a lot of bandwidth to re-send the all offline data even if you don't need it. What you need to remember is that cookies are vulnerable to being deleted if a user simply decides to clear them, so this approach is recommended for the simplest storage requirements only.

## Shared Preferences

To develop an offline app for Android and iOS, you will need a certain mechanism that allows the storing of users' preferences, which are pieces of information that you save persistently and use to configure your app. Often, mobile apps expose preferences to users so they can customize the appearance and behavior of the app.

### Android Platform

Android platform provides [SharedPreferences](https://developer.android.com/reference/android/content/SharedPreferences.html), APIs that can be used to save a relatively small collection of primitive data in key-values pairs. In simple words, a SharedPreferences object is a reference to the file that contains key-value pairs and APIs provide simple methods to read and write preferences. In this case, you have a key that can only be the string type, and the appropriate value for that key. In turn, the value can be one of the following types: boolean, float, int, long, or string. Each of the SharedPreferences files is managed by the Android platform and is internally stored as an .xml file in a private directory. An app can have multiple SharedPreferences files and, ideally, they are used to store app preferences. The mentioned APIs provide two Context methods that can be used to get a SharedPreferences object. The first of those two is used when an app has a single preferences file, and the second one when your app has multiple preferences files, or if you want to give a custom name for the SharedPreferences instance. Below is an example of how to work with SharedPreferences on Android:

In order to add/edit a value, use the Editor's `putXXX()` method, where XXX is one of the appropriate type's name. You can also remove a key-value preference pair by calling the `remove()` method. Finally, the Editor's `commit()` method should be called after putting or removing values, otherwise, your changes will not be persisted. Here is an example of how to manage SharedPreferences on Android:

### iOS Platform

While developing an offline mode for an iOS app, you can use the NSUserDefaults class in order to save and update user's preferences. The NSUserDefaults class provides a programmatic interface that permits an app to customize its behavior to match a user's preferences. For example, you can give an opportunity for users to save a profile image offline or add a feature that saves documents automatically. These preferences are recorded by the app in what is known as the iOS "defaults system." In this way, information is cached, which helps avoid the opening of the user's defaults database each time you need a default value. And as the iOS defaults system is available within all of the code in your mobile app, any saved to the defaults system data will persist through app sessions. What this means for the user is that after he closes the app or reboots his phone he is still able to use the saved data next time he opens an app.

### Local (Internal/External) Storage

There are lots of cases where you might want to store data but the SharedPreferences method is too limiting for your needs, such as storing images, serialized objects, .xml, JSON, or other files. Then, an Internal/External Data Storage method is a good way to go. It is used specifically for those situations when you need to store data to the device filesystem that doesn't require relational database capabilities. The next worthy point is that it allows very fast storage of data and is easy to use. Additionally, all of the data that was stored using the Internal Storage method is thoroughly private to your app, and after your app is uninstalled, the data is deleted from the device.

### SQLite Database

Finally, the majority of mobile platforms, such as Android, iOS, and Windows Phone, provide support for apps to use [SQLite databases](https://www.sqlite.org/) for data storage, although database managing is specific for each platform. Here's why it is such a big deal. SQLite is an open source database system which works great on mobile devices as its storage offers an app the speed and power of a full featured relational database. To make the managing side simple SQLite uses a single file to store all the data. Of course, it won't solve too much on the sync and conflict resolution site, but it is an easy and simple to use alternative for queuing or caching information. So if you are going to store data that needs to be queried, SQLite storage is an option to consider. Here is a simple list of code that shows how to create a single table in Android platform:
    
    
            sqLiteDatabase.execSQL("CREATE TABLE " + PERSON_TABLE_NAME + " (" +
    
    
        public void onUpgrade(SQLiteDatabase sqLiteDatabase, int i, int i1) {

If you use SQLite storage in the process of mobile app development and data privacy is a vital need, the development of its environment requires a specific approach. One of the acceptable ways to do this will be encryption using [SQLCipher](https://www.zetetic.net/sqlcipher). SQLCipher is an extension to SQLite that provides transparent 256-bit AES encryption of database files. It makes the development of a secure mobile app easier and, as a result, it helps protect the data of end users better. The main benefits of SQLCipher are that it is a very robust system for encrypting SQLite databases and it has versions for the mobile platforms listed above. Also, it is available in different editions depending on the level of security and support you need, and provides both community (free) and commercial editions.

## Synchronization

One of the core features of an offline app is that users are able to perform some actions in offline mode and then synchronize it with a central repository. In many cases, your app may have both client side storage and server side storage, and the app will manage the flow of data between server and client. Usually, by implementing the offline mode feature, you encounter cases when your customers are able to edit information on the server-side and, at the same time, on the mobile side. This is the most complete and powerful of the scenarios. Note that while it might be tempting to build offline apps that support the two-way sync, it is by far the most complicated approach of all. With this approach, your synchronization logic should ensure that after successful synchronization, data will be up-to-date on the mobile and server side at the same time.

This can be achieved by adding certain "audit" fields to each object that should be synchronized between mobile and server, and vice versa. These fields can be like these: 'last_updated_on', 'created_on', and if the data isn't physically removed: 'deleted_on'. Be aware of physical removes since the rows deleted from the server DB have to be removed in the mobile DB also. If data should be physically removed from the server DB, your architecture should provide an approach to keep information about data that was removed. As a variant, it can be a 'deleted_record' table with a following fields 'table_name', 'deleted_on', 'server_record_id'. Based on my experience, I would recommend having a timestamp 'last_updated_on' column in every table that should be synchronized, and every time user inserts or updates the record your logic should update the appropriate 'last_updated_on' column. Then, when mobile client request server for a synchronization, your logic will iterate all over the tables checking if the timestamp in 'last_updated_on' is newer than the date of the last synchronization. If it is newer, the logic will put it into the collection and send a response to the client. In the case that the records are deleted physically, you will have to read all the new rows of the 'deleted_record' table and execute an extraction in the mobile DB. In the case that data is edited on both sides, you can not use the DB's ID as an identifier of the objects because there can be the same IDs for the newly created objects in the different mobile devices. To ensure the unicity on the different devices, you should use some unique identifier. In our implementation, we call this field 'synchronization_key' and, usually, it contains a [UUID](https://en.wikipedia.org/wiki/Universally_unique_identifier) value.

Let's summarize all that has been said in this tutorial. We live in high-tech times where mobile users expect not just good, but excellent levels of performance and user experience in their mobile applications. Today, offline support is a part of these expectations and can no longer be ignored. By implementing support of the majority of offline scenarios, you will dramatically improve the mobile app user's experience and boost your team's productivity.

[Keep up with the latest DevTest Jargon](https://dzone.com/go?i=204133&u=http%3A%2F%2Finfo.perfectomobile.com%2Fmobile-devtest-dictionary.html%3Futm_source%3Dmmg-dzonespon) with the latest Mobile DevTest Dictionary. Brought to you in partnership with [Perfecto](https://dzone.com/go?i=204133&u=http%3A%2F%2Finfo.perfectomobile.com%2Fmobile-devtest-dictionary.html%3Futm_source%3Dmmg-dzonespon).

Topics:

mobile ,mobile app development ,data syncing ,caching ,android ,ios ,sqlite
