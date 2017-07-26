# UX: iOS Onboarding without Signup Screens

_Captured: 2015-12-01 at 20:50 from [medium.com](https://medium.com/welcome-aboard/ios-onboarding-without-signup-screens-cb7a76d01d6e#.auky062vb)_

![](https://cdn-images-1.medium.com/freeze/max/30/1*Lj71nARd6cD9LIO12TvAzQ.jpeg?q=20)![](https://cdn-images-1.medium.com/max/2000/1*Lj71nARd6cD9LIO12TvAzQ.jpeg)

… or how to use the user's built-in iCloud account for** secure, invisible authentication**, including code example in **Swift 2 **at the bottom.

Nothing drives more first-time users away from an app than the need to fill a signup form during onboarding. Typing on a smartphone is a pain, especially entering an email address and two times a long password and very often the result is just the receiving of annoying newsletters.

Since the rise of app analytics onboarding steps are heavily measured and many app developers see that **more than 50% new users immediately abandon** a freshly downloaded app if they are confronted with a signup screen.

> App signup screens are **conversion killers**!

I am personally so fed up with these forms that at 99% whenever I need to fill such a form in a new app I right away close and delete it.

#### The Solution: iCloud

At least on iOS a wonderful, built-in authentication solution called iCloud is existing to overcome the need for a signup screen. On iOS, every user has an iCloud account because you need it to download even free apps from the App Store and you can get one even without a credit card.

> Every iOS user has an iCloud account.

Further below I explain the details but at first some background information about iCloud.

Over the past years Apple strongly extended its cloud offering and today iCloud stands as umbrella word for a whole ecosystem of services.

At first **iCloud** started as internal cloud storage system just used by Apple's own apps, then it was released to app developers and extended to hold documents and key-value pairs (perfect for syncing of settings across devices) and since 2014 developers can even use the underlying technology called **CloudKit** to store files and data in Apple's iCloud ecosystem.

#### iCloud as Invisible Signup Screen

So why does that matter to user experience, onboarding, my users and me?

**The "magic" of iCloud authentication lays in its invisibility to the user.**

With iCloud an app does not need to ask the user for an email address or a password to be able to uniquely identify who is running the app (and to later spam the user in marketing campaigns).

With the built-in, invisible iCloud authentication every app (developer) **automatically** can** get a secure, globally unique representation **of the currently logged-in iCloud user from iOS itself which it then can use to replace email and password as identifiers.

> An app should not ask for a user's email address. Never ever.

And the best: that solution respects a user's privacy much, much more because **Apple does NOT expose the iPhone user's details** like his email address, password or credit card details to the app developer.

#### A User's iCloud ID Token

Whenever an app wants to know the iCloud ID of the current iPhone, iPad or Mac OS X user then it needs to "ask" internally, hidden to the user, the operating system for it. If the user is logged into iCloud, which he mostly is, the app will receive a unique 33 character string representing the iCloud user.

> **Hi, my name is "_cd2f38d1db30d2fe80df12c89f463a9e"**

That iCloud ID token …

  1. is globally unique, every user has it's own token similar to an email
  2. it is the same on every device of a user
  3. it does not unveil any user details like his email address
  4. **is different for every app**

Wait? What does the last point mean?

It means that Apple generates these iCloud tokens not just based on the user but also relating the app it asks for it. So even if an app would publish all its tokens on the internet another app could not use that token to see if both apps do share users!

#### Summary

Dear iOS app developers, product managers and founders. Please **DO NOT ASK the user for his email address** and password. Use the invisibly fetched iCloud ID token of a user instead. It is more secure to the user, it does not offend the user during onboarding, it is better for your conversions and it just works out of the box. Your marketing guys won't like it because they can not send newsletters but today push notifications are anyway the better tool for customer re-activation.

Oh, and if you later plan a web service or an Android app then you can easily combine the token on your server with an email address which you ask the user for on the other devices to authenticate the user across multiple systems.

But again, please, at least on iOS: do not ask for a user's email address!

#### The Technical Solution in Swift 2

You are still with me and you like Swift? Great, let's do some coding.

But at first, please activate CloudKit in your Xcode project if not already done. You actually do not need to use CloudKit as storage in your app but it still needs to be activated as shown here:

To make a long story short here, my solution is an async function that I always use to get a user's CKRecordID. A CKRecordID is an optional object which contains CloudKit (=iCloud!) data of a user.** The only important property of the object is CKRecordID.recordName** because that is the iCloud ID token as String. Please mind that you need to import CloudKit, too.

import CloudKit

/// async gets iCloud record ID object of logged-in iCloud user

func iCloudUserIDAsync(complete: (instance: CKRecordID?, error: NSError?) -> ()) {

let container = CKContainer.defaultContainer()

container.fetchUserRecordIDWithCompletionHandler() {

recordID, error in

if error != nil {

print(error!.localizedDescription)

complete(instance: nil, error: error)

} else {

print("fetched ID \\(recordID?.recordName)")

complete(instance: recordID, error: nil)

}

}

}

And that is how you call the function to get the iCloud ID token:

import CloudKit

iCloudUserIDAsync() {

recordID, error in

if let userID = recordID?.recordName {

print("received iCloudID \\(userID)")

} else {

print("Fetched iCloudID was nil")

}

}

Of course, you should check if there were errors and store the token appropriately in Keychain to avoid constantly pinging iCloud for the ID.
