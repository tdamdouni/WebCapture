# Redesigning Evernote for iOS

_Captured: 2017-03-02 at 22:12 from [medium.com](https://medium.com/evernote-design/redesigning-evernote-for-ios-2c72d8dce419#.95oee065m)_

# Redesigning Evernote for iOS

## What I learned redesigning the Evernote mobile experience, twice!

![](https://cdn-images-1.medium.com/max/2000/1*QnPmkRy_ptEK15-i80aS_Q.png)

Redesigns are intense. As the ship date creeps closer and closer, the team is overcome with a whirlwind of emotion. After months of pouring our blood, sweat, and tears into the product, we ask ourselves, "Is it ready?" _Is it ever really ready?_ How will our users react -- love, hate, a mix of both? And how do we feel? Fear. Panic. But also, optimism. Euphoria, even.

_We've reached the finish line._

It's been just over a month since we publicly unveiled Evernote 8.0 to the world. In the wake of our recent launch, I've been reflecting on when we last shipped a major redesign, back in 2013.

![](https://cdn-images-1.medium.com/max/2000/1*zK7acKlBffkM5iq7L4HYeg.png)

> _The evolution of Evernote's iOS app_

### **Going back in time**

When Apple introduced the controversial flat design aesthetic of iOS 7 in June of 2013, it sparked a design movement in mobile apps. Skeumorphism was dead: no more over-pronounced drop shadows, textures, or patterns. This was a radical change, and no one wanted to be left behind.

As I watched Apple's announcement from a conference room at Evernote HQ, I wondered, what will this mean for us? It quickly became clear that, if we wanted to stay relevant, we were heading down the redesign path. The challenge was that our team's goal was to be in the App Store on day one of the iOS 7 launch, a mere three months away.

Tackling a redesign of this magnitude in three months didn't exactly set us up for success, but we achieved the impossible, and pulled it off.

What we weren't prepared for was the reaction from the general public. Don't get me wrong, we received plenty of love from users, the press, and even a spotlight in Apple's Keynote. But the unhappy bunch? They certainly made themselves heard. They told us that the app had become cluttered, the UI was unintuitive, features were missing, and my personal favorite -- we were overusing a "hideous" green color.

We get it. Change isn't easy. Being forced to deal with change that affects your daily productivity is worse.

The tight timeline meant that we couldn't do proper user testing or get a read from our Beta community -- which probably would have impacted what we shipped.

![](https://cdn-images-1.medium.com/max/1600/1*qtlZ4KnoyniS3nKDXzRQgA.png)

> _Evernote version 7.8_

Redesigns are sometimes necessary, and it was critical to me, my colleagues, and frankly all of Evernote, that we learned from, and didn't repeat, past mistakes.

### **Let's do it better this time**

A few years later, in 2015, a few designers and I started to take a closer look at Evernote's navigation to identify areas of confusion and opportunities for improvement.

It quickly became obvious that our navigation issues weren't trivial and couldn't be addressed by simply moving a few parts around. Underlying problems surfaced. User growth and engagement were stagnant. Other productivity apps were leapfrogging ahead of us, scooping up our aggravated users in the process.

We became acutely aware of how inefficient and cumbersome our app had become. Creating notes and navigating between them took longer than it should. We all use Evernote constantly in our core workflows, and even we were starting to turn to other apps for quick notes. It's humbling to admit, but it was time.

> We became acutely aware of how inefficient and cumbersome our app had become.

**So, we set out with a key goal in mind: improve efficiency.** As a team, we decided to take our time, explore possibilities, and get feedback along the way. We couldn't afford to rush and get this wrong.

At this point, I was one of the only team members who'd been a part of the previous redesign, so I was in a unique position to apply what we'd learned, and I was tasked with leading the charge. There was a lot riding on this, and I was determined to try like hell to get it right.

#### **Getting started**

First, we needed to determine where to focus our efforts.

We scoured our forums to see where users were being the most vocal; what were the most common requests and complaints? We ran user studies to learn how new users experience the app, what features were most appealing, and what was confusing. We polled our coworkers to find what was most important to them, and what they wanted to see improved.

We synthesized our findings, and weren't surprised to see many concerns consistently repeated.

### **Navigating the tough design decisions**

There are easily a million decisions to be made during the course of a redesign, many small and easy, some gut-wrenchingly difficult. Here's a peek into a few of the tricky challenges we had to work through.

#### **Creating notes at the speed of thought**

With speed and efficiency as our primary objectives, one thing we wanted to pay close attention to was "time to note," a phrase coined by our CEO, [Chris O'Neill](https://twitter.com/croneill). Users should be able to open the app and jump right into a new note, with as little friction as possible.

Evernote version 7.0 immediately presented 5 options for creating new notes: text, photo, reminder, list, or audio. The problem was that users had to choose every time.

We asked ourselves: _Do users like having so many options up front? _Or, are we slowing them down by making them choose right away? In this case, taking a look at data helped us form a point of view.

Turns out, people chose to create a text note the majority of the time.

![](https://cdn-images-1.medium.com/max/1600/1*l5CW1SSnF0qBQ6zz1e-32Q@2x.png)

> _Note creation options in Evernote version 7.8_

In version 8.0, we introduced the big green new note button on the bottom tab bar, nicely situated in that sweet spot above your thumb. Now, the question was, _what exactly should happen when you press it?_

![](https://cdn-images-1.medium.com/max/1600/1*LUg_JDXzy2NdR7lSuclJ5A@2x.png)

> _The prominent + button provides quick access to create new notes_

With one button, there were a few options. The easiest, and perhaps most obvious, was to mimic what we do on Android: tap the plus button and several options fly out. A few of our designers pointed to other iOS apps, like Dropbox, who did something similar. But was that actually any better than seeing multiple buttons at the same time?

Instead, I proposed tapping the plus button would simply (and quickly!) launch a new note. You can capture your idea first and foremost, and then add a photo or other content afterwards.

Then, to optimize for other note creation workflows -- taking a photo or scanning a document, creating a reminder, or recording audio -- we introduced a long press gesture for quick access. So, tap to create a note, or long press and slide to select another option.

![](https://cdn-images-1.medium.com/max/1600/1*zF9rAt5TDGv88SccUn5mHw.png)

> _Long press on the + button to reveal more options_

Was this solution the right call? It's too soon to tell. Hiding things behind a gesture is definitely risky. Some people will never discover the long press functionality, even though we try to teach them up front. I'm just hoping that for the sake of simplicity and efficiency, it was the right place to start.

#### Finding a new home for notebooks

Since the very first version of Evernote for iPhone, notebooks have been a top-level navigation item, a first-class citizen. There was a section for all of your notes, and one for your notebooks.

When we began the redesign, I questioned the validity and necessity of this sacred rule. Since notebooks are essentially folders, users constantly had to drill in and out to move between notebooks. There wasn't an easy way to quickly switch, like in our desktop apps, so it was a pain to try to multitask. Some users never really understood why we separated 'All Notes' and Notebooks in the first place.

In some of our early design explorations, we looked at an option where we maintained the separation between 'All Notes' and Notebooks, but user testing proved it didn't really solve any core problems. We tried leading with a 'Recents' section, which just confused folks. We even looked at the dreaded hamburger menu, but just couldn't stomach it.

![](https://cdn-images-1.medium.com/max/2000/1*eEwQsT9cytlHtscgidCecw.png)

> _Some early explorations for notes and notebooks navigation_

I wanted to try something radically different. What if notebooks were simply a way to filter your complete list of notes?

I'd seen a pattern in the iBooks app where tapping the title "All Books" at the top would bring up a menu of other collections (audio books, pdfs, etc). We could use a similar interaction model to switch between notebooks.

![](https://cdn-images-1.medium.com/max/1600/1*keRyv1O-V0GkX2RURsXMwA.png)

> _Tap the title in the navigation bar to reveal your list of notebooks_

This was a pretty huge change. I was asking people to do something out of the ordinary, and I wasn't following common iOS patterns. I did get some push back from a few product designers, and rightfully so. I'm thankful I have a team who isn't afraid to challenge my decisions.

User testing was the obvious next step. We hosted research studies with both existing users and others who weren't familiar with Evernote. It was a new paradigm, but could they learn?

![](https://cdn-images-1.medium.com/max/2000/1*dRo-zKNv5V0vdawzO_M42g.png)

> _The new way to navigate between notebooks_

Testing went surprisingly well. I was pleased (and relieved) to find that though people didn't necessarily know what would happen if they tapped on "All Notes", most saw the arrow and figured it was tappable. This gave us the boost of confidence we needed to move forward.

### **How did we do?**

[Evernote 8.0](https://itunes.apple.com/us/app/evernote-stay-organized/id281796108?mt=8) has been in the hands of our users for over a month now, and to be honest, the jury is still out. We've heard the full gamut of feedback, from enthusiastic and hopeful, to pissed off and disappointed, but that's to be expected.

The press has been overwhelmingly positive, and we were even given a [thorough spotlight from Wired](https://www.wired.com/2017/01/evernotes-new-app-update-reboot/).

> "It's the fastest, cleanest app the company has ever released." -Wired

We've also gotten a lot of love from our users. Some have raved that this is the best version of Evernote yet, that it's cleaner, simpler, and that we've put the most important things front and center. Some of our most active and passionate users (who are often our toughest critics!) have said they're actually [using the app significantly more](https://michaelhyatt.com/evernote-mobile.html) since the redesign. But as a designer, it can be hard to focus on the positive sentiment. The negative feedback seems so much louder.

For an app used by millions, any changes you make, whether significant or minute, are bound to upset someone. It's impossible to win over everybody. But, we can listen. As much as it stings to sift through angry comments, we owe it to people who rely so heavily on Evernote to welcome, and try to understand, negative feedback.

To the user who rage-tweets that they think the new interface is horrible, we need to ask why. To the users who are now crippled in meetings because we removed the presentation mode feature, we need to re-evaluate if that was the right decision or not.

It can be hard to remember, but we have to focus on separating out what people don't like just because it's different (and therefore _feels_ slower and more difficult), from what's actually broken.

We need to believe, though we may fumble now and again, that what we're doing is truly benefitting our users, our community, and our company.

We've come a long way, but we're also just getting started.

_I'd like to extend a huge thank you to all who were involved and came along for the ride with me over the past year, including our product manager, Chuck Pletcher, my design partner, Hannah Peckham, our entire product design team, and of course our kick-ass engineers. Thanks for all your help and support!_
