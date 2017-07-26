# 6 Pillars of UI Design

_Captured: 2016-04-01 at 02:31 from [medium.com](https://medium.com/p/80fe255f5091)_

![](https://cdn-images-1.medium.com/max/1200/1*XV_I_uS_Tkrd-06saL_89Q.jpeg)

> _The 6 pillars at the front of Northern Ireland Assembly Parliament_

If there's something **_critical _for the success **of an app, website or any other software, that is the **good user interface. **If the people behind it don't put thought and effort into creating great and effective user interfaces, results range from users facing tons of errors to not using your product _at all_. Ian Sommerville, in his awesome "Software Engineering", introduces us to a few design principles that, if taken into account and applied correctly, are game-changers in UI design and therefore one step ahead to the success of your software.

> "**UI designer must take into account the physical and mental capabilities of the people who use software. […] Human capabilities are the basis for the design principles**" -- Ian Sommerville ("Software Engineering", 6th Ed.)

### 1\. User Familiarity

This is principle is sometimes overlooked by software engineers and designers in general, but it is a defining point in UI -- Usability is often related with familiarity by users, and the UI should reflect that by using terms and styles the user potentially knows or are at least familiar with.

![](https://cdn-images-1.medium.com/max/600/1*Zt5RH13YmrAfJpQMIi7A0g.png)

> _Ubuntu's Unity Graphical Interface_

For instance, if you've been Windows user for your whole live it wouldn't be too hard for you to be confused with Ubuntu Unity's left-sided window buttons or the File menu on the system's top bar instead of inside the window. Although they don't have cater only for former Windows-users, it can be a barrier for migration!

As a second example, think you're building a system for truck drivers. They aren't used to terms like _freight, shipper, receiver, terminal, routes, carrier, _etc; If you tell them there's a new _package _to be delivered and the weight of it is 10 tons, you probably put the wrong mental model on the user's head, who may have thought of a small delivery instead of a big one.

### 2\. Consistency

I can't emphasize this enough: **Lack of consistency frustrates users and raises their learning curve**. Inconsistency can be a great and powerful tool, so it is _highly _recommended that you be careful when to use it. Define a pattern and follow it, be it for text, colour code or actions flow. Some discrepancies like:

  * My Account/Your Account
  * Login and Logout/Sign in and Sign out
![](https://cdn-images-1.medium.com/max/600/1*Bx8rW7DPIpOvhcWjRzM-Hg.png)

> _Inconsistency of order frustrates users;_

  * Button Order in different pages (Cancel, Save vs Save and Cancel)
  * Different commands (Private Browsing -- CTRL+SHIFT + N in Chrome and Opera, CTRL+SHIFT + P in Firefox and I.E.)

There's no lack of examples for that, and I am sure you got the point. What the user learned in the one section of your application must be applicable to or at least similar in other sections.

### 3\. Least Surprise

Users have expectations, and the role of a UI Designer is also to not disappoint them. This principle is a very simple one, but necessary: _your UI should be designed to not surprise the users and be as obvious as possible._

> _The first style can be easily confused with plain text!_

Example:

_In the image on the left, which one is more likely to be a button?  
_ The most obvious option would be the second, a boxed and with darker background text. A user could lose minutes looking for the button instead of clicking on what looks like plain text (been there, done that!) and probably would be surprised and disappointed too.

### 4\. Recoverability

Most of the time it is better err on the safe side and it is inevitable: users will make mistakes. No, I don't mean _maybe, _I mean they _will_.   
The UI has to be able to help the user repair their faults (and even software faults!). It ranges from having edition capabilities for already stored information to things like confirmations of actions (like in the image below) or the capability to restore things to a previous state (Undo buttons, for instance).

![](https://cdn-images-1.medium.com/max/800/0*6MwnpHNCe7riGdWc.png)

> _Confirmation for a destructive action is one of the options(from the Material Design guidelines)_

### 5\. User Assistance

Creating an interface that helps and guides the user must be the biggest goal of a UI designer and is a key point on ensuring they can leverage your software to its full extent.

The UI shouldn't mislead users and must provide them with meaningful feedback -- you must induce them to the right mental model. For instance, the other day I tried to sign in to this XYZ platform, and got this as a response:

![](https://cdn-images-1.medium.com/max/800/1*_xsa_Q9dZYtRJLGBPFWyyQ.png)

> _Green message box for an error? What?_

Since I usually have _zero chills_, I was just trying to log in subsequently instead of reading the text. _That_ is what you **shouldn't **do.

![](https://cdn-images-1.medium.com/max/600/1*P-CCq00WIbOuKuwpu2vImQ.png)

> _Heinz's 404 page -- Explains the problem and gives alternatives to the user_

**_Ensuring the user is aware of what's going on _**and that there's**_ help available_** if they need is a task that goes from error messages, form tool-tips and general UI text to tutorials, wizards and even manuals -- **_not a task solely from UI Designers but a joint effort with Developers, Tech. Writers, etc._**

### 6\. User Diversity

This is a principle not applicable just to UI, but for everything in our modern world! Keep in mind humanity isn't homogeneous, neither will be your user-base. You can narrow your user base down to some category, but your users will always have some particularities that make each person different from the other.

You should try your best to cater for all the different types of users who will engage with your UI -- Gender, technical level, disabilities, etc., are some of the points you should look at while designing UIs which work for diverse audiences.

It is possible that some of the above pillars overlap with this one; Some users require way lesser levels of guidance and help than others, or several users will be familiar with different types of stuff, depending on your software. Inevitably you won't be able to 100% satisfy all the specific requirements of all the types of users, but you also can't just assume they are all the same!

### **Bottom line**

If you're tasked with designing User Interfaces and want them to satisfy your users as much as possible, be mindful of the above points. As you go deeper into researching User Experience, you will find some subdivisions and several scholars have different naming conventions for those.

If you can take only one phrase out of this article, take this TL,DR:

> Frustrated user = unhappy user. Design your UI to meet your users needs and expectations.

All the best

_If you liked this, share it with your friends and stay tuned for more posts focused on web development, UI and UX._**_[Follow me on Twitter_**](https://twitter.com/joaolucasluc)_ and here on Medium, and don't hesitate to _**_hit me up with feedback or question_**_s!_
