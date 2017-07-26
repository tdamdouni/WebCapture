# CloudKit: Introduction and let’s build an app

_Captured: 2015-10-30 at 10:59 from [szulctomasz.com](http://szulctomasz.com/cloudkit-introduction-and-lets-build-an-app/)_

Let's take a look what CloudKit gives us and how to start using it. We'll build very simple app to see how it works in action.

Storing application data, synchronization it on multiple devices, sharing public data, and keeping private data in in user's space. These goals are similar to most of apps that need to use a backend. You can write your own backend from the ground up or use [CloudKit](https://developer.apple.com/cloudkit/).

CloudKit has access to iCloud servers and it's multi-platform. I mean, it works on iOS, OSX and even on the web. Authentication is realized by using iCloud accounts, so user do not have to log in to the app or do not need to create account because he has one already.

## Containers and databases

CloudKit operates on containers ( CKContainer). Every app has its own default container when iCloud with CloudKit is enabled for the app. Name of the default container is the same as bundle identifier of the app. Apps can have other containers for other purposes that simple storing data. They can be used for data sharing between apps of the same developer. So, you can have app that keeps your photos, like album with photos, and you can have an app on your Mac computer, that can browse these photos and edits them.

Container consists of databases. Every container have one public database ( CKDatabase) and private databases. Number of private databases is equal to number of users of the app.

In public database app can store public data, public database records and publicly accessible assets.  
In private databases user's can store their data, their private records managed by the app, and so on. Only the user has access to their private database.

As a developer you cannot browse entries from private databases, but you have access to records from public databases using [CloudKit Dashboard](https://icloud.developer.apple.com/dashboard).

Speaking about assets/files. CloudKit framework is responsible for uploading them, and allowing user to download them. It uses iCloud storage. The CloudKit is just transportation layer, and do not provide local persistence for your apps.

Important note: _Containers cannot be deleted_. I am not sure why this works this way. I tried to think more on this but cannot see real reason behind that. Is it maybe for not removing private data of app's users? Anyway, before you set name of a container, think twice, you cannot undo this after app with new settings launched - containers are created when you launch the app.

Public databases can be accessed by not logged in app's users. Being not logged in give them just read-only access to public databases, so they can only browse the data. Of course when user is logged out, he cannot have access to private database.

## Data Persistence

As I mentioned above, CloudKit does not support any data persistence in an app. It only provides some data when app requests it. During development you have to think about mapping those records into your local model's objects. You can use Core Data to store what app fetches and creates or store them in an other way if Core Data is overkill for your app.

CloudKit database's records are represented by CKRecord objects. When mapping these objects to your local ones you don't need and you should not assign this CKRecord object to e.g. record property of app's model. You don't need entire record object. One of important properties is recordID property of type CKRecordID which uniquely identifies object in CloudKit databases, and recordChangeTag of type String which specifies version of a record object. So those property should be included in your local objects, so you can fetch proper record from the backend when you need to update it or remove on the backend.

Storing both record and local model object cause that you stores twice much data that you need for one object.

## Database Schema

CloudKit allows to have several types of data in containers. Here is a list of them:

Asset - separately stored file that is associated with a record in database. In app it is represented by CKAsset object that contains property specifying where file is stored on a device's disk.

Bytes - NSData with byte buffers that is stored with the record. (Notice: If your record type contains this type of property be careful with printing this to console. When you print CKRecord object to console it'll print all the attribute fields associated with it, so also will print content of this Bytes property which may be very long).

Date/Time - A point in time, represented by NSDate.

Double,Int - Numbers, represented by NSNumber.

Location - Location that is represented by CLLocation class. Contains informations about geographical coordinate and altitude.

Reference - A relationship between objects represented by CKReference class. This attribute contains information about object that is connected with and information about action while referred object is deleted. More on references below.

List - Array that consists of any of the above types.

## References

You can create references between objects, e.g. like relationship in Core Data using CKReference class. It can specify ownership of objects, and action that have to be performed when referred object is deleted. There are two types of actions to perform:

CKReferenceActionNone - which means, do nothing when referred object is deleted.  
CKReferenceActionDeleteSelf - which deletes source of a reference and other objects that deleted objects in chain are referred to. Meaning, it will cause cascade deletions.

Speaking about references, we can identify two objects: source and target. Source is object that contains property of Reference type. A target is an object whose recordID is assigned into source's property.

To be able to save information about reference, you have to ensure that target of a reference exists in the CloudKit database before you save it. If you're creating reference with target not yet saved on the backend you need to save this object and reference in the same operation so CloudKit can find this object when saving reference.

Notice that references can be created only between objects from the same container, database and record zone.

## Record Zones

Record Zone is represented by CKRecordZone class in CloudKit framework. It represents area of related records in a database. Each database have their own default zone, and you can create custom zones in private databases. With zones you can add/remove multiple records in a single transaction using [CKModifyRecordZonesOperation](https://developer.apple.com/library/ios/documentation/CloudKit/Reference/CKModifyRecordZonesOperation_class/index.html#//apple_ref/occ/cl/CKModifyRecordZonesOperation).

Of course you need to create zone and save it to database before you start adding records to them, otherwise you'll get errors. And you cannot create zones in a public database.

Using zones you can better manage objects in the app, especially in terms of caching or updating existing objects in the app. Zones have capabilities represented by [CKRecordZoneCapabilities](http://szulctomasz.com/cloudkit-introduction-and-lets-build-an-app/CKRecordZoneCapabilities) structure. One of the capabilities is FetchChanges which let you fetch only those records that changed, instead of fetching all the records in specific zone.

Another capability is Atomic that let you save your transaction atomically. It means that if there are few things to be saved/updated/deleted and one operation fails, all operation will be canceled.

## Queries

To make a query on a database you need to use CKQuery and CKQueryOperation classes.

CKQuery object contains informations about criteria for searching for records in a database - type of records, predicate to match and sort descriptors.

CKQueryOperation specifies operation of querying against a database. You need to initialize the operation object with a query, set result limit if need to limit the query's results and set two blocks. First block is recordFetchedBlock which is called every time a record is fetched from the set of records for the query, and queryCompletionBlock which is called after operation finished.

You can also set desiredKeys to fetch only specified properties of a record type. It may make requests faster, depending on what is stored in filtered records.

After the query and operation are configured, the last step is to pass operation to CKDatabase's addOperation(_:) method.

## Subscriptions

Subscription is used to track changes on the server and is represented by CKSubscription class. Subscription have an entry in the database and is something like persistent query. This query can track three events: creation, deletion and modification of records. Every subscribed event occurs, backend sends a push notification that app can observe and react appropriately.

Except saving, you can cancel or delete subscription object to stop observing specific events, e.g. when some object is deleted and do not need to be observed.

How to subscribe will be covered below.

## CloudKit for Web

With CloudKit you can create web service that will communicate with iCloud servers and will use CloudKit database like native iOS/OSX app using CloudKit JS framework. It's ported version of iOS framework with small differences (said by speaker on WWDC 2015). You should use it if you want to create web service to your existing app. Unfortunately I'll not cover it in this article.

You can of course create all the communication, uploading, downloading files, endpoints, and all other related stuff on your own without CloudKit JS framework, but this will not be a good way to go. CloudKit JS framework does anything you want, like in iOS.

In the web service, user is using Apple ID to log in, like to native app. Web service uses Apple's browser window with login form that supports reminding password, creating account functionality, etc. I think it's nice to have this since the beginning of creating web services. It just work. As a developer you do not have any access to this window and to what user typed in the form fields.

## Development vs Production

There are few differences that might be important and need to be considered when working with CloudKit in development and production environments.

In development environment you can create or update schema on the backend by creating records using CloudKit API in an app. When object is saved, the type of the record and properties are created automatically (called just-in-time schema). It is not possible to do in production. You can create types in production by deploying development schema that is tested and accepted.

In production environment, users that are not logged in can read records from the public database but cannot write anything to it. In development environment, when running app from Xcode, you need to log into iCloud account to read records from the public database.

In production environment, you can add, modify and delete records in the public database, but you cannot modify the schema like in development environment.

The app store (released) app uses always production environment and it cannot be changed. The app launched from Xcode also uses development environment, but you can switch to production by archiving the app and exporting it for testing. During archiving process you'll be asked to select proper environment for testing.

Reseting development environment may differs depending on status of the environment. If there is schema that is already deployed to production, and development schema is updated, and need to be reseted, it will be reseted to match the production schema. If there is no schema deployed for production yet, all the records and record types will be removed to empty state.

## Pricing and Quota

CloudKit is available for free with some limits. It scales up when more users use the app. There is a _40 requests per seconds_ available for you (10 per 100,000 users, up to 4,000,000 of them) and a lot of space and data transfer. I was a bit confused about this pricing stuff, because you can exceed the limits, and what's then? I googled a bit and found ([What happens if the free CloudKit limit is reached?](https://forums.developer.apple.com/thread/6430 )) that what will happen is the backend will return errors to users - specifically CKError.LimitExceeded. Also, in [What's New in CloudKit](https://developer.apple.com/videos/play/wwdc2015-704/) WWDC 2015 Session one guy answer these questions. So, when app exceeds limit, you can just buy more to make app work properly and stop returning errors.

The limits are pretty high, though, and you should not be worried about it until you hit like 4,000,000 or your users are really really active (or something is wrong with app architecture and you make too many requests).

What's important here in terms of data transfer and database requests per second, is that only downloading/uploading to public database and performing requests on public database counts. If user perform actions on private database it does not count, it is user's quota, data transfer, etc.

## Let's build an app

Let's analyze some code while creating some simple app. I'll call it Goatstagram. It will be app that is about goats, and it will present simple feed with photos of goats :)

At the beginning you need to enable iCloud + CloudKit and pushes. Remember that you need to be the Agent of the account to have ability to create containers on iCloud. After you run the app, the containers will be created automatically and you should see them in the [CloudKit Dashboard](http://icloud.developer.apple.com/dashboard/).

![Screen Shot 2015-10-26 at 23.42.17](http://szulctomasz.com/wp-content/uploads/2015/10/Screen-Shot-2015-10-26-at-23.42.17-700x340.png)

> _[Screen Shot 2015-10-26 at 23.42.17](http://szulctomasz.com/wp-content/uploads/2015/10/Screen-Shot-2015-10-26-at-23.42.17.png)_

![Screen Shot 2015-10-26 at 23.44.42](http://szulctomasz.com/wp-content/uploads/2015/10/Screen-Shot-2015-10-26-at-23.44.42-700x223.png)

> _[Screen Shot 2015-10-26 at 23.44.42](http://szulctomasz.com/wp-content/uploads/2015/10/Screen-Shot-2015-10-26-at-23.44.42.png)_

After this is done create Record Type the same as on the screenshot. We would like to store Asset that is the file and Reference to the user that posted the photo of a goat.

Next thing is to fetch status of an user's iCloud account so we are sure that we can start sending more requests to the iCloud. You can make a check on a default container using accountStatusWithCompletionHandler method.

12345678 
CKContainer.defaultContainer().accountStatusWithCompletionHandler{(status,error)inguard error==nilelse{print(error)completion(available:false)return}completion(available:true)}

Based on what the method returns, you can decide to enable or disable UI, like buttons or other stuff that uses CloudKit functionality. You don't want to let user doing anything related to CloudKit if he has no account. Especially call the method before accessing private database if you didn't check it before.

FWIW, documentation differs between this available under Option key when clicking on this method in the code and between this available online. In online documentation there is mentioned that you should observe NSUbiquityIdentityDidChangeNotification notification to be notified about changes in account availability.

Okay, after we've got confirmation that account is available (test it on actual device) we can fetch user's RecordID which is needed for posting photos. Store the ID somewhere for future use.

12345678 
CKContainer.defaultContainer().fetchUserRecordIDWithCompletionHandler{(fetchedRecordID,error)inguard error==nilelse{print(error)completion(nil)return}completion(fetchedRecordID)}

After this is done we can fetch few photos from the backend. You can upload them to the backend by creating records in database manually in Default Zone section.

12345678910111213141516171819202122232425262728 
varphotos=[Photo]()letquery=CKQuery(recordType:"Photos",predicate:NSPredicate(value:true))query.sortDescriptors=[NSSortDescriptor(key:"creationDate",ascending:false)]letqueryOperation=CKQueryOperation(query:query)queryOperation.resultsLimit=number;queryOperation.queryCompletionBlock={(cursor,error)iniferror!=nil{print(error)}dispatch_async(dispatch_get_main_queue(),{completion(photos:photos,success:error==nil)})}queryOperation.recordFetchedBlock={record inletphoto=Photo(record:record)photos.append(photo)dispatch_async(dispatch_get_main_queue(),{perPhotoCompletion(photo)})}CKContainer.defaultContainer().publicCloudDatabase.addOperation(queryOperation)

This method is interesting. It takes two blocks. First is called when everything is downloaded and the second one is called every single record is fetched from the backend. You can do some housekeeping work in this moment. The way how the querying work is described about in Querying section above.

After this is done, the last thing is to subscribe for changes in the feed, so we can react and re-fetch those new photos. This part is tricker. First, we need to check if there is any subscription already saved for us, and if there is none, we'll save one.

12345678910111213141516171819202122232425262728 
/// truncated for readability/// ...CKContainer.defaultContainer().publicCloudDatabase.fetchAllSubscriptionsWithCompletionHandler{(subscriptions,error)->Voidinguard error==nilelse{print(error)completion(subscriptionID:nil)return}/// Check if subscription existsforsubscriptioninsubscriptions!{ifsubscription.recordType=="Photos"&&subscription.subscriptionOptions==[.FiresOnRecordCreation]{completion(subscriptionID:subscription.subscriptionID)return}}/// Create new subscriptionletsubscription=CKSubscription(recordType:"Photos",predicate:NSPredicate(value:true),options:[.FiresOnRecordCreation])CKContainer.defaultContainer().publicCloudDatabase.saveSubscription(subscription){(savedSubscription,error)->Voidiniferror!=nil{print(error)}completion(subscriptionID:savedSubscription?.subscriptionID)}}

To make it work, app needs to be registered for push notifications, as usual, and notification should be handled in application(_:didReceiveRemoteNotification:) and passed along to object that will handle it, e.g. using NSNotificationCenter or other mechanism that you want to use.

Now, when this is coded well, you should be able to get some photos from your backend, and if you add new one, it'll be updated. Remember to fetch last image after you get notification about the change. You can fetch RecordID of newly added photo from received push notification.

Okay, the last thing is to upload a photo with a goat on the backend. To post the photo, you need to have URL to it to create CKAsset object. Then, you need to use the user's RecordID that we fetched earlier and create CKRecord of a Photos record type and set it.

12345678910111213141516 
letassetURL=/// url of an assetletphotoRecord=CKRecord(recordType:"Photos")photoRecord["asset"]=CKAsset(fileURL:assetURL)photoRecord["user"]=CKReference(recordID:userRecordID,action:CKReferenceAction.None)letdatabase=CKContainer.defaultContainer().publicCloudDatabasedatabase.saveRecord(photoRecord){(savedRecord,error)->Voidinguard error==nilelse{print(error)completion(savedRecord:nil)return}print(savedRecord)completion(savedRecord:savedRecord)}

And that's all :)

## A problem with calling CloudKit async methods

I noticed the problem when coding the CloudKit related code. I was calling method for obtaining user's account status and in the same time I was asking for all the saved subscriptions - I know this might not be a great idea, but when I did it, the CloudKit API gave me different results for the same calls every time I reseted the app. Sometimes it gave me info that iCloud account is not available, and sometimes that I am not authenticated to do some calls. I created a thread on Apple Developer Forum, because I don't know if this is something that Apple should be aware of, or they just assumed that nobody is doing this - [Doing few requests in the same time gives different results](https://forums.developer.apple.com/message/80647#80647).

My solution was to create operations that were depending on others so I created something like chain of operations that I passed to operation queue - you can see this in the repo. Not ideal solution, but works for now.

## Repository

App is available on the github here [tomkowz/cloudkit-demo-goatstagram](https://github.com/tomkowz/cloudkit-demo-goatstagram), so you can run it and check how it work. I believe that you need to make changes in bundle identifier and identifier of default container to match your Apple Developer Program account.

And here is a feed with photos of goats :)

![Photo 27-10-15 12 10 38 AM](http://szulctomasz.com/wp-content/uploads/2015/10/Photo-27-10-15-12-10-38-AM1.png)

> _[Photo 27-10-15 12 10 38 AM](http://szulctomasz.com/wp-content/uploads/2015/10/Photo-27-10-15-12-10-38-AM1.png)_

## Conclusion

CloudKit is nice addition to our toolbox, and causes that we may stop worrying about the backend side, if not for production solution, then at least for prototyping and testing ideas. It gives us ability to tracking changes, synchronizing assets and syncing data with a small effort.

It is also nice replacement for solutions like [Parse.com](http://parse.com), if you don't need cross-platform feature and if you want to stick just with iOS/OSX or web.

I think it has potential, I like how easy is to create some record types, add something to database, etc. I also like the API - it's clean and easy to remember and use, though, I found some issues that are bothering me.

I am wondering which apps already use CloudKit, so I could check and play with them for a while. Do you know any? Let me know in comments. I am wondering, in which specific projects I would like to use it, and would be nice to have a chance to play with it in some commercial project.

Though the post is a bit longer than usually, not all the CloudKit things were presented here, and I would like to elaborate more on specific topics. And will do in the near future. So, if you want to read more about CloudKit, stay tuned.

## Additional resources to follow

Here is a list of additional resources that may be useful. Especially take a look on WWDC sessions that are very interesting and nicely present how all this stuff works.
