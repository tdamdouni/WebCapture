# Google is testing a new way of training its AI algorithms directly on your phone

_Captured: 2017-04-10 at 17:48 from [www.theverge.com](http://www.theverge.com/2017/4/10/15241492/google-ai-user-data-federated-learning)_

![](https://cdn0.vox-cdn.com/thumbor/xd1skv5i709AdwcVFtt3vPVJVg4=/0x0:2040x1360/1200x800/filters:focal\(857x517:1183x843\)/cdn0.vox-cdn.com/uploads/chorus_image/image/54165861/jbareham_160926_1228_0389.0.0.jpg)

When big tech firms use machine learning to improve their software, the process is usually a very centralized one. Companies like Google and Apple gather information about how you use their apps; collect it in one place; and then train new algorithms using this aggregated data. The end result for users could be anything from sharper photos on your phone's camera, to better a search function in your email app.

This method is effective, but the back-and-forth of updating apps and gathering feedback is time-consuming. And it's not great for user privacy, as companies have to store data on how you use your apps on their servers. So, to try and address these problems, Google is experimenting with a new method of AI training it calls [Federated Learning](https://research.googleblog.com/2017/04/federated-learning-collaborative.html).

As the name implies, Federated Learning approach is all about decentralizing the work of artificial intelligence. Instead of collecting user data in one place on Google's servers and training algorithms with it, the teaching process happens directly on each user's device. Essentially, your phone's CPU is being recruited to help train Google's AI.

Google is currently testing Federated Learning using its keyboard app, Gboard, on Android devices. When Gboard shows users suggested Google searches based on their messages, the app will remember what suggestions they took notice of and which they ignored. This information is then used to personalize the app's algorithms directly on users' phones. (To carry out this training, Google has incorporated a slimmed-down version of its machine learning software, [TensorFlow](http://www.theverge.com/2015/11/9/9696020/google-machine-learning-tensorflow-open-source), into the Gboard app itself). The changes are sent back to Google, which aggregates the, and issues an update to the app for all its users.

As Google explains in a [blog post](https://research.googleblog.com/2017/04/federated-learning-collaborative.html), this approach has a number of benefits. It's more private, as the data used to improve the app never leaves users' device; and it delivers benefits immediately, as users don't have to wait for Google to issue a new app update before they can start using their personalized algorithms. Google says the whole system has been streamlined to make sure it doesn't interfere with your phone's battery life or performance. The training process only takes place when your phone is "idle, plugged in, and on a free wireless connection."

As Google research scientists Brendan McMahan and Daniel Ramage sum up: "Federated Learning allows for smarter models, lower latency, and less power consumption, all while ensuring privacy."

This isn't the first time we've seen tech companies try to mitigate AI's thirst for user data. Last June, Apple announced its own machine learning models would be using something called "[differential privacy](http://www.theverge.com/2016/6/17/11957782/apple-differential-privacy-ios-10-wwdc-2016)" to achieve a similar aim using, essentially, statistical camouflage. Methods like this are only going to become more common in the future, as companies try to balance their need for user data, with users demands for privacy. The end result, though, should still be better AI for all.
